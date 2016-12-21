---
layout: post
title:  "virtualenv & virtualenvwrapper"
date:   2016-02-16 09:40:15 +0800
categories: jekyll update
---

### 1.virtualenv 能否用全局的python库？
```
创建虚拟环境的时候加上 --system-site-packages
```

### 2.只用部分全局库的时候，其他库与全局库版本不同？
```
创建虚拟环境的时候加上 --system-site-packages，同时在本地pip install 加上"-I" or "--ignore-installed",此时会安装本地库，用的就是本地库
```

### 3. 本机的uwsgi使用virtualenv 环境？
{% highlight python %}
wsgi 启动的时候指定virtualenv pythonhome路径
方法:
    -H|--home set PYTHONHOME/virtualenv
    -H|--virtualenv set PYTHONHOME/virtualenv
    -H|--venv set PYTHONHOME/virtualenv
    -H|--pyhome set PYTHONHOME/virtualenv
{% endhighlight %}


### 注意：用virtualenvwrapper的时候，需要在.profile or .bashrc or .zshrc中加上下面两句是配置永久生效

    export WORKON_HOME=~/Envs
    ubuntu:
    source /usr/local/bin/virtualenvwrapper.sh
    centos:
    source /usr/bin/virtualenvwrapper.sh


