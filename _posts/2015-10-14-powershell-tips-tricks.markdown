---
layout: post
title:  "Collection of Frequently Used Powershell Commands"
date:   2015-10-15 10:22:41
tags: windows sysadmin
---

list hidden files
{% highlight winbatch %}
ls -Force
{% endhighlight %}

search for file in directory (find)
{% highlight winbatch %}
ls -Path C:\Path\To\Directory -Recurse -Filter pattern
{% endhighlight %}

symbolic link
{% highlight winbatch %}
cmd /c mklink C:\link\to\target C:\target\file
{% endhighlight %}

Powershell community extensions:
[http://pscx.codeplex.com/](http://pscx.codeplex.com)
