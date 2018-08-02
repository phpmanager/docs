Explanation on Source Code
==========================

By `Lex Li`_

This article describes the code base details.

.. contents:: In this article:
  :local:
  :depth: 1

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

Installer Projects
------------------
The installer projects are of Visual Studio Setup Project type,

* PHPManagerSetup.vdproj generates PHPManagerForIIS.msi, for IIS 7.x x86.
* PHPManagerSetup_64.vdproj generates PHPManagerForIIS_64.msi, for IIS 7.x x64.
* PHPManagerSetup8.vdproj generates PHPManagerForIIS8.msi, for IIS 8.x and 10.x
  x86.
* PHPManagerSetup8_64.vdproj generates PHPManagerForIIS8_64.msi, for IIS 8.x
  and 10.x x64.
