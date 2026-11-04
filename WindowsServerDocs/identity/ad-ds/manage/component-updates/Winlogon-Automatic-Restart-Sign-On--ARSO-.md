---
layout: Conceptual
title: Winlogon automatic restart sign-on (ARSO) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/winlogon-automatic-restart-sign-on--arso-
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: How Windows automatic restart sign-on can help make your users more productive.
author: robinharwood
ms.author: roharwoo
ms.reviewer: cahick
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: e8068577-6ae5-917e-d708-2ad5a162c6e9
document_version_independent_id: 48b7ac00-fb50-e7a5-52b0-7c4b063e8652
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/component-updates/Winlogon-Automatic-Restart-Sign-On--ARSO-.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/component-updates/winlogon-automatic-restart-sign-on--arso-
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/component-updates/Winlogon-Automatic-Restart-Sign-On--ARSO-.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6ff5d977-c265-59f3-113b-aa6cccadaef0
---

# Winlogon automatic restart sign-on (ARSO) | Microsoft Learn

During a Windows Update, there are user specific processes that must happen for the update to be complete. These processes require the user to be logged in to their device. On the first sign in after an update has been initiated, users must wait until these user specific processes are complete before they can start using their device.

## How does it work?

When Windows Update initiates an automatic reboot, ARSO extracts the currently logged in user's derived credentials, persists it to disk, and configures Autologon for the user. Windows Update running as system with TCB privilege initiates the RPC call.

After the final Windows Update reboot, the user will automatically be logged in via the Autologon mechanism, and the user's session is rehydrated with the persisted secrets. Additionally, the device is locked to protect the user's session. The locking is initiated via Winlogon whereas the credential management is done by the Local Security Authority (LSA). Upon a successful ARSO configuration and sign in, the saved credentials are immediately deleted from disk.

By automatically logging in and locking the user on the console, Windows Update can complete the user specific processes before the user returns to the device. In this way, the user can immediately start using their device.

ARSO treats unmanaged and managed devices differently. For unmanaged devices, device encryption is used but not required for the user to get ARSO. For managed devices, TPM 2.0, SecureBoot, and BitLocker are required for ARSO configuration. IT admins can override this requirement via Group Policy. ARSO for managed devices is currently only available for devices that are joined to Microsoft Entra ID.

| Windows Update | shutdown -g -t 0 | User-initiated reboots | APIs with SHUTDOWN\_ARSO / EWX\_ARSO flags |
| --- | --- | --- | --- |
| Managed devices - Yes<br>Unmanaged devices - Yes | Managed devices - Yes<br>Unmanaged devices - Yes | Managed devices - No<br>Unmanaged devices - Yes | Managed devices - Yes<br>Unmanaged devices - Yes |

Note

After a Windows Update induced reboot, the last interactive user is automatically logged in and the session is locked. This gives the ability for a user's lock screen apps to still run despite the Windows Update reboot.

![Settings Page](media/winlogon-automatic-restart-sign-on--arso-/gtr-adds-lockscreenapp.png)

## Policy #1

### Sign-in and lock last interactive user automatically after a restart

In Windows 10, ARSO is disabled for Server SKUs and opted out for Client SKUs.

**Group policy location:** Computer Configuration &gt; Administrative Templates &gt; Windows Components &gt; Windows sign in Options

**Intune policy:**

- Platform: Windows 10 and later
- Profile type: Administrative Templates
- Path: \Windows Components\Windows Logon Options

**Supported on:** At least Windows 10 Version 1903

**Description:**

This policy setting controls whether a device will automatically sign in and lock the last interactive user after the system restarts or after a shutdown and cold boot.

It only occurs if the last interactive user didn't sign out before the restart or shutdown.

If the device is joined to Active Directory or Microsoft Entra ID, this policy only applies to Windows Update restarts. Otherwise, it applies to both Windows Update restarts and user-initiated restarts and shutdowns.

If you don't configure this policy setting, it's enabled by default. When the policy is enabled, the user is automatically signed in. Additionally, after the device boots, the session is locked with all lock screen apps configured for that user.

After enabling this policy, you can configure its settings through the ConfigAutomaticRestartSignOn policy. It sets the mode to automatic sign in and locks the last interactive user after a restart or cold boot.

If you disable this policy setting, the device doesn't configure automatic sign in. The user's lock screen apps aren't restarted after the system restarts.

**Registry editor:**

| Value Name | Type | Data |
| --- | --- | --- |
| DisableAutomaticRestartSignOn | DWORD | 0 (Enable ARSO) |
|  |  | 1 (Disable ARSO) |

**Policy registry location:** HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System

**Type:** DWORD

![Screenshot of the Sign-in and lock last interactive user automatically after a restart dialog box.](media/winlogon-automatic-restart-sign-on--arso-/gtr-adds-signinpolicy.png)

## Policy #2

### Configure the mode of automatically signing in and locking last interactive user after a restart or cold boot

**Group policy location:** Computer Configuration &gt; Administrative Templates &gt; Windows Components &gt; Windows Logon Options

**Intune policy:**

