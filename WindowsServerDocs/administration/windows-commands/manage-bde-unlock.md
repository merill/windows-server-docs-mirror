---
layout: Conceptual
title: manage-bde unlock | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/manage-bde-unlock
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the manage-bde unlock command, which unlocks a BitLocker-protected drive by using a recovery password or a recovery key.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-01-17T00:00:00.0000000Z
locale: en-us
document_id: 4a504df6-57a1-96a8-e00b-971fd9a3ed0b
document_version_independent_id: a9fe4704-fc82-2eca-cfc2-981e805e73a6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/manage-bde-unlock.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/manage-bde-unlock
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/manage-bde-unlock.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 20e80471-54cd-06a1-4d10-733e12cc7b4c
---

# manage-bde unlock | Microsoft Learn

Unlocks a BitLocker-protected drive by using a recovery password or a recovery key.

## Syntax

```
manage-bde -unlock {-recoverypassword -password | -recoverykey <pathtoexternalkeyfile>} <drive> [-certificate {-cf pathtocertificatefile | -ct certificatethumbprint} {-pin}] [-password] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -recoverypassword | Specifies that a recovery password will be used to unlock the drive. You can also use **-rp** as an abbreviated version of this command. This is the recovery key that's saved to a text file and must be written exactly as shown including dashes. |
| -password | Represents the recovery password that can be used to unlock the drive that either you or your administrator has set. |
| -recoverykey | Specifies that an external recovery key file will be used to unlock the drive. You can also use **-rk** as an abbreviated version of this command. This method searches for the **.bek** recovery key file that is saved to a USB drive. |
| `<pathtoexternalkeyfile>` | Represents the external recovery key file that can be used to unlock the drive. |
| `<drive>` | Represents a drive letter followed by a colon. |
| -certificate | The local user certificate for a BitLocker certificate to unlock the volume is located in the local user certificate store. You can also use **-cert** as an abbreviated version of this command. |
| -cf `<pathtocertificatefile>` | Path to the certificate file. |
| -ct `<certificatethumbprint>` | Certificate thumbprint which may optionally include the PIN (-pin). |
| -password | Presents a prompt for the password to unlock the volume. You can also use **-pw** as an abbreviated version of this command. |
| -computername | Specifies that manage-bde.exe will be used to modify BitLocker protection on a different computer. You can also use **-cn** as an abbreviated version of this command. |
| `<name>` | Represents the name of the computer on which to modify BitLocker protection. Accepted values include the computer's NetBIOS name and the computer's IP address. |
| -? or /? | Displays brief Help at the command prompt. |
| -help or -h | Displays complete Help at the command prompt. |

### Examples

To unlock drive E with a password, type:

```cmd
manage-bde -unlock E: -password
```

To unlock drive E with a recovery password, type:

```cmd
manage-bde -unlock E: -recoverypassword xxxxxx-xxxxxx-xxxxxx-xxxxxx-xxxxxx-xxxxxx-xxxxxx-xxxxxx
```

To unlock drive E with a recovery key file that's been saved to a backup folder on another drive, type:

```cmd
manage-bde -unlock E: -recoverykey F:\Backupkeys\recoverykey.bek
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [manage-bde command](manage-bde)