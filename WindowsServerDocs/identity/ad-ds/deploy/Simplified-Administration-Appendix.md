---
layout: Conceptual
title: Simplified Administration Appendix | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/simplified-administration-appendix
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Simplified Administration Appendix'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 509ba4c3-e39a-0775-0fd4-b71ac99a715c
document_version_independent_id: 5cff4f3c-0a12-7ada-c667-314697daf06e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/deploy/Simplified-Administration-Appendix.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/deploy/simplified-administration-appendix
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/deploy/Simplified-Administration-Appendix.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 8e243fe4-f28f-e157-ecc2-912c84b0ef42
---

# Simplified Administration Appendix | Microsoft Learn

- [Server Manager Add Servers Dialog (Active Directory)](simplified-administration-appendix#BKMK_AddServers)
- [Server Manager Remote Server Status](simplified-administration-appendix#BKMK_ServerMgrStatus)
- [Windows PowerShell Module Loading](simplified-administration-appendix#BKMK_PSLoadModule)
- [RID Issuance Hotfixes for Previous Operating Systems](simplified-administration-appendix#BKMK_Rid)
- [Ntdsutil.exe Install from Media Changes](simplified-administration-appendix#BKMK_IFM)

## Server Manager Add Servers Dialog (Active Directory)

The **Add Servers** dialog allows searching Active Directory for servers, by operating system, using wildcards, and by location. The dialog also allows using DNS queries by fully qualified domain name or prefix name. These searches use native DNS and LDAP protocols implemented through .NET, not AD Windows PowerShell against the AD Management Gateway through SOAP - meaning that the domain controllers contacted by Server Manager can even run Windows Server 2003. You can also import a file with server names for provisioning purposes.

The Active Directory search uses the following LDAP filters:

```
(&(ObjectCategory=computer)

(&(ObjectCategory=computer)(cn=dc*)(OperatingSystemVersion=6.2*))

(&(ObjectCategory=computer)(OperatingSystemVersion=6.1*))

(&(ObjectCategory=computer)(OperatingSystemVersion=6.0*))

(&(ObjectCategory=computer)(|(OperatingSystemVersion=5.2*)(OperatingSystemVersion=5.1*)))

```

The Active Directory search returns the following attributes:

```
( dnsHostName )( operatingSystem )( cn )

```

## Server Manager Remote Server Status

Server Manager tests remote server accessibility using Address Routing Protocol. Any servers not responding to ARP requests aren't listed, even if they are in the pool.

If ARP responds, then DCOM and WMI connections are made to the server to return status information. If RPC, DCOM, and WMI are unreachable, server manager can't fully manage the server.

## Windows PowerShell Module Loading

Windows PowerShell 3.0 implements dynamic module loading. Using the **Import-Module** cmdlet is typically no longer required; instead, simply invoking the cmdlet, alias, or function automatically loads the module.

To see loaded modules, use the **Get-Module** cmdlet.

```
Get-Module

```

![Simplified Administration](media/simplified-administration-appendix/adds_psgetmodule.gif)

To see all installed modules with their exported functions and cmdlets, use:

```
Get-Module -ListAvailable

```

The main case for using the **import-module** command is when you need access to the "AD:" Windows PowerShell virtual drive and nothing else has already loaded the module. For example, using the following commands:

```
import-module activedirectory
cd ad:
dir

```

## RID Issuance Hotfixes for Previous Operating Systems

See [An update is available to detect and prevent too much consumption of the global RID pool on a domain controller that is running Windows Server 2008 R2](https://support.microsoft.com/kb/2618669).

## Ntdsutil.exe Install from Media Changes

Windows Server 2012 adds two additional options to the Ntdsutil.exe command-line tool for the **IFM (IFM Media Creation)** menu. These allow you to create IFM stores without first performing an offline defrag of the exported NTDS.DIT database file. When disk space isn't a premium, this saves time creating the IFM.

The following table describes the two new menu items:

| Menu Item | Explanation |
| --- | --- |
| Create Full NoDefrag %s | Create IFM media without defragmenting for a full AD DC or an AD/LDS instance into folder %s |
| Create Sysvol Full NoDefrag %s | Create IFM media with SYSVOL and without defragmenting for a full AD DC into folder %s |

![Screenshot of a terminal window that shows the process for creating IFM media.](media/simplified-administration-appendix/adds_psifm.png)

![Screenshot of a terminal window that shows the IFM media was successfully created.](media/simplified-administration-appendix/adds_psifmcomplete.gif)