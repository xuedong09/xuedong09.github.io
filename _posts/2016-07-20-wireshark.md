---
layout: post
title:  "wireshark"
date:   2016-07-20 09:30:15 +0800
categories: jekyll update
---

### ubuntu latest wireshark

    sudo add-apt-repository ppa:wireshark-dev/stable

### create an wireshark group and add user to group

    sudo dpkg-reconfigure wireshark-common
    sudo gpasswd -a $USER wireshark 
