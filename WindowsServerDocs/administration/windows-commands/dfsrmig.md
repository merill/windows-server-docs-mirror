---
layout: Conceptual
title: dfsrmig | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dfsrmig
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the dfsrmig command, which migrates SYSvol replication from FRS to DFS Replication, provides information about the progress of the migration, and modifies AD DS objects to support the migration.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-01-03T00:00:00.0000000Z
locale: en-us
document_id: 3b39d577-4c79-3dbd-bf5e-4b1bf551f73e
document_version_independent_id: 4bead400-5af7-bd08-5bfe-8297cbc8dd85
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/dfsrmig.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/dfsrmig
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/dfsrmig.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 7b87a542-1955-18e9-6061-7c5f3503de0c
---

# dfsrmig | Microsoft Learn

The migration tool for the DFS Replication service, dfsrmig.exe, is installed with the DFS Replication service. This tool migrates SYSvol replication from File Replication Service (FRS) to Distributed File System (DFS) Replication. It also provides information about the progress of the migration and modifies Active Directory Domain Services (AD DS) objects to support the migration.

## Syntax

```
dfsrmig [/setglobalstate <state> | /getglobalstate | /getmigrationstate | /createglobalobjects |
/deleterontfrsmember [<read_only_domain_controller_name>] | /deleterodfsrmember [<read_only_domain_controller_name>] | /?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `/setglobalstate <state>` | Sets the domain's global migration state to one that corresponds to the value specified by *state*. You can only set the global migration state to a stable state. The *state* values include:<br>- **0** - Start state<br>- **1** - Prepared state<br>- **2** - Redirected state<br>- **3** - Eliminated state |
| /getglobalstate | Retrieves the current global migration state for the domain from the local copy of the AD DS database, when run on the PDC emulator. Use this option to confirm that you set the correct global migration state.<br>**Important:** You should only run this command on the PDC emulator. |
| /getmigrationstate | Retrieves the current local migration state for all domain controllers in the domain and determines whether those local states match the current global migration state. Use this option to determine if all domain controllers have reached the global migration state. |
| /createglobalobjects | Creates the global objects and settings in AD DS used by DFS Replication uses. The only situations where you should use this option to manually create objects and settings, are:<br>- **A new read-only domain controller is promoted during migration**. If a new read-only domain controller is promoted in the domain after moving into the **Prepared** state, but before migration to the **Eliminated** state, then the objects that correspond to the new domain controller aren't created, causing replication and the migration to fail.<br>- **Global settings for the DFS Replication service are missing or were deleted**. If these settings are missing for a domain controller, migration from the **Start** state to the **Prepared** state will stall at the **Preparing** transition state. **Note:** Because the global AD DS settings for the DFS Replication service for a read-only domain controller are created on the PDC emulator, these settings need to replicate to the read-only domain controller from the PDC emulator before the DFS Replication service on the read-only domain controller can use these settings. Because of Active Directory replication latencies, this replication can take some time to occur. |
| `/deleterontfrsmember [<read_only_domain_controller_name>]` | Deletes the global AD DS settings for FRS replication that correspond to the specified read-only domain controller, or deletes the global AD DS settings for FRS replication for all read-only domain controllers if no value is specified for `<read_only_domain_controller_name>`.<br>You shouldn't need to use this option during a normal migration process, because the DFS Replication service automatically deletes these AD DS settings during the migration from the **Redirected** state to the **Eliminated** state. Use this option to manually delete the AD DS settings only when the automatic deletion fails on a read-only domain controller and stalls the read-only domain controller for a long time during the migration from the **Redirected** state to the **Eliminated** state. |
| `/deleterodfsrmember [<read_only_domain_controller_name>]` | Deletes the global AD DS settings for DFS Replication that correspond to the specified read-only domain controller, or deletes the global AD DS settings for DFS Replication for all read-only domain controllers if no value is specified for `<read_only_domain_controller_name>`.<br>Use this option to manually delete the AD DS settings only when the automatic deletion fails on a read-only domain controller and stalls the read-only domain controller for a long time when rolling back the migration from the Prepared state to the start state. |
| /? | Displays help at the command prompt. |

#### Remarks

- Use the `/setglobalstate <state>` command to set the global migration state in AD DS on the PDC emulator to initiate and control the migration process. If the PDC emulator isn't available, this command fails.
- Migration to the **Eliminated** state is irreversible and rollback isn't possible, so use a value of **3** for *state* only when you are fully committed to using DFS Replication for SYSvol replication.
- Global migration states must be a stable migration state.
- Active Directory replication replicates the global state to other domain controllers in the domain, but because of replication latencies, you can get inconsistencies if you run `dfsrmig /getglobalstate` on a domain controller other than the PDC emulator.
- The output of `dfsrmig /getmigrationstate` indicates whether migration to the current global state is complete, listing the local migration state for any domain controllers that haven't yet reached the current global migration state. The local migration state for domain controllers can also include transition states for domain controllers that have not reached the current global migration state.
- Read-only domain controllers can't delete settings from AD DS, the PDC emulator performs this operation, and the changes eventually replicate to the read-only domain controllers after the applicable latencies for active directory replication.
- The **dfsrmig** command is supported only on domain controllers that run at the Windows Server domain functional level, because SYSvol migration from FRS to DFS Replication is only possible on domain controllers that operate at that level.
- You can run the **dfsrmig** command on any domain controller, but operations that create or manipulate AD DS objects are only allowed on read-write capable domain controllers (not on read-only domain controllers).

## Examples

To set the global migration state to Prepared (**1**) and to initiate migration or to rollback from the Prepared state, type:

```
dfsrmig /setglobalstate 1
```

To set the global migration state to Start (**0**) and to initiate rollback to the Start state, type:

```
dfsrmig /setglobalstate 0
```

To display the global migration state, type:

```
dfsrmig /getglobalstate
```

Output from the `dfsrmig /getglobalstate` command:

```
Current DFSR global state: Prepared
Succeeded.
```

To display information about whether the local migration states on all the domain controllers match the global migration state and if there are any local migration states where the local state doesn't match the global state, type:

```
dfsrmig /GetMigrationState
```

Output from the `dfsrmig /getmigrationstate` command when the local migration states on all of the domain controllers match the global migration state:

```
All Domain Controllers have migrated successfully to Global state (Prepared).
Migration has reached a consistent state on all Domain Controllers.
Succeeded.
```

Output from the `dfsrmig /getmigrationstate` command when the local migration states on some domain controllers don't match the global migration state.

```
The following Domain Controllers are not in sync with Global state (Prepared):
Domain Controller (Local Migration State) DC type
=========
CONTOSO-DC2 (start) ReadOnly DC
CONTOSO-DC3 (Preparing) Writable DC
Migration has not yet reached a consistent state on all domain controllers
State information might be stale due to AD latency.
```

To create the global objects and settings that DFS Replication uses in AD DS on domain controllers where those settings were not created automatically during migration or where those settings are missing, type:

```
dfsrmig /createglobalobjects
```

To delete the global AD DS settings for FRS replication for a read-only domain controller named contoso-dc2 if those settings were not deleted automatically by the migration process, type:

```
dfsrmig /deleterontfrsmember contoso-dc2
```

To delete the global AD DS settings for FRS replication for all read-only domain controllers if those settings were not deleted automatically by the migration process, type:

```
dfsrmig /deleterontfrsmember
```

To delete the global AD DS settings for DFS Replication for a read-only domain controller named contoso-dc2 if those settings were not deleted automatically by the migration process, type:

```
dfsrmig /deleterodfsrmember contoso-dc2
```

To delete the global AD DS settings for DFS Replication for all read-only domain controllers if those settings were not deleted automatically by the migration process, type:

```
dfsrmig /deleterodfsrmember
```

To display help at the command prompt:

```
dfsrmig
```

```
dfsrmig /?
```

## Related links

- [Command-Line Syntax Key](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc771080%28v=ws.11%29)
- [SYSvol Migration Series: Part 2 dfsrmig.exe: The SYSvol Migration Tool](https://techcommunity.microsoft.com/t5/storage-at-microsoft/sysvol-migration-series-part-2-8211-dfsrmig-exe-the-sysvol/ba-p/423470)
- [Active Directory Domain Services](../../identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)