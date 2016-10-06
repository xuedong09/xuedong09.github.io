---
layout: post
title:  "crontab problem"
date:   2016-03-19 09:30:15 +0800
categories: jekyll update
---

### crontab use date with format
{% highlight shell %}
* * * * * `date "+\%Y-\%m-\%d \%H:\%M:\%S"` > ~/tttt
{% endhighlight %}


### crontab no daemon docker run cron job, use supervisor

     [program:cron]
     command=cron -f
