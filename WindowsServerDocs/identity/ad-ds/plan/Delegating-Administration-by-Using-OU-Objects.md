---
layout: Conceptual
title: Delegating Administration by Using OU Objects | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/delegating-administration-by-using-ou-objects
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Delegating Administration by Using OU Objects'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: c5fd9a39-164e-2862-ab5d-4a5f051914d9
document_version_independent_id: 0b1d47d1-b231-c07f-0e8a-f347c44bd28c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Delegating-Administration-by-Using-OU-Objects.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/delegating-administration-by-using-ou-objects
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Delegating-Administration-by-Using-OU-Objects.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: dc7bbf37-6733-4469-40bd-4e917ae6e5d3
---

# Delegating Administration by Using OU Objects | Microsoft Learn

You can use organizational units (OUs) to delegate the administration of objects, such as users or computers, within the OU to a designated individual or group. To delegate administration by using an OU, place the individual or group to which you are delegating administrative rights into a group, place the set of objects to be controlled into an OU, and then delegate administrative tasks for the OU to that group.

Active Directory Domain Services (AD DS) enables you to control the administrative tasks that can be delegated at a very detailed level. For example, you can assign one group to have full control of all objects in an OU; assign another group the rights only to create, delete, and manage user accounts in the OU; and then assign a third group the right only to reset user account passwords. You can make these permissions inheritable so that they apply to any OUs that are placed in subtrees of the original OU.

Default OUs and containers are created during the installation of AD DS and are controlled by service administrators. It is best if service administrators continue to control these containers. If you need to delegate control over objects in the directory, create additional OUs and place the objects in these OUs. Delegate control over these OUs to the appropriate data administrators. This makes it possible to delegate control over objects in the directory without changing the default control given to the service administrators.

The forest owner determines the level of authority that is delegated to an OU owner. This can range from the ability to create and manipulate objects within the OU to only being allowed to control a single attribute of a single type of object in the OU. Granting a user the ability to create an object in the OU implicitly grants that user the ability to manipulate any attribute of any object that the user creates. In addition, if the object that is created is a container, the user implicitly has the ability to create and manipulate any objects that are placed in the container.