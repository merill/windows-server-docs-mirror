---
layout: Conceptual
title: Configure Claims Rules | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-claim-rules
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure Claim Rules in AD FS for Windows Server'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: e96ca077-885a-36d4-767b-22ef92eee65d
document_version_independent_id: 51160ab9-7ed1-aed2-cb54-d43b0e3b4cc9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Configure-Claim-Rules.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/configure-claim-rules
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Configure-Claim-Rules.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 79845942-953d-1c5f-1d29-53b37da296d6
---

# Configure Claims Rules | Microsoft Learn

In a claims-based identity model, the function of Active Directory Federation Services (AD FS) as federation services is to issue a token that contains a set of claims. Claims rules govern the decisions with regard to claims that AD FS issues. Claim rules and all server configuration data are stored in the AD FS configuration database.

AD FS makes issuance decisions that are based on identity information that is provided to it in the form of claims and other contextual information. At a high level, AD FS operates as a rules processor by taking one set of claims as input, performs a number of transformations, and then returns a different set of claims as output.

The following topics will assist you in creating the rules that AD FS will process:

- [Create a Rule to Pass Through or Filter an Incoming Claim](create-a-rule-to-pass-through-or-filter-an-incoming-claim)
- [Create a Rule to Permit All Users](create-a-rule-to-permit-all-users)
- [Create a Rule to Permit or Deny Users Based on an Incoming Claim](create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim)
- [Create a Rule to Send LDAP Attributes as Claims](create-a-rule-to-send-ldap-attributes-as-claims)
- [Create a Rule to Send Group Membership as a Claim](create-a-rule-to-send-group-membership-as-a-claim)
- [Create a Rule to Transform an Incoming Claim](create-a-rule-to-transform-an-incoming-claim)
- [Create a Rule to Send an Authentication Method Claim](create-a-rule-to-send-an-authentication-method-claim)
- [Create a Rule to Send an AD FS 1.x Compatible Claim](create-a-rule-to-send-an-ad-fs-1x-compatible-claim)
- [Create a Rule to Send Claims Using a Custom Rule](create-a-rule-to-send-claims-using-a-custom-rule)