---
layout: Conceptual
title: refsutil fixboot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil-fixboot
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil fixboot tool, which repairs or updates the boot sector of a ReFS (Resilient File System) volume in Windows.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-02T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 98bfa12c-60f9-f330-41df-99594abb1ff3
document_version_independent_id: 98bfa12c-60f9-f330-41df-99594abb1ff3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil-fixboot.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil-fixboot
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil-fixboot.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 102b02e0-b69b-ce8a-61eb-e0a6ee961c8f
---

# refsutil fixboot | Microsoft Learn

The `refsutil fixboot` command repairs or updates the boot sector of a specified ReFS (Resilient File System) volume. It ensures the boot sector is correctly configured based on the provided drive, version, and cluster size.

Warning

This operation modifies the boot sector(s) of a volume and may lead to complete data loss. Proceed with caution.

## Syntax

```
refsutil fixboot <drive> <MajorVersion> <MinorVersion> <ClusterSize> [-f] [-w <Dir>] [-smr <SMRBandSizeInMB>] [-x]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `<drive>` | Specifies the drive letter of the volume to be fixed in the format `E:`. |
| `<MajorVersion>` | Specifies the major version of the ReFS volume. |
| `<MinorVersion>` | Specifies the minor version of the ReFS volume. |
| `<ClusterSize>` | Specifies the cluster size of the volume, either 4096 or 65536 bytes. |
| `-f` | Forces the operation to ignore any valid boot sector found and fix the boot sector based on the provided parameters. |
| `-w <Dir>` | Writes the changes to one or more boot sectors if needed and backs up one or more current boot sectors into the specified backup directory `<DIR>`. |
| `-smr <SMRBandSizeInMB>` | Specifies that the volume is in SMR (Shingled Magnetic Recording) format. The cluster size must be 65536 bytes. `SMRBandSizeinMB` can be either 128 MB or 256 MB. |
| `-x` | Forces the volume to dismount if necessary and invalidates all open handles to the volume. |

## Examples

To fix the boot sector of a ReFS volume on drive D: with a major version of 3, minor version of 3, and a cluster size of `4096` bytes, run this command:

```
refsutil fixboot D: 3 3 4096
```

To fix the boot sector of the ReFS volume on drive D: with a major version of 2, minor version of 1, and a cluster size of `65536` bytes, run the following command. This command forces the operation to ignore any valid boot sector found and writes the necessary changes to the boot sector, then backing up the boot sector into the directory `C:\Backup`:

```
refsutil fixboot D: 2 1 65536 -f -w C:\Backup
```

To fix the boot sector of the ReFS volume on drive D: with a major version of 2, minor version of 0, and a cluster size of `65536` bytes, run the following command. The command specifies that the volume is in SMR format with a band size of 128 MB:

```
refsutil fixboot D: 2 0 65536 -smr 128
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)