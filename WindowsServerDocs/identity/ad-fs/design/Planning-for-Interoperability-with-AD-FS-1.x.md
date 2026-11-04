---
layout: Conceptual
title: Planning for Interoperability with AD FS 1.x | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-for-interoperability-with-ad-fs-1.x
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Planning for Interoperability with AD FS 1.x'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 45eeb7fa-bb88-e86a-b355-b1e898770277
document_version_independent_id: 2ed15765-0c62-d8be-b5f2-ebf23115c1d0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Planning-for-Interoperability-with-AD-FS-1.x.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/planning-for-interoperability-with-ad-fs-1.x
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Planning-for-Interoperability-with-AD-FS-1.x.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6c57776-ab71-4356-880c-c5ff411d7fe1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/e2d3fbf8-36df-4730-9ac5-e1c53887f039
platformId: 49f4b273-f0fe-d8df-5a64-f5db1824fdae
---

# Planning for Interoperability with AD FS 1.x | Microsoft Learn

Active Directory Federation Services (AD FS) federation servers running Windows Server® 2012 can interoperate with both an AD FS 1.0 (installed with Windows Server 2003 R2) Federation Service and an AD FS 1.1 (installed with Windows Server 2008 or Windows Server 2008 R2) Federation Service. Any of the following interoperability combinations are supported:

- Any AD FS 1.*x* Federation Service can send a claim that can be consumed by an AD FS Federation Service in Windows Server 2012 . For more information, see [Checklist: Configuring AD FS to Consume Claims from AD FS 1.x](../deployment/checklist--configuring-ad-fs--to-consume-claims-from-ad-fs-1.x).
- Any AD FS Federation Service in Windows Server 2012 can send an AD FS 1.*x*-compatible claim that can be consumed by an AD FS 1.*x* Federation Service. For more information, see [Checklist: Configuring AD FS to Send Claims to an AD FS 1.x Federation Service](../deployment/checklist--configuring-ad-fs-to-send-claims-to-an-ad-fs-1.x-federation-service).
- Any AD FS Federation Service in Windows Server 2012 can send an AD FS 1.*x*-compatible claim that can be consumed by one or more Web servers running the AD FS 1.*x* claims-aware Web agent. For more information, see [Checklist: Configuring AD FS to Send Claims to an AD FS 1.x Claims-Aware Web Agent](../deployment/checklist--configuring-ad-fs-to-send-claims-to-an-ad-fs-1.x-claims-aware-web-agent).

Note

AD FS does not support or interoperate with the AD FS 1.*x* Windows NT token–based Web agent.

An AD FS 1.*x*-compatible claim is a claim that can be sent by an AD FS Federation Service in Windows Server 2012 and understood by an AD FS 1.*x* Federation Service. So that an AD FS 1.*x* Federation Service can consume the claims that an AD FS Federation Service sends, a Name Identifier (ID) claim type must be sent.

## Understanding the Name ID claim type

The Name ID claim type is the equivalent of the identity claim type that AD FS 1.*x* uses. It must be used whenever you want to interoperate with AD FS 1.*x*. The Name ID claim type enables either an AD FS 1.*x* Federation Service or the AD FS 1.*x* claims-aware Web agent to consume claims that AD FS in Windows Server 2012 sends, as long as these claims are sent in one of the Name ID formats in the following table.

| Name ID format | Corresponding URI |
| --- | --- |
| AD FS 1.*x* Email Address | `http://schemas.xmlsoap.org/claims/EmailAddress` |
| AD FS 1.*x* Email UPN | `http://schemas.xmlsoap.org/claims/UPN` |
| Common Name | `http://schemas.xmlsoap.org/claims/CommonName` |
| Group | `http://schemas.xmlsoap.org/claims/Group` |

Only one Name ID claim in the appropriate format must be sent. When that criterion is satisfied, many other claims may be sent as well, assuming that they conform to the restrictions described in the table.

Note

An AD FS 1.*x* Federation Service can interpret only incoming claim types that begin with the Uniform Resource Identifier (URI) of `http://schemas.xmlsoap.org/claims/`.