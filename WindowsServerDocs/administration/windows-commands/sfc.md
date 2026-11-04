---
layout: Conceptual
title: sfc | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/sfc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the sfc command, which scans and verifies the integrity of all protected system files and replaces incorrect versions with correct versions.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-10-19T00:00:00.0000000Z
locale: en-us
document_id: 0d979606-3b11-34e5-70db-88d90855cf5c
document_version_independent_id: d2358e0b-7688-ac7f-0f08-fc198b6a57a9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/sfc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/sfc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/sfc.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f258535b-f236-8d3c-baf5-e133662fb5b4
---

# sfc | Microsoft Learn

Scans and verifies the integrity of all protected system files and replaces incorrect versions with correct versions. If this command discovers that a protected file has been overwritten, it retrieves the correct version of the file from the **systemroot\** folder, and then replaces the incorrect file.

Important

You must be logged on as a member of the Administrators group to run this command.

## Syntax

```
sfc [/scannow] [/verifyonly] [/scanfile=<file>] [/verifyfile=<file>] [/offwindir=<offline windows directory> /offbootdir=<offline boot directory> /offlogfile=<log file path>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /scannow | Scans the integrity of all protected system files and repairs files with problems when possible. |
| /verifyonly | Scans the integrity of all protected system files, without performing repairs. |
| /scanfile `<file>` | Scans the integrity of the specified file (full path and filename) and attempts to repair any problems if they're detected. |
| /verifyfile `<file>` | Verifies the integrity of the specified file (full path and filename), without performing repairs. |
| /offwindir `<offline windows directory>` | Specifies the location of the offline windows directory, for offline repair. |
| /offbootdir `<offline boot directory>` | Specifies the location of the offline boot directory for offline repair. |
| /offlogfile=`<log file path>` | Specifies a location to store the log file other than the default. |
| /? | Displays help at the command prompt. |

## Examples

To verify the *kernel32.dll file*, type:

```
sfc /verifyfile=c:\windows\system32\kernel32.dll
```

To set up the offline repair of the *kernel32.dll* file with an offline boot directory set to **D:** and an offline windows directory set to **D:\Windows**, type:

```
sfc /scanfile=D:\windows\system32\kernel32.dll /offbootdir=D:\ /offwindir=d:\windows
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)