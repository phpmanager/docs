Supported Platforms
===================

By `Lex Li`_

This article describes what are the supported platforms.

PHP on Windows Status
---------------------
There are two facts you should keep in mind that,

* Microsoft discontinued its support of PHP 8.0 and above on Windows as
  `announced on July 9, 2020 <https://news-web.php.net/php.internals/110907>`_
* All PHP versions below 8.0 are
  `now end of life <https://www.php.net/supported-versions.php>`_

So, if you are now running your PHP web apps on Windows/IIS, you can only rely
on the PHP community for support. Note that this applies to
`all PHP related components <https://docs.lextudio.com/blog/who-should-be-contacted-for-php-on-iis-issues-c80b90bd365>`_.
Even if you meet an issue (such as incompatibilities) with the closed source
IIS components, you are not likely to receive assistance from Microsoft.

To avoid all the hurdles, you'd better migrate PHP web apps to Linux.

Overview
--------
Generally speaking, the installers of PHP Manager are designed to work for all
supported Windows releases from Microsoft.

Platform specific dependencies are listed below. They must be installed in
advance, or the installer might not work properly.

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
