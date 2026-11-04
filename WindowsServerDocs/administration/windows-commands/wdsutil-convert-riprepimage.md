---
layout: Conceptual
title: convert-riprepimage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-convert-riprepimage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the convert-riprepimage command, which converts an existing Remote Installation Preparation (RIPrep) image to Windows Image (.wim) format.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c838a24b-8c37-46e6-a388-0bab53d64066
document_version_independent_id: ed4da81f-d56e-768b-289c-67d97addcb39
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-convert-riprepimage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-convert-riprepimage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-convert-riprepimage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: af98905c-6e1a-d88f-ba4e-ee9f91e2d8c1
---

# convert-riprepimage | Microsoft Learn

Converts an existing Remote Installation Preparation (RIPrep) image to Windows Image (.wim) format.

## Syntax

```
wdsutil [Options] /Convert-RIPrepImage /FilePath:<Filepath and name> /DestinationImage /FilePath:<Filepath and name> [/Name:<Name>] [/Description:<Description>] [/InPlace] [/Overwrite:{Yes | No | Append}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /FilePath:`<Filepath and name>` | Specifies the full filepath and name of the .sif file that corresponds to the RIPrep image. This file is typically called Riprep.sif and is found in the **\Templates** subfolder of the folder that contains the RIPrep image. |
| /DestinationImage | Specifies the settings for the destination image. Uses the following options;<br>- `/FilePath:<Filepath and name>` - Sets the full file path for the new file. For example: **C:\Temp\convert.wim**<br>- [`/Name:<Name>`] - Sets the display name of the image. If no display name is specified, the display name of the source image is used.<br>- [`/Description:<Description>`] - Sets the description of the image.<br>- [/InPlace] - Specifies that the conversion should take place on the original RIPrep image and not on a copy of the original image, which is the default behavior.<br>- [`/Overwrite:{Yes | No | Append}` - Sets whether this image should overwrite or append any existing files. |

## Examples

To convert the specified RIPrep.sif image to RIPREP.wim, type:

```
wdsutil /Convert-RiPrepImage /FilePath:R:\RemoteInstall\Setup\English \Images\Win2k3.SP1\i386\Templates\riprep.sif /DestinationImage /FilePath:C:\Temp\RIPREP.wim
```

To convert the specified RIPrep.sif image to RIPREP.wim with the specified name and description, and overwrite it with the new file if a file already exists, type:

```
wdsutil /Verbose /Progress /Convert-RiPrepImage /FilePath:\\Server \RemInst\Setup\English\Images\WinXP.SP2\i386\Templates\riprep.sif /DestinationImage /FilePath:\\Server\Share\RIPREP.wim /Name:WindowsXP image /Description:Converted RIPREP image of WindowsXP /Overwrite:Append
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)