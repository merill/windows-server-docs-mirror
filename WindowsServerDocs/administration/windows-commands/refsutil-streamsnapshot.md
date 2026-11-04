---
layout: Conceptual
title: refsutil streamsnapshot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil-streamsnapshot
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil streamsnapshot tool, which manages Resilient File System (ReFS) data stream snapshots where you can create, delete, list, or compare snapshots in Windows.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-02T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: fc8ef60f-1a85-7f9e-a3f3-3af2903389d0
document_version_independent_id: fc8ef60f-1a85-7f9e-a3f3-3af2903389d0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil-streamsnapshot.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil-streamsnapshot
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil-streamsnapshot.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d774b87-7dcb-40bf-a0b9-5a7a9efff0d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/89dc5f37-0e4e-4b05-ad87-5fcd2b941a8a
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f52d34a3-2eae-9d7b-74da-22e7ddbfb3cd
---

# refsutil streamsnapshot | Microsoft Learn

The `refsutil streamsnapshot` command allows you to manage snapshots of data streams within files in the Resilient File System (ReFS). You can create, delete, list, or compare snapshots of data streams at specified points in time. The `file.dat` file contains the data streams for which you want to create, delete, list, or compare snapshots. Essentially, it's the target file upon which this utility performs its operations.

## Syntax

```
refsutil streamsnapshot [/c <name>] [/l] [/d <name>] [/q <name>] <file[:stream]>
```

## Parameters

| Parameter | Description |
| --- | --- |
| `/c <name>` | Creates a snapshot named `<name>` of the stream specified by `file[:stream]` at the current point in time. This option is mutually exclusive with `/d`, `/l`, and `/q`. |
| `/d <name>` | Deletes the snapshot named `<name>` from the specified file `<file>`. This parameter ignores the `[:stream]` portion of the file path and is mutually exclusive with `/c`, `/l`, and `/q`. |
| `/l <name>` | Lists all snapshots for the stream specified by `file[:stream]` that match the given `<name>`. Wildcards are allowed in `<name>`. This parameter is mutually exclusive with `/c`, `/d`, and `/q`. |
| `/q <name>` | Lists all modifications between the snapshot `<name>` and the current state of the stream specified by `[:stream]`. Both must reference streams in the same snapshot chain, with `<name>` being older than `[:stream]`. This parameter is mutually exclusive with `/c`, `/d`, and `/l`. |

Note

If `[:stream]` isn't provided, this utility acts on the default unnamed data stream, `$DATA`.

## Examples

To create a snapshot named "snapshot\_jan\_2024" of the stream at the current point in time, run the following command:

```
refsutil streamsnapshot /c "snapshot_jan_2024" C:\file.dat
```

To delete a snapshot named "snapshot\_jan\_2024" from the file, run the following command:

```
refsutil streamsnapshot /d "snapshot_jan_2024" C:\file.dat
```

To list all snapshots for the stream in the file matching any pattern using the `*` wildcard, run the following command:

```
refsutil streamsnapshot /l "*" C:\file.dat
```

To list all modifications between the snapshot "snapshot\_jan\_2024" and the stream "snapshot\_feb\_2024", run the following command:

```
refsutil streamsnapshot /q "snapshot_jan_2024" C:\file.dat:snapshot_feb_2024
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)