---
layout: Conceptual
title: secedit export | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/secedit-export
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the secedit export, which exports security settings stored in a database configured with security templates.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 535f1d4b-c5ca-fdf4-18d3-9fa2726be165
document_version_independent_id: ee2492e3-d290-3f48-8114-ae6489615374
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/secedit-export.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/secedit-export
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/secedit-export.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 08d0cea9-23ff-cb44-3956-83be5aec9d00
---

# secedit export | Microsoft Learn

Exports security settings stored in a database configured with security templates. You can use this command to backup your security policies on a local computer, in addition to importing the settings to another computer.

## Syntax

```
secedit /export [/db <database file name>] [/mergedpolicy] /cfg <configuration file name> [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /db | Requires that you specify the path and file name of the database containing the stored configuration when exporting to a location other than the default. If not specified, the system security database will be stored in **%windir%\security\database**. If the file name specifies a database that hasn't had a security template (as represented by the configuration file) associated with it, the `/cfg <configuration file name>` option must also be specified for the export. |
| /mergedpolicy | Merges and exports domain and local policy security settings. |
| /cfg | Required. Specifies the path and file name for the security template that will be imported into the database for analysis. This option is only valid when used with the `/db <database file name>` parameter. If this parameter isn't also specified, the analysis is performed against any configuration already stored in the database. |
| /areas | Specifies the security areas to be applied to the system. If this parameter is not specified, all security settings defined in the database are applied to the system. To configure multiple areas, separate each area by a space. The following security areas are supported:<br>- **securitypolicy:** Local policy and domain policy for the system, including account policies, audit policies, security options, and so on.<br>- **group\_mgmt:** Restricted group settings for any groups specified in the security template.<br>- **user\_rights:** User logon rights and granting of privileges.<br>- **regkeys:** Security on local registry keys.<br>- **filestore:** Security on local file storage.<br>- **services:** Security for all defined services. |
| /log | Specifies the path and file name of the log file to be used in the process. If you don't specify a file location, the default log file, `<systemroot>\Documents and Settings\<UserAccount>\My Documents\Security\Logs\<databasename>.log` is used. |
| /quiet | Suppresses screen and log output. You can still view analysis results by using the Security Configuration and Analysis snap-in to the Microsoft Management Console (MMC). |

## Examples

To export the security database and the domain security policies to an inf file, and then import that file to a different database in order to replicate the security policy settings on another computer, type:

```
secedit /export /db C:\Security\FY11\SecDbContoso.sdb /mergedpolicy /cfg SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log /quiet
```

To import your example file to a different database on another computer, type:

```
secedit /import /db C:\Security\FY12\SecDbContoso.sdb /cfg SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY12.log /quiet
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [secedit /analyze](secedit-analyze)
- [secedit /configure](secedit-configure)
- [secedit /generaterollback](secedit-generaterollback)
- [secedit /import](secedit-import)
- [secedit /validate](secedit-validate)