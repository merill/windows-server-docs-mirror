---
layout: Conceptual
title: Step 3 - Approve and Deploy Updates in WSUS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/deploy/3-approve-and-deploy-updates-in-wsus
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: wsus
ms.update-cycle: 1095-days
description: Windows Server Update Service (WSUS) topic - Approve and Deploy Updates in WSUS is step three in a four step process for deploying WSUS
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-03T00:00:00.0000000Z
locale: en-us
document_id: 30cf542b-ba6f-4d92-2e19-cfe97d632f7a
document_version_independent_id: 48a4babb-cf50-35bb-7052-44d1f9b05fab
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-server-update-services/deploy/3-approve-and-deploy-updates-in-wsus.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-server-update-services/deploy/3-approve-and-deploy-updates-in-wsus
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-server-update-services/deploy/3-approve-and-deploy-updates-in-wsus.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b740ab61-581c-883d-95e0-1977f3e945ac
---

# Step 3 - Approve and Deploy Updates in WSUS | Microsoft Learn

Computers in a computer group automatically contact the WSUS server over the next 24 hours to obtain updates. You can use the WSUS reporting feature to determine whether those updates were deployed to the test computers. When the tests are successfully completed, you can approve the updates for the applicable computer groups in your organization.

## 3.1. Approve and deploy WSUS updates

Use the following procedure to approve and deploy updates.

#### To approve and deploy WSUS updates

1. On the WSUS Administration Console, click **Updates**. In the right pane, an update status summary is displayed for **All Updates**, **Critical Updates**, **Security Updates**, and **WSUS Updates**.
2. In the **All Updates** section, click **Updates needed by computers**.
3. In the list of updates, select the updates that you want to approve for installation in your test computer group. Information about a selected update is available in the bottom pane of the **Updates** panel. To select multiple contiguous updates, hold down the **shift** key while clicking the update names. To select multiple noncontiguous updates, press down the **CTRL** key while clicking the update names.
4. Right-click the selection, and then click **Approve**.
5. In the **Approve Updates** dialog box, select your test group, and then click the down arrow.
6. Click **Approved for Install**, and then click **OK**.
7. The **Approval Progress** window appears, which shows the progress of the tasks that affect update approval. When the approval process is complete, click **Close**.

## 3.2. Configure auto-approval rules

Automatic Approvals enables you to specify how to automatically approve installation of updates for selected groups, and how to approve revisions to existing updates.

#### To configure Automatic Approvals

1. In the WSUS Administration Console, under **Update Services**, expand the WSUS server, and then click **Options**. The **Options** window opens.
2. In **Options**, click **Automatic Approvals**. The Automatic Approvals dialog opens.
3. In **Update Rules**, click **New Rule**. The **add Rule** dialog opens.
4. In **add Rule**, in **Step 1: select Properties**, select any single option, or combination of options from the following:

    - **When an update is in a specific classification**

        - When selecting the **Upgrades** classification, be aware that Windows feature updates that get published monthly are also classified as **Upgrades**. Automatically approving these updates could cause devices to upgrade their OS. For example, applicable Windows 10 devices could get upgraded to Windows 11. Additionally, feature updates would require additional disk space. For more information, see [UUP considerations when planning your WSUS deployment](../plan/plan-your-wsus-deployment#uup-considerations).
    - **When an update is in a specific product**
    - **Set a deadline for the approval**
5. In **Step 2: edit the properties**, click each of the options listed, and then select the appropriate options for each.
6. In **Step 3: Specify a name**, type a name for your rule, and then click **OK**.
7. Click **OK** to close the Automatic Approvals dialog.

## 3.3. Review installed updates with WSUS Reports

24 hours after you approve the updates, you can use the WSUS Reports feature to determine whether the updates were deployed to the test group computers. To check the status of an update, you can use the WSUS Reports feature as follows.

#### To review updates

1. In the navigation pane of the WSUS Administration Console, click **Reports**.
2. On the **Reports** page, click the **Update Status Summary** report. The **Updates Report** window appears.
3. If you want to filter the list of updates, select the criteria that you want to use, for example, **Include updates in these classifications**, and then click **Run Report**.
4. You will see the **Updates Report** pane. You can check the status of individual updates by selecting the update in the left section of the pane. The last section of the report pane shows the status summary of the update.
5. You can save or print this report by clicking the applicable icon on the toolbar.
6. After you test the updates, you can approve the updates for installation on the applicable computer groups in your organization.