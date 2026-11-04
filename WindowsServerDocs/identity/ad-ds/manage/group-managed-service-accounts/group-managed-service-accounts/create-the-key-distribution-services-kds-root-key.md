---
layout: Conceptual
title: Create a Key Distribution Service (KDS) Root Key | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/create-the-key-distribution-services-kds-root-key
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to create a Key Distribution Service root key on a domain controller by using Windows PowerShell to generate group Managed Service Account passwords in Windows Server 2012 or later.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-09T00:00:00.0000000Z
locale: en-us
document_id: 49ebbb7b-d760-706c-e8ac-05a92b8d4817
document_version_independent_id: 49ebbb7b-d760-706c-e8ac-05a92b8d4817
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/create-the-key-distribution-services-kds-root-key.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/create-the-key-distribution-services-kds-root-key
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/create-the-key-distribution-services-kds-root-key.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6c57776-ab71-4356-880c-c5ff411d7fe1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e2d3fbf8-36df-4730-9ac5-e1c53887f039
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 4066d663-dc97-b52c-71b9-3e1a30226662
---

# Create a Key Distribution Service (KDS) Root Key | Microsoft Learn

This article for IT professionals describes how to create a Key Distribution Service (kdssvc.dll) root key on the domain controller by using Windows PowerShell to generate group Managed Service Account passwords in Windows Server 2012 or later.

Domain controllers (DC) require a root key to begin generating gMSA passwords. The domain controllers will wait up to 10 hours from time of creation to allow all domain controllers to converge their Active Directory replication before allowing the creation of a gMSA. Waiting up to 10 hours is a safety measure to prevent password generation from occurring before all DCs in the environment are capable of answering gMSA requests. Trying to use a gMSA too soon might fail when the gMSA host attempts to retrieve the password, because the key might not have been replicated to all domain controllers. gMSA password retrieval failures can also occur when you use DCs with limited replication schedules or if there's a replication issue.

Note

Deleting and re-creating the root key can lead to issues where the old key continues to be used after deletion due to caching of the key. The KDC should be restarted on all domain controllers if the root key is re-created.

Membership in the **Domain Admins** or **Enterprise Admins** groups, or the equivalent, is the minimum requirement for completing this procedure. For detailed information about using the appropriate accounts and group memberships, see [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

Note

A 64-bit architecture is required to run the Windows PowerShell commands that are used to administer group Managed Service Accounts.

#### To create the KDS root key by using the Add-KdsRootKey cmdlet

1. On the Windows Server 2012 or later domain controller, run Windows PowerShell from the Taskbar.
2. At the command prompt for the Windows PowerShell Active Directory module, type the following commands, and then select **Enter**:

    **Add-KdsRootKey -EffectiveImmediately**

    Tip

    You can use the Effective time parameter to provide time for keys to be propagated to all DCs before use. Using Add-KdsRootKey -EffectiveImmediately will add a root key to the target DC that will be used by the KDS service immediately. However, other domain controllers won't be able to use the root key until replication is successful.

KDS root keys are stored in Active Directory in container `CN=Master Root Keys,CN=Group Key Distribution Service,CN=Services,CN=Configuration,DC=<forest name>;`. They have an attribute msKds-DomainID that links to the computer account of the domain controller that created the object. When this domain controller is demoted and removed from the domain, the value will refer to the tombstone of the computer account. You can ignore the broken value because it's only used to help the administrator track the object when it's freshly created. You can also change the attribute value to point it to the computer object of another domain controller in your forest.

For test environments that have only one DC, you can create a KDS root key and set the start time in the past to avoid the interval wait for key generation by using the following procedure. Validate that a 4004 event has been logged in the KDS event log.

#### To create the KDS root key in a test environment for immediate effectiveness

1. On the Windows Server 2012 or later domain controller, run the Windows PowerShell from the Taskbar.
2. At the command prompt for the Windows PowerShell Active Directory module, type the following commands, and then select **Enter**:

    **$a=Get-Date**

    **$b=$a.AddHours(-10)**

    **Add-KdsRootKey -EffectiveTime $b**

    Or use a single command:

    **Add-KdsRootKey -EffectiveTime ((get-date).addhours(-10))**