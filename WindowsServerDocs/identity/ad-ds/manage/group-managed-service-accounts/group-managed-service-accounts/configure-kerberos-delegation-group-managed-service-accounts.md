---
layout: Conceptual
title: Configuring Kerberos Delegation for Group Managed Service Accounts | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/configure-kerberos-delegation-group-managed-service-accounts
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Explains how to configure Kerberos delegation for group Managed Service Accounts.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-09T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: b7e0a894-0c98-0b80-c84c-a906403eed62
document_version_independent_id: b7e0a894-0c98-0b80-c84c-a906403eed62
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/configure-kerberos-delegation-group-managed-service-accounts.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/configure-kerberos-delegation-group-managed-service-accounts
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/configure-kerberos-delegation-group-managed-service-accounts.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 29250a1f-719b-31d2-1f68-88a1fe88bb6c
---

# Configuring Kerberos Delegation for Group Managed Service Accounts | Microsoft Learn

Normally, when you work with Kerberos delegation, you set the service principal name (SPN) either with a setspn.exe command or manually by using the attribute editor in Active Directory Users and Computers. Additionally, enabling **View** &gt; **Advanced features** in Active Directory Users and Computers adds another way to configure Kerberos delegation from the **Delegation** tab of a user or a computer account.

But for standalone and group Managed Service Accounts, the **Delegation** tab doesn't appear, even after you add SPNs to these accounts or enable **View** &gt; **Advanced features**.

To configure delegation for these special accounts, you need to set the correct attributes manually. There are two attributes that you need to modify for these accounts:

- userAccountControl defines the type of delegation.
- msDS-AllowedToDelegateTo defines where the SPNs for delegation will be added.

You can set these attributes in two ways:

- Use PowerShell.
- Manually update the userAccountControl value.

## Use PowerShell commands

The more secure and convenient way is to use PowerShell commands to update those attributes. You don't need to calculate final userAccountControl values when using PowerShell. Here are the commands to enable different types of delegation:

- **Don't trust this computer for delegation**

    ```powershell
    Set-ADAccountControl -Identity TestgMSA$ -TrustedForDelegation $false -TrustedToAuthForDelegation $false
    Set-ADServiceAccount -Identity TestgMSA$ -Clear 'msDS-AllowedToDelegateTo'
    ```
- **Unconstrained delegation / Trust this computer for delegation to any service**

    ```powershell
    Set-ADAccountControl -Identity TestgMSA$ -TrustedForDelegation $true -TrustedToAuthForDelegation $false
    Set-ADServiceAccount -Identity TestgMSA$ -Clear 'msDS-AllowedToDelegateTo'
    ```
- **Kerberos-constrained delegation / Trust this computer for delegation to specified services only (Use Kerberos only)**

    ```powershell
    Set-ADAccountControl -Identity TestgMSA$ -TrustedForDelegation $false -TrustedToAuthForDelegation $false
    ```

    Update the Backend Service SPNs in msDS-AllowedToDelegateTo attribute.
- **Kerberos-constrained delegation with protocol transition / Trust this computer for delegation to specified services only (Use any authentication protocol)**

    ```powershell
    Set-ADAccountControl -Identity TestgMSA$ -TrustedForDelegation $false -TrustedToAuthForDelegation $true
    ```

    Update the Backend Service SPNs in msDS-AllowedToDelegateTo attribute.

## Manually update the userAccountControl value

Some of the easiest ways to modify attributes are by enabling **View** &gt; **Advanced features** in Active Directory Users and Computers or by using ADSIEdit.msc.

Here are the userAccountControl values that can be added for different types of delegation. Be careful when you edit this attribute value. Ensure that only the TRUSTED\_FOR\_DELEGATION or TRUSTED\_TO\_AUTH\_FOR\_DELEGATION flag is added, and that other properties aren't changed. Also, ensure that both the flags aren't added together in the userAccountControl value on a Managed Service Account.

| Delegation type | Property flag | Value in hexadecimal | Value in decimal |
| --- | --- | --- | --- |
| Unconstrained delegation / Trust this computer for delegation to any service | TRUSTED\_FOR\_DELEGATION | 0x80000 | 524288 |
| Kerberos-constrained delegation / Trust this computer for delegation to specified services only (Use Kerberos only) | No change | No change | No change |
| Kerberos-constrained delegation with protocol transition / Trust this computer for delegation to specified services only (Use any authentication protocol) | TRUSTED\_TO\_AUTH\_FOR\_DELEGATION | 0x1000000 | 16777216 |

When you manually update the userAccountControl value, make sure the new value is added with the existing value and doesn't replace the existing value. For example, say the current value of UAC is 4096 (hexadecimal 0x1000), which is WORKSTATION\_TRUST\_ACCOUNT:

![Screenshot that shows a userAccountControl value of 4096.](media/user-account-control-4096.png)

To enable **Unconstrained delegation (Not secure)**, you must add the userAccountControl value for TRUSTED\_FOR\_DELEGATION together with the existing value. The UAC value should become 0x81000 (0x1000 + 0x80000), which means WORKSTATION\_TRUST\_ACCOUNT and TRUSTED\_FOR\_DELEGATION.

![Screenshot that shows a userAccountControl value of 81000.](media/user-account-control-81000.png)

If you add SPNs by mistake or want to remove SPNs from the delegation list of the account, you can manually edit the **msDS-AllowedToDelegateTo** attribute of the account. This method is applicable for any user or computer account.

![Screenshot that shows the msDS-AllowedToDelegateTo attribute in the Multi-valued String Editor.](media/allowed-to-delegate.png)