---
layout: Conceptual
title: new-DiscoverImage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-new-discoverimage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for new-DiscoverImage, which creates a new discover image from an existing boot image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ea1f8c8b-fe32-e6bf-368b-c51a65426366
document_version_independent_id: 133a019e-c809-3d6d-f7e2-517b4f96d3ed
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-new-discoverimage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-new-discoverimage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-new-discoverimage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 97f0b73e-47bb-40c7-ff05-25a4d03b1ea4
---

# new-DiscoverImage | Microsoft Learn

Creates a new discover image from an existing boot image. Discover images are boot images that force the Setup.exe program to start in Windows Deployment Services mode and then discover a Windows Deployment Services server. Typically these images are used to deploy images to computers that are not capable of booting to PXE. For more information, see Creating Images ([https://go.microsoft.com/fwlink/?LinkId=115311](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730907%28v=ws.10%29)).

## Syntax

```
wdsutil [Options] /New-DiscoverImage [/Server:<Server name>]
     /Image:<Image name>
     /Architecture:{x86 | ia64 | x64}
     [/Filename:<File name>]
     /DestinationImage
         /FilePath:<File path and name>
         [/Name:<Name>]
         [/Description:<Description>]
         [/WDSServer:<Server name>]
         [/Overwrite:{Yes | No | Append}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| /Image:&lt;Image name&gt; | Specifies the name of the source boot image. |
| /Architecture:{x86 | ia64 |
| [/Filename:&lt;File name&gt;] | If the image cannot be uniquely identified by name, you must use this option to specify the file name. |
| /DestinationImage | Specifies the settings for the destination image. You can specify the settings using the following options:- /FilePath:&lt; File path and name&gt; - Sets full file path for the new image.- [/Name:&lt;Name&gt;] - Sets the display name of the image. If no display name is specified, the display name of the source image will be used.- [/Description: &lt;Description&gt;] - Sets the description of the image.- [/WDSServer: &lt;Server name&gt;] - Specifies the name of the server that all clients who boot from the specified image should contact to download the install image. By default, all clients who boot this image will discover a valid Windows Deployment Services server. Using this option bypasses the discovery functionality and forces the booted client to contact the specified server.- [/Overwrite:{Yes |

## Examples

To create a discover image out of boot image, and name it WinPEDiscover.wim, type:

```
wdsutil /New-DiscoverImage /Image:WinPE boot image /Architecture:x86 /DestinationImage /FilePath:C:\Temp\WinPEDiscover.wim
```

To create a discover image out of boot image, and name it WinPEDiscover.wim with the specified settings, type:

```
wdsutil /Verbose /Progress /New-DiscoverImage /Server:MyWDSServer
/Image:WinPE boot image /Architecture:x64 /Filename:boot.wim /DestinationImage /FilePath:\\Server\Share\WinPEDiscover.wim
/Name:New WinPE image /Description:WinPE image for WDS Client discovery /Overwrite:No
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)