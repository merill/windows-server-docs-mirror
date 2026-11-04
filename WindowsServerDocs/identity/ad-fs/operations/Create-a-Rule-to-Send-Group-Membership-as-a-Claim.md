---
layout: Conceptual
title: Create a Rule to Send Group Membership as a Claim | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/create-a-rule-to-send-group-membership-as-a-claim
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Create a Rule to Send Group Membership as a Claim'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b2db6276-d90b-8680-4fce-6e2ac0ee275b
document_version_independent_id: 5377acf2-9f0f-25ce-2425-2b4ff25bcd65
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/create-a-rule-to-send-group-membership-as-a-claim
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d4500e36-326b-7d2c-1c7b-daf946f75745
---

# Create a Rule to Send Group Membership as a Claim | Microsoft Learn

Using the Send Group Membership as a Claim rule template in Active Directory Federation Services (AD FS), you can create a rule that will make it possible for you to select an Active Directory security group to send as a claim. Only a single claim will be emitted from this rule, based on the group that you select. For example, you can use this rule template to create a rule that will send a group claim with a value of Admin if the user is a member of the Domain Admins security group. This rule should be used only for users in the local Active Directory domain.

You can use the following procedure to create a claim rule with the AD FS Management snap-in.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

## To create a rule to send group membership as a claim on a Relying Party Trust in Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Relying Party Trusts**. ![Screenshot that shows where to select Relying Party Trusts when you create a rule to send group membership as a claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule9.png)
3. Right-click the selected trust, and then click **Edit Claim Issuance Policy**. ![Screenshot that shows where to select Edit Claim Issuance Policy when you create a rule to send group membership as a claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule10.png)
4. In the **Edit Claim Issuance Policy** dialog box, under **Issuance Transform Rules** click **Add Rule** to start the rule wizard. ![Screenshot that shows where to select Add Rule when you create a rule to send group membership as a claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule11.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Send Group Membership as Claim** from the list, and then click **Next**. ![Screenshot that shows where to select the Send Group Membership as Claim template when you create a rule to send group membership as a claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-send-group-membership-as-a-claim/group3.png)
6. On the **Configure Rule** page under **Claim rule name** type the display name for this rule, in **User's group** click **Browse** and select a group, under **Outgoing claim type** select the desired claim type, and then under **Outgoing Claim Type** type a value. ![Screenshot that shows where to type the claim rule name when you create a rule to send group membership as a claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-send-group-membership-as-a-claim/group4.png)
7. Click the **Finish** button.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## To create a rule to send group membership as a claim on a Claims Provider Trust in Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Claims Provider Trusts**. ![Screenshot that shows where to select Claims Provider Trusts when you create a rule to send group membership as a claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule1.png)
3. Right-click the selected trust, and then click **Edit Claim Rules**. ![Screenshot that shows where to select Edit Claim Rules when you create a rule to send group membership as a claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule2.png)
4. In the **Edit Claim Rules** dialog box, under **Acceptance Transform Rules** click **Add Rule** to start the rule wizard. ![Screenshot that shows where to select Add Rule when you create a rule to send group membership as a claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule3.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Send Group Membership as Claim** from the list, and then click **Next**. ![Screenshot that shows where to select the Send Group Membership as Claim template when you create a rule to send group membership as a claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-send-group-membership-as-a-claim/group3.png)
6. On the **Configure Rule** page under **Claim rule name** type the display name for this rule, in **User's group** click **Browse** and select a group, under **Outgoing claim type** select the desired claim type, and then under **Outgoing Claim Type** type a value. ![Screenshot that shows where to type the claim rule name when you create a rule to send group membership as a claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-send-group-membership-as-a-claim/group4.png)
7. Click the **Finish** button.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## To create a rule to send group membership as a claim in Windows Server 2012 R2

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS\Trust Relationships**, click either **Claims Provider Trusts** or **Relying Party Trusts**, and then click a specific trust in the list where you want to create this rule.
3. Right-click the selected trust, and then click **Edit Claim Rules**. ![Screenshot that shows where to select Edit Claim Rules when you create a rule to send group membership as a claim in Windows Server 2012 R2.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule6.png)
4. In the **Edit Claim Rules** dialog box, select one the following tabs, depending on the trust that you are editing and which rule set you want to create this rule in, and then click **Add Rule** to start the rule wizard that is associated with that rule set:

    - **Acceptance Transform Rules**
    - **Issuance Transform Rules**
    - **Issuance Authorization Rules**
    - **Delegation Authorization Rules**![create rule](media/create-a-rule-to-permit-all-users/permitall5.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Send Group Membership as a Claim** from the list, and then click **Next**. ![Screenshot that shows where to select the Send Group Membership as a Claim template when you create a rule to send group membership as a claim in Windows Server 2012 R2.](media/create-a-rule-to-send-group-membership-as-a-claim/group1.png)
6. On the **Configure Rule** page under **Claim rule name** type the display name for this rule, in **User's group** click **Browse** and select a group, under **Outgoing claim type** select the desired claim type, and then under **Outgoing Claim Type** type a value. ![Screenshot that shows where to type the claim rule name when you create a rule to send group membership as a claim in Windows Server 2012 R2.](media/create-a-rule-to-send-group-membership-as-a-claim/group2.png)
7. Click **Finish**.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## Additional references

[Configure Claim Rules](configure-claim-rules)

[Checklist: Creating Claim Rules for a Relying Party Trust](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913578%28v=ws.11%29)

[Checklist: Creating Claim Rules for a Claims Provider Trust](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913564%28v=ws.11%29)

[When to Use an Authorization Claim Rule](../technical-reference/when-to-use-an-authorization-claim-rule)

[The Role of Claims](../technical-reference/the-role-of-claims)

[The Role of Claim Rules](../technical-reference/the-role-of-claim-rules)