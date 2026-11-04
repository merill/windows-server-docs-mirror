---
layout: Conceptual
title: Managing WSUS Client computers and WSUS computer Groups | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/manage/managing-wsus-client-computers-and-wsus-computer-groups
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: wsus
ms.update-cycle: 1095-days
description: Windows Server Update Service (WSUS) topic - How to manage client computers and groups
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0cfb7b55-6852-69f8-5fd4-a12b42967923
document_version_independent_id: 98ae4498-a9f1-2a09-0ac0-2c6b80d0cd9f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-server-update-services/manage/managing-wsus-client-computers-and-wsus-computer-groups.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-server-update-services/manage/managing-wsus-client-computers-and-wsus-computer-groups
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-server-update-services/manage/managing-wsus-client-computers-and-wsus-computer-groups.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e15cf5c-4ecb-276b-28bb-0f443189f002
---

# Managing WSUS Client computers and WSUS computer Groups | Microsoft Learn

The Computers node is the central access point in the WSUS administrative console for managing WSUS client computers and devices. Under this node you can find the different groups you have set up (plus the default group, Unassigned computers).

## Managing Client computers

Selecting one of the computer groups in the **Computers** node causes the computers in that group to be displayed in the details pane. If a computer is assigned to multiple groups, it will appear in the listings of all groups. If you select a computer in the list, you can see its properties, which include general details about the computer and the status of updates for it. You can filter the list of computers under a given computer group by status. The default shows only computers for which updates are needed or which have had installation failures; however, you can filter the display by any status. Click **Refresh** after changing the status filter.

You can also manage computer groups on the computers page, which includes creating the groups and assigning computers to them. For more information about managing computer groups, see Managing computer Groups in the next section of this guide, and section [1.5. Plan WSUS computer groups](../plan/plan-your-wsus-deployment#15-plan-wsus-computer-groups) in Step 1: Prepare for Your WSUS Deployment of the WSUS deployment guide.

Note

You must first configure client computers to contact the WSUS server before you can manage them from that server. Until you perform this task, your WSUS server will not recognize your client computers and they will not be displayed in the list on the computers page. For more information about setting up client computers, see [1.5. Plan WSUS computer groups](../plan/plan-your-wsus-deployment#15-plan-wsus-computer-groups) of Step 1: Prepare for Your WSUS Deployment, and Step 3: Configure WSUS, in the WSUS deployment guide.

## Controlling when WSUS client computers install updates

There are two methods to control when WSUS client computers install updates:

- Approval with deadlines: Deadlines strictly enforce when an update is installed
- WSUS Group Policies: Group Policies control when the Windows Update Agent scans and installs updates

    For more information, see [Step 5: Configure Group Policy Settings for Automatic Updates](../deploy/4-configure-group-policy-settings-for-automatic-updates), in the WSUS Deployment Guide.

## Managing computer Groups

WSUS allows you to target updates to groups of client computers, so you can ensure that specific computers always get the right updates at the most convenient times. For example, if all the computers in one department (such as the Accounting team) have a specific configuration, you can set up a group for that team, decide which updates their computers need and what time they should be installed, and then use WSUS reports to evaluate the updates for the team.

Computers are always assigned to the **All computers** group, and remain assigned to the **Unassigned computers** group until you assign them to another group. Computers can belong to more than one group.

Computer groups can be set up in hierarchies (for example, the Payroll group and the Accounts Payable group below the Accounting group). Updates that are approved for a higher group will automatically be deployed to lower groups, as well as to the higher group itself. Thus, if you approve Update1 for the Accounting group, the update will be deployed to all the computers in the Accounting group, all the computers in the Payroll group, and all the computers in the Accounts Payable group.

Because computers can be assigned to multiple groups, it is possible for a single update to be approved more than once for the same computer. However, the update will be deployed only once, and any conflicts will be resolved by the WSUS server. To continue with the example above, if computerA is assigned to both the Payroll and the Accounts Payable groups, and Update1 is approved for both groups, it will be deployed only once.

You can assign computers to computer groups by using one of two methods, server-side targeting or client-side targeting. With server-side targeting, you manually move one or more client computers to one computer group at a time. With client-side targeting, you use Group Policy or edit the registry settings on client computers to enable those computers to automatically add themselves into the previously created computer groups. This process can be scripted and deployed to many computers at once. You must specify the targeting method you will use on the WSUS server by selecting one of the two options on the **Computers** section of the **Options** page.

Note

If a WSUS server is running in replica mode, computer groups cannot be created on that server. All the computer groups needed for clients of the replica server must be created on the WSUS server that is the root of the WSUS server hierarchy. For more information about replica mode, see [Running WSUS Replica mode](running-wsus-replica-mode) and for more information about server-side and client-side targeting, see section [1.5. Plan WSUS computer groups](../plan/plan-your-wsus-deployment#15-plan-wsus-computer-groups) of Step 1: Prepare for Your WSUS Deployment in the WSUS deployment guide.