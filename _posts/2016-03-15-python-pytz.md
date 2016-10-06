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

### 根据机器时间获取太平洋时间是pst还是pdt

    def get_local_utcoffset():
        now = datetime.datetime.now()
        pacific = pytz.timezone('US/Pacific')
        now_tz = pacific.localize(now)
        local_utcoffset = -7 if now_tz.strftime('%z') == '-0700' else -8
        return local_utcoffset

### 获取两个时区的间隔

    def get_delta_utcoffset(utcoffset):
      local_utcoffset = get_local_utcoffset()
      delta_utcoffset = utcoffset - local_utcoffset
      delta_t = datetime.timedelta(hours=delta_utcoffset)
      return delta_utcoffset

### 将本地时间换算成对应时区的日期

    def get_utc_date(utcoffset):
        now = datetime.datetime.now()
        delta_utcoffset = get_delta_utcoffset(utcoffset)
        delta_hour = datetime.timedelta(hours=delta_utcoffset)
        utc_date = now + delta_hour
        utc_date = str(utc_date.date())
        return utc_date


### 给本地时间加timezone

    import datetime
    from pytz import timezone
    now = datetime.datetime.now()
    tz = timezone('US/Pacific')
    tznow = tz.localize(now)


### format datetime string

    import datetime

    now = datetime.datetime.now()
    now.strftime("%Y-%m-%dT%H:%M:%S.%f%z")

