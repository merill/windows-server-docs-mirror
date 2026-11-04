---
layout: Conceptual
title: new-CaptureImage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-new-captureimage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for new-CaptureImage, which creates a new capture image from an existing boot image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e4ed740c-9aab-d3c2-9b53-b2358803e2c0
document_version_independent_id: 62ab6f87-29c3-539a-c8cb-91673d48bb32
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-new-captureimage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-new-captureimage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-new-captureimage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e8f6b163-dc7b-c4fc-574a-ac1e847ac8f5
---

# new-CaptureImage | Microsoft Learn

Creates a new capture image from an existing boot image. Capture images are boot images that start the Windows Deployment Services capture utility instead of starting Setup. When you boot a reference computer (that has been prepared with Sysprep) into a capture image, a wizard creates an install image of the reference computer and saves it as a Windows Image (.wim) file. You can also add the image to media (such as a CD, DVD, or USB drive), and then boot a computer from that media. After you create the install image, you can add the image to the server for PXE boot deployment. For more information, see Creating Images ([https://go.microsoft.com/fwlink/?LinkId=115311](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730907%28v=ws.10%29)).

## Syntax

```
wdsutil [Options] /New-CaptureImage [/Server:<Server name>]
     /Image:<Image name>
     /Architecture:{x86 | ia64 | x64}
     [/Filename:<File name>]
     /DestinationImage
        /FilePath:<File path and name>
        [/Name:<Name>]
        [/Description:<Description>]
        [/Overwrite:{Yes | No | Append}]
        [/UnattendFilePath:<File path>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| /Image:&lt;Image name&gt; | Specifies the name of the source boot image. |
| /Architecture: {x86 | ia64 |
| [/Filename: &lt;Filename&gt;] | If the image cannot be uniquely identified by name, you must use this option to specify the file name. |
| /DestinationImage | Specifies the settings for the destination image. You specify the settings using the following options:- /FilePath: &lt;File path and name&gt; Sets the full file path for the new capture image.- [/Name: &lt;Name&gt;] - Sets the display name of the image. If no display name is specified, the display name of the source image will be used.- [/Description: &lt;Description&gt;] - Sets the description of the image.- [/Overwrite: {Yes |

## Examples

To create a capture image and name it WinPECapture.wim, type:

```
wdsutil /New-CaptureImage /Image:WinPE boot image /Architecture:x86 /DestinationImage /FilePath:C:\Temp\WinPECapture.wim
```

To create a capture image and apply the specified settings, type:

```
wdsutil /Verbose /Progress /New-CaptureImage /Server:MyWDSServer /Image:WinPE boot image /Architecture:x64 /Filename:boot.wim
/DestinationImage /FilePath:\\Server\Share\WinPECapture.wim /Name:New WinPE image /Description:WinPE image with capture utility /Overwrite:No /UnattendFilePath:\\Server\Share\WDSCapture.inf
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)