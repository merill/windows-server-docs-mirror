---
layout: Conceptual
title: Manage Certificate Stores in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/inspect-certificates-manage-certificate-stores
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Inspect certificate stores and safely import or export public certificates on Windows Server 2025, including user, computer, service, logical, and physical stores.
author: Orin-Thomas
ms.author: orthomas
ms.topic: how-to
ms.date: 2026-08-17T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 033fff68-61f9-fb0b-4cdf-a40d06204341
document_version_independent_id: 033fff68-61f9-fb0b-4cdf-a40d06204341
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/inspect-certificates-manage-certificate-stores.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/inspect-certificates-manage-certificate-stores
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/inspect-certificates-manage-certificate-stores.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d79cb62f-d88d-87c1-77b7-af36f1d66728
---

# Manage Certificate Stores in Windows Server | Microsoft Learn

Certificate stores are the system locations where Windows keeps the certificates that users, the computer, and services rely on to authenticate identities and encrypt communication. A certificate that's in the wrong store, expired, or missing a trusted chain can cause applications to fail, and an incorrect change to a trusted root store can weaken security for the entire computer.

This article shows you how to inspect a certificate, its store scope, and its chain, and how to safely import and export public certificates, so that you can validate and change store contents with confidence. It uses the Certificates snap-in in Microsoft Management Console (MMC) and the PowerShell Certificate provider on Windows Server 2025.

This article covers local user, computer, and service-account stores. It doesn't duplicate Certification Authority Web Enrollment or Group Policy trust-distribution procedures.

## Prerequisites

- A Windows Server 2025 computer and the identity that owns the store you need to inspect.
- Permissions appropriate for the target store and action. Managing certificates and the Trusted Root Certification Authorities store typically requires administrator privileges, so use an elevated session for Local Computer and service-account stores.
- The certificate file and its expected issuer, purpose, and thumbprint when you import a public certificate.
- A separate, approved private-key export plan if you need a PFX (Personal Information Exchange) file.

Caution

Adding or removing a certificate in the **Local Computer** **Trusted Root Certification Authorities** store changes the set of root certification authorities (CAs) that the computer trusts and can affect applications that use it. A Current User root-store change applies to that user context. Improper changes to certificates and the Trusted Root Certification Authorities store can compromise the security of the system.

## Understand certificate-store scopes

Windows certificate system stores are collections that consist of one or more physical sibling stores. A certificate can therefore appear through a logical store without being a separate certificate copy in every view.

| Store scope | What it represents | How to inspect it |
| --- | --- | --- |
| Current user | Stores associated with the signed-in user. The Certificate provider exposes this location as `Cert:\CurrentUser`. | Run `certmgr.msc` or use the `Cert:\CurrentUser` path. |
| Local computer | Stores that are local to the computer and available to its users. The Certificate provider exposes this location as `Cert:\LocalMachine`. | Run `certlm.msc` or use the `Cert:\LocalMachine` path. |
| Service account | Stores associated with a named Windows service. Windows stores them beneath `...\Cryptography\Services\ServiceName\SystemCertificates`. | Add a **Certificates** snap-in for a **Service account**. |
| Logical store | A collection that presents certificates from one or more physical sibling stores. Standard store names include `MY`, `Root`, `Trust`, and `CA`. | Review the store scope and certificate thumbprint before changing an entry. |
| Physical store | An underlying sibling store in a system-store collection, such as a default, local-machine, policy, or enterprise location. | Use the [System Store Locations](/en-us/windows/win32/seccrypto/system-store-locations) reference when you need to identify the backing location. |

Current-user stores, except **Personal**, inherit the contents of the local-machine certificate stores. If a certificate appears more than once, compare its thumbprint and scope before you remove or replace it. See [Local Machine and Current User Certificate Stores](/en-us/windows-hardware/drivers/install/local-machine-and-current-user-certificate-stores).

Windows supports remote opening of local-machine, local-machine policy, service, and user system-store locations. Treat remote inspection as a separate management connection with its own authorization boundary; it isn't a substitute for interactive enrollment in the remote computer's context.

## Open the Certificates MMC snap-in

Use the following tools for the most common scopes:

- Run `certmgr.msc` to open the current-user certificate store.
- Run `certlm.msc` to open the local-computer certificate store.
- To choose a user, service, or computer scope explicitly, run `mmc` and complete these steps:

    1. Select **File** &gt; **Add/Remove Snap-in**.
    2. Select **Certificates**, then select **Add**.
    3. Select **My user account**, **Service account**, or **Computer account**.
    4. For a computer scope, select **Next** &gt; **Local computer: (the computer this console is running on)** &gt; **Finish**.
    5. Select **OK**.

