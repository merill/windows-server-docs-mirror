---
layout: Conceptual
title: secedit commands | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/secedit
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the secedit commands, which compare your current security configurations against specified security templates.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4f36797f-df17-1220-a5db-85f13304302c
document_version_independent_id: d6240630-090c-8845-bfa7-9271ebc29c5c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/secedit.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/secedit
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/secedit.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 69321676-32cb-c6cc-8751-4cacce57eeb4
---

# secedit commands | Microsoft Learn

Configures and analyzes system security by comparing your current security configuration against specified security templates.

Note

The Microsoft Management Console (MMC) and the Security Configuration and Analysis snap-in are not available on Server Core.

## Syntax

```
secedit /analyze
secedit /configure
secedit /export
secedit /generaterollback
secedit /import
secedit /validate
```

### Parameters

| Parameter | Description |
| --- | --- |
| [secedit /analyze](secedit-analyze) | Allows you to analyze current systems settings against baseline settings that are stored in a database. The analysis results are stored in a separate area of the database and can be viewed in the Security Configuration and Analysis snap-in. |
| [secedit /configure](secedit-configure) | Allows you to configure a system with security settings stored in a database. |
| [secedit /export](secedit-export) | Allows you to export security settings stored in a database. |
| [secedit /generaterollback](secedit-generaterollback) | Allows you to generate a rollback template with respect to a configuration template. |
| [secedit /import](secedit-import) | Allows you to import a security template into a database so that the settings specified in the template can be applied to a system or analyzed against a system. |
| [secedit /validate](secedit-validate) | Allows you to validate the syntax of a security template. |

#### Remarks

- If there is no filepath specified, all filenames will default to the current directory.
- Your analysis results are stored in a separate area of the database and can be viewed in the Security Configuration and Analysis snap-in to the MMC.
- If your security templates are created by using the Security Template snap-in, and if you run the Security Configuration and Analysis snap-in against those templates, the following files are created:

    | File | Description |
    | --- | --- |
    | scesrv.log | - **Location:**`%windir%\security\logs`<br>    - **Created by:** Operating system<br>    - **File type:** Text<br>    - **Refresh rate:** Overwritten when `secedit analyze`, `secedit configure`, `secedit export` or `secedit import` is run.<br>    - **Content:** Contains the results of the analysis grouped by policy type. |
    | *user-selected name*.sdb | - **Location:**`%windir%\<user account>\Documents\Security\Database`<br>    - **Created by:** Running the Security Configuration and Analysis snap-in<br>    - **File type:** Proprietary<br>    - **Refresh rate:** Updated whenever a new security template is created.<br>    - **Content:** Local security policies and user-created security templates. |
    | *user-selected name*.log | - **Location:** User-defined, but defaults to `%windir%\<user account>\Documents\Security\Logs`<br>    - **Created by:** Running the `secedit analyze` or `secedit configure` commands, or by using the Security Configuration and Analysis snap-in.<br>    - **File type:** Text<br>    - **Refresh rate:** Overwritten when `secedit analyze` or `secedit configure` is run, or by using the Security Configuration and Analysis snap-in.<br>    - **Content:** Log file name, date and time, and the results of the analysis or investigation. |
    | *user-selected name*.inf | - **Location:**`%windir%\*<user account>\Documents\Security\Templates`<br>    - **Created by:** Running the Security Template snap-in.<br>    - **File type:** Text<br>    - **Refresh rate:** Overwritten each time the security template is updated.<br>    - **Content:** Contains the set up information for the template for each policy selected using the snap-in. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)