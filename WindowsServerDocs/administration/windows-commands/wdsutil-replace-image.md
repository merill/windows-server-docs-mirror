---
layout: Conceptual
title: wdsutil replace-image | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-replace-image
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil replace-image, which replaces an existing image with a new version of that image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7667f8ac-1a39-8f09-8f7b-36c922147681
document_version_independent_id: 82f0223a-6c59-cc45-5132-f080b5bd1ef0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-replace-image.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-replace-image
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-replace-image.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0a94f90d-7fba-7587-c629-855cd3c5d42b
---

# wdsutil replace-image | Microsoft Learn

Replaces an existing image with a new version of that image.

## Syntax

for boot images:

```
WDSUTIL [Options]
        /Replace-Image
        /Image:<Image name>
        [/Server:<Server name>]
        /ImageType:Boot
        /Architecture:{x86 | x64 | arm | arm64}
        [/Filename:<File name>]
        /ReplacementImage
          /ImageFile:<WIM file path>
          [/Name:<Image name>]
          [/Description:<Image description>]

/Architecture:{x86 | x64 | arm | arm64}
        The architecture of the image to be replaced. Since it is
        possible to have the same image name for boot images in
        different architectures, specifying the architecture value
        ensures that the correct image is replaced.

[/Filename:<File name>]
        If the image cannot be uniquely identified by name, the file
        name must be specified.

/ReplacementImage
  /ImageFile:<WIM file path>
        Specifies the full path and file name of the new WIM file.

  [/Name:<Name>]
        Sets the display name of the image.

  [/Description:<Description>]
        Sets the description of the image.
```

for install images:

```
WDSUTIL [Options]
        /Replace-Image
        /Image:<Image name>
        [/Server:<Server name>]
        /ImageType:Install
        [/ImageGroup:<Image group name>]
        [/Filename:<File name>]
        /ReplacementImage
          /ImageFile:<WIM file path>
          [/SourceImage:<Source image name>]
          [/Name:<Image name>]
          [/Description:<Image description>]

[/ImageGroup:<Image group name>]
        The image group containing the image to be replaced. If not
        specified and only one image group exists on the server, that
        image group will be used by default. If more than one image
        group exists on the server, then the image group must be
        specified.

[/Filename:<File name>]
        If the image cannot be uniquely identified by name, the file
        name must be specified.

/ReplacementImage
  /ImageFile:<WIM file path>
        Specifies the full path and file name of the new WIM file.

  [/SourceImage:<image name>]
        Specifies the image to use if the new WIM file contains
        multiple images.

  [/Name:<Name>]
        Sets the display name of the image.

  [/Description:<Description>]
        Sets the description of the image.
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Image:&lt;Image name&gt; | Specifies the name of the image to be replaced. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| mediatype:{Boot | Install} | Specifies the type of image to be replaced. |
| /Architecture:{x86 | ia64 | x64} | Specifies the architecture of the image to be replaced. Because it's possible to have the same image name for different boot images in different architectures, specifying the architecture ensures that the correct image is replaced. |
| [/Filename:&lt;File name&gt;] | if the image can't be uniquely identified by name, you must use this option to specify the file name. |
| /replacementImage | Specifies the settings for the replacement image. You set these settings using the following options:<br>- mediaFile: &lt;file path&gt; - Specifies the name and location (full path) of the new .wim file.- [/SourceImage: &lt;image name&gt;] - Specifies the image to be used if the .wim file contains multiple images. This option applies only to install images.- [/Name:&lt;Image name&gt;] Sets the display name of the image.- [/Description:&lt;Image description&gt;] - Sets the description of the image. |

## Examples

To replace a boot image, type one of the following:

```
WDSUTIL /Replace-Image /Image:"WinPE Boot Image" /ImageType:Boot /Architecture:x86 /ReplacementImage /ImageFile:"C:\MyFolder\Boot.wim"

WDSUTIL /Verbose /Progress /Replace-Image /Image:"WinPE Boot Image" /Server:MyWDSServer /ImageType:Boot /Architecture:x64 /Filename:boot.wim /ReplacementImage /ImageFile:\\MyServer\Share\Boot.wim /Name:"My WinPE Image" /Description:"WinPE Image with drivers"
```

To replace an install image, type one of the following:

```
WDSUTIL /Replace-Image /Image:"Windows 10 Home"
/ImageType:Install /ReplacementImage /ImageFile:"C:\MyFolder\Install.wim"

WDSUTIL /Verbose /Progress /Replace-Image /Image:"Windows 10 Pro" /Server:MyWDSServer /ImageType:Install /ImageGroup:ImageGroup1 /Filename:Install.wim /ReplacementImage /ImageFile:\\MyServer\Share \Install.wim /SourceImage:"Windows 10 Pro" /Name:"Windows Vista Desktop" /Description:"Windows 10 Pro with standard business applications."
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-image command](wdsutil-add-image)
- [wdsutil copy-image command](wdsutil-copy-image)
- [wdsutil export-image command](wdsutil-export-image)
- [wdsutil get-image command](wdsutil-get-image)
- [wdsutil replace-image command](wdsutil-replace-image)
- [wdsutil set-image command](wdsutil-set-image)