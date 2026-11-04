---
layout: Conceptual
title: Plan Device-based Conditional Access on-Premises | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/plan-device-based-conditional-access-on-premises
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Plan Device-based Conditional Access on-Premises'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: d4ead20d-8590-f267-506b-59f3fce14bbb
document_version_independent_id: 20871f1c-eed9-0117-f479-c4e77a022c99
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Plan-Device-based-Conditional-Access-on-Premises.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/plan-device-based-conditional-access-on-premises
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Plan-Device-based-Conditional-Access-on-Premises.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 94be6d6d-af17-3f43-5613-c6762ceb3c08
---

# Plan Device-based Conditional Access on-Premises | Microsoft Learn

This document describes conditional access policies based on devices in a hybrid scenario where the on-premises directories are connected to Microsoft Entra ID using Microsoft Entra Connect.

## AD FS and Hybrid conditional access

AD FS provides the on premises component of conditional access policies in a hybrid scenario. When you register devices with Microsoft Entra ID for conditional access to cloud resources, the Microsoft Entra Connect device write-back capability makes device registration information available on premises for AD FS policies to consume and enforce. This way, you have a consistent approach to access control policies for both on premises and cloud resources.

![conditional access](media/plan-device-based-conditional-access-on-premises/adfs_itpro4.png)

### Types of registered devices

There are three kinds of registered devices, all of which are represented as Device objects in Microsoft Entra ID and can be used for conditional access with AD FS on premises as well.

| Description | Add Work or School Account | Microsoft Entra join | Windows 10 Domain Join |
| --- | --- | --- | --- |
| Description | Users add their work or school account to their BYOD device interactively. **Note:** Add Work or School Account is the replacement for Workplace Join in Windows 8/8.1 | Users join their Windows 10 work device to Microsoft Entra ID. | Windows 10 domain joined devices automatically register with Microsoft Entra ID. |
| How users log in to the device | No log in to Windows as the work or school account. Log in using a Microsoft account. | Log in to Windows as the (work or school) account that registered the device. | Log in using AD account. |
| How devices are managed | MDM Policies (with additional Intune enrollment) | MDM Policies (with additional Intune enrollment) | Group Policy, Configuration Manager |
| Microsoft Entra ID Trust type | Workplace joined | Microsoft Entra joined | Domain joined |
| W10 Settings location | Settings &gt; Accounts &gt; Your account &gt; Add a work or school account | Settings &gt; System &gt; About &gt; Join Microsoft Entra ID | Settings &gt; System &gt; About &gt; Join a domain |
| Also available for iOS and Android Devices? | Yes | No | No |

For more information on the different ways to register devices, see also:

- [Using Windows devices in your workplace](/en-us/azure/active-directory/devices/overview)
- [Microsoft Entra registered devices](/en-us/azure/active-directory/devices/concept-azure-ad-register)
- [Microsoft Entra joined devices](/en-us/azure/active-directory/devices/concept-azure-ad-join)

### How Windows 10 User and Device Sign-on is different from previous versions

For Windows 10 and AD FS 2016, there are some new aspects of device registration and authentication you should know about (especially if you are familiar with device registration and "workplace join" in previous releases).

