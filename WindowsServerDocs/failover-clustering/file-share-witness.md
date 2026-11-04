---
layout: Conceptual
title: Configure a file share witness for Failover Clustering in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/failover-clustering/file-share-witness
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: failover-clustering
ms.update-cycle: 1095-days
description: Configure cluster quorum as a file share witness in domain-joined and non-domain joined devices using Failover Cluster Manager.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-01-28T00:00:00.0000000Z
locale: en-us
document_id: 906e7261-a2cb-bb56-e596-7681a721c288
document_version_independent_id: e2a93d15-92ca-adb2-9625-03e40cf4bb67
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/failover-clustering/file-share-witness.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: failover-clustering/file-share-witness
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/failover-clustering/file-share-witness.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: c8bd7823-e28a-cf1b-34d8-2a4076b1b5ce
---

# Configure a file share witness for Failover Clustering in Windows Server | Microsoft Learn

When a cluster contains an even number of voting nodes, you should configure a witness. Adding a witness vote enables the cluster to continue running if half the cluster nodes simultaneously go down or are disconnected. A file share witness is a type of quorum witness that uses a Server Message Block (SMB) file share to maintain cluster information in a log file. This file share can be hosted on a server, USB storage, or Network Attached Storage (NAS).

The file share witness is also beneficial for multisite clusters with replicated storage.

You might use a file share witness when:

- A Cloud Witness can't be used because your cluster nodes don't have a reliable internet connection or an internet connectivity.
- A disk witness can't be used because there aren't any shared drives to use for a disk witness. For example, a Storage Spaces Direct cluster, SQL Server Always On Availability Groups (AG), or Exchange Database Availability Group (DAG). None of these types of clusters use shared disks.

In this article, learn how-to configure a file share witness for your Failover Cluster.

## Prerequisites

Before you can use a file share witness, you must have the following prerequisites in place:

- The Failover Cluster feature must be installed and configured on your device. To learn more, see [Install or Uninstall Roles, Role Services, or Features](/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features).
- You have the **Full Control** permission on the Failover Cluster.
- Administrative credentials to configure a file share on the witness device.
- A device to host the file share witness supporting SMB 2 or later.
- If you're using a non-domain joined device for the file share, your cluster must be running Windows Server 2019 or later.
- The device hosting the file share witness must have a minimum of 5 MB of free space.

Warning

The use of Distributed File System (DFS) or replicated storage technologies isn't supported with failover clustering. DFS can cause a partition-in-space or partition-in-time, where the cluster nodes are running independently of each other and could cause data loss.

## Configure the file share

When configuring a file share witness for the cluster quorum, the file share:

- Must be dedicated to the single cluster and not used to store user or application data.
- A single file server can be configured with multiple file shares to use as a witness for multiple clusters.
- Should be physically separate from the cluster nodes or cluster sites. For example, consider the separation of network, power, rack, and rooms if necessary. Separation allows opportunity for cluster nodes or sites to survive if network communication between them is lost.
- You can use a separate Failover Cluster for high availability of the file share.

The file share witness can be hosted on a domain-joined Windows device or a non-domain joined device, for example:

- NAS devices.
- Windows devices joined to a workgroup.
- Routers with local USB storage.

The steps to configure the file share witness are different depending on the type of device hosting the file share. To create the file share, select the relevant tab for your scenario.

# [Domain-joined Windows device](#tab/domain-joined-witness)
To configure the file share witness on a domain-joined Windows device, follow these steps:

Important

The SMB file share must be hosted on a Windows server joined to the same Active Directory forest as the cluster.

1. Right-click **Start**, select **Computer Management**.
2. In the **Computer Management** console, expand **System Tools &gt; Shared Folders**.
3. Right-click **Shares**, select **New Share**.
4. On the **Create A Shared Folder Wizard**, select **Next** to begin.
5. Enter the path to the folder that you want to share or select **Browse** to locate a folder, then select **Next**.
6. Enter a name for the **Share name**, then select **Change** to configure the offline settings. Adding a description for the share is optional.
7. Select **No files or programs from the shared folder are available offline**. Select **OK**, then select **Next**.
8. Under **Shared Folder Permissions**, select **Customize permissions**, then select **Custom**.
9. Select **Everyone**, then select **Remove**.
10. Select **Add**, enter the name, or locate the Cluster Name Object (CNO) for the cluster or suitable Active Directory group containing the CNO. Then select **OK**.
11. Select both **Change** and **Read** permissions.
12. Select the **Security** tab, then select **Advanced**.
13. In the **Advanced Security Settings** screen, under the **Permissions** tab, select **Add**.
14. Select **Select a principal**, and then enter the name or locate the Cluster Name Object (CNO) for the cluster or suitable Active Directory group containing the CNO. Select **OK**.
15. Under **Basic permissions**, select **Modify**, **Read & execute**, **List folder contents**, and **Read**. Then select **OK**.
16. Confirm and configure any other folder permissions to meet your organization's requirements. Select **OK** for each dialog until you return to the **Shared Folder Permissions** screen.
17. Select **Finish** to create the share.

