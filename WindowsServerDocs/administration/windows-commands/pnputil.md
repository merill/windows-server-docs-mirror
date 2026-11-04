---
layout: Conceptual
title: pnputil | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pnputil
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pnputil command, which adds driver packages, removes driver packages, and lists driver packages that are in the driver store, using the pnputil.exe utility.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: c6b4c587-7bcb-b996-c366-00043ed97799
document_version_independent_id: 23fb9ac8-f6ee-ab8a-eeab-39c955e9b124
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pnputil.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pnputil
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pnputil.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 91c642a6-01a5-6102-f7c8-049ab85d0747
---

# pnputil | Microsoft Learn

Pnputil.exe is a command line utility that you can use to manage the driver store. You can use this command to add driver packages, remove driver packages, and list driver packages that are in the store.

## Syntax

```
pnputil.exe [-f | -i] [ -? | -a | -d | -e ] <INF name>
```

### Parameters

| Parameter | Description |
| --- | --- |
| -a | Specifies to add the identified INF file. |
| -d | Specifies to delete the identified INF file. |
| -e | Specifies to enumerate all third-party INF files. |
| -f | Specifies to force the deletion of the identified INF file. Can't be used in conjunction with the **-i** parameter. |
| -i | Specifies to install the identified INF file. Can't be used in conjunction with the **-f** parameter. |
| /? | Displays help at the command prompt. |

### Examples

To add an INF file, named USBCAM.INF, type:

```
pnputil.exe -a a:\usbcam\USBCAM.INF
```

To add all INF files, located in c:\drivers, type:

```
pnputil.exe -a c:\drivers\*.inf
```

To add and install the USBCAM.INF driver, type:

```
pnputil.exe -i -a a:\usbcam\USBCAM.INF
```

To enumerate all third-party drivers, type:

```
pnputil.exe -e
```

To delete the INF file and driver named oem0.inf, type:

```
pnputil.exe -d oem0.inf
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [popd command](popd)