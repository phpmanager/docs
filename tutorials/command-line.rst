Managing PHP installations with PHP Manager command line
========================================================

By `Ruslan Yakushev`_

This article describes how to use PHP Manager command line.

Prerequisites
-------------
Make sure you install PHP Manager for IIS properly following
:doc:`/getting-started/installation` .

After installation is complete, launch the Windows PowerShell command line
window in an evelated mode (right-click and select "Run as Administrator").
After that type the following command:

.. code-block:: text

   Add-PsSnapin PHPManagerSnapin

This will register the PHP Manager powershell cmdlets that can be used to setup
and configure PHP installation from command line.

To get the list of available cmdlets use Get-Command cmdlet:

.. code-block:: text

   PS C:\Users\Administrator> Get-Command -Module phpmanagersnapin

   CommandType     Name                                                Definition
   -----------     ----                                                ----------
   Cmdlet          Get-PHPConfiguration                                Get-PHPConfiguration [-SiteName <String>] [-Virt...
   Cmdlet          Get-PHPExtension                                    Get-PHPExtension [[-Name] <String>] [[-Status] <...
   Cmdlet          Get-PHPSetting                                      Get-PHPSetting [[-Name] <String>] [-Section <Str...
   Cmdlet          Get-PHPVersion                                      Get-PHPVersion [[-HandlerName] <String>] [[-Vers...
   Cmdlet          New-PHPSetting                                      New-PHPSetting [-Name] <String> [-Value] <String...
   Cmdlet          New-PHPVersion                                      New-PHPVersion [-ScriptProcessor] <String> [-Sit...
   Cmdlet          Remove-PHPSetting                                   Remove-PHPSetting [-Name] <String> [-Force] [-Si...
   Cmdlet          Set-PHPExtension                                    Set-PHPExtension [-Name] <String[]> [-Status] <P...
   Cmdlet          Set-PHPSetting                                      Set-PHPSetting [-Name] <String> [-Value] <String...
   Cmdlet          Set-PHPVersion                                      Set-PHPVersion [-HandlerName] <String> [-SiteNam...

To learn what each cmdlet does use Get-Help cmdlet:

.. code-block:: text

   PS C:\Users\Administrator> get-help Get-PHPExtension

   NAME
       Get-PHPExtension

   SYNOPSIS
       Gets the list of PHP extensions available in the currently active PHP version.

   SYNTAX
      Get-PHPExtension [[-Name] <String>] [[-Status] <PHPExtensionStatus>] [-SiteName <String>] [-VirtualPath <String>] [
       <CommonParameters>]

   DESCRIPTION
       The Get-PHPExtension cmdlet outputs the list of all PHP extensions available in the currently active PHP version. T
       he list can be filtered by extension name and by the status (enabled or disabled).

   RELATED LINKS
       Set-PHPExtension

   REMARKS
       To see the examples, type: "get-help Get-PHPExtension -examples".
       For more information, type: "get-help Get-PHPExtension -detailed".
       For technical information, type: "get-help Get-PHPExtension -full".

Registering PHP with IIS
------------------------
To register a new PHP version with IIS, first you need to download the zip
archive with PHP binaries from http://windows.php.net/ and then extract the
files from it into a folder of your choice.

.. note:: You can also install PHP by using Web Platform Installer or the
   Windows installer from http://windows.php.net/ - the PHP Manager can be used
   to manage those PHP installations as well.

In the PowerShell command line window type while providng the absolute path to
the location where you have extracted PHP binaries:

.. code-block:: text

   New-PHPVersion -ScriptProcessor "<absolute path to php-cgi.exe>"

To get information about the registered PHP version use
``Get-PHPConfiguraiton`` command:

.. code-block:: text

   PS C:\Users\Administrator> Get-PHPConfiguration

   HandlerName              : php-5.3.6
   Version                  : 5.3.6
   ScriptProcessor          : C:\php\536\php-cgi.exe
   HandlerType              : Local
   ErrorLog                 : C:\Windows\Temp\php-5.3.6_errors.log
   PHPIniFilePath           : C:\php\536\php.ini
   InstalledExtensionsCount : 35
   EnabledExtensionsCount   : 9

Switching between PHP versions
------------------------------
To get the list of PHP versions registerd with IIS use the ``Get-PHPVersion``
command:

.. code-block:: text

   PS C:\Users\Administrator> Get-PHPVersion

   HandlerName                   Version                       ScriptProcessor                                      Active
   -----------                   -------                       ---------------                                      ------
   php-5.3.6                     5.3.6                         C:\php\536\php-cgi.exe                                 True
   PHP53_via_FastCGI             5.3.6                         C:\Program Files (x86)\PHP...                         False

To switch the version use ``Set-PHPVersion``. After that use ``Get-PHPVersion``
command to check if the change took effect:

.. code-block:: text

   PS C:\Users\Administrator> Set-PHPVersion -HandlerName php53_via_fastcgi
   PS C:\Users\Administrator> Get-PHPVersion

   HandlerName                   Version                       ScriptProcessor                                      Active
   -----------                   -------                       ---------------                                      ------
   PHP53_via_FastCGI             5.3.6                         C:\Program Files (x86)\PHP...                          True
   php-5.3.6                     5.3.6                         C:\php\536\php-cgi.exe                                False

Configuring PHP settings
------------------------
To get the list PHP configuration settings and their values use
``Get-PHPSetting`` command. By default it will output a long list of all
available settings, so it is a good idea to filter the output by using wildcard
pattern for setting name or section name. For example, the following command
will output all settings from MySQL sesion:

.. code-block:: text

   PS C:\Users\Administrator> Get-PHPSetting -Section mysql

   Name                                    Value                                   Section
   ----                                    -----                                   -------
   mysql.allow_local_infile                On                                      MySQL
   mysql.allow_persistent                  On                                      MySQL
   mysql.cache_size                        2000                                    MySQL
   mysql.max_persistent                    -1                                      MySQL
   mysql.max_links                         -1                                      MySQL
   mysql.default_port                      <Not set>                               MySQL
   mysql.default_socket                    <Not set>                               MySQL
   mysql.default_host                      <Not set>                               MySQL
   mysql.default_user                      <Not set>                               MySQL
   mysql.default_password                  <Not set>                               MySQL
   mysql.connect_timeout                   60                                      MySQL
   mysql.trace_mode                        Off                                     MySQL

This command will output all settings which have word "error" in their names:

.. code-block:: text

   PS C:\Users\Administrator> Get-PHPSetting -Name *error*

   Name                                    Value                                   Section
   ----                                    -----                                   -------
   error_reporting                         E_ALL & ~E_DEPRECATED                   PHP
   display_errors                          Off                                     PHP
   display_startup_errors                  Off                                     PHP
   log_errors                              On                                      PHP
   log_errors_max_len                      1024                                    PHP
   ignore_repeated_errors                  Off                                     PHP
   track_errors                            Off                                     PHP
   html_errors                             Off                                     PHP
   mssql.min_error_severity                10                                      MSSQL
   error_log                               C:\Windows\temp\php53_errors.log        WebPIChanges

To change the value of an existing setting use ``Set-PHPSetting`` command:

.. code-block:: text

   Set-PHPSetting -Name display_errors -Value On

To add a new setting use ``New-PHPSetting`` command:

.. code-block:: text

   New-PHPSetting -Name wincache.debuglevel -Value 101 -Section wincache

To remove an existing setting use ``Remove-PHPSetting`` command.

Enabling and Disabling PHP extensions
-------------------------------------
To get the list of currently installed extension use ``Get-PHPExtension``
command:

.. code-block:: text

   PS C:\Users\Administrator> Get-PHPExtension

   Name                                                                                 Status
   ----                                                                                 ------
   php_mysql.dll                                                                        Enabled
   php_mysqli.dll                                                                       Enabled
   php_mbstring.dll                                                                     Enabled
   php_gd2.dll                                                                          Enabled
   php_gettext.dll                                                                      Enabled
   php_curl.dll                                                                         Enabled
   php_exif.dll                                                                         Enabled
   php_xmlrpc.dll                                                                       Enabled
   php_openssl.dll                                                                      Enabled
   php_soap.dll                                                                         Enabled
   php_pdo_mysql.dll                                                                    Enabled
   php_pdo_sqlite.dll                                                                   Enabled
   php_pdo_sqlsrv.dll                                                                   Enabled
   php_imap.dll                                                                         Enabled
   php_tidy.dll                                                                         Enabled
   php_wincache.dll                                                                     Enabled
   php_bz2.dll                                                                         Disabled
   php_enchant.dll                                                                     Disabled
   php_fileinfo.dll                                                                    Disabled
   php_gmp.dll                                                                         Disabled
   php_interbase.dll                                                                   Disabled
   php_intl.dll                                                                        Disabled
   php_ldap.dll                                                                        Disabled
   php_oci8.dll                                                                        Disabled
   php_oci8_11g.dll                                                                    Disabled
   php_pdo_firebird.dll                                                                Disabled
   php_pdo_oci.dll                                                                     Disabled
   php_pdo_odbc.dll                                                                    Disabled
   php_pdo_pgsql.dll                                                                   Disabled
   php_pgsql.dll                                                                       Disabled
   php_shmop.dll                                                                       Disabled
   php_snmp.dll                                                                        Disabled
   php_sockets.dll                                                                     Disabled
   php_sqlite.dll                                                                      Disabled
   php_sqlite3.dll                                                                     Disabled
   php_sybase_ct.dll                                                                   Disabled
   php_xsl.dll                                                                         Disabled

To enable or disable an extension use ``Set-PHPExtension`` command:

.. code-block:: text

   Set-PHPExtension -Name php_enchant.dll -Status enabled

To enable all pdo extension use this command:

.. code-block:: text

   PS C:\Users\Administrator> Get-PHPExtension -Name *pdo* | Set-PHPExtension -Status enabled
   PS C:\Users\Administrator> Get-PHPExtension -Name *pdo*

   Name                                                                               Status
   ----                                                                               ------
   php_pdo_mysql.dll                                                                  Enabled
   php_pdo_sqlite.dll                                                                 Enabled
   php_pdo_sqlsrv.dll                                                                 Enabled
   php_pdo_firebird.dll                                                               Enabled
   php_pdo_oci.dll                                                                    Enabled
   php_pdo_odbc.dll                                                                   Enabled
   php_pdo_pgsql.dll                                                                  Enabled

Managing PHP on a site or a folder level
----------------------------------------
All the PHP Manager cmdlets described in above examples can be applied on a
site, application or a folder levels in IIS. This can be done by using the
``SiteName`` and ``VirtualPath`` parameters. The following example demonstrates
how to change the PHP version for the directory "test" under "Default Web
Site":

.. code-block:: text

   PS C:\Users\Administrator> Get-PHPVersion -SiteName "Default Web Site" -VirtualPath "test"

   HandlerName                   Version                       ScriptProcessor                                      Active
   -----------                   -------                       ---------------                                      ------
   php-5.2.17                    5.2.17                        C:\php\5217\php-cgi.exe                                True
   php-5.3.6                     5.3.6                         C:\php\536\php-cgi.exe                                False

   PS C:\Users\Administrator> Set-PHPVersion -HandlerName php-5.3.6 -SiteName "Default Web Site" -VirtualPath "test"
   PS C:\Users\Administrator> Get-PHPVersion -SiteName "Default Web Site" -VirtualPath "test"

   HandlerName                   Version                       ScriptProcessor                                      Active
   -----------                   -------                       ---------------                                      ------
   php-5.3.6                     5.3.6                         C:\php\536\php-cgi.exe                                 True
   php-5.2.17                    5.2.17                        C:\php\5217\php-cgi.exe                               Fals

Related Resources
-----------------

- :doc:`/getting-started/installation`
- :doc:`/tutorials/user-interface`
