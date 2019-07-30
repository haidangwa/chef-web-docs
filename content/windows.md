+++
title = "Chef for Microsoft Windows"
description = "DESCRIPTION"
draft = false

aliases = "/windows.html"

[menu]
  [menu.docs]
    title = "Chef for Microsoft Windows"
    identifier = "chef for microsoft windows/windows.html"
    parent = "getting started/chef on windows guide"
    weight = 10
+++    

[\[edit on
GitHub\]](https://github.com/chef/chef-web-docs/blob/master/chef_master/source/windows.rst)

Overview
========

The Chef Infra Client has specific components that are designed to
support unique aspects of the Microsoft Windows platform, including
Windows PowerShell, Internet Information Services (IIS), and SQL Server.

{{% windows_install_overview %}}

Setting up Windows Workstations
===============================

To set up your Windows workstation follow the steps on [Chef for
Microsof Windows](/dk_windows/)

Install Chef Infra Client on Windows Nodes
==========================================

{{% chef_client_summary %}}

This command has the following syntax:

``` bash
$ chef-client OPTION VALUE OPTION VALUE ...
```

This command has the following options specific to Microsoft Windows:

`-A`, `--fatal-windows-admin-check`

:   Cause a Chef Infra Client run to fail when Chef Infra Client does
    not have administrator privileges in Microsoft Windows.

`-d`, `--daemonize`

:   Run the executable as a daemon.

    This option is only available on machines that run in UNIX or Linux
    environments. For machines that are running Microsoft Windows that
    require similar functionality, use the `chef-client::service` recipe
    in the `chef-client` cookbook:
    <https://supermarket.chef.io/cookbooks/chef-client>. This will
    install a Chef Infra Client service under Microsoft Windows using
    the Windows Service Wrapper.

System Requirements
-------------------

The recommended minimum amount of RAM available to Chef Infra Client
during a Chef Infra Client run is 512MB. Each node and workstation must
have access to Chef Infra Server via HTTPS. The Chef Infra Client can be
used to manage machines that run on the following versions of Microsoft
Windows:

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Operating System</th>
<th>Architecture</th>
<th>Version</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Windows</td>
<td><code>x86</code>, <code>x64</code></td>
<td><code>7</code>, <code>8.1</code>, <code>2008 R2</code>, <code>2012</code>, <code>2012 R2</code>, <code>2016</code>, <code>10 (all channels except "insider" builds)</code>, <code>2019 (Long-term servicing channel (LTSC), both Desktop Experience and Server Core)</code></td>
</tr>
</tbody>
</table>

After Chef Infra Client is installed, it is located at `C:\chef`. The
main configuration file for Chef Infra Client is located at
`C:\chef\client.rb`.

Information for Windows Users
-----------------------------

### Set the System Ruby

To set the system Ruby for the Microsoft Windows platform [the steps
described for all platforms are true](/install_dk.html#set-system-ruby),
but then require the following manual edits to the
`chef shell-init bash` output for the Microsoft Windows platform:

1.  Add quotes around the variable assignment strings.
2.  Convert `C:/` to `/c/`.
3.  Save those changes.

### Run With Elevated Privileges

{{% ctl_chef_client_elevated_privileges %}}

{{% ctl_chef_client_elevated_privileges_windows %}}

### config.rb

When running Microsoft Windows, the config.rb file is located at
`%HOMEDRIVE%:%HOMEPATH%\.chef` (e.g. `c:\Users\<username>\.chef`). If
this path needs to be scripted, use `%USERPROFILE%\.chef`.

### Spaces and Directories

{{% windows_spaces_and_directories %}}

### Top-level Directory Names

{{% windows_top_level_directory_names %}}

### PATH System Variable

{{% windows_environment_variable_path %}}

### Proxy Settings

{{% proxy_windows %}}

Install Chef Infra Client using knife-windows
---------------------------------------------

{{% knife_windows_summary %}}

Se the [knife windows](/knife_windows/) for more information.

### Ports

{{% knife_windows_winrm_ports %}}

### Msiexec.exe

{{% windows_msiexec %}}

### ADDLOCAL Options

{{% windows_msiexec_addlocal %}}

Install Chef Infra Client using the MSI Installer
-------------------------------------------------

A Microsoft Installer Package (MSI) is available for installing Chef
Infra Client on a Microsoft Windows machine from [Chef
Downloads](https://downloads.chef.io/).

### Enable as a Scheduled Task

{{% install_chef_client_windows_as_scheduled_task %}}

Install Chef Infra Client using an Existing Process
---------------------------------------------------

{{% windows_install_system_center %}}

Windows Cookbooks
=================

Some of the most popular Chef-maintained cookbooks that contain custom
resources useful when configuring machines running Microsoft Windows are
listed below:

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 75%" />
</colgroup>
<thead>
<tr class="header">
<th>Cookbook</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="https://github.com/chef-cookbooks/iis">iis Cookbook</a></td>
<td>The <code>iis</code> cookbook is used to install and configure Internet Information Services (IIS).</td>
</tr>
<tr class="even">
<td><a href="https://github.com/chef-cookbooks/iis_urlrewrite">iis_urlrewrite Cookbook</a></td>
<td>This cookbook downloads and installs the IIS URL Rewrite 2.0 extension into Microsoft Internet Information Server.</td>
</tr>
<tr class="odd">
<td><a href="https://github.com/chef-cookbooks/powershell">PowerShell Cookbook</a></td>
<td>Installs and configures PowerShell 2.0, 3.0, 4.0 or 5.0.</td>
</tr>
<tr class="even">
<td><a href="https://github.com/chef-cookbooks/miccrosoft_azure">Microsoft Azure Cookbook</a></td>
<td>This cookbook provides resources and providers to create an manage Microsoft Azure components.</td>
</tr>
<tr class="odd">
<td><a href="https://github.com/chef-cookbooks/vcruntime">Microsoft Visual C++ Runtime Cookbook</a></td>
<td>Installs Microsoft Visual C++ runtime version 6 (2005), 9 (2008), 10 (2010), 11 (2012), 12 (2013), 14 (2015) or 15 (2017) on Windows.</td>
</tr>
<tr class="even">
<td><a href="https://github.com/chef-cookbooks/mingw">Mingw Cookbook</a></td>
<td>Installs <code>msys/mingw</code> compiler toolchains on windows.</td>
</tr>
<tr class="odd">
<td><a href="https://github.com/chef-cookbooks/webpi">Webpi Cookbook</a></td>
<td>The <code>webpi</code> cookbook is used to run the Microsoft Web Platform Installer (WebPI).</td>
</tr>
<tr class="even">
<td><a href="https://github.com/chef-cookbooks/windows">Windows Cookbook</a></td>
<td>The <code>windows</code> cookbook is used to configure auto run, batch, reboot, enable built-in operating system packages, configure Microsoft Windows packages, reboot machines, and more.</td>
</tr>
<tr class="odd">
<td><a href="https://github.com/chef-cookbooks/windows_dns">Windows_dns Cookbook</a></td>
<td>This cookbook provides a resource for managing DNS on Windows hosts.</td>
</tr>
<tr class="even">
<td><a href="https://github.com/chef-cookbooks/windows_uac">windows_uac Cookbook</a></td>
<td>The <code>windows_uac</code> resource configures UAC on Windows hosts by setting registry keys at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System</code></td>
</tr>
</tbody>
</table>

Community Supported Windows Projects
------------------------------------

Two community supports two provisioners for Kitchen:

-   [kitchen-dsc](https://github.com/test-kitchen/kitchen-dsc)
-   [kitchen-pester](https://github.com/test-kitchen/kitchen-pester)

Windows Resources
=================

{{% resources_common %}}

Windows Resources
-----------------

Chef Infra provides a growing number of Windows-specific resources.

-   [Chocolatey_config](/resource_chocolatey_config/)
-   [Chocolatey_package](/resource_chocolatey_package/)
-   [Chocolatey_source](/resource_chocolatey_package/)
-   [dsc_resource](/resource_dsc_resource/)
-   [resource_registry_key](/resource_registry_key/)
-   [Windows_ad_join](/resource_windows_ad_join/)
-   [Windows_ad_join](/resource_windows_ad_join.rst)
-   [Windows_auto_run](/resource_windows_auto_run.rst)
-   [Windows_certificate](/resource_windows_certificate.rst)
-   [Windows_dfs_folder](/resource_windows_dfs_folder.rst)
-   [Windows_dfs_namespace](/resource_windows_dfs_namespace.rst)
-   [Windows_dfs_server](/resource_windows_dfs_server.rst)
-   [Windows_dns_record](/resource_windows_dns_record.rst)
-   [Windows_dns_zone](/resource_windows_dns_zone.rst)
-   [Windows_env](/resource_windows_env.rst)
-   [Windows_feature_dism](/resource_windows_feature_dism.rst)
-   [Windows_feature_powershell](/resource_windows_feature_powershell.rst)
-   [Windows_feature](/resource_windows_feature.rst)
-   [Windows_firewall_rule](/resource_windows_firewall_rule.rst)
-   [Windows_font](/resource_windows_font.rst)
-   [Windows_package](/resource_windows_package.rst)
-   [Windows_pagefile](/resource_windows_pagefile.rst)
-   [Windows_path](/resource_windows_path.rst)
-   [Windows_windows_printer_port](/resource_windows_printer_port.rst)
-   [Windows_printer](/resource_windows_printer.rst)
-   [Windows_service](/resource_windows_service.rst)
-   [Windows_share](/resource_windows_share.rst)
-   [Windows_shortcut](/resource_windows_shortcut.rst)
-   [Windows_task](/resource_windows_task.rst)
-   [Windows_uac](/resource_windows_uac.rst)
-   [Windows_workgroup](/resource_windows_workgroup.rst)

Windows Compatible Resources
----------------------------

The most popular core resources in Chef Infra Client work the same way
in Microsoft Windows as they do on any UNIX- or Linux-based platform.

-   [cookbook_file](/resource_cookbook_file/)
-   [directory](/resource_directory/)
-   [env](/resource_env/)
-   [execute](/resource_execute/)
-   [file](/resource_file/)
-   [group](/resource_group/)
-   [http_request](/resource_http_request/)
-   [link](/resource_link/)
-   [mount](/resource_mount/)
-   [package](/resource_package/)
-   [remote_directory](/resource_remote_directory/)
-   [remote_file](/resource_remote_file/)
-   [ruby_block](/resource_ruby_block/)
-   [service](/resource_service/)
-   [template](/resource_template/)
-   [user](/resource_user/)

The file-based resources have attributes that support unique
requirements within the Microsoft Windows platform, including `inherits`
(for file inheritance), `mode` (for octal modes), and `rights` (for
access control lists, or ACLs).

-   [cookbook_file](/resource_cookbook_file/)
-   [file](/resource_file/)
-   [remote_file](/resource_remote_file/)
-   [template](/resource_template/)