---
layout: Conceptual
title: bdehdcfg | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bdehdcfg
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bdehdcfg command, which prepares a hard drive with the partitions necessary for BitLocker Drive Encryption.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7fedca50-9865-33ad-ccaf-e48af959f898
document_version_independent_id: f5abac60-d3f6-55a4-0c34-b6bb608f785d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bdehdcfg.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bdehdcfg
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bdehdcfg.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9d9d87b9-46b9-65d3-2858-bc2c16bc9d49
---

# bdehdcfg | Microsoft Learn

Prepares a hard drive with the partitions necessary for BitLocker Drive Encryption. Most installations of Windows 7 will not need to use this tool because BitLocker setup includes the ability to prepare and repartition drives as required.

Warning

There is a known conflict with the **Deny write access to fixed drives not protected by BitLocker** Group Policy setting located in **Computer Configuration\Administrative Templates\Windows Components\BitLocker Drive Encryption\Fixed Data Drives**.

If bdehdcfg is run on a computer when this policy setting is enabled, you may encounter the following issues:

- If you attempted to shrink the drive and create the system drive, the drive size will be successfully reduced and a raw partition will be created. However, the raw partition will not be formatted. The following error message is displayed: The new active Drive cannot be formatted. You may need to manually prepare your drive for BitLocker.
- If you attempted to use unallocated space to create the system drive, a raw partition will be created. However, the raw partition will not be formatted. The following error message is displayed: The new active Drive cannot be formatted. You may need to manually prepare your drive for BitLocker.
- If you attempted to merge an existing drive into the system drive, the tool will fail to copy the required boot file onto the target drive to create the system drive. The following error message is displayed: BitLocker setup failed to copy boot files. You may need to manually prepare your drive for BitLocker.
- If this policy setting is being enforced, a hard drive cannot be repartitioned because the drive is protected. If you are upgrading computers in your organization from a previous version of Windows and those computers were configured with a single partition, you should create the required BitLocker system partition before applying the policy setting to the computers.

## Syntax

```
bdehdcfg [-driveinfo <drive_letter>] [-target {default|unallocated|<drive_letter> shrink|<drive_letter> merge}] [-newdriveletter] [-size <size_in_mb>] [-quiet]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| [bdehdcfg: driveinfo](bdehdcfg-driveinfo) | Displays the drive letter, the total size, the maximum free space, and the partition characteristics of the partitions on the drive specified. Only valid partitions are listed. Unallocated space is not listed if four primary or extended partitions already exist. |
| [bdehdcfg: target](bdehdcfg-target) | Defines which portion of a drive to use as the system drive and makes the portion active. |
| [bdehdcfg: newdriveletter](bdehdcfg-newdriveletter) | Assigns a new drive letter to the portion of a drive used as the system drive. |
| [bdehdcfg: size](bdehdcfg-size) | Determines the size of the system partition when a new system drive is being created. |
| [bdehdcfg: quiet](bdehdcfg-quiet) | Prevents the display of all actions and errors in the command-line interface and directs bdehdcfg to use the Yes answer to any Yes/No prompts that may occur during subsequent drive preparation. |
| [bdehdcfg: restart](bdehdcfg-restart) | Directs the computer to restart after the drive preparation has finished. |
| /? | Displays Help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)