---
layout: Conceptual
title: wdsutil add-device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-device
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil add-device command, which pre-stages a computer in Active Directory Domain Services.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 286f5e01-f577-429d-78a2-6ce88be32bcd
document_version_independent_id: d75b4ba6-5411-2365-c161-68ca6fcbc210
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-device.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: cc9711df-0a1a-60d7-9d3d-a1b4718371b7
---

# wdsutil add-device | Microsoft Learn

Pre-stages a computer in Active Directory Domain Services (AD DS). Pre-staged computers are also called *known computers*. This allows you to configure properties to control the installation for the client. For example, you can configure the network boot program and the unattend file that the client should receive, as well as the server from which the client should download the network boot program.

## Syntax

```
wdsutil /add-Device /Device:<Devicename> /ID:<UUID | MAC address> [/ReferralServer:<Servername>] [/BootProgram:<Relativepath>] [/WdsClientUnattend:<Relativepath>] [/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relativepath>] [/OU:<DN of OU>] [/Domain:<Domain>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Device:`<Devicename>` | Specifies the name of the device to be added. |
| /ID:`<UUID|MAC address>` | Specifies either the GUID/UUID or the MAC address of the computer. A GUID/UUID must be in one of two formats: Binary string (`/ID:ACEFA3E81F20694E953EB2DAA1E8B1B6`) or GUID string (`/ID:E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6`). A MAC address must be in the following format: **00B056882FDC** (no dashes) or **00-B0-56-88-2F-DC** (with dashes) |
| [/ReferralServer:`<Servername>`] | Specifies the name of the server to be contacted to download the network boot program and the boot image by using Trivial File Transfer Protocol (tftp). |
| [/BootProgram:`<Relativepath>`] | Specifies the relative path from the **remoteInstall** folder to the network boot program that this computer should receive. For example: `boot\x86\pxeboot.com` |
| [/WdsClientUnattend:`<Relativepath>`] | Specifies the relative path from the **remoteInstall** folder to the unattended installation file that automates the installation screens of the Windows Deployment Services client. |
| [/User:`<Domain\User|User@Domain>`] | Sets permissions on the computer account object to give the specified user the necessary rights to join the computer to the domain. |
| [/JoinRights:`{JoinOnly|Full}`] | Specifies the type of rights to be assigned to the user.<br>- **JoinOnly** - Requires the administrator to reset the computer account before the user can join the computer to the domain.<br>- **Full** - Gives full access to the user, which includes the right to join the computer to the domain. |
| [/JoinDomain:`{Yes|No}`] | Specifies whether the computer should be joined to the domain as this computer account during operating system installation. The default value is **Yes**. |
| [/BootImagepath:`<Relativepath>`] | Specifies the relative path from the **remoteInstall** folder to the boot image that this computer should use. |
| [/OU:`<DN of OU>`] | The distinguished name of the organizational unit where the computer account object should be created. For example: **OU=MyOU,CN=Test, DC=Domain,DC=com**. The default location is the default computer's container. |
| [/Domain:`<Domain>`] | The domain where the computer account object should be created. The default location is the local domain. |

## Examples

To add a computer by using a MAC address, type:

```
wdsutil /add-Device /Device:computer1 /ID:00-B0-56-88-2F-DC
```

To add a computer by using a GUID string, type:

```
wdsutil /add-Device /Device:computer1 /ID:{E8A3EFAC-201F-4E69-953F-B2DAA1E8B1B6} /ReferralServer:WDSServer1 /BootProgram:boot\x86\pxeboot.com/WDSClientUnattend:WDSClientUnattend\unattend.xml /User:Domain\MyUser/JoinRights:Full /BootImagepath:boot\x86\images\boot.wim /OU:OU=MyOU,CN=Test,DC=Domain,DC=com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-alldevices command](wdsutil-get-alldevices)
- [wdsutil get-device command](wdsutil-get-device)
- [wdsutil set-device command](wdsutil-set-device)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)
- [New-WdsClient](/en-us/powershell/module/wds/New-WdsClient)