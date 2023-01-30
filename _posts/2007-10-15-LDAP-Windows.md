---
layout: post
title:  "on linux + MS AD Authentication using nssldap and PAM"
date:   2007-10-15 17:45:47 +0100
categories: IT windows linux
---

# Authentication in hybrid (linux and MS Windows) environments has always been a headache for administrators.

I have been enough around to have seen people trying to solve the problem in different ways. There are of course many ways to approach the problem (i.e. winbind). In the environment I am working in we decided to go for an AD based solution including the Unix attributes in the directory tree. This howto is not focused on the windows side of the installation; this information will follow. The linux side of the installation is actually the complex one. We are working in a native windows environment meaning that our clients usually boot windows however, we are also offering LINUX to our “clients”

NOTES: in a Debian / Enviroment the following packages will be needed for this installation:
#apt-get install libnss-ldap libpam-ldap libpam-krb5 krb5-user krb5-config
optionally you could add the following package:
#apt-get install ldapvi

Packages in ubuntu are named differently: libnss-ldap, libpam-krb5

1. nss_ldap configuration

The nss_ldap module can be used to access the MS AD ldap tree if configured correctly:

We need the following options:

```
/etc/nssswitch.conf
passwd: compat ldap
group: compat ldap
```

We also need to change the /etc/ldap.conf or /etc/ldap/ldap.conf configuration file

We shall be able to check if everything is working correctly by issuing the following command

```getent passwd DOMAINUSER```

NOTES:
We do not use SSL since it adds a a level of complexity to our environment. We are already in a very tight capsule as to be worried about securities issues. If you prefer to go on the save side you could add the AD DC SSL certificate.

2. kerberos configuration

In order to enable kerberos for user login we only need to edit the following file:
/etc/krb5.conf and add the realm of the domain against we want to authenticate:

```
/etc/krb5.conf
[libdefaults]
default_realm = EXAMPLE.COM
```

After this step the configuration could be tested issuing the following command

``` kinit username@EXAMPLE.COM ```

The following command should show a list with exactly one ticket:
``` klist ```

If you get the following error:
“kinit(v5):Clock skew too great while getting initial credentials”
you should update the date and time of the system by using ntp-date.

1. SSH configuration

The final step of our configuration is to allow ssh access to domain users:

```/etc/pam.d/ssh:
# PAM configuration for the Secure Shell service
```

```
# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth required pam_env.so # [1]
```

```
# Standard Un*x authentication.
#@include common-auth
auth sufficient pam_krb5.so

# Standard Un*x authorization.
#@include common-account
account sufficient pam_krb5.so

# Standard Un*x session setup and teardown.
@include common-session

# Print the message of the day upon successful login.
session optional pam_motd.so # [1]

# Print the status of the user’s mailbox upon successful login.
session optional pam_mail.so standard noenv # [1]

# Set up user limits from /etc/security/limits.conf.
session required pam_limits.so

# Set up SELinux capabilities (need modified pam)
# session required pam_selinux.so multiple

# Standard Un*x password updating.
@include common-password
```

Resources:
- Debian Samba 3 / LDAP / PHP LDAP Admin HOWTO: [https://www.nomis52.net/?section=docs&page=samldap](https://www.nomis52.net/?section=docs&page=samldap)