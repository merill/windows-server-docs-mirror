---
layout: Conceptual
title: repair-bde | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/repair-bde
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the repair-bde command, which can try to reconstruct critical parts of a severely damaged drive and salvage recoverable data if the drive was encrypted by using BitLocker.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4006b303-a81e-8de3-e75e-23dd7d097111
document_version_independent_id: af6d19cc-90f1-38e8-60cd-03b64a97f532
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/repair-bde.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/repair-bde
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/repair-bde.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c6e3f8e4-a5cb-15f5-0749-90afa9b96c37
---

# repair-bde | Microsoft Learn

Attempts to reconstruct critical parts of a severely damaged drive and salvage recoverable data if the drive was encrypted by using BitLocker and if it has a valid recovery password or recovery key for decryption.

Important

If the BitLocker metadata data on the drive is corrupt, you must be able to supply a backup key package in addition to the recovery password or recovery key. If you used the default key back up setting for Active Directory Domain Services, your key package is backed up there. You can use the [BitLocker: Use BitLocker Recovery Password Viewer](/en-us/troubleshoot/windows-server/windows-security/bitlocker-recovery-password-viewer-tool) to obtain the key package from AD DS.

Using the key package and either the recovery password or recovery key, you can decrypt portions of a BitLocker-protected drive, even if the disk is corrupted. Each key package works only for a drive with the corresponding drive identifier.

## Syntax

```
repair-bde <inputvolume> <outputvolumeorimage> [-rk] [-rp] [-pw] [-kp] [-lf] [-f] [{-?|/?}]
```

Warning

The contents of the output volume will be **completely deleted and overwritten** by the decrypted contents from the damaged BitLocker drive. If you want to save any existing data on the selected target drive, move the existing data to other reliable backup media first, before running the `repair-bde` command.

### Parameters

| Parameter | Description |
| --- | --- |
| `<inputvolume>` | Identifies the drive letter of the BitLocker-encrypted drive that you want to repair. The drive letter must include a colon; for example: **C:**. If the path to a key package isn't specified, this command searches the drive for a key package. In the event that the hard drive is damaged, this command might not be able to find the package and will prompt you to provide the path. |
| `<outputvolumeorimage>` | Identifies the drive on which to store the content of the repaired drive. All information on the output drive will be overwritten. |
| -rk | Identifies the location of the recovery key that should be used to unlock the volume. This command can also be specified as **-recoverykey**. |
| -rp | Identifies the numerical recovery password that should be used to unlock the volume. This command can also be specified as **-recoverypassword**. |
| -pw | Identifies the password that should be used to unlock the volume. This command can also be specified as **-password** |
| -kp | Identifies the recovery key package that can be used to unlock the volume. This command can also be specified as **-keypackage**. |
| -lf | Specifies the path to the file that will store Repair-bde error, warning, and information messages. This command may also be specified as **-logfile**. |
| -f | Forces a volume to be dismounted even if it cannot be locked. This command can also be specified as **-force**. |
| -? or /? | Displays Help at the command prompt. |

### Limitations

The following limitations exist for the this command:

- This command can't repair a drive that failed during the encryption or decryption process.
- This command assumes that if the drive has any encryption, then the drive has been fully encrypted.

## Examples

To attempt to repair drive C:, to write the content from drive C: to drive D: using the recovery key file (RecoveryKey.bek) stored on drive F:, and to write the results of this attempt to the log file (log.txt) on drive Z:, type:

```
repair-bde C: D: -rk F:\RecoveryKey.bek -lf Z:\log.txt
```

To attempt to repair drive C: and to write the content from drive C: to drive D: using the 48-digit recovery password specified, type:

```
repair-bde C: D: -rp 111111-222222-333333-444444-555555-666666-777777-888888
```

Note

The recovery password should be typed in eight blocks of six digits with a hyphen separating each block.

To force drive C: to dismount, attempt to repair drive C:, and then to write the content from drive C: to drive D: using the recovery key package and recovery key file (RecoveryKey.bek) stored on drive F:, type:

```
repair-bde C: D: -kp F:\RecoveryKeyPackage -rk F:\RecoveryKey.bek -f
```

To attempt to repair drive C: and to write the content from drive C: to drive D:, where you must type a password to unlock drive C: (when prompted), type:

```
repair-bde C: D: -pw
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)