---
layout: Conceptual
title: wdsutil export-image | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-export-image
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil export-image command, which exports an existing image from the image store to another Windows Image (.wim) file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3c2ad704-f3b1-e12f-5050-ea5c5da3dd27
document_version_independent_id: 00cb4841-7ba6-cc0a-f88d-f2a901dc93da
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-export-image.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-export-image
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-export-image.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1ebbfa27-a8e9-b7e2-5819-1350556c84c4
---

# wdsutil export-image | Microsoft Learn

Exports an existing image from the image store to another Windows Image (.wim) file.

## Syntax

For boot images:

```
wdsutil [options] /Export-Image image:<Image name> [/Server:<Servername>]
    imagetype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<Filename>]
     /DestinationImage
         /Filepath:<Filepath and name>
         [/Name:<Name>]
         [/Description:<Description>]
     [/Overwrite:{Yes | No}]
```

For install images:

```
wdsutil [options] /Export-Image image:<Image name> [/Server:<Servername>]
    imagetype:Install imageGroup:<Image group name>]
     [/Filename:<Filename>]
     /DestinationImage
         /Filepath:<Filepath and name>
         [/Name:<Name>]
         [/Description:<Description>]
     [/Overwrite:{Yes | No | append}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| image:`<Imagename>` | Specifies the name of the image to be exported. |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| imagetype:`{Boot|Install}` | Specifies the type of image to be exported. |
| \imageGroup:`<Image group name>`] | Specifies the image group containing the image to be exported. If no image group name is specified and only one image group exists on the server, that image group will be used by default. If more than one image group exists on the server, the image group must be specified. |
| /Architecture:`{x86|ia64|x64}` | Specifies the architecture of the image to be exported. Because it is possible to have the same image name for boot images in different architectures, specifying the architecture value ensures that the correct image will be returned. |
| [/Filename:`<Filename>`] | if the image cannot be uniquely identified by name, the file name must be specified. |
| /DestinationImage | Specifies the settings for the destination image. You can specify these settings using the following options:<br>- `/Filepath:<Filepath and name>` - Specifies the full file path for the new image.<br>- `[/Name:<Name>]` - Sets the display name of the image. If no name is specified, the display name of the source image will be used.<br>- `[/Description: <Description>]` - Sets the description of the image. |
| [/Overwrite:`{Yes|No|append}`] | Determines whether the file specified in the **/DestinationImage** option will be overwritten if an existing file with that name already exists at the /Filepath. The **Yes** option causes the existing file to be overwritten, the **No** option (default) causes an error to occur if a file with the same name already exists, and the **append** option causes the generated image to be appended as a new image within the existing .wim file. |

## Examples

To export a boot image, type either:

```
wdsutil /Export-Image image:WinPE boot image imagetype:Boot /Architecture:x86 /DestinationImage /Filepath:C:\temp\boot.wim
```

```
wdsutil /verbose /Progress /Export-Image image:WinPE boot image /Server:MyWDSServer imagetype:Boot /Architecture:x64 /Filename:boot.wim /DestinationImage /Filepath:\\Server\Share\ExportImage.wim /Name:Exported WinPE image /Description:WinPE Image from WDS server /Overwrite:Yes
```

To export an install image, type either:

```
wdsutil /Export-Image image:Windows Vista with Office imagetype:Install /DestinationImage /Filepath:C:\Temp\Install.wim
```

```
wdsutil /verbose /Progress /Export-Image image:Windows Vista with Office /Server:MyWDSServer imagetype:Instal imageGroup:ImageGroup1 /Filename:install.wim /DestinationImage /Filepath:\\server\share\export.wim /Name:Exported Windows image /Description:Windows Vista image from WDS server /Overwrite:append
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-image command](wdsutil-add-image)
- [wdsutil copy-image command](wdsutil-copy-image)
- [wdsutil get-image command](wdsutil-get-image)
- [wdsutil remove-image command](wdsutil-remove-image)
- [wdsutil replace-image command](wdsutil-replace-image)
- [wdsutil set-image command](wdsutil-set-image)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)