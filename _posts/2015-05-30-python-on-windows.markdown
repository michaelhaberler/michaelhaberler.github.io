---
layout: post
title:  "Running Python on Windows"
date:   2015-05-30 10:22:41
categories: windows python
---

1. Download a suiting windows installer from
   [https://www.python.org/downloads/windows/][python-windows-installer] and
   execute it to start the installation. Using default settings, I ended up with
   python in ``C:\Python27``.

The python installation structure look similar to the linux version:

--------------------------------- ----------------------------------------------
``C:\Python27\python.exe``        ``/usr/bin/python``
``C:\Python27\Scripts\pip.exe``   ``/usr/local/bin/pip`` (probably installed with
``get-pip.py``)
``C:\Python27\Lib``               ``/usr/bin/lib/python2.7``
``C:\Python27\Lib\site-packages`` ``/usr/bin/lib/python2.7/site-packages``
--------------------------------- ----------------------------------------------

{% highlight winbatch %}
PS C:\> ls C:\Python27


    Directory: C:\Python27\Lib\site-packages


Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         5/30/2015  10:03 PM            pip
d----         5/30/2015  10:03 PM            pip-7.0.1.dist-info
d----         5/30/2015  10:03 PM            pkg_resources
d----         5/30/2015  10:03 PM            setuptools
d----         5/30/2015  10:03 PM            setuptools-16.0.dist-info
d----         5/30/2015  10:03 PM            _markerlib
-a---         5/30/2015  10:03 PM        126 easy_install.py
-a---         5/30/2015  10:03 PM        346 easy_install.pyc
-a---         4/30/2014   9:54 AM        119 README.txt


{% endhighlight %}

2. Make sure to add the python installation directory to the windows ``PATH``
   variable.



[python-windows-installer]: https://www.python.org/downloads/windows/
