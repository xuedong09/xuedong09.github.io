---
layout: post
title:  "Better Exception"
date:   2018-05-29 09:30:15 +0800
categories: jekyll update
---
#### Use Better Exception in try：

{% highlight python %}
   import sys
   import better_exceptions
   better_exceptions.hook()

   try:
      pass
   except Exception as e:
      sys.excepthook(e.__class__, e, sys.exc_info()[2])

{% endhighlight %}
