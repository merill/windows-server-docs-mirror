---
layout: Conceptual
title: Choose whether to install HGS in its own new forest or in an existing bastion forest | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-choose-where-to-install-hgs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Choose whether to install HGS in its own dedicated forest or in an existing bastion forest'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: d6788af4-e9b5-47a9-926a-1847fa6380a3
document_version_independent_id: 71f420df-b89e-61b1-d32f-4b18e6de17af
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-choose-where-to-install-hgs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-choose-where-to-install-hgs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-choose-where-to-install-hgs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7c01134-b8f3-438c-822d-13471e513908
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/82fff6b2-939d-4e9a-8f9c-d1c41a59749b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 77eabcfc-bb30-d5f8-6257-5e471e18f1bf
---

# Choose whether to install HGS in its own new forest or in an existing bastion forest | Microsoft Learn

The Active Directory forest for HGS is sensitive because its administrators have access to the keys that control shielded VMs. The default installation will set up a new forest dedicated for HGS and configure other dependencies. This option is recommended because the environment is self-contained and known to be secure when it is created.

The only technical requirement for installing HGS in an existing forest is that it be added to the root domain; non-root domains are not supported. But there are also operational requirements and security-related best practices for using an existing forest. Suitable forests are purposely built to serve one sensitive function, such as the forest used by [Privileged Access Management for AD DS](/en-us/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) or an [Enhanced Security Administrative Environment (ESAE) forest](/en-us/security/compass/privileged-access-access-model#esae-administrative-forest-design-approach). Such forests usually exhibit the following characteristics:

- They have few admins (separate from fabric admins)
- They have a low number of logons
- They are not general-purpose in nature

General purpose forests such as production forests are not suitable for use by HGS. Fabric forests are also unsuitable because HGS needs to be isolated from fabric administrators.