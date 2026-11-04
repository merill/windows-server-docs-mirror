---
layout: Conceptual
title: Configure Additional Authentication Methods for AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure Additional Authentication Methods for AD FS'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b9067120-9721-1333-384b-d0c322f3ba35
document_version_independent_id: e58479e3-8137-6de4-d095-7b1b47839b91
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Configure-Additional-Authentication-Methods-for-AD-FS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Configure-Additional-Authentication-Methods-for-AD-FS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 0447b866-4f6d-260e-aebf-0cba89294ce3
---

# Configure Additional Authentication Methods for AD FS | Microsoft Learn

In order to enable multifactor authentication (MFA), you must select at least one extra authentication method. By default, in Active Directory Federation Services (AD FS) in Windows Server, you can select Certificate Authentication (in other words, smart card-based authentication) as an extra authentication method.

Note

If you select Certificate Authentication, ensure that the smart card certificates have been provisioned securely and have pin requirements.

Did you know that Microsoft Azure provides similar functionality in the cloud? Learn more about [Microsoft Azure identity solutions](https://aka.ms/m2w274).

Create a hybrid identity solution in Microsoft Azure:

- [Learn about Microsoft Entra multifactor authentication.](/en-us/azure/active-directory/authentication/concept-mfa-howitworks)
- [Manage identities for single-forest hybrid environments using cloud authentication.](/en-us/previous-versions/windows/it-pro/solutions-guidance/dn550986%28v=ws.11%29)
- [Manage risk with additional multifactor authentication for sensitive applications.](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280946%28v=ws.11%29)

## Microsoft and non-Microsoft authentication methods

You can also configure and enable Microsoft and non-Microsoft authentication methods in AD FS in Windows Server. Once installed and registered with AD FS, you can enforce MFA as part of the global or per-relying-party authentication policy.

The following table lists Microsoft and non-Microsoft providers with MFA offerings currently available for AD FS in Windows Server.

| Provider | Offering | Link to learn more |
| --- | --- | --- |
| Akamai Technologies | Akamai MFA | [Integrating Akamai MFA with Microsoft AD FS](https://techdocs.akamai.com/mfa/docs/adsf) |
| aPersona | aPersona Adaptive multifactor authentication for Microsoft AD FS SSO | [aPersona ASM AD FS Adapter](https://www.apersona.com/adfs) |
| Cyphercor Inc. | LoginTC multifactor authentication for AD FS | [LoginTC AD FS Connector](https://www.logintc.com/docs/connectors/adfs.html) |
| Duo Security | Duo MFA Adapter for AD FS | [Duo Authentication for AD FS](https://duo.com/docs/adfs) |
| Duo Security | Duo MFA Adapter for AD FS | [Duo Authentication for AD FS](https://duo.com/docs/adfs) |
| Futurae | Futurae Authentication Suite for AD FS | [Futurae Strong Authentication](https://futurae.com) |
| Green Rocket Security | GreenRADIUS MFA Adapter for AD FS | [GreenRADIUS MFA for AD FS](https://www.greenrocketsecurity.com/2fa-for-adfs/) |
| inWebo Technologies | inWebo Enterprise Authentication service | [inWebo Enterprise Authentication](http://www.inwebo.com) |
| Microsoft Corp. | Microsoft Azure MFA | [Configure Azure MFA as authentication provider with AD FS](configure-ad-fs-and-azure-mfa) |
| Mideye | Mideye Authentication Provider for AD FS | [Mideye two-factor authentication with Microsoft Active Directory Federation Service](https://docs.mideye.com/6.4/integrations/microsoft-adfs/) |
| Okta | Okta MFA for Active Directory Federation Services | [Okta MFA for Active Directory Federation Services (AD FS)](https://help.okta.com/en/prod/Content/Topics/integrations/adfs-okta-int.htm) |
| One Identity | Defender AD FS | [Defender AD FS Adapter](https://www.oneidentity.com/products/defender/) |
| Ping Identity | PingID MFA Adapter for AD FS | [PingID MFA Adapter for AD FS](https://docs.pingidentity.com/pingid/pingid_integrations/pid_integrate_with_ad_fs.html) |
| RSA | RSA SecurID Authentication Agent for Microsoft Active Directory Federation Services | [RSA SecurID Authentication Agent for Microsoft Active Directory Federation Services](https://community.rsa.com/t5/securid-authentication-agent-for/tkb-p/auth-agent-ad-fs-documentation) |
| SecureMFA | SecureMFA OTP Provider | [AD FS multifactor authentication Providers](https://www.securemfa.com/) |
| Swisscom | Mobile ID Authentication Service and Signature Services | [Mobile ID Authentication Service](http://swisscom.ch/mid) |
| Symantec | Symantec Validation and ID Protection Service (VIP) | [Symantec Validation and ID Protection Service (VIP)](https://vip.symantec.com/) |
| Thales | SafeNet Trusted Access (STA) | [Authentication with AD Federation Services](https://thalesdocs.com/sta/operator/community_content/auth_adfs/index.html) |
| Trusona | Essential (passwordless MFA) and Executive (Essential + Identity Proofing) | [Trusona multifactor authentication](https://www.trusona.com/) |

## Custom authentication method for AD FS in Windows Server

We now provide instructions for building your own custom authentication method for AD FS in Windows Server. For more information, see [Build a Custom Authentication Method for AD FS in Windows Server 2012 R2](../development/ad-fs-build-custom-auth-method).