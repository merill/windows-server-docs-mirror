---
layout: Conceptual
title: Troubleshooting Windows volume activation | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/activation-troubleshooting-guide
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Lists resources that provide information about best practices for volume activation, and information about troubleshooting activation issues
ms.topic: troubleshooting
ms.date: 2019-09-24T00:00:00.0000000Z
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 394bc2ad-a15e-6963-17f9-efee2b2b0518
document_version_independent_id: 67f14fb2-16be-3f1e-0f83-72362361d089
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/activation-troubleshooting-guide.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/activation-troubleshooting-guide
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/activation-troubleshooting-guide.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 85a67ca7-037c-0c80-1eac-cfed7f19559a
---

# Troubleshooting Windows volume activation | Microsoft Learn

Product activation is the process of validating software after it's installed on a specific computer. Activation confirms that the product is genuine (not a fraudulent copy) and that the product key or serial number is valid and has not been compromised or revoked. Activation also establishes a link or relationship between the product key and the installation.

Volume activation is the process of activating volume-licensed products. To become a volume licensing customer, an organization must set up a volume licensing agreement with Microsoft. Microsoft offers customized volume licensing programs that accommodate the organization's size and purchasing preference. For more information, see the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).

The [Windows Server 2016 Activation Guide](server-2016-activation) focuses on the Key Management Service (KMS) activation technology. This section addresses common issues and provides troubleshooting guidelines for KMS and several other volume activation technologies.

## Best practices for volume activation

The following articles provide technical information and best practices for Microsoft's volume activation technologies.

### Key Management Service (KMS)

- [Plan for volume activation](/en-us/windows/deployment/volume-activation/plan-for-volume-activation-client)
- [Understanding KMS](/en-us/previous-versions/tn-archive/ff793434%28v=technet.10%29)
- [Deploying KMS Activation](/en-us/previous-versions/tn-archive/ff793409%28v=technet.10%29)
- [Configuring KMS Hosts](/en-us/previous-versions/tn-archive/ff793407%28v%3dtechnet.10%29)
- [Configuring DNS](/en-us/previous-versions/tn-archive/ff793405%28v%3dtechnet.10%29)
- [Activate using Key Management Service](/en-us/windows/deployment/volume-activation/activate-using-key-management-service-vamt)

### Active Directory-based activation (ADBA)

- [Deploy Active-Directory-based Activation](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn502534%28v%3dws.11%29)
- [Activate using Active Directory-based activation](/en-us/windows/deployment/volume-activation/activate-using-active-directory-based-activation-client)
- [Active Directory-Based Activation overview](/en-us/windows/deployment/volume-activation/active-directory-based-activation-overview)

### Multiple Activation Key (MAK) activation

- [Using MAK Activation](/en-us/previous-versions/tn-archive/ff793438%28v=technet.10%29)
- [Understanding MAK Activation](/en-us/previous-versions/tn-archive/ff793435%28v%3dtechnet.10%29)
- [Activating MAK Clients](/en-us/previous-versions/tn-archive/ff793398%28v%3dtechnet.10%29)

### Subscription activation

- [Windows 10 Subscription Activation](/en-us/windows/deployment/windows-10-subscription-activation)
- [Deploy Windows 10 Enterprise licenses](/en-us/windows/deployment/deploy-enterprise-licenses)
- [Windows 10 Enterprise E3 in CSP](/en-us/windows/deployment/windows-10-enterprise-e3-overview)

## Resources for troubleshooting activation issues

The following articles provide guidelines and information about tools for troubleshooting volume activation issues:

- [Guidelines for troubleshooting the Key Management Service (KMS)](activation-troubleshoot-kms-general)
- [Slmgr.vbs options for obtaining volume activation information](activation-slmgr-vbs-options)
- [Example: Troubleshooting ADBA clients that do not activate](activation-troubleshoot-adba-clients)

The following articles provide guidance for addressing more specific activation issues:

- [Resolving common activation error codes](activation-error-codes)
- [KMS activation: known issues](activation-troubleshoot-kms-issues)
- [MAK activation: known issues](activation-troubleshoot-mak-issues)
- [Guidelines for troubleshooting DNS-related activation issues](common-troubleshooting-procedures-kms-dns)
- [How to rebuild the Tokens.dat file](activation-rebuild-tokens-dat-file)