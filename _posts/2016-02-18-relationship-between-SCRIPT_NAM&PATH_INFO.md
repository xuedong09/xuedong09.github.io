---
layout: post
title:  "relationship between SCRIPT_NAME and PATH_INFO"
date:   2016-02-18 09:30:15 +0800
categories: jekyll update
---

### In the PEP it says:
{% highlight python %}
SCRIPT_NAME

   The initial portion of the request URL's "path" that corresponds

   to the application object, so that the application knows its virtual

   "location". This may be an empty string, if the application

   corresponds to the "root" of the server.

PATH_INFO

   The remainder of the request URL's "path", designating the virtual

   "location" of the request's target within the application. This may

   be an empty string, if the request URL targets the application root

   and does not have a trailing slash.

Seeking further clarification on what happens in certain circumstances,

paste.lint says:

   - That SCRIPT_NAME and PATH_INFO are empty or start with /

   - That at least one of SCRIPT_NAME or PATH_INFO are set.

   - That SCRIPT_NAME is not '/' (it should be '', and PATH_INFO should

     be '/').

As illustration of what this appears to all mean:

   Mount Point: /application

   Request URL: /application/something

yields:

   SCRIPT_NAME: /application

   PATH_INFO: /something

and:

   Request URL: /application

yields:

   SCRIPT_NAME: /application

with PATH_INFO not needing to actually be defined as it will be empty.

Further:

   Request URL: /application/

yields:

   SCRIPT_NAME: /application

   PATH_INFO: /

For application mounted at the root of the web server:

   Mount Point:

   Request URI: /something

yields:

   SCRIPT_NAME:

   PATH_INFO: /something

Where SCRIPT_NAME doesn't really need to be defined given that it is 

empty.

All okay so far.

Now my questions revolve around where an application is mounted

at a URL which itself has a trailing slash. For example, in Apache 

one can

say:

   <Location /application/>

   ...

   </Location>

If a request arrives which is for '/application', it will not 

actually be directed

to the application because it doesn't have the required trailing 

slash and

so will not match the path in the directive.

In effect the mount point of the application is '/application/'. One 

cannot treat

the mount point as being '/application' as if that is then used by 

user code

to reference back to the root of the application for a link or 

redirect it will not

actually work as the trailing slash is missing.

Thus, this would suggest that for this case that one would have:

   SCRIPT_NAME: /application/

This though doesn't seem to marry up with WSGI very well. This is 

because

reconstruction of URLs indicates that all that is required is to join 

SCRIPT_NAME

and PATH_INFO back together. Ie.,

   from urllib import quote

   url = environ['wsgi.url_scheme']+'://'

   if environ.get('HTTP_HOST'):

       url += environ['HTTP_HOST']

   else:

       url += environ['SERVER_NAME']

       if environ['wsgi.url_scheme'] == 'https':

           if environ['SERVER_PORT'] != '443':

              url += ':' + environ['SERVER_PORT']

       else:

           if environ['SERVER_PORT'] != '80':

              url += ':' + environ['SERVER_PORT']

   url += quote(environ.get('SCRIPT_NAME',''))

   url += quote(environ.get('PATH_INFO',''))

   if environ.get('QUERY_STRING'):

       url += '?' + environ['QUERY_STRING']

If that is seen as being the case, then we would need to have:

   Mount Point: /application/

   Request URL: /application/something

yields:

   SCRIPT_NAME: /application/

   PATH_INFO: something

This though violates what paste.lint says is correct:

   - That SCRIPT_NAME and PATH_INFO are empty or start with /

Ie., can't have PATH_INFO not start without a slash. But to put one 

in and still

have SCRIPT_NAME valid as far as what the mount point is, you would 

need:

   SCRIPT_NAME: /application/

   PATH_INFO: /something

In URL reconstruction though this would yield:

   /application//something

Ie., introduce a double slash.

It also sort of violates the definition of PATH_INFO in the PEP as well.

It therefore seems that the idea of the mount point for an 

application having a

trailing slash may be incompatible with WSGI. Can this be considered 

to be the

case or is there some other way one is meant to deal with this?

Should a WSGI adapter for a web server which allows a mount point to 

have a

trailing slash specifically flag as a configuration error an attempt 

to use such a

mount point given that it appears to be incompatible with WSGI?

Thanks in advance for any feedback.

Graham

{% endhighlight %}
