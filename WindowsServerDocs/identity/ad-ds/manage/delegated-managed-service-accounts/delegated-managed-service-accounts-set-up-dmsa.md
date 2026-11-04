---
layout: Conceptual
title: Setting up delegated Managed Service Accounts (dMSA) in Windows Server 2025 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-set-up-dmsa
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to set up delegated Managed Service Accounts (dMSA) in Windows Server 2025 to ensure device credentials isolation in Active Directory.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-30T00:00:00.0000000Z
locale: en-us
document_id: 80316fd1-ca9e-9300-d7fc-da97966d8ada
document_version_independent_id: 80316fd1-ca9e-9300-d7fc-da97966d8ada
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-set-up-dmsa.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-set-up-dmsa
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-set-up-dmsa.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 15ede08b-ac99-fa66-07fa-aae89cc7d59e
---

# Setting up delegated Managed Service Accounts (dMSA) in Windows Server 2025 | Microsoft Learn

A delegated Managed Service Account (dMSA) is an Active Directory (AD) account that provides secure and efficient management of credentials. Unlike traditional service accounts, dMSAs don't require manual password management since AD automatically takes care of it. With dMSAs, specific permissions can be delegated to access resources in the domain, which reduces security risks and provides better visibility and logs of service account activity.

Setting up a dMSA is currently only available on devices running Windows Server 2025. DMSA is a more secure and manageable approach to service account management compared to traditional service accounts. By migrating critical services to dMSA, organizations can ensure that these services are managed in a secure and compliant manner. DMSA provides a higher level of security by offering unique and frequently rotated passwords, which reduces the likelihood of unauthorized access and improves overall security.

## Prerequisites

- The **Active Directory Domain Services** role must be installed on your device or on any device if using remote management tools. To learn more, see [Install or Uninstall Roles, Role Services, or Features](/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features).
- Once the role is installed, your device must be promoted to a Domain Controller (DC). In **Server Manager**, the flag icon displays a new notification. Select **Promote this server to a domain controller**, then complete the necessary steps.
- You must be a member of the **Domain Admins** or **Enterprise Admins** group, or have equivalent AD permissions, to create or migrate to a dMSA.
- Ensure that a two-way forest trust is established between the relevant AD forests to support authentication for cross-domain and cross-forest scenarios with dMSA.
- The **KDS root key** must be generated on the DC before a dMSA is created or migrated. Run `Get-KdsRootKey` in PowerShell to verify if the key is available. If the key is unavailable, it can be added by running `Add-KdsRootKey –EffectiveTime ((get-date).addhours(-10))`.

    Note

    In order to use the dMSA as a standalone Managed Service Account (MSA) or to supersede a legacy service account, the following command needs to be ran on the client device:

    ```powershell
    $params = @{
     Path = "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\Parameters"
     Name = "DelegatedMSAEnabled"
     Value = 1
     Type = "DWORD"
    }
    Set-ItemProperty @params
    ```

## Create a standalone dMSA

The following instructions allow users to create a new dMSA without migrating from a traditional service account.

1. Open a PowerShell session with admin rights and run:

    ```powershell
    $params = @{
     Name = "ServiceAccountName"
     DNSHostName = "DNSHostName"
     CreateDelegatedServiceAccount = $true
     KerberosEncryptionType = "AES256"
    }
    New-ADServiceAccount @params
    ```
2. Grant permission to the specific device to retrieve the password for the service account in AD:

    ```powershell
    $params = @{
     Identity = "DMSA Name"
     PrincipalsAllowedToRetrieveManagedPassword = "Machine$"
    }
    Set-ADServiceAccount @params
    ```
3. The **msDS-DelegatedMSAState** property value for the dMSA must be set to **3**. To view the current property value, run:

    ```powershell
    $params = @{
     Identity = "dMSAsnmp"
     Properties = "msDS-DelegatedMSAState"
    }
    Get-ADServiceAccount @params
    ```

    To set this value to **3**, run:

    ```powershell
    $params = @{
     Identity = "dMSAsnmp"
     Properties = @{
      "msDS-DelegatedMSAState" = 3
     }
    }
    Set-ADServiceAccount @params
    ```

## Migrate to a dMSA

To migrate a service account to a dMSA, follow these steps:

1. Create a dMSA a described in Create a standalone dMSA.
2. Initiate account migration to a dMSA:

    ```powershell
    $params = @{
     Identity = "<DMSAName>"
     SupersededAccount = "<DN of service account>"
    }
    Start-ADServiceAccountMigration @params
    ```
3. If the service account being migrated to a dMSA has access to multiple servers, a registry policy must first be applied to ensure it defaults to the DC. Once you sign in using the dMSA, run:

    ```powershell
    $params = @{
     Path = "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\Kerberos\Parameters"
     Name = "DelegatedMSAEnabled"
     Value = "1"
     PropertyType = "DWORD"
     Force = $true
    }
    New-ItemProperty @params
    ```
4. Once changes to the registry are applied and the account is linked, restart the running services for the account by running:

    ```powershell
    Get-Service | Where-Object {$_.Status -eq "Running"} | Restart-Service
    ```

Note

In the case that the service account is connected to multiple devices and migration has ended, the [PrincipalsAllowedToRetrieveManagedPassword](/en-us/powershell/module/activedirectory/set-adserviceaccount?view=windowsserver2022-ps#example-3-set-the-principals-allowed-to-retrieve-the-password-for-an-msa&amp;preserve-view=true) needs to be updated manually.

### Complete account migration

Warning

When finalizing the migration, **never** delete the original service account in case you need to revert back to it post migration as this causes several issues.

To complete the account migration, traditional service accounts must be disabled to ensure that all services use the dMSA.

To disable the traditional service account, run the following command:

```powershell
$params = @{
 Identity = "<DMSAName>"
 SupersededAccount = "<DN of service account>"
}
Complete-ADServiceAccountMigration @params
```

If the wrong account is being migrated, run the following to undo all steps during migration:

```powershell
$params = @{
 Identity = "<DMSAName>"
 SupersededAccount = "<DN of service account>"
}
Undo-ADServiceAccountMigration @params
```

To revert a service account back to an inactive or unlinked state, run:

```powershell
$params = @{
 Identity = "<DMSAName>"
 SupersededAccount = "<DN of service account>"
}
Reset-ADServiceAccountMigration @params
```

## View dMSA event logs

Events can be viewed using the Event Viewer (eventvwr.exe) by performing the following actions:

1. Right-click on **Start** and select **Event Viewer**.
2. In the left pane, expand **Applications and Services** and navigate to **Microsoft\Windows\Security-Kerberos\Operational**.
3. Logging for this provider is disabled by default, to enable logging, right-click on **Operational** and select **Enable Log**.

The following table describes these captured events.

| Event ID | Description |
| --- | --- |
| 307 | **dMSA Migration** - This event is written for both dMSAs under migration and for ones that migrated. It contains information about the old service account and the new dMSA. |
| 308 | **dMSA Permission Add** - This event is logged when a machine attempts to add itself to the principals allowed to retrieve managed password field of a dMSA during migration. |
| 309 | **dMSA Key Fetch** - This event is logged when the Kerberos client attempts to fetch keys for a dMSA from the domain controller. |