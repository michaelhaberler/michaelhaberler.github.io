Powershell Tips & Tricks
========================


.. author:: default
.. categories:: none
.. tags:: windows, powershell, sysadmin
.. comments::


List hidden files

.. code-block:: winbatch

    ls -Force

Search for file in directory (find)

.. code-block:: winbatch
    
    ls -Path C:\Path\To\Directory -Recursive -Filter pattern

Create symbolic link

.. code-block:: winbatch

    cmd /c mklink C:\link\to\target C:\target\file

Powershell community extensions `<http://pscx.codeplex.com>`_
