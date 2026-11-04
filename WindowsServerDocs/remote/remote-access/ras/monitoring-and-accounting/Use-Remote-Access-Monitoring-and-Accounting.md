---
layout: Conceptual
title: Use Remote Access Monitoring and Accounting | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/monitoring-and-accounting/use-remote-access-monitoring-and-accounting
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to leverage the monitoring capabilities of Remote Access by using the DirectAccess management console and the corresponding Windows PowerShell cmdlets.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: b620a74a-d5c5-87fb-e69e-fe7ba475275e
document_version_independent_id: 8048eea9-c155-ce64-8eee-6a371cb0582d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Use-Remote-Access-Monitoring-and-Accounting.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/monitoring-and-accounting/use-remote-access-monitoring-and-accounting
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/monitoring-and-accounting/Use-Remote-Access-Monitoring-and-Accounting.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 46884a54-57d4-a3c7-a599-30a4cc16e0f6
---

# Use Remote Access Monitoring and Accounting | Microsoft Learn

Remote Access monitoring reports remote user activity and status for DirectAccess and VPN connections. It tracks the number and duration of client connections (among other statistics), and monitors the operations status of the server. An easy-to-use monitoring console provides a view of your entire Remote Access infrastructure. Monitoring views are available for single server, cluster, and multisite configurations.

**Note:** Windows Server 2012 combines DirectAccess and Routing and Remote Access Service (RRAS) into a single Remote Access role.

Note

In addition to this topic, the following topics on monitoring Remote Access are available.

- [Monitor the existing load on the Remote Access server](monitor-the-existing-load-on-the-remote-access-server)
- [Monitor the configuration distribution status of the Remote Access server](monitor-the-configuration-distribution-status-of-the-remote-access-server)
- [Monitor the Operations Status of the Remote Access server and its components](monitor-the-operations-status-of-the-remote-access-server-and-its-components)
- [Identify and resolve Remote Access server operations problems](identify-and-resolve-remote-access-server-operations-problems)
- [Monitor connected remote clients for activity and status](monitor-connected-remote-clients-for-activity-and-status)
- [Generate a usage report for remote clients using historical data](generate-a-usage-report-for-remote-clients-using-historical-data)

## In this guide

This document contains instructions for leveraging the monitoring capabilities of Remote Access by using the DirectAccess management console and the corresponding Windows PowerShell cmdlets, which are provided as part of the Remote Access server role.

The following monitoring and accounting scenarios are explained:

1. Monitor the existing load on the Remote Access server
2. Monitor the configuration distribution status of the Remote Access server
3. Monitor the operations status of the Remote Access server and its components
4. Identify and resolve Remote Access server operations issues
5. Monitor connected remote clients for activity and status
6. Generate a usage report for remote clients by using historical data

### Understand monitoring and accounting

Before you begin monitoring and accounting tasks for remote clients, you need to understand the difference between the two.

- **Monitoring** shows actively connected users at a given point in time.
- **Accounting** keeps a history of users who have connected to the corporate network, and their usage details (for compliance and auditing purposes).

Remote client monitoring is based on connections. There are two types of tunnel connections that are established by DirectAccess clients:

- **Machine tunnel traffic connections**: This tunnel is established by the computer, in system context, to access servers that are required for name resolution, authentication, remediation updating, and so on.
- **User tunnel traffic connections**: This tunnel is established by the user account on the computer, in a user context, when the user tries to access a resource on the corporate network. Depending on the deployment requirements, a user might have to provide strong credentials (for example, by using a smart card or providing a one-time password) to access the corporate network resources.

For DirectAccess, a connection is uniquely identified by the IP address of the remote client. For example, if a machine tunnel is open for a client computer, and a user is connected from that computer, these would be using the same connection. In a situation where the user disconnects and connects again while the machine tunnel is still active, it is a single connection.