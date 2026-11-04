---
layout: FAQ
title: Delegated Managed Service Accounts FAQ | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-faq
summary: >
  <p>This article contains answers to frequently asked questions (FAQs) about using Delegated Managed Service Accounts (dMSA) in Windows Server 2025.</p>
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Frequently asked questions about Delegated Managed Service Accounts (dMSA).
author: robinharwood
ms.author: roharwoo
ms.date: 2024-08-15T00:00:00.0000000Z
ms.topic: faq
locale: en-us
document_id: f804c40c-6cd4-8c2a-b615-d0180dcee623
document_version_independent_id: f804c40c-6cd4-8c2a-b615-d0180dcee623
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-faq.yml
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: faq
toc_rel: ../../../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
platformId: 172bcb43-f154-9712-4afb-39fd7fb13249
---

# Delegated Managed Service Accounts FAQ | Microsoft Learn

This article contains answers to frequently asked questions (FAQs) about using Delegated Managed Service Accounts (dMSA) in Windows Server 2025.

## General

### Can I just extend the schema to Windows Server 2025 and then use a Windows Server 2025 member server to start using dMSA without having a Windows Server 2025 Domain Controller (DC)?

No, you must have at least one Windows Server 2025 DC, which must be discoverable by the client or member server.

### My application server running a service account is behind a Read-Only DC (RODC) with no connectivity to a Read/Write DC. Is this a supported configuration for dMSA?

Yes, this configuration is supported provided the following prerequisites are met:

1. The dMSA account must be cached on the RODC.
2. The dMSA account must be manually added to the **PrincipalsAllowedToRetrieveManagedPassword** attribute of the machine by running the following command:

    ```powershell
    Set-ADServiceAccount -Identity dMSAFinApp -PrincipalsAllowedToRetrieveManagedPassword Client$
    ```

### Can I force a password reset for a dMSA account?

No, you can't force a password reset for a dMSA account.

## Migration

### Can I migrate a gMSA to a dMSA account?

No, this scenario isn't supported. To learn more, see [Delegated Managed Service Accounts overview](/en-us/windows-server/identity/ad-ds/manage/delegated-managed-service-accounts/delegated-managed-service-accounts-overview).

### I have three service accounts in my environment running different application workloads. Can I migrate all three service accounts to a single dMSA?

No, each service account must have its own dMSA. You can't migrate multiple service accounts to a single dMSA.

### Instead of migrating the service account, can I reconfigure all of my services to a new dMSA? If I have a SQL Server farm currently using a service account, and want to avoid the hassle of migration, can I replace my service account with a dMSA?

Yes, you can replace the service account with a dMSA. This process would require:

1. Creating a new dMSA account.
2. Reconfiguring the service to use the new dMSA account.
3. Retiring the old service account.

### Will my service start using the dMSA during the migration process or only after the migration is complete?

The service will start using the newly created and configured dMSA only after the migration process is complete.

### Can I delete the service account after migration? What should I do with the service account post-migration?

The service account is disabled, and its information, including permissions, SPNs, and delegation, will be moved to the dMSA account. However, you should keep the service account intact because:

1. The service is still configured with the service account and won't automatically change to the dMSA account. Deleting the service account stops the service.
2. The service account has forward and backward links to the dMSA account.

### I have three Windows Server 2022 operating systems and one Windows Server 2025 operating system running my SQL application. Can I migrate to dMSA in a Windows Server 2025 domain environment?

No, all your clients and/or servers must be running on dMSA-supported operating system to perform the migration.

### Can I reset the password of my service account after I have started the migration process but before it's complete?

No, it isn't recommended to reset the password during the migration process.

### What if I mistakenly migrated a service account that shouldn't have been migrated? Can I undo or unlink the migration?

Yes, you can undo a migration or unlink a service account and start from scratch. Use the `Undo-ADServiceAccountMigration` or `Reset-ADServiceAccountMigration` cmdlets.

### I have migrated a service account, and it's now automatically disabled. Can I move the service account to a different Organizational Unit (OU)?

Yes, you can move the disabled service account to another OU.