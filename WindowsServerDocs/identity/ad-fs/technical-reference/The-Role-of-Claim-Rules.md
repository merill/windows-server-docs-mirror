---
layout: Conceptual
title: The Role of Claim Rules | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/technical-reference/the-role-of-claim-rules
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: The Role of Claim Rules'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: aad31160-1daa-169e-d87c-b5ad9fe87694
document_version_independent_id: bb49ffa6-7372-1539-d8b4-a8110d0429d9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/technical-reference/The-Role-of-Claim-Rules.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/technical-reference/the-role-of-claim-rules
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/technical-reference/The-Role-of-Claim-Rules.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
platformId: f5d4bab8-1131-9e51-af4c-75512aad3715
---

# The Role of Claim Rules | Microsoft Learn

The overall function of the Federation Service in Active Directory Federation Services (AD FS) is to issue a token that contains a set of claims. The decision regarding what claims AD FS accepts and then issues is governed by claim rules.

## What are claim rules?

A claim rule represents an instance of business logic that will take one or more incoming claims, apply conditions to them (if x then y) and produce one or more outgoing claims based on the condition parameters. For more information about incoming and outgoing claims, see [The Role of Claims](the-role-of-claims).

You use claim rules when you need to implement business logic that will control the flow of claims through the claims pipeline. While the claims pipeline is more a logical concept of the end-to-end process for flowing claims, claim rules are an actual administrative element that you can use to customize the flow of claims through the claims issuance process.

For more information about the claims pipeline, see [The Role of the Claims Engine](the-role-of-the-claims-engine).

Claim rules provide the following benefits:

- Provide a mechanism for administrators to apply run-time business logic for trusting claims from claims providers
- Provide a mechanism for administrators to define what claims are released to relying parties
- Provide rich and detailed claims-based authorization capabilities to administrators who want to permit or deny access to specific users

### How claim rules are processed

Claim rules are processed through the claims pipeline using the *claims engine*. The claims engine is a logical component of the Federation Service that examines the set of incoming claims presented by a user, and will then, depending on the logic in each rule, produce an output set of claims.

Together, the claims rule engine and the set of claim rules associated with a given federated trust determine whether incoming claims should be passed through as they are, filtered to meet a specific condition's criteria or transformed into an entirely new set of claims before they are issued as outgoing claims by your Federation Service.

For more information about this process, see [The Role of the Claims Engine](the-role-of-the-claims-engine).

## What are claim rule templates?

AD FS includes a predefined set of claim rule templates that are designed to help you easily select and create the most appropriate claim rules for your particular business need. Claim rule templates are only used during the claim rule creation process.

In the AD FS Management snap-in, rules can only be created using claim rule templates. After you use the snap-in to select a claim rule template, input the necessary data for the rule logic and save it to the configuration database, it will be (from that point forward) referred to in the UI as a claim rule.

### How claim rule templates work

At first glance, claim rule templates appear to be just input forms provided by the snap-in to collect data and process specific logic on incoming claims. However, at a much more detailed level, claim rule templates store the necessary claim rule language framework that make up the base logic necessary for you to quickly create a rule without needing to know the language intimately.

Each template that is provided in the user interface (UI) represents a prepopulated claim rule language syntax, based on the most commonly required administrative tasks. There is one rule template however, that is the exception. This template is referred to as the custom rule template. With this template, no syntax is prepopulated. Instead you must directly author the claim rule language syntax in the body of the claim rule template form using the claim rule language syntax.

For more information about how to use the claim rule language syntax, see [The Role of the Claim Rule Language](the-role-of-the-claim-rule-language) in the AD FS Deployment Guide.

Tip

You can view the claim rule language associated with a rule at any time by clicking the **View Rule Language** button on the properties of a claim rule.

### How to create a claim rule

Claim rules are created separately for each federated trust relationship within the Federation Service and are not shared across multiple trusts. You can either create a rule from a claim rule template, start from scratch by authoring the rule using the claim rule language or use Windows PowerShell to customize a rule.

All of these options coexist to provide you with the flexibility of choosing the appropriate method for a given scenario. For more information about how to create a claim rule, see [Configuring Claim Rules](../deployment/configuring-claim-rules) in the AD FSDeployment Guide.

