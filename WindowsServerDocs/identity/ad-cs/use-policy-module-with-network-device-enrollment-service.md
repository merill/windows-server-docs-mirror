---
layout: Conceptual
title: Use a policy module with Network Device Enrollment Service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/use-policy-module-with-network-device-enrollment-service
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about the policy module and how it works. Understand how to install and uninstall the policy module for the Network Device Enrollment Service.
author: robinharwood
ms.topic: how-to
ms.author: roharwoo
ms.date: 2025-02-06T00:00:00.0000000Z
locale: en-us
document_id: 65df5414-f636-b0af-6f8c-b073133e2c16
document_version_independent_id: 65df5414-f636-b0af-6f8c-b073133e2c16
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/use-policy-module-with-network-device-enrollment-service.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/use-policy-module-with-network-device-enrollment-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/use-policy-module-with-network-device-enrollment-service.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: cbb43a6f-744e-9132-ed4d-3042cb8b6f9d
---

# Use a policy module with Network Device Enrollment Service | Microsoft Learn

The Active Directory Certificate Services (AD CS) Network Device Enrollment Service (NDES) support a policy module that provides extra security for the Simple Certificate Enrollment Protocol (SCEP). Without this policy module, when a user or a device requests a certificate, the SCEP requires either a unique or shared password. A rogue user using a legitimately obtained password could request a certificate that creates the following security risks:

- The subject name value matches a different user, allowing the rogue user to impersonate that other user.
- The user changes the certificate purpose, giving themselves elevated privileges.

When you use a policy module with the NDES, this module addresses these security risks by requiring extra authentication. For example, the module can verify that the requested certificate is for a specific user and for a specific purpose, and it can enforce whether to deploy a user certificate or computer certificate.

This article explains how the policy module works, and your deployment options.

## Process flow for a policy module and the Network Device Enrollment Service

Use a policy module to support enrolling user and computer certificates for mobile devices using cloud services. This scenario is also known as *over-the-air enrollment*. The following diagram shows an example process for a scenario where a mobile device administrator configures a certificate enrollment policy for mobile devices used by information workers.

![Diagram showing process flow after mobile device admin enrolls certificates.](../media/mobile-device-admin-config.png)

1. The mobile device management (MDM) software requests a challenge password from the NDES.

    Note

    The MDM software contacts the NDES mscep\_admin interface.
2. The NDES delegates the challenge password request to the policy module.
3. The policy module creates a challenge password that requires that the certificate request includes the user, purpose, and type of certificate (user or computer), and then sends this instruction to the NDES.
4. When the mobile device management software receives the challenge password, this software sends the uniform resource indicator (URI) for contacting the NDES and the challenge password to the mobile device.
5. The mobile device contacts the NDES to enroll a certificate.
6. The NDES delegates the request to the policy module.
7. The policy module verifies the challenge password and certificate request. Then the policy module returns the result of the verification to the NDES. If the challenge password and certificate request aren't successfully verified, the NDES returns an error to the mobile device. If the verification is successful, the NDES forwards the request to the certification authority.
8. When the request is approved by the certification authority, the certificate is issued to the NDES.
9. The NDES sends the certificate to the mobile device.

## Deployment options for the Network Device Enrollment Service and a policy module

You can choose between the three deployment options when you use the NDES and the policy module. Deployment in:

- A separate forest
- An isolated network
- An internal domain

### Deployment in a separate forest

You can create a new forest that covers the server running the NDES, the policy module, and the issuing certificate authority (CA). This design creates a security boundary from your internal domain controllers and domain accounts on the intranet, thereby reducing the risk of exposure. This deployment design is the most secure but requires more infrastructure to support more computers in another forest.

Note

When you install the NDES on a domain member, you must also install an issuing CA in the same domain. If you install the NDES on a workgroup computer, you must install the issuing CA on the same computer.

This design helps protect the internal network by isolating the domain and forest accounts you use on the perimeter network and the internal network. Because the issuing CA on the perimeter network is subordinate to the root CA, the system trusts the certificates it issues in both the perimeter and internal networks. If the perimeter network is compromised, you can use the root CA to revoke the certificate of the issuing CA in the perimeter network, which invalidates all certificates from the issuing CA in the perimeter network. Once you resolve the safety issue, you can rebuild the perimeter network and issue new certificates.

### Deployment in an isolated network

This deployment design offers a compromise between the most and least secure designs. You still need to change some infrastructure and configurations, but you don't need to create a separate forest.

This deployment design requires a single computer to run the NDES and the mobile device management solution. This computer is a member of the internal domain, so you don't have to install a separate issuing CA. You attach the computer running the NDES and the mobile device management solution by using a VPN or DirectAccess connection, which provides the isolated network environment. Mobile devices authenticate to the mobile device management software entering a username and password before they can get the certificate that lets them access resources on the internally secured wireless network.

In this design, there's a possibility that the server running the NDES and the mobile device management solution are at risk from attackers to compromise the internal network. To help mitigate this risk, use a temporary Domain Admin or Enterprise Admin account to install and configure the server running the NDES in the internal domain. Once you're finished, delete the temporary account, then move the server to the isolated network. Use extra security controls to protect this server and monitor it carefully for suspicious activity or signs that it might be compromised.

### Deployment on an internal domain

This deployment design is the least secure, but it lets you use your existing internal domain structure to deploy your enrollment solution.

In this design, the NDES isn't isolated and is a member of the internal domain. The mobile device management software must authenticate all requests for certificates from the wireless network. For example, the software might prompt users for username and password to authenticate them.

This deployment design doesn't use a security boundary when you connect the wireless network that issues certificates to the internal domain. In this scenario, an attacker could potentially use the external wireless network directly to try to compromise the internal domain. If you use this design, all computers on the internal network become potential targets for attack if the wireless network is compromised, so make sure that you use extra security controls to protect the entire internal network and all computers. Monitor your devices carefully for suspicious activity or signs that they might be compromised.