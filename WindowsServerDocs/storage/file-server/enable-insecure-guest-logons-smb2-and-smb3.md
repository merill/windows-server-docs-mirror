---
layout: Conceptual
title: Enable insecure guest logons in SMB2 and SMB3 for Windows client and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/enable-insecure-guest-logons-smb2-and-smb3
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to enable guest logons policy in SMB2 and SMB3 for Windows client and Windows Server devices using Group Policy and PowerShell.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-13T00:00:00.0000000Z
locale: en-us
document_id: cc878db6-4d29-8a59-e537-f23651ecec2e
document_version_independent_id: cc878db6-4d29-8a59-e537-f23651ecec2e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/enable-insecure-guest-logons-smb2-and-smb3.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/enable-insecure-guest-logons-smb2-and-smb3
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/enable-insecure-guest-logons-smb2-and-smb3.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 98258d45-9296-90b7-a4bf-89c18c4fb9bf
---

# Enable insecure guest logons in SMB2 and SMB3 for Windows client and Windows Server | Microsoft Learn

This article describes Server Message Block (SMB) insecure guest logon default behaviors, why you might enable guest access, and how to enable it for the SMB client using Group Policy and PowerShell.

Since Windows 2000, Windows disabled inbound guest access and prevented SMB2 and SMB3 client guest authentication since Windows 10. However, guest credentials might still be required when connecting to a third-party device that doesn't support a username and password. The recommendation is to upgrade or replace any third-party software or devices that only support guest authentication.

## Default behaviors

Starting from Windows 10, version 1709 and Windows Server 2019, SMB2 and SMB3 clients no longer allow the following actions by default:

- Guest account access to a remote server.
- Fall back to the Guest account after invalid credentials are provided.

SMB2 and SMB3 have the following behavior for different versions of Windows:

- By default, guest credentials can't be used to connect to a remote share in Windows 10 Enterprise, Windows 10 Pro for Workstations, and Windows 10 Education even if requested by the remote server.
- The use of guest credentials to connect to a remote share is no longer allowed by default in Windows Server 2019 Datacenter and Standard editions, even if requested by the remote server.
- Windows 10 Home and Pro editions still allow the use of guest authentication by default, as they did previously.
- In Windows 11 Pro Insider Preview build 25267, and all subsequent builds, guest credentials can't be used to connect to a remote share by default, even if requested by the remote server.
- SMB signing is required by default for Windows 11, version 24H2, Windows Server 2025, and later builds which results in compatibility issues with guest authentication if signing doesn't succeed.

Note

This behavior is present in various versions of Windows 10, including 1709, 1803, 1903, 1909, 2004, 20H2, and 21H1, as long as [KB5003173](https://support.microsoft.com/topic/may-11-2021-kb5003173-os-builds-19041-985-19042-985-and-19043-985-2824ace2-eabe-4c3c-8a49-06e249f52527) is installed.

## Reason for enabling guest logons

Enabling guest logons might be necessary where a user needs to access a resource on a server but the server doesn't provide user accounts, only guest access.

Caution

It's important to note that enabling guest logons can pose a security threat as it permits:

- An attacker to deceive a user into connecting to a spoofed malicious server without producing credential errors or prompts.
- Execution of malicious code such as ransomware through the guest logon.
- Guest logons are vulnerable to adversary-in-the-middle attacks that can expose sensitive data on the network.

As a result, the recommendation is to enable guest logons only in specific situations where required. Windows disables insecure guest logons by default. We recommend that you don't enable insecure guest logons.

## Prerequisites

Before you can begin modifying insecure guest logons for the SMB client, you need the following.

- An account that's a member of the Administrators group, or equivalent.
- SMB client running on one of the following operating systems:

    - Windows 10 or later.
    - Windows Server 2019 or later.

If you're planning on to enable auditing for insecure guest logons, the SMB client must be running on one of the following operating systems.

- Windows 11, version 24H2 or later.
- Windows Server 2025.

## Enable insecure guest logons

Enabling insecure guest logons can be performed through Group Policy or PowerShell.

Note

If you need to modify the Active Directory domain-based group policy, use **Group Policy Management** (gpmc.msc).

# [Group Policy](#tab/group-policy)
1. Select **Start**, type **gpedit.msc**, and select **Edit group policy**.
2. In the left pane under **Local Computer Policy**, navigate to **Computer Configuration\Administrative Templates\Network\Lanman Workstation**.
3. Open **Enable insecure guest logons**, select **Enabled**, then select **OK**.

# [PowerShell](#tab/powershell)
Run the following command through an elevated PowerShell prompt:

```powershell
Set-SmbClientConfiguration -EnableInsecureGuestLogons $true -Force
```

---

Both SMB signing, and SMB encryption policies must be disabled in Group Policy in order to use guest logons. Doing so can potentially compromise the security of the client and leave users open to credential theft and relay attacks.

Note

Guest logons don't support standard security features such as SMB signing and SMB encryption even if the SMB client is set to allow guest logons.

## Audit insecure guest logons

Once the insecure guest logons policy is enabled, these events are captured in the **Event Viewer**. To review these logs, perform the following steps:

1. Right-click on **Start**, select **Event Viewer**.
2. In the left pane, navigate to **Applications and Service Logs\Microsoft\Windows\SMBClient\Security**.

In the middle pane, you can review the following information concerning these events:

| Event ID | Output |
| --- | --- |
| 3023 | Log Name: Microsoft-Windows-SmbServer/Security  Source: Microsoft-Windows-SMBServer  Logged: Date/Time  Task Category: InsecureGuestLogon  Level: Informational  Keywords: Authentication  User: SYSTEM  Computer: **Description**: The SMB client was logged on as Guest account. |
| 31017 | Log Name: Microsoft-Windows-SmbClient/Security  Source: Microsoft-Windows-SMBClient  Logged: Date/Time  Task Category: RejectedInsecureGuestAuth  Level: Error  Keywords: Authentication  User: NETWORK SERVICE  Computer: **Description**: Rejected an insecure guest logon. The machine attempted to connect to the server using an insecure guest logon. The server denied the connection. Ensure that the guest account is enabled on the server and configured to allow access from the network. |
| 31018 | Log Name: Microsoft-Windows-SmbClient/Security  Source: Microsoft-Windows-SMBClient  Logged: Date/Time  Task Category: InsecureGuestAuthEnabled  Level: Warning  Keywords: Authentication  User: NETWORK SERVICE  Computer: **Description**: An administrator has enabled AllowInsecureGuestAuth. Clients using insecure guest logons are more vulnerable to attackers-in-the-middle, phishing, and malware. |
| 31022 | Log Name: Microsoft-Windows-SmbClient/Security  Source: Microsoft-Windows-SMBClient  Logged: Date/Time  Task Category: AllowedInsecureGuestAuth  Level: Warning  Keywords: Authentication  User: SYSTEM  Computer: **Description**: Allowed an insecure guest logon. This event indicates that the server attempted to log the user on as an unauthenticated guest and was allowed by the client.  Username: nonexistantaccount  Server name: |