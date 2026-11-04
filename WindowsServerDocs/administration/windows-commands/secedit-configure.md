---
layout: Conceptual
title: secedit configure | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/secedit-configure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the secedit configure command, which allows you to configure the current system settings using security settings stored in a database.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ac024157-8eb4-1c2c-5234-2794543972a0
document_version_independent_id: a65a4531-d160-a164-8a10-f7a399c7b80f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/secedit-configure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/secedit-configure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/secedit-configure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ea4cfda7-a380-ffdc-837e-641d7d870b03
---

# secedit configure | Microsoft Learn

Allows you to configure the current system settings using security settings stored in a database.

## Syntax

```
secedit /configure /db <database file name> [/cfg <configuration file name>] [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /db | Required. Specifies the path and file name of the database containing the stored configuration. If the file name specifies a database that hasn't had a security template (as represented by the configuration file) associated with it, the `/cfg <configuration file name>` option must also be specified. |
| /cfg | Specifies the path and file name for the security template that will be imported into the database for analysis. This option is only valid when used with the `/db <database file name>` parameter. If this parameter isn't also specified, the analysis is performed against any configuration already stored in the database. |
| /overwrite | Specifies whether the security template in the **/cfg** parameter should overwrite any template or composite template that is stored in the database, instead of appending the results to the stored template. This option is only valid when the `/cfg <configuration file name>` parameter is also used. If this parameter isn't also specified, the template in the **/cfg** parameter is appended to the stored template. |
| /areas | Specifies the security areas to be applied to the system. If this parameter is not specified, all security settings defined in the database are applied to the system. To configure multiple areas, separate each area by a space. The following security areas are supported:<br>- **securitypolicy:** Local policy and domain policy for the system, including account policies, audit policies, security options, and so on.<br>- **group\_mgmt:** Restricted group settings for any groups specified in the security template.<br>- **user\_rights:** User logon rights and granting of privileges.<br>- **regkeys:** Security on local registry keys.<br>- **filestore:** Security on local file storage.<br>- **services:** Security for all defined services. |
| /log | Specifies the path and file name of the log file to be used in the process. If you don't specify a file location, the default log file, `<systemroot>\Documents and Settings\<UserAccount>\My Documents\Security\Logs\<databasename>.log` is used. |
| /quiet | Suppresses screen and log output. You can still view analysis results by using the Security Configuration and Analysis snap-in to the Microsoft Management Console (MMC). |

## Examples

To perform the analysis for the security parameters on the security database, *SecDbContoso.sdb*, and then direct the output to the file *SecAnalysisContosoFY11*, including prompts to verify the command ran correctly, type:

```
secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /log C:\Security\FY11\SecAnalysisContosoFY11.log
```

To incorporate changes required by the analysis process on the *SecContoso.inf* file, and then to direct the output to the existing file, *SecAnalysisContosoFY11*, without prompting, type:

```
secedit /configure /db C:\Security\FY11\SecDbContoso.sdb /cfg SecContoso.inf /overwrite /log C:\Security\FY11\SecAnalysisContosoFY11.xml /quiet
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [secedit /analyze](secedit-analyze)
- [secedit /export](secedit-export)
- [secedit /generaterollback](secedit-generaterollback)
- [secedit /import](secedit-import)
- [secedit /validate](secedit-validate)