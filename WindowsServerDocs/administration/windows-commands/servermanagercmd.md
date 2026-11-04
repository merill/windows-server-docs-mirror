---
layout: Conceptual
title: servermanagercmd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/servermanagercmd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the servermanagercmd command, which installs and removes roles, role services, and features.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 6062bcb6-3aa2-b8b2-4a19-83581983dbe9
document_version_independent_id: 6e6854e3-bab7-fb4b-3a8f-9fff46e946ad
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/servermanagercmd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/servermanagercmd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/servermanagercmd.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 63aada8c-8e57-84ca-6b8e-09d9bf0a6d7d
---

# servermanagercmd | Microsoft Learn

Installs and removes roles, role services, and features. Also displays the list of all roles, role services, and features available, and shows which are installed on this computer.

Important

This command, servermanagercmd, has been deprecated and it's not guaranteed to be supported in future releases of Windows. We recommend instead that you use the Windows PowerShell cmdlets that are available for Server Manager. For more information, see [Install or Uninstall Roles, Role Services, or Features](/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features).

## Syntax

```
servermanagercmd -query [[[<drive>:]<path>]<query.xml>] [-logpath [[<drive>:]<path>]<log.txt>]
servermanagercmd -inputpath  [[[<drive>:]<path>]<answer.xml>] [-resultpath <result.xml> [-restart] | -whatif] [-logpath [[<drive>:]<path>]<log.txt>]
servermanagercmd -install <id> [-allSubFeatures] [-resultpath [[<drive>:]<path>]<result.xml> [-restart] | -whatif] [-logpath [[<Drive>:]<path>]<log.txt>]
servermanagercmd -remove <id> [-resultpath <result.xml> [-restart] | -whatif] [-logpath  [[<drive>:]<path>]<log.txt>]
servermanagercmd [-help | -?]
servermanagercmd -version
```

### Parameters

| Parameter | Description |
| --- | --- |
| -query `[[[<drive>:]<path>]<query.xml>]` | Displays a list of all roles, role services, and features installed and available for installation on the server. You can also use the short form of this parameter, **-q**. If you want the query results saved to an XML file, specify an XML file to replace `<query.xml>`. |
| -inputpath `[[[<drive>:]<path>]<answer.xml>]` | Installs or removes the roles, role services, and features specified in an XML answer file represented by `<answer.xml>`. You can also use the short form of this parameter, **-p.** |
| -install `<id>` | Installs the role, role service, or feature specified by `<id>`. The identifiers are case-insensitive. Multiple roles, role services, and features must be separated by spaces. The following optional parameters are used with the **-install** parameter:<br>- **-setting**`<SettingName>=<SettingValue>` - Specifies required settings for the installation.<br>- **-allSubFeatures** - Specifies the installation of all subordinate services and features along with the parent role, role service, or feature named in the `<id>` value.<br>    **NOTE**Some role containers do not have a command line identifier to allow installation of all role services. This is the case when role services cannot be installed in the same instance of the Server Manager command. For example, the Federation Service role service of active directory Federation Services and the Federation Service Proxy role service cannot be installed by using the same Server Manager command instance.<br>- **-resultpath**`<result.xml>` - Saves installation results to an XML file represented by `<result.xml>`. You can also use the short form of this parameter, **-r**.<br>    **NOTE**You can't run servermanagercmd with both the **-resultpath** parameter and the **-whatif** parameter specified.<br>- **-restart** - Restarts the computer automatically when installation is complete (if restarting is required by the roles or features installed).<br>- **-whatif** - Displays any operations specified for the **-install** parameter. You can also use the short form of the **-whatif** parameter, **-w**. You can't run **servermanagercmd** with both the **-resultpath** parameter and the **-whatif** parameter specified.<br>- **-logpath**`<[[<drive>:]<path>]<log.txt>>` - Specifies a name and location for the log file, other than the default, `%windir%\temp\servermanager.log`. |
| -remove `<id>` | Removes the role, role service, or feature specified by `<id>`. The identifiers are case-insensitive. Multiple roles, role services, and features must be separated by spaces. The following optional parameters are used with the **-remove** parameter:<br>- **-resultpath**`<[[<drive>:]<path>]result.xml>` - Saves removal results to an XML file represented by `<result.xml>`. You can also use the short form of this parameter, **-r**.<br>    **NOTE**You can't run servermanagercmd with both the **-resultpath** and the **-whatif** parameters specified.<br>- **-restart** - Restarts the computer automatically when removal is complete (if restarting is required by remaining roles or features).<br>- **-whatif** - Displays any operations specified for the -remove parameter. You can also use the short form of the -whatif parameter, **-w**. You can't run servermanagercmd with both the **-resultpath** and the **-whatif** parameters specified.<br>- **-logpath**`<[[<Drive>:]<path>]<log.txt>>` - Specifies a name and location for the log file, other than the default, `%windir%\temp\servermanager.log`. |
| -version | Displays the Server Manager version number. You can also use the short form, **-v**. |
| -help | Displays help in the Command prompt window. You can also use the short form, **-?**. |

## Examples

To display a list of all roles, role services, and features available, and which roles, role services, and features are installed on the computer, type:

```
servermanagercmd -query
```

To install the Web Server (IIS) role, and save the installation results to an XML file represented by *installResult.xml*, type:

```
servermanagercmd -install Web-Server -resultpath installResult.xml
```

To display detailed information about the roles, role services, and features that would be installed or removed, based upon instructions that are specified in an XML answer file represented by *install.xml*, type:

```
servermanagercmd -inputpath install.xml -whatif
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Server Manager overview](/en-us/windows-server/administration/server-manager/server-manager)