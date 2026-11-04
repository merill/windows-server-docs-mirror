---
layout: Conceptual
title: Credential Guard protected machine accounts in Windows Server 2025 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/delegated-managed-service-accounts/credential-guard-protected-machine-accounts
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to enhance machine accounts security in Windows Server 2025 through Credential Guard machine protected identity isolation group policy settings.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-04-11T00:00:00.0000000Z
locale: en-us
document_id: 1db0a3ac-35c1-0765-eb7a-99c5862e8b2a
document_version_independent_id: 1db0a3ac-35c1-0765-eb7a-99c5862e8b2a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/delegated-managed-service-accounts/credential-guard-protected-machine-accounts.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/delegated-managed-service-accounts/credential-guard-protected-machine-accounts
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/delegated-managed-service-accounts/credential-guard-protected-machine-accounts.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: ac78be4e-f3ff-f4dc-ac47-5633cc421cdd
---

# Credential Guard protected machine accounts in Windows Server 2025 | Microsoft Learn

Important

Starting with the April Windows security update ([KB5055523](https://aka.ms/WinServer2025/5055523)), Credential Guard protected machine accounts is temporarily disabled in Windows Server 2025 and Windows 11, version 24H2. This feature has been disabled due to an issue with machine password rotation using Kerberos. The feature remains disabled until a permanent fix is available. To learn more about the machine password rotation issue, see the [Windows Server 2025 known issues and notifications](/en-us/windows/release-health/status-windows-server-2025?context=%2Fwindows-server%2Fcontext%2Fwindows-server-get-started) article.

Recent Windows features, such as the Flexible Authentication Secure Tunneling (FAST) Kerberos extension, also known as Kerberos Armoring, became increasingly dependent on machine accounts to enhance security. The machine account is used to add entropy to the client's secret key and both gMSA and dMSA service accounts now rely on machine accounts and grant them access to service accounts. However, this reliance on machine accounts created a vulnerability in service account security, as machine accounts can be easily extracted from the registry and used to access highly secured service accounts.

In order to strengthen service account security, the opt-in feature of machine accounts in Credential Guard is now available in Windows Server 2025 devices that have Credential Guard enabled. It's crucial to take measures to address this issue. This feature relocates the storage of machine account credentials from the registry to Credential Guard, which provides a separate trusted execution environment for the machine account password. Security is improved by ensuring that:

- The password can't be accessed by unprivileged users, administrators, or drivers.
- The security of machine accounts is enhanced, which hardens the overall security of service accounts in Active Directory (AD).

## Machine Identity Isolation

Enabling machine identity isolation allows for virtualization-based protection of AD machine accounts. When enabled, the machine account credentials of the device will be relocated into Credential Guard. As a result, all future machine account authentications, such as logging into a domain-joined device, will be routed through Credential Guard. However, if Credential Guard fails to start after a device reboot, it results in the inability to complete domain authentication, potentially requiring intervention from a local administrator account to recover.

### Machine Identity Isolation Configuration

To enable the **Machine Identity Isolation Configuration** setting, open **Group Policy** and navigate to the following path, and select **Enabled**:

- **Computer Configuration\Administrative Templates\System\Device Guard\Turn On Virtualization Based Security**

![A screenshot of the Turn On Virtualization Based Security group policy setting set to enabled.](../media/delegated-managed-service-accounts/turn-on-virtualization-based-security-group-policy-setting.png)

The available options for this specific setting are:

- **Disabled**: Turns off Machine Identity Isolation. If this policy was previously set to *Enabled in audit mode*, no further action is needed. If this policy was previously set to *Enabled in enforcement mode*, the device must be unjoined and rejoined to the domain, as it's unable to authenticate otherwise.

    Note

    - If local cached logon is enabled when this setting is disabled, local logon will still work while the cache is fresh, but domain authentication will break.
    - Only the local administrator account can be used to unjoin and rejoin the machine.
- **Enabled in audit mode**: This option creates a new secret in Credential Guard and copies it into the Local Security Authority (LSA). The old LSA secret is then deleted. When auditing, attempts to authenticate the machine identity will first try to use the copy in Credential Guard. If that fails, authentication falls back to using the original machine identity from LSA.

    Note

    If the policy was previously set to enforcement mode, the device must be manually unjoined and rejoined.
- **Enabled in enforcement mode**: This option moves the machine account secret into Credential Guard and deletes it from LSA. This makes the machine account secret inaccessible except as utilized by Credential Guard for machine authentication.
- **Not Configured**: Leaves the policy setting undefined. Group Policy doesn't write the policy setting to the registry and has no impact on computers or users. If there's a current setting in the registry, it won't be modified.