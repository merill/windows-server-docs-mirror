---
layout: Conceptual
title: Deploy Always On VPN profile to Windows clients with Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/how-to-aovpn-client-intune
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to deploy Always On VPN profile to Windows clients with Microsoft Intune.
ms.topic: install-set-up-deploy
ms.date: 2023-03-14T00:00:00.0000000Z
ms.author: roharwoo
author: robinharwood
locale: en-us
document_id: 4494634e-f720-e32d-8e5e-5dff08f8a943
document_version_independent_id: 4494634e-f720-e32d-8e5e-5dff08f8a943
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/how-to-aovpn-client-intune.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/how-to-aovpn-client-intune
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/how-to-aovpn-client-intune.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 285e1e22-5ff3-7ec3-0b21-3b7af5754802
---

# Deploy Always On VPN profile to Windows clients with Microsoft Intune | Microsoft Learn

In this how-to article, we show you how to use Intune to create and deploy Always On VPN profiles.

However, if you want to create a custom VPN profileXML, follow the guidance in [Apply ProfileXML using Intune](/en-us/windows/security/identity-protection/vpn/vpn-profile-options#apply-profilexml-using-intune).

## Prerequisites

Intune uses Microsoft Entra user groups, so you need to:

- Ensure that you have a Private Key Infrastructure (PKI) capable of issuing user and device certificates for authentication. For more information on certificates for Intune, see [Use certificates for authentication in Microsoft Intune](/en-us/mem/intune/protect/certificates-configure).
- Create a Microsoft Entra user group that's associated with VPN users and assign new users to the group as needed.
- Make sure that the VPN users have VPN server connection permissions.

## Create the Extensible Authentication Protocol (EAP) configuration XML

In this section, you'll create an Extensible Authentication Protocol (EAP) configuration XML.

1. Copy the following XML string to a text editor:

    Important

    Any other combination of upper or lower case for 'true' in the following tags results in a partial configuration of the VPN profile:

    &lt;AlwaysOn&gt;**true**&lt;/AlwaysOn&gt; &lt;RememberCredentials&gt;**true**&lt;/RememberCredentials&gt;

    ```XML
    <EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type xmlns="http://www.microsoft.com/provisioning/EapCommon">25</Type><VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId></EapMethod><Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"><Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>25</Type><EapType xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1"><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames>NPS.contoso.com</ServerNames><TrustedRootCA>5a 89 fe cb 5b 49 a7 0b 1a 52 63 b7 35 ee d7 1c c2 68 be 4b </TrustedRootCA></ServerValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>13</Type><EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames>NPS.contoso.com</ServerNames><TrustedRootCA>5a 89 fe cb 5b 49 a7 0b 1a 52 63 b7 35 ee d7 1c c2 68 be 4b </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</PerformServerValidation><AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">true</AcceptServerName></EapType></Eap><EnableQuarantineChecks>false</EnableQuarantineChecks><RequireCryptoBinding>false</RequireCryptoBinding><PeapExtensions><PerformServerValidation xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">true</PerformServerValidation><AcceptServerName xmlns="http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2">true</AcceptServerName></PeapExtensions></EapType></Eap></Config></EapHostConfig>
    ```
2. Replace the **&lt;ServerNames&gt;NPS.contoso.com&lt;/ServerNames&gt;** in the sample XML with the FQDN of the domain-joined NPS where authentication takes place.
3. Replace the **&lt;TrustedRootCA&gt;5a 89 fe cb 5b 49 a7 0b 1a 52 63 b7 35 ee d7 1c c2 68 be 4b&lt;/TrustedRootCA&gt;** in the sample with the certificate thumbprint of your on-premises root certificate authority in both places.

    Important

    Do not use the sample thumbprint in the &lt;TrustedRootCA&gt;&lt;/TrustedRootCA&gt; section below. The TrustedRootCA must be the certificate thumbprint of the on-premises root certificate authority that issued the server-authentication certificate for RRAS and NPS servers. **This must not be the cloud root certificate, nor the intermediate issuing CA certificate thumbprint**.
4. Save the XML for use in the next section.

## Create the Always On VPN configuration policy

1. Sign into [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/).
2. Go to **Devices** &gt; **Configuration profiles**.
3. Select **+ Create profile**.
4. For **Platform**, select **Windows 10 and later**.
5. For **Profile type**, select **Templates**.
6. For **Template name**, select **VPN**.
7. Select **Create**.
8. For the **Basics** tab:

    - Enter a **Name** for the VPN profile and (optionally) a description.
9. For the **Configuration settings** tab:

    1. For **Use this VPN profile with a user/device scope**, select **User**.
    2. For **Connection type:**, select **IKEv2**.
    3. For **Connection name:** enter the name of the VPN connection; for example, *Contoso AutoVPN*.
    4. For **Servers:**, add the VPN server addresses and descriptions. For the default server, set **Default server** to **True**.
    5. For **Register IP addresses with internal DNS**, select **Disable**.
    6. For **Always On:**, select **Enable**.
    7. For **Remember credentials at each logon**, select the value that's appropriate to your security policy.
    8. For **Authentication Method**, select **EAP**.
    9. For **EAP XML**, select the XML you saved in Create the EAP XML.
    10. For **Device Tunnel**, select *Disable*. To learn more about device tunnels, see [Configure VPN device tunnels in Windows 10](/en-us/windows-server/remote/remote-access/vpn/vpn-device-tunnel-config).
    11. For **IKE Security Association Parameters**

        - Set **Split tunneling** to *Enable*.
        - Configure **Trusted Network Detection**. To find the DNS suffix, you can use `Get-NetConnectionProfile > Name` on a system that's currently connected to the network and has the domain profile applied (`NetworkCategory:DomainAuthenticated`).
    12. Leave the remaining settings as default, unless your environment requires further configuration. For more information on EAP Profile settings for Intune, see [Windows 10/11 and Windows Holographic device settings to add VPN connections using Intune](/en-us/mem/intune/configuration/vpn-settings-windows-10).
    13. Select **Next**.
10. For the **Scope Tags** tab, leave default settings and select **Next**.
11. For the **Assignments** tab:

    1. Select **Add groups**, and add your VPN user group.
    2. Select **Next**.
12. For the **Applicability Rules** tab, leave default settings and select **Next**.
13. For the **Review + Create** tab, review all your settings, and select **Create**.

### Sync the Always On VPN configuration policy with Intune

To test the configuration policy, sign in to a Windows 10+ client computer as a VPN user and then sync with Intune.

1. On the Start menu, select **Settings**.
2. In Settings, select **Accounts**, and select **Access work or school**.
3. Select the account to connect to your Microsoft Entra ID, and select **Info**.
4. Move down and select **Sync** to force an Intune policy evaluation and retrieval.
5. When the synchronization is complete, close **Settings**. After synchronization, you should be able to connect to your organization's VPN server.