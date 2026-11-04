---
layout: Conceptual
title: print | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/print
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the print command, which sends a text file to a printer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 674f6399-9f65-9829-5a08-504056cdc9b2
document_version_independent_id: 5ee5cb40-b6de-995c-bd4e-64edafe53391
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/print.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/print
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/print.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 118037b8-268a-fe91-226b-7925d929b83c
---

# print | Microsoft Learn

Sends a text file to a printer. A file can print in the background if you send it to a printer connected to a serial or parallel port on the local computer.

Note

You can perform many configuration tasks from the command prompt by using the [Mode command](mode), including configuring a printer connected to a parallel or a serial port, displaying printer status, or preparing a printer for code page switching.

## Syntax

```
print [/d:<printername>] [<drive>:][<path>]<filename>[ ...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /d:`<printername>` | Specifies the printer that you want to print the job. To print to a locally connected printer, specify the port on your computer where the printer is connected. Valid values for parallel ports are **LPT1**, **LPT2**, and **LPT3**. Valid values for serial ports are **COM1**, **COM2**, **COM3**, and **COM4**. You can also specify a network printer by using its queue name (`\\server_name\printer_name`). If you don't specify a printer, the print job is sent to **LPT1** by default. |
| `<drive>`: | Specifies the logical or physical drive where the file you want to print is located. This parameter isn't required if the file you want to print is located on the current drive. |
| `<path>` | Specifies the location of the file you want to print. This parameter isn't required if the file you want to print is located in the current directory. |
| `<filename>[ ...]` | Required. Specifies the file you want to print. You can include multiple files in one command. |
| /? | Displays help at the command prompt. |

### Examples

To send the **report.txt** file, located in the current directory, to a printer connected to **lpt2** on the local computer, type:

```
print /d:lpt2 report.txt
```

To send the **report.txt** file, located in the **c:\accounting** directory, to the **printer1** print queue on the **/d:\copyroom** server, type:

```
print /d:\\copyroom\printer1 c:\accounting\report.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Print Command Reference](print-command-reference)
- [Mode command](mode)