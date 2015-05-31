---
layout: post
title:  "Running Python on Windows"
date:   2015-05-30 10:22:41
categories: windows python
---

Download the Python Interpreter
-------------------------------

Download a suiting windows installer from
[https://www.python.org/downloads/windows/][python-windows-installer] and
execute it to start the installation. Using default settings, I ended up with
python in ``C:\Python27``.

The python installation structure look similar to the linux version

|Windows                            | Linux (or Mac OSX)
| ``C:\Python27\python.exe``        | ``/usr/bin/python``
| ``C:\Python27\Scripts\pip.exe``   | ``/usr/local/bin/pip`` (probably installed with ``get-pip.py``)
| ``C:\Python27\Lib``               | ``/usr/bin/lib/python2.7``
| ``C:\Python27\Lib\site-packages`` | ``/usr/bin/lib/python2.7/site-packages``


Installation Directory and PATH
-------------------------------

Make sure to add the python installation directory to the windows ``PATH``
variable (as described [on StackOverflow][so-windows-path] and
[in a blog post][blog-windows-python]). 


To update the ``PATH`` variable I had I had to log out and in first. Afterwards
I could run a python script from any location
 
{% highlight winbatch %}
PS Z:\Developer\python> python.exe .\little.py
hello world!
['Z:\\Developer\\python', 'C:\\Windows\\SYSTEM32\\python27.zip', 'C:\\Python27\\DLLs', 'C:\\Python27\\lib', 'C:\\Python2
7\\lib\\plat-win', 'C:\\Python27\\lib\\lib-tk', 'C:\\Python27', 'C:\\Python27\\lib\\site-packages']

PS Z:\Developer\python> cat .\little.py
import sys

print("hello world!")
print(sys.path)
{% endhighlight %}


Packaging and pip
-----------------

For windows, pip & wheel packages seem fine (see [Christoph Golkhe's site][christoph-golkhe]). For this, wheel packages (with C/C++) python extension modules have to be compiled on windows.


Create wheel package 

{% highlight winbatch %}
python.exe setup.py bdist_wheel -d TARGET
{% endhighlight %}

Install wheel package
[https://pip.pypa.io/en/latest/user_guide.html#installing-from-wheels][pip-install-from-wheels].

{% highlight winbatch %}
pip.exe install TARGET-majorV.minorV-py2.whl
{% endhighlight %}

Use case ``mpl_qt``
-------------------

Package and run [mpl_qt](https://github.com/michaelhaberler/mpl_qt) run on windows.

{% highlight winbatch %}
git clone https://github.com/michaelhaberler/mpl_qt.git
cd mpl_qt
python.exe setup.py bdist_wheel
cd dist
pip.exe install .\mpl_qt-0.1-py2-none-any.whl 
{% endhighlight %}

Let's try

{% highlight winbatch %}
mpl_qt
{% endhighlight %}

This won't work. First, ``mpl_qt`` [is not recognized as an executable
(missing ``.exe`` suffix perhaps?) and it isn't associated with the python
interpreter](https://docs.python.org/2/faq/windows.html) and second,
dependencies are ignored.

The dependencies can be resolved with ``pip``

{% highlight winbatch %}
# PySide
pip.exe install PySide
# numpy (download appropriate file from http://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy)
pip.exe install .\numpy-1.9.2+mkl-cp27-none-win_amd64.whl
# matplotlib (download from http://www.lfd.uci.edu/~gohlke/pythonlibs/#matplotlib)
pip.exe install .\matplotlib-1.4.3-cp27-none-win_amd64.whl
{% endhighlight %}

Finally, the python script runs by stating the absolute path. The Qt-powered GUI
of ``mpl_qt`` will now pop up

{% highlight winbatch %}
python.exe C:\Python27\Scripts\mpl_qt
{% endhighlight %}

Convert Python Script to Windows Executable
-------------------------------------------

http://www.py2exe.org/


[python-windows-installer]: https://www.python.org/downloads/windows/
[so-windows-path]: http://stackoverflow.com/questions/6318156/adding-python-path-on-windows-7
[blog-windows-python]: http://www.anthonydebarros.com/2014/02/16/setting-up-python-in-windows-8-1/
[christoph-golkhe]: http://www.lfd.uci.edu/~gohlke/pythonlibs/
[pip-install-from-wheels]: https://pip.pypa.io/en/latest/user_guide.html#installing-from-wheels

[official-python-windows-doc]: https://docs.python.org/2/using/windows.html
