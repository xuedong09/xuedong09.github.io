---
layout: post
title:  "logrotate"
date:   2017-01-17 09:30:15 +0800
categories: jekyll update
---

### daily logrotate

    /var/log/*.log {
        daily
        missingok
        rotate 30
        notifempty
        #size 1k
        copytruncate
        #create 640 user group
        dateformat .%Y-%m-%d
        dateext 
    }
