---
layout: Conceptual
title: Monitor connected remote clients for activity and status | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/monitoring-and-accounting/monitor-connected-remote-clients-for-activity-and-status
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to use the management console on the Remote Access server to monitor remote client activity and status.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 15e074d0-9a82-8119-7c04-941d52a0c060
document_version_independent_id: d838f0f6-ce4b-e0b9-c541-9a65dd5877c1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Monitor-connected-remote-clients-for-activity-and-status.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/monitoring-and-accounting/monitor-connected-remote-clients-for-activity-and-status
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Monitor-connected-remote-clients-for-activity-and-status.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c3b43c13-0029-5137-36f2-dc5efd9e4a44
---

# Monitor connected remote clients for activity and status | Microsoft Learn

**Note:** Windows Server 2012 combines DirectAccess and Remote Access Service (RAS) into a single Remote Access role.

You can use the management console on the Remote Access server to monitor remote client activity and status.

Note

You must be signed in as a member of the Domain Admins group or a member of the Administrators group on each computer to complete the tasks described in this topic. If you cannot complete a task while you are signed in with an account that is a member of the Administrators group, try performing the task while you are signed in with an account that is a member of the Domain Admins group.

#### To monitor remote client activity and status

1. In **Server Manager**, click **Tools**, and then click **Remote Access Management**.
2. Click **REPORTING** to navigate to **Remote Access Reporting** in the **Remote Access Management Console**.
3. Click **Remote Client Status** to navigate to the remote client activity and status user interface in the **Remote Access Management Console**.
4. You will see the list of users who are connected to the Remote Access server and detailed statistics about them. Click the first row in the list that corresponds to a client. When you select a row, the remote user activity is shown in the preview pane.

![Windows PowerShell](../../../media/monitor-connected-remote-clients-for-activity-and-status/powershelllogosmall.gif)***Windows PowerShell equivalent commands***

The following Windows PowerShell cmdlet or cmdlets perform the same function as the preceding procedure. Enter each cmdlet on a single line, even though they may appear word-wrapped across several lines here because of formatting constraints.

```
PS> Get-RemoteAccessConnectionStatistics
```

The user statistics can be filtered, based on criteria selections, by using the fields in the following table.

| Field Name | Value |
| --- | --- |
| Username | The user name or alias of the remote user. Wildcard characters can be used to select a group of users, such as contoso\\* or \*\administrator. |
| Hostname | The computer account name of the remote user. An IPv4 or IPv6 address also can be specified. |
| Type | DirectAccess or VPN. If DirectAccess is selected, all remote users who are connected by using DirectAccess are listed. If VPN is selected, all remote users who are connected by using VPN are listed. |
| ISP address | The IPv4 or IPv6 address of the remote user. |
| IPv4 address | The inner IPv4 address of the tunnel that connect the remote user to the corporate network. |
| IPv6 address | The inner IPv6 address of the tunnel that connects the remote user to the corporate network. |
| Protocol/Tunnel | The transitioning technology that is used by the remote client. This is Teredo, 6to4, or IP-HTTPS for DirectAccess users, and it is PPTP, L2TP, SSTP, or IKEv2 for VPN users. |
| Resource Accessed | All users who are accessing a particular corporate resource or an endpoint. The value that corresponds to this field is the hostname/IP address of the server. |
| Server | The Remote Access server to which clients are connected. This is relevant only for cluster and multisite deployments. |