---
layout: post
title:  "python pytz"
date:   2016-03-15 17:00:15 +0800
categories: jekyll update
---



### 根据时区获取当前的utc offset（尤其针对有dst要求的时区）以太平洋时区为例（PST/PDT）

{% highlight python %}

import pytz
import datetime

pytz.all_timezonses 
pacific = pytz.timezone('US/Pacific')
now = datetime.datetime.now()
now_tz = pacific.localize(now)
now_tz.strftime("%z")

{% endhighlight %}




