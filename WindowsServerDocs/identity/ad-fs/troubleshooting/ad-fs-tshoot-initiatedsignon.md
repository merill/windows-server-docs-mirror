---
layout: Conceptual
title: Troubleshoot AD FS IdP-Initiated Sign-In | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-initiatedsignon
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn how to use the sign-in page to troubleshoot Active Directory Federation Services (AD FS) authentication.
ms.date: 2023-05-19T00:00:00.0000000Z
ms.topic: troubleshooting-general
ms.custom: sfi-image-nochange
locale: en-us
document_id: 17b38f1d-31ff-81bb-b850-2d86a6ae9ba7
document_version_independent_id: fc89f75a-b53f-ac96-c9c3-60dbea6ff19d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-initiatedsignon.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-initiatedsignon
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-initiatedsignon.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e67957a4-af27-6053-b426-d026fb66121a
---

# Troubleshoot AD FS IdP-Initiated Sign-In | Microsoft Learn

You can use the Active Directory Federation Services (AD FS) sign-in page to check if authentication is working. To do this test, you go to the page and sign in. Also, you can use the sign-in page to verify that all SAML 2.0 relying parties are listed.

## Enable the IdP-initiated sign-in page

By default, AD FS in Windows 2016 doesn't have the sign-in page enabled. To enable the page, use the PowerShell command `Set-AdfsProperties`. Use the following procedure to enable the page:

1. Open Windows PowerShell.
2. Enter `Get-AdfsProperties`.
3. Verify that the `EnableIdpInitiatedSignonPage` property is set to `False`.

    ![Screenshot that shows PowerShell output highlighting that the EnableIdpInitiatedSignonPage property is set to false.](media/ad-fs-tshoot-initiatedsignon/idp2.png)
4. In PowerShell, enter `Set-AdfsProperties -EnableIdpInitiatedSignonPage $true`.
5. PowerShell doesn't provide a confirmation for the `Set-AdfsProperties` command. To confirm that the `EnableIdpInitatedSignonPage` property is set to `True`, enter the `Get-AdfsProperties` command again and check the value for the property.

    ![Screenshot that shows PowerShell output highlighting that the EnableIdpInitiatedSignonPage property is set to True.](media/ad-fs-tshoot-initiatedsignon/idp4.png)

## Test authentication

Use the following procedure to test AD FS authentication with the Identity Provider (IdP)-initiated sign-in page.

1. Open a web browser, and go to the IdP sign-in page. Your URL might look like `https://sts.contoso.com/adfs/ls/idpinitiatedsignon.aspx`.
2. You're prompted to sign in. Enter your credentials.

    ![Screenshot that shows the sign-in page and the dialog that prompts for credentials.](media/ad-fs-tshoot-initiatedsignon/idp5.png)

If the process succeeds, you're signed in.

## Test authentication with seamless sign-in

You can test the seamless sign-in experience by making sure that the URL for your AD FS servers is added to the local intranet zone of your internet options. Use the following procedure:

1. On a Windows 10 client, select **Start**, enter **internet options**, and select **Internet Options**.
2. Select the **Security** tab, and then select **Local intranet** &gt; **Sites**.

    ![Screenshot that shows the Security tab of the Internet Properties dialog that shows the Local intranet option highlighted.](media/ad-fs-tshoot-initiatedsignon/idp8.png)
3. Select **Advanced**.
4. Enter your URL, and then select **Add** &gt; **Close**.

    ![Screenshot that shows the local intranet popup box requesting the URL to be added for authentication.](media/ad-fs-tshoot-initiatedsignon/idp9.png)
5. Select **OK**. Then select **OK** to close the internet options.
6. Open a web browser and go to the IdP sign-in page. Your URL might look like `https://sts.contoso.com/adfs/ls/idpinitiatedsignon.aspx`.
7. Select **Sign in**. You should automatically sign in and not be prompted for credentials.

    ![Screenshot that shows the sign-in page showing that the user wasn't prompted for credentials.](media/ad-fs-tshoot-initiatedsignon/idp6.png)

## Known issues

The AD FS sign-in page can't be used to initiate a sign-in with a claims provider trust that's configured with a WS-Federation passive endpoint only.