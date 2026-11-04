---
layout: Conceptual
title: The Role of the Claims Pipeline | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/technical-reference/the-role-of-the-claims-pipeline
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: The Role of the Claims Pipeline'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: b29b34e4-9db4-991d-4549-d7abd055b0d4
document_version_independent_id: ec24f28d-d8ce-52ef-6308-aab873e22ee0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/technical-reference/The-Role-of-the-Claims-Pipeline.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/technical-reference/the-role-of-the-claims-pipeline
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/technical-reference/The-Role-of-the-Claims-Pipeline.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 49c3838e-1ba3-a9a2-3a4e-f7aa674dc035
---

# The Role of the Claims Pipeline | Microsoft Learn

The claims pipeline in Active Directory Federation Services (AD FS) represents the path that claims must follow through the Federation Service before they can be issued. The Federation Service manages the entire end-to-end process of flowing claims through the various stages of the claims pipeline, which also includes the processing of claim rules by the claim rule engine.

For more information about claim rules, see [The Role of Claim Rules](the-role-of-claim-rules). For more information about how the claim rule engine processes rules, see [The Role of the Claims Engine](the-role-of-the-claims-engine).

The following section discusses the process that the Federation Service oversees in greater detail.

## Claims pipeline process

The claims pipeline process consists of three high-level stages. Each stage in this process initializes the claim rule engine to process claim rules that are specific to that stage. These stages include (in the order that they occur):

1. Accepting incoming claims—This stage in the claims pipeline is used to extract the incoming claims from the token and eliminate claims that are not expected or trusted. After they are extracted, the acceptance rules that make up the acceptance transform rule set for a claims provider trust are run. These rules can be used to pass through or add new claims that can then be used in the subsequent stages of the claims pipeline. The output of this stage is used as an input to second and third stage.
2. Authorizing the claims requester—This stage is used by the claims engine to issue permit or deny claims based on whether the token requester is allowed to obtain a token for the given relying party or not. However, before this can occur the authorization rules that make up either the issuance authorization rule set or the delegation authorization rule set for a relying party trust are ran.
3. Issuing outgoing claims—This stage is used to issue outgoing claims and send them along the pipeline where they will be packaged into a security token. However, before this can occur the issuance rules that make up the issuance transform rule set for a relying party trust are ran, which will determine what claims will be issued as outgoing claims.

All three stages above perform claims rules processing but use a different set of rules. As described above, each stage has an associated set of rules based on either the issuer of the incoming claims (the acceptance rules) or the target service for which the claimincludes are being issued (authorization and issuance rules).

Claims are token-agnostic but are transmitted over the network encapsulated in security tokens. The claim rules operate over claims regardless of the format of the incoming or outgoing security token.

Claims rules contain the administrator-defined logic by which the claims engine will accept the incoming claims, authorize claims based on the requester's identity and issue claims that are needed by a relying party. Ultimately, it is the claims engine that determines what claims will go into the security token that will be issued after the claim has been flowed through the claims pipeline.

As shown in the following illustration, the claims pipeline is responsible for the entire end-to-end process of flowing a claim through the various pipeline stages in order to end up with an issued claim that will be sent over a relying party trust. The outgoing claim in the illustration represents the issued claim.

![AD FS roles](media/adfs2_pipeline.gif)

Although it is not shown in the illustration, it is the claims engine that performs the actual processing of the rules at each stage. For more information, see [The Role of the Claims Engine](the-role-of-the-claims-engine).