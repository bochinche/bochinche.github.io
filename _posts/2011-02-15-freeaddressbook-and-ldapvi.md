---
layout: post
title:  "on a free based ldap address-book and ldapvi"
date:   2011-02-15 17:45:47 +0100
categories: IT
---

With the advent of smartphones, tablet PCs and the use of multiple social networks, the need to keep contact information in sync across multiple accounts and providers has become increasingly difficult. Social networks such as Facebook, Xing, and Linked-in try to access your Gmail, Hotmail, and other accounts to collect data on your "social" connections.

It is not the intention of this post to argue for or against the use of your personal data by big companies to establish demographic patterns or studies on direct advertising... I try to keep most information to myself and decide what to share with the world and what not.

Recently I had to change my ldap provider and stumbled upon a free ldap service provided by entic.net. LDAP stands for Lightweight Directory Access Protocol. It is one of the foundations of MS Active Directory services. LDAP can be used in many ways... one of them is to store your contact information in a central database and provide access to it via a standardized protocol.

Being a CLI freak, I try to keep things dumb and simple. Instead of using GUIs to edit my contacts, I use a small vi program called ldapvi. Ldapvi is available in most Linux repositories and in macports for the Mac.

To make ldapvi work with entic.net's free ldap services, you need to set some options:

```
ldapvi \ 
-D uid=<username>, ou=people, o=entic.net \ 
-w YOURPASSWORD \ 
-h ldaps://ds1-lon.entic.net:636 \ 
-b uid=<username>, ou=People, o=entic.net \ 
-tls allow
```

With the above options you are ready to edit your contacts from your CLI. Entic.net also offers an iPhone app that you can use to edit your contacts.

I haven't migrated my contacts yet because I still have to work out some privacy issues.