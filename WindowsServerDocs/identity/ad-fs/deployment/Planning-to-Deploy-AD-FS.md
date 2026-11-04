---
layout: Conceptual
title: Planning to Deploy AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/planning-to-deploy-ad-fs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Planning to Deploy AD FS'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: 997b0bf4-b0b4-7026-9817-ffba130318b8
document_version_independent_id: 87f787b9-310e-5eef-f6f3-b4343b7ecf93
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Planning-to-Deploy-AD-FS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/planning-to-deploy-ad-fs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Planning-to-Deploy-AD-FS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: 380ff332-728e-bcde-62cb-123edb1dbf05
---

# Planning to Deploy AD FS | Microsoft Learn

After you collect information about your environment and you decide on an Active Directory Federation Services (AD FS) design by following the guidance in the [AD FS Design Guide in Windows Server 2012](../design/ad-fs-design-guide-in-windows-server-2012), you can begin to plan the deployment of your organization's AD FS design. With the completed design and the information in this topic, you can determine which tasks to perform to deploy AD FS in your organization.

## Reviewing your AD FS design

If the design team that constructed the original AD FS design for your organization is different from the deployment team that will actually implement the deployment, make sure that the deployment team reviews the final design with the design team. Review the following points regarding the design:

- The design team's strategy to determine the best physical topology for the placement of federation servers in your corporate network or perimeter network. The deployment team can refer to documentation about this subject by reviewing the following topics in the AD FS Design Guide:

    - [The Role of the AD FS Configuration Database](../technical-reference/the-role-of-the-ad-fs-configuration-database)
    - [Planning Federation Server Placement](../design/planning-federation-server-placement)
    - [Planning Federation Server Proxy Placement](../design/planning-federation-server-proxy-placement)

    It is possible that the design team might leave the subject of federation server or federation server proxy placement for the deployment team. The deployment team is then responsible for documenting and implementing the physical topology of the servers.
- The business reasons for your organization's designation as a claims provider, relying party, or both, within the scope of the documented AD FS design. Ensure that members of the deployment team understand the reasons why AD FS is being deployed and what other companies or organizations are involved in the federation partnership. Ensure that members of the deployment team also understand the constraints that exist for the other companies or organizations (limited hardware, no extranet environment, and so forth) that may limit the scope of the design in some way. For more information about partner organizations, see [Planning Your Deployment](../design/planning-your-deployment).

After the design teams and deployment teams agree on these issues, they can proceed with the deployment of the AD FS design. For more information, see [Implementing Your AD FS Design Plan](implementing-your-ad-fs-design-plan).