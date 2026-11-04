---
layout: Conceptual
title: Forest Design Models | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/forest-design-models
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Forest Design Models'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: c617af5e-5261-e7d7-f1ef-43667cdb9afe
document_version_independent_id: f15d4ce9-f39d-c2e0-9f8d-b6cff36c6070
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Forest-Design-Models.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/forest-design-models
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Forest-Design-Models.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 72f3bc3a-c38b-8459-3833-b9f450dd4be6
---

# Forest Design Models | Microsoft Learn

You can apply one of the following three forest design models in your Active Directory environment:

- Organizational forest model
- Resource forest model
- Restricted access forest model

It is likely that you will need to use a combination of these models to meet the needs of all the different groups in your organization.

## Organizational forest model

In the organizational forest model, user accounts and resources are contained in the forest and managed independently. The organizational forest can be used to provide service autonomy, service isolation, or data isolation, if the forest is configured to prevent access to anyone outside the forest.

If users in an organizational forest need to access resources in other forests (or the reverse), trust relationships can be established between one organizational forest and the other forests. This makes it possible for administrators to grant access to resources in the other forest. The following illustration shows the organizational forest model.

![Illustration that shows the organizational forest model.](media/forest-design-models/b1ddb47e-78a5-49c7-bb21-d7421b7b84b8.gif)

Every Active Directory design includes at least one organizational forest.

## Resource forest model

In the resource forest model, a separate forest is used to manage resources. Resource forests do not contain user accounts other than those required for service administration and those required to provide alternate access to the resources in that forest, if the user accounts in the organizational forest become unavailable. Forest trusts are established so that users from other forests can access the resources contained in the resource forest. The following illustration shows the resource forest model.

![Illustration that shows the resource forest model.](media/forest-design-models/c0b348a6-958c-4fc5-9035-e2d2a54d5573.gif)

Resource forests provide service isolation that is used to protect areas of the network that need to maintain a state of high availability. For example, if your company includes a manufacturing facility that needs to continue to operate when there are problems on the rest of the network, you can create a separate resource forest for the manufacturing group.

## Restricted access forest model

In the restricted access forest model, a separate forest is created to contain user accounts and data that must be isolated from the rest of the organization. Restricted access forests provide data isolation in situations where the consequences of compromising project data are severe. The following illustration shows a restricted access forest model.

![forest design models](media/forest-design-models/e49cfc8c-a58a-4386-93bd-d4a6ee00f89c.gif)

Users from other forests cannot be granted access to the restricted data because no trust exists. In this model, users have an account in an organizational forest for access to general organizational resources and a separate user account in the restricted access forest for access to the classified data. These users must have two separate workstations, one connected to the organizational forest and the other connected to the restricted access forest. This protects against the possibility that a service administrator from one forest can gain access to a workstation in the restricted forest.

In extreme cases, the restricted access forest might be maintained on a separate physical network. Organizations that work on classified government projects sometimes maintain restricted access forests on separate networks to meet security requirements.