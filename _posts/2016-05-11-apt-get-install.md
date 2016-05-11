---
layout: post
title:  "apt-get isntall"
date:   2016-05-11 09:30:15 +0800
categories: jekyll update
---

### swig insall error
    SWIG/_evp.i:12: Error: Unable to find 'openssl/opensslconf.h'
    SWIG/_ec.i:7: Error: Unable to find 'openssl/opensslconf.h'
    
    solution:
    ln -s /usr/include/x86_64-linux-gnu/openssl/opensslconf.h /usr/include/openssl/opensslconf.h
