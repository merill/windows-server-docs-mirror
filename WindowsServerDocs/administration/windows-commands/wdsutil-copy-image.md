---
layout: Conceptual
title: wdsutil copy-image | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-copy-image
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil copy-image command, which copies images that are within the same image group.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e16e947a-1ace-e67b-5ad4-56978fde02f0
document_version_independent_id: 8187bc63-8887-b876-79d0-e0fee861ff69
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-copy-image.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-copy-image
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-copy-image.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1e3396c3-59c1-d167-156e-7b66db4dbc96
---

# wdsutil copy-image | Microsoft Learn

Copies images that are within the same image group. To copy images between image groups, use the [wdsutil Export-Image command](wdsutil-export-image) command and then the [wdsutil add-Image command](wdsutil-add-image) command.

## Syntax

```
wdsutil [Options] /copy-Image image:<Image name> [/Server:<Server name>] imagetype:Install imageGroup:<Image group name>] [/Filename:<File name>] /DestinationImage /Name:<Name> /Filename:<File name> [/Description:<Description>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| image:`<Imagename>` | Specifies the name of the image to be copied. |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| imagetype:Install | Specifies the type of image to be copied. This option must be set to **install**. |
| \imageGroup:`<Image groupname>`] | Specifies the image group that contains the image to be copied. If no image group is specified and only one group exists on the server, that image group is used by default. If more than one image group exists on the server, you must specify the image group. |
| [/Filename:`<Filename>`] | Specifies the file name of the image to be copied. If the source image cannot be uniquely identified by name, you must specify the file name. |
| /DestinationImage | Specifies the settings for the destination image. The valid values are:<br>- /Name:`<Name>` - Sets the display name of the image to be copied.<br>- /Filename:`<Filename>` - Sets the name of the destination image file that will contain the image copy.<br>- [/Description:`<Description>`] - Sets the description of the image copy. |

## Examples

To create a copy of the specified image and name it WindowsVista.wim, type:

```
wdsutil /copy-Image image:Windows Vista with Office imagetype:Install /DestinationImage /Name:copy of Windows Vista with Office / Filename:WindowsVista.wim
```

To create a copy of the specified image, apply the specified settings, and name the copy WindowsVista.wim, type:

```
wdsutil /verbose /Progress /copy-Image image:Windows Vista with Office /Server:MyWDSServe imagetype:Install imageGroup:ImageGroup1
/Filename:install.wim /DestinationImage /Name:copy of Windows Vista with Office /Filename:WindowsVista.wim /Description:This is a copy of the original Windows image with Office installed
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-image command](wdsutil-add-image)
- [wdsutil export-image command](wdsutil-export-image)
- [wdsutil get-image command](wdsutil-get-image)
- [wdsutil remove-image command](wdsutil-remove-image)
- [wdsutil replace-image command](wdsutil-replace-image)
- [wdsutil set-image command](wdsutil-set-image)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)