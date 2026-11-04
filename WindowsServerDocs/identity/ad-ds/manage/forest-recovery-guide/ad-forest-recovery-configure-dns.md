---
layout: Conceptual
title: AD Forest Recovery - Configure DNS Server service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-configure-dns
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Configuring the DNS Server service'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 459d0f3e-d20e-4905-beb3-8e84c59b9e4d
document_version_independent_id: 459d0f3e-d20e-4905-beb3-8e84c59b9e4d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-configure-dns.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-configure-dns
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-configure-dns.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 14c3bde3-65eb-a23c-a727-5cb325e1dc8c
---

# AD Forest Recovery - Configure DNS Server service | Microsoft Learn

If the DNS server role isn't installed on the DC that you restore from backup, you must install and configure the DNS server.

## Install and configure the DNS Server service

Complete this step for each restored DC that isn't running as a DNS server after the restore is complete.

Note

If the DC that you restored from backup is running Windows Server 2008 R2, you must connect the DC to an isolated network in order to install DNS server. Then connect each of the restored DNS servers to a mutually shared, isolated network. Run repadmin /replsum to verify that replication is functioning between the restored DNS servers. After you verify replication, you can connect the restored DCs to the production network If the DNS server role is already installed, you can apply a hotfix that makes it possible for a DNS server to start while the server is not connected to any network. You should slipstream the hotfix into the operating system installation image during your automated build processes. For more information about the hotfix, see [Article 975654](https://go.microsoft.com/fwlink/?LinkId=184691) in the Microsoft Knowledge Base (https://go.microsoft.com/fwlink/?LinkId=184691).

Complete the installation and configuration steps below.

### Install and the DNS Server service using Server Manager

1. Open Server Manager and select **Add roles and features**.
2. In the Add Roles Wizard, if the **Before You Begin** page appears, select **Next**.
3. On the **Installation type** screen select **Role-based or feature based installation** and select **Next**.
4. On the **Server Selection** screen select the server and select **Next**.
5. On the **Server Roles** screen select **DNS Server**, if prompted select **Add Features** and select **Next**.
6. On the **Features** screen select **Next**.
7. Read the information on the **DNS Server** page, and then select **Next**. ![Screenshot that shows the DNS Server page.](media/dns1.png)
8. On the **Confirmation** page, verify that the DNS Server role will be installed, and then select **Install**.

### Configure the DNS Server service

1. Open Server Manager, select **Tools** and select **DNS**. ![Screenshot that shows the DNS object.](media/dns2.png)
2. Create DNS zones for the same DNS domain names that were hosted on the DNS servers before the critical malfunction. For more information, see Add a Forward Lookup Zone ([https://go.microsoft.com/fwlink/?LinkId=74574](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771566%28v=ws.11%29)).
3. Configure the DNS data as it existed before the critical malfunction. For example:
    - Configure DNS zones to be stored in AD DS. For more information, see Change the Zone Type ([https://go.microsoft.com/fwlink/?LinkId=74579](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771150%28v=ws.11%29)).
    - Configure the DNS zone that is authoritative for domain controller locator (DC Locator) resource records to allow secure dynamic update. For more information, see Allow Only Secure Dynamic Updates ([https://go.microsoft.com/fwlink/?LinkId=74580](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753751%28v=ws.11%29)).
4. Ensure that the parent DNS zone contains delegation resource records (name server (NS) and glue host (A) resource records) for the child zone that is hosted on this DNS server. For more information, see Create a Zone Delegation ([https://go.microsoft.com/fwlink/?LinkId=74562](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753500%28v=ws.11%29)).
5. After you configure DNS, you can speed up registration of the NETLOGON Records. 
    Note

    Secure dynamic updates only work when a global catalog server is available. At the command prompt, type the following command, and then press ENTER: `net stop netlogon`
6. Type the following command, and then press ENTER: `net start netlogon`![DNS server](media/dns3.png)