---
layout: Conceptual
title: Deploy Claims Across Forests | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/deploy-claims-across-forests
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Deploy Claims Across Forests'
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: af91af2b-df48-64dd-e5db-58d364fc3c6e
document_version_independent_id: 6d97c82c-bfcb-09a4-9e06-75f62086f378
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Deploy-Claims-Across-Forests.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/deploy-claims-across-forests
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Deploy-Claims-Across-Forests.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 819fc4cb-2c97-45bd-f5ac-89516dbcb974
---

# Deploy Claims Across Forests | Microsoft Learn

In Windows Server 2012 , a claim type is an assertion about the object with which it's associated. Claim types are defined per forest in Active Directory. There are many scenarios where a security principal may need to traverse a trust boundary to access resources in a trusted forest. Cross-forest claims transformation in Windows Server 2012 enables you to transform egress and ingress claims that traverse forests so that the claims are recognized and accepted in the trusting and trusted forests. Some of the real-world scenarios for transformation of claims are:

- Trusting forests can use claim transformation as a guard against elevation of privilege by filtering the incoming claims with specific values.

    Trusting forests can also issue claims for principals coming over a trust boundary if the trusted forest does not support or issue any claims.
- Trusted forests can use claim transformation to prevent certain claim types and claims with certain values from going out to the trusting forest.
- You can also use claim transformation to map different claim types between trusting and trusted forests. This can be used to generalize the claim-type, the claim value, or both. Without this, you need to standardize the data between the forests before you can use the claims. Generalizing claims between the trusting and trusted forests reduces the IT costs.

## Claim transformation rules

The transformation rule language syntax divides a single rule into two main parts: a series of condition statements and the issue statement. Each condition statement has two subcomponents: the claim identifier and the condition. The issue statement contains keywords, delimiters, and an issue expression. The condition statement optionally begins with a claim identifier variable, which represents the matched input claim. The condition checks for the expression. If the input claim does not match the condition, then the transformation engine ignores the issue statement and evaluates the next input claim against the transformation rule. If all conditions match the input claim, it processes the issue statement.

For detailed information on claim rules language, see [Claims Transformation Rules Language](claims-transformation-rules-language).

## Linking claim transformation policies to forests

There are two components involved in setting up claim transformation policies: claim transformation policy objects and the transformation link. The policy objects live in the configuration naming context in a forest, and they contain mapping information for the claims. The link specifies which trusting and trusted forests the mapping applies to.

It is important to understand if the forest is the trusting or trusted forest because this is basis for linking transformation policy objects. For example, the trusted forest is the forest that contains user accounts that require access. The trusting forest is the forest that contains resources that you want to give users access to. Claims travel in the same direction as the security principal that requires access. For example, if there is a one-way trust from the contoso.com forest to the adatum.com forest, the claims will flow from adatum.com to contoso.com, which allows users from adatum.com to access resources in contoso.com.

By default, a trusted forest allows all outgoing claims to pass, and a trusting forest drops all incoming claims that it receives.

## In this scenario

The following guidance is available for this scenario:

- [Deploy Claims Across Forests (Demonstration Steps)](deploy-claims-across-forests--demonstration-steps-)
- [Claims Transformation Rules Language](claims-transformation-rules-language)

## Roles and features included in this scenario

The following table lists the roles and features that are part of this scenario and describes how they support it.

| Role/feature | How it supports this scenario |
| --- | --- |
| Active Directory Domain Services | In this scenario, you are required to set up two Active Directory forests with a two-way trust. You have claims in both forests. You also set central access policies on the trusting forest where the resources reside. |
| File and Storage Services role | In this scenario, the data classification is applied to the resources on the file servers. The central access policy is applied to the folder where you want to grant user access. After transformation, the claim grants user access to resources based on the central access policy that is applied to the folder on the file server. |