#### Using claim rule templates

Claim rule templates are only used during the claim rule creation process. You can use any of the following templates to create a claim rule:

- Pass Through or Filter an Incoming Claim
- Transform an Incoming Claim
- Send LDAP Attributes as Claims
- Send Group Membership as a Claim
- Send Claims Using a Custom Rule
- Permit or Deny Users Based on an Incoming Claim
- Permit All Users

For more information describing each of these claim rule templates, see [Determine the Type of Claim Rule Template to Use](determine-the-type-of-claim-rule-template-to-use).

#### Using the claim rule language

For business rules that are beyond the scope of standard claim rule templates, you can use a custom rule template to express a series of complex logic conditions using the claim rule language. For more information about using a custom rule, see [When to Use a Custom Claim Rule](when-to-use-a-custom-claim-rule).

#### Using Windows PowerShell

You can also use the ADFSClaimRuleSet cmdlet object with Windows PowerShell to create or administer rules in AD FS. For more information about how you can use Windows PowerShell with this cmdlet, see [AD FS Administration with Windows PowerShell](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee126138%28v=ws.10%29).

## What is a claim rule set?

As shown in the following illustration, a claim rule set is a grouping of one or more rules for a given federated trust that will define how claims will be processed by the claims rule engine. When an incoming claim is received by the Federation Service the claim rule engine applies the logic specified by the appropriate claim rule set. It is the final sum of the logic from each rule in the set that will determine how claims will be issued for a given trust in its entirety.

![AD FS roles](media/adfs2_claimruleset.gif)

Claim rules are processed by the claims engine in chronological order within a given rule set. This order is important, because the output of one rule can be used as the input to the next rule in the set.

## What are claim rule set types?

A claim rule set type is a logical segment of a federated trust that categorically identifies whether the claim rule set associated with the trust will be used for claims issuance, authorization or acceptance. Each federated trust can have one or more claim rule set types associated with it, depending on the type of trust that is used.

The following table describes the various types of claim rule sets and explains its relation with either a claims provider trust or relying party trust.

| Claim rule set type | Description | Used on |
| --- | --- | --- |
| Acceptance transform rule set | A set of claim rules that you use on a particular claims provider trust to specify the incoming claims that will be accepted from the claims provider organization and the outgoing claims that will be sent to the relying party trust.<br>The incoming claims that will be used to source this rule set, will be the claims that are output by the issuance transform rule set as specified in the claims provider organization.<br><br>By default, the claims provider trust node contains a claim provider trust named **Active Directory** which is used to represent the source attribute store for the acceptance transform rule set. This trust object is used to represent the connection from your Federation Service to an Active Directory database on your network. This default trust is what processes claims for users that have been authenticated by Active Directory and it cannot be deleted. | Claims provider trusts |
| Issuance Transform Rule Set | A set of claim rules that you use on a relying party trust to specify the claims that will be issued to the relying party.<br>The incoming claims that will be used to source this rule set, will initially be the claims that are output by the acceptance transform rules. | Relying party trusts |
| Issuance Authorization Rule Set | A set of claim rules that you use on a relying party trust to specify the users that will be permitted to receive a token for the relying party.<br>These rules determine whether a user can receive claims for a relying party and, therefore, access to the relying party.<br><br>Unless you specify an issuance authorization rule, all users will be denied access by default. | Relying party trusts |
| Delegation Authorization Rule Set | A set of claim rules that you use on a relying party trust to specify the users that will be permitted to act as delegates for other users to the relying party.<br>These rules determine whether the requester is permitted to impersonate a user while still identifying the requester in the token that is sent to the relying party.<br><br>Unless you specify a delegation authorization rule, no users can act as delegates by default. | Relying party trusts |
| Impersonation Authorization Rule Set | A set of claim rules that you configure using Windows PowerShell to determine whether a user can fully impersonate another user to the relying party.<br>These rules determine whether the requester is permitted to impersonate a user without identifying the requester in the token that is sent to the relying party.<br><br>Impersonating another user in this way is a very powerful capability, because the relying party will not know that the user is being impersonated. | Relying party trust |

For more information about select the appropriate claim rules to use in your organization, see [Determine the Type of Claim Rule Template to Use](determine-the-type-of-claim-rule-template-to-use).