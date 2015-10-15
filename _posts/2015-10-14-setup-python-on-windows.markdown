---
layout: post
title:  "Setup Python on Windows"
date:   2015-10-14 10:22:41
tags: windows python sysadmin
---

Download and run the [python installer](https://www.python.org/downloads/windows/):
- add python to PATH
- install pip
- install for all users (installs to C:\Program Files\, or C:\Program Files (x86) if 32-bit version)
- add python to environment variables (after powershell restart $env:Path has C:\Program Files\Python x.y)

Add python scripts to the path (in powershell) (gives you pip) for the session:
{% highlight winbatch %}
$env:Path += ';C:\Program Files\Python 3.5\Scripts'
{% endhighlight %}

Find py.exe and pip.exe
{% highlight winbatch %}
$env:Path.Split(";") | ls -Filter pip.exe
{% endhighlight %}

Look up systemsteuerung > system und sicherheit > system > erweiterte systemeinstellungen > Umgebungsvariablen
{% highlight winbatch %}
> pip list
pip (7.1.2)
setuptools (18.2)
{% endhighlight %}

for complex packages with binaries use the [unofficial python extension package repository for windows](http://www.lfd.uci.edu/~gohlke/pythonlibs/)
instead of pip install numpy matplotlib

successful installation:
{% highlight winbatch %}
pip install six
pip install python-dateutil
pip install pytz
pip install pyparsing
pip install pillow
pip install tornado
{% endhighlight %}

failed:
{% highlight winbatch %}
pip install pycairo --allow-external pycairo --allow-unverified pycairo
pip install pyside
{% endhighlight %}

will install (when executed in powershell as administarator) to
C:\Program Files\Python 3.5\Lib\site-packages

download [qt](http://www.qt.io/download-open-source/#section-2)
