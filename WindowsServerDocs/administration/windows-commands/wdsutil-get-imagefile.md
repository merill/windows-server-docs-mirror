---
layout: Conceptual
title: get-ImageFile | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-imagefile
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for get-ImageFile, which retrieves information about the images contained in a Windows Image (.wim) file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 69ace54e-bea2-f2b8-02d8-f7bfd890e2b6
document_version_independent_id: 50aa1722-467f-4c28-7c1a-aa94f7bd6992
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-imagefile.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-imagefile
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-imagefile.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: dc2dd800-d618-253b-d859-30f8fdbcac6e
---

# get-ImageFile | Microsoft Learn

Retrieves information about the images contained in a Windows Image (.wim) file.

## Syntax

```
wdsutil [Options] /Get-ImageFile /ImageFile:<wim file path> [/Detailed]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /ImageFile:&lt;WIM file path&gt; | Specifies the full path and file name of the .wim file. |
| [/Detailed] | Returns all image metadata from each image. If this option is not used, the default behavior is to return only the image name, description, and file name. |

## Examples

To view information about an image, type:

```
wdsutil /Get-ImageFile /ImageFile:C:\temp\install.wim
```

To view detailed information, type:

```
wdsutil /Verbose /Get-ImageFile /ImageFile:\\Server\Share\My Folder \install.wim /Detailed
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)