---
layout: Conceptual
title: AD FS prompt=login | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/ad-fs-prompt-login
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn about the native support for the prompt=login parameter that is available in AD FS.
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
ms.custom: it-pro, has-azure-ad-ps-ref, azure-ad-ref-level-one-done
locale: en-us
document_id: 0eaa668f-880c-8415-17bb-8169fe23fd26
document_version_independent_id: fe5d3e99-46fc-6daf-a8af-5b0653d500f7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/AD-FS-Prompt-Login.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/ad-fs-prompt-login
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/AD-FS-Prompt-Login.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0fcf92b4-04c1-df7e-f1c4-a43fe78498e7
---

# AD FS prompt=login | Microsoft Learn

The following document describes the native support for the prompt=login parameter that is available in AD FS.

## What is prompt=login?

When applications need to request fresh authentication from Microsoft Entra ID, meaning that they need Microsoft Entra ID to re-authenticate the user even if the user has already been authenticated, they can send the `prompt=login` parameter to Microsoft Entra ID as part of the authentication request.

When this request is for a federated user, Microsoft Entra ID needs to inform the IdP, like AD FS, that the request is for fresh authentication.

By default, Microsoft Entra ID translates `prompt=login` to `wfresh=0` and `wauth=https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password` when sending this type of authentication requests to the federated IdP.

These parameters mean:

- `wfresh=0`: do fresh authentication
- `wauth=https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`: use username/password for the fresh authentication request

This can cause problems with corporate intranet and multi-factor authentication scenarios in which an authentication type other than username and password, as requested by the `wauth` parameter, is desired.

AD FS in Windows Server 2012 R2 with the July 2016 update rollup introduced native support for the `prompt=login` parameter. This means that now Microsoft Entra ID can send this parameter as-is to AD FS service as part of Microsoft Entra ID and Office 365 authentication requests.

## AD FS versions that support prompt=login

The following is a list of AD FS versions that support the `prompt=login` parameter.

- AD FS in Windows Server 2012 R2 with the July 2016 update rollup
- AD FS in Windows Server 2016 or later

## How to configure a federated domain to send prompt=login to AD FS

Use the [Microsoft Graph PowerShell](/en-us/powershell/microsoftgraph/installation) module to configure the setting.

1. First obtain the current values of `FederatedIdpMfaBehavior`, `PreferredAuthenticationProtocol`, and `PromptLoginBehavior` for the federated domain by running the following PowerShell command:

    ```powershell
    Get-MgDomainFederationConfiguration -DomainId <your_domain_name> | Format-List *
    ```

    Note

    The output of `Get-MgDomainFederationConfiguration` by default does not display certain properties in the console. To view all the properties you should pipe (`|`) its output to `Format-List *` to force the output of all the properties of the object.

    If the value of the property `PromptLoginBehavior` is empty (`$null`) the behavior of `TranslateToFreshPasswordAuth` is used.
2. Configure the desired value of `PromptLoginBehavior` by running the following command:

    ```powershell
    New-MgDomainFederationConfiguration -DomainId <your_domain_name> `
       -FederatedIdpMfaBehavior <current_value_from_step1> `
       -PreferredAuthenticationProtocol <current_value_from_step1> `
       -PromptLoginBehavior <TranslateToFreshPasswordAuth|nativeSupport|Disabled>
    ```

Following are the possible values of `PromptLoginBehavior` parameter and their meaning:

- **TranslateToFreshPasswordAuth**: means the default Microsoft Entra behavior of translating `prompt=login` to `wauth=https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password` and `wfresh=0`.
- **nativeSupport**: means that the `prompt=login` parameter will be sent as is to AD FS. This is the recommended value if AD FS is in Windows Server 2012 R2 with the July 2016 update rollup or higher.
- **Disabled**: means that only `wfresh=0` is sent to AD FS.