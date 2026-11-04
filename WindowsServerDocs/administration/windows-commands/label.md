---
layout: Conceptual
title: label | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/label
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the label command, which creates, changes, or deletes the volume label (that is, the name) of a disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f3adb2eb-3c9c-d811-6979-6c23f6712d67
document_version_independent_id: bbf6f4f2-7238-04d9-488d-d3581f50d2a0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/label.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/label
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/label.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 71dd6375-8ad6-542d-e899-60590f66cc2d
---

# label | Microsoft Learn

Creates, changes, or deletes the volume label (that is, the name) of a disk. If used without parameters, the **label** command changes the current volume label or deletes the existing label.

## Syntax

```
label [/mp] [<volume>] [<label>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /mp | Specifies that the volume should be treated as a mount point or volume name. |
| `<volume>` | Specifies a drive letter (followed by a colon), mount point, or volume name. If a volume name is specified, the **/mp** parameter is unnecessary. |
| `<label>` | Specifies the label for the volume. |
| /? | Displays help at the command prompt. |

## Remarks

- Windows displays the volume label and serial number (if it has one) as part of the directory listing.
- An NTFS volume label can be up to 32 characters in length, including spaces. NTFS volume labels retain and display the case that was used when the label was created.

## Examples

To label a disk in drive A that contains sales information for July, type:

```
label a:sales-july
```

To view and delete the current label for drive C, follow these steps:

1. At the command prompt, type:

    ```
    label
    ```

    Output similar to the following should be displayed:

    ```
    Volume in drive C: is Main Disk
    Volume Serial Number is 6789-ABCD
    Volume label (32 characters, ENTER for none)?
    ```
2. Press ENTER. The following prompt should be displayed:

    ```
    Delete current volume label (Y/N)?
    ```
3. Press **Y** to delete the current label, or **N** if you want to keep the existing label.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)