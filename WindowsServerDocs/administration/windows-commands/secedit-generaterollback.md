---
layout: Conceptual
title: secedit generaterollback | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/secedit-generaterollback
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the secedit generaterollback command, which allows you to generate a rollback template for a specified configuration template.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 72f0e378-2dec-fd8f-8b80-14db8f6e31ce
document_version_independent_id: 9aa4796d-d041-a29a-66d2-4246c0fce2cc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/secedit-generaterollback.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/secedit-generaterollback
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/secedit-generaterollback.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6bcd7cc2-fc46-cee9-f54a-cf1bbd917800
---

# secedit generaterollback | Microsoft Learn

Allows you to generate a rollback template for a specified configuration template. If an existing rollback template exists, running this command again will overwrite the existing information.

Successfully running this command logs the mismatches between the specified security template the security policy configuration into the scesrv.log file.

## Syntax

```
secedit /generaterollback /db <database file name> /cfg <configuration file name> /rbk <rollback template file name> [/log <log file name>] [/quiet]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /db | Required. Specifies the path and file name of the database containing the stored configuration against which the analysis is performed. If the file name specifies a database that hasn't had a security template (as represented by the configuration file) associated with it, the `/cfg <configuration file name>` option must also be specified. |
| /cfg | Required. Specifies the path and file name for the security template that will be imported into the database for analysis. This option is only valid when used with the `/db <database file name>` parameter. If this parameter isn't also specified, the analysis is performed against any configuration already stored in the database. |
| /rbk | Required. Specifies a security template into which the rollback information is written. Security templates are created using the Security Templates snap-in. Rollback files can be created with this command. |
| /log | Specifies the path and file name of the log file to be used in the process. If you don't specify a file location, the default log file, `<systemroot>\Documents and Settings\<UserAccount>\My Documents\Security\Logs\<databasename>.log` is used. |
| /quiet | Suppresses screen and log output. You can still view analysis results by using the Security Configuration and Analysis snap-in to the Microsoft Management Console (MMC). |

## Examples

To create the rollback configuration file, for the previously created *SecTmplContoso.inf* file, while saving the original settings, and then write out the action to the *SecAnalysisContosoFY11* log file, type:

```
secedit /generaterollback /db C:\Security\FY11\SecDbContoso.sdb /cfg sectmplcontoso.inf /rbk sectmplcontosoRBK.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [secedit /analyze](secedit-analyze)
- [secedit /configure](secedit-configure)
- [secedit /export](secedit-export)
- [secedit /import](secedit-import)
- [secedit /validate](secedit-validate)