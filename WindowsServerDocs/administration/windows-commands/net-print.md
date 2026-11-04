---
layout: Conceptual
title: net print | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/net-print
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the net print command. This command has been deprecated and isn't guaranteed to be supported in future releases of Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 31f8515b-37e7-cad8-ce06-c5940815df08
document_version_independent_id: 4a529086-bc07-3435-34dc-a33bb701d3b5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/net-print.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/net-print
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/net-print.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9cd229c8-f5ac-e28b-33cd-f0078b0bfb90
---

# net print | Microsoft Learn

Important

This command has been deprecated. However, you can perform many of the same tasks using the [prnjobs command](prnjobs), [Windows Management Instrumentation (WMI)](/en-us/windows/win32/wmisdk/wmi-start-page), [PrintManagement in Powershell](/en-us/powershell/module/printmanagement).

Displays information about a specified printer queue or a specified print job, or controls a specified print job.

## Syntax

```
net print {\\<computername>\<sharename> | \\<computername> <jobnumber> [/hold | /release | /delete]} [help]
```

### Parameters

| Parameters | Description |
| --- | --- |
| `\\<computername>\<sharename>` | Specifies (by name) the computer and print queue about which you want to display information. |
| `\\<computername>` | Specifies (by name) the computer that hosts the print job you want to control. If you do not specify a computer, the local computer is assumed. Requires the `<jobnumber>` parameter. |
| `<jobnumber>` | Specifies the number of the print job you want to control. This number is assigned by the computer that hosts the print queue where the print job is sent. After a computer assigns a number to a print job, that number is not assigned to any other print jobs in any queue hosted by that computer. Required when using the `\\<computername>` parameter. |
| `[/hold | /release | /delete]` | Specifies the action to take with the print job. If you specify a job number, but don't specify any action, information about the print job is displayed.<br>- **/hold** - Delays the job, allowing other print jobs to bypass it until it is released.<br>- **/release** - Releases a print job that has been delayed.<br>- **/delete** - Removes a print job from a print queue. |
| help | Displays help at the command prompt. |

#### Remarks

- The `net print\\<computername>` command displays information about print jobs in a shared printer queue. The following is an example of a report for all print jobs in a queue for a shared printer named *LASER*:

    ```
    printers at \\PRODUCTION
    Name              Job #      Size      Status
    -----------------------------
    LASER Queue       3 jobs               *printer active*
    USER1          84        93844      printing
    USER2          85        12555      Waiting
    USER3          86        10222      Waiting
    ```
- The following is an example of a report for a print job:

    ```
    Job #            35
    Status           Waiting
    Size             3096
    remark
    Submitting user  USER2
    Notify           USER2
    Job data type
    Job parameters
    additional info
    ```

### Examples

To list the contents of the *Dotmatrix* print queue on the *\Production* computer, type:

```
net print \\Production\Dotmatrix
```

To display information about job number *35* on the *\Production* computer, type:

```
net print \\Production 35
```

To delay job number *263* on the *\Production* computer, type:

```
net print \\Production 263 /hold
```

To release job number *263* on the *\Production* computer, type:

```
net print \\Production 263 /release
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [print command reference](print-command-reference)
- [prnjobs command](prnjobs)
- [Windows Management Instrumentation (WMI)](/en-us/windows/win32/wmisdk/wmi-start-page)
- [PrintManagement in Powershell](/en-us/powershell/module/printmanagement)