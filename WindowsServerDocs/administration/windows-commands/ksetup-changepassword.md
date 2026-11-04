---
layout: Conceptual
title: ksetup changepassword | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-changepassword
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup changepassword command, which uses the Key Distribution Center (KDC) password (kpasswd) value to change the password of the logged-on user.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fc2ce838-fb98-a6dd-9eb8-93169446c223
document_version_independent_id: 329a80fa-ba5d-3f98-154a-424f836b186d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-changepassword.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-changepassword
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-changepassword.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 01c5dd47-8f9f-9dff-b983-61999121957c
---

# ksetup changepassword | Microsoft Learn

Uses the Key Distribution Center (KDC) password (kpasswd) value to change the password of the logged-on user. The output of the command informs you of the success or failure status.

You can check whether the **kpasswd** is set, by running the `ksetup /dumpstate` command and viewing the output.

## Syntax

```
ksetup /changepassword <oldpassword> <newpassword>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<oldpassword>` | Specifies the logged-on user's existing password. |
| `<newpassword>` | Specifies the logged on user's new password. This password must meet all the password requirements set on this computer. |

#### Remarks

- If the user account isn't found in the current domain, the system will ask you to supply the domain name where the user account resides.
- If you want to force a password change at next logon, this command allows the use of the asterisk (\*) so the user will be prompted for a new password.

### Examples

To change the password of a user who is currently logged on to this computer in this domain, type:

```
ksetup /changepassword Pas$w0rd Pa$$w0rd
```

To change the password of a user who is currently logged on in the Contoso domain, type:

```
ksetup /domain CONTOSO /changepassword Pas$w0rd Pa$$w0rd
```

To force the currently logged on user to change the password at the next logon, type:

```
ksetup /changepassword Pas$w0rd *
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup dumpstate command](ksetup-dumpstate)
- [ksetup addkpasswd command](ksetup-addkpasswd)
- [ksetup delkpasswd command](ksetup-delkpasswd)
- [ksetup dumpstate command](ksetup-dumpstate)