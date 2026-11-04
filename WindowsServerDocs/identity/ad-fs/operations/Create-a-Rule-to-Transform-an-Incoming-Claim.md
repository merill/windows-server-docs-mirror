---
layout: Conceptual
title: Create a Rule to Transform an Incoming Claim | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/create-a-rule-to-transform-an-incoming-claim
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Create a Rule to Transform an Incoming Claim'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 9fc5faeb-ed96-ecbe-63e3-8e3dd7ac59d5
document_version_independent_id: aee0f598-002a-bcf6-43c2-ef2c9f10a311
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/create-a-rule-to-transform-an-incoming-claim
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: d9a9c87c-1ef0-825a-2859-18fb04483481
---

# Create a Rule to Transform an Incoming Claim | Microsoft Learn

By using the **Transform an Incoming Claim** rule template in Active Directory Federation Services (AD FS), you can select an incoming claim, change its claim type, and change its claim value. For example, you can use this rule template to create a rule that sends a role claim with the same claim value of an incoming group claim. You can also use this rule to send a group claim with a claim value of Purchasers when there is an incoming group claim with a value of Admins, or you can send only user principal name (UPN) claims that end with @fabrikam.

You can use the following procedure to create a claim rule with the AD FS Management snap-in.

Membership in **Administrators**, or equivalent, on the local computer is the minimum requirement to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

