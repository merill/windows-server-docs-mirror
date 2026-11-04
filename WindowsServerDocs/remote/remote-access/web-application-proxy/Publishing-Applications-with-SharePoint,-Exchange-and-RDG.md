---
layout: Conceptual
title: Publishing Applications with SharePoint, Exchange and RDG | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/web-application-proxy/publishing-applications-with-sharepoint,-exchange-and-rdg
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: 'Learn more about: Publishing Applications with SharePoint, Exchange and RDG'
author: robinharwood
ms.author: roharwoo
ms.date: 2018-04-30T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5dbee2ba-d766-93b9-77fa-c727528e35d9
document_version_independent_id: 78b6df02-dc9d-f5b0-15ce-01f3175e3d3c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/web-application-proxy/Publishing-Applications-with-SharePoint,-Exchange-and-RDG.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/web-application-proxy/publishing-applications-with-sharepoint,-exchange-and-rdg
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/web-application-proxy/Publishing-Applications-with-SharePoint,-Exchange-and-RDG.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 0837e1ba-1ab8-46c0-037b-58902845b7f7
---

# Publishing Applications with SharePoint, Exchange and RDG | Microsoft Learn

**This content is relevant for the on-premises version of Web Application Proxy. To enable secure access to on-premises applications over the cloud, see the [Microsoft Entra application proxy content](/en-us/entra/identity/app-proxy/overview-what-is-app-proxy).**

This topic describes the tasks necessary to publish SharePoint Server, Exchange Server or Remote Desktop Gateway (RDP) through Web Application Proxy.

Note

This information is provided as-is. Remote Desktop Services supports and recommends using [Azure App Proxy to provide secure remote access to on-premises applications](/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application).

## Publish SharePoint Server

You can publish a SharePoint site through Web Application Proxy when the SharePoint site is configured for claims-based authentication or Integrated Windows authentication. If you want to use Active Directory Federation Services (AD FS) for pre-authentication, you must configure a relying party using one of the wizards.

