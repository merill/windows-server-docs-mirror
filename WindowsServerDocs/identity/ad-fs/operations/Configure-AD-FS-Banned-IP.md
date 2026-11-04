---
layout: Conceptual
title: Configure AD FS banned IP addresses | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-ad-fs-banned-ip
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn more about banned IP addresses in AD FS
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: ff4808bd-e241-3a8c-81ff-2d8cd7ffc56b
document_version_independent_id: f68f6660-5f5b-ed41-db50-124360edff5e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Configure-AD-FS-Banned-IP.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/configure-ad-fs-banned-ip
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Configure-AD-FS-Banned-IP.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6dc8d958-171d-ca2c-9fcf-ee332abd7415
---

# Configure AD FS banned IP addresses | Microsoft Learn

AD FS on Windows Server 2016 introduced **Banned IPs** as part of the AD FS June 2018 update. This update enables you to configure a set of IP addresses globally in AD FS so that requests coming from those IP addresses are blocked. Requests that have IP addresses in the **x-forwarded-for** or **x-ms-forwarded-client-ip** headers are also blocked by AD FS.

## Adding banned IPs

To add banned IPs to the global list, use the below PowerShell cmdlet:

```powershell
PS C:\ >Set-AdfsProperties -AddBannedIps "1.2.3.4", "::3", "1.2.3.4/16"
```

Allowed formats are as follows:

- IPv4
- IPv6
- CIDR format with IPv4 or v6

There's a limit of 300 entries for banned IP addresses. You can use CIDR or range format to deny a large block of entries with a single entry.

## Removing banned IPs

To remove banned IPs from the global list, use the following PowerShell cmdlet:

```powershell
PS C:\ >Set-AdfsProperties -RemoveBannedIps "1.2.3.4"
```

### Reading banned IPs

To read the current set of banned IP addresses, use the following PowerShell cmdlet:

```powershell
PS C:\ >Get-AdfsProperties
```

Example output:

```
BannedIpList                   : {1.2.3.4, ::3,1.2.3.4/16}
```

## Related links

[Best practices for securing Active Directory Federation Services](../deployment/best-practices-securing-ad-fs)

[Set-AdfsProperties](/en-us/powershell/module/adfs/set-adfsproperties)

[AD FS Operations](../ad-fs-operations)