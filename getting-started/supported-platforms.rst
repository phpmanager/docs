Supported Platforms
===================

By `Lex Li`_

This article describes what are the supported platforms.

.. contents:: In this article:
  :local:
  :depth: 1

Overview
--------
Generally speaking, the installers are designed to work for all supported Windows
releases from Microsoft.

Platform specific dependencies are listed below. They must be installed in
advance, or the installer might not work properly.

Windows Server 2012
^^^^^^^^^^^^^^^^^^^
* Require IIS 8.0
* Require .NET Framework 4.6.2

Supported till October 10, 2023

Windows Server 2012 R2
^^^^^^^^^^^^^^^^^^^^^^
* Require IIS 8.5
* Require .NET Framework 4.6.2

Supported till October 10, 2023

Windows 10
^^^^^^^^^^
* Require IIS 10

Supported till Oct 14, 2025

Windows Server 2016
^^^^^^^^^^^^^^^^^^^
* Require IIS 10

Supported till Jan 12, 2027

Windows Server 2019
^^^^^^^^^^^^^^^^^^^
* Require IIS 10

Supported till Jan 9, 2029

Windows 11
^^^^^^^^^^
* Require IIS 10

Windows Server 2022
^^^^^^^^^^^^^^^^^^^
* Require IIS 10

Supported till Oct 14, 2031

PHP on Windows Status
---------------------
There are two facts you should keep in mind that,

* Microsoft discontinued its support of PHP 8.0 and above on Windows as `announced on July 9, 2020 <https://news-web.php.net/php.internals/110907>`_
* All PHP versions below 8.0 are `now end of life <https://www.php.net/supported-versions.php>`_

So, if you are now running your PHP web apps on Windows/IIS, you can only reach out to the PHP community for support. Note that this applies to `all PHP related components <https://halfblood.pro/who-should-be-contacted-for-php-on-iis-issues-c80b90bd365>`_. Even if you meet an issue (such as incompatibilities) with the closed source IIS components, you are not likely to receive assistance from Microsoft.

To avoid all the hurdles, you should migrate to Linux.