- If the SharePoint site uses claims-based authentication, you must use the Add Relying Party Trust Wizard to configure the relying party trust for the application.
- If the SharePoint site uses Integrated Windows authentication, you must use the Add Non-Claims-Based Relying Party Trust Wizard to configure the relying party trust for the application. You can use IWA with a claims-based web application provided that you configure KDC.

    To allow users to authenticate using Integrated Windows authentication, the Web Application Proxy server must be joined to a domain.

    You must configure the application to support Kerberos constrained delegation. You can do this on the domain controller for any application. You can also configure the application directly on the backend server if it is running on Windows Server 2012 R2 or Windows Server 2012. For more information, see [What's New in Kerberos Authentication](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831747%28v=ws.11%29). You must also make sure that the Web Application Proxy servers are configured for delegation to the service principal names of the backend servers. For a walkthrough of how to configure Web Application Proxy to publish an application using Integrated Windows authentication, see [Configure a site to use Integrated Windows authentication](/en-us/previous-versions/orphan-topics/ws.11/dn308246%28v=ws.11%29).

If your SharePoint site is configured using either alternate access mappings (AAM) or host-named site collections, you can use different external and backend server URLs to publish your application. However, if you do not configure your SharePoint site using AAM or host-named site collections, you must use the same external and backend server URLs.

## Publish Exchange Server

The following table describes the Exchange services that you can publish through Web Application Proxy and the supported pre-authentication for these services:

| Exchange service | Pre-authentication | Notes |
| --- | --- | --- |
| Outlook Web App | - AD FS using non-claims-based authentication- Pass-through- AD FS using claims-based authentication for on-premises Exchange 2013 Service Pack 1 (SP1) | For more information see: [Using AD FS claims-based authentication with Outlook Web App and EAC](/en-us/exchange/using-ad-fs-claims-based-authentication-with-outlook-web-app-and-eac-exchange-2013-help) |
| Exchange Control Panel | Pass-through |  |
| Outlook Anywhere | Pass-through | You must publish additional URLs for Outlook Anywhere to work correctly:<br>- The autodiscover, EWS, and OAB (in case of Outlook cache mode) URL.- The external host name of the Exchange Server; that is, the URL that is configured for clients to connect to.- The internal FQDN of the Exchange Server. |
| Exchange ActiveSync | Pass-through AD FS using HTTP Basic authorization protocol |  |
| Exchange Web Services | Pass-through |  |
| Autodiscover | Pass-through |  |
| Offline Address Book | Pass-through |  |

To publish Outlook Web App using Integrated Windows authentication, you must use the Add Non-Claims-Based Relying Party Trust Wizard to configure the relying party trust for the application.

To allow users to authenticate using Kerberos constrained delegation the Web Application Proxy server must be joined to a domain.

You must configure the application to support Kerberos authentication. Additionally you need to register a service principal name (SPN) to the account that the web service is running under. You can do this on the domain controller or on the backend servers. In a load balanced Exchange environment this would require using the Alternate Service Account, see [Configuring Kerberos authentication for load-balanced Client Access servers](/en-us/exchange/configuring-kerberos-authentication-for-load-balanced-client-access-servers-exchange-2013-help)

You can also configure the application directly on the backend server if it is running on Windows Server 2012 R2 or Windows Server 2012. For more information, see [What's New in Kerberos Authentication](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831747%28v=ws.11%29). You must also make sure that the Web Application Proxy servers are configured for delegation to the service principal names of the backend servers.

## Publishing Remote Desktop Gateway through Web Application Proxy

If you want to restrict access to your Remote Access Gateway and add pre-authentication for remote access, you can roll it out through Web Application Proxy. This is a really good way to make sure you have rich pre-authentication for RDG including MFA. Publishing without pre-authentication is also an option and provides a single point of entry into your systems.

#### How to publish an application in RDG using Web Application Proxy pass-through authentication

1. Installation will be different depending on whether your RD Web Access (/rdweb) and RD Gateway (rpc) roles are on the same server or on different servers.
2. If the RD Web Access and RD Gateway roles are hosted on the same RDG server, you can simply publish the root FQDN in Web Application Proxy such as `https://rdg.contoso.com/`.

    You can also publish the two virtual directories individually e.g.https://rdg.contoso.com/rdweb/ and `https://rdg.contoso.com/rpc/`.
3. If the RD Web Access and the RD Gateway are hosted on separate RDG servers, you have to publish the two virtual directories individually. You can use the same or different external FQDNs, e.g., `https://rdweb.contoso.com/rdweb/` and `https://gateway.contoso.com/rpc/`.
4. If the External and Internal FQDNs are different you should not disable request header translation on the RDWeb publishing rule. This can be done by running the following PowerShell script on the Web Application Proxy server but it should be enabled by default.

    ```PowerShell
    Get-WebApplicationProxyApplication applicationname | Set-WebApplicationProxyApplication -DisableTranslateUrlInRequestHeaders:$false
    ```

    Note

    If you need to support rich clients such as RemoteApp and Desktop Connections or iOS Remote Desktop connections, these do not support pre-authentication so you have to publish RDG using pass-through authentication.

#### How to publish an application in RDG using Web Application Proxy with pre-authentication

1. Web Application Proxy pre-authentication with RDG works by passing the pre-authentication cookie obtained by Internet Explorer being passed into the Remote Desktop Connection client (mstsc.exe). This is then used by the Remote Desktop Connection client (mstsc.exe). This is then used by Remote Desktop Connection client as proof of authentication.

    The following procedure tells the Collection server to include the necessary custom RDP properties in the Remote App RDP files that are sent to clients. These tell the client that pre-authentication is required and to pass the cookies for the pre-authentication server address to Remote Desktop Connection client (mstsc.exe). In conjunction with disabling the HttpOnly feature on the Web Application Proxy application, this allows the Remote Desktop Connection client (mstsc.exe) to utilize the Web Application Proxy cookie obtained through the browser.

    Authentication to the RD Web Access server will still use the RD Web Access form logon. This provides the least number of user authentication prompts as the RD Web Access logon form creates a client-side credential store that can then be used by Remote Desktop Connection client (mstsc.exe) for any subsequent Remote App launch.
2. First, create a manual Relying Party Trust in AD FS as if you were publishing a claims aware app. This means that you have to create a dummy relying party trust that is there to enforce pre-authentication, so that you get pre-authentication without Kerberos Constrained Delegation to the published server. Once a user has authenticated, everything else is passed through.

    Warning

    It might seem that using delegation is preferable but it does not fully solve mstsc SSO requirements and there are issues when delegating to the /rpc directory because the client expects to handle the RD Gateway authentication itself.
3. To create a manual Relying Party Trust, follow the steps in the AD FS Management Console:

    1. Use the **Add Relying Party Trust** wizard
    2. Select **Enter data about the relying party manually**.
    3. Accept all default settings.
    4. For the Relying Party Trust identifier, enter the external FQDN you will use for RDG access, for example `https://rdg.contoso.com/`.

        This is the relying party trust you will use when publishing the app in Web Application Proxy.
4. Publish the root of the site (for example, `https://rdg.contoso.com/` ) in Web Application Proxy. Set the pre-authentication to AD FS and use the relying party trust you created above. This will enable /rdweb and /rpc to use the same Web Application Proxy authentication cookie.

    It is possible to publish /rdweb and /rpc as separate applications and even to use different published servers. You just need to ensure that you publish both using the same Relying Party Trust as the Web Application Proxy token is issued for the Relying Party Trust and is therefore valid across applications published with the same Relying Party Trust.
5. If the External and Internal FQDNs are different you should not disable request header translation on the RDWeb publishing rule. This can be done by running the following PowerShell script on the Web Application Proxy server but it should be enabled by default:

    ```PowerShell
    Get-WebApplicationProxyApplication applicationname | Set-WebApplicationProxyApplication -DisableTranslateUrlInRequestHeaders:$true
    ```
6. Disable the HttpOnly cookie property in Web Application Proxy on the RDG published application. To allow the RDG ActiveX control access to the Web Application Proxy authentication cookie, you have to disable the HttpOnly property on the Web Application Proxy cookie.

    This requires you to install the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2 (KB3000850)](https://support.microsoft.com/kb/3000850).

    After installing the hotfix, run the following PowerShell script on the Web Application Proxy server specifying the relevant application name:

    ```PowerShell
    Get-WebApplicationProxyApplication applicationname | Set-WebApplicationProxyApplication -DisableHttpOnlyCookieProtection:$true
    ```

    Disabling HttpOnly allows the RDG ActiveX control access to the Web Application Proxy authentication cookie.
7. Configure the relevant RDG collection on the Collection server to let the Remote Desktop Connection client (mstsc.exe) know that pre-authentication is required in the rdp file.

    - In Windows Server 2012 and Windows Server 2012 R2 this can be accomplished by running the following PowerShell cmdlet on the RDG Collection server:

        ```PowerShell
        Set-RDSessionCollectionConfiguration -CollectionName "<yourcollectionname>" -CustomRdpProperty "pre-authentication server address:s: <https://externalfqdn/rdweb/>`nrequire pre-authentication:i:1"
        ```

        Make sure you remove the &lt; and &gt; brackets when you replace with your own values, for example:

        ```PowerShell
        Set-RDSessionCollectionConfiguration -CollectionName "MyAppCollection" -CustomRdpProperty "pre-authentication server address:s: https://rdg.contoso.com/rdweb/`nrequire pre-authentication:i:1"
        ```
    - In Windows Server 2008 R2:

        1. Sign in to the Terminal Server with an account that has Administrator privileges.
        2. Go to **Start** &gt;**Administrative Tools** &gt; **Terminal Services** &gt; **TS RemoteApp Manager.**
        3. In the **Overview** pane of TS RemoteApp Manager, next to RDP Settings, select **Change**.
        4. On the **Custom RDP Settings** tab, type the following RDP settings into the Custom RDP settings box:

            `pre-authentication server address: s: https://externalfqdn/rdweb/`

            `require pre-authentication:i:1`
        5. When you are done, select **Apply**.

            This tells the Collection server to include the custom RDP properties in the RDP files that are sent to clients. These tell the client that pre-authentication is required and to pass the cookies for the pre-authentication server address to the Remote Desktop Connection client (mstsc.exe). This, in conjunction with disabling HttpOnly on the Web Application Proxy application, allows the Remote Desktop Connection client (mstsc.exe) to utilize the Web Application Proxy authentication cookie obtained through the browser.

            For more information on RDP, see [Configuring the TS Gateway OTP Scenario](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731249%28v=ws.10%29).

## See also

- [Planning to Publish Applications Using Web Application Proxy](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn383650%28v=ws.11%29)
- [Troubleshooting Web Application Proxy](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn770156%28v=ws.11%29)
- [Web Application Proxy Walkthrough Guide](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn280944%28v=ws.11%29)