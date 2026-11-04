---
layout: Conceptual
title: systeminfo | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/systeminfo
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the systeminfo command, which displays detailed configuration information about a computer and its operating system, including operating system configuration, security information, product ID, and hardware properties (such as RAM, disk space, and network cards).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fbcdf4af-20d3-5838-2078-84e5f444719f
document_version_independent_id: aa263a68-e2dc-ea0d-1b43-5d58fb29c7fd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/systeminfo.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/systeminfo
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/systeminfo.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c77b108b-3928-da1e-bc14-8c352558044e
---

# systeminfo | Microsoft Learn

Displays detailed configuration information about a computer and its operating system, including operating system configuration, security information, product ID, and hardware properties (such as RAM, disk space, and network cards).

## Syntax

```
systeminfo [/s <computer> [/u <domain>\<username> [/p <password>]]] [/fo {TABLE | LIST | CSV}] [/nh]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /s `<computer>` | Specifies the name or IP address of a remote computer (do not use backslashes). The default is the local computer. |
| /u `<domain>\<username>` | Runs the command with the account permissions of the specified user account. If **/u** is not specified, this command uses the permissions of the user who is currently logged on to the computer that is issuing the command. |
| /p `<password>` | Specifies the password of the user account that is specified in the **/u** parameter. |
| /fo `<format>` | Specifies the output format with one of the following values:<br>- **TABLE** - Displays output in a table.<br>- **LIST** - Displays output in a list.<br>- **CSV** - Displays output in comma-separated values (.csv) format. |
| /nh | Suppresses column headers in the output. Valid when the **/fo** parameter is set to TABLE or CSV. |
| /? | Displays help at the command prompt. |

## Examples

To view configuration information for a computer named *Srvmain*, type:

```
systeminfo /s srvmain
```

To remotely view configuration information for a computer named *Srvmain2* that is located on the *Maindom* domain, type:

```
systeminfo /s srvmain2 /u maindom\hiropln
```

To remotely view configuration information (in list format) for a computer named *Srvmain2* that is located on the *Maindom* domain, type:

```
systeminfo /s srvmain2 /u maindom\hiropln /p p@ssW23 /fo list
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)