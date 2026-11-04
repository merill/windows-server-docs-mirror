---
layout: Conceptual
title: Generate a usage report for remote clients using historical data | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/monitoring-and-accounting/generate-a-usage-report-for-remote-clients-using-historical-data
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to enable accounting on the Remote Access server so you can generate a usage report for the remote clients that are accessing the server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 009645bd-210f-f81e-42e7-e858e9cdd035
document_version_independent_id: ff0b7b0a-e402-40f3-631e-b6c5cc169dbc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Generate-a-usage-report-for-remote-clients-using-historical-data.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/monitoring-and-accounting/generate-a-usage-report-for-remote-clients-using-historical-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Generate-a-usage-report-for-remote-clients-using-historical-data.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: ad3109f8-0512-f343-a62e-cf9b0e91769d
---

# Generate a usage report for remote clients using historical data | Microsoft Learn

**Note:** Windows Server 2012 combines DirectAccess and Routing and Remote Access Service (RRAS) into a single Remote Access role.

The management console on the Remote Access server can be used to generate a usage report for the remote clients that are accessing the server. To generate a usage report for remote clients, you first enable accounting on the Remote Access server. After you generate the report, you can use the monitoring dashboard that is available in the management console on the Remote Access server to view the load statistics on the server.

Note

You must be signed in as a member of the Domain Admins group or a member of the Administrators group on each computer to complete the tasks described in this topic. If you cannot complete a task while you are signed in with an account that is a member of the Administrators group, try performing the task while you are signed in with an account that is a member of the Domain Admins group.

#### To enable accounting on the Remote Access Server

1. In **Server Manager**, click **Tools**, and then click **Remote Access Management**.
2. Click **REPORTING** to navigate to **Remote Access Reporting** in the **Remote Access Management Console**.
3. Click **Configure Accounting** in the **Remote Access Reporting** task pane.
4. Select the **Use inbox accounting** check box to enable accounting on the Remote Access server.
5. Click **Apply** to enable the accounting configuration on the server, and then click **Close** after the server has applied the configuration successfully.

#### To generate the usage report

1. In **Server Manager**, click **Tools**, and then click **Remote Access Management**.
2. Click **REPORTING** to navigate to **Remote Access Reporting** in the **Remote Access Management Console**.
3. In the middle pane, click dates in the calendar to select the report duration **Start date:** and **End date:**, and then click **Generate Report**.
4. You will see the list of users that have connected to the Remote Access server within the selected time and detailed statistics about them. Click the first row in the list. When you select a row, the remote user activity is shown in the preview pane. Now select the **Server Load Statistics** tab in the preview pane to see the historical load on the server.

    Click the **Server Load Statistics** tab in the preview pane to see the historical load on the server.

Note

**Understanding sessions**

Remote Access accounting is based on the concept of **sessions**. In contrast to a **connection**, a **session** is uniquely identified by a combination of remote client IP address and user name. For example, if a machine tunnel is formed from the remote client, named Client1, a session will be created and stored in the accounting database. When a user named User1 connects from that client after some time passes (but the machine tunnel is still active), the session is recorded as a separate session. The distinction of sessions is to retain the distinction between machine tunnel and user tunnel.

![Windows PowerShell](../../../media/generate-a-usage-report-for-remote-clients-using-historical-data/powershelllogosmall.gif)***Windows PowerShell equivalent commands***

The following Windows PowerShell cmdlet or cmdlets perform the same function as the preceding procedure. Enter each cmdlet on a single line, even though they may appear word-wrapped across several lines here because of formatting constraints.

In the following script, change the date range for which you want a report in the **-StartDateTime** and **-EndDateTime** parameters.

```
PS> Get-RemoteAccessConnectionStatisticsSummary -StartDateTime "1 October 2010 00:00:00" -EndDateTime "14 October 2010 00:00:00"
Shows server load statistics.
PS> Get-RemoteAccessUserActivity -HostIPAddress 10.0.0.1 -StartDateTime "1 October 2010 00:00:00" -EndDateTime "14 October 2010 00:00:00"
```