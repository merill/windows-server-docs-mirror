---
layout: Conceptual
title: Block NTLM connections on SMB in Windows Server 2025 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-ntlm-blocking
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to make SMB more secure by blocking NTLM.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2024-10-25T00:00:00.0000000Z
locale: en-us
document_id: 209f957e-39e4-8546-878f-fed847af61b8
document_version_independent_id: 209f957e-39e4-8546-878f-fed847af61b8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/smb-ntlm-blocking.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/smb-ntlm-blocking
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/smb-ntlm-blocking.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 75a212cf-7829-4cda-12c6-25e8a8d76c02
---

# Block NTLM connections on SMB in Windows Server 2025 | Microsoft Learn

The SMB client now supports blocking NTLM authentication for remote outbound connections. Blocking NTLM authentication prevents bad actors from tricking clients into sending NTLM requests to malicious servers, counteracting brute force, cracking, and pass-the-hash attacks. NTLM blocking is also required for switching an organization's authentication protocols to Kerberos, which is more secure than NTLM because it can verify server identities with its ticket system. However, organizations can also enable this layer of protection without having to disable NTLM entirely.

## Prerequisites

NTLM blocking for the SMB client requires the following prerequisites:

- An SMB client running on one of the following operating systems.
    - Windows Server 2025 or later.
    - Windows 11, version 24H2 or later.
- An SMB server that allows using Kerberos.

Tip

NTLM blocking is an SMB client capability only. The SMB client is built into both Windows Server and Windows client operating systems. The destination SMB server can be any operating system where PKU2U or kerberos can be used.

## Configure SMB client NTLM blocking

Starting with Windows Server 2025 and Windows 11, version 24H2, you have the option to configure SMB to block NTLM. To improve the security of deployments running earlier versions of Windows, you must disable NTLM manually, either by editing the relevant Group Policy or running a specific command in PowerShell.

To configure NTLM blocking:

# [Group Policy](#tab/group-policy)
1. Open the **Group Policy Management Console**.
2. In the console tree, go to **Computer Configuration** &gt; **Administrative Templates** &gt; **Network** &gt; **Lanman Workstation**.
3. Right-click **Block NTLM (LM, NTLM, NTLMv2)** and select **Edit**.
4. Select **Enabled**.

# [PowerShell](#tab/powershell)
1. Open an elevated PowerShell window.
2. Run the following command to enable NTLM blocking.

    ```powershell
    Set-SmbClientConfiguration -BlockNTLM $true 
    ```

---

## Enable exceptions to NTLM blocking

There might be scenarios where you need to allow certain machines to use NTLM instead of blocking it globally. For example, when the SMB server you're trying to connect to isn't joined to an Active Directory domain.

To enable a list of exceptions to NTLM blocking:

# [Group Policy](#tab/group-policy)
1. In the **Group Policy Editor Console** tree, go to **Computer Configuration** &gt; **Administrative Templates** &gt; **Network** &gt; **Lanman Workstation**.
2. Right-click **Block NTLM Server Exception List** and select **Edit**.
3. Select **Enabled**.
4. Enter the IP addresses, NetBIOS names, and fully qualified domain names (FQDNs) of the remote machines you want to allow NTLM authentication to.

# [PowerShell](#tab/powershell)
There isn't currently a PowerShell equivalent to the Block NTLM Server Exception List Group Policy object. In order to set up an exception list, you must go into the Group Policy Editor and configure the setting manually. However, once you've completed the manual setup, you can make individual exceptions for certain IPs by running this command with the DNS name, IP address, or NetBIOS name in the `AddToList` parameter:

```powershell
$params = @{
  Path = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\LanmanWorkstation"
  Name = "BlockNTLMServerExceptionList"
}
$CurrentValue = (Get-ItemProperty @params).BlockNTLMServerExceptionList
$params["Value"] = if ($CurrentValue -eq $null) { @("") } else { $CurrentValue + "AddToList" }
Set-ItemProperty @params 
```

You can also add multiple variables to the `AddToList` parameter by separating them with a comma, as shown in the following example command:

```powershell
$params = @{
  Path = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\LanmanWorkstation"
  Name = "BlockNTLMServerExceptionList"
}
$CurrentValue = (Get-ItemProperty @params).BlockNTLMServerExceptionList
$params["Value"] = if ($CurrentValue -eq $null) { @("") } else { $CurrentValue + "192.168.10.10","corp.contoso.com","CORP" }
Set-ItemProperty @params 
```

---

## Block NTLM while mapping SMB drives

You can also block NTLM when mapping new SMB drives by running the following commands.

Run this command to specify NTLM blocking when mapping a drive with NET USE:

```powershell
NET USE \\server\share /BLOCKNTLM
```

Run this command to specify NTLM blocking when mapping an SMB drive:

```powershell
New-SmbMapping -RemotePath \\server\share -BlockNTLM $true
```