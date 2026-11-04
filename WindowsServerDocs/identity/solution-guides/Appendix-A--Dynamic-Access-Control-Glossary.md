---
layout: Conceptual
title: Appendix A Dynamic Access Control Glossary | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/appendix-a--dynamic-access-control-glossary
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Appendix A: Dynamic Access Control Glossary'
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: glossary
locale: en-us
document_id: 8096bae6-5e21-6cfa-6e8e-ad8b1863390b
document_version_independent_id: b03237e1-4cb1-2dee-3925-16b18b075c4b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Appendix-A--Dynamic-Access-Control-Glossary.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/appendix-a--dynamic-access-control-glossary
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Appendix-A--Dynamic-Access-Control-Glossary.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 28eda4d5-94a5-31a9-a33b-a726f7e4a622
---

# Appendix A Dynamic Access Control Glossary | Microsoft Learn

Following are the list of terms and definitions that are included in the Dynamic Access Control scenario.

| Term | Definition |
| --- | --- |
| Automatic classification | Classification that occurs based on classification properties that are determined by classification rules configured by an administrator. |
| CAPID | Central access policy ID. This ID references a specific central access policy, and it is used to reference the policy from the security descriptor of files and folders. |
| Central access rule | A rule that includes a condition and an access expression. |
| Central access policy | Policies that are authored and hosted in Active Directory. |
| Claims-based access control | A paradigm that utilizes claims to make access control decisions to resources. |
| Classification | The process of determining the classification properties of resources and assigning these properties to the metadata that is associated with the resources. See also REF AutomaticClassification \h \\* MERGEFORMAT Automatic classification, REF InheritedClassification \h \\* MERGEFORMAT Inherited classification, and REF ManualClassification \h \\* MERGEFORMAT Manual classification. |
| Device claim | A claim that is associated with the system. With user claims, it is included in the token of a user attempting to access a resource. |
| Discretionary access control list (DACL) | An access control list that identifies trustees who are allowed or denied access to a securable resource. It can be modified at the discretion of the resource owner. |
| Resource property | Properties (such as labels) that describe a file and are assigned to files by using automatic classification or manual classification. Examples include: Sensitivity, Project, and Retention period. |
| File Server Resource Manager | A feature in the Windows Server operating system that offers management of folder quotas, file screening, storage reports, file classification, and file management jobs on a file server. |
| Folder properties and labels | Properties and labels that describe a folder and are assigned manually by administrators and folder owners. These properties assign default property values to the files within these folders, for example, Secrecy or Department. |
| Group Policy | A set of rules and policies that controls the working environment of users and computers in an Active Directory environment. |
| Near real time classification | Automatic classification that is performed shortly after a file is created or modified. |
| Near real-time file management tasks | File management tasks that are performed shortly after (a file is created or modified. These tasks are triggered by the Near real-time classification. |
| Organizational Unit (OU) | An Active Directory container that represents hierarchical, logical structures within an organization. It is the smallest scope to which Group Policy settings are applied. |
| Secure property | A classification property that the authorization runtime can trust to be a valid assertion about the resource at a certain point-in-time. In claims-based access control, a secure property that is assigned to a resource is treated as a resource claim. |
| Security descriptor | A data structure that contains security information associated with a securable resource, such as access control lists. |
| Security descriptor definition language | A specification that describes the information in a security descriptor as a text string. |
| Staging policy | A central access policy that is not yet in effect. |
| System access control list (SACL) | An access control list that specifies the types of access attempts by particular trustees for which audit records need to be generated. |
| User claim | Attributes of a user that are provided within the user security token. Examples include: Department, Company, Project, and Security clearance. Information in the user token from systems prior to Windows Server 2012 , such as the security groups that the user is part of, can also be considered user claims. Some user claims are provided through Active Directory and others are calculated dynamically, such as whether the user logged in with a smart card. |
| User token | A data object that identifies a user and the user claims and device claims that are associated with that user. It is used to authorize the user's access to resources. |