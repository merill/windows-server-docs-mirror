---
layout: Conceptual
title: ftype | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftype
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftype command, which displays or modifies file type used in file name extension associations.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 82c6afb5-a5de-1ae1-3d52-11b521e0eba1
document_version_independent_id: 7ba91c7d-8f3a-706c-01ce-b363fb28364b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftype.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftype
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftype.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1f311345-5900-7fe4-cc53-5dfc56654240
---

# ftype | Microsoft Learn

Displays or modifies file types that are used in file name extension associations. If used without an assignment operator (=), this command displays the current open command string for the specified file type. If used without parameters, this command displays the file types that have open command strings defined.

Note

This command is only supported within cmd.exe and is not available from PowerShell. Though you can use `cmd /c ftype` as a workaround.

## Syntax

```
ftype [<filetype>[=[<opencommandstring>]]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<filetype>` | Specifies the file type to display or change. |
| `<opencommandstring>` | Specifies the open command string to use when opening files of the specified file type. |
| /? | Displays help at the command prompt. |

#### Remarks

The following table describes how **ftype** substitutes variables within an open command string:

| Variable | Replacement value |
| --- | --- |
| `%0` or `%1` | Gets substituted with the file name being launched through the association. |
| `%*` | Gets all of the parameters. |
| `%2`, `%3`, ... | Gets the first parameter (`%2`), the second parameter (`%3`), and so on. |
| `%~<n>` | Gets all of the remaining parameters starting with the *n*th parameter, where *n* can be any number from 2 to 9. |

### Examples

To display the current file types that have open command strings defined, type:

```
ftype
```

To display the current open command string for the *txtfile* file type, type:

```
ftype txtfile
```

This command produces output similar to the following:

`txtfile=%SystemRoot%\system32\NOTEPAD.EXE %1`

To delete the open command string for a file type called *example*, type:

```
ftype example=
```

To associate the .pl file name extension with the PerlScript file type and enable the PerlScript file type to run PERL.EXE, type the following commands:

```
assoc .pl=PerlScript
ftype PerlScript=perl.exe %1 %*
```

To eliminate the need to type the .pl file name extension when invoking a Perl script, type:

```
set PATHEXT=.pl;%PATHEXT%
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)