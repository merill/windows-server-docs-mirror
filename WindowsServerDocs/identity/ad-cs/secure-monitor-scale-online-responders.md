---
layout: Conceptual
title: Secure and Scale AD CS Online Responders - Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/secure-monitor-scale-online-responders
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Keep AD CS Online Responders protected and available on Windows Server 2025 by managing OCSP signing certificates, renewal, monitoring, and scale-out.
author: Orin-Thomas
ms.author: orthomas
ms.topic: how-to
ms.date: 2026-08-17T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 267ef0fa-a48d-36b8-293b-37617140f652
document_version_independent_id: 267ef0fa-a48d-36b8-293b-37617140f652
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/secure-monitor-scale-online-responders.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/secure-monitor-scale-online-responders
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/secure-monitor-scale-online-responders.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
platformId: 6739091e-d915-f221-1860-15e3ac225c95
---

# Secure and Scale AD CS Online Responders - Windows Server | Microsoft Learn

An Online Responder answers real-time queries about whether a certificate is still valid or revoked, by using the Online Certificate Status Protocol (OCSP). It signs each status response, so clients across your organization depend on its signing certificate, certificate revocation list (CRL) availability, and endpoint configuration staying available and trustworthy.

After you deploy a responder, the routine operations that keep certificate validation working are securing the service, monitoring client results, renewing the signing certificate, and adding capacity. This article describes how to perform those operations for an Active Directory Certificate Services (AD CS) Online Responder after you deploy and validate its initial revocation configuration.

This article covers the conventional enterprise-template deployment: independently configured responder instances behind external traffic distribution. It deliberately doesn't prescribe legacy array operations, and it doesn't reproduce the initial ML-DSA deployment procedure. The **Scale availability without assuming array support** section later in this article explains the reasons behind the traffic-distribution approach.

## Prerequisites

Before making an operational change, have the following:

- A responder that passes the good-certificate and revoked-certificate validation described in [Deploy and validate an Online Responder](configure-ml-dsa-online-responder).
- A test certificate issued by every certification authority (CA) represented in the responder configuration and a documented test client network for each client population.
- A change record containing the current responder URL, issuing CA, signing-template name, signing-certificate thumbprint, and revocation-data retrieval paths.
- A separate management account or group for responder administration, separate from CA and certificate-template administration where your authorization model allows it.
- A rollback plan that retains the last known working signing certificate and revocation-data source until the replacement configuration passes end-to-end validation.

## Security considerations

Use least privilege and make each administrator's scope explicit. A responder operator shouldn't automatically receive authority to change CA issuance policy, publish a template, or modify the public endpoint.

- Review the OCSP response-signing template security. Limit **Read**, **Enroll**, and **Autoenroll** to the responder computer accounts that need a signing certificate.
- Keep the signing certificate limited to the OCSP signing purpose. Don't use it for server authentication, user authentication, encryption, or enrollment-agent tasks.
- Restrict access to the responder host and its private-key material under your privileged-access policy. Use a managed administration path and record every configuration change in the same change system as CA changes.
- Review the public endpoint separately from the responder. Restrict inbound access to the service URL as your client population requires, but don't expose the responder management interface to untrusted networks.
- Preserve current certificate and configuration evidence before changing the signing template, revocation configuration, or URL.

Note

The Server Core installation option includes the **Online Responder** role service, but not the AD CS management tools that provide `ocsp.msc`. Microsoft doesn't currently document a remote-management configuration for Online Responder Management on Windows Server 2025, including firewall rules, DCOM or RPC settings, or a supported way to point `ocsp.msc` at a remote responder. Run the console from an approved hardened session on a responder that has the management tools installed, or validate a remote-management design in a production-equivalent lab first. Don't enable historical firewall rules or DCOM settings solely because they appeared in an earlier Windows Server release.

## Monitor the Online Responder configuration, client results, and revocation data

Monitor the service at three layers: the local configuration, actual client results, and the revocation information that the configuration depends on. A healthy console status alone doesn't prove that every client can reach the published URL.

### Review local configuration status

On each responder, open `ocsp.msc`, select each revocation configuration under **Array Configuration**, and record the following:

