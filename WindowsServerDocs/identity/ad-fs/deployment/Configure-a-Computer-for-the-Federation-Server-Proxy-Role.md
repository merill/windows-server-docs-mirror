---
layout: Conceptual
title: Configure a Computer for the Federation Server Proxy Role | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/configure-a-computer-for-the-federation-server-proxy-role
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure a Computer for the Federation Server Proxy Role'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 85e318a2-f48a-3793-3bee-1ec627668c60
document_version_independent_id: 7e3e6c5f-d128-dfaa-c154-d44be88c22d5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Configure-a-Computer-for-the-Federation-Server-Proxy-Role.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/configure-a-computer-for-the-federation-server-proxy-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Configure-a-Computer-for-the-Federation-Server-Proxy-Role.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 40f92abd-9742-aa78-c8c1-49fa71dc620d
---

# Configure a Computer for the Federation Server Proxy Role | Microsoft Learn

After you configure a computer with the required certificates and have installed the Federation Service Proxy role service, you are ready to configure the computer to become a federation server proxy. You can use the following procedure so that the computer acts in the federation server proxy role.

Important

Before you use this procedure to configure the federation server proxy computer, make sure that you have followed all the steps in [Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy) in the order that they are listed. Make sure that at least one federation server is deployed and that all the necessary credentials for authorizing a federation server proxy configuration are implemented. You must also configure Secure Sockets Layer (SSL) bindings on the Default Web Site, or this wizard will not start. All these tasks must be completed before this federation server proxy can function.

After you finish setting up the computer, verify that the federation server proxy is working as expected. For more information, see [Verify That a Federation Server Proxy Is Operational](verify-that-a-federation-server-proxy-is-operational).

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### To configure a computer for the federation server proxy role

1. There are two ways to start the AD FS Federation Server Configuration Wizard. To start the wizard, do one of the following:

    - On the **Start** screen, type**AD FS Federation Server Proxy Configuration Wizard**, and then press ENTER.
    - Anytime after the setup wizard is complete, open Windows Explorer, navigate to the **C:\Windows\ADFS** folder, and then double-click **FspConfigWizard.exe**.
2. Using either method, start the wizard, and on the **Welcome** page, click **Next**.
3. On the **Specify Federation Service Name** page, under **Federation Service name**, type the name that represents the Federation Service for which this computer will act in the proxy role.
4. Based on your specific network requirements, determine whether you will need to use an HTTP proxy server to forward requests to the Federation Service. If so, select the **Use an HTTP proxy server when sending requests to this Federation Service** check box, under **HTTP proxy server address** type the address of the proxy server, click **Test Connection** to verify connectivity, and then click **Next**.
5. When you are prompted, specify the credentials that are necessary to establish a trust between this federation server proxy and the Federation Service.

    By default, only the service account used by the Federation Service or a member of the local BUILTIN\Administrators group can authorize a federation server proxy.
6. On the **Ready to Apply Settings** page, review the details. If the settings appear to be correct, click **Next** to begin configuring this computer with these proxy settings.
7. On the **Configuration Results** page, review the results. When all the configuration steps are finished, click **Close** to exit the wizard.

    There is no Microsoft Management Console (MMC) snap-in to use for administering federation server proxys. To configure settings for each of the federation server proxys in your organization, use Windows PowerShell cmdlets.

## Configuring an Alternate TCP/IP Port for Proxy Operations

By default, the federation server proxy service is configured to use TCP port 443 for HTTPS traffic and port 80 for HTTP traffic for communication with the federation server. To configure different ports, such as TCP port 444 for HTTPS and port 81 for HTTP, the following tasks must be completed.

Note

If you intend to initially deploy AD FS to operate under alternate TCP/IP ports, you should first modify ports in your IIS protocol bindings for HTTP and HTTPS on both the federation server and federation server proxy computers. This should occur before you run the AD FS configuration wizards for initial configuration. If you configure Internet Information Services (IIS) first, your alternate TCP/IP port settings are discovered when wizard-based configuration occurs within AD FS, and the following procedure is not necessary. If you want to change the port settings later, update IIS protocol bindings first, and then use the following procedure to update port settings appropriately. For more information about editing IIS bindings, see [article 149605](/en-us/iis/configuration/system.applicationhost/sites/site/bindings/) in the Microsoft Knowledge Base.

#### To configure alternate TCP/IP ports for the federation server proxy to use

1. Configure the federation server to use the nondefault ports.

    To do this, specify the nondefault port number by including it with the *HttpsPort* and *HttpPort* options as part of the **Set-ADFSProperties** cmdlet. For example, to configure these ports, use the following commands in the Windows PowerShell session on the federation server computer:

    ```
    Set-ADFSProperties -HttpsPort 444
    Set-ADFSProperties -HttpPort 81
    ```
2. Configure the federation server proxy to use the nondefault port.

    To do this, specify the nondefault port number by including it with the *HttpsPort* and *HttpPort* options as part of the **Set-ADFSProxyProperties** cmdlet. For example, to configure these ports, use the following commands in the Windows PowerShell session on the federation server computer:

    ```
    Set-ADFSProxyProperties -HttpsPort 444
    Set-ADFSProxyProperties -HttpPort 81
    ```

    Note

    Endpoint URLs are not enabled by default for the federation server proxy service. If you are configuring a new federation server installation, you must enable federation server proxy service endpoints first. For example, it is assumed that for all the endpoints that the example in this procedure refers to you have enabled them for proxy by selecting them in the AD FS Management snap-in and then selecting **Enable on proxy**.
3. Update the IIS installation at the federation server proxy so that Security Assertion Markup Language (SAML) and WS-Trust endpoints are configured to reflect the updated port number. To do this, you can use Notepad to modify the following in the Web.config file, which is located at systemdrive%\inetpub\adfs\ls\ on the federation server proxy computer. For example, assuming that you have a federation server named sts1.contoso.com and the new port number is 444, browse to and open the Web.config file in Notepad on the federation server proxy computer, locate the following section, modify the port number as highlighted below, and then save and exit Notepad.

    ```
    <securityTokenService samlProtocolEndpoint="https://sts1.contoso.com:444/adfs/services/trust/samlprotocol/proxycertificatetransport"
          wsTrustEndpoint="https://sts1.contoso.com:444/adfs/services/trust/proxycertificatetransport" />
    ```
4. Add the federation server proxy service user account to the access control list (ACL) for the related endpoint URLs. For example, if the port number is 1234 and the user account that is used to run the AD FSfederation server proxy service under is the built-in Network Service account, type the following command at a command prompt:

    ```
    netsh http add urlacl https://+:444/adfs/fs/federationserverservice.asmx/ user="NT Authority\Network Service"
    netsh http add urlacl https://+:444/FederationMetadata/2007-06/ user="NT Authority\Network Service"
    netsh http add urlacl https://+:444/adfs/services/ user="NT Authority\Network Service"
    
    netsh http add urlacl http://+:81/adfs/services/ user="NT Authority\Network Service"
    ```

    The previous commands must be run on both the federation server and the federation server proxy computers.

## Additional references

[Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy)