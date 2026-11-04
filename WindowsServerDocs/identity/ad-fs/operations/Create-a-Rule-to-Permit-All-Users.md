---
layout: Conceptual
title: Create a Rule to Permit All Users | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/create-a-rule-to-permit-all-users
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Create a Rule to Permit All Users'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 558ad770-fc90-9be8-eaa8-112ca1b702d5
document_version_independent_id: d24f54bb-167a-924f-a577-c881135d6d81
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Permit-All-Users.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/create-a-rule-to-permit-all-users
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Create-a-Rule-to-Permit-All-Users.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: edcf9d05-fd1d-988a-9e64-ff1816368f3e
---

# Create a Rule to Permit All Users | Microsoft Learn

In Windows Server 2016, you can use an **Access Control Policy** to create a rule that will give all users access to a relying party. In Windows Server 2012 R2, using the **Permit All Users** rule template in Active Directory Federation Services (AD FS), you can create an authorization rule that will give all users access to the relying party.

You can use additional authorization rules to further restrict access. Users who are permitted to access the relying party from the Federation Service may still be denied service by the relying party.

You can use the following procedures to create a claim rule with the AD FS Management snap-in.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

## To create a rule to permit all users in Windows Server 2016

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS**, click **Relying Party Trusts**. ![Screenshot that shows where to select Relying Party Trusts.](media/create-a-rule-to-permit-all-users/permitall1.png)
3. Right-click the **Relying Party Trust** that you want to permit access to and select **Edit Access Control Policy**. ![Screenshot that shows where to select Edit Access Control Policy.](media/create-a-rule-to-permit-all-users/permitall2.png)
4. On the Access control policy select **Permit everyone** and then click **Apply** and **Ok**. ![Screenshot that highlights the Permit everyone Access control policy.](media/create-a-rule-to-permit-all-users/permitall3.png)

## To create a rule to permit all users in Windows Server 2012 R2

1. In Server Manager, click **Tools**, and then select **AD FS Management**.
2. In the console tree, under **AD FS\Trust Relationships\Relying Party Trusts**, click a specific trust in the list where you want to create this rule.
3. Right-click the selected trust, and then click **Edit Claim Rules**. ![Screenshot that shows where to select Edit Claim Rules.](media/create-a-rule-to-permit-all-users/permitall4.png)
4. In the **Edit Claim Rules** dialog box, click the **Issuance Authorization Rules** tab or the **Delegation Authorization Rules** tab (based on the type of authorization rule you require), and then click **Add Rule** to start the **Add Authorization Claim Rule Wizard**. ![Screenshot that shows the Issuance Authorization Rules tab.](media/create-a-rule-to-permit-all-users/permitall5.png)
5. On the **Select Rule Template** page, under **Claim rule template**, select **Permit All Users** from the list, and then click **Next**. ![create rule](media/create-a-rule-to-permit-all-users/permitall6.png)
6. On the **Configure Rule** page, click **Finish**.
7. In the **Edit Claim Rules** dialog box, click **OK** to save the rule.

## Additional references

[Configure Claim Rules](configure-claim-rules)

[Checklist: Creating Claim Rules for a Relying Party Trust](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913578%28v=ws.11%29)

[When to Use an Authorization Claim Rule](../technical-reference/when-to-use-an-authorization-claim-rule)

[The Role of Claims](../technical-reference/the-role-of-claims)

[The Role of Claim Rules](../technical-reference/the-role-of-claim-rules)