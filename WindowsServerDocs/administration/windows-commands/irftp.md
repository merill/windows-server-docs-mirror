---
layout: Conceptual
title: irftp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/irftp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the irftp command, which sends files over an infrared link.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fffee314-e328-019a-aeec-b84e626da304
document_version_independent_id: 2ce45518-50b5-b7b1-1d51-3b6c0dec9aee
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/irftp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/irftp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/irftp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 66ada337-c03e-054c-176a-8a2f6f175e7b
---

# irftp | Microsoft Learn

Sends files over an infrared link.

Important

Make sure the devices intended to communicate over an infrared link have infrared functionality enabled and are working correctly. Also make sure an infrared link is established between the devices.

## Syntax

```
irftp [<drive>:\] [[<path>] <filename>] [/h][/s]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<drive>:\` | Specifies the drive that contains the files that you want to send over an infrared link. |
| `[path]<filename>` | Specifies the location and name of the file or set of files that you want to send over an infrared link. If you specify a set of files, you must specify the full path for each file. |
| /h | Specifies hidden mode. When hidden mode is used, the files are sent without displaying the Wireless Link dialog box. |
| /s | Opens the **Wireless Link** dialog box, so that you can select the file or set of files that you want to send without using the command line to specify the drive, path, and file names. The **Wireless Link** dialog box also opens if you use this command without any parameters. |

### Examples

To send *c:\example.txt* over the infrared link, type:

```
irftp c:\example.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)