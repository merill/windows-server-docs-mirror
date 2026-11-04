---
layout: Conceptual
title: Improved interoperability with SAML 2.0 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/improved-interoperability-with-saml-2.0
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Improved interoperability with SAML 2.0'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: ae507a19-3f9e-56be-609e-de0428f89c56
document_version_independent_id: 35f3b756-467d-587a-fee6-c225d4fa8a3f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Improved-interoperability-with-SAML-2.0.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/improved-interoperability-with-saml-2.0
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Improved-interoperability-with-SAML-2.0.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c7fab23f-87a9-5a44-42b6-a00be47fbde5
---

# Improved interoperability with SAML 2.0 | Microsoft Learn

AD FS in Windows Server 2016 contains additional SAML protocol support, including support for importing trusts based on metadata that contains multiple entities. This enables you to configure AD FS to participate in confederations such as InCommon Federation and other implementations conforming to the eGov 2.0 standard.

The new capability is based on groups of relying party or claims provider trusts. Each group is an EntitiesDescriptor (&lt;md:EntitiesDescriptor&gt;) element as specified in the eGov 2.0 profile, containing one or many EntityDescriptor elements. The groups have common authorization rules, and all other properties can be modified like individual trust objects.

Once the trust groups are imported into AD FS, AD FS automatically updates the trusts as a group based on the metadata document.

Enabling these scenarios is as simple as using the new PowerShell commandlets that Add and Remove AdfsClaimsProviderTrustsGroup and AdfsRelyingPartyTrustsGroup objects. This can be done using a metadata URL or a file, as shown in the examples below.

Additionally, AD FS 2016 has support for the scoping parameter as described in the SAML Core specification, section 3.4.1.2. This element allows relying parties to specify one or more identity providers for an authentication request.

## Examples

```
Add-AdfsClaimsProviderTrustsGroup -MetadataUrl "https://www.contosoconsortium.com/metadata/metadata.xml"
```

```
Add-AdfsClaimsProviderTrustsGroup -MetadataFile "C:\metadata.xml"
```

## References

You can find the eGov 2.0 profile [here](https://kantarainitiative.github.io/SAMLprofiles/eGovImplProfile.html).

The SAML Core specification can be found [here.](https://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf)