---
layout: Conceptual
title: tsprof | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tsprof
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tsprof command, which copies the Remote Desktop Services user configuration information from one user to another.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d7daa1ac-11e9-8b51-9769-08ee4a2de508
document_version_independent_id: 593d3dea-a009-dc73-a4a7-c2399dd312f9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tsprof.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tsprof
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tsprof.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 318fd86e-0aa8-a85a-99a3-8f78e9605769
---

# tsprof | Microsoft Learn

Copies the Remote Desktop Services user configuration information from one user to another. The Remote Desktop Services user configuration information appears in the Remote Desktop Services extensions to Local Users and Groups and active directory Users and computers.

Note

You can also use the [tsprof command](tsprof) to set the profile path for a user.

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
tsprof /update {/domain:<Domainname> | /local} /profile:<path> <username>
tsprof /copy {/domain:<Domainname> | /local} [/profile:<path>] <src_user> <dest_user>
tsprof /q {/domain:<Domainname> | /local} <username>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /update | Updates profile path information for `<username>` in domain `<domainname>` to `<profilepath>`. |
| /domain:`<Domainname>` | Specifies the name of the domain in which the operation is applied. |
| /local | Applies the operation only to local user accounts. |
| /profile:`<path>` | Specifies the profile path as displayed in the Remote Desktop Services extensions in Local Users and Groups and active directory Users and computers. |
| `<username>` | Specifies the name of the user for whom you want to update or query the server profile path. |
| /copy | Copies user configuration information from `<src_user>` to `<dest_user>` and updates the profile path information for `<dest_user>` to `<profilepath>`. Both `<src_user>` and `<dest_user>` must either be local or must be in domain `<domainname>`. |
| `<src_user>` | Specifies the name of the user from whom you want to copy the user configuration information. Also known as the source user. |
| `<dest_user>` | Specifies the name of the user to whom you want to copy the user configuration information. Also known as the destination user. |
| /q | Displays the current profile path of the user for whom you want to query the server profile path. |
| /? | Displays help at the command prompt. |

## Examples

To copy user configuration information from *LocalUser1* to *LocalUser2*, type:

```
tsprof /copy /local LocalUser1 LocalUser2
```

To set the Remote Desktop Services profile path for *LocalUser1* to a directory called *c:\profiles*, type:

```
tsprof /update /local /profile:c:\profiles LocalUser1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)