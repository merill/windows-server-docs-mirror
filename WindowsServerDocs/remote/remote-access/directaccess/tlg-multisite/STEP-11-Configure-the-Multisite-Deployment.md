---
layout: Conceptual
title: STEP 11 Configure the Multisite Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-multisite/step-11-configure-the-multisite-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to make changes to the current Remote Access configuration wizard on EDGE1, enable the multisite feature, and then add 2-EDGE1 as a second entry point.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 39fd6945-86a0-2c3a-c412-74337cdb62c5
document_version_independent_id: 8eddd80c-6192-17ee-bfa6-eb08657cc581
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-11-Configure-the-Multisite-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-multisite/step-11-configure-the-multisite-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-11-Configure-the-Multisite-Deployment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 03bc8ec6-3ff0-d3cb-4fbc-f760c77f07e8
---

# STEP 11 Configure the Multisite Deployment | Microsoft Learn

To configure a multisite deployment, make changes to the current Remote Access configuration wizard on EDGE1, enable the multisite feature, and then add 2-EDGE1 as a second entry point.

- Configure Remote Access on EDGE1
- Enable multisite configuration on EDGE1
- Add 2-EDGE1 as a second entry-point

## Configure Remote Access on EDGE1

1. On the **Start** screen, type**RAMgmtUI.exe**, and then press ENTER. If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Yes**.
2. In the Remote Access Management Console, click **Configuration**.
3. In the middle pane of the console, in the **Step 2 Remote Access Server** area, click **Edit**.
4. Click **Prefix Configuration**. On the **Prefix Configuration** page, in **Internal network IPv6 prefixes**, enter **2001:db8:1::/64; 2001:db8:2::/64**. In **IPv6 prefix assigned to DirectAccess client computers**, enter **2001:db8:1:1000::/64**, click **Next**, and then click **Finish**.
5. In the middle pane of the console, in the **Step 3 Infrastructure Servers** area, click **Edit**.
6. Click **DNS Suffix Search List**. On the **DNS Suffix Search List** page, make sure that the **Configure DirectAccess clients with DNS client suffix search list** check box is selected and that the **corp.contoso.com** and **corp2.corp.contoso.com** domain suffixes appear in the **Domain suffixes to use** list, click **Next**, and then click Finish.
7. In the middle pane of the console, click **Finish**.
8. On the **Remote Access Review** dialog box, review the configuration settings, and then click **Apply**. On the **Applying Remote Access Setup Wizard Settings** dialog box, click **Close**.
9. In the **Tasks** pane, click **Refresh Management Servers**, and click **Close** when finished.

## Enable multisite configuration on EDGE1

1. In the Remote Access Management Console, in the **Tasks** pane, click **Enable Multisite**.
2. In the Enable Multisite Deployment wizard, on the **Before You Begin** page, click **Next**.
3. On the **Deployment Name** page, in **Multisite deployment name**, type **Contoso**, in **First entry point name**, type **Edge1-Site**, and then click **Next**.
4. On the **Entry Point Selection** page, click **Assign entry points automatically, and allow clients to select manually**, and then click **Next**.
5. On the **Global Load Balancing** page, click **No, do not use global load balancing**, and then click **Next**.
6. On the **Client Support** page, click **Allow client computers running Windows 7 to access this entry point**, and click **Add**.
7. On the **Select Groups** dialog box, in **Enter the object names to select**, type **Win7\_Clients\_Site1**, click **OK**, and then click **Next**.
8. On the **Client GPO Settings** page, click **Next**.
9. On the **Summary** page, click **Commit**.
10. On the **Enabling Multisite Deployment** dialog box, click **Close** and then on the Enable Multisite Deployment wizard, click **Close**.

## Add 2-EDGE1 as a second entry-point

1. In the Remote Access Management Console, in the **Tasks** pane, click **Add an Entry Point**.
2. In the Add an Entry Point Wizard, on the **Entry Point Details** page, in **Remote Access server**, type **2-edge1.corp2.corp.contoso.com**, in **Entry point name**, type **2-Edge1-Site**, and then click **Next**.
3. On the **Network Topology** page, click **Edge**, and then click **Next**.
4. On the **Network Name or IP Address** page, in **Type in the public name or IP address used by clients to connect to the Remote Access server**, type **2-edge1.contoso.com**, and then click **Next**.
5. On the **Network Adapters** page, make sure that the **External adapter** is **Internet**, the **Internal adapter** is **2-Corpnet**, the certificate is **CN=2-edge1.contoso.com**, and then click **Next**.
6. On the **Prefix Configuration** page, in **IPv6 prefix assigned to DirectAccess client computers**, type **2001:db8:2:2000::/64**, and then click **Next**.
7. On the **Client Support** page, click **Allow client computers running Windows 7 to access this entry point**, and click **Add**.
8. On the **Select Groups** dialog box, in **Enter the object names to select**, type **Win7\_Clients\_Site2**, click **OK**, and then click **Next**.
9. On the **Client GPO Settings** page, click **Next**.
10. On the **Server GPO Settings** page, click **Next**.
11. On the **Summary** page click **Commit**.
12. On the **Adding Entry Point** dialog box, click **Close** and then on the Add an Entry Point wizard, click **Close**.