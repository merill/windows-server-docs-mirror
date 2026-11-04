---
layout: Conceptual
title: ReFS integrity streams | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/refs/integrity-streams
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: 'Learn more about: ReFS integrity streams'
author: robinharwood
ms.author: roharwoo
ms.date: 2018-10-16T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: aa4f8adc-7422-04df-56a8-3b16f73a5e2d
document_version_independent_id: a5b7899f-d1f1-3e58-01c4-858291128be7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/refs/integrity-streams.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/refs/integrity-streams
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/refs/integrity-streams.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d774b87-7dcb-40bf-a0b9-5a7a9efff0d1
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/89dc5f37-0e4e-4b05-ad87-5fcd2b941a8a
platformId: 39d0a7a1-5c7f-2312-f012-47488bb517b1
---

# ReFS integrity streams | Microsoft Learn

Integrity streams is an optional feature in ReFS that validates and maintains data integrity using checksums. While ReFS always uses checksums for metadata, ReFS doesn't, by default, generate or validate checksums for file data. Integrity streams is an optional feature that allows users to utilize checksums for file data. When integrity streams are enabled, ReFS can clearly determine if data is valid or corrupt. Additionally, ReFS and Storage Spaces can jointly correct corrupt metadata and data automatically.

## How it works

Integrity streams can be enabled for individual files, directories, or the entire volume, and integrity stream settings can be toggled at any time. Additionally, integrity stream settings for files and directories are inherited from their parent directories.

Once integrity streams is enabled, ReFS will create and maintain a checksum for the specified file(s) in that file's metadata. This checksum allows ReFS to validate the integrity of the data before accessing it. Before returning any data that has integrity streams enabled, ReFS will first calculate its checksum:

![Compute checksum for file data](media/compute-checksum.gif)

Then, this checksum is compared to the checksum contained in the file metadata. If the checksums match, then the data is marked as valid and returned to the user. If the checksums don't match, then the data is corrupt. The resiliency of the volume determines how ReFS responds to corruptions:

- If ReFS is mounted on a non-resilient simple space or a bare drive, ReFS will return an error to the user without returning the corrupted data.
- If ReFS is mounted on a resilient mirror or parity space, ReFS will attempt to correct the corruption.
    - If the attempt is successful, ReFS will apply a corrective write to restore the integrity of the data, and it will return the valid data to the application. The application remains unaware of any corruptions.
    - If the attempt is unsuccessful, ReFS will return an error.

ReFS will record all corruptions in the System Event Log, and the log will reflect whether the corruptions were fixed.

![Corrective write restores data integrity](media/corrective-write.gif)

## Performance

Though integrity streams provides greater data integrity for the system, it also incurs a performance cost. There are a couple different reasons for this:

- If integrity streams are enabled, all write operations become allocate-on-write operations. Though this avoids any read-modify-write bottlenecks since ReFS doesn't need to read or modify any existing data, file data frequently becomes fragmented, which delays reads.
- Depending on the workload and underlying storage of the system, the computational cost of computing and validating the checksum can cause IO latency to increase.

Because integrity streams carries a performance cost, we recommend leaving integrity streams disabled on performance sensitive systems.

## Integrity scrubber

As described above, ReFS will automatically validate data integrity before accessing any data. ReFS also uses a background scrubber, which enables ReFS to validate infrequently accessed data. This scrubber periodically scans the volume, identifies latent corruptions, and proactively triggers a repair of any corrupt data.

Note

The data integrity scrubber can only validate file data for files where integrity streams is enabled.

By default, the scrubber runs every four weeks, though this interval can be configured within Task Scheduler under Microsoft\Windows\Data Integrity Scan.

## Examples

To monitor and change the file data integrity settings, ReFS uses the **Get-FileIntegrity** and **Set-FileIntegrity** cmdlets.

### Get-FileIntegrity

To see if integrity streams is enabled for file data, use the **Get-FileIntegrity** cmdlet.

```PowerShell
PS C:\> Get-FileIntegrity -FileName 'C:\Docs\TextDocument.txt'
```

You can also use the **Get-Item** cmdlet to get the integrity stream settings for all the files in a specified directory.

```PowerShell
PS C:\> Get-Item -Path 'C:\Docs\*' | Get-FileIntegrity
```

### Set-FileIntegrity

To enable/disable integrity streams for file data, use the **Set-FileIntegrity** cmdlet.

```PowerShell
PS C:\> Set-FileIntegrity -FileName 'H:\Docs\TextDocument.txt' -Enable $True
```

You can also use the **Get-Item** cmdlet to set the integrity stream settings for all the files in a specified folder.

```PowerShell
PS C:\> Get-Item -Path 'H\Docs\*' | Set-FileIntegrity -Enable $True
```

The **Set-FileIntegrity** cmdlet can also be used on volumes and directories directly.

```PowerShell
PS C:\> Set-FileIntegrity H:\ -Enable $True
PS C:\> Set-FileIntegrity H:\Docs -Enable $True
```

## Additional References

- [ReFS overview](refs-overview)
- [ReFS block cloning](block-cloning)
- [Storage Spaces Direct overview](../storage-spaces/storage-spaces-direct-overview)