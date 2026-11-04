---
layout: Conceptual
title: assoc | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/assoc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the assoc command, which displays or modifies file name extension associations.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 6ddbfcb0-76bc-5263-5754-29f5d5539522
document_version_independent_id: ac32f8da-db57-0c70-b9a8-a1f0030495e8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/assoc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/assoc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/assoc.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 72eba69e-7ee6-9408-b709-ae4605df16fa
---

# assoc | Microsoft Learn

Displays or modifies file name extension associations. If used without parameters, **assoc** displays a list of all the current file name extension associations.

Note

This command is only supported within cmd.exe and is not available from PowerShell. Though you can use `cmd /c assoc` as a workaround.

## Syntax

```
assoc [<.[ext]>[=[<filetype>]]]
```

Note

In the syntax, square brackets `[ ]` indicate optional items and angle brackets `< >` indicate placeholder values that you replace with your own text. Don't type the brackets. For example, to remove the association for the .jar file name extension, type `assoc .jar=`, not `assoc .jar=<filetype>`. If you type the angle brackets, cmd.exe treats `<` and `>` as redirection operators and returns an error. For more information, see [Command-Line Syntax Key](command-line-syntax-key).

### Parameters

| Parameter | Description |
| --- | --- |
| `<.ext>` | Specifies the file name extension. |
| `<filetype>` | Specifies the file type to associate with the specified file name extension. |
| /? | Displays help at the command prompt. |

### Remarks

- To make changes in associations, you need administrator privileges.
- To remove the file type association for a file name extension, type the extension and an equal sign with nothing after it, for example `assoc .ext=`. You don't need to add a trailing space after the equal sign.
- To associate files without extension to a file type, use just a dot (see the examples).
- To view current file types that have open command strings defined, use the **ftype** command.
- To redirect the output of **assoc** to a text file, use the `>` redirection operator.

## Examples

To view the current file type association for the file name extension .txt, type:

```
assoc .txt
```

To remove the file type association for the file name extension .bak, type:

```
assoc .bak=
```

Type nothing after the equal sign. Don't type placeholder text such as `<filetype>`, and don't add a trailing space.

To remove the file type association for the file name extension .jar, type:

```
assoc .jar=
```

To view the output of **assoc** one screen at a time, type:

```
assoc | more
```

To send the output of **assoc** to the file assoc.txt, type:

```
assoc>assoc.txt
```

Associate **.log** to text files:

```
assoc .log=txtfile
```

Associate files with no extension to text files:

```
assoc .=txtfile
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftype command](ftype)