First, in Windows 10 and AD FS in Windows Server 2016, device registration and authentication is no longer based solely on an X509 user certificate. There is a new and more robust protocol that provides better security and a more seamless user experience. The key differences are that, for Windows 10 Domain Join and Microsoft Entra join, there is an X509 computer certificate and a new credential called a PRT. You can read all about it [here](https://jairocadena.com/2016/01/18/how-domain-join-is-different-in-windows-10-with-azure-ad/) and [here](https://jairocadena.com/2016/02/01/azure-ad-join-what-happens-behind-the-scenes/).

Second, Windows 10 and AD FS 2016 support user authentication using Windows Hello for Business, which you can read about [here](https://jairocadena.com/2016/03/09/azure-ad-and-microsoft-passport-for-work-in-windows-10/) and [here](/en-us/windows/security/identity-protection/hello-for-business/hello-identity-verification).

AD FS 2016 provides seamless device and user SSO based on both PRT and Passport credentials. Using the steps in this document, you can enable these capabilities and see them work.

### Device Access Control Policies

Devices can be used in simple AD FS access control rules such as:

- Allow access only from a registered device
- Require multifactor authentication when a device is not registered

These rules can then be combined with other factors such as network access location and multifactor authentication, creating rich conditional access policies such as:

- Require multifactor authentication for unregistered devices accessing from outside the corporate network, except for members of a particular group or groups

With AD FS 2016, these policies can be configured specifically to require a particular device trust level as well: either **authenticated**, **managed**, or **compliant**.

For more information on configuring AD FS access control policies, see [Access control policies in AD FS](../operations/access-control-policies-in-ad-fs).

#### Authenticated devices

Authenticated devices are registered devices that are not enrolled in MDM (Intune and third party MDMs for Windows 10, Intune only for iOS and Android).

Authenticated devices will have the **isManaged** AD FS claim with value **FALSE**. (Whereas devices that are not registered at all will lack this claim.) Authenticated devices (and all registered devices) will have the isKnown AD FS claim with value **TRUE**.

#### Managed Devices:

Managed devices are registered devices that are enrolled with MDM.

Managed devices will have the isManaged AD FS claim with value **TRUE**.

#### Devices compliant (with MDM or Group Policies)

Compliant devices are registered devices that are not only enrolled with MDM but compliant with the MDM policies. (Compliance information originates with the MDM and is written to Microsoft Entra ID.)

Compliant devices will have the **isCompliant** AD FS claim with value **TRUE**.

For complete list of AD FS 2016 device and conditional access claims, see Reference.

## Reference

#### [Updates and breaking changes - Microsoft identity platform | Microsoft Docs](/en-us/azure/active-directory/develop/reference-breaking-changes)

#### Complete list of new AD FS 2016 and device claims

- `https://schemas.microsoft.com/ws/2014/01/identity/claims/anchorclaimtype`
- `https://schemas.xmlsoap.org/ws/2005/05/identity/Identity_Selector_Interoperability_Profile_V1.5.pdf`
- `https://schemas.microsoft.com/2014/03/psso`
- `https://schemas.microsoft.com/2015/09/prt`
- `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn`
- `https://schemas.microsoft.com/ws/2008/06/identity/claims/primarygroupsid`
- `https://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid`
- `https://schemas.xmlsoap.org/ws/2005/05/identity/Identity_Selector_Interoperability_Profile_V1.5_Web_Guide.pdf`
- `https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname`
- `https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`
- `https://schemas.microsoft.com/2012/01/devicecontext/claims/registrationid`
- `/dotnet/api/system.security.claims.claimtypes.windowsdeviceclaim`
- `https://schemas.microsoft.com/2012/01/devicecontext/claims/identifier`
- `https://schemas.microsoft.com/2012/01/devicecontext/claims/ostype`
- `https://schemas.microsoft.com/2012/01/devicecontext/claims/osversion`
- `https://schemas.microsoft.com/2012/01/devicecontext/claims/ismanaged`
- `https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`
- `/dotnet/api/system.security.claims.claimtypes.windowsdeviceclaim`
- `https://schemas.microsoft.com/2014/02/deviceusagetime`
- `https://schemas.microsoft.com/2014/09/devicecontext/claims/iscompliant`
- `https://schemas.microsoft.com/2014/09/devicecontext/claims/trusttype`
- `https://schemas.microsoft.com/claims/authnmethodsreferences`
- `https://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-client-user-agent`
- `https://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-endpoint-absolute-path`
- `https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`
- `https://schemas.microsoft.com/2012/01/requestcontext/claims/client-request-id`
- `https://schemas.microsoft.com/2012/01/requestcontext/claims/relyingpartytrustid`
- `https://schemas.microsoft.com/2012/01/requestcontext/claims/x-ms-client-ip`
- `https://schemas.microsoft.com/2014/09/requestcontext/claims/userip`
- `https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod`