---
layout: Conceptual
title: time | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/time
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the time command, which displays or sets the system time.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: da7db9a9-6797-e70c-99b4-6c88d92ad23c
document_version_independent_id: ebe0f1c8-6bb4-d2b6-9d4f-8b2c2715de3f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/time.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/time
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/time.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 56cfef98-ee8c-6e1e-dfee-83e5c8d06844
---

# time | Microsoft Learn

Displays or sets the system time. If used without parameters, **time** displays the current system time and prompts you to enter a new time.

Note

You must be an administrator to change the current time.

## Syntax

```
time [/t | [<HH>[:<MM>[:<SS>]] [am|pm]]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<HH>[:<MM>[:<SS>[.<NN>]]] [am | pm]` | Sets the system time to the new time specified, where *HH* is in hours (required), *MM* is in minutes, and *SS* is in seconds. *NN* can be used to specify hundredths of a second. You must separate values for *HH*, *MM*, and *SS* with colons (:). *SS* and *NN* must be separated with a period (.).<br>If **am** or **pm** isn't specified, **time** uses the 24-hour format by default. |
| /t | Displays the current time without prompting you for a new time. |
| /? | Displays help at the command prompt. |

#### Remarks

- Valid *HH* values are 0 through 24.
- Valid *MM* and *SS* values are 0 through 59.

## Examples

If command extensions are enabled, to display the current system time, type:

```
time /t
```

To change the current system time to 5:30 PM, type either of the following:

```
time 17:30:00
time 5:30 pm
```

To display the current system time, followed by a prompt to enter a new time, type:

```
The current time is: 17:33:31.35
Enter the new time:
```

To keep the current time and return to the command prompt, press ENTER. To change the current time, type the new time and then press ENTER.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)