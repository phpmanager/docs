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

Build Environment in GitHub Actions
-----------------------------------
The configuration file ``dotnet-desktop.yml`` shows the basic information on how to
compile the code base,

* Use ``windows-latest`` image.
* Run ``dist.release.bat`` to create release build.

The artifacts are the installers for testing.

Local Environment for Development
---------------------------------
You might set up a local development environment to match GitHub Actions's
``windows-latest`` image.

* A Visual Studio release (VS2022 and above recommended) to work on the C#
  projects.
* .NET Framework 4.6.2 and above.

C# Projects
-----------
The C# projects are the core assemblies to extend IIS Manager functionality,

* ``.Server`` is the extension server which provides access to PHP configuration.
* ``.Client`` is the extension client which implements UI elements in IIS Manager.
* ``.PowerShell`` provides PowerShell snapin support.
* ``.Setup Helper`` is a custom action for installation.

Installer Project
-----------------
The installer project uses WiX Toolset. To work on it, the following
dependencies must be installed,

* WiX Toolset (3.11.1 and above)
* WiX Toolset Visual Studio Extension (if you use Visual Studio)

References
----------

- :doc:`/getting-started/installation`
- :doc:`/getting-started/debugging`
