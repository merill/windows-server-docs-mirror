---
layout: Conceptual
title: Configure failover cluster accounts in Active Directory | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/failover-clustering/configure-failover-cluster-accounts
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: failover-clustering
ms.update-cycle: 1095-days
description: Learn how to configure cluster accounts in Active Directory for Windows Server failover clusters.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2025-07-17T00:00:00.0000000Z
locale: en-us
document_id: 4fa80e51-1cef-3dfd-807e-f0150c801b70
document_version_independent_id: ee403411-e81d-67af-d04d-00064ea045f0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/failover-clustering/configure-failover-cluster-accounts.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: failover-clustering/configure-failover-cluster-accounts
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/failover-clustering/configure-failover-cluster-accounts.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 16939650-a039-a088-bdfb-f7140a167347
---

# Configure failover cluster accounts in Active Directory | Microsoft Learn

Cluster accounts in Active Directory (AD) are essential for the secure and reliable operation of Windows Server failover clusters. These accounts, which include the cluster name account and accounts for clustered services or applications, enable clusters to interact with domain resources, authenticate actions, and manage permissions. Proper configuration of these accounts ensures that clusters can be created, managed, and maintained in accordance with organizational security policies and best practices.

## Prerequisites

The **Active Directory Domain Services** role must be installed on your device. To learn more, see [Add or remove roles and features in Windows Server](/en-us/windows-server/administration/server-manager/add-remove-roles-features).

The account used by the person installing the cluster is important since it's used to create the computer account for the cluster during setup. The following are required based on your scenario:

- **Domain account**: If you're responsible for creating the cluster account in AD and assigning the necessary permissions, you must have domain-level privileges. You must be a member of the **Domain Admins** or **Account Operators** group or have equivalent permissions.
- **Assigning local permissions**: If the cluster account is already created in AD by someone else, and your task is to add this account to the local **Administrators** group on each cluster server, you only need administrative rights on those servers. You must be a member of the local **Administrators** group on each server.

## Configure the cluster account

Create or obtain the domain account for the person who will install the cluster. This account can be a standard domain user account or an **Account Operators** account. If you're using a standard user account, you'll need to grant additional permissions later in this process. If the account you created or obtained isn't automatically part of the local **Administrators** group on domain computers, follow these steps to add it to the local **Administrators** group on each server that becomes part of the failover cluster:

1. In **Server Manager**, select **Tools**, then select **Computer Management**.
2. In the left pane under **System Tools**, expand **Local Users and Groups**, then expand **Groups**.
3. In the center pane, right-click **Administrators**, select **Add to Group**, then select **Add**.
4. Under the **Enter the object names to select** field, type or search for the name of the user account you created or obtained. If prompted, enter the credentials and then select **OK**.

Repeat these steps on each server that become a node in the failover cluster.

Important

These steps must be repeated on all servers that become nodes in the cluster.

If your account is a domain administrator, you can skip the following steps. Otherwise, you need to grant the account **Create Computer Objects** and **Read All Properties** permissions in the domain's computer accounts container by following these steps on the domain controller (DC):

1. In **Server Manager**, select **Tools**, then select **Active Directory Users and Computers**.
2. Select the **View** tab, then select **Advanced Features**.
3. In the left pane, expand your domain, right-click **Computers**, and then select **Properties**.
4. Select the **Security** tab, then select **Advanced**.
5. Select **Add**, select **Select a principal**, type or search for the name of the account, then select **OK**.
6. Under **Permissions**, select **Create Computer objects**. Under **Properties**, select **Read all properties**. Then select **OK**.
7. Select **OK** to close the **Advanced Security Settings** window, then select **OK** again.

## Prestage the cluster name account

If organizational policies require you to prestage the cluster name account, follow the provided steps. Otherwise, you can allow the Create Cluster Wizard to automatically create and configure the account during cluster setup. Before you begin, ensure you have the cluster name and the user account that will be used to create the cluster. You can use this account to complete the prestaging steps:

1. On the DC, select **Start**, select **Administrative Tools**, and then select **Active Directory Users and Computers**.
2. In the left pane, right-click **Computers**, then select **New** &gt; **Computer**.
3. Enter the name you intend to use for the failover cluster. This is the cluster name that is entered in the Create Cluster Wizard, select **OK**.
4. Right-click the account that you created, then select **Disable Account**. If prompted to confirm your choice, select **Yes**, then select **OK**.

    Disabling the account ensures that the Create Cluster Wizard can verify the account isn't already assigned to another computer or cluster in the domain before proceeding.
5. Select the **View** tab, make sure that **Advanced Features** is selected. If not, select it.
6. Right-click on **Computers**, select **Properties**, select the **Security** tab, then select **Advanced**.
7. Select **Add**, select **Select a principal**, select **Object Types** and ensure **Computers** is selected. Then select **OK**.
8. Under **Enter the object name to select**, type or search for the name of the computer account you created, then select **OK**.
9. A security message displays notifying the addition of a disabled object. Select **OK**.
10. Under **Permissions**, select **Create Computer objects**. Under **Properties**, select **Read all properties**. Select **OK**, then select **OK** again.

If you're using the same account to create the cluster and perform this procedure, you can skip the following steps. Otherwise, ensure that the user account designated for cluster creation has full control permissions on the computer account you created:

1. In **Active Directory Users and Computers**, select the **View** tab. Make sure that **Advanced Features** is selected. If not, select it.
2. In the left pane, select **Computers**. Right-click on the computer account you created and select **Properties**.
3. Select the **Security** tab, select **Add**, select **Object Types** and ensure **Computers** is selected. Then select **OK**.
4. Under **Enter the object name to select**, type or search for the name of the computer account, then select **OK**.
5. Ensure that the user account you just added is selected. Under **Permissions** for the account, select **Full control**, then select **OK**.

## Prestage an account for a clustered service or application (optional)

For most scenarios, it's easier to let the High Availability Wizard automatically create and configure the account during setup. If your organization's policies require prestaging, follow these steps.

Make sure that you know the name of the cluster and the name that the clustered service or application will have.

1. On the DC, in **Server Manager**, select **Tools**, then select **Active Directory Users and Computers**.
2. In the left pane, right-click **Computers**, select **New** &gt; **Computer**.
3. Type the name that you'll use for the clustered service or application, and then select **OK**.
4. Select the **View** tab. Make sure that **Advanced Features** is selected. If not, select it.
5. Right-click the computer account you created, select **Properties**, select the **Security** tab, then select **Add**.
6. Select **Object Types** and ensure **Computers** is selected. Then select **OK**.
7. Under **Enter the object name to select**, type the cluster name account, then select **OK**.
8. Make sure that the cluster name account is selected, select **Full control**, then select **OK**.