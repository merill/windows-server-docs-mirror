---
layout: Conceptual
title: wdsutil get-allimages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-allimages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil get-allimages command, which retrieves information about all images on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: db529d3c-602e-fca0-0251-53be6ac80702
document_version_independent_id: bb77655d-a546-95cb-fc2d-c4db733263be
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-allimages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-allimages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-allimages.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 07f34374-8ef8-178c-c015-510a117aa6f3
---

# wdsutil get-allimages | Microsoft Learn

Retrieves information about all images on a server.

## Syntax

```
wdsutil /get-allimages [/server:<servername>] /show:{boot | install | legacyris | all} [/detailed]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[/server:<servername>]` | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| `/show:{boot | install | legacyris | all}` | Where **boot** returns only boot images, **install** returns install images as well as information about the image groups that contain them, **LegacyRis** returns only remote Installation Services (RIS) images, and **All** returns boot image information, install image information (including information about the image groups), and RIS image information. |
| [/detailed] | Indicates that all image metadata from each image should be returned. If this option is not used, the default behavior is to return only the image name, description, and file name. |

## Examples

To view information about the images, type either:

```
wdsutil /get-allimages /show:install
```

```
wdsutil /verbose /get-allimages /server:MyWDSServer /show:all /detailed
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-image command](wdsutil-add-image)
- [wdsutil copy-image command](wdsutil-copy-image)
- [wdsutil export-image command](wdsutil-export-image)
- [wdsutil remove-image command](wdsutil-remove-image)
- [wdsutil replace-image command](wdsutil-replace-image)
- [wdsutil set-image command](wdsutil-set-image)