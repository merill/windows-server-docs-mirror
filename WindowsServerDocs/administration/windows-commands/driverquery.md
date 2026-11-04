---
layout: Conceptual
title: driverquery | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/driverquery
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the driverquery command, which enables an administrator to display a list of installed device drivers and their properties.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 93d0c2a5-66da-7556-c45a-924e7d32b55f
document_version_independent_id: e0a221b0-7aaa-df91-c33c-139f8d1ffd8e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/driverquery.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/driverquery
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/driverquery.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c4732367-138c-6771-fdfb-a8e76c68f12c
---

# driverquery | Microsoft Learn

Enables an administrator to display a list of installed device drivers and their properties. If used without parameters, **driverquery** runs on the local computer.

## Syntax

```
driverquery [/s <system> [/u [<domain>\]<username> [/p <password>]]] [/fo {table | list | csv}] [/nh] [/v | /si]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /s `<system>` | Specifies the name or IP address of a remote computer. Do not use backslashes. The default is the local computer. |
| /u `[<domain>]<username>` | Runs the command with the credentials of the user account as specified by *user* or *domain\user*. By default, */s* uses the credentials of the user who is currently logged on to the computer that is issuing the command. **/u** can't be used unless **/s** is specified. |
| /p `<password>` | Specifies the password of the user account that is specified in the **/u** parameter. **/p** cannot be used unless **/u** is specified. |
| /fo table | Formats the output as a table. This is the default. |
| /fo list | Formats the output as a list. |
| /fo csv | Formats the output with comma-separated values. |
| /nh | Omits the header row from the displayed driver information. Not valid if the **/fo** parameter is set to **list**. |
| /v | Displays verbose output. **/v** is not valid for signed drivers. |
| /si | Provides information about signed drivers. |
| /? | Displays help at the command prompt. |

### Examples

To display a list of installed device drivers on the local computer, type:

```
driverquery
```

To display the output in a comma-separated values (CSV) format, type:

```
driverquery /fo csv
```

To hide the header row in the output, type:

```
driverquery /nh
```

To use the **driverquery** command on a remote server named *server1* using your current credentials on the local computer, type:

```
driverquery /s server1
```

To use the **driverquery** command on a remote server named *server1* using the credentials for *user1* on the domain *maindom*, type:

```
driverquery /s server1 /u maindom\user1 /p p@ssw3d
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)