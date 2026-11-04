---
layout: Conceptual
title: manage-bde on | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/manage-bde-on
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the manage-bde on command, which encrypts the drive and turns on BitLocker.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 89b24529-dea2-66a9-5b3d-5ac74f34a017
document_version_independent_id: f50a742f-9c10-d895-c64d-1e08dad8cfd7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/manage-bde-on.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/manage-bde-on
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/manage-bde-on.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7f2c34fa-012e-289a-5a7e-2d2825e880d4
---

# manage-bde on | Microsoft Learn

Encrypts the drive and turns on BitLocker.

## Syntax

```
manage-bde -on <drive> {[-recoverypassword <numericalpassword>]|[-recoverykey <pathtoexternaldirectory>]|[-startupkey <pathtoexternalkeydirectory>]|[-certificate]|
[-tpmandpin]|[-tpmandpinandstartupkey <pathtoexternalkeydirectory>]|[-tpmandstartupkey <pathtoexternalkeydirectory>]|[-password]|[-ADaccountorgroup <domain\account>]}
[-usedspaceonly][-encryptionmethod {aes128_diffuser|aes256_diffuser|aes128|aes256}] [-skiphardwaretest] [-discoveryvolumetype <filesystemtype>] [-forceencryptiontype <type>] [-removevolumeshadowcopies][-computername <name>]
[{-?|/?}] [{-help|-h}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<drive>` | Represents a drive letter followed by a colon. |
| -recoverypassword | Adds a numerical password protector. You can also use **-rp** as an abbreviated version of this command. |
| `<numericalpassword>` | Represents the recovery password. |
| -recoverykey | Adds an external key protector for recovery. You can also use **-rk** as an abbreviated version of this command. |
| `<pathtoexternaldirectory>` | Represents the directory path to the recovery key. |
| -startupkey | Adds an external key protector for startup. You can also use **-sk** as an abbreviated version of this command. |
| `<pathtoexternalkeydirectory>` | Represents the directory path to the startup key. |
| -certificate | Adds a public key protector for a data drive. You can also use **-cert** as an abbreviated version of this command. |
| -tpmandpin | Adds a Trusted Platform Module (TPM) and personal identification number (PIN) protector for the operating system drive. You can also use **-tp** as an abbreviated version of this command. |
| -tpmandstartupkey | Adds a TPM and startup key protector for the operating system drive. You can also use **-tsk** as an abbreviated version of this command. |
| -tpmandpinandstartupkey | Adds a TPM, PIN, and startup key protector for the operating system drive. You can also use **-tpsk** as an abbreviated version of this command. |
| -password | Adds a password key protector for the data drive. You can also use **-pw** as an abbreviated version of this command. |
| -ADaccountorgroup | Adds a SID-based identity protector for the volume. The volume will automatically unlock if the user or computer has the proper credentials. When specifying a computer account, append a **$** to the computer name and specify **-service** to indicate that the unlock should happen in the content of the BitLocker server instead of the user. You can also use **-sid** as an abbreviated version of this command. |
| -usedspaceonly | Sets the encryption mode to Used Space Only encryption. The sections of the volume containing used space will be encrypted but the free space will not. If this option is not specified, all used space and free space on the volume will be encrypted. You can also use **-used** as an abbreviated version of this command. |
| -encryptionMethod | Configures the encryption algorithm and key size. You can also use **-em** as an abbreviated version of this command. |
| -skiphardwaretest | Begins encryption without a hardware test. You can also use **-s** as an abbreviated version of this command. |
| -discoveryvolumetype | Specifies the file system to use for the discovery data drive. The discovery data drive is a hidden drive added to a FAT-formatted, BitLocker-protected removable data drive that contains the BitLocker To Go Reader. |
| -forceencryptiontype | Forces BitLocker to use either software or hardware encryption. You can specify either **Hardware** or **Software** as the encryption type. If the **hardware** parameter is selected, but the drive doesn't support hardware encryption, manage-bde returns an error. If Group Policy settings forbids the specified encryption type, manage-bde returns an error. You can also use **-fet** as an abbreviated version of this command. |
| -removevolumeshadowcopies | Force deletion of Volume Shadow Copies for the volume. You won't be able to restore this volume using previous system restore points after running this command. You can also use **-rvsc** as an abbreviated version of this command. |
| `<filesystemtype>` | Specifies which file systems can be used with discovery data drives: FAT32, default, or none. |
| -computername | Specifies that manage-bde is being used to modify BitLocker protection on a different computer. You can also use **-cn** as an abbreviated version of this command. |
| `<name>` | Represents the name of the computer on which to modify BitLocker protection. Accepted values include the computer's NetBIOS name and the computer's IP address. |
| -? or /? | Displays brief Help at the command prompt. |
| -help or -h | Displays complete Help at the command prompt. |

### Examples

To turn on BitLocker for drive C, and to add a recovery password to the drive, type:

```
manage-bde -on C: -recoverypassword
```

To turn on BitLocker for drive C, add a recovery password to the drive, and to save a recovery key to drive E, type:

```
manage-bde -on C: -recoverykey E:\ -recoverypassword
```

To turn on BitLocker for drive C, using an external key protector (such as a USB key) to unlock the operating system drive, type:

```
manage-bde -on C: -startupkey E:\
```

Important

This method is required if you are using BitLocker with computers that don't have a TPM.

To turn on BitLocker for data drive E, and to add a password key protector, type:

```
manage-bde -on E: -pw
```

To turn on BitLocker for operating system drive C, and to use hardware-based encryption, type:

```
manage-bde -on C: -fet hardware
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [manage-bde off command](manage-bde-off)
- [manage-bde pause command](manage-bde-pause)
- [manage-bde resume command](manage-bde-resume)
- [manage-bde command](manage-bde)