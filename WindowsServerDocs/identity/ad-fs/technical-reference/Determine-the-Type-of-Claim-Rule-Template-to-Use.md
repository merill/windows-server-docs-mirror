---
layout: Conceptual
title: Determine the Type of Claim Rule Template to Use | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/technical-reference/determine-the-type-of-claim-rule-template-to-use
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Determine the Type of Claim Rule Template to Use'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: a0884d94-4371-b655-6e27-2a2efd4f52d1
document_version_independent_id: e4926ec4-c942-17e7-c2d9-7d6809a16242
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/technical-reference/Determine-the-Type-of-Claim-Rule-Template-to-Use.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/technical-reference/determine-the-type-of-claim-rule-template-to-use
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/technical-reference/Determine-the-Type-of-Claim-Rule-Template-to-Use.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 94ddfd10-31a3-ca82-06ec-0787f15cdd15
---

# Determine the Type of Claim Rule Template to Use | Microsoft Learn

An important part of designing an Active Directory Federation Services (AD FS) infrastructure is determining the complete set of claim rules—and which corresponding claim rule templates you should use to create them—for each partner that will participate in federation with your organization. You create rules by using claim rule templates in the AD FS Management snap-in.

Each set of claim rules you configure can only be associated with one federated trust. This means that you cannot create a set of rules on one trust and use them for other trusts in your Federation Service. Instead you can easily create rules from claim rule templates to more quickly help produce a desired set of claims that are agreed upon between each federated partner and your organization.

For more information about rules and rule templates, see [The Role of Claim Rules](the-role-of-claim-rules).

Before you begin to determine the types of claim rule templates you should use, consider the following questions:

- What claims will be provided by your trusted claims providers?
- What claims do you trust from each claims provider?
- What claims are required by the relying parties that trust this Federation Service?
- What claims are you willing to divulge to each relying party?
- Which users should have access to each relying party?

Answering these questions will help you plan a solid claim rule design. It will also assist you in creating a smooth authorization and access control strategy and make your deployment team more efficient during the rollout.

In this next section you can learn about the type of rule templates to select for your environment based on your business needs.

## Claim rule template types

The following table describes all of the types of claim rule templates that you can use to create rules using the AD FS Management snap-in, and the benefits of using one template type over another.

| Rule template type | Description | Advantages | Disadvantages |
| --- | --- | --- | --- |
| Pass Through or Filter an Incoming Claim | Used to create a rule that will pass through all claim values for a selected claim type or filter claims based on the claim values so that only certain claim values for a selected claim type will pass through.<br>For more information, see [When to Use a Pass Through or Filter Claim Rule](when-to-use-a-pass-through-or-filter-claim-rule). | - Can be used to select particular claims to be accepted or issued unchanged | - Claim type and value cannot be changed |
| Transform an Incoming Claim | Used to create a rule that can select an incoming claim and map it to a different claim type or map its claim value to a new claim value.<br>For more information, see [When to Use a Transform Claim Rule](when-to-use-a-transform-claim-rule). | - Can be used to normalize claim types or values- Can replace an e-mail suffix of an incoming claim | - More complex string replacements require a custom rule |
| Send LDAP Attributes as Claims | Used to create a rule that will select attributes from an LDAP attribute store to send as claims to the relying party.<br>For more information, see [When to Use a Send LDAP Attributes as Claims Rule](when-to-use-a-send-ldap-attributes-as-claims-rule). | - Can source claims from any AD DS/AD LDS attribute store- Multiple claims can be issued using a single rule | - Performance – slow as a result of account lookup- Cannot use a custom LDAP filter for querying |
| Send Group Membership as a Claim | Used to create a rule that can send a specified claim type and value when a user is a member of an Active Directory security group. Only a single claim will be sent using this rule, based on the group that you select.<br>For more information, see [When to Use a Send Group Membership as a Claim Rule](when-to-use-a-send-group-membership-as-a-claim-rule). | - Fast performance for issuing group claims – no account lookup | - User must be a member of a local Active Directory group |
| Send Claims Using a Custom Rule | Used to create a custom rule that will provide more advanced options than a standard rule template. You write custom rules with the AD FS claim rule language.<br>For more information, see [When to Use a Custom Claim Rule](when-to-use-a-custom-claim-rule). | - Can be used to source claims from an SQL attribute store- Can be used to specify a custom LDAP filter- Can be used to issue a PPID- Can be used with a custom attribute store- Can be used to add claims only to the input claim set- Can be used to send claims based on more than one incoming claim | - More difficult to configure - Some ramp up time may be needed to initially gain knowledge of the claim rule language |
| Permit or Deny Users Based on an Incoming Claim | Used to create a rule that will permit or deny access by users to the relying party, based on the type and value of an incoming claim.<br>For more information, see [When to Use an Authorization Claim Rule](when-to-use-an-authorization-claim-rule). | - Simplifies the authorization process | - Requires that only one claim type and one claim value be specified- Does not support pattern matching for claim values |
| Permit All Users | Used to create a rule that will permit all users to access the relying party.<br>For more information, see [When to Use an Authorization Claim Rule](when-to-use-an-authorization-claim-rule). | - Simple to configure | - Less secure than using the Permit or Deny Users Based on an Incoming Claim template |