---
layout: Conceptual
title: cd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/cd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the cd command, which displays the name of or changes the current directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 52ed71f1-2459-7f4d-0526-478187c4590d
document_version_independent_id: 9e5a0d9f-36c5-6e6b-bf46-f8a27f0ae363
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/cd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/cd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/cd.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 73787279-88d6-336a-5aaa-feb498446c3e
---

# cd | Microsoft Learn

Displays the name of the current directory or changes the current directory. If used with only a drive letter (for example, `cd C:`), **cd** displays the names of the current directory in the specified drive. If used without parameters, **cd** displays the current drive and directory.

Note

This command is the same as the [chdir command](chdir).

## Syntax

```
cd [/d] [<drive>:][<path>]
cd [..]
chdir [/d] [<drive>:][<path>]
chdir [..]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /d | Changes the current drive as well as the current directory for a drive. |
| `<drive>:` | Specifies the drive to display or change (if different from the current drive). |
| `<path>` | Specifies the path to the directory that you want to display or change. |
| [..] | Specifies that you want to change to the parent folder. |
| /? | Displays help at the command prompt. |

## Remarks

If command extensions are enabled, the following conditions apply to the **cd** command:

- The current directory string is converted to use the same case as the names on the disk. For example, `cd c:\temp` would set the current directory to C:\Temp if that is the case on the disk.
- Spaces aren't treated as delimiters, so `<path>` can contain spaces without enclosing quotation marks. For example:

    ```
    cd username\programs\start menu
    ```

    is the same as:

    ```
    cd "username\programs\start menu"
    ```

    If extensions are disabled, the quotation marks are required.
- To disable command extensions, type:

    ```
    cmd /e:off
    ```

## Examples

To return to the root directory, the top of the directory hierarchy for a drive:

```
cd\
```

To change the default directory on a drive that is different from the one you are on:

```
cd [<drive>:[<directory>]]
```

To verify the change to the directory, type:

```
cd [<drive>:]
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [chdir command](chdir)