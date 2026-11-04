---
layout: Conceptual
title: Identify and resolve Remote Access server operations problems | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/monitoring-and-accounting/identify-and-resolve-remote-access-server-operations-problems
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to identify Remote Access server operations issues, their root causes, and the resolution required to fix the issues.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 4aef8c47-9a4e-44f5-a0d5-4c84f9047d03
document_version_independent_id: 38d52ebd-df58-7d7d-f2c5-aea9bf75c6bb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Identify-and-resolve-Remote-Access-server-operations-problems.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/monitoring-and-accounting/identify-and-resolve-remote-access-server-operations-problems
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Identify-and-resolve-Remote-Access-server-operations-problems.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 832c8942-64be-d2c4-a58b-501a5be7953f
---

# Identify and resolve Remote Access server operations problems | Microsoft Learn

**Note:** Windows Server 2012 combines DirectAccess and Routing and Remote Access Service (RRAS) into a single Remote Access role.

You can using the following procedures to identify Remote Access server operations issues, their root causes, and the resolution required to fix the issues.

Note

You must be signed in as a member of the Domain Admins group or a member of the Administrators group on each computer to complete the tasks described in this topic. If you cannot complete a task while you are signed in with an account that is a member of the Administrators group, try performing the task while you are signed in with an account that is a member of the Domain Admins group.

This topic includes information about performing the following tasks:

- Simulate an operations issue
- Identify the operations issue and take corrective action
- Restore the IP Helper service

### Simulate an operations issue

Caution

Because your Remote Access server is probably configured properly and not experiencing any issues, you can use the following procedure to simulate an operations issue. If your server is currently servicing clients in a production environment, you may not want to take these actions at this time. Rather, you can read through the steps to understand how to address issues that might arise on your Remote Access server in the future.

The IP Helper service (IPHlpSvc) hosts IPv6 transitioning technologies (such as IP-HTTPS, 6to4, or Teredo), and it is required for the DirectAccess server to function properly. To demonstrate a simulated operations issue on the Remote Access server, you must stop the (IPHlpSvc) network service.

##### To stop the IP Helper service

1. On the **Start** screen of the Remote Access server, click **Administrative Tools**, and then double-click **Services**.
2. In the list of **Services**, scroll down and right-click **IP Helper**, and then click **Stop**.

### Identify the operations issue and take corrective action

Turning off the IP Helper service will cause a serious error on the Remote Access server. The monitoring dashboard will show the operations status of the server and the details of the issue.

##### To identify the details and take corrective action

1. In **Server Manager**, click **Tools**, and then click **Remote Access Management**.
2. Click **DASHBOARD** to navigate to **Remote Access Dashboard** in the **Remote Access Management Console**.
3. Make sure your Remote Access server is selected in the left pane, and then in the middle pane, click **Operations Status**.
4. You will see the list of components with green or red icons, which indicate their operational status. Click the **IP-HTTPS** row in the list. When you selected a row, the details for the operation are shown in the **Details** pane as follows:

    **Error**

    The IP Helper service (IPHlpSvc) has stopped. DirectAccess might not function as expected. The IP Helper service provides tunnel connectivity by using the connectivity platform, IPv6 transition technologies, and IP-HTTPS.

    **Causes**

    1. The IP Helper service has stopped.
    2. The IP Helper service is not responding.

    **Resolution**

    1. To ensure that the service is running, type **Get-Service iphlpsvc** at a Windows PowerShell prompt.
    2. To enable the service, type **Start-Service iphlpsvc** from an elevated Windows PowerShell prompt.
    3. To restart the service, type **Restart-Service iphlpsvc** from an elevated Windows PowerShell prompt.

### Restore the IP Helper service

To restore the IP Helper service on your Remote Access server, you can follow the Resolution steps above to start or restart the service, or you can use the following procedure to reverse the procedure that you used to simulate the IP Helper service failure.

##### To restart the IP Helper service on the Remote Access server

1. On the **Start** screen, click **Administrative Tools**, and then double-click **Services**.
2. In the list of **Services**, scroll down and right-click **IP Helper**, and then click **Start**.

![Windows PowerShell](../../../media/identify-and-resolve-remote-access-server-operations-problems/powershelllogosmall.gif)***Windows PowerShell equivalent commands***

The following Windows PowerShell cmdlet or cmdlets perform the same function as the preceding procedure. Enter each cmdlet on a single line, even though they may appear word-wrapped across several lines here because of formatting constraints.

```PowerShell
PS> Get-RemoteAccessHealth | Where-Object {$_.Component -eq "IP-HTTPS"} | Format-List -Property *
```