After you add the Certificates snap-in for a computer account, the console tree shows **Certificates (Local Computer)**. To inspect machine roots, expand **Trusted Root Certification Authorities** and select **Certificates**.

## Inspect a certificate before changing it

1. Open the appropriate certificate store.
2. Locate the certificate in the store that the application uses, and then open it.
3. On the **Details** tab, record the certificate's subject, issuer, serial number, thumbprint, validity dates, subject alternative names, and intended application policy before you make a change.
4. On the **Certification Path** tab, inspect the complete path: the root and its trust status, any intermediate CAs, and the end-entity certificate.
5. Confirm that the intended application policy and identity match the application's documented requirements.

Use PowerShell for a read-only inventory:

```powershell
Get-ChildItem -Path Cert:\

Get-ChildItem -Path Cert:\CurrentUser\My

Get-ChildItem -Path Cert:\LocalMachine\My
```

The Certificate provider exposes certificate objects by thumbprint. To inspect a known certificate, replace `THUMBPRINT` with its actual value:

```powershell
$certificate = Get-Item -Path 'Cert:\LocalMachine\My\THUMBPRINT'
$certificate | Format-List DnsNameList, EnhancedKeyUsageList, HasPrivateKey, NotAfter, Subject, Thumbprint
```

For a server certificate, validate the SSL policy, DNS name, and revocation status with `Test-Certificate`:

```powershell
Get-ChildItem -Path Cert:\LocalMachine\My |
    Test-Certificate -Policy SSL -DNSName 'dns=server.contoso.com'
```

`Test-Certificate` checks revocation by default. A `True` result means the cmdlet passed the supplied policy in its chain context: machine by default, or current user when you use `-User`. It doesn't establish the relying application's trust configuration or replace an end-to-end application test.

## Show archived certificates in an MMC console

To show archived certificates in a local-computer MMC:

1. Add the local-computer **Certificates** snap-in.
2. Select **Certificates (Local Computer)**.
3. Select **View** &gt; **View Options**.
4. Select **Archived certificates**, and then select **OK**.

## Inspect certificate files and CRLs with certutil

For file-level troubleshooting, `certutil` can inspect a PKCS #7 certificate file and validate a certificate revocation list (CRL). `certutil` is an administrator and developer tool, not a production-code dependency.

```cmd
certutil -dump .\Incoming\chain.p7b

certutil -verify .\Incoming\issuer.crl .\Incoming\issuer-ca.cer
```

To retrieve certificate validation URLs while validating a certificate file, use:

```cmd
certutil -urlfetch -verify .\Incoming\server.cer
```

`-urlfetch` can contact the URLs that the certificate carries, so use it only from an approved troubleshooting environment. For supported syntax and file types, see [certutil](/en-us/windows-server/administration/windows-commands/certutil).

## Import a public certificate

`Import-Certificate` imports public certificate files with the `.sst`, `.p7b`, or `.cert` format. It doesn't import a PFX/private key.

1. Verify the file's expected issuer, thumbprint, and intended destination store.
2. Preview the destination with `-WhatIf`:

    ```powershell
    $params = @{
        FilePath = '.\Incoming\issuer.cer'
        CertStoreLocation = 'Cert:\CurrentUser\My'
        WhatIf = $true
    }
    Import-Certificate @params
    ```
3. After confirming the file and destination, remove `WhatIf` and run the command again.
4. Reopen the store and compare the imported certificate's thumbprint with the expected value.

If a non-SST file contains multiple certificates, `Import-Certificate` imports only the first certificate. Use the file type that matches the intended import and don't import a certificate into **Trusted Root Certification Authorities** as a routine troubleshooting step.

## Export a public certificate

`Export-Certificate` exports only public certificate material. It doesn't include the private key.

```powershell
$certificate = Get-ChildItem -Path 'Cert:\CurrentUser\My\THUMBPRINT'

$params = @{
    Cert = $certificate
    FilePath = '.\certificate.cer'
    NoClobber = $true
}
Export-Certificate @params
```

Choose an output format that matches the receiver's requirements:

| Format | `Export-Certificate`type | Contents |
| --- | --- | --- |
| `.cer` | `CERT` | One DER-encoded public certificate. |
| `.p7b` | `P7B` | One or more certificates in PKCS #7 format. |
| `.sst` | `SST` | One or more certificates in a Microsoft serialized certificate store. |

