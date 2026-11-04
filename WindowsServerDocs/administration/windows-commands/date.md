---
layout: Conceptual
title: date | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/date
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the date command, which displays or sets the system date. If used without parameters,
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-10-26T00:00:00.0000000Z
locale: en-us
document_id: cf5bf65b-0725-ce75-22a3-1b902008187e
document_version_independent_id: fc6b8570-983c-b25d-a8fd-29685bc17153
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/date.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/date
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/date.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 34051002-7fa5-b85e-5464-64eb2cac55c3
---

# date | Microsoft Learn

Displays or sets the system date. If used without parameters, **date** displays the current system date setting and prompts you to enter a new date.

Important

You must be an administrator to use this command.

## Syntax

```
date [/t | <month-day-year>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<month-day-year>` | Sets the date specified, where *month* is the month (one or two digits, including values 1 through 12), *day* is the day (one or two digits, including values 1 through 31), and *year* is the year (two or four digits, including the values 00 through 99 or 1980 through 2099). You must separate values for *month*, *day*, and *year* with periods (.), hyphens (-), or slash marks (/).<br>**Note:** Be mindful if you use 2 digits to represent the year, the values 80-99 correspond to 1980 through 1999. |
| /t | Displays the current date without prompting you for a new date. |
| /? | Displays help at the command prompt. |

## Examples

If command extensions are enabled, to display the current system date, type:

```
date /t
```

To change the current system date to August 3, 2007, you can type any of the following:

```
date 08.03.2007
date 08-03-07
date 8/3/07
```

To display the current system date, followed by a prompt to enter a new date, type:

```
date
```

To keep the current date and return to the command prompt, press **ENTER**. To change the current date, type the new date based on your current date configuration, as seen in the second example above, and then press **ENTER**.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)