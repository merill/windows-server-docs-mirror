---
layout: Conceptual
title: Find the Current Active Directory Schema Version | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/find-active-directory-schema
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: This article describes how to find the current schema version in Active Directory for Windows Server.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-07-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 28663494-1825-5397-9e9f-876fae131f51
document_version_independent_id: 28663494-1825-5397-9e9f-876fae131f51
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/deploy/find-active-directory-schema.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/deploy/find-active-directory-schema
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/deploy/find-active-directory-schema.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 14a517e4-dc7e-406b-7718-44915c8e885e
---

# Find the Current Active Directory Schema Version | Microsoft Learn

An Active Directory (AD) schema is a set of rules that defines what kinds of object classes you can create in an AD forest. For more information, see [Active Directory schema (AD DS)](/en-us/windows/win32/ad/active-directory-schema).

This article walks you through how to find the schema version and Exchange Services schema version that your forest uses.

## Prerequisites

To perform the tasks described in this article, ensure that your environment meets the following requirements:

- Your machine should run Microsoft Exchange Server 2016 or later.
- You must install the Active Directory Domain Services (AD DS) role. To learn more, see [Install or uninstall roles, role services, or features](../../../administration/server-manager/install-or-uninstall-roles-role-services-or-features).
- The server must be a domain controller (DC).
- Users must be part of the Domain Admins or Enterprise Admins group.

## Finding the schema version

To find the current Active Directory schema version:

Note

The internal root domain used in this demo is **contoso.local**. You need to modify the DC= field to correspond with the AD configuration in your own environment.

Depending on your configuration, you might also need to import the AD PowerShell module by running the `Import-Module ActiveDirectory` command before you can start running AD cmdlets.

# [GUI](#tab/gui)
1. Open the **Start** menu.
2. Enter **ADSIEdit.msc**, and then select **Enter** to open **ADSI Edit**.
3. In the pane on the left side of the window, right-click **ADSI Edit**, and then select **Connect to**.
4. In the **Connection Settings** window, under **Select a well known Naming Context**, select **Schema**, and then select **OK**.
5. In the pane on the left side of the window, expand the schema for your DC.
6. Right-click **CN=Schema,CN=Configuration,DC=contoso,DC=local** and then select **Properties**.
7. In the **Attribute** list, scroll down until you find the *objectvVersion* attribute. The value is the schema version.

# [CMD](#tab/cmd)
Use the `DSQuery` command line. Run the following command:

```cmd
dsquery * "cn=schema,cn=configuration,dc=contoso,dc=local" -scope base -attr objectVersion
```

# [PowerShell](#tab/powershell)
Use the `Get-ItemProperty` PowerShell cmdlet. Run the following command:

```powershell
Get-ItemProperty 'AD:\CN=Schema,CN=Configuration,DC=contoso,DC=local' -Name objectVersion
```

---

When you finish, use the table in Mapping the objectVersion attribute to find which operating system (OS) version corresponds to your version number.

### Mapping the objectVersion attribute

The following table maps the number shown in the **objectVersion** attribute with its corresponding OS version:

| Version | Operating system |
| --- | --- |
| 91 | Windows Server 2025 |
| 88 | Windows Server 2022 |
| 88 | Windows Server 2019 |
| 87 | Windows Server 2016 |
| 69 | Windows Server 2012 R2 |
| 56 | Windows Server 2012 |
| 47 | Windows Server 2008 R2 |
| 44 | Windows Server 2008 RTM |
| 31 | Windows Server 2003 R2 |
| 30 | Windows Server 2003 RTM, Windows 2003 Service Pack 1, Windows 2003 Service Pack 2 |

## Find the current Exchange Schema version

To find the current Exchange Schema version, you can use one of the following methods:

# [GUI](#tab/gui)
1. Open the **Start** menu.
2. Enter **ADSIEdit.msc**, and then select **Enter** to open **ADSI Edit**.
3. In the pane on the left side of the window, right-click **ADSI Edit**, and then select **Connect to**.
4. In the **Connection Settings** window, under **Select a well known Naming Context**, select **Schema**, and then select **OK**.
5. In the pane on the left side of the window, expand the schema for your DC.
6. Select **CN=Schema,CN=Configuration,DC=contoso,DC=local**.
7. In the pane in the center of the window, scroll down the **Name** list and open **CN=ms-Exch-Schema-Version-Pt**.
8. In the **Attribute** list, scroll down until you find the *rangeUpper* attribute. The value is the schema version.

# [CMD](#tab/cmd)
Use the `DSQuery` command:

```cmd
dsquery * "CN=ms-Exch-Schema-Version-Pt,cn=schema,cn=configuration,dc=contoso,dc=local" -scope base -attr rangeUpper
```

# [PowerShell](#tab/powershell)
Run the `Get-ItemProperty` PowerShell cmdlet:

```powershell
Get-ItemProperty "AD:\CN=ms-Exch-Schema-Version-Pt,cn=schema,cn=configuration,$((get-addomain).DistinguishedName)" -Name rangeUpper
```

---

When you finish, use the information in Mapping the rangeUpper attribute to determine which version of Exchange Schema corresponds to your attribute value.

### Mapping the rangeUpper attribute

The following articles show how to map the **rangeUpper** attribute value with its corresponding Exchange Schema version:

- [Exchange 2016 Active Directory versions](/en-us/exchange/plan-and-deploy/prepare-ad-and-domains?view=exchserver-2016&amp;preserve-view=true#exchange-2016-active-directory-versions)
- [Exchange 2019 Active Directory versions](/en-us/exchange/plan-and-deploy/prepare-ad-and-domains?view=exchserver-2019&amp;preserve-view=true#exchange-2019-active-directory-versions)