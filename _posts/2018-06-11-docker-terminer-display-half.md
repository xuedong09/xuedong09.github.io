---
layout: post
title:  "docker terminal display half"
date:   2018-06-11 09:30:15 +0800
categories: jekyll update
---

### docker terminal display half
    
    docker exec -it aflt_kernel-api-master /bin/bash -c "export COLUMNS=`tput cols`; export LINES=`tput lines`; exec bash"
    docker exec  -e COLUMNS="`tput cols`" -e LINES="`tput lines`"  -it aflt_kernel-api-master bash 