Use `-NoClobber` to prevent overwriting an existing export. For command details, see [Export-Certificate](/en-us/powershell/module/pki/export-certificate).

## Export a PFX only when you need the private key

A PFX is different from a public-certificate export because it can include the private key. `Export-PfxCertificate` exports a PFX file and requires either a password or `-ProtectTo`. A PFX export succeeds only when the included private keys are exportable.

Important

Don't treat a `.cer`, `.p7b`, or `.sst` export as a private-key backup. Conversely, don't create or distribute a PFX when a public-certificate export meets the requirement.

Use [Export a certificate with its private key](export-certificate-private-key) for the protected PFX workflow. `Export-PfxCertificate` encrypts private keys with `TripleDES_SHA1` unless you set `-CryptoAlgorithmOption AES256_SHA256`. For password or identity protection and chain options, see [Export-PfxCertificate](/en-us/powershell/module/pki/export-pfxcertificate).

## Import a PFX when the application needs the private key

Import a PFX only when the destination needs its private key. By default, `Import-PfxCertificate` imports the private key as nonexportable; don't add `-Exportable` unless the approved design requires future private-key export.

1. Verify the PFX owner, destination store, and protected transfer path.
2. Preview the import:

    ```powershell
    $credential = Get-Credential -UserName 'Enter PFX password' -Message 'Enter the PFX password'
    
    $params = @{
        FilePath = '.\certificate.pfx'
        CertStoreLocation = 'Cert:\LocalMachine\My'
        Password = $credential.Password
        WhatIf = $true
    }
    Import-PfxCertificate @params
    ```
3. After confirming the destination, remove `WhatIf` and run the command again.
4. Verify the certificate's thumbprint and `HasPrivateKey` value, then test the application as its runtime identity.

For parameter behavior and password-protected import examples, see [Import-PfxCertificate](/en-us/powershell/module/pki/import-pfxcertificate).

## Validate private-key access

`HasPrivateKey` confirms an associated private key, not that a service or application can use it. Test the certificate as the application's runtime identity, verify the intended operation succeeds, and retain least-privilege access to the key. In an approved negative test, an identity that lacks permission to use the key should remain unable to complete the private-key operation. Don't grant broad key access merely to bypass an application error.

## Make controlled certificate-store changes

Treat certificate deletion, movement, and property changes as controlled changes rather than routine cleanup.

1. Identify the certificate by thumbprint and record its store scope, intended use, chain, and application dependencies.
2. Determine whether the certificate has a private key. Export only the material required for the approved rollback plan: a public-certificate export doesn't preserve a private key.
3. Verify the physical and logical store context before you change a certificate that appears in more than one view.
4. Use the least-privileged account that can change the target store. Don't modify a root or service store merely to resolve an application error.
5. Make one change at a time, then validate the relying application and its runtime identity.
6. If validation fails, use the documented rollback material or reissue process. Don't restore a certificate to a different store scope without confirming that the application uses that scope.

## Security considerations

- Verify the exact store scope before you import, export, delete, or replace a certificate. A user-store change doesn't necessarily affect a service or local-computer store.
- Treat root-store modifications as a trust-policy change, not as a general certificate-repair action.
- Keep a PFX private key under approved access controls. Use public-certificate export when the recipient doesn't need the key.
- Don't use `-AllowUntrustedRoot` as a final trust-validation result. That option intentionally permits an untrusted root while building a chain, and `Test-Certificate` doesn't check revocation when you use it.
- Validate a certificate with the relying application after any change. A valid chain in one context doesn't prove that every service uses the same store or certificate selection rule.

## Troubleshoot certificate-store operations

| Symptom | Check |
| --- | --- |
| The same certificate appears in more than one view. | Compare thumbprints and store scopes. Logical collections and current-user inheritance can show the same certificate through multiple paths. |
| A service doesn't find a certificate that exists for your user. | Inspect the local-computer or service-account store that the service uses. A current-user certificate isn't automatically available to a service. |
| An import didn't add every certificate in the file. | Confirm the file format. For a non-SST file, `Import-Certificate` imports only the first certificate. |
| A PFX/private-key export isn't available or fails. | Confirm that the certificate has a private key and that the key is exportable. Use the PFX-specific guidance rather than a public-certificate export command. |
| A certificate doesn't pass SSL validation. | Verify the certificate's DNS identity, SSL policy, chain, and revocation result with `Test-Certificate`. If the application requires a specific extended key usage (EKU), also specify that object identifier (OID) with `-EKU`, then test the actual service. |