- **Signing Certificate** status and the certificate expiration date.
- **Revocation Provider Status**.
- The issuing CA and signing-template selection.
- Any change in the configured responder URL or the CA certificate that the configuration uses.

Alert before the signing certificate reaches the renewal window that your certificate policy defines. Establish the lead time from the documented enrollment, approval, and rollback time for your environment rather than from a universal number.

### Test from client networks

Run a good-status and revoked-status test from every distinct client network or egress path that relies on the responder. Use a newly issued certificate so that its OCSP extension reflects the current CA configuration.

```cmd
certutil -verify -urlfetch .\ocsp-good.cer
certutil -verify -urlfetch .\ocsp-revoked.cer
```

For each test, verify that the output includes a `Certificate OCSP` section with a `Verified "OCSP"` result for the valid certificate and a `Revoked "OCSP"` result for the revoked certificate. A successful CRL retrieval is useful evidence for the CA publication path, but it isn't a substitute for a verified OCSP result.

### Monitor revocation-data freshness

For each issuing CA, monitor when it publishes revocation information and test retrieval from the responder's network. A CA's CRL distribution point (CDP) design can include both HTTP and LDAP locations, and [Windows clients retrieve the list of URLs in sequential order](pki-design-considerations#authority-information-access-and-certificate-revocation-list-distribution-point-settings) until they retrieve a valid CRL. Validate the actual locations that your CA certificates contain, in the order they appear.

When you investigate a stale or failed response, preserve these facts before changing the configuration:

- The exact end-entity certificate, its serial number, and the issuing CA certificate.
- The responder's signing-certificate status and expiration date.
- The time when the CA last published the relevant base or delta CRL.
- The responder-side and client-side result for the same certificate.
- DNS and network access to each publication location from the affected network.

Microsoft doesn't currently document Online Responder-specific local-CRL cache settings or web-proxy tuning for Windows Server 2025. Don't set historical cache size, thread, local-CRL, or proxy properties as a default. If your network requires a proxy, test the complete CA-to-responder-to-client path under your approved proxy configuration, including failure behavior and authentication requirements.

### Collect operational evidence

Forward service availability, operating system security, and change management telemetry from each responder to your central monitoring system.

The **Audit Certification Services** advanced audit policy generates events when AD CS operations occur, including when the OCSP Responder Service starts or stops. Its documented event volume is medium or low on servers that host AD CS role services. Enable it through your approved audit policy process, and configure request-level web logging separately: a status service can receive high request volumes, so a design that records every request can create an operational load of its own.

At a minimum, make these events and observations searchable together:

- Responder service starts, stops, and unexpected restarts.
- Authorized configuration and signing-certificate changes.
- Certificate-enrollment failures for the responder computer account.
- Repeated client validation failures, response latency changes, and endpoint reachability failures.
- A change in revocation-provider status or a signing certificate nearing expiration.

Test your selected audit and event-forwarding policy on patched Windows Server 2025 before relying on it. For subcategory descriptions and the AD CS event list, see [Advanced audit policy configuration](../ad-ds/plan/security-best-practices/advanced-audit-policy-configuration).

## Renew an OCSP response-signing certificate

Use autoenrollment for the enterprise responder configuration whenever possible. By using autoenrollment, the responder can get a new template-based signing certificate without exporting the private key.

1. Before the current signer expires, check the signing-template permissions and confirm that the responder computer still has the intended enrollment rights.
2. In `ocsp.msc`, review the revocation configuration and confirm that **Automatically select a signing certificate** and **Auto-Enroll for an OCSP signing certificate** remain selected for the expected issuing CA and template.
3. Allow the responder to get the replacement certificate through the approved enrollment process.
4. Confirm that **Signing Certificate** reports **OK**, select **View Signing Certificate**, and inspect the certificate's issuer, public key, signature algorithm, extended key usage (EKU), validity dates, and thumbprint. Note whether the certificate contains the `id-pkix-ocsp-nocheck` extension.
5. Run the good-certificate and revoked-certificate tests from a client network.
6. Keep the prior signing certificate and the documented last known working configuration until the new signer passes validation and your rollback window closes.
7. Remove retired private keys and certificates only through your approved certificate-retirement process.

Caution

Plan CA certificate and CA-key renewal together with responder signing-certificate renewal. RFC 6960 requires a delegated signer to carry the OCSP Signing EKU, and it requires the CA that issued the checked certificate to issue the signer directly. Relying systems recognize the delegation only when the same CA key signed both the signer certificate and the checked certificate. The RFC also permits a relying party to use a locally configured signing authority, so don't assume that exception applies to your clients. Don't apply undocumented registry workarounds to force clients to accept a signer after a key change. Instead, stage the CA renewal and validate signer behavior for certificates issued under each CA key before production cutover.

## Scale availability without assuming array support

Separate service availability from responder-configuration replication.

Important

Current Windows Server 2025 guidance shows the **Array Configuration** node in Online Responder Management, but it doesn't document supported Windows Server 2025 procedures for creating an array, designating an array controller, adding or removing members, or synchronizing members. Don't use archived array procedures as a production runbook. This article covers independently configured responder instances behind external traffic distribution and deliberately doesn't prescribe those legacy array operations.

An external DNS or load-balancing design decides which responder receives an HTTP request. It doesn't create, synchronize, or validate an Online Responder configuration. Conversely, a successful local configuration on one responder doesn't prove that another responder has the expected signing certificate and revocation-data status.

Use this procedure to add an independently validated responder instance:

1. Deploy the additional Windows Server 2025 responder by using the procedure in [Deploy and validate an Online Responder](configure-ml-dsa-online-responder).
2. Configure the same issuing CA and approved signing template on the new instance.
3. Validate its signing-certificate and revocation-provider status in `ocsp.msc`.
4. Run good and revoked certificate tests directly against the new instance from each intended client network.
5. Add the instance to your external traffic-distribution mechanism only after the direct tests pass.
6. Test one-instance withdrawal from traffic, a responder restart, a stale revocation-data scenario, a signer-expiration scenario, and restoration to service.
7. Record how the traffic-distribution system evaluates endpoint health. Use an OCSP-aware test rather than a TCP-only check as the release gate where your load balancer supports it.

Don't claim that external load balancing provides configuration replication, member synchronization, or automatic signer consistency. Establish those capabilities only after Microsoft documents them for your Windows Server 2025 deployment and you've tested them.

## Retire a responder or revocation configuration

Retiring a responder is a certificate-lifecycle change, not only a server change.

1. Inventory unexpired certificates that contain the responder URL and identify the CA that issued each certificate.
2. Publish and validate the replacement URL on the issuing CA before it issues replacement certificates.
3. Reissue or replace affected certificates according to their business lifecycle. Remember that existing certificates retain their older OCSP extension.
4. Keep the old responder URL available until the final affected certificate expires, you replace it, or it has an approved exception.
5. Remove the responder from external traffic distribution only after all dependency checks pass.
6. Preserve the final validation output and configuration record before deleting a revocation configuration or retiring the server.

## Troubleshoot operational changes

| Symptom | Investigation and safe response |
| --- | --- |
| The responder doesn't select a new signing certificate. | Check the selected CA and template, template enrollment permissions, certificate validity, and the status in `ocsp.msc`. Keep the prior signer in place until the replacement succeeds. |
| Clients receive different results through different responders. | Remove the inconsistent responder from external traffic distribution, test it directly, compare its signing-certificate and revocation-provider status with the known-good instance, and return it only after good and revoked tests agree. |
| Revocation information is stale or unavailable. | Confirm CA publication first, then test each HTTP or LDAP retrieval path from the responder and client networks. Avoid changing cache or proxy settings based on legacy guidance. |
| A remote management connection fails. | Use an approved local management session while you validate identity, firewall, protocol, and authorization behavior in a test environment. Don't open broad DCOM/RPC access as a troubleshooting shortcut. |
| The public endpoint is healthy but OCSP validation fails. | Test a newly issued certificate directly against the endpoint, inspect the certificate's OCSP extension, and verify the responder's signing-certificate and revocation-provider statuses. A basic transport health check doesn't validate OCSP. |