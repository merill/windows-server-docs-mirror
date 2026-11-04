---
layout: Conceptual
title: Create a Rule to Permit or Deny Users Based on an Incoming Claim | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Create a Rule to Permit or Deny Users Based on an Incoming Claim'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 02321fe5-3aa1-5510-269f-11168b25a84b
document_version_independent_id: 269c64a2-8c70-4933-5834-4c6635e09f24
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 38d9abd7-656c-ab78-f855-49c836f44184
---

# Create a Rule to Permit or Deny Users Based on an Incoming Claim | Microsoft Learn

In Windows Server 2016, you can use an **Access Control Policy** to create a rule that will permit or deny users based on an incoming claim. In Windows Server 2012 R2, using the **Permit or Deny Users Based on an Incoming Claim** rule template in Active Directory Federation Services (AD FS), you can create an authorization rule that will grant or deny user's access to the relying party based on the type and value of an incoming claim.

For example, you can use this to create a rule that will permit only users that have a group claim with a value of Domain Admins to access the relying party. If you want to permit all users to access the relying party, use the **Permit Everyone** Access Control Policy or the **Permit All Users** rule template depending on your version of Windows Server. Users who are permitted to access the relying party from the Federation Service may still be denied service by the relying party.

You can use the following procedure to create a claim rule with the AD FS Management snap-in.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

## To create a rule to permit users based on an incoming claim on Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Access Control Policies**. ![Screenshot that highlights Access Control Policies in the console tree.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny3.png)
3. Right-click and select **Add Access Control Policy**. ![Screenshot that highlights the Add Access Control Policy menu option.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny4.png)
4. In the name box, enter a name for your policy, a description and click **Add**. ![Screenshot that shows where to add an Access Control Policy when you create a rule to permit users based on an incoming claim on Windows Server 2016.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny5.png)
5. On the **Rule Editor**, under users, place a check in **with specific claims in the request** and click the underlined **specific** at the bottom. ![Screenshot that highlights where to select the underlined specific.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny6.png)
6. On the **Select Claims** screen, click the **Claims** radio button, select the **Claim type**, the **Operator**, and the **Claim Value** then click **Ok**. ![Screenshot that shows where to select the Claims option.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny7.png)
7. On the **Rule Editor** click **Ok**. On the **Add Access Control Policy** screen, click **Ok**.
8. In the **AD FS Management** console tree, under **AD FS**, click **Relying Party Trusts**. ![Screenshot that shows where to select Relying Party Trusts.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule9.png)
9. Right-click the **Relying Party Trust** that you want to permit access to and select **Edit Access Control Policy**. ![Screenshot that shows where to select the Edit Access Control Policy menu option.](media/create-a-rule-to-permit-all-users/permitall2.png)
10. On the Access control policy select your policy and then click **Apply** and **Ok**. ![Screenshot that shows where to select Apply and OK.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny8.png)

## To create a rule to deny users based on an incoming claim on Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Access Control Policies**. ![Screenshot that shows where to select Access Control Policies.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny3.png)
3. Right-click and select **Add Access Control Policy**. ![Screenshot that shows where to add an Access Control Policy.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny4.png)
4. In the name box, enter a name for your policy, a description and click **Add**. ![Screenshot that shows where to enter a name for your policy.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny9.png)
5. On the **Rule Editor**, make sure everyone is selected and under **Except** place a check in **with specific claims in the request** and click the underlined **specific** at the bottom. ![Screenshot that shows where to make sure that the everyone option is selected.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny10.png)
6. On the **Select Claims** screen, click the **Claims** radio button, select the **Claim type**, the **Operator**, and the **Claim Value** then click **Ok**. ![Screenshot that shows the Select Claims screen.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny11.png)
7. On the **Rule Editor** click **Ok**. On the **Add Access Control Policy** screen, click **Ok**.
8. In the **AD FS Management** console tree, under **AD FS**, click **Relying Party Trusts**. ![create rule](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule9.png)
9. Right-click the **Relying Party Trust** that you want to permit access to and select **Edit Access Control Policy**. ![Screenshot that shows where to right-click Relying Party Trust to access the Edit Access Control Policy menu option.](media/create-a-rule-to-permit-all-users/permitall2.png)
10. On the Access control policy select your policy and then click **Apply** and **Ok**. ![Screenshot that shows how go apply the changes to the Access Control Policy.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny12.png)

## To create a rule to permit or deny users based on an incoming claim on Windows Server 2012 R2

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS\Trust Relationships\Relying Party Trusts**, click a specific trust in the list where you want to create this rule.
3. Right-click the selected trust, and then click **Edit Claim Rules**. ![Screenshot that shows the Edit Claim Rules menu option.](media/create-a-rule-to-pass-through-or-filter-an-incoming-claim/claimrule6.png)
4. In the **Edit Claim Rules** dialog box, click the **Issuance Authorization Rules** tab or the **Delegation Authorization Rules** tab (based on the type of authorization rule you require), and then click **Add Rule** to start the **Add Authorization Claim Rule Wizard**. ![Screenshot that shows how to start the Add Authorization Claim Rule Wizard.](media/create-a-rule-to-permit-all-users/permitall5.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Permit or Deny Users Based on an Incoming Claim** from the list, and then click **Next**. ![Screenshot that shows where to select the Permit or Deny Users Based on an Incoming Claim template.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny1.png)
6. On the **Configure Rule** page under **Claim rule name** type the display name for this rule, in **Incoming claim type** select a claim type in the list, under **Incoming claim value** type a value or click Browse (if it is available) and select a value, and then select one of the following options, depending on the needs of your organization:

    - **Permit access to users with this incoming claim**
    - **Deny access to users with this incoming claim**![Screenshot that shows where to select the incoming claim type.](media/create-a-rule-to-permit-or-deny-users-based-on-an-incoming-claim/permitdeny2.png)
7. Click **Finish**.
8. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## Additional references

[Configure Claim Rules](configure-claim-rules)

[Checklist: Creating Claim Rules for a Relying Party Trust](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913578%28v=ws.11%29)

[When to Use an Authorization Claim Rule](../technical-reference/when-to-use-an-authorization-claim-rule)

[The Role of Claims](../technical-reference/the-role-of-claims)

[The Role of Claim Rules](../technical-reference/the-role-of-claim-rules)