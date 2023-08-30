---
layout: post
title:  "RaspberryPi: installing jekyll on RPI"
date:   2023-08-30 08:45:47 +0100
categories: rpi it webdesign 
---

# Installing Jekyll on Raspberry Pi: Simplifying Local Development

If you've ever wanted the convenience of designing and testing your website locally on your Raspberry Pi, installing [Jekyll](https://jekyllrb.com/) can be a game-changer. Jekyll allows you to build and manage your website right on your Raspberry Pi. In this post, we'll guide you through the installation process to get you started.

## Installation Steps

To install Jekyll on your Raspberry Pi, follow these simple steps:

1. Update your package list to ensure you have the latest information about available packages:
    ```bash
    sudo apt-get update
    ```

2. Install the necessary software properties common package:
    ```bash
    sudo apt-get install software-properties-common -y
    ```

3. Install the Ruby programming language (required by Jekyll) along with its full set of functionalities:
    ```bash
    sudo apt-get install ruby-full -y
    ```

4. With Ruby in place, you can now install Jekyll using the following command:
    ```bash
    sudo gem install jekyll
    ```

5. Additionally, it's recommended to install Bundler, a tool to manage your Ruby application's dependencies:
    ```bash
    sudo gem install bundler
    ```

Now you're all set to start using Jekyll for your local web development needs.

## Additional Resources

For more detailed instructions and troubleshooting tips, you can refer to the [Raspberry Pi Guide](https://raspberrypi-guide.github.io/other/installing-jekyll-webserver) on installing Jekyll and setting up a web server.

## Conclusion

Setting up Jekyll on your Raspberry Pi opens up a world of possibilities for streamlined local web development. With a few simple commands, you can have Jekyll up and running, allowing you to design, test, and perfect your website right on your Raspberry Pi.

## Additional steps
```bash
bundle config set --local path '$HOME/.gem'
bundle install
```