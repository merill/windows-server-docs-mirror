---
layout: Conceptual
title: Manage SMB dialects in Windows and Windows Server 2025 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/manage-smb-dialects
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to manage SMB2 and SMB3 dialects using Group Policy and Windows PowerShell in Windows Server and Windows client.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2024-10-25T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 5d221a78-3628-ee71-5b3d-7aa760851c05
document_version_independent_id: 5d221a78-3628-ee71-5b3d-7aa760851c05
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/manage-smb-dialects.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/manage-smb-dialects
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/manage-smb-dialects.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 216c99ff-ac66-2d38-317f-d1fa0780a5f8
---

# Manage SMB dialects in Windows and Windows Server 2025 | Microsoft Learn

Administrators have the ability to manage SMB2 and SMB3 dialects in Windows Server and Windows client. In this article, learn how to configure a minimum and maximum SMB dialect for the SMB server and client using Group Policy and Windows PowerShell.

By default SMB Server and client automatically negotiates the highest matched dialect from SMB 2.0.2 to 3.1.1. Beginning with Windows 11, version 24H2, and [Windows Server 2025](/en-us/windows-server/get-started/whats-new-windows-server-2025), you can specify the SMB protocols used, blocking older, less secure, versions from connecting to the server. For example, you can specify connection to only use SMB 3.1.1, the most secure dialect of the protocol.

## Prerequisites

Before you can configure SMB dialects you need:

- An SMB server running on one of the following operating systems.
    - Windows Server 2025.
    - Windows 11, 24H2 or later.
- Administrative privileges to the computer.
- If you're using Group Policy on a domain, you need privileges to create or edit a Group Policy object (GPO) and link it to the appropriate organizational unit (OU).

## Configure maximum and minimum SMB dialects

You can configure the dialects available for negotiation using Group Policy or PowerShell. The minimum and maximum dialects can be set independently for the SMB server and client. Alternately, you can choose not to set a maximum. For example, you can set a minimum of 3.1.1 which effectively sets the maximum to 3.1.1.

## SMB server

You can configure the dialects available to your SMB server (that is, for inbound connections), by following these steps:

# [PowerShell](#tab/powershell)
Here's how to configure the minimum and maximum SMB dialects for the SMB server using PowerShell using the [Set-SmbServerConfiguration](/en-us/powershell/module/smbshare/set-smbserverconfiguration) cmdlet:

From an elevated PowerShell prompt, run the following commands:

```powershell
Set-SmbServerConfiguration -Smb2DialectMax {SMB202 | SMB210 |
SMB300 | SMB302 | SMB311 | None} -Smb2DialectMin {None | SMB202 | SMB210 | SMB300 | SMB302 | SMB311}
```

For example, to set the minimum dialect to SMB 3.0.0 and maximum dialects to SMB 3.1.1, run the following command:

```powershell
Set-SmbServerConfiguration -Smb2DialectMax SMB311 -Smb2DialectMin SMB300
```

# [Group Policy](#tab/group-policy)
Here's how to configure the minimum and maximum SMB dialects for the SMB server using Group Policy for domain joined machines.

To configure SMB dialect minimum and maximum for the SMB server:

1. Open the **Group Policy Management Console**.
2. Edit or create a Group Policy Object (GPO) that you want to use.
3. In the console tree, select **Computer Configuration &gt; Administrative Templates &gt; Network &gt; Lanman Server**.
4. For the setting, right-click **Mandate the Minimum version of SMB** and select **Edit**.
5. Select the minimum version of the dialects using a dropdown menu and select **OK**.
6. For the setting, right-click **Mandate the Maximum version of SMB** and select **Edit**.
7. Select the maximum version of the dialects using a dropdown menu and select **OK**.

---

## SMB client

You can configure the dialects available to your SMB client (that is, for outbound connections), by following these steps:

# [PowerShell](#tab/powershell)
Here's how to configure the minimum and maximum SMB dialects for the SMB client using PowerShell using the [Set-SmbClientConfiguration](/en-us/powershell/module/smbshare/set-smbclientconfiguration) cmdlet:

From an elevated PowerShell prompt, run the following commands:

```powershell
Set-SmbClientConfiguration -Smb2DialectMax {SMB202 | SMB210 |
SMB300 | SMB302 | SMB311 | None} -Smb2DialectMin {None | SMB202 | SMB210 | SMB300 | SMB302 | SMB311}
```

For example, to set the minimum and maximum dialects to SMB 3.1.1, run the following command:

```powershell
Set-SmbClientConfiguration -Smb2DialectMax SMB311 -Smb2DialectMin SMB311
```

# [Group Policy](#tab/group-policy)
Here's how to configure the minimum and maximum SMB dialects for the SMB client using Group Policy for domain joined machines.

To configure SMB dialect minimum and maximum for the SMB client:

1. Open the **Group Policy Management Console**.
2. Edit or create a Group Policy Object (GPO) that you want to use.
3. In the console tree, select **Computer Configuration &gt; Administrative Templates &gt; Network &gt; Lanman Workstation**.
4. For the setting, right-click **Mandate the minimum version of SMB** and select **Edit**.
5. Select the minimum version of the dialects using a dropdown menu and select **OK**.
6. For the setting, right-click **Mandate the maximum version of SMB** and select **Edit**.
7. Select the maximum version of the dialects using a dropdown menu and select **OK**.

    ![Screenshot showing group policy editor and select SMB version dropdown.](media/manage-smb-dialects/select-minimum-maximum.jpg)

---

## Verify dialect negotiation

You can use a network capture tool like Wireshark to examine the client and server responses during negotiation of the SMB protocol. In the following example, the client requests SMB 3.1.1 only because it's configured with a minimum and maximum dialect of 3.1.1:

![Screenshot showing ethernet capture of SMB session creation.](media/manage-smb-dialects/capture-smb-session-creation.jpg)