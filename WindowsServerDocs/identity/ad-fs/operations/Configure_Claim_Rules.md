---
layout: Conceptual
title: Configure Claims Rules in AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure_claim_rules
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure Claim Rules'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 464c6836-1f4b-2bf7-ad2b-c590e3254677
document_version_independent_id: 7095eddc-809a-f341-0b85-2526107ccb60
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Configure_Claim_Rules.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/configure_claim_rules
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Configure_Claim_Rules.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 5af7525d-aa5b-be80-9200-87b07b4a01fd
---

# Configure Claims Rules in AD FS | Microsoft Learn

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
- [Create a Rule to Send Claims Using a Custom Rule](create-a-rule-to-send-claims-using-a-custom-rule)