---
layout: Conceptual
title: Checklist - Creating Claim Rules for a Claims Provider Trust | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/checklist--creating-claim-rules-for-a-claims-provider-trust
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Checklist: Creating Claim Rules for a Claims Provider Trust'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: 6c8c5d66-9135-9cb5-dfdf-0a65a6c6953b
document_version_independent_id: 45b90f8e-aee0-a3f1-66c3-467060a0dd42
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Checklist--Creating-Claim-Rules-for-a-Claims-Provider-Trust.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/checklist--creating-claim-rules-for-a-claims-provider-trust
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Checklist--Creating-Claim-Rules-for-a-Claims-Provider-Trust.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 215735d0-6d0c-b000-2b6f-b2feec006f57
---

# Checklist - Creating Claim Rules for a Claims Provider Trust | Microsoft Learn

This checklist includes tasks for planning, designing, and deploying claim rules that are associated with a claims provider trust in Active Directory Federation Services (AD FS).

Note

Complete the tasks in this checklist in order. When a reference link takes you to a procedure, return to this topic after you complete the steps in that procedure so that you can proceed with the remaining tasks in this checklist.

![Icon for the Creating a claim rule set for a claims provider trust checklist.](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**Checklist: Creating a claim rule set for a claims provider trust**

| Task | Reference |
| --- | --- |
| Review concepts about claims, claim rules, claim rule sets, and claim rule templates and how they are associated with federated trusts. | ![Icon for the The Role of Claims link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Claims](../technical-reference/the-role-of-claims)<br>![Icon for the The Role of Claim Rules link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Claim Rules](../technical-reference/the-role-of-claim-rules) |
| Review concepts about how a claim flows through all the stages in the claims issuance pipeline and how rules are processed by the claims issuance engine. | ![Icon for the The Role of the Claims Pipeline link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claims Pipeline](../technical-reference/the-role-of-the-claims-pipeline)<br>![Icon for the The Role of the Claims Engine link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claims Engine](../technical-reference/the-role-of-the-claims-engine) |
| To effectively plan and implement the output claims that will be issued over this claims provider trust, determine whether one or more claim rules are needed and which claim rules you should use with this claims provider trust. | ![Icon for the Determine the Type of Claim Rule Template to Use link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Determine the Type of Claim Rule Template to Use](../technical-reference/determine-the-type-of-claim-rule-template-to-use) |
| Review concepts about when to create one claim rule over another and how you can use the claim rule language to provide more complex logic than standard rules in order to provide a desired result in the ideal output claim set. | ![Icon for the When to Use a Pass Through or Filter Claim Rule link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[When to Use a Pass Through or Filter Claim Rule](../technical-reference/when-to-use-a-pass-through-or-filter-claim-rule)<br>![Icon for the When to Use a Transform Claim Rule link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[When to Use a Transform Claim Rule](../technical-reference/when-to-use-a-transform-claim-rule)<br><br>![Icon for the When to Use a Send LDAP Attributes as Claims Rule link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[When to Use a Send LDAP Attributes as Claims Rule](../technical-reference/when-to-use-a-send-ldap-attributes-as-claims-rule)<br><br>![Icon for the When to Use a Send Group Membership as a Claim Rule link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[When to Use a Send Group Membership as a Claim Rule](../technical-reference/when-to-use-a-send-group-membership-as-a-claim-rule)<br><br>![Icon for the When to Use a Custom Claim Rule link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[When to Use a Custom Claim Rule](../technical-reference/when-to-use-a-custom-claim-rule)<br><br>![Icon for the The Role of the Claim Rule Language link.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claim Rule Language](../technical-reference/the-role-of-the-claim-rule-language) |
| A claim description must be created if one does not already exist that will fulfill the needs of your organization. AD FS ships with a default set of claim descriptions that are exposed in the AD FS Management snap-in. | ![Icon for the Add a Claim Description link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Add a Claim Description](../operations/add-a-claim-description) |
| Depending on the needs of your organization, create one or more claim rules for the acceptance transform rules set that is associated with this claims provider trust so that claims will be issued appropriately. | ![Icon for the Create a Rule to Pass Through or Filter an Incoming Claim link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Rule to Pass Through or Filter an Incoming Claim](../operations/create-a-rule-to-pass-through-or-filter-an-incoming-claim)<br>![Icon for the Create a Rule to Send LDAP Attributes as Claims link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Rule to Send LDAP Attributes as Claims](../operations/create-a-rule-to-send-ldap-attributes-as-claims)<br><br>![Icon for the Create a Rule to Send Group Membership as a Claim link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Rule to Send Group Membership as a Claim](../operations/create-a-rule-to-send-group-membership-as-a-claim)<br><br>![Icon for the Create a Rule to Transform an Incoming Claim link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Rule to Transform an Incoming Claim](../operations/create-a-rule-to-transform-an-incoming-claim)<br><br>![Icon for the Create a Rule to Send an Authentication Method Claim link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Rule to Send an Authentication Method Claim](../operations/create-a-rule-to-send-an-authentication-method-claim)<br><br>![Icon for the Create a Rule to Send an AD FS 1.x Compatible Claim link.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Rule to Send an AD FS 1.x Compatible Claim](../operations/create-a-rule-to-send-an-ad-fs-1x-compatible-claim)<br><br>![creating claim rules](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Create a Rule to Send Claims Using a Custom Rule](../operations/create-a-rule-to-send-claims-using-a-custom-rule) |