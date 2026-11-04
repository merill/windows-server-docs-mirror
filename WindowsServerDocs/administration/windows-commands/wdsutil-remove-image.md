---
layout: Conceptual
title: wdsutil remove-image | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-remove-image
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil remove-image, which deletes an image from a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a2ef0c10-95a0-feaa-da19-7bd2b8948624
document_version_independent_id: f7b2c7d8-6e32-f508-966d-a75a7a63391a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-remove-image.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-remove-image
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-remove-image.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1b68aa7f-c148-2043-0a6a-d2df1c21eb8f
---

# wdsutil remove-image | Microsoft Learn

Deletes an image from a server.

## Syntax

for boot images:

```
wdsutil [Options] /remove-Image:<Image name> [/Server:<Server name> type:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<Filename>]
```

for install images:

```
wdsutil [Options] /remove-image:<Image name> [/Server:<Server name> type:Install ImageGroup:<Image group name>] [/Filename:<Filename>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /remove-image:&lt;Image name&gt; | Specifies the name of the image. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| mediatype:{Boot | Install} | Specifies the type of image. |
| /Architecture:{x86 | ia64 | x64} | Specifies the architecture of the image. Because it is possible to have the same image name for different boot images in different architectures, specifying the architecture value ensures that the correct image will be removed. |
| \ImageGroup:&lt;Image group name&gt;] | Specifies the image group that contains the image. If no image group name is specified and only one image group exists on the server, that image group will be used. If more than one image group exists, you must use this option to specify the image group. |
| [/Filename:&lt;File name&gt;] | if the image cannot be uniquely identified by name, you must use this option to specify the file name. |

## Examples

To remove a boot image, type:

```
wdsutil /remove-Imagmedia:WinPE Boot Imagemediatype:Boot /Architecture:x86
```

```
wdsutil /verbose /remove-Image:WinPE Boot Image /Server:MyWDSServer type:Boot /Architecture:x64 /Filename:boot.wim
```

To remove an install image, type:

```
wdsutil /remove-Image:Windows Vista with Officemediatype:Install
```

```
wdsutil /verbose /remove-Image:Windows Vista with Office /Server:MyWDSServemediatype:Install ImageGroup:ImageGroup1 /Filename:install.wim
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-image command](wdsutil-add-image)
- [wdsutil copy-image command](wdsutil-copy-image)
- [wdsutil export-image command](wdsutil-export-image)
- [wdsutil get-image command](wdsutil-get-image)
- [wdsutil replace-image command](wdsutil-replace-image)
- [wdsutil set-image command](wdsutil-set-image)