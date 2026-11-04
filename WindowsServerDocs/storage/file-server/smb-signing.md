---
layout: Conceptual
title: Control SMB signing behavior | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-signing
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: How to disable SMB signing on third-party servers in Windows 11 and Windows Server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-13T00:00:00.0000000Z
locale: en-us
document_id: 3643163c-3f2f-61ce-e3c9-9bdc654779a9
document_version_independent_id: 3643163c-3f2f-61ce-e3c9-9bdc654779a9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/smb-signing.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/smb-signing
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/smb-signing.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: c57c86d7-a8f1-7708-fc71-9f6916258c5d
---

# Control SMB signing behavior | Microsoft Learn

## How SMB signing works

Server Message Block (SMB) signing is a security feature that uses the session key and cipher suite to add a signature to a message going across a connection. This signature contains a hash of the entire message in the SMB header. If someone tampers with the message in transit, the data in the tampered message doesn't match the hash in the signature. The hash also includes the identities of the original sender and the intended recipient. Signature mismatches alert users to possible foul play, helping them protect their deployments from relay and spoofing attacks.

SMB signing requirements can involve both outbound signing, which covers traffic from the SMB client, and inbound signing, which covers traffic to the server. Windows and Windows Server can require outbound signing only, inbound signing only, both, or neither. For example:

- Windows 11, version 24H2 Enterprise, Pro, and Education require both outbound and inbound SMB signing.
- Windows Server 2025 requires outbound SMB signing only.
- Windows 11, version 24H2 Home edition doesn't require outbound or inbound SMB signing.

## SMB signing behavior

Although all versions of Windows and Windows Server support SMB signing, a third-party might opt to disable or not support it. If you try to connect to a remote share on a third-party SMB server that doesn't allow SMB signing, you might encounter one of the following error messages:

```error
0xc000a000
-1073700864
STATUS_INVALID_SIGNATURE
The cryptographic signature is invalid.
```

To resolve this issue, adjust the settings on your third-party SMB server to allow (enable) SMB signing.

When you try to connect to third-party devices that use guest accounts to simplify access, you might receive one of these error messages:

```error
You can't access this shared folder because your organization's security policies block
unauthenticated guest access. These policies help protect your PC from unsafe or malicious
devices on the network.
```

```error
Error code: 0x80070035
The network path was not found.
```

```error
System error 3227320323 has occurred.
```

Disabling SMB signing might be necessary if you're unable to disable guest usage for your third-party. However, this means that you're using guest access and preventing your client from ensuring signing to a trusted device.

Caution

We don't recommend disabling SMB signing as a workaround for third-party servers. We also don't recommend trying to sign with guest accounts.

## Prerequisites

In order to control SMB signing behavior and maximize its capabilities, your system must be running one of the following two operating systems:

- Windows 11, version 24H2 or later
- Windows Server 2025 or later

You should also follow these recommendations to ensure your SMB signatures are effective at securing your data:

- Use Kerberos instead of NTLMv2.
- Don't connect to shares using IP addresses.
- Don't use CNAME Domain Name System (DNS) records. Instead, assign alternate computer names with `netdom.exe`.

## Disable SMB signing

SMB signing is required by default on the latest Insider Preview builds of Windows 11 and Windows Server 2025. All Windows environments support SMB signing. However, if your environment uses third-party servers and the third-party server doesn't support SMB signing, you can't connect to the remote share.

Requiring SMB signing also disables guest access to shares. In these cases, you must disable SMB signing manually to restore access for guest accounts. You can manually disable SMB signing through Group Policy, PowerShell, and Windows Admin Center.

Note

If you need to modify the Active Directory domain-based group policy, use **Group Policy Management** (gpmc.msc).

# [Group Policy](#tab/group-policy)
To disable SMB signing in Group Policy, perform the following steps:

1. Select **Start**, type **gpedit.msc**, then hit Enter.
2. In the **Local Group Policy Editor**, navigate to **Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options**.
3. Open **Microsoft network client: Digitally sign communications (always)**, select **Disabled**, then select **OK**.

# [PowerShell](#tab/powershell)
1. Open an elevated PowerShell window.
2. To disable SMB client signing for outbound connections, run this command:

    ```powershell
    Set-SmbClientConfiguration -RequireSecuritySignature $false
    ```
3. To disable SMB server signing for inbound connections, run this command:

    ```powershell
    Set-SmbServerConfiguration -RequireSecuritySignature $false
    ```

# [Windows Admin Center](#tab/wac)
1. Open **Windows Admin Center**.
2. Select the name of the server you want to edit.
3. Select **Settings**.
4. Select **File Shares (SMB server)**.
5. Under **SMB signing**, select **Not required**.
6. Select **Save**.

Disabling SMB client for outbound connections can only be accomplished through Group Policy and PowerShell.

---

## Enable SMB signing

SMB signing ensures data integrity by verifying that data isn't tampered with during transmission. Additionally, SMB signing provides authentication by verifying the identity of the server and client, which helps prevent adversary-in-the-middle attacks.

# [Group Policy](#tab/group-policy)
To enable SMB signing in Group Policy, perform the following steps:

1. Select **Start**, type **gpedit.msc**, then hit Enter.
2. In the **Local Group Policy Editor**, navigate to **Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options**.
3. Open **Microsoft network client: Digitally sign communications (always)**, select **Enabled**, then select **OK**.

# [PowerShell](#tab/powershell)
1. Open an elevated PowerShell window.
2. To enable SMB client signing for outbound connections, run this command:

    ```powershell
    Set-SmbClientConfiguration -RequireSecuritySignature $true
    ```
3. To enable SMB server signing for inbound connections, run this command:

    ```powershell
    Set-SmbServerConfiguration -RequireSecuritySignature $true
    ```

# [Windows Admin Center](#tab/wac)
1. Open **Windows Admin Center**.
2. Select the name of the server you want to edit.
3. Select **Settings**.
4. Select **File Shares (SMB server)**.
5. Under **SMB signing**, select **Required**.
6. Select **Save**.

Enabling SMB client for outbound connections can only be accomplished through Group Policy and PowerShell.

---

## Verify SMB signing status

To check if SMB signing is enabled or disabled on your SMB client or SMB server, run the following command:

```powershell
Get-SmbClientConfiguration | FL RequireSecuritySignature
```

```powershell
Get-SmbServerConfiguration | FL RequireSecuritySignature
```

If the returned information is **True**, then SMB signing is enabled, otherwise, if the returned information is **False**, then SMB signing is disabled.