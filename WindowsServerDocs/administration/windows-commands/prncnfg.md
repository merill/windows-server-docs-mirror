---
layout: Conceptual
title: prncnfg | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/prncnfg
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the prncnfg command, which configures or displays configuration information about a printer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 85d83cf4-0f18-a21f-127c-5b1afeb46aa9
document_version_independent_id: f7ecca1e-f62c-1691-7c1a-24a4c15aa8d2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/prncnfg.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/prncnfg
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/prncnfg.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: c2c0a886-93b4-c51d-1152-f9f457760ddc
---

# prncnfg | Microsoft Learn

Configures or displays configuration information about a printer. This command is a Visual Basic script located in the `%WINdir%\System32\printing_Admin_Scripts\<language>` directory. To use this command at a command prompt, type **cscript** followed by the full path to the prncnfg file, or change directories to the appropriate folder. For example: `cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prncnfg`.

## Syntax

```
cscript prncnfg {-g | -t | -x | -?} [-S <Servername>] [-P <Printername>] [-z <newprintername>] [-u <Username>] [-w <password>] [-r <portname>] [-l <location>] [-h <sharename>] [-m <comment>] [-f <separatorfilename>] [-y <datatype>] [-st <starttime>] [-ut <untiltime>] [-i <defaultpriority>] [-o <priority>] [<+|->shared] [<+|->direct] [<+|->hidden] [<+|->published] [<+|->rawonly] [<+|->queued] [<+|->enablebidi] [<+|->keepprintedjobs] [<+|->workoffline] [<+|->enabledevq] [<+|->docompletefirst]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -g | Displays configuration information about a printer. |
| -t | Configures a printer. |
| -x | Renames a printer. |
| -S `<Servername>` | Specifies the name of the remote computer that hosts the printer that you want to manage. If you don't specify a computer, the local computer is used. |
| -P `<Printername>` | Specifies the name of the printer that you want to manage. Required. |
| -z `<newprintername>` | Specifies the new printer name. Requires the **-x** and **-P** parameters. |
| -u `<Username>` -w `<password>` | Specifies an account with permissions to connect to the computer that hosts the printer that you want to manage. All members of the target computer's local Administrators group have these permissions, but the permissions can also be granted to other users. If you don't specify an account, you must be logged on under an account with these permissions for the command to work. |
| -r `<portname>` | Specifies the port where the printer is connected. If this is a parallel or a serial port, then use the ID of the port (for example, LPT1 or COM1). If this is a TCP/IP port, use the port name that was specified when the port was added. |
| -l `<location>` | Specifies the printer location, such as **Copyroom**. If the location contains spaces, use quotation marks around the text, such as **"Copy Room"**. |
| -h `<sharename>` | Specifies the printer's share name. |
| -m `<comment>` | Specifies the printer's comment string. |
| -f `<separatorfilename>` | Specifies a file that contains the text that appears on the separator page. |
| -y `<datatype>` | Specifies the data types that the printer can accept. |
| -st `<starttime>` | Configures the printer for limited availability. Specifies the time of day the printer is available. If you send a document to a printer when it is unavailable, the document is held (spooled) until the printer becomes available. You must specify time as a 24-hour clock. For example, to specify 11:00 P.M., type **2300**. |
| -ut `<endtime>` | Configures the printer for limited availability. Specifies the time of day the printer is no longer available. If you send a document to a printer when it is unavailable, the document is held (spooled) until the printer becomes available. You must specify time as a 24-hour clock. For example, to specify 11:00 P.M., type **2300**. |
| -o `<priority>` | Specifies a priority that the spooler uses to route print jobs into the print queue. A print queue with a higher priority receives all its jobs before any queue with a lower priority. |
| -i `<defaultpriority>` | Specifies the default priority assigned to each print job. |
| `{+|-}`shared | Specifies whether this printer is shared on the network. |
| `{+|-}`direct | Specifies whether the document should be sent directly to the printer without being spooled. |
| `{+|-}`published | Specifies whether this printer should be published in active directory. If you publish the printer, other users can search for it based on its location and capabilities (such as color printing and stapling). |
| `{+|-}`hidden | Reserved function. |
| `{+|-}`rawonly | Specifies whether only raw data print jobs can be spooled in this queue. |
| `{+|-}`}queued | Specifies that the printer should not begin to print until after the last page of the document is spooled. The printing program is unavailable until the document has finished printing. However, using this parameter ensures that the whole document is available to the printer. |
| `{+|-}`keepprintedjobs | Specifies whether the spooler should retain documents after they are printed. Enabling this option allows a user to resubmit a document to the printer from the print queue instead of from the printing program. |
| `{+|-}`workoffline | Specifies whether a user is able to send print jobs to the print queue if the computer is not connected to the network. |
| `{+|-}`enabledevq | Specifies whether print jobs that don't match the printer setup (for example, PostScript files spooled to non-PostScript printers) should be held in the queue rather than being printed. |
| `{+|-}`docompletefirst | Specifies whether the spooler should send print jobs with a lower priority that have completed spooling before sending print jobs with a higher priority that have not completed spooling. If this option is enabled and no documents have completed spooling, the spooler will send larger documents before smaller ones. You should enable this option if you want to maximize printer efficiency at the cost of job priority. If this option is disabled, the spooler always sends higher priority jobs to their respective queues first. |
| `{+|-}`enablebidi | Specifies whether the printer sends status information to the spooler. |
| /? | Displays help at the command prompt. |

### Examples

To display configuration information for the printer named *colorprinter\_2* with a print queue hosted by the remote computer named *HRServer*, type:

```
cscript prncnfg -g -S HRServer -P colorprinter_2
```

To configure a printer named *colorprinter\_2* so that the spooler in the remote computer named *HRServer* keeps print jobs after they have been printed, type:

```
cscript prncnfg -t -S HRServer -P colorprinter_2 +keepprintedjobs
```

To change the name of a printer on the remote computer named *HRServer* from *colorprinter\_2* to *colorprinter 3*, type:

```
cscript prncnfg -x -S HRServer -P colorprinter_2 -z "colorprinter 3"
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Print Command Reference](print-command-reference)