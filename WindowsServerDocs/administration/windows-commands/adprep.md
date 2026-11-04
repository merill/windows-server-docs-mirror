---
layout: Conceptual
title: Adprep | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/adprep
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Learn about adprep command line tool to prepare a forest and domain for a domain controller for Windows Server.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2024-04-22T00:00:00.0000000Z
locale: en-us
document_id: d917b9b8-a8af-9406-b679-9d2abbb79974
document_version_independent_id: d917b9b8-a8af-9406-b679-9d2abbb79974
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/adprep.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/adprep
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/adprep.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9aeec447-0d7e-d2db-6b55-c6ef0ff94529
---

# Adprep | Microsoft Learn

Applies to: Windows Server (All supported versions)

The adprep command extends the Active Directory schema and updates permissions as necessary to prepare a forest and domain for a domain controller that runs Windows Server.

`Adprep.exe` is a command-line tool available in Windows Server. You must run **adprep** from an elevated command prompt. To open an elevated command prompt, select **Start**, right-select **Command Prompt**, and then select **Run as administrator**.

Adprep is available in a 32-bit version and a 64-bit version. The 64-bit version runs by default. If you need to run Adprep on a 32-bit computer, run the 32-bit version (Adprep32.exe).

For more information about running `Adprep.exe` and how to resolve errors that can occur when you run it, see [Running Adprep.exe](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd464018%28v=ws.10%29).

For examples of how this command can be used, see Examples.

For more information about running `adprep /forestprep`, see [Prepare a Windows 2000 or Windows Server 2003 Forest Schema for a Domain Controller that Runs Windows Server 2008 or Windows Server 2008 R2](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753437%28v=ws.10%29).

For more information about running `adprep /domainprep /gpprep`, see [Prepare a Windows 2000 or Windows Server 2003 Domain for a Domain Controller That Runs Windows Server 2008 or Windows Server 2008 R2](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754670%28v=ws.10%29).

For more information about running `adprep /rodcprep`, see [Prepare a Forest for a Read-Only Domain Controller](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771055%28v=ws.10%29).

## Syntax

adprep {/forestprep | /domainprep | /domainprep /gpprep | /rodcprep | /wssg | /silent }

## Parameters

| Parameter | Description |
| --- | --- |
| /forestprep | Prepares a forest for the introduction of a domain controller that runs Windows Server. You run this command only once in the forest. You must run this command on the domain controller that holds the schema operations master role (also known as flexible single master operations or FSMO) for the forest. You must be a member of all the following groups to run this command:<br><br>- The Enterprise Admins group<br>- The Schema Admins group<br>- The Domain Admins group of the domain that hosts the schema master |
| /domainprep | Prepares a domain for the introduction of a domain controller that runs Windows Server. You run this command after the **forestprep** command finishes and after the changes replicate to all the domain controllers in the forest.<br><br>Run this command in each domain where you plan to add a domain controller that runs Windows Server. You must run this command on the domain controller that holds the infrastructure operations master role for the domain. You must be a member of the Domain Admins group to run this command. |
| /domainprep <br><br>/gpprep | Performs similar updates to **domainprep**. However, this command also provides updates that are necessary to enable the Resultant Set of Policy (RSOP) Planning Mode functionality. <br><br>In Active Directory environments that run Microsoft Windows, this command performs updates during off-peak hours. Replicating updates to file system permissions and Active Directory permissions on existing Group Policy objects (GPOs) during off-peak hours minimizes replication traffic. <br><br>Run this command after the **forestprep** command finishes and after the changes replicate to all domain controllers in the forest. You must run this command on the infrastructure master for the domain. For more information about running this command in Windows Active Directory environments, see [Prepare Your Infrastructure for Upgrade](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc783495%28v=ws.10%29). |
| /rodcprep | This parameter updates permissions on the application directory partitions to enable replication of the partitions to read-only domain controllers (RODCs). This operation runs remotely; it contacts the infrastructure master in each domain to update the permissions. You need to run this command only once in the forest. However, you can rerun this command anytime if it fails to complete successfully because an infrastructure master isn't available. You can run this command on any computer in the forest. You must be a member of the Enterprise Admins group to run this command. |
| /wssg | Returns an expanded set of exit codes, instead of just 0 (Success) and 1 (Failure). |
| /silent | Specifies that no standard output is returned from an operation. This parameter can be used only if /wssg is also used. |
| quit | Returns to the prior menu. |
| Help | Displays Help for this command. |
| ? | Displays Help for this command. |

## Remarks

- To prepare an existing Windows or Windows Server Active Directory environment for a Windows Server domain controller, run the version of adprep included in the Windows Server installation media.
- You can also perform verification steps before and after you run the **adprep** command to help ensure that the operations complete successfully. For more information, see [Steps for Extending the Schema](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc773360%28v=ws.10%29).

## Exit Codes

The following table lists exit codes that Adprep can return after an operation completes.

| Return Code | Description |
| --- | --- |
| 1 | Failure |
| 2 | Schema conflict error |
| 3 | FSMO role error |
| 4 | Connection error |
| 5 | Schema upgrade error |
| 6 | Unable to modify error |
| 7 | Server busy error |
| 8 | Permission error |
| 9 | Unable to initialize log file error |
| 10 | Not a domain controller |
| 11 | In nonnative mode |
| 12 | Need to run forest update first |
| 13 | Forest update already done |
| 14 | Domain update already done |
| 15 | GPO update already done |
| 16 | Forest update wait replication |

## Examples

The following example prepares a forest for a domain controller that runs Windows Server:

```cli
adprep /forestprep
```

The following example prepares a domain for a domain controller that runs Windows Server:

```cli
adprep /domainprep
```

The following example prepares a domain for an RODC:

```cli
adprep /rodcprep
```