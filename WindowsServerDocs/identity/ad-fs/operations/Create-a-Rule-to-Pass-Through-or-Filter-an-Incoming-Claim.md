---
layout: Conceptual
title: Create a Rule to Pass Through or Filter an Incoming Claim | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/create-a-rule-to-pass-through-or-filter-an-incoming-claim
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Create a Rule to Pass Through or Filter an Incoming Claim'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 850122ae-52d5-7f26-8360-579b700bc8aa
document_version_independent_id: 7ef7757a-44c6-ca56-4ee2-9d92b2eb3cc0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/create-a-rule-to-pass-through-or-filter-an-incoming-claim
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 77948bbe-31d4-0e6b-9d6f-468453855bed
---

# Create a Rule to Pass Through or Filter an Incoming Claim | Microsoft Learn

Using the Pass Through or Filter an Incoming Claim rule template in Active Directory Federation Services (AD FS), you can pass through all incoming claims with a selected claim type. You can also filter the values of incoming claims with a selected claim type. For example, you can use this rule template to create a rule that will send all incoming group claims. You can also use this rule to send only user principal name (UPN) claims that end with @fabrikam.

You can use the following procedure to create a claim rule with the AD FS Management snap-in.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

## To create a rule to pass through or filter an incoming claim on a Relying Party Trust in Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Relying Party Trusts**. ![Screenshot that highlights Relying Party Trusts in the console tree.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule9.png)
3. Right-click the selected trust, and then click **Edit Claim Issuance Policy**. ![Screenshot that highlights the Edit Claim Issuance Policy menu option.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule10.png)
4. In the **Edit Claim Issuance Policy** dialog box, under **Issuance Transform Rules** click **Add Rule** to start the rule wizard. ![Screenshot that shows the Issuance Transform Rules tab.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule11.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Pass Through or Filter an Incoming Claim** from the list, and then click **Next**. ![Screenshot that shows where to select the Pass Through or Filter an Incoming Claim template.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule4.png)
6. On the **Configure Rule** page under **Claim rule name** type the display name for this rule, in **Incoming claim type** select a claim type in the list, and then select one of the following options, depending on the needs of your organization:

    - **Pass through all claim values**
    - **Pass through only a specific claim value**
    - **Pass through only claim values that match a specific email suffix value**
    - **Pass through only claim values that start with a specific value**![Screenshot that shows where to select the incoming claim type.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule5.png)
7. Click the **Finish** button.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## To create a rule to pass through or filter an incoming claim on a Claims Provider Trust in Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Claims Provider Trusts**. ![Screenshot that highlights Claims Provider Trusts in the console tree.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule1.png)
3. Right-click the selected trust, and then click **Edit Claim Rules**. ![Screenshot that highlights the Edit Claim Rules menu option.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule2.png)
4. In the **Edit Claim Rules** dialog box, under **Acceptance Transform Rules** click **Add Rule** to start the rule wizard. ![Screenshot that shows the Acceptance Transform Rules tab.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule3.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Pass Through or Filter an Incoming Claim** from the list, and then click **Next**. ![Screenshot that shows where to select a rule template.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule4.png)
6. On the **Configure Rule** page under **Claim rule name** type the display name for this rule, in **Incoming claim type** select a claim type in the list, and then select one of the following options, depending on the needs of your organization:

    - **Pass through all claim values**
    - **Pass through only a specific claim value**
    - **Pass through only claim values that match a specific email suffix value**
    - **Pass through only claim values that start with a specific value**![Screenshot that shows where to ad the claim rule name.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule5.png)
7. Click the **Finish** button.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## To create a rule to pass through or filter an incoming claim in Windows Server 2012 R2

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FSAD FS\Trust Relationships**, click either **Claims Provider Trusts** or **Relying Party Trusts**, and then click a specific trust in the list where you want to create this rule.
3. Right-click the selected trust, and then click **Edit Claim Rules**. ![Screenshot that shows where to select Edit Claim Rules.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule6.png)
4. In the **Edit Claim Rules** dialog box, select one the following tabs, depending on the trust you are editing and which rule set you want to create this rule in, and then click **Add Rule** to start the rule wizard that is associated with that rule set:

    - **Acceptance Transform Rules**
    - **Issuance Transform Rules**
    - **Issuance Authorization Rules**
    - **Delegation Authorization Rules**![Screenshot thats shows the Add Rule button.](media/create-a-rule-to-permit-all-users/permitall5.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Pass Through or Filter an Incoming Claim** from the list, and then click **Next**. ![Screenshot that shows the the Choose Rule Type screen.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule7.png)
6. On the **Configure Rule** page under **Claim rule name** type the display name for this rule, in **Incoming claim type** select a claim type in the list, and then select one of the following options, depending on the needs of your organization:

    - **Pass through all claim values**
    - **Pass through only a specific claim value**
    - **Pass through only claim values that match a specific email suffix value**
    - **Pass through only claim values that start with a specific value**![create rule](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule8.png)
7. Click the **Finish** button.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## Additional references

[Configure Claim Rules](configure-claim-rules)

[When to Use a Pass Through or Filter Claim Rule](../technical-reference/when-to-use-a-pass-through-or-filter-claim-rule)

[The Role of Claims](../technical-reference/the-role-of-claims)

[The Role of Claim Rules](../technical-reference/the-role-of-claim-rules)