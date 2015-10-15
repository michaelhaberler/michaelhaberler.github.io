---
layout: post
title:  "Vim on Windows"
date:   2015-10-14 10:22:41
tags: windows vim
---

Collection of Tips/Tricks:
[http://vim.wikia.com/wiki/Category:Windows](http://vim.wikia.com/wiki/Category:Windows)


Folder structre for vim on windows:
{% highlight winbatch %}
cp .vimrc _vimrc
mkdir ~/vimfiles
mkdir ~/vimfiles/autoload
mkdir ~/vimfiles/bundle
mkdir ~/vimfiles/ftplugin
mkdir ~/vimfiles/indent
{% endhighlight %}

Download and install pathogen:
{% highlight winbatch %}
curl -outfile ~/vimfiles/autoload/pathogen.vim https://tpo.pe/pathogen.vim
{% endhighlight %}
