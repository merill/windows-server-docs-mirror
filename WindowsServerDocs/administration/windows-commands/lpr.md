---
layout: Conceptual
title: lpr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/lpr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the lpr command, which sends a file to a computer or printer sharing device running the Line printer Daemon (LPD) service in preparation for printing.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c1e53281-96e5-5237-4df9-9db1f10223e9
document_version_independent_id: 19981a13-a9ef-533e-ea15-ab52b0580905
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/lpr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/lpr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/lpr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 55428ed3-0997-f263-8471-8db7737b2def
---

# lpr | Microsoft Learn

Sends a file to a computer or printer sharing device running the Line printer Daemon (LPD) service in preparation for printing.

## Syntax

```
lpr [-S <servername>] -P <printername> [-C <bannercontent>] [-J <jobname>] [-o | -o l] [-x] [-d] <filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| -S `<servername>` | Specifies (by name or IP address) the computer or printer sharing device that hosts the LPD print queue with a status that you want to display. This parameter is required and must be capitalized. |
| -P `<printername> ` | Specifies (by name) the printer for the print queue with a status that you want to display. To find the name of the printer, open the **Printers** folder. This parameter is required and must be capitalized. |
| -C `<bannercontent>` | Specifies the content to print on the banner page of the print job. If you don't include this parameter, the name of the computer from which the print job was sent appears on the banner page. This parameter must be capitalized. |
| -J `<jobname>` | Specifies the print job name that will be printed on the banner page. If you don't include this parameter, the name of the file being printed appears on the banner page. This parameter must be capitalized. |
| `[-o | -o l]` | Specifies the type of file that you want to print. The parameter **-o** specifies that you want to print a text file. The parameter **-o l** specifies that you want to print a binary file (for example, a PostScript file). |
| -d | Specifies that the data file must be sent before the control file. Use this parameter if your printer requires the data file to be sent first. For more information, see your printer documentation. |
| -x | Specifies that the **lpr** command must be compatible with the Sun Microsystems operating system (referred to as SunOS) for releases up to and including 4.1.4\_u1. |
| `<filename>` | Specifies (by name) the file to be printed. This parameter is required. |
| /? | Displays help at the command prompt. |

### Examples

To print the *Document.txt* text file to the *Laserprinter1* printer queue on an LPD host at *10.0.0.45*, type:

```
lpr -S 10.0.0.45 -P Laserprinter1 -o Document.txt
```

To print the *PostScript\_file.ps* Adobe PostScript file to the *Laserprinter1* printer queue on an LPD host at *10.0.0.45*, type:

```
lpr -S 10.0.0.45 -P Laserprinter1 -o l PostScript_file.ps
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Print Command Reference](print-command-reference)