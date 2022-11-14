Project History
===============

By `Lex Li`_

This article describes the history of PHP Manager.

.. contents:: In this article:
  :local:
  :depth: 1

Overview of PHP on IIS
----------------------
PHP has been a popular programming platform for web applications. It has been
integrated to IIS a long time ago by the PHP community.

However, the initial work used IIS ISAPI to integrate, and had stability
issues.

In 2006, Microsoft announced a new initiative to support PHP on IIS officially
via FastCGI protocol [1]_ .

It took about a year for that to finish and then the ISAPI module became
obsolete.

The same technology was later used in Windows Azure (renamed to Microsoft Azure
today) to support PHP web apps.

Initial Releases from Ruslan Yakushev
-------------------------------------
From the code commit history we can see that Ruslan made the first commit on
August 9, 2010. However, the initial code seems to be a little bit older than
that. [2]_

This project is an IIS Manager extension (plus PowerShell snapin) to better
support PHP configuration system via IIS Manager experience. So it was quite
popular.

Ruslan worked for Microsoft, and was in IIS team (Product Manager) before later moved to other positions.

The last commit he made was on December 13, 2013.

The releases from him were 1.0.x-1.2.1.

Chaos in The Coming Years
-------------------------
There were many factors that made the situation tough for PHP Manager users,

* PHP started to evolve fast. The 7.x releases came quickly and things started
  to age.
* Windows started to release more often. New IIS releases (8.x and 10.x) were
  not quite well supported.
* .NET Framework 4.x introduced breaking changes that also affected the old
  installers.
* CodePlex shutdown took effect a few months ago, which closed down the home
  page for this project.
* Other noticeable changes.

There were several attempts to help out the users, but they only provided
temporary solutions [3]_ , and none aimed to revive the project and bring it to
a healthy state.

Noticeably, there were installers for "1.3.0" and "1.4.0" from
SkyDrive/OneDrive, but the actual source code was not available.

There was an installer for 1.5.0, but it only aims for IIS 10.

New Repository for 2.0 Release and Above
----------------------------------------
To fully take over the project and make it healthy again, Lex Li did the
following,

* Fork the code on GitHub.
* Set up AppVeyor to compile the code and generate new installers.
* Migrate the documentation to the new homepage.
* Fix known issues.
* Test on all supported platforms.

The 2.0 release was published in August, 2018. [4]_ Other 2.x releases were
published with additional updates.

.. rubric:: Footnotes

.. [1] http://mvolo.com/fastcgi-for-iis-60-is-released-on-download-center/
.. [2] http://ruslany.net/tag/php-manager/
.. [3] https://github.com/phpmanager/phpmanager/issues/1
.. [4] https://www.phpmanager.xyz
