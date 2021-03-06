---
layout: post
title:  "Boot a new machine!"
date:   2016-03-11 09:40:15 +0800
categories: jekyll update
---

### Ubuntu

    # update system
    sudo apt-get update

    # base application
    sudo apt-get install git vim tmux -y

    # zsh
    sudo apt-get install zsh -y
    sudo chsh -s /usr/bin/zsh username
    sudo reboot
    sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    rm -rf .oh-my-zsh
    git clone https://github.com/xuedong09/oh-my-zsh.git .oh-my-zsh
    #change .zshrm theme to "xd", logout and login again

    # docker install

### ssh

    vim authorized_keys
    paste pub

### python3.7

    https://linuxize.com/post/how-to-install-python-3-7-on-ubuntu-18-04/

    sudo apt-get install python3.7-dev
    sudo apt-get install python3.7-distutils
    
    add to .zshrc:
        alias python='python3.7'
        export PATH="/home/xuedong09/.local/bin:$PATH"
        ulimit -n 65535

### pip
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    python get-pip.py

    
### vpn

    # create docker vpn container
    docker run \
    --name vpn \
    --env-file ./vpn.env \
    --restart=always \
    -p 500:500/udp \
    -p 4500:4500/udp \
    -v /lib/modules:/lib/modules:ro \
    -d --privileged \
    hwdsl2/ipsec-vpn-server

    # create environment file "vpn.env"
    VPN_IPSEC_PSK=password1
    VPN_USER=username
    VPN_PASSWORD=password2


### ufw add a new application

    [linode]
    title=This server open ports
    description=My linode will open these ports
    ports=
    
    sudo ufw default deny
    sudo ufw allow 22
    sudo ufw enable


### Python

    # install pip
    sudo apt-get install python-pip
    sudo pip install pip --upgrade
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    sudo python get-pip.py

    virtualenv
    virtualenvwrapper
    scrapy
        libxml2-dev
        libxslt1-dev
        libffi-dev
        libssl-dev
    click
    ansible
        paramiko
        PyYAML
        Jinja2
        httplib2
        six
    flask
    django
    pyinstaller


### ubbuntu sogou 输入法在其他应用中使用
    fcitx-frontend-qt4和fcitx-frontend-qt5
