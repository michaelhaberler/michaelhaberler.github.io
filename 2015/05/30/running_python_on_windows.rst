Running Python on Windows
=========================


.. author:: default
.. categories:: none
.. tags:: windows, python, sysadmin
.. comments::


Download the Python Interpreter
-------------------------------

Download a suiting windows installer from `python windows installer`_ and
execute it to start the installation. Using default settings, I ended up with
python in ``C:\Python27``.

The python installation structure look similar to the linux version

+----------------------------------+-----------------------------------------+
|Windows                           |Linux (or Mac OSX)                       |
+==================================+=========================================+
|``C:\Python27\python.exe``        |``/usr/bin/python``                      |
+----------------------------------+-----------------------------------------+
|``C:\Python27\Scripts\pip.exe``   |``/usr/local/bin/pip``                   |
+----------------------------------+-----------------------------------------+
|``C:\Python27\Lib``               |``/usr/bin/lib/python2.7``               |
+----------------------------------+-----------------------------------------+
|``C:\Python27\Lib\site-packages`` |``/usr/bin/lib/python2.7/site-packages`` |
+----------------------------------+-----------------------------------------+


Installation Directory and PATH
-------------------------------

Make sure to add the python installation directory to the windows ``PATH``
variable (as described `on StackOverflow`_ and `in a blog post`_).


To update the ``PATH`` variable I had I had to log out and in first. Afterwards
I could run a python script from any location

.. code-block:: winbatch

    PS Z:\Developer\python> python.exe .\little.py
    hello world!
    ['Z:\\Developer\\python', 'C:\\Windows\\SYSTEM32\\python27.zip', 'C:\\Python27\\DLLs', 'C:\\Python27\\lib', 'C:\\Python2
    7\\lib\\plat-win', 'C:\\Python27\\lib\\lib-tk', 'C:\\Python27', 'C:\\Python27\\lib\\site-packages']

    PS Z:\Developer\python> cat .\little.py
    import sys

    print("hello world!")
    print(sys.path)


Packaging and pip
-----------------

For windows, pip & wheel packages seem fine (see `Christoph Golkhe's site`_).
For this, wheel packages (with C/C++) python extension modules have to be
compiled on windows.

Create wheel package

.. code-block:: winbatch

    python.exe setup.py bdist_wheel -d TARGET

`Install wheel package`_

.. code-block:: winbatch

    pip.exe install TARGET-majorV.minorV-py2.whl


Use case ``mpl_qt``
-------------------

Package and run `mpl_qt`_ run on windows.

.. code-block:: winbatch

    git clone https://github.com/micviklui/mpl_qt.git
    cd mpl_qt
    python.exe setup.py bdist_wheel
    cd dist
    pip.exe install .\mpl_qt-0.1-py2-none-any.whl

Let's try

.. code-block:: winbatch

    mpl_qt

This won't work. First, ``mpl_qt`` is `not recognized as an executable`_
(missing ``.exe`` suffix perhaps?) and it isn't associated with the python
interpreter and second, dependencies are ignored.

The dependencies can be resolved with ``pip``

.. code-block:: winbatch

    # PySide
    pip.exe install PySide
    # numpy (download appropriate file from http://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy)
    pip.exe install .\numpy-1.9.2+mkl-cp27-none-win_amd64.whl
    # matplotlib (download from http://www.lfd.uci.edu/~gohlke/pythonlibs/#matplotlib)
    pip.exe install .\matplotlib-1.4.3-cp27-none-win_amd64.whl

Finally, the python script runs by stating the absolute path. The Qt-powered GUI
of ``mpl_qt`` will now pop up

.. code-block:: winbatch

    python.exe C:\Python27\Scripts\mpl_qt


.. _python windows installer: https://www.python.org/downloads/windows/
.. _on StackOverflow: http://stackoverflow.com/questions/6318156/adding-python-path-on-windows-7
.. _in a blog post: http://www.anthonydebarros.com/2014/02/16/setting-up-python-in-windows-8-1/
.. _Christoph Golkhe's site: http://www.lfd.uci.edu/~gohlke/pythonlibs/
.. _Install wheel package: https://pip.pypa.io/en/latest/user_guide.html#installing-from-wheels
.. _mpl_qt: https://github.com/micviklui/mpl_qt
.. _not recognized as an executable: https://docs.python.org/2/faq/windows.html

..
    .. _official python windows doc: https://docs.python.org/2/using/windows.html
