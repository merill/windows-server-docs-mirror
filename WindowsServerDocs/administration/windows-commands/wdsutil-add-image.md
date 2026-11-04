---
layout: Conceptual
title: wdsutil add-image | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-image
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil add-image command, which adds images to a Windows Deployment Services server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-06-30T00:00:00.0000000Z
locale: en-us
document_id: d597eca3-40f7-6c36-b683-8de4822836f6
document_version_independent_id: 0ae91c11-1a15-3226-87eb-fe993be88a8d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-image.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-image
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-image.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5802420e-3ab0-b3e0-6446-b014ef1cb60e
---

# wdsutil add-image | Microsoft Learn

Adds images to a Windows Deployment Services server.

## Syntax

For boot images, use the following syntax:

```
wdsutil /Add-Image /ImageFile:<wim file path> [/Server:<Server name> /ImageType:Boot [/SkipVerify] [/Name:<Image name>] [/Description:<Image description>] [/Filename:<New wim file name>]
```

For install images, use the following syntax:

```
wdsutil /Add-Image /ImageFile:<wim filepath> [/Server:<Servername>] /ImageType:Install [/SkipVerify] /ImageGroup:<Image group name>] [/SingleImage:<Single image name>] [/Name:<Name>] [/Description:<Description>] [/Filename:<File name>] [/UnattendFile:<Unattend file path>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /ImageFile:`<.wim filepath>` | Specifies the full path and file name of the Windows Image (.wim) file that contains the images to be added. |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If a server name is not specified, the local server is used. |
| [/ImageType:`{Boot \| Install}`] | Specifies the type of images to be added. |
| [/SkipVerify] | Specifies that integrity verification will not be performed on the source image file before the image is added. |
| [/Name:`<Name>`] | Sets the display name of the image. |
| [/Description:`<Description>`] | Sets the description of the image. |
| [/Filename:`<Filename>`] | Specifies the new file name for the .wim file. This enables you to change the filename of the .wim file when adding the image. If you don't specify a filename, the source image filename is used. In all cases, Windows Deployment Services checks to determine whether the file name is unique in the boot image store of the destination computer. |
| /ImageGroup:`<Imagegroupname>`] | Specifies the name of the image group in which the images are to be added. If more than one image group exists on the server, the image group must be specified. If you don't specify the image group, and an image group doesn't already exist, a new image group is created. Otherwise, the existing image group is used. |
| [/SingleImage:`<Singleimagename>`] [/Name:`<Name>`] [/Description:`<Description>`] | Copies the specified single image out of a .wim file, and sets the image's display name and description. |
| [/UnattendFile:`<Unattendfilepath>`] | Specifies the full path to the unattended installation file to be associated with the images that are being added. If **/SingleImage** isn't specified, the same unattend file is associated with all of the images in the .wim file. |

## Examples

To add a boot image, type:

```
wdsutil /Add-Image /ImageFile:"C:\MyFolder\Boot.wim" /ImageType:Boot
wdsutil /Verbose /Progress /Add-Image /ImageFile:\\MyServer\Share\Boot.wim /Server:MyWDSServer /ImageType:Boot /Name:"My WinPE Image" /Description:"WinPE Image containing the WDS Client" /Filename:WDSBoot.wim
```

To add an install image, type one of the following:

```
wdsutil /Add-Image /ImageFile:"C:\MyFolder\Install.wim" /ImageType:Install
wdsutil /Verbose /Progress /Add-Image /ImageFile:\\MyServer\Share\Install.wim /Server:MyWDSServer /ImageType:Install /ImageGroup:ImageGroup1
/SingleImage:"Windows Pro" /Name:"My WDS Image" /Description:"Windows Pro image with Microsoft Office" /Filename:"Win Pro.wim" /UnattendFile:"\\server\share\unattend.xml"
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil copy-image command](wdsutil-copy-image)
- [wdsutil export-image command](wdsutil-export-image)
- [wdsutil get-image command](wdsutil-get-image)
- [wdsutil remove-image command](wdsutil-remove-image)
- [wdsutil replace-image command](wdsutil-replace-image)
- [wdsutil set-image command](wdsutil-set-image)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)