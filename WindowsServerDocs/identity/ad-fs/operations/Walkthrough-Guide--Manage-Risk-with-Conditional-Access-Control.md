---
layout: Conceptual
title: Walkthrough Guide - Manage Risk with Conditional Access Control | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/walkthrough-guide--manage-risk-with-conditional-access-control
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Walkthrough Guide: Manage Risk with Conditional Access Control'
ms.date: 2021-10-22T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 7a09965e-bb25-dbd2-18b7-4550b1bedefd
document_version_independent_id: dc776e65-60eb-c04b-8994-7b7df8ab2af2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Conditional-Access-Control.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/walkthrough-guide--manage-risk-with-conditional-access-control
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Conditional-Access-Control.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 58356a9e-5d3d-d7a6-d2d7-2603f9624047
---

# Walkthrough Guide - Manage Risk with Conditional Access Control | Microsoft Learn

## About This Guide

This walkthrough provides instructions for managing risk with one of the factors (user data) available through the conditional access control mechanism in Active Directory Federation Services (AD FS) in Windows Server 2012 R2. For more information about conditional access control and authorization mechanisms in AD FS in Windows Server 2012 R2, see [Manage Risk with Conditional Access Control](manage-risk-with-conditional-access-control).

This walkthrough consists of the following sections:

- [Step 1: Setting up the lab environment](walkthrough-guide--manage-risk-with-conditional-access-control#BKMK_1)
- [Step 2: Verify the default AD FS access control mechanism](walkthrough-guide--manage-risk-with-conditional-access-control#BKMK_2)
- [Step 3: Configure conditional access control policy based on user data](walkthrough-guide--manage-risk-with-conditional-access-control#BKMK_3)
- [Step 4: Verify conditional access control mechanism](walkthrough-guide--manage-risk-with-conditional-access-control#BKMK_4)

## Step 1: Setting up the lab environment

In order to complete this walkthrough, you need an environment that consists of the following components:

- An Active Directory domain with a test user and group accounts, running on Windows Server 2008, Windows Server 2008 R2, or Windows Server 2012 with its schema upgraded to Windows Server 2012 R2 or an Active Directory domain running on Windows Server 2012 R2
- A federation server running on Windows Server 2012 R2
- A web server that hosts your sample application
- A client computer from which you can access the sample application

Warning

It is highly recommended (both in production or test environments) that you do not use the same computer to be your federation server and your web server.

In this environment, the federation server issues the claims that are required so that users can access the sample application. The Web server hosts a sample application that will trust the users who present the claims that the federation server issues.

For instructions on how to set up this environment, see [Set up the lab environment for AD FS in Windows Server 2012 R2](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2).

## Step 2: Verify the default AD FS access control mechanism

In this step you will verify the default AD FS access control mechanism, where the user is redirected to the AD FS sign-in page, provides valid credentials, and is granted access to the application. You can use the **Robert Hatley** AD account and the **claimapp** sample application that you configured in [Set up the lab environment for AD FS in Windows Server 2012 R2](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2).

#### To verify the default AD FS access control mechanism

1. On your client computer, open a browser window, and navigate to your sample application: **`https://webserv1.contoso.com/claimapp`**.

    This action automatically redirects the request to the federation server and you are prompted to sign in with a username and password.
2. Type in the credentials of the **Robert Hatley** AD account that you created in [Set up the lab environment for AD FS in Windows Server 2012 R2](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2).

    You will be granted access to the application.

## Step 3: Configure conditional access control policy based on user data

In this step you will set up an access control policy based on the user group membership data. In other words, you will configure an **Issuance Authorization Rule** on your federation server for a relying party trust that represents your sample application - **claimapp**. By this rule's logic, **Robert Hatley** AD user will be issued claims that are required to access this application because he belongs to a **Finance** group. You have added the **Robert Hatley** account to the **Finance** group in [Set up the lab environment for AD FS in Windows Server 2012 R2](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2).

You can complete this task using either AD FS Management Console or via Windows PowerShell.

#### To configure conditional access control policy based on user data via the AD FS Management Console

1. In the AD FS Management Console, navigate to **Trust Relationships**, and then **Relying Party Trusts**.
2. Select the relying party trust that represents your sample application (**claimapp**), and then either in the **Actions** pane or by right-clicking this relying party trust, select **Edit Claim Rules**.
3. In the **Edit Claim Rules for claimapp** window, select **Issuance Authorization Rules** tab and click **Add Rule**.
4. In the **Add Issuance Authorization Claim Rule Wizard**, on the **Select Rule Template page**, select **Permit or Deny Users Based on an Incoming Claim** claim rule template and then click **Next**.
5. On the **Configure Rule** page, do all of the following and then click **Finish**:

    1. Enter a name for the claim rule, for example **TestRule**.
    2. Select **Group SID** as **Incoming claim type**.
    3. Click **Browse**, type in **Finance** for the name of your AD test group, and resolve it for the **Incoming claim value** field.
    4. Select the **Deny access to users with this incoming claim** option.
6. In the **Edit Claim Rules for claimapp** window, make sure to delete the **Permit Access to All Users** rule that was created by default when you created this relying party trust.

#### To configure conditional access control policy based on user data via Windows PowerShell

1. On your federation server, open the Windows PowerShell command window and run the following command:

```powershell
$rp = Get-AdfsRelyingPartyTrust -Name claimapp
```

1. In the same Windows PowerShell command window, run the following command:

```powershell
$GroupAuthzRule = '@RuleTemplate = "Authorization" @RuleName = "Foo" c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid", Value =~ "^(?i)<group_SID>$"] =>issue(Type = "https://schemas.microsoft.com/authorization/claims/deny", Value = "DenyUsersWithClaim");'
Set-AdfsRelyingPartyTrust -TargetRelyingParty $rp -IssuanceAuthorizationRules $GroupAuthzRule
```

Note

Make sure to replace &lt;group\_SID&gt; with the value of the SID of your AD **Finance** group.

## Step 4: Verify conditional access control mechanism

In this step you will verify the conditional access control policy that you set up in the previous step. You can use the following procedure to verify that **Robert Hatley** AD user can access your sample application because he belongs to the **Finance** group and AD users who do not belong to the **Finance** group cannot access the sample application.

1. On your client computer, open a browser window, and navigate to your sample application: **`https://webserv1.contoso.com/claimapp`**

    This action automatically redirects the request to the federation server and you are prompted to sign in with a username and password.
2. Type in the credentials of the **Robert Hatley** AD account that you created in [Set up the lab environment for AD FS in Windows Server 2012 R2](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2).

    You will be granted access to the application.
3. Type in the credentials of another AD user that does NOT belong to the **Finance** group. (For more information on how to create user accounts in AD, see [https://technet.microsoft.com/library/cc7833232.aspx](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc783323%28v=ws.10%29).

    At this point, because of the access control policy that you set up in the previous step, an 'access denied' message is displayed for this AD user that does NOT belong to the **Finance** group. The default message text is **You are not authorized to access this site. Click here to sign out and sign in again or contact your administrator for permissions.** However, this text is fully customizable. For more information about how to customize the sign-in experience, see [Customizing the AD FS Sign-in Pages](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280950%28v=ws.11%29).