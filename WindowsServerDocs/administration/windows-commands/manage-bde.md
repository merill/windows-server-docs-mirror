---
layout: Conceptual
title: manage-bde | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/manage-bde
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the manage-bde command, which turns on or turns off BitLocker, specifies unlock mechanisms, updates recovery methods, and unlocks BitLocker-protected data drives.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-12-15T00:00:00.0000000Z
locale: en-us
document_id: 57c9b953-a63d-e238-9318-8363698a0de6
document_version_independent_id: 366abac3-f803-f0c6-48e0-cd2f867d95fb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/manage-bde.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/manage-bde
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/manage-bde.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7ca6e7a9-aed2-3c00-1739-e5025fdcdaaa
---

# manage-bde | Microsoft Learn

Turns on or turns off BitLocker, specifies unlock mechanisms, updates recovery methods, and unlocks BitLocker-protected data drives.

Note

This command-line tool can be used in place of the **BitLocker Drive Encryption** Control Panel item.

## Syntax

```
manage-bde [-status] [-on] [-off] [-pause] [-resume] [-lock] [-unlock] [-autounlock] [-protectors] [-tpm]
[-setidentifier] [-forcerecovery] [-changepassword] [-changepin] [-changekey] [-keypackage] [-upgrade] [-wipefreespace] [{-?|/?}] [{-help|-h}]
```

Note

Each subcommand has its own syntax, parameters, and examples. Select a subcommand link in the following table to view its detailed usage information.

### Parameters

| Parameter | Description |
| --- | --- |
| [manage-bde status](manage-bde-status) | Provides information about all drives on the computer, whether or not they are BitLocker-protected. |
| [manage-bde on](manage-bde-on) | Encrypts the drive and turns on BitLocker. |
| [manage-bde off](manage-bde-off) | Decrypts the drive and turns off BitLocker. All key protectors are removed when decryption is complete. |
| [manage-bde pause](manage-bde-pause) | Pauses encryption or decryption. |
| [manage-bde resume](manage-bde-resume) | Resumes encryption or decryption. |
| [manage-bde lock](manage-bde-lock) | Prevents access to BitLocker-protected data. |
| [manage-bde unlock](manage-bde-unlock) | Allows access to BitLocker-protected data with a recovery password or a recovery key. |
| [manage-bde autounlock](manage-bde-autounlock) | Manages automatic unlocking of data drives. |
| [manage-bde protectors](manage-bde-protectors) | Manages protection methods for the encryption key. |
| [manage-bde tpm](manage-bde-tpm) | Configures the computer's Trusted Platform Module (TPM). This command isn't supported on computers running Windows 8 or **win8\_server\_2**. To manage the TPM on these computers, use either the TPM Management MMC snap-in or the TPM Management cmdlets for Windows PowerShell. |
| [manage-bde setidentifier](manage-bde-setidentifier) | Sets the drive identifier field on the drive to the value specified in the **Provide the unique identifiers for your organization** Group Policy setting. |
| [manage-bde ForceRecovery](manage-bde-forcerecovery) | Forces a BitLocker-protected drive into recovery mode on restart. This command deletes all TPM-related key protectors from the drive. When the computer restarts, only a recovery password or recovery key can be used to unlock the drive. |
| [manage-bde changepassword](manage-bde-changepassword) | Modifies the password for a data drive. |
| [manage-bde changepin](manage-bde-changepin) | Modifies the PIN for an operating system drive. |
| [manage-bde changekey](manage-bde-changekey) | Modifies the startup key for an operating system drive. |
| [manage-bde KeyPackage](manage-bde-keypackage) | Generates a key package for a drive. |
| [manage-bde upgrade](manage-bde-upgrade) | Upgrades the BitLocker version. |
| [manage-bde WipeFreeSpace](manage-bde-wipefreespace) | Wipes the free space on a drive. |
| -? or /? | Displays brief Help at the command prompt. |
| -help or -h | Displays complete Help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Enabling BitLocker by Using the Command Line](/en-us/previous-versions/windows/it-pro/windows-7/dd894351%28v=ws.10%29)