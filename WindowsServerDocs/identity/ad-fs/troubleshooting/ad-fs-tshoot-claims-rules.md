---
layout: Conceptual
title: AD FS Troubleshooting - Claims Rules | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-claims-rules
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This article describes how to troubleshoot claims rule syntax with Active Directory Federation Services (AD FS).
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: troubleshooting-general
ms.custom: sfi-image-nochange
locale: en-us
document_id: c2f7b34d-aead-7d39-208b-9a32fe38e1dc
document_version_independent_id: 9a04307d-5e57-cfe4-993c-54231b242bd9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-claims-rules.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-claims-rules
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-claims-rules.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 96d87c08-87a1-e960-2338-8c657e48fd72
---

# AD FS Troubleshooting - Claims Rules | Microsoft Learn

A claim is a statement that one subject makes about itself or another subject. A relying party issues the claims. They're given one or more values and then packaged in security tokens that the Active Directory Federation Services (AD FS) server issues. This article deals with the claims syntax and creation. For information on claims issuance, see [Troubleshoot AD FS](ad-fs-tshoot-claims-issuance).

## How claim rules are processed

Claim rules are processed through the [claims pipeline](../technical-reference/the-role-of-the-claims-pipeline) by using the [claims engine](../technical-reference/the-role-of-the-claims-engine). The claims engine is a logical component of AD FS that examines the set of incoming claims presented by a user. Depending on the logic in each rule, it produces an output set of claims.

## How to create a claim rule

Claim rules are created separately for each federated trust relationship within AD FS. They aren't shared across multiple trusts. You can:

- Create a rule from a [claim rule template](../technical-reference/determine-the-type-of-claim-rule-template-to-use).
- Start from scratch by authoring the rule by using the [claim rule language](../technical-reference/when-to-use-a-custom-claim-rule).
- Use Windows PowerShell to customize a rule.

## Components of the claim rule language

The claim rule language consists of the following components, separated by the `" =>"` operator:

- A condition is used to check input claims and determine whether the issuance statement of the rule should be executed. It represents a logical expression that must be evaluated to true to run the rule body part.
- An issuance statement.

Here's an example:

```
c:[type == "Name", value == "domain user"] => issue(type = "Role", value = "employee");
```

This claim has:

- **Condition**: `c:[type == "Name", value == "domain user"]` evaluates the input claim of whether the Windows account name is a domain user.
- **Issuance**: `issue(type = "Role", value = "employee")` adds a new claim to the input claim with the role of employee, if the condition is true.

For more information on claims and the syntax, see [The role of the claim rule language](../technical-reference/the-role-of-the-claim-rule-language).

## Claims rule editor

The claims rule editor performs syntax checking after you finish the claim and select **OK**. If you have the incorrect syntax, the editor informs you.

![Screenshot that shows the A D F S Management dialog with a message stating that the custom claim rule syntax isn't valid.](media/ad-fs-tshoot-claims/claims1.png)

## Event logs

When you try to troubleshoot a claim by using the logs, the best approach is to look for claims output. Look for 1000 and 1001 events in the event log.

![Screenshot that shows the Event Properties dialog box with the results of a 1000 event I D.](media/ad-fs-tshoot-claims/claims2.png)

## Create a sample application

You can also create a sample application that echoes your claims. For example, you can use a sample application and create a relying party that has the same claim that you're trying to troubleshoot and see if the app has any issues with that claim.

![Screenshot that shows the sample application in a browser.](media/ad-fs-tshoot-claims/claim4.png)

A good sample web app is available. The app echoes the claims that it receives from the relying party. To use it, edit the web.config app:

- Change `https://app1.contoso.com/sampapp` to the URL that's used for hosting the sample app.
- Change all instances of `sts.contoso.com` to point to your AD FS server.
- Replace the thumbprint with your thumbprint.
- Replace the `decryptionKey` and the `validationKey` values with values that are appropriate for your scenario.

![Screenshot that shows the web config file in Visual Studio.](media/ad-fs-tshoot-claims/claims3.png)

[This blog article](/en-us/archive/blogs/tangent_thoughts/install-and-configure-a-simple-net-4-5-sample-federated-application-samapp) has excellent, in-depth instructions for setting up the app.