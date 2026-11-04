---
layout: Conceptual
title: Configure Client Automatic Hosted Cache Discovery by Service Connection Point | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/bc-hcm/10-bc-client-by-scp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to use Group Policy to enable and configure BranchCache hosted cache mode on domain-joined computers that are running the following BranchCache-capable Windows operating systems.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: d2b24e3c-8db5-f124-7775-da23131d13c1
document_version_independent_id: c8153f39-43fd-bc3a-bec7-2bad83433bbb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/10-Bc-Client-By-Scp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/bc-hcm/10-bc-client-by-scp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/10-Bc-Client-By-Scp.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a75666cf-9ce7-724d-3327-01247f833464
---

# Configure Client Automatic Hosted Cache Discovery by Service Connection Point | Microsoft Learn

With this procedure you can use Group Policy to enable and configure BranchCache hosted cache mode on domain-joined computers that are running the following BranchCache-capable Windows operating systems.

- Windows 10 Enterprise
- Windows 10 Education
- Windows 8.1 Enterprise
- Windows 8 Enterprise

Note

To configure domain-joined computers that are running Windows Server 2008 R2 or Windows 7, see the Windows Server 2008 R2 [BranchCache Deployment Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649232%28v=ws.10%29).

Membership in **Domain Admins**, or equivalent is the minimum required to perform this procedure.

### To use Group Policy to configure clients for hosted cache mode

1. On a computer upon which the Active Directory Domain Services server role is installed, open Server Manager, select the Local Server, click **Tools**, and then click **Group Policy Management**. The Group Policy Management console opens.
2. In the Group Policy Management console, expand the following path: **Forest:***corp.contoso.com*, **Domains**, *corp.contoso.com*, **Group Policy Objects**, where *corp.contoso.com* is the name of the domain where the BranchCache client computer accounts that you want to configure are located.
3. Right-click **Group Policy Objects**, and then click **New**. The **New GPO** dialog box opens. In **Name**, type a name for the new Group Policy object (GPO). For example, if you want to name the object BranchCache Client Computers, type **BranchCache Client Computers**. Click **OK**.
4. In the Group Policy Management console, ensure that **Group Policy Objects** is selected, and in the details pane right-click the GPO that you just created. For example, if you named your GPO BranchCache Client Computers, right-click **BranchCache Client Computers**. Click **Edit**. The Group Policy Management Editor console opens.
5. In the Group Policy Management Editor console, expand the following path: **Computer Configuration**, **Policies**, **Administrative Templates: Policy definitions (ADMX files) retrieved from the local computer**, **Network**, **BranchCache**.
6. Click **BranchCache**, and then in the details pane, double-click **Turn on BranchCache**. The **Turn on BranchCache** dialog box opens.
7. In the **Turn on BranchCache** dialog box, click **Enabled**, and then click **OK**.
8. In the Group Policy Management Editor console, ensure that **BranchCache** is still selected, and then in the details pane double-click **Enable Automatic Hosted Cache Discovery by Service Connection Point**. The policy setting dialog box opens.
9. In the **Enable Automatic Hosted Cache Discovery by Service Connection Point** dialog box, click **Enabled**, and then click **OK**.
10. To enable client computers to download and cache content from BranchCache file server-based content servers: In the Group Policy Management Editor console, ensure that **BranchCache** is still selected, and then in the details pane double-click **BranchCache for network files**. The **Configure BranchCache for network files** dialog box opens.
11. In the **Configure BranchCache for network files** dialog box, click **Enabled**. In **Options**, type a numeric value, in milliseconds, for the maximum round trip network latency time, and then click **OK**.

    Note

    By default, client computers cache content from file servers if the round trip network latency is longer than 80 milliseconds.
12. To configure the amount of hard disk space allocated on each client computer for the BranchCache cache: In the Group Policy Management Editor console, ensure that **BranchCache** is still selected, and then in the details pane double-click **Set percentage of disk space used for client computer cache**. The **Set percentage of disk space used for client computer cache** dialog box opens. Click **Enabled**, and then in **Options** type a numeric value that represents the percentage of hard disk space used on each client computer for the BranchCache cache. Click **OK**.
13. To specify the default age, in days, for which segments are valid in the BranchCache data cache on client computers: In the Group Policy Management Editor console, ensure that **BranchCache** is still selected, and then in the details pane double-click **Set age for segments in the data cache**. The **Set age for segments in the data cache** dialog box opens. Click **Enabled**, and then in the details pane type the number of days that you prefer. Click **OK**.
14. Configure additional BranchCache policy settings for client computers as appropriate for your deployment.
15. Refresh Group Policy on branch office client computers by running the command **gpupdate /force**, or by rebooting the client computers.

Your BranchCache Hosted Cache mode deployment is now complete.

For additional information on the technologies in this guide, see [Additional Resources](11-bc-hcm-additional-resources).