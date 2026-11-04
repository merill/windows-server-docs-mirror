---
layout: Conceptual
title: wdsutil set-device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-set-device
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil set-device, which changes the attributes of a prestaged computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 60aa4404-d166-7325-7c38-7808e22d5267
document_version_independent_id: 2983f3a0-2cb4-69ee-0c72-b4509391c031
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-set-device.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-set-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-set-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2b978f4b-6b65-55fc-3c3b-cd0fb09eeb5f
---

# wdsutil set-device | Microsoft Learn

Changes the attributes of a prestaged computer. A prestaged computer is a computer that has been linked to a computer account object in active directory Domain Servers (AD DS). Prestaged clients are also called known computers. You can configure properties on the computer account to control the installation for the client. For example, you can configure the network boot program and the unattend file that the client should receive, as well as the server from which the client should download the network boot program.

## Syntax

```
wdsutil [Options] /Set-Device /Device:<Device name> [/ID:<UUID | MAC address>] [/ReferralServer:<Server name>] [/BootProgram:<Relative path>]
[/WdsClientUnattend:<Relative path>] [/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relative path>] [/Domain:<Domain>] [/resetAccount]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Device:&lt;computer name&gt; | Specifies the name of the computer (SAM-Account-Name). |
| [/ID:&lt;UUID | MAC address&gt;] | Specifies either the GUID/UUID or the MAC address of the computer. This value must be in one of the following three formats:<br>- Binary string: **/ID:ACEFA3E81F20694E953EB2DAA1E8B1B6**- GUID/UUID string: /ID:**E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6**- MAC address: **00B056882FDC** (no dashes) or **00-B0-56-88-2F-DC** (with dashes) |
| [/ReferralServer:&lt;Server name&gt;] | Specifies the name of the server to be contacted to download the network boot program and boot image using Trivial File Transfer Protocol (tftp). |
| [/BootProgram:&lt;Relative path&gt;] | Specifies the relative path from the remoteInstall folder to the network boot program that the specified computer will receive. For example: **boot\x86\pxeboot.com** |
| [/WdsClientUnattend:&lt;Relative path&gt;] | Specifies the relative path from the remoteInstall folder to the unattend file that automates the installation screens for the Windows Deployment Services client. |
| [/User:&lt;Domain\User | User@Domain&gt;] | Sets permissions on the computer account object to give the specified user the necessary rights to join the computer to the domain. |
| [/JoinRights:{JoinOnly | Full}] | Specifies the type of rights to be assigned to the user.<br>- **JoinOnly** requires the administrator to reset the computer account before the user can join the computer to the domain.- **Full** gives full access to the user, including the right to join the computer to the domain. |
| [/JoinDomain:{Yes | No}] | Specifies whether or not the computer should be joined to the domain as this computer account during a Windows Deployment Services installation. The default setting is **Yes**. |
| [/BootImagepath:&lt;Relative path&gt;] | Specifies the relative path from the remoteInstall folder to the boot image that the computer will use. |
| [/Domain:&lt;Domain&gt;] | Specifies the domain to be searched for the prestaged computer. The default value is the local domain. |
| [/resetAccount] | resets the permissions on the specified computer so that anyone with the appropriate permissions can join the domain by using this account. |

## Examples

To set the network boot program and referral server for a computer, type:

```
wdsutil /Set-Device /Device:computer1 /ReferralServer:MyWDSServer
/BootProgram:boot\x86\pxeboot.n12
```

To set various settings for a computer, type:

```
wdsutil /verbose /Set-Device /Device:computer2 /ID:00-B0-56-88-2F-DC /WdsClientUnattend:WDSClientUnattend\unattend.xml
/User:Domain\user /JoinRights:JoinOnly /JoinDomain:No /BootImagepath:boot\x86\images\boot.wim /Domain:NorthAmerica /resetAccount
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-device command](wdsutil-add-device)
- [wdsutil get-alldevices command](wdsutil-get-alldevices)
- [wdsutil get-device command](wdsutil-get-device)