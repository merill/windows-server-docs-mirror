---
layout: Conceptual
title: AD Forest Recovery - Seizing an Operations Master Role | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-seizing-operations-master-role
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Seizing an operations master role'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 7e6bb370-f840-4416-b5e2-86b0ba715f4f, inhenkel
locale: en-us
document_id: 4666f048-663d-dfa8-1632-e553a87c7d75
document_version_independent_id: 4666f048-663d-dfa8-1632-e553a87c7d75
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-seizing-operations-master-role.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-seizing-operations-master-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-seizing-operations-master-role.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 8c61207d-7678-8eb4-cac5-101a25f9db25
---

# AD Forest Recovery - Seizing an Operations Master Role | Microsoft Learn

Use the following procedure to seize an operations master role (also known as a flexible single master operations (FSMO) role). You can use Ntdsutil.exe, a command-line tool that is installed automatically on all DCs.

## Seize an operations master role

1. At the command prompt, type the following command, and then press ENTER:

    ```cli
    ntdsutil
    ```
2. At the **ntdsutil:** prompt, type the following command, and then press ENTER:

    ```cli
    roles
    ```
3. At the **FSMO maintenance:** prompt, type the following command, and then press ENTER:

    ```cli
    connections
    ```
4. At the **server connections:** prompt, type the following command, and then press ENTER:

    ```cli
    Connect to server ServerFQDN
    ```

    Where *ServerFQDN* is the fully qualified domain name (FQDN) of this DC, for example: **connect to server nycdc01.example.com**.

    If *ServerFQDN* does not succeed, use the NetBIOS name of the DC.
5. At the **server connections:** prompt, type the following command, and then press ENTER:

    ```cli
    quit
    ```
6. Depending on the role that you want to seize, at the **FSMO maintenance:** prompt, type the appropriate command as described in the following table, and then press ENTER.

| Role | Credentials | Command |
| --- | --- | --- |
| Domain naming master | Enterprise Admins | **Seize naming master** |
| Schema master | Schema Admins | **Seize schema master** |
| Infrastructure master **Note:** After you seize the infrastructure master role, you may receive an error later if you need to run Adprep /Rodcprep. For more information, see KB article [949257](https://support.microsoft.com/kb/949257). | Domain Admins | **Seize infrastructure master** |
| PDC emulator master | Domain Admins | **Seize pdc** |
| RID master | Domain Admins | **Seize rid master** |

After you confirm the request, Active Directory or AD DS attempts to transfer the role. When the transfer fails, some error information appears, and Active Directory or AD DS proceeds with the seizure. After the seizure is complete, a list of the roles and the Lightweight Directory Access Protocol (LDAP) name of the server that currently holds each role appears. You can also run **Netdom Query FSMO** at an elevated command prompt to verify current role holders.

Note

If this computer was not a RID master before the failure and you attempt to seize the RID master role, the computer tries to synchronize with a replication partner before accepting this role. However, because this step is performed when the computer is isolated, it will not succeed in synchronizing with a partner. Therefore, a dialog box appears asking you whether you want to continue with the operation despite this computer not being able to synchronize with a partner. Click **Yes**.