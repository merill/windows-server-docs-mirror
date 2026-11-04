---
layout: Conceptual
title: wdsutil approve-autoadddevices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-approve-autoadddevices
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil approve-autoadddevices command, which approves computers that are pending administrative approval.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f92af9f2-b2d8-720a-73ee-ce23eb0228af
document_version_independent_id: e20d6a65-7495-f564-a21d-a30b3118f74f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-approve-autoadddevices.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-approve-autoadddevices
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-approve-autoadddevices.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 779b0391-5b30-efb8-4199-eb235d0dbea3
---

# wdsutil approve-autoadddevices | Microsoft Learn

Approves computers that are pending administrative approval. When the Auto-add policy is enabled, administrative approval is required before unknown computers (those that are not pre-staged) can install an image. You can enable this policy using the **PXE Response** tab of the server s properties page.

## Syntax

```
wdsutil [Options] /Approve-AutoaddDevices [/Server:<Server name>] /RequestId:{<Request ID>| ALL} [/MachineName:<Device name>] [/OU:<DN of OU>] [/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>] [/BootImagepath:<Relative path>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Server:`<Servername>` | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If no server name is specified, the local server is used. |
| /RequestId:`{Request ID|ALL}` | Specifies the request ID assigned to the pending computer. Specify **ALL** to approve all pending computers. |
| /Machinename:`<Devicename>` | Specifies the name of the device to be added. You can't use this option when approving all computers. |
| [/OU:`<DN of OU>`] | The distinguished name of the organizational unit where the computer account object should be created. For example: **OU=MyOU,CN=Test, DC=Domain,DC=com**. The default location is the default computer's container. |
| [/User:`<Domain\User|User@Domain>`] | Sets permissions on the computer account object to give the specified user the necessary rights to join the computer to the domain. |
| [/JoinRights:`{JoinOnly|Full}`] | Specifies the type of rights to be assigned to the user.<br>- **JoinOnly** - Requires the administrator to reset the computer account before the user can join the computer to the domain.<br>- **Full** - Gives full access to the user, which includes the right to join the computer to the domain. |
| [/JoinDomain:`{Yes|No}`] | Specifies whether the computer should be joined to the domain as this computer account during operating system installation. The default value is **Yes**. |
| [/ReferralServer:`<Servername>`] | Specifies the name of the server to contact to download the network boot program and boot image by using Trivial File Transfer Protocol (tftp). |
| [/BootProgram:`<Relativepath>`] | Specifies the relative path from the **remoteInstall** folder to the network boot program that this computer should receive. For example: **boot\x86\pxeboot.com**. |
| [/WdsClientUnattend:`<Relativepath>`] | Specifies the relative path from the **remoteInstall** folder to the unattend file that automates the Windows Deployment Services client. |
| [/BootImagepath:`<Relativepath>`] | Specifies the relative path from the remoteInstall folder to the boot image that this computer should receive. |

## Examples

To approve the computer with a RequestId of 12, type:

```
wdsutil /Approve-AutoaddDevices /RequestId:12
```

To approve the computer with a RequestID of 20 and to deploy the image with the specified settings, type:

```
wdsutil /Approve-AutoaddDevices /RequestId:20 /MachineName:computer1 /OU:OU=Test,CN=company,DC=Domain,DC=Com /User:Domain\User1
/JoinRights:Full /ReferralServer:MyWDSServer /BootProgram:boot\x86\pxeboot.n12 /WdsClientUnattend:WDSClientUnattend\Unattend.xml /BootImagepath:boot\x86\images\boot.wim
```

To approve all pending computers, type:

```
wdsutil /verbose /Approve-AutoaddDevices /RequestId:ALL
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil delete-autoadddevices command](wdsutil-delete-autoadddevices)
- [wdsutil get-autoadddevices command](wdsutil-get-autoadddevices)
- [wdsutil reject-autoadddevices command](wdsutil-reject-autoadddevices)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)