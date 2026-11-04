---
layout: Conceptual
title: About dump encryption | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/about-dump-encryption
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Describes how to encrypt dump files and troubleshoot encryption.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.asset: b78ab493-e7c3-41f5-ab36-29397f086f32
ms.date: 2016-11-03T00:00:00.0000000Z
locale: en-us
document_id: c528b66c-233e-238b-d761-44b70db44cf9
document_version_independent_id: 3593517c-e853-cf83-85b6-131fc91f6696
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/manage/About-dump-encryption.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/manage/about-dump-encryption
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/manage/About-dump-encryption.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9f88f1f3-32dd-0c05-5f24-52b04f004d0f
---

# About dump encryption | Microsoft Learn

Dump encryption can be used to encrypt crash dumps and live dumps generated for a system. The dumps are encrypted using a symmetric encryption key which is generated for each dump. This key itself is then encrypted using the public key specified by the trusted administrator of the host (crash dump encryption key protector). This ensures that only someone having the matching private key can decrypt and therefore access contents of the dump. This capability is leveraged in a guarded fabric. Note: If you configure dump encryption, also disable Windows Error Reporting. WER cannot read encrypted crash dumps.

## Configuring dump encryption

### Manual configuration

To turn on dump encryption using the registry, configure the following registry values under `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl`

| Value Name | Type | Value |
| --- | --- | --- |
| DumpEncryptionEnabled | DWORD | 1 to enable dump encryption, 0 to disable dump encryption |
| EncryptionCertificates\Certificate.1::PublicKey | Binary | Public key (RSA, 2048 Bit) that should be used for encrypting dumps. This has to be formatted as [BCRYPT_RSAKEY_BLOB](/en-us/windows/win32/api/bcrypt/ns-bcrypt-bcrypt_rsakey_blob). |
| EncryptionCertificates\Certificate.1::Thumbprint | String | Certificate thumbprint to allow automatic lookup of private key in the local certificate store when decrypting a crash dump. |

### Configuration using script

To simplify configuration, a [sample script](https://github.com/Microsoft/Virtualization-Documentation/tree/live/hyperv-tools/DumpEncryption) is available to enable dump encryption based on a public key from a certificate.

1. In a trusted environment: Create a certificate with a 2048 Bit RSA key and export the public certificate
2. On target hosts: Import the public certificate to the local certificate store
3. Run the sample configuration script 

    ```
    .\Set-DumpEncryptionConfiguration.ps1 -Certificate (Cert:\CurrentUser\My\093568AB328DF385544FAFD57EE53D73EFAAF519) -Force
    ```

## Decrypting encrypted dumps

To decrypt an existing encrypted dump file, you need to download and install the Debugging Tools for Windows. This tool set contains KernelDumpDecrypt.exe which can be used to decrypt an encrypted dump file. If the certificate including the private key is present in the current user's certificate store, the dump file can be decrypted by calling

```
    KernelDumpDecrypt.exe memory.dmp memory_decr.dmp
```

After decryption, tools like WinDbg can open the decrypted dump file.

## Troubleshooting dump encryption

If dump encryption is enabled on a system but no dumps are being generated, please check the system's `System` event log for `Kernel-IO` event 1207. When dump encryption cannot be initialized, this event is created and dumps are disabled.

| Detailed error message | Steps to mitigate |
| --- | --- |
| Public Key or Thumbprint registry missing | Check if both registry values exist in the expected location |
| Invalid Public Key | Make sure that the public key stored in the PublicKey registry value is stored as [BCRYPT_RSAKEY_BLOB](/en-us/windows/win32/api/bcrypt/ns-bcrypt-bcrypt_rsakey_blob). |
| Unsupported Public Key Size | Currently, only 2048 Bit RSA keys are supported. Configure a key that matches this requirement |

Also check if the value `GuardedHost` under `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\CrashControl\ForceDumpsDisabled` is set to a value other than 0. This disables crash dumps completely. If this is the case, set it to 0.