Now you have a file share on a domain-joined Windows device with the necessary permissions per your organization. Proceed to the next step to configure the cluster quorum settings.

# [Non-domain joined device](#tab/nondomain-joined-witness)
To configure the file share witness on a non-domain joined device, follow these steps:

Important

If you're using a non-Windows device, consult your vendor documentation for how to create local accounts and configuring an SMB share on your device. These steps are generalized.

1. Sign in to your device as an administrator.
2. Create a local account on the device for the cluster to use to authenticate the file share. Store the credentials in a secure location.
3. Create an SMB file share on the device that uses the SMB 2 or later protocol.
4. Update the share permissions to remove all users and groups except the new local account and any permissions required to meet your organization's requirements. The new local account should have the **Change** and **Read** permissions.
5. If necessary, modify your file system permissions. Grant the new local account **Modify**, **Read & execute**, **List folder contents**, and **Read** permissions as applicable to your file system. The local account must have write access.
6. Confirm and configure any other folder permissions to meet your organization's requirements.
7. Complete any further steps to create the file share.

Now you have a file share on a non-domain joined Windows device with the necessary permissions per your organization. Proceed to the next step to configure the cluster quorum settings.

---

## Configure the cluster quorum

You can configure the cluster quorum settings by using Failover Cluster Manager or the [FailoverClusters](/en-us/powershell/module/failoverclusters/failoverclusters) PowerShell module.

# [Domain joined Windows device](#tab/domain-joined-witness)
To configure the cluster quorum to use a file share witness on a domain joined device using Failover Cluster Manager, follow these steps:

1. In **Server Manager**, select **Tools**, then select **Failover Cluster Manager**.
2. On the left pane, under **Failover Cluster Manager**, select the cluster that you want to configure.
3. On the right pane, under **Actions**, select **More Actions**, and then select **Configure Cluster Quorum Settings**.
4. Under the **Configure Cluster Quorum Wizard**, select **Next**.
5. Under **Select Quorum Configuration Option**, select **Select the quorum witness**, then select **Next**.
6. Under **Select Quorum Witness**, select **Configure a file share witness**, then select **Next**.
7. Under **Configure File Share Witness**, type the file path location or select **Browse**, select **Browse** again and locate the file share to use as the witness resource. Then select **Next**.
8. Under **Confirmation**, review your configuration and select **Next**.
9. After the wizard runs, the **Summary** page appears. If you want to view a report of the tasks that the wizard performed, select **View Report**. Select **Finish** to complete your configuration.

Note

After you configure the cluster quorum, we recommend that you run the **Validate Quorum Configuration** test to verify the updated quorum settings.

# [Non-domain joined device](#tab/nondomain-joined-witness)
Here's how to configure the cluster quorum to use a file share witness on a non-domain joined device. A non-domain joined file share witness can only be configured from PowerShell using the [Set-ClusterQuorum](/en-us/powershell/module/failoverclusters/set-clusterquorum) cmdlet.

Sign into the device that has the Failover Cluster Management Remote Server Administration Tool (RSAT) installed or on a server where you installed the Failover Cluster feature. Perform the following steps:

1. Open an elevated PowerShell window.
2. Run the following command to configure the cluster quorum to use a file share witness. You're prompted to enter the local credential for the file share witness. Replace `<ClusterName>` with the name of your cluster and `\\FileShareWitnessServer\WitnessShare` with the path to the file share witness.

    ```powershell
    Set-ClusterQuorum -Cluster <ClusterName> -FileShareWitness \\FileShareWitnessServer\WitnessShare -Credential (Get-Credential)
    ```
3. To verify the cluster quorum settings, run the following command:

    ```powershell
    Get-ClusterQuorum -Cluster <ClusterName> | Format-List *
    ```

After you configure the cluster quorum, we recommend that you validate the quorum configuration settings by running the `Test-Cluster` cmdlet.

---