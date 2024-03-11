Debugging 
=========

By `Lex Li`_

This article describes how to debug the code.

.. contents:: In this article:
  :local:
  :depth: 1

Prerequisites
-------------
#. Make sure you set up a local development environment as revealed in
:doc:`/getting-started/source`.

#. Install PHP Manager locally so all IIS Manager configuration is set.

Detailed Steps
--------------
#. Launch Visual Studio as administrator.
#. Open the solution and make your changes.
#. Compile the solution.
   .. note:: Post build events would register the new assemblies in GAC.
#. Close IIS Manager if you already opened it.
#. Open IIS Manager and do nothing yet.
#. Attach Visual Studio to IIS Manager process (`inetmgr.exe`).
#. Set break points if you like.
#. Back to IIS Manager and open PHP Manager pages to trigger the break points.

.. note:: Don't attempt to launch IIS Manager from Visual Studio directly as it
   might only work on 32 bit Windows.

References
----------

- :doc:`/getting-started/installation`
- :doc:`/getting-started/source`
