---
layout: Conceptual
title: Home Realm Discovery Customization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/home-realm-discovery-customization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Home Realm Discovery Customization'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 981e5a8a-d352-6c4e-ba9b-7b914c9379ef
document_version_independent_id: a97653cb-16f5-2410-b4e4-adda13ec8b5c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Home-Realm-Discovery-Customization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/home-realm-discovery-customization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Home-Realm-Discovery-Customization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: f8de82e2-1b56-5038-ad6e-e43d6c171c7b
---

# Home Realm Discovery Customization | Microsoft Learn

When the AD FS client first requests a resource, the resource federation server has no information about the realm of the client. The resource federation server responds to the AD FS client with a **Client Realm Discovery** page, where the user selects the home realm from a list. The list values are populated from the display name property in the Claims Provider Trusts. Use the following Windows PowerShell cmdlets to modify and customize the AD FS Home Realm Discovery experience.

![home realm](media/ad-fs-user-sign-in-customization/adfs_blue_custom4.png)

Warning

Be aware that the Claims Provider name that shows up for local Active Directory is the federation service display name.

## Configure Identity Provider to use certain email suffixes

An organization can federate with multiple claims providers. AD FS now provides the in-box capability for administrators to list the suffixes, for example, @us.contoso.com, @eu.contoso.com, that is supported by a claims provider and enable it for suffix-based discovery. With this configuration, end users can type in their organizational account, and AD FS automatically selects the corresponding claims provider.

To configure an identity provider (IDP), such as `fabrikam`, to use certain email suffixes, use the following Windows PowerShell cmdlet and syntax.

`Set-AdfsClaimsProviderTrust -TargetName fabrikam -OrganizationalAccountSuffix @("fabrikam.com";"fabrikam2.com") `

Note

When federating between two AD FS servers, set PromptLoginFederation property on the claims provider trust to ForwardPromptAndHintsOverWsFederation. This is so that AD FS will forward the login\_hint and prompt parmeter to the IDP. This can be done by running the following PowerShell cmdlet:

`Set-AdfsclaimsProviderTrust -PromptLoginFederation ForwardPromptAndHintsOverWsFederation`

## Configure an identity provider list per relying party

For some scenarios, an organizations might want end users to only see the claims providers that are specific to an application so that only a subset of claims provider are displayed on the home realm discovery page.

To configure an IDP list per relying party (RP), use the following Windows PowerShell cmdlet and syntax.

`Set-AdfsRelyingPartyTrust -TargetName claimapp -ClaimsProviderName @("Fabrikam","Active Directory") `

## Bypass Home Realm Discovery for the intranet

Most organizations only support their local Active Directory for any user who accesses from inside their firewall. In those cases, administrators can configure AD FS to bypass home realm discovery for the intranet.

To bypass HRD for the intranet, use the following Windows PowerShell cmdlet and syntax.

`Set-AdfsProperties -IntranetUseLocalClaimsProvider $true `

Important

Please note that if an identity provider list for a relying party has been configured, even though the previous setting has been enabled and the user accesses from the intranet, AD FS still shows the home realm discovery (HRD) page. To bypass HRD in this case, you have to ensure that "Active Directory" is also added to the IDP list for this relying party.

## Additional references

[AD FS User Sign-in Customization](ad-fs-user-sign-in-customization)