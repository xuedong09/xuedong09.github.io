---
layout: post
title:  "jekyll"
date:   2016-02-18 17:23:15 +0800
categories: jekyll update
---

### jekyll highlight tag never closed bug
{% highlight html %}
This excerpt will result in Liquid Exception: highlight tag was never closed in buggy-post.txt, 
since the {{% highlight %}} tag is never closed.

To fix this, you can either fix every post so that the excerpt is valid Liquid markup,
or prevent Jekyll from generating the excerpts in the first place.
Jekyll does not yet have a way to disable excerpts entirely, 
so the next-best option is to configure it so that the excerpts are always valid Liquid.

You can do this by setting excerpt_separator to a nonsense string that never appears in your posts, 
so that the excerpt will include the entire post (which is already known to be valid markup).
Better yet, you can set excerpt_separator to an empty string, so that the excerpt will end immediately.
This will reduce the amount of work that Jekyll needs to do, making your site build slightly faster.

In short, this bug can be fixed by adding the following line to _config.yml:
excerpt_separator: ""   # Workaround for http://blog.slaks.net/2013-08-09/jekyll-tag-was-never-closed
{% endhighlight %}


### jekll escape {{ " {{ " }}}} and {{ "{% " }}%}
    {{ "{% this " }}%}
    and for tags, to escape {{ this }} use:
    {{ "{{ this " }}}}
