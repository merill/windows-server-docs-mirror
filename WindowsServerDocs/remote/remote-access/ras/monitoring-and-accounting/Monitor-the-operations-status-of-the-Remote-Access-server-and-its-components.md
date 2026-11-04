---
layout: Conceptual
title: Monitor the operations status of the Remote Access server and its components | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/monitoring-and-accounting/monitor-the-operations-status-of-the-remote-access-server-and-its-components
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to use the management console in the Remote Access server to monitor its operations status.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: c2fde51c-6ab9-6369-c69b-9d5298973146
document_version_independent_id: 3290236e-13c8-ac56-9fa6-6f551d887341
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Monitor-the-operations-status-of-the-Remote-Access-server-and-its-components.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/monitoring-and-accounting/monitor-the-operations-status-of-the-remote-access-server-and-its-components
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Monitor-the-operations-status-of-the-Remote-Access-server-and-its-components.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: df222d8e-6294-6234-01ae-9bc7dbbc6417
---

# Monitor the operations status of the Remote Access server and its components | Microsoft Learn

**Note:** Windows Server 2012 combines DirectAccess and Routing and Remote Access Service (RRAS) into a single Remote Access role.

The management console in the Remote Access server can be used to monitor its operations status.

Note

You must be signed in as a member of the Domain Admins group or a member of the Administrators group on each computer to complete the task described in this topic. If you cannot complete a task while you are signed in with an account that is a member of the Administrators group, try performing the task while you are signed in with an account that is a member of the Domain Admins group.

#### To monitor the Remote Access server operations status

1. In **Server Manager**, click **Tools**, and then click **Remote Access Management**.
2. Click **DASHBOARD** to navigate to **Remote Access Reporting** in the **Remote Access Management Console**.
3. On the monitoring dashboard, notice the **Operations Status** tile within the **Server Status** tile. This tile lists the server operations status and the status of all the server's components.
4. Click **Refresh** under **Tasks** in the right pane to reload the operations status. The operations status is automatically refreshed every five minutes, which is the default refresh interval. To change the default refresh interval, click **Configure Refresh Interval**.

![Windows PowerShell](../../../media/monitor-the-operations-status-of-the-remote-access-server-and-its-components/powershelllogosmall.gif)***Windows PowerShell equivalent commands***

The following Windows PowerShell cmdlet or cmdlets perform the same function as the preceding procedure. Enter each cmdlet on a single line, even though they may appear word-wrapped across several lines here because of formatting constraints.

Note

The command for operations status of a cluster is included for reference.

```
PS> Get-RemoteAccessHealth
PS> Get-RemoteAccessHealth -Cluster
```