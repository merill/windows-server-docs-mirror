---
layout: Conceptual
title: attrib | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/attrib
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the attrib command that displays, sets, or removes attributes assigned to files or directories.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-09-22T00:00:00.0000000Z
locale: en-us
document_id: 62650d46-4208-8880-2c41-1d7220bfdd89
document_version_independent_id: 9577a78a-7c08-0e57-d507-a7e96a335660
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/attrib.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/attrib
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/attrib.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 37fc89cf-27d6-4882-cf59-b6ab79990d33
---

# attrib | Microsoft Learn

Displays, sets, or removes attributes assigned to files or directories. If used without parameters, **attrib** displays attributes of all files in the current directory.

## Syntax

```
attrib [{+|-}r] [{+|-}a] [{+|-}s] [{+|-}h] [{+|-}o] [{+|-}i] [{+|-}x] [{+|-}p] [{+|-}u] [{+|-}b] [<drive>:][<path>][<filename>] [/s [/d] [/l]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `{+\|-}r` | Sets (**+**) or clears (**-**) the Read-only file attribute. |
| `{+\|-}a` | Sets (**+**) or clears (**-**) the Archive file attribute. This attribute set marks files that have changed since the last time they were backed up. The **xcopy** command uses archive attributes. |
| `{+\|-}s` | Sets (**+**) or clears (**-**) the System file attribute. If a file uses this attribute set, you must clear the attribute before you can change any other attributes for the file. |
| `{+\|-}h` | Sets (**+**) or clears (**-**) the Hidden file attribute. If a file uses this attribute set, you must clear the attribute before you can change any other attributes for the file. |
| `{+\|-}o` | Sets (**+**) or clears (**-**) the Offline file attribute. |
| `{+\|-}i` | Sets (**+**) or clears (**-**) the Not Content Indexed file attribute. |
| `{+\|-}x` | Sets (**+**) or clears (**-**) the Scrub file attribute. |
| `{+\|-}p` | Sets (**+**) or clears (**-**) the Pinned file attribute. |
| `{+\|-}u` | Sets (**+**) or clears (**-**) the Unpinned file attribute. |
| `{+\|-}b` | Sets (**+**) or clears (**-**) the SMR Blob file attribute. |
| `[<drive>:][<path>][<filename>]` | Specifies the location and name of the directory, file, or group of files that you want to view or change attributes.You can use the **?** and **\*** wildcard characters in the *filename* parameter to display or change the attributes for a group of files. |
| /s | Applies **attrib** and any command-line options to matching files in the current directory and all of its subdirectories. |
| /d | Applies **attrib** and any command-line options to directories. |
| /l | Applies **attrib** and any command-line options to the Symbolic Link, rather than the target of the Symbolic Link. |
| /? | Displays help at the command prompt. |

## Examples

To display the attributes of a file named News86 that is located in the current directory, type:

```
attrib news86
```

To assign the Read-only attribute to the file named report.txt, type:

```
attrib +r report.txt
```

To remove the Read-only attribute from files in the public directory and its subdirectories on a disk in drive b:, type:

```
attrib -r b:\public\*.* /s
```

To set the Archive attribute for all files on drive a:, and then clear the Archive attribute for files with the .bak extension, type:

```
attrib +a a:*.* & attrib -a a:*.bak
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [xcopy command](xcopy)