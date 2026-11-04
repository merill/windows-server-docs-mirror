---
layout: Conceptual
title: prnmngr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/prnmngr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the prnmngr command, which adds, deletes, and lists printers or printer connections, in addition to setting and displaying the default printer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 30c13681-aa1e-e000-f6f9-acdf24fc6b3a
document_version_independent_id: 4949d5d2-efda-f057-da73-717e8d32569a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/prnmngr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/prnmngr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/prnmngr.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 00490be6-7aee-b7a7-78c9-da71e390ad7f
---

# prnmngr | Microsoft Learn

Adds, deletes, and lists printers or printer connections, in addition to setting and displaying the default printer. This command is a Visual Basic script located in the `%WINdir%\System32\printing_Admin_Scripts\<language>` directory. To use this command at a command prompt, type **cscript** followed by the full path to the prnmngr file, or change directories to the appropriate folder. For example: `cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnmngr`.

## Syntax

```
cscript prnmngr {-a | -d | -x | -g | -t | -l | -?}[c] [-s <Servername>] [-p <Printername>] [-m <printermodel>] [-r <portname>] [-u <Username>]
[-w <password>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -a | Adds a local printer connection. |
| -d | Deletes a printer connection. |
| -x | Deletes all printers from the server specified by the **-s** parameter. If you don't specify a server, Windows deletes all printers on the local computer. |
| -g | Displays the default printer. |
| -t | Sets the default printer to the printer specified by the **-p** parameter. |
| -l | Lists all printers installed on the server specified by the **-s** parameter. If you don't specify a server, Windows lists the printers installed on the local computer. |
| c | Specifies that the parameter applies to printer connections. Can be used with the **-a** and **-x** parameters. |
| -s `<Servername>` | Specifies the name of the remote computer that hosts the printer that you want to manage. If you don't specify a computer, the local computer is used. |
| -p `<Printername>` | Specifies the name of the printer that you want to manage. |
| -m `<Modelname>` | Specifies (by name) the driver you want to install. Drivers are often named for the model of printer they support. See the printer documentation for more information. |
| -r `<portname>` | Specifies the port where the printer is connected. If this is a parallel or a serial port, use the ID of the port (for example, LPT1: or COM1:). If this is a TCP/IP port, use the port name that was specified when the port was added. |
| -u `<Username>` -w `<password>` | Specifies an account with permissions to connect to the computer that hosts the printer that you want to manage. All members of the target computer's local Administrators group have these permissions, but the permissions can also be granted to other users. If you don't specify an account, you must be logged on under an account with these permissions for the command to work. |
| /? | Displays help at the command prompt. |

#### Remarks

- If the information that you supply contains spaces, use quotation marks around the text (for example, "Computer Name").

### Examples

To add a printer named colorprinter\_2 that is connected to LPT1 on the local computer and requires a printer driver called color printer Driver1, type:

```
cscript prnmngr -a -p colorprinter_2 -m "color printer Driver1" -r lpt1:
```

To delete the printer named colorprinter\_2 from the remote computer named HRServer, type:

```
cscript prnmngr -d -s HRServer -p colorprinter_2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Print Command Reference](print-command-reference)