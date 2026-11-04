---
layout: Conceptual
title: Configuring Claim Rules | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/configuring-claim-rules
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configuring Claim Rules'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: e8cd1ba5-8da7-39ab-442f-7782ccebeb33
document_version_independent_id: 78305d18-93b1-9cf0-310b-0160eaf949e6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Configuring-Claim-Rules.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/configuring-claim-rules
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Configuring-Claim-Rules.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 5803955d-db5b-811d-d0b6-3fa47e8aa711
---

# Configuring Claim Rules | Microsoft Learn

In a claims-based identity model, the function of Active Directory Federation Services (AD FS) as federation services is to issue a token that contains a set of claims. Claims rules govern the decision in regard of claims that AD FS issues. Claim rules and all server configuration data are stored in the AD FS configuration database.

AD FS makes issuance decisions that are based on identity information that is provided to it in the form of claims and other contextual information. At a high level, AD FS operates as a rules processor by taking one set of claims as input, performs a number of transformations, and then returns a different set of claims as output.

- [Create a Rule to Pass Through or Filter an Incoming Claim](../operations/create-a-rule-to-pass-through-or-filter-an-incoming-claim)
- [Create a Rule to Permit All Users](../operations/create-a-rule-to-permit-all-users)
- [Create a Rule to Send an AD FS 1.x Compatible Claim](../operations/create-a-rule-to-send-an-ad-fs-1x-compatible-claim)
- [Create a Rule to Permit or Deny Users Based on an Incoming Claim](../operations/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim)
- [Create a Rule to Send LDAP Attributes as Claims](../operations/create-a-rule-to-send-ldap-attributes-as-claims)
- [Create a Rule to Send Group Membership as a Claim](../operations/create-a-rule-to-send-group-membership-as-a-claim)
- [Create a Rule to Transform an Incoming Claim](../operations/create-a-rule-to-transform-an-incoming-claim)
- [Create a Rule to Send an Authentication Method Claim](../operations/create-a-rule-to-send-an-authentication-method-claim)
- [Create a Rule to Send Claims Using a Custom Rule](../operations/create-a-rule-to-send-claims-using-a-custom-rule)

## Additional references

[AD FS Operations](../ad-fs-operations)