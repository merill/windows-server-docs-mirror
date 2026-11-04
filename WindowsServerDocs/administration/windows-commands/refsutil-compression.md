---
layout: Conceptual
title: refsutil compression | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil-compression
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil compression tool, which queries or modifies compression settings on a Resilient File System (ReFS) volume in Windows.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-02T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: aa05967d-709a-b81b-59a8-4b6251194ae7
document_version_independent_id: aa05967d-709a-b81b-59a8-4b6251194ae7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil-compression.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil-compression
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil-compression.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7eae42d7-9bca-958b-4b6f-2ecb0a300847
---

# refsutil compression | Microsoft Learn

The `refsutil compression` command is used to query or set the compression parameters on a specified Resilient File System (ReFS) volume. You can check the current compression status, apply compression using different formats, or decompress a compressed volume.

## Syntax

```
refsutil compression <drive> <[/q]> | <[/c] [/f <format>] [/e <engine>] [/cs <size>]>
```

## Parameters

| Parameters | Description |
| --- | --- |
| `<drive>` | Specifies the drive letter of the volume to be compressed in the format `E:`. |
| `/q` | Queries the volume's current compression parameters. |
| `/c` | Compresses the volume with the specified compression parameters. |
| `/f <format>` | Specifies the compression format to use. Valid options include:- `LZ4`: A fast compression algorithm.<br>- `ZSTD`: A compression algorithm that offers a good balance between compression ratio and speed.<br>- `NONE`: Used to *decompress* a previously compressed volume. When using `NONE`, omit the engine and compression chunk size parameters. |
| `/e <engine>` | Defines the compression level to use, which varies by format:- `LZ4`: Levels `1`, `3-12`. The default is `1`. Levels `3-12` use the LZ4HC algorithm, which provides higher compression ratios at the cost of slower compression speeds.<br>- `ZSTD`: Levels `1-22`. The default is `3`. Higher levels provide better compression ratios but reduce compression speed and might require more memory (especially levels `20` and greater). Decompression speed remains consistent regardless of the chosen compression level.<br> Omitting the `/e` parameter or using the value `0` sets the default level for any given compression format. |
| `/cs <size>` | Specifies the compression chunk size in bytes. This value must be to the power of two (2^*n*), at least equal to the volume's cluster size, and no greater than `64MB`. Larger chunk sizes can enhance compression ratios but might negatively impact read performance for smaller data amounts. Beyond `1MB`, the benefits diminish significantly, so larger sizes aren't recommended. If omitted or set to `0`, the volume's cluster size is used. |

Note

For the `/e` parameter, the default compression values are subject to change.

## Examples

To query the F: volume compression parameters, run the command:

```
refsutil compression F: /q
```

To compress the F: volume using the `LZ4` format with level 12 compression and a chunk size of 524,288 bytes (512 KB), run the command:

```
refsutil compression F: /c /f LZ4 /e 12 /cs 524288
```

To compress the F: volume using the `ZSTD` format with level 15 compression and a chunk size of 131,072 bytes (128 KB), run the command:

```
refsutil compression F: /c /f ZSTD /e 15 /cs 131072
```

To compress the F: volume using the `ZSTD` format with default compression parameters, run the command:

```
refsutil compression F: /c /f ZSTD
```

To decompress the F: volume, run the command:

```
refsutil compression F: /c /f NONE
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)