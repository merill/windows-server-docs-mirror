---
layout: Conceptual
title: wdsutil get-image | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-image
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-image, which retrieves information about an image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 51c9843d-cc0c-b198-1d28-fd2027ea7e62
document_version_independent_id: 86178f06-5b18-6951-5fff-76d22310727b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-image.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-image
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-image.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ec47608b-d18c-72c1-f453-3b17c664de0c
---

# wdsutil get-image | Microsoft Learn

Retrieves information about an image.

## Syntax

For boot images:

```
wdsutil [Options] /Get-Image image:<Image name> [/Server:<Server name> imagetype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>]
```

For install images:

```
wdsutil [Options] /Get-image image:<Image name> [/Server:<Server name> imagetype:Install imagegroup:<Image group name>] [/Filename:<File name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| \image:&lt;Image name&gt; | Specifies the name of the image. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| imagetype:{Boot | Install} | Specifies the type of image. |
| /Architecture:{x86 | ia64 | x64} | Specifies the architecture of the image. Because it is possible to have the same image name for boot images in different architectures, specifying the architecture value ensures that the correct image is returned. |
| [/Filename:&lt;File name&gt;] | if the image cannot be uniquely identified by name, you must use this option to specify the file name. |
| \imagegroup:&lt;Image group name&gt;] | Specifies the image group that contains the image. If no image group is specified and only one image group exists on the server, that group will be used. If more than one image group exists on the server, you must use this parameter to specify the image group. |

## Examples

To retrieve information about a boot image, type one of the following:

```
wdsutil /Get-Image image:WinPE boot imagetype:Boot /Architecture:x86
wdsutil /verbose /Get-Image image:WinPE boot image /Server:MyWDSServer imagetype:Boot /Architecture:x86 /Filename:boot.wim
```

To retrieve information about an install image, type one of the following:

```
wdsutil /Get-Image:Windows Vista with Office imagetype:Install
wdsutil /verbose /Get-Image:Windows Vista with Office /Server:MyWDSServer imagetype:Install imagegroup:ImageGroup1 /Filename:install.wim
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-image command](wdsutil-add-image)
- [wdsutil copy-image command](wdsutil-copy-image)
- [wdsutil export-image command](wdsutil-export-image)
- [wdsutil remove-image command](wdsutil-remove-image)
- [wdsutil replace-image command](wdsutil-replace-image)
- [wdsutil set-image command](wdsutil-set-image)