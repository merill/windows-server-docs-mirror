---
layout: Conceptual
title: Checklist - Configuring the Account Partner Organization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/checklist--configuring-the-account-partner-organization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Checklist: Configuring the Account Partner Organization'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: bb1f6762-5f15-b683-d7f3-3ab97dffdb9f
document_version_independent_id: 47c10c58-de4a-2d0c-2b23-7190822c3674
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Checklist--Configuring-the-Account-Partner-Organization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/checklist--configuring-the-account-partner-organization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Checklist--Configuring-the-Account-Partner-Organization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: d0cfd4c6-1e74-19f2-5824-cbe6ef0a562f
---

# Checklist - Configuring the Account Partner Organization | Microsoft Learn

The account partner organization contains the users that will access Web-based applications in the resource partner. Administrators in this organization must use the AD FS Management snap-in to create relying party trusts to represent their trust relationships with resource partner organizations. In turn, the resource partner administrator must create claims provider trusts for each account partner organization that they want to trust.

This checklist includes tasks for deploying Active Directory Federation Services (AD FS) in the account partner organization. It also includes tasks for configuring the components that are required to establish one-half of a federation partnership.

If you are deploying a [Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807033%28v=ws.11%29), you do not have to follow this checklist. However, you do have to complete the tasks in this checklist to successfully deploy a [Federated Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807050%28v=ws.11%29).

Important

Make sure that the administrator in the resource partner organization follows the guidance in [Checklist: Configuring the Resource Partner Organization](checklist--configuring-the-resource-partner-organization) to ensure that all necessary deployment tasks will be completed to successfully create the second half of the federation partnership.

Note

Complete the tasks in this checklist in order. When a reference link takes you to a procedure, return to this topic after you complete the steps in that procedure so that you can proceed with the remaining tasks in this checklist.

![Check mark icon, Configure the account partner organization.](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**Checklist: Configuring the account partner organization**

| Task | Reference |
| --- | --- |
| If you have an existing AD FS 1.0 or 1.1 deployment in your production environment today, see the link to the right for information about how to migrate settings from your current Federation Service to a new AD FS Federation Service. If you are deploying AD FS for the first time in your organization using AD FS, you can skip this step and continue to the next task in this checklist for information about how to set up a new account partner organization. | ![Icon, Plan to migrate to AD FS 2.0.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning a Migration to AD FS 2.0](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff678044%28v=ws.10%29) |
| Based on your deployment goals, review information about the components that are required to provide users with access to the federated applications. | ![Icon, Provide your AD users access to your claims-aware applications.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807071%28v=ws.11%29)<br>![Icon, Provide your AD users access to applications and services.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Provide Your Active Directory Users Access to the Applications and Services of Other Organizations](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807123%28v=ws.11%29)<br><br>![Icon, Provide users in another organization access to your claims-aware applications and services.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Provide Users in Another Organization Access to Your Claims-Aware Applications and Services](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807099%28v=ws.11%29) |
| Determine which AD FS design this account partner organization will be associated with. | ![Icon, Web SSO design.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807033%28v=ws.11%29)<br>![Icon, Federated Web SSO design.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Federated Web SSO Design](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807050%28v=ws.11%29) |
| Before you begin deploying your AD FS servers, review the; 1.) advantages and disadvantages of choosing either Windows Internal Database (WID) or SQL Server to store the AD FS configuration database 2.) AD FS deployment topology types and their associated server placement and network layout recommendations. | ![Icon, Determine your AD FS deployment topology.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Determine Your AD FS Deployment Topology](../design/determine-your-ad-fs-deployment-topology)<br>![Icon, AD FS deployment topology considerations.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[AD FS Deployment Topology Considerations](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/gg982489%28v=ws.11%29) |
| Review AD FS capacity planning guidance to determine the proper number of federation server and federation server proxy servers you should use in your production environment. | ![Icon, Plan for AD FS server capacity.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning for AD FS Server Capacity](../design/planning-for-ad-fs-server-capacity) |
| To effectively plan and implement the physical topology for the account partner deployment, determine whether your AD FS design requires one or more federation servers or federation server proxies. | ![Icon, Set up a Federation server.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)<br>![Icon, Set up a Federation server proxy.](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy) |
| Determine the type of attribute store that you want to add to AD FS. Then, add the attribute store using the AD FS Management snap-in. | ![Icon, The role of attribute stores.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Attribute Stores](../technical-reference/the-role-of-attribute-stores)<br>![Icon, Add an attribute store.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Add an Attribute Store](../operations/add-an-attribute-store) |
| If you will need to send claims to or consume claims from a resource partner who is using either an AD FS 1.0 or 1.1 Federation Service, see the link to the right for information about how to configure AD FS to interoperate with previous versions of AD FS. If the resource partner organization is also using AD FS to send or consume claims to your organization, you can skip this step and continue with the next task in this checklist. | ![Icon, Plan for interoperability with AD FS 1.x.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning for Interoperability with AD FS 1.x](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678040%28v=ws.11%29) |
| After you deploy the first federation server in the account partner organization, create a relying party trust relationship using the AD FS Management snap-in. You can create a relying party trust by entering data about a resource partner manually or by using a federation metadata URL that the administrator of the resource partner organization provides to you. You can use the federation metadata to retrieve the data for the resource partner automatically. **Note:** If the resource partner publishes its federation metadata or can provide a file copy of it for you to use, we recommend that you retrieve the data automatically because it can save time. | ![Icon, Manually create a relying party trust.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Relying Party Trust Manually](../operations/create-a-relying-party-trust)<br>![Icon, Create a relying party trust using Federation metadata.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Relying Party Trust Using Federation Metadata](../operations/create-a-relying-party-trust) |
| Depending on the needs of your organization, create one or more claim rule sets for each relying party trust that is specified in the AD FS Management snap-in so that claims will be issued appropriately. | ![Icon, Create claim rules for a relying party trust.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Checklist: Creating Claim Rules for a Relying Party Trust](checklist--creating-claim-rules-for-a-relying-party-trust) |
| A claim description must be created if one does not already exist that will fulfill the needs of your organization. AD FS ships with a default set of claim descriptions that are exposed in the AD FS Management snap-in. | ![Icon, Add a claim description.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Add a Claim Description](../operations/add-a-claim-description) |
| Determine whether your organization will need to use identity delegation to authorize or constrain a specified account to "act as" or impersonate other users. This is often a requirement when front-end Web applications must interact with back-end Web services. | ![Icon, Use identity delegation.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[When to Use Identity Delegation](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807122%28v=ws.11%29) |
| Prepare client computers for federation by:<br>- Adding the URL for the account partner federation server to the trusted sites list for the client browser.- Using Group Policy to push the appropriate Secure Sockets Layer (SSL) certificates to client computers. | ![Icon, Prepare client computers in the account partner.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Prepare Client Computers in the Account Partner](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807114%28v=ws.11%29)<br>![Icon, Configure client computers to trust the account Federation server.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Configure Client Computers to Trust the Account Federation Server](configure-client-computers-to-trust-the-account-federation-server)<br><br>![configure account partner org](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Distribute Certificates to Client Computers by Using Group Policy](distribute-certificates-to-client-computers-by-using-group-policy) |