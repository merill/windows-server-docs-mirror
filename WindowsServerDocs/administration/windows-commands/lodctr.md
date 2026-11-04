---
layout: Conceptual
title: lodctr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/lodctr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the lodctr command, which allows you to register or save performance counter name and registry settings in a file and designate trusted services.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-10-22T00:00:00.0000000Z
locale: en-us
document_id: d4b3ac89-b24b-e0c9-3c32-6f341e99d256
document_version_independent_id: 5fbaecde-5418-5179-9690-17f87843a131
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/lodctr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/lodctr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/lodctr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0f0caf63-6182-62f6-4cf2-ca07495ee4a9
---

# lodctr | Microsoft Learn

Allows you to register or save performance counter name and registry settings in a file and designate trusted services.

## Syntax

```
lodctr <filename> [/s:<filename>] [/r:<filename>] [/t:<servicename>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<filename>` | Specifies the name of the initialization file that registers the performance counter name settings and explanatory text. |
| /s:`<filename>` | Specifies the name of the file to which the performance counter registry settings and explanatory text are saved. |
| /r | Restores counter registry settings and explanatory text from current registry settings and cached performance files related to the registry. |
| /r:`<filename>` | Specifies the name of the file that restores the performance counter registry settings and explanatory text.<br>**Warning:** If you use this command, you'll overwrite all performance counter registry settings and explanatory text, replacing them with the configuration defined in the specified file. |
| /t:`<servicename>` | Indicates that service `<servicename>` is trusted. |
| /? | Displays help at the command prompt. |

#### Remarks

- If the information that you supply contains spaces, use quotation marks around the text (for example, "file name 1").
- An exit code of **0** indicates the command line syntax was correct. It doesn't mean the operation was successful. Check the output from the command for potential error messages.

### Examples

To save the current performance registry settings and explanatory text to file *"perf backup1.txt"*, type:

```
lodctr /s:"perf backup1.txt"
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)