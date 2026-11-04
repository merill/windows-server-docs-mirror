---
layout: Conceptual
title: fsutil resource | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-resource
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil resource command, which manages a Transactional Resource Manager and its behavior.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 103a059e-9079-9e7c-cbb3-95cde62384a0
document_version_independent_id: 4bde29e5-d6ce-28fc-633a-60bdc624ebd5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-resource.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-resource
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-resource.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
platformId: 53b0da85-32c6-5968-970e-89bb5aef6418
---

# fsutil resource | Microsoft Learn

Creates a Secondary Transactional Resource Manager, starts or stops a Transactional Resource Manager, or displays information about a Transactional Resource Manager, and modifies the following behavior:

- Whether a default Transactional Resource Manager cleans its transactional metadata at the next mount.
- The specified Transactional Resource Manager to prefer consistency over availability.
- The specified Transaction Resource Manager to prefer availability over consistency.
- The characteristics of a running Transactional Resource Manager.

## Syntax

```
fsutil resource [create] <rmrootpathname>
fsutil resource [info] <rmrootpathname>
fsutil resource [setautoreset] {true|false} <Defaultrmrootpathname>
fsutil resource [setavailable] <rmrootpathname>
fsutil resource [setconsistent] <rmrootpathname>
fsutil resource [setlog] [growth {<containers> containers|<percent> percent} <rmrootpathname>] [maxextents <containers> <rmrootpathname>] [minextents <containers> <rmrootpathname>] [mode {full|undo} <rmrootpathname>] [rename <rmrootpathname>] [shrink <percent> <rmrootpathname>] [size <containers> <rmrootpathname>]
fsutil resource [start] <rmrootpathname> [<rmlogpathname> <tmlogpathname>
fsutil resource [stop] <rmrootpathname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| create | Creates a secondary Transactional Resource Manager. |
| `<rmrootpathname>` | Specifies the full path to a Transactional Resource Manager root directory. |
| info | Displays the specified Transactional Resource Manager's information. |
| setautoreset | Specifies whether a default Transactional Resource Manager will clean the transactional metadata on the next mount.<br>- **true** - Specifies that the Transaction Resource Manager will clean the transactional metadata on the next mount, by default.<br>- **false** - Specifies that the Transaction Resource Manager will not clean the transactional metadata on the next mount, by default. |
| `<defaultrmrootpathname>` | Specifies the drive name followed by a colon. |
| setavailable | Specifies that a Transactional Resource Manager will prefer availability over consistency. |
| setconsistent | Specifies that a Transactional Resource Manager will prefer consistency over availability. |
| setlog | Changes the characteristics of a Transactional Resource Manager that is already running. |
| growth | Specifies the amount by which the Transactional Resource Manager log can grow.<br>The growth parameter can be specified as follows:<br><br>- Number of containers, using the format: `<containers> containers`<br>- Percentage, using the format: `<percent> percent` |
| `<containers>` | Specifies the data objects that are used by the Transactional Resource Manager. |
| maxextent | Specifies the maximum number of containers for the specified Transactional Resource Manager. |
| minextent | Specifies the minimum number of containers for the specified Transactional Resource Manager. |
| mode `{full|undo}` | Specifies whether all transactions are logged ( **full**) or only rolled back events are logged (**undo**). |
| rename | Changes the GUID for the Transactional Resource Manager. |
| shrink | Specifies percentage by which the Transactional Resource Manager log can automatically decrease. |
| size | Specifies the size of the Transactional Resource Manager as a specified number of *containers*. |
| start | Starts the specified Transactional Resource Manager. |
| stop | Stops the specified Transactional Resource Manager. |

### Examples

To set the log for the Transactional Resource Manager that is specified by *c:\test*, to have an automatic growth of five containers, type:

```
fsutil resource setlog growth 5 containers c:test
```

To set the log for the Transactional Resource Manager that is specified by *c:\test*, to have an automatic growth of two percent, type:

```
fsutil resource setlog growth 2 percent c:test
```

To specify that the default Transactional Resource Manager will clean the transactional metadata on the next mount on drive C, type:

```
fsutil resource setautoreset true c:\
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)
- [Transactional NTFS](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc730726%28v=ws.10%29)