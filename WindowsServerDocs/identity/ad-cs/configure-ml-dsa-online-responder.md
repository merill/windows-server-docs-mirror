---
layout: Conceptual
title: Configure Online Responders (OCSP) to use ML-DSA in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/configure-ml-dsa-online-responder
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to configure ML-DSA post-quantum OCSP response signing in Active Directory Certificate Services (AD CS) for certificate revocation checking.
author: robinharwood
ms.topic: how-to
ms.author: roharwoo
ms.reviewer: Tjha
ms.date: 2026-05-12T00:00:00.0000000Z
ai-usage: ai-generated
locale: en-us
document_id: c2463625-3cca-52fe-d6cf-3b96c7d77273
document_version_independent_id: c2463625-3cca-52fe-d6cf-3b96c7d77273
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/configure-ml-dsa-online-responder.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/configure-ml-dsa-online-responder
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/configure-ml-dsa-online-responder.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e2b867db-eee4-8e9a-01f7-e9c919b4f717
---

# Configure Online Responders (OCSP) to use ML-DSA in Windows Server | Microsoft Learn

This article describes how to configure an Online Responder (OCSP) to sign responses by using Module-Lattice-Based Digital Signature Algorithm (ML-DSA) in Active Directory Certificate Services (AD CS). When you configure OCSP with ML-DSA, you enable revocation checking for certificates by using post-quantum signed responses.

## Prerequisites

- A Subordinate CA configured with ML-DSA and issuing certificates. See [Configure a certification authority to use ML-DSA](configure-ml-dsa-certification-authority).
- A domain-joined member server for the Online Responder, running Windows Server 2025 with the 2026-05 Security update ([KB5087539](https://support.microsoft.com/help/5087539)) or later installed. Ensure that the Online Responder role service is installed on this server. The installation steps are the same as for any Online Responder deployment. For detailed guidance, see [Implementing an OCSP Responder: Configuring OCSP for use with Enterprise CAs](https://techcommunity.microsoft.com/blog/askds/implementing-an-ocsp-responder-part-iii---configuring-ocsp-for-use-with-enterpri/396584).
- An account with permissions to install and configure AD CS role services.
- Membership in **Domain Admins** or equivalent to manage certificate templates.

## Create an OCSP Response Signing template with ML-DSA

Before configuring the OCSP responder, create an OCSP Response Signing certificate template that uses ML-DSA.

1. Open the **Certificate Templates** console on a machine with AD CS management tools installed.
2. Right-click the **OCSP Response Signing** template, and then select **Duplicate Template**.
3. On the **General** tab, enter a **Template display name** (for example, *PQC OCSP Response Signing*).
4. On the **Cryptography** tab:

    - Set **Provider Category** to **Key Storage Provider**.
    - Set **Algorithm name** to the desired ML-DSA parameter set (for example, **ML-DSA:65**).
    - The **Minimum key size** and **Request hash** fields update automatically.

    ![Screenshot of the OCSP Response Signing template Cryptography tab with Provider Category set to Key Storage Provider and Algorithm name set to ML-DSA:65.](media/configure-ml-dsa-online-responder/ocsp-template-cryptography-ml-dsa-65.png)
5. On the **Security** tab, grant **Enroll** and **Autoenroll** permissions to the computer account of the OCSP responder.
6. Select **OK** to save the template.
7. In the **Certification Authority** console on the Subordinate CA configured with ML-DSA, right-click **Certificate Templates**, select **New** &gt; **Certificate Template to Issue**, and then select the template you created.

## Configure the OCSP revocation provider

The revocation provider configuration is where ML-DSA-specific settings apply. You associate the Online Responder with your ML-DSA Subordinate CA and specify the ML-DSA signing certificate template.

1. Open the **Online Responder Management** console (`ocsp.msc`).
2. Right-click **Revocation Configuration** and select **Add Revocation Configuration**.
3. On the **Name the Revocation Configuration** page, enter a name (for example, *PQC SubCA OCSP*).
4. On the **Select CA Certificate Location** page, select **Select a certificate for an Existing enterprise CA**.
5. On the **Choose CA Certificate** page, select **Browse CA certificates published in Active Directory**, and then select the Subordinate CA configured with ML-DSA.
6. On the **Select Signing Certificate** page:

    - Select **Automatically select a signing certificate**.
    - Select **Auto-Enroll for an OCSP signing certificate**.
    - Set the **Certification authority** to the Subordinate CA configured with ML-DSA.
    - Set the **Certificate Template** to the ML-DSA OCSP Response Signing template you created (for example, *PQCOCSPResponseSigning*).

    ![Screenshot of the Select Signing Certificate page with auto-enroll selected and the PQCOCSPResponseSigning template chosen.](media/configure-ml-dsa-online-responder/select-signing-certificate.png)
7. Select **Finish** to complete the configuration.
8. In the **Online Responder Management** console, under **Array Configuration**, verify that the **Revocation Configuration Status** shows:

    - **Signing Certificate**: OK
    - **Revocation Provider Status**: The ML-DSA revocation provider is successfully configured.

    ![Screenshot of the Online Responder Management console showing Signing Certificate OK and successful revocation provider status.](media/configure-ml-dsa-online-responder/revocation-configuration-status.png)

## Update the AIA extension on the subordinate CA

To direct clients to use the OCSP responder for ML-DSA certificate revocation checking, add the OCSP URL to the Authority Information Access (AIA) extension on the subordinate CA.

1. On the subordinate CA, open the **Certification Authority** console (`certsrv.msc`).
2. Right-click the CA name and select **Properties**.
3. On the **Extensions** tab, select **Authority Information Access (AIA)** from the dropdown.
4. Select **Add** and enter the OCSP responder URL (for example, `http://<ocsp-server-fqdn>/ocsp`).
5. Check **Include in the online certificate status protocol (OCSP) extension**.
6. Clear **Include in the AIA extension of issued certificates** for the OCSP URL entry.

    ![Screenshot of the CA Properties Extensions tab showing the Authority Information Access extension with the OCSP responder URL added.](media/configure-ml-dsa-online-responder/aia-extension-properties.png)
7. Select **OK** and restart the CA service when prompted.

Important

The AIA extension change applies only to certificates issued after the change. Previously issued certificates continue to reference the original AIA locations.

## Validate ML-DSA OCSP responses

After configuration, verify that the OCSP responder correctly returns ML-DSA signed responses.

### Verify by using `certutil`

1. Enroll for a test certificate from the Subordinate CA by using an ML-DSA template. Export the certificate to a `.cer` file.
2. Run the following command to check the revocation status:

    ```cmd
    certutil -verify -urlfetch <certificate-file>.cer
    ```
3. In the output, look for the **Certificate OCSP** section. A valid certificate shows:

    ```output
    Verified "OCSP" Time: 0
    ```
4. To verify the responder correctly identifies revoked certificates, revoke the certificate on the issuing CA, publish a new certificate revocation list (CRL), and then run the same command. A revoked certificate shows:

    ```output
    Revoked "OCSP" Time: 0
    ```

### Verify the ML-DSA signature

To confirm the OCSP response uses an ML-DSA signature, inspect the signing certificate in the **Online Responder Management** console:

1. Open `ocsp.msc` on the OCSP responder server.
2. Select the revocation configuration, and then select **View Signing Certificate**.
3. On the **Details** tab, confirm the **Public key** field shows the ML-DSA parameter set and key size.
4. The **Signature algorithm** shows the issuing CA's ML-DSA parameter set, confirming the ML-DSA CA issued the signing certificate.