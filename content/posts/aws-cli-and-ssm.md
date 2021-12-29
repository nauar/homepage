---
author: "Arnau Oncins"
title: "Installing AWS cli v2 and Session Manager plugin in a portable way on Linux"
date: "2021-03-29"
description: "An alternative way of installing AWS cli v2 and its Session Manager plugin (portable way) on Linux"
comments: true
tags: ["aws", "cli", "ssm"]
---

After more than a year not showing any activity here, I am retaking the blog. Some personal topics, in top of COVID-19 pandemia, made me abandon it for a long while.

## My way of installing software on Linux systems

I'm using Linux since the late 90s. I began with Slackware, later I moved to Debian, later to Ubuntu, later to Kubuntu, and, since 2008, I'm using [Archlinux](https://archlinux.org). In this journey, I also have tested Mandriva, Suse, Fedora and many others. I also wear a pendrive with the latest version of Backtrack/Kali Linux on my laptop.

After more than 20 years being Linux user, I have developed some habits. One of them is I prefer to use `.tar.gz` distributions of applications I directly use whenever I can (despite using the distribution package manager for pure system packages, `pacman` or `aur` in my case).

This may seem a bit excentric. However, the reason behind this weird habit is that I don't like how are built some app packages that install some bloatware files in my system. It reminds me the first time I used `pip` to install some [Python](https://www.python.org/) dependencies to use certain scripts. They installed in an uncontrolled way a lot of packages for executing once that python script. Thanks God for  creating the [Python virtual environments](https://docs.python.org/3/tutorial/venv.html) some time ago! 😊

## Installing AWS CLI v2 and the Session Manager plugin in a portable way

I want to show a way of installing [AWS CLI v2](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) and its [Session Manager plugin](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-working-with-install-plugin.html).

By clicking on these links, you will find instructions to install both of them. If you want to install them in a portable way, you will find very easily an AWS CLI v2 binary. However, the Session Manager plugin looks like harder to install in this way as it is only available in a Debian-like (.deb) or RedHat-like (.rpm) package.

At the end of the day, the Session Manager plugin it's another binary. Thus, I thought it will be very likely to find this binary very easily inside any of these packages. I knew that .deb packages are pure Linux archives (you can handle them with `ar` command).

So, I did the following steps to obtain the executable from this package:

1. Download the latest ubuntu package:

`$ curl "https://s3.amazonaws.com/session-manager-downloads/plugin/latest/ubuntu_64bit/session-manager-plugin.deb" -o "session-manager-plugin.deb"`

2. Unarchive the elements of the .deb package:

`$ ar x session-manager-plugin.deb`

3. Untar the data element of the .deb package:

`$ tar xfvz data.tar.gz`

4. In `./usr/local/sessionmanagerplugin/bin/` folder, you will find the binary executable. You can copy/move it to any folder in your path.

This way, you can make use of AWS CLI v2 and its Session Manager plugin without having to use a Debian-like or a RedHat-like Linux distribution to use them in your system. You can find the scripts for updating both elements in the following [GitHub Gist](https://gist.github.com/nauar/c628a15ecb7db608edcdbfc8c543fa22).