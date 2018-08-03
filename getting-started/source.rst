Source Code
===========

By `Lex Li`_

This article describes the technical details on the code base.

.. contents:: In this article:
  :local:
  :depth: 1

Source Code Repository
----------------------
The latest source code can be found on `GitHub
<https://github.com/phpmanager/phpmanager>`_ .

Build Environment in AppVeyor
-----------------------------
The configuration file ``AppVeyor.yml`` shows the basic information on how to
compile the code base,

* Use Visual Studio 2013 image.
* Run ``dist.release.bat`` to create release build.

The artifacts are the installers for testing.

Local Environment for Development
---------------------------------
You might set up a local development environment to match AppVeyor's Visual
Studio 2013 image.

* A Visual Studio release (VS2013 and above recommanded) to work on the C#
  projects.
* A Visual Studio release (VS2013 and above recommended) to build the installer
  projects.
* Windows SDK for Windows Server 2008 and .NET Framework 3.5.

C# Projects
-----------
The C# projects are the core assemblies to extend IIS Manager functionality,

* Server is the extension server which provides access to PHP configuration.
* Client is the extension client which implements UI elements in IIS Manager.
* PowerShell provides PowerShell snapin support.
* Setup Helper is a custom action for installation.

Installer Project
-----------------
The installer project uses WiX toolset. To work on it, the following
dependencies must be installed,

* WiX Toolset (3.11.1 and above)
* WiX Toolset Visual Studio Extension (if you use Visual Studio)

Refereces
---------

- :doc:`/getting-started/installation`
- :doc:`/getting-started/debugging`