## To create a rule to transform an incoming claim on a Relying Party Trust in Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Relying Party Trusts**. ![Screenshot that shows where to select Relying Party Trusts when you create a rule to transform an incoming claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule9.png)
3. Right-click the selected trust, and then click **Edit Claim Issuance Policy**. ![Screenshot that shows where to select Edit Claim Issuance Policy when you create a rule to transform an incoming claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule10.png)
4. In the **Edit Claim Issuance Policy** dialog box, under **Issuance Transform Rules** click **Add Rule** to start the rule wizard. ![Screenshot that shows where to select Add Rule when you create a rule to transform an incoming claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule11.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Transform an Incoming Claim** from the list, and then click **Next**. ![Screenshot that shows where to select the Transform an Incoming Claim when you create a rule to transform an incoming claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-transform-an-incoming-claim/transform3.png)
6. On the **Configure Rule** page, under **Claim rule name**, type the display name for this rule. In **Incoming claim type**, select a claim type in the list. In **Outgoing claim type**, select a claim type in the list, and then select one of the following options, which depends on the requirements of your organization:

    - **Pass through all claim values**
    - **Replace an incoming claim value with a different outgoing claim value**
    - **Replace incoming e-mail suffix claims with a new e-mail suffix**![Screenshot that shows where to type the claim rule name when you create a rule to transform an incoming claim on a Relying Party Trust in Windows Server 2016.](media/create-a-rule-to-transform-an-incoming-claim/transform4.png)
7. Click the **Finish** button.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

Note

If you are setting up the Dynamic Access Control scenario that uses AD FS-issued claims, first create a transform rule on the claims provider trust, and in **Incoming claim type**, type the name for the incoming claim, or, if a claim description was previously created, select it from the list. Second, in **Outgoing claim type**, select the claim URL that you want, and then create a transform rule on the relying party trust to issue the device claim.

For more information about Dynamic Access Control scenarios, see [Dynamic Access Control Content Roadmap](../../solution-guides/dynamic-access-control--scenario-overview) or [Using AD DS Claims with AD FS](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831504%28v=ws.11%29).

## To create a rule to transform an incoming claim on a Claims Provider Trust in Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Claims Provider Trusts**. ![Screenshot that shows where to select Claims Provider Trusts when you create a rule to transform an incoming claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule1.png)
3. Right-click the selected trust, and then click **Edit Claim Rules**. ![Screenshot that shows where to select Edit Claim Rules when you create a rule to transform an incoming claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule2.png)
4. In the **Edit Claim Rules** dialog box, under **Acceptance Transform Rules** click **Add Rule** to start the rule wizard. ![Screenshot that shows where to select Add Rule when you create a rule to transform an incoming claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule3.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Transform an Incoming Claim** from the list, and then click **Next**. ![Screenshot that shows where to select the Transform an Incoming Claim template when you create a rule to transform an incoming claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-transform-an-incoming-claim/transform3.png)
6. On the **Configure Rule** page, under **Claim rule name**, type the display name for this rule. In **Incoming claim type**, select a claim type in the list. In **Outgoing claim type**, select a claim type in the list, and then select one of the following options, which depends on the requirements of your organization:

    - **Pass through all claim values**
    - **Replace an incoming claim value with a different outgoing claim value**
    - **Replace incoming e-mail suffix claims with a new e-mail suffix**![Screenshot that shows where to type the claim rule name when you create a rule to transform an incoming claim on a Claims Provider Trust in Windows Server 2016.](media/create-a-rule-to-transform-an-incoming-claim/transform4.png)
7. Click the **Finish** button.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

Note

If you are setting up the Dynamic Access Control scenario that uses AD FS-issued claims, first create a transform rule on the claims provider trust, and in **Incoming claim type**, type the name for the incoming claim, or, if a claim description was previously created, select it from the list. Second, in **Outgoing claim type**, select the claim URL that you want, and then create a transform rule on the relying party trust to issue the device claim.

For more information about Dynamic Access Control scenarios, see [Dynamic Access Control Content Roadmap](../../solution-guides/dynamic-access-control--scenario-overview) or [Using AD DS Claims with AD FS](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831504%28v=ws.11%29).

## To create a rule to transform an incoming claim in Windows Server 2012 R2

1. In Server Manager, click **Tools**, and then click **AD FS Management**.
2. In the console tree, under **AD FS\Trust Relationships**, click either **Claims Provider Trusts** or **Relying Party Trusts**, and then click a specific trust in the list where you want to create this rule.
3. Right-click the selected trust, and then click **Edit Claim Rules**. ![Screenshot that shows where to select Edit Claim Rules when you create a rule in Windows Server 2012 R2.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule6.png)
4. In the **Edit Claim Rules** dialog box, select one the following tabs, which depends on the trust that you are editing and in which rule set you want to create this rule, and then click **Add Rule** to start the rule wizard that is associated with that rule set:

    - **Acceptance Transform Rules**
    - **Issuance Transform Rules**
    - **Issuance Authorization Rules**
    - **Delegation Authorization Rules**![Screenshot that shows where to select Edit Claim Rules when you create a rule to transform an incoming claim in Windows Server 2012 R2.](media/create-a-rule-to-permit-all-users/permitall5.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Transform an Incoming Claim** from the list, and then click **Next**. ![Screenshot that shows where to select the Transform an Incoming Claim template when you create a rule to transform an incoming claim in Windows Server 2012 R2.](media/create-a-rule-to-transform-an-incoming-claim/transform1.png)
6. On the **Configure Rule** page, under **Claim rule name**, type the display name for this rule. In **Incoming claim type**, select a claim type in the list. In **Outgoing claim type**, select a claim type in the list, and then select one of the following options, which depends on the requirements of your organization:

    - **Pass through all claim values**
    - **Replace an incoming claim value with a different outgoing claim value**
    - **Replace incoming e-mail suffix claims with a new e-mail suffix**![create rule](media/create-a-rule-to-transform-an-incoming-claim/transform2.png)

Note

If you are setting up the Dynamic Access Control scenario that uses AD FS-issued claims, first create a transform rule on the claims provider trust, and in **Incoming claim type**, type the name for the incoming claim, or, if a claim description was previously created, select it from the list. Second, in **Outgoing claim type**, select the claim URL that you want, and then create a transform rule on the relying party trust to issue the device claim.

For more information about Dynamic Access Control scenarios, see [Dynamic Access Control Content Roadmap](../../solution-guides/dynamic-access-control--scenario-overview) or [Using AD DS Claims with AD FS](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831504%28v=ws.11%29).

1. Click **Finish**.
2. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## Additional references

[Configure Claim Rules](configure-claim-rules)

[Checklist: Creating Claim Rules for a Relying Party Trust](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913578%28v=ws.11%29)

[Checklist: Creating Claim Rules for a Claims Provider Trust](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913564%28v=ws.11%29)

[When to Use an Authorization Claim Rule](../technical-reference/when-to-use-an-authorization-claim-rule)

[The Role of Claims](../technical-reference/the-role-of-claims)

[The Role of Claim Rules](../technical-reference/the-role-of-claim-rules)