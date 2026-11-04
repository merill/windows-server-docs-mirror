---
layout: Conceptual
title: Disable NAS Notification Forwarding in NPS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-disable-nas-notifications
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to disable the forwarding of start and stop messages from network access servers to members of a remote RADIUS server group configured in NPS.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 26a80a6b-68f4-6e13-bbc3-5d635e127ab3
document_version_independent_id: b0ab2f01-261f-436a-1152-707227a551f9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-disable-nas-notifications.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-disable-nas-notifications
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-disable-nas-notifications.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c9a9de8a-2f05-1d96-b044-e5ffe93a830f
---

# Disable NAS Notification Forwarding in NPS | Microsoft Learn

You can use this procedure to disable the forwarding of start and stop messages from network access servers (NASs) to members of a remote RADIUS server group configured in NPS.

When you have remote RADIUS server groups configured and, in NPS **Connection Request Policies**, you clear the **Forward accounting requests to this remote RADIUS server group** check box, these groups are still sent NAS start and stop notification messages.

This creates unnecessary network traffic. To eliminate this traffic, disable NAS notification forwarding for individual servers in each remote RADIUS server group.

To complete this procedure, you must be a member of the **Administrators** group.

### To disable NAS notification forwarding

1. In Server Manager, click **Tools**, and then click **Network Policy Server**. The NPS console opens.
2. In the NPS console, double-click **RADIUS Clients and Servers**, click **Remote RADIUS Server Groups**, and then double-click the remote RADIUS server group that you want to configure. The remote RADIUS server group **Properties** dialog box opens.
3. Double-click the group member that you want to configure, and then click the **Authentication/Accounting** tab.
4. In **Accounting**, clear the **Forward network access server start and stop notifications to this server** check box, and then click **OK**.
5. Repeat steps 3 and 4 for all group members that you want to configure.

For more information about managing NPS, see [Manage Network Policy Server](nps-manage-top).

For more information about NPS, see [Network Policy Server (NPS)](nps-top).