---
layout: Conceptual
title: Configure a federation server with Device Registration Service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/configure-a-federation-server-with-device-registration-service
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure a federation server with Device Registration Service'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: ed8700a9-1545-7d06-cbdf-d04cd3d17c1b
document_version_independent_id: e36d8cbb-8f37-0cb3-162b-154098b096c1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Configure-a-federation-server-with-Device-Registration-Service.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/configure-a-federation-server-with-device-registration-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Configure-a-federation-server-with-Device-Registration-Service.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 351e4d8d-9d91-4ed9-1a52-66dda1281be0
---

# Configure a federation server with Device Registration Service | Microsoft Learn

You can enable Device Registration Service (DRS) on your federation server after you complete the procedures in [Step 4: Configure a Federation Server](/en-us/previous-versions/orphan-topics/ws.11/dn303424%28v=ws.11%29). The Device Registration Service provides an onboarding mechanism for seamless second factor authentication, persistent single sign-on (SSO), and conditional access to consumers that require access to company resources. For more information about DRS, see [Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications](../operations/join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications)

## Prepare your Active Directory forest to support devices

Note

This is a one-time operation that you must run to prepare your Active Directory forest to support devices. You must be logged on with enterprise administrator permissions and your Active Directory forest must have the Windows Server 2012 R2 schema to complete this procedure.

Additionally, DRS requires that you have at least one global catalog server in your forest root domain. The global catalog server is required in order to run Initialize-ADDeviceRegistration and during AD FS authentication. AD FS initializes an in-memory representation of the DRS config object on each authentication request and if the DRS config object cannot be found on a DC in the current domain, the request is attempted against the GC on which the DRS objects were provisioned during Initialize-ADDeviceRegistration.

#### To prepare the Active Directory forest

1. On your federation server, open a Windows PowerShell command window and type:

    ```
    Initialize-ADDeviceRegistration
    ```
2. When prompted for ServiceAccountName, enter the name of the service account you selected as the service account for AD FS. If it is a gMSA account, enter the account in the **domain\accountname$** format. For a domain account, use the format **domain\accountname**.

## Enable Device Registration Service on a federation server farm node

Note

You must be logged on with domain administrator permissions to complete this procedure.

#### To enable Device Registration Service

1. On your federation server, open a Windows PowerShell command window and type:

    ```
    Enable-AdfsDeviceRegistration
    ```
2. Repeat this step on each federation farm node in your AD FS farm..

## Enable seamless second factor authentication

Seamless second factor authentication is an enhancement in AD FS that provides an added level of access protection to corporate resources and applications from external devices that are trying to access them. When a personal device is Workplace Joined, it becomes a 'known' device and administrators can use this information to drive conditional access and gate access to resources.

#### To enable seamless second factor authentication, persistent single sign-on (SSO) and conditional access for Workplace Joined devices

1. In the AD FS Management console, navigate to Authentication Policies. Select Edit Global Primary Authentication. Select the check box next to Enable Device Authentication, and then click OK.

## Update the Web Application Proxy configuration

Important

You do not need to publish the Device Registration Service to the Web Application Proxy. The Device Registration Service will be available through the Web Application Proxy once it is enabled on a federation server. You may need to complete this procedure to update the Web Application Proxy configuration if it was deployed prior to enabling the Device Registration Service.

#### To update the Web Application Proxy Configuration

1. On your Web Application Proxy server, open a Windows PowerShell command window and type

    ```
    Update-WebApplicationProxyDeviceRegistration
    ```
2. When prompted for credentials, enter the credentials of an account that has administrative rights to your federation servers.