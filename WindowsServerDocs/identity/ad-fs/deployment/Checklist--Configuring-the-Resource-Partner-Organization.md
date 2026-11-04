---
layout: Conceptual
title: Checklist - Configuring the Resource Partner Organization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/checklist--configuring-the-resource-partner-organization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Checklist: Configuring the Resource Partner Organization'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: f52fd4bb-a3e8-45b4-1dbf-68b0292c4232
document_version_independent_id: 726078ab-f04b-b3c6-bcbd-b1260f4c34b6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Checklist--Configuring-the-Resource-Partner-Organization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/checklist--configuring-the-resource-partner-organization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Checklist--Configuring-the-Resource-Partner-Organization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 17da6fb8-ff73-1379-6d2b-a3ea0f631326
---

# Checklist - Configuring the Resource Partner Organization | Microsoft Learn

The resource partner organization contains the Web servers hosting the Web-based applications that will be accessed by users in the account partner. Administrators in this organization must use the AD FS Management snap-in to create claims provider trusts to represent their trust relationships with account partner organizations. In turn, the account partner administrator must create relying party trusts for each account partner organization that they want to trust.

This checklist includes the tasks that are necessary for deploying Active Directory Federation Services (AD FS) in the resource partner organization. It also includes tasks for configuring the components that are required to establish one-half of a federation partnership.

If you are deploying a [Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807033%28v=ws.11%29), you do not have to follow this checklist. However, you do have to complete the tasks in this checklist to successfully deploy a [Federated Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807050%28v=ws.11%29).

Important

Make sure that the administrator of the account partner organization follows the guidance in [Checklist: Configuring the Account Partner Organization](checklist--configuring-the-account-partner-organization) to ensure that all necessary deployment tasks will be completed to successfully create the second half of the federation partnership

Note

Complete the tasks in this checklist in order. When a reference link takes you to a procedure, return to this topic after you complete the steps in that procedure so that you can proceed with the remaining tasks in this checklist.

![Check mark icon for the Configuring the resource partner organization check list.](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**Checklist: Configuring the resource partner organization**

| Task | Reference |
| --- | --- |
| If you have an existing AD FS 1.0 or 1.1 deployment in your production environment today, see the link to the right for information about how to migrate settings from your current Federation Service to a new AD FS Federation Service. If you are deploying AD FS for the first time in your organization using AD FS, you can skip this step and continue to the next task in this checklist for information about how to set up a new resource partner organization. | ![Icon for the Planning a Migration to AD FS link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning a Migration to AD FS](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff678044%28v=ws.10%29) |
| Based on your deployment goals, review information about the components that are required to provide users with access to the federated applications. | ![Icon for the Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807071%28v=ws.11%29)<br>![Icon for the Provide Your Active Directory Users Access to the Applications and Services of Other Organizations link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Provide Your Active Directory Users Access to the Applications and Services of Other Organizations](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807123%28v=ws.11%29)<br><br>![Icon for the Provide Users in Another Organization Access to Your Claims-Aware Applications and Services link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Provide Users in Another Organization Access to Your Claims-Aware Applications and Services](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807099%28v=ws.11%29) |
| Determine which AD FS design this resource partner organization will be associated with. | ![Icon for the Web SSO Design link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807033%28v=ws.11%29)<br>![Icon for the Federated Web SSO Design link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Federated Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807050%28v=ws.11%29) |
| Review the different application types, and decide which application to deploy. | ![Icon for the Determine Your Federated Application Strategy in the Resource Partner link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Determine Your Federated Application Strategy in the Resource Partner](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807077%28v=ws.11%29) |
| Before you begin deploying your AD FS servers, review the; 1.) advantages and disadvantages of choosing either Windows Internal Database (WID) or SQL Server to store the AD FS configuration database 2.) AD FS deployment topology types and their associated server placement and network layout recommendations. | ![Icon for the Determine Your AD FS Deployment Topology link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Determine Your AD FS Deployment Topology](../design/determine-your-ad-fs-deployment-topology)<br>![Icon for the AD FS Deployment Topology Considerations link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[AD FS Deployment Topology Considerations](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/gg982489%28v=ws.11%29) |
| Review AD FS capacity planning guidance to determine the proper number of federation server and federation server proxy servers you should use in your production environment. | ![Icon for the Planning for AD FS Server Capacity link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning for AD FS Server Capacity](../design/planning-for-ad-fs-server-capacity) |
| To effectively plan and implement the physical topology for the account partner deployment, determine whether your AD FS design requires one or more federation servers or federation server proxies. | ![Icon for the Checklist: Setting Up a Federation Server link.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)<br>![Icon for the Checklist: Setting Up a Federation Server Proxy link.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy) |
| Determine the type of attribute store that you want to add to AD FS. Then, add the attribute store using the AD FS Management snap-in. | ![Icon for the The Role of Attribute Stores link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Attribute Stores](../technical-reference/the-role-of-attribute-stores)<br>![Icon for the Add an Attribute Store link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Add an Attribute Store](../operations/add-an-attribute-store) |
| If you will need to send claims to or consume claims from an account partner who is using either an AD FS 1.0 or 1.1 Federation Service, see the link to the right for information about how to configure AD FS to interoperate with previous versions of AD FS. If the account partner organization is also using AD FS to send or consume claims to your organization, you can skip this step and continue with the next task in this checklist. | ![Icon for the Planning for Interoperability with AD FS 1.x link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning for Interoperability with AD FS 1.x](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678040%28v=ws.11%29) |
| After you deploy the first federation server in the resource partner organization, create a claims provider trust relationship by using the AD FS Management snap-in. You can create a claims provider trust by entering data about an account partner manually or by using a federation metadata URL that the administrator of the account partner organization provides to you. You can use the federation metadata to retrieve the data for the resource partner automatically. **Note:** If the account partner publishes its federation metadata or can provide a file copy of it for you to use, we recommend that you retrieve the data automatically because it can save time. | ![Icon for the Create a Claims Provider Trust Manually link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Claims Provider Trust Manually](../operations/create-a-claims-provider-trust#to-create-a-claims-provider-trust-manually)<br>![Icon for the Create a Claims Provider Trust Using Federation Metadata link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Claims Provider Trust Using Federation Metadata](../operations/create-a-claims-provider-trust#to-create-a-claims-provider-trust-using-federation-metadata) |
| Depending on the needs of your organization, create one or more claim rule sets for each claims provider trust that is specified in the AD FS Management snap-in so that incoming claims will be passed through, transformed, or mapped appropriately to corresponding claims in the resource partner. | ![Icon for the Checklist: Creating Claim Rules for a Claims Provider Trust link.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Creating Claim Rules for a Claims Provider Trust](checklist--creating-claim-rules-for-a-claims-provider-trust) |
| (Optional) A claim description may have to be created if one does not already exist that will fulfill the needs of your organization. AD FS includes a default set of claim descriptions that are exposed in the AD FS Management snap-in. | ![configure resource partner org](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Add a Claim Description](../operations/add-a-claim-description) |