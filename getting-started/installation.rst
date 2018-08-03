Installation on Windows
=======================

By `Lex Li`_

This article describes how to install PHP Manager for IIS on Windows.

.. contents:: In this article:
  :local:
  :depth: 1

Supported Platforms
-------------------
Make sure you are using a supported Windows release,

* Windows Server 2008
* Windows 7
* Windows Server 2008 R2
* Windows Server 2012
* Windows 8.1
* Windows Server 2012 R2
* Windows 10
* Windows Server 2016

All other releases are either end-of-life, or not yet supported.

Prerequisites
-------------
There are a few requirements on the system,

Windows Server 2008 Specific
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* .NET Framework 3.5 SP1
* PowerShell 2.0
* Windows PowerShell snap-in for IIS 7

Windows Server 2008 R2 Specific
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* .NET Framework 3.5.1 feature must be manually enabled.

Windows Server 2012 Specific
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* .NET Framework 4.5.2 must be installed in advance.

Windows 8.1 Specific
^^^^^^^^^^^^^^^^^^^^
* .NET Framework 4.5.2 must be installed in advance.

Windows Server 2012 R2 Specific
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* .NET Framework 4.5.2 must be installed in advance.

FastCGI
^^^^^^^
On all IIS releases you should enable FastCGI. More information can be found in
`this article <https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-on-iis/enable-fastcgi-support-in-iis-7-on-windows-server-2008-windows-server-2008-r2-windows-vista-or-windows-7>`_ .

Installers
----------
Please visit `Releases <https://github.com/phpmanager/phpmanager/releases>`_ to
find the latest releases. Each releases shows the installers you can use.

For 2.0 Beta 1, there are four installers for different scenarios,

* PHPManagerForIIS7x.msi, for IIS 7.x x86.
* PHPManagerForIIS7x_64.msi, for IIS 7.x x64.
* PHPManagerForIIS8x10x.msi, for IIS 8.x and 10.x x86.
* PHPManagerForIIS8x10x_64.msi, for IIS 8.x and 10.x x64.

Please download the proper installer for your machine and then execute it.

.. note:: Please report issues to `Issues
   <https://github.com/phpmanager/phpmanager/issues>`_ .

Refereces
---------

- :doc:`/getting-started/source`

