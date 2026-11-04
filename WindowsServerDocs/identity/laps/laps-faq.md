---
layout: FAQ
title: Windows LAPS frequently asked questions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-faq
summary: >
  <p>This article provides answers to many commonly asked questions about Windows Local Administrator

  Password Solution (Windows LAPS).</p>
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Get answers to frequently asked questions about Windows LAPS.
author: jay98014
ms.author: roharwoo
ms.topic: faq
ms.date: 2025-05-12T00:00:00.0000000Z
locale: en-us
document_id: 991083f2-950b-3d1c-4f80-14c9a61176de
document_version_independent_id: 991083f2-950b-3d1c-4f80-14c9a61176de
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/laps/laps-faq.yml
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: faq
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/laps/laps-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/laps/laps-faq.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a5d26e33-6cdd-5de7-3628-fc29358a2f42
---

# Windows LAPS frequently asked questions | Microsoft Learn

This article provides answers to many commonly asked questions about Windows Local Administrator Password Solution (Windows LAPS).

## General

### Is it supported to run 3rd-party local account password manager products side-by-side with Windows LAPS?

Yes, this scenario is supported with the following condition. You must take care to configure Windows LAPS and the 3rd-party product to manage different local accounts. If you mistakenly configure both to manage the same account, Windows LAPS rejects attempts by the 3rd-party product to modify the account's password. See [Account password tampering protection](laps-concepts-overview#account-password-tampering-protection).

### Why can't I change the password of a local admin account currently managed by Windows LAPS?

Windows LAPS prevents accidental or spurious changes to the managed account's password. This protection helps prevent a torn state situation where the password stored in the directory doesn't match the password stored locally on the device. See [Account password tampering protection](laps-concepts-overview#account-password-tampering-protection).

### Why isn't the Windows LAPS PowerShell module hosted on GitHub, PowerShell Gallery, or similar?

The Windows LAPS PowerShell module is part of Windows and not available outside of the operating system.

### How can I copy the Windows LAPS PowerShell module to an older operating system?

This scenario isn't supported.

### How can I submit unanswered questions or feature requests?

See [Submit feedback](laps-overview#submit-feedback-about-windows-laps).

### I see errors in my Windows LAPS event log - how do I fix them?

See [Windows LAPS Troubleshooting Guidance](/en-us/troubleshoot/windows-server/windows-security/windows-laps-troubleshooting-guidance).

### Microsoft promotes a password-less strategy and direction. Why was a password-based feature like Windows LAPS added to Windows?

All Windows LAPS scenarios involve the management of a Windows local account's password for use with help desk tasks, device recovery, and other scenarios. Since Windows only supports password-based authentication for local accounts, password management is necessary.

## Windows LAPS and Active Directory

### Can I deploy and use Windows LAPS even if my domain is running older domain controllers?

Yes with some limitations. See [Domain functional level and domain controller version requirements](laps-scenarios-windows-server-active-directory#domain-functional-level-and-domain-controller-operating-system-version-requirements).

### Can I deploy and use Windows LAPS even if my domain isn't yet at Windows Server 2016 Domain Functional Level?

Yes with some limitations. See [Domain functional level and domain controller version requirements](laps-scenarios-windows-server-active-directory#domain-functional-level-and-domain-controller-operating-system-version-requirements).

### Do I need to deploy a Windows Server 2022 or 2019 DC in order to extend my forest's schema with the Windows LAPS schema extensions?

No - you can run the `Update-LapsADSchema` cmdlet from any operating system updated with the Windows LAPS feature. The only requirement is that the client credentials are authorized to modify the Active Directory schema. See [Update the Windows Server Active Directory schema](laps-scenarios-windows-server-active-directory#update-the-windows-server-active-directory-schema).

### How can I copy the Windows LAPS-enabled Active Directory User and Computers snap-in to an older operating system?

This scenario isn't supported.

### I installed RSAT and I still don't see the new LAPS-enabled Active Directory User and Computers snap-in?

The new snap-in is only available in the Windows in-box versions of RSAT on supported Windows LAPS platforms. See [Windows LAPS snap-in availability](laps-management-user-interface#windows-laps-snap-in-availability).

### Why don't I see the new Windows LAPS policy in my GPO central store?

The new Windows LAPS policy isn't automatically installed as part of the GPO central store. See [Group Policy Object Central Store](laps-management-policy-settings#group-policy-object-central-store).

### Are Windows LAPS passwords available during a catastrophic AD disaster scenario?

Yes, assuming that AD domain controller database backups are being regularly taken and maintained. For more information, see [Retrieve passwords during Active Directory disaster recovery scenarios](laps-scenarios-windows-server-active-directory#retrieve-passwords-during-windows-server-active-directory-disaster-recovery-scenarios)

### Is it supported to run legacy Microsoft LAPS side-by-side with Windows LAPS?

Yes, this scenario is supported with the following conditions. A new Windows LAPS policy must be configured, and you must take care to configure Windows LAPS and the legacy LAPS to manage different local accounts.

### What happens if I accidentally configure a Windows LAPS policy setting with an unsupported value?

See [Windows LAPS default policy values](laps-management-policy-settings#windows-laps-default-policy-values).

### How can I enable passphrases, which are only available in Windows 11 24H2, since older operating systems don't support the new passphrase-related PasswordComplexity settings (6-8)?

There are two options in this scenario. Either allow the older OSs to fall back to the default setting, or create two policies. See [Windows LAPS default policy values](laps-management-policy-settings#windows-laps-default-policy-values).

## Windows LAPS and Microsoft Entra ID

### Why is my Microsoft Entra joined device getting an error when attempting to post the password to Microsoft Entra ID?

The most common reason for this forgetting to enable the LAPS feature for your Microsoft Entra tenant. See [Enabling Windows LAPS with Microsoft Entra ID](/en-us/azure/active-directory/devices/howto-manage-local-admin-passwords#enabling-windows-laps-with-azure-ad).

### Do I need to extend my forest's schema if I'm only planning to back up passwords to Microsoft Entra ID?

No.

### Do I need Intune in order to use Windows LAPS?

No. You can deploy and use Windows LAPS in either Active Directory or Microsoft Entra mode without Intune. Intune does provide many benefits to the Windows LAPS scenario (for example, policy deployment at scale, monitoring, and password-reset action support).

### Do I need Microsoft Entra Connect in order to use Windows LAPS?

No. There are no dependencies between these two features. See [Windows LAPS and Microsoft Entra Connect in hybrid environments](laps-scenarios-azure-active-directory#windows-laps-and-azure-ad-connect-in-hybrid-environments).

### How do I configure a hybrid-joined device to back up the password to both Microsoft Entra ID and AD?

This scenario isn't supported. You can only back up the password to one directory at a time.

### Which specific Azure clouds support Windows LAPS?

See [Windows Local Administrator Password Solution in Microsoft Entra ID](https://aka.ms/cloudlaps) and [Microsoft Intune support for Windows LAPS](/en-us/mem/intune/protect/windows-laps-overview) for information on which specific clouds are supported.

### Does Microsoft Entra Domain Services support Windows LAPS?

[Microsoft Entra Domain Services](/en-us/azure/active-directory-domain-services/overview) doesn't currently support Windows LAPS.

### How are Windows LAPS passwords protected when stored in Microsoft Entra ID?

Windows LAPS passwords are always protected in transit (https) when sent from the managed device to the cloud. Windows LAPS passwords that are stored in the cloud are always encrypted with AES256. The decryption keys are only available to those internal Microsoft Entra services that have a technical need to actually handle the clear-text passwords, for example during storage or query operations. This encryption layer is specific to Windows LAPS passwords, and is always enabled in addition to the default Microsoft Entra data protection mechanisms - see [Microsoft Entra Data Security Considerations](https://azure.microsoft.com/resources/azure-active-directory-data-security-considerations).

### I see a 20000 warning event in the event log during a Windows Autopilot pre-provisioning workflow - how do I fix this issue?

The Windows LAPS CSP rejects MDM configuration directives when the device doesn't appear to be joined. The CSP logs an event ID 20000 in the Windows LAPS operational event log when this condition occurs. You might see one or more of these events during the technician flow phase of an Autopilot pre-provisioning workflow, when Autopilot unjoins the device from Microsoft Entra.

This situation gets resolved during the later user flow phase of Autopilot provisioning when the device is rejoined to Microsoft Entra. At that point Windows LAPS is fully functional and starts backing up passwords to Microsoft Entra.

This issue doesn't affect other Autopilot scenarios aside from pre-provisioning. The CSP warning events should be ignored when seen in an Autopilot pre-provisioning workflow as described earlier.

See [Step by step tutorial for Windows Autopilot for pre-provisioned deployment Microsoft Entra join in Intune](/en-us/autopilot/tutorial/pre-provisioning/azure-ad-join-workflow).