- Platform: Windows 10 and later
- Profile type: Administrative Templates
- Path: \Windows Components\Windows Logon Options

**Supported on:** At least Windows 10 Version 1903

**Description:**

This policy setting controls the configuration under which an automatic restart and sign on and lock occurs after a restart or cold boot. If you chose “Disabled” in the “Sign-in and lock last interactive user automatically after a restart” policy, then automatic sign on won't occur and this policy doesn't need to be configured.

If you enable this policy setting, you can choose one of the following two options:

1. “Enabled if BitLocker is on and not suspended” specifies that automatic sign on and lock will only occur if BitLocker is active and not suspended during the reboot or shutdown. Personal data can be accessed on the device's hard drive at this time if BitLocker isn't on or suspended during an update. BitLocker suspension temporarily removes protection for system components and data but may be needed in certain circumstances to successfully update boot-critical components.
    - BitLocker is suspended during updates if:
        - The device doesn't have TPM 2.0 and PCR7, or
        - The device doesn't use a TPM-only protector
2. “Always Enabled” specifies that automatic sign on will happen even if BitLocker is off or suspended during reboot or shutdown. When BitLocker isn't enabled, personal data is accessible on the hard drive. Automatic restart and sign on should only be run under this condition if you're confident that the configured device is in a secure physical location.

If you disable or don't configure this setting, automatic sign on will default to the “Enabled if BitLocker is on and not suspended” behavior.

**Registry editor**

| Value Name | Type | Data |
| --- | --- | --- |
| AutomaticRestartSignOnConfig | DWORD | 0 (Enable ARSO if secure) |
|  |  | 1 (Enable ARSO always) |

**Policy registry location:** HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System

**Type:** DWORD

![Screenshot of the Configure the mode of automatically signing in and locking last interactive user after a restart or cold boot dialog box.](media/winlogon-automatic-restart-sign-on--arso-/arso-policy-setting.png)

## Troubleshooting

When Winlogon performs a sign-in, Winlogon's state trace is stored in the Winlogon event log. Check **Applications and Services Logs &gt; Microsoft &gt; Windows &gt; Winlogon &gt; Operational** in Event Viewer for the following Winlogon events:

| Event ID | Event description | Event source |
| --- | --- | --- |
| 1 | `Authentication started.` | Winlogon |
| 2 | `Authentication stopped. Result 0` | Winlogon |

The status of an ARSO configuration attempt is stored in the LSA event log. Check **Applications and Services Logs &gt; Microsoft &gt; Windows &gt; LSA &gt; Operational** in Event Viewer for the following LSA events:

| Event ID | Event description | Event source |
| --- | --- | --- |
| 320 | `Automatic restart sign on successfully configured the autologon credentials for: Account name: <accountName> Account Domain: <accountDomain>` | LSA |
| 321 | `Automatic restart sign on successfully deleted autologon credentials from LSA memory` | LSA |
| 322 | `Automatic restart sign on failed to configure the autologon credentials with error: <errorText>` | LSA |

### Reasons why autologon might fail

There are several cases in which a user automatic login can't be achieved. This section is intended to capture the known scenarios in which this can occur.

### User must change password at next login

User login can enter a blocked state when password change at next login is required. This can be detected prior to restart in most cases, but not all (for example, password expiry can be reached between shutdown and next login.

### User account disabled

An existing user session can be maintained even if disabled. Restart for an account that is disabled can be detected locally in most cases in advance, depending on gp it may not be for domain accounts (some domain cached login scenarios work even if account is disabled on DC).

### Logon hours and parental controls

The Logon Hours and parental controls can prohibit a new user session from being created. If a restart were to occur during this window, the user wouldn't be permitted to log in. The policy also causes lock or logout as a compliance action. The status of an Autologon configuration attempt is logged.

## Security details

In environments where the device’s physical security is of concern (for example, the device can be stolen), Microsoft doesn't recommend using ARSO. ARSO relies on the integrity of the platform firmware and TPM, an attacker with physical access maybe able to compromise these and as such access the credentials stored on disk with ARSO enabled.

In enterprise environments where the security for user data protected by Data Protection API (DPAPI) is of concern, Microsoft doesn't recommend using ARSO. ARSO negatively impacts user data protected by DPAPI because decryption doesn't requires user credentials. Enterprises should test the impact on the security of user data protected by DPAPI before using ARSO.

### Credentials stored

| Password hash | Credential key | Ticket-granting ticket | Primary refresh token |
| --- | --- | --- | --- |
| Local account - Yes | Local account - Yes | Local account - No | Local account - No |
| MSA account - Yes | MSA account - Yes | MSA account - No | MSA account - No |
| Microsoft Entra joined account - Yes | Microsoft Entra joined account - Yes | Microsoft Entra joined account - Yes (if hybrid) | Microsoft Entra joined account - Yes |
| Domain joined account - Yes | Domain joined account - Yes | Domain joined account - Yes | Domain joined account - Yes (if hybrid) |

### Credential Guard interaction

ARSO is supported with Credential Guard enabled on devices beginning with Windows 10 version 2004.