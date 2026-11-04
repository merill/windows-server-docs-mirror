---
layout: Conceptual
title: Monitor the existing load on the Remote Access server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/monitoring-and-accounting/monitor-the-existing-load-on-the-remote-access-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to use the monitoring dashboard to view the load statistics for the server, or you can use Performance Monitor counters to track the statistics.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 3f851265-252b-3c8f-80cf-f2393d5903ec
document_version_independent_id: a555658c-fb02-42d7-39e3-ebd4aa49991c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Monitor-the-existing-load-on-the-Remote-Access-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/monitoring-and-accounting/monitor-the-existing-load-on-the-remote-access-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Monitor-the-existing-load-on-the-Remote-Access-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: ffe759bd-e511-a61d-205f-805ef98b8495
---

# Monitor the existing load on the Remote Access server | Microsoft Learn

**Note:** Windows Server 2012 combines DirectAccess and Routing and Remote Access Service (RRAS) into a single Remote Access role.

The term **Load** refers to the statistics that relate to the number of connections on the Remote Access server. Following are the steps required to track the load on the Remote Access server.

You can use the monitoring dashboard that is available in the management console on the Remote Access server to view the load statistics for the server, or you can use Performance Monitor counters to track the statistics.

Note

You must be signed in as a member of the Domain Admins group or a member of the Administrators group on each computer to complete the tasks described in this topic. If you cannot complete a task while you are signed in with an account that is a member of the Administrators group, try performing the task while you are signed in with an account that is a member of the Domain Admins group.

#### To use the monitoring dashboard to monitor the Remote Access server load

1. In **Server Manager**, click **Tools**, and then click **Remote Access Management**.
2. Click **DASHBOARD** to navigate to **Remote Access Dashboard** in the **Remote Access Management Console**.
3. On the monitoring dashboard, notice the **Remote Client Status** tile within the **Server Status** tile. This tile lists statistics such as the total number of remote clients that are connected, the total number of DirectAccess clients that are connected, and the maximum number of users who connected in last 24 hours.
4. You can click **Refresh** under **Tasks** in the right pane to reload the health status. To change the default refresh interval, click **Configure Refresh Interval** under **Tasks**.

#### To use the Performance Monitor tool to monitor performance counters on the Remote Access server

1. Click **Start**, click **Administrative Tools**, and then double-click **Performance Monitor**.
2. Under **Performance**, click **Performance Monitor**.
3. Click the **Add** button (denoted by a green cross icon) in the **Performance Monitor** toolbar.
4. From the list of **Available Counters**, select all the counters in the **RAS** and **RAmgmtsvc** categories, and then click **Add&gt;&gt;**.
5. Again, from the list of **Available Counters**, select all the counters in the **IPsec Connections** category, and then click **Add&gt;&gt;.**
6. Click **OK** to add the selected counters in the **Performance Monitor** console for tracking.

**Performance Monitor** will now graphically show the selected server load statistics.

![Windows PowerShell](../../../media/monitor-the-existing-load-on-the-remote-access-server/powershelllogosmall.gif)***Windows PowerShell equivalent commands***

The following Windows PowerShell cmdlet or cmdlets perform the same function as the preceding procedure. Enter each cmdlet on a single line, even though they may appear word-wrapped across several lines here because of formatting constraints.

```
PS> Get-RemoteAccessConnectionStatisticsSummary
```