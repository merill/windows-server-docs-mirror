---
layout: Conceptual
title: Manage DirectAccess Clients Remotely | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/manage-remote-clients/manage-directaccess-clients-remotely
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to leverage the monitoring capabilities of Remote Access by using the DirectAccess management console and the corresponding Windows PowerShell cmdlets, which are provided as part of the Remote Access server role.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 30624741-f132-3ca1-a1e3-004444d6836b
document_version_independent_id: 4b13acb8-ad4b-7d20-0e70-2a574ca217e2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/manage-remote-clients/Manage-DirectAccess-Clients-Remotely.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/manage-remote-clients/manage-directaccess-clients-remotely
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/manage-remote-clients/Manage-DirectAccess-Clients-Remotely.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 68e0dc0c-de45-1b24-c7c1-a7c03be1698b
---

# Manage DirectAccess Clients Remotely | Microsoft Learn

Remote Access monitoring reports remote user activity and status for DirectAccess and VPN connections. It tracks the number and duration of client connections (among other statistics), and monitors the operations status of the server. An easy-to-use monitoring console provides a view of your entire Remote Access infrastructure. Monitoring views are available for single server, cluster, and multisite configurations.

**Note:** Windows Server 2016 combines DirectAccess and Remote Access Service (RAS) into a single Remote Access role.

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