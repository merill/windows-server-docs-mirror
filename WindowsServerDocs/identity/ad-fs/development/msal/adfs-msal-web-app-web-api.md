---
layout: Conceptual
title: AD FS MSAL Web app (server app) calling web APIs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/development/msal/adfs-msal-web-app-web-api
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn how to build a web app signing-in users authenticated by AD FS 2019.
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: 1023d1b4-ba6b-32ab-7e9c-7cfb7a4b07dd
document_version_independent_id: 876ffb88-2999-179c-aab8-a7db6e773011
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/development/msal/adfs-msal-web-app-web-api.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/development/msal/adfs-msal-web-app-web-api
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/development/msal/adfs-msal-web-app-web-api.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e31b9be-b6e9-4221-a20b-d1460dbd5dfa
- https://authoring-docs-microsoft.poolparty.biz/devrel/5f286262-a4cb-47f4-92d3-dc24f172492b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
- https://authoring-docs-microsoft.poolparty.biz/devrel/8d63a4c4-4889-43b4-a98e-8e50dbfdb083
- https://authoring-docs-microsoft.poolparty.biz/devrel/90571f66-8410-4272-8117-79ce87fc2dcc
platformId: 8c136d3a-c68d-5842-d5c7-2aa00e39839f
---

# AD FS MSAL Web app (server app) calling web APIs | Microsoft Learn

Learn how to build a web app signing-in users authenticated by AD FS 2019 and acquiring tokens using [MSAL library](/en-us/entra/msal/dotnet/) to call web APIs.

Before reading this article, you should be familiar with the [AD FS concepts](../ad-fs-openid-connect-oauth-concepts) and [Authorization code grant flow](../../overview/ad-fs-openid-connect-oauth-flows-scenarios#authorization-code-grant-flow)

## Overview

![Overview of web app calling web api](media/adfs-msal-web-app-web-api/webapp1.png)

In this flow, you add authentication to your Web App (Server App), which can therefore sign in users and calls a web API. From the Web App, to call the Web API, use MSAL's AcquireTokenByAuthorizationCode token acquisition method. You use the Authorization code flow, storing the acquired token in the token cache. Then the controller acquires tokens silently from the cache when needed. MSAL refreshes the token if needed.

Web Apps that calls Web APIs:

- are confidential client applications.
- registered a secret (application shared secret, certificate or AD account) with AD FS. This secret is passed-in during the call to AD FS to get a token.

To register a Web App in AD FS and to configure it to acquire tokens to call a Web API, let's use a sample available [here](/en-us/entra/msal/dotnet/) and walk through the app registration and code configuration steps.

## Pre-requisites

- GitHub client tools
- AD FS 2019 or later configured and running
- Visual Studio 2013 or later

## App Registration in AD FS

This section shows how to register the Web App as a confidential client and Web API as a Relying Party (RP) in AD FS.

1. In AD FS Management, right-click on **Application Groups** and select **Add Application Group**.
2. On the Application Group Wizard, for the **Name** enter **WebAppToWebApi** and under **Client-Server applications** select the **Server application accessing a Web API** template. Click **Next**.

    ![Screenshot of the Welcome page of the Add Application Group Wizard showing the Server application accessing a web A P I template highlighted.](media/adfs-msal-web-app-web-api/webapp2.png)
3. Copy the **Client Identifier** value. The value is used later as the value for **ida:ClientId** in the applications **Web.config** file. Enter the following for **Redirect URI:** - https://localhost:44326. Click Add. Click **Next**.

    ![Screenshot of the Server application page of the Add Application Group Wizard showing the correct client identifier and redirect U R I.](media/adfs-msal-web-app-web-api/webapp3.png)
4. On the Configure Application Credentials screen, place a check-in **Generate a shared secret** and copy the secret. This secret is used later as the value for **ida:ClientSecret** in the applications **Web.config** file. Click **Next**.

    ![Screenshot of the Configure Application Credentials application page of the Add Application Group Wizard showing the Generate a shared secret option selected and the generated shared secret populated.](media/adfs-msal-web-app-web-api/webapp4.png)
5. On the Configure Web API screen, enter the **Identifier:** https://webapi. Click **Add**. Click **Next**. This value is used later for **ida:GraphResourceId** in the applications **Web.config** file.

    ![Screenshot of the Configure Web API page of the Add Application Group Wizard showing the correct identifier.](media/adfs-msal-web-app-web-api/webapp5.png)
6. On the Apply Access Control Policy screen, select **Permit** everyone and click **Next**.

    ![Screenshot of the Choose Access Control Policy page of the Add Application Group Wizard showing the Permit everyone option highlighted.](media/adfs-msal-web-app-web-api/webapp6.png)
7. On the Configure Application Permissions screen, make sure **openid** and **user\_impersonation** are selected and click **Next**.

    ![Screenshot of the Configure Application Permissions page of the Add Application Group Wizard showing the open I D and user impersonation options selected.](media/adfs-msal-web-app-web-api/webapp7.png)
8. On the Summary screen, click **Next**.
9. On the Complete screen, click **Close**.

## Code Configuration

This section shows how to configure a ASP.NET Web App to sign-in user and retrieve token to call the Web API

1. Download the sample from [here](https://github.com/Azure-Samples/active-directory-dotnet-native-aspnetcore-v2/)
2. Open the sample using Visual Studio
3. Open the web.config file. Modify the following:

    - `ida:ClientId` - enter the **Client Identifier** value from #3 in App Registration in AD FS section.
    - `ida:ClientSecret` - enter the **Secret** value from #4 in App Registration in AD FS section.
    - `ida:RedirectUri` - enter the **Redirect URI** value from #3 in App Registration in AD FS section.
    - `ida:Authority` - enter https://[your AD FS hostname]/adfs. E.g., `https://adfs.contoso.com/adfs`
    - `ida:Resource` - enter the **Identifier** value from #5 in App Registration in AD FS section.

        ![Screenshot of the web config file showing the modified values.](media/adfs-msal-web-app-web-api/webapp8.png)

### Test the sample

This section shows how to test the sample configured.

1. Once the code changes are made rebuild the solution.
2. At the top of Visual Studio, make sure Internet Explorer is selected and click the green arrow.

    ![Screenshot of the Visual Studio UI with the IIS Express (Internet Explorer) option called out.](media/adfs-msal-web-app-web-api/webapp9.png)
3. On Home Page, click on Sign-in.

    ![Screenshot of the Home Page with the Sign in option called out.](media/adfs-msal-web-app-web-api/webapp10.png)
4. You'll be re-directed to the AD FS sign-in page. Go ahead and sign in.

    ![Screenshot of the Sign in page.](media/adfs-msal-web-app-web-api/webapp11.png)
5. Once signed-in, click on Access Token.

    ![Screenshot of the Home Page with the Access Token option called out.](media/adfs-msal-web-app-web-api/webapp12.png)
6. Clicking on Access Token gets the access token info by calling the Web API.

    ![Screenshot of the Access Token page showing the access token info.](media/adfs-msal-web-app-web-api/webapp13.png)