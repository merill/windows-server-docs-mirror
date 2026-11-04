---
layout: Conceptual
title: Use Windows LAPS event logs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-management-event-log
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about key events in Windows Local Administrator Password Solution (Windows LAPS) and how to view the logs.
author: jay98014
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: b59916bb-bdd4-2a82-3764-98ffc404abd7
document_version_independent_id: b59916bb-bdd4-2a82-3764-98ffc404abd7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/laps/laps-management-event-log.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/laps/laps-management-event-log
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/laps/laps-management-event-log.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 159297d8-a66f-511e-f308-c695f34289be
---

# Use Windows LAPS event logs | Microsoft Learn

Windows Local Administrator Password Solution (Windows LAPS) has a dedicated event log channel. All Windows LAPS operations are tracked with rich eventing. Learn about key events and how to view the log.

## View the event log

To view the Windows LAPS event log channel, in Windows Server Event Viewer, go to **Applications and Services** &gt; **Logs** &gt; **Microsoft** &gt; **Windows** &gt; **LAPS** &gt; **Operational**.

![Screenshot of the event log and a Windows LAPS policy processing started event log message.](media/laps-management-event-log/laps-management-event-log-event-log.png)

## Key events

It's important to be aware of some key Windows LAPS events and how to view them in the event logs:

- Policy processing start and end events
- Policy configuration details
- Password update confirmation events
- Blocked external password modification request
- Post-authentication-action related events

### Policy processing cycle start and end

When Windows LAPS begins a background policy processing cycle, the progress of the operation is tracked in the event log. Knowing the specific events that indicate the start and end of each cycle makes it easy to read the event log and understand the events.

Each background policy processing cycle starts with a 10003 event:

```output
LAPS policy processing is now starting.
```

Each 10003 event is followed by several other events that describe what's happening. When the cycle finishes, the final event marks the operation as succeeded or failed.

A successful cycle is tracked with a 10004 event. Here's an example of a 10004 event:

```output
LAPS policy processing succeeded.
```

A failed cycle is tracked with a 10005 event. Here's an example of a 10005 event:

```output
LAPS policy processing failed with the error code below.

Error code: 80070032
```

If a failure occurs, you can use the error code to troubleshoot. You also can look at the intervening events for detailed information.

### Policy configuration details

When password backup is enabled, a policy configuration event is emitted during each Windows LAPS background policy processing cycle. The event logs the specific policy setting value for each cycle iteration.

When the policy is configured to back up the password to Windows Server Active Directory, a 10021 event is logged. Here's an example of a 10021 event:

```output
The current LAPS policy is configured as follows:

Policy source: GPO
Backup directory: Active Directory
Local administrator account name:
Password age in days: 30
Password complexity: 4
Password length: 14
Password expiration protection enabled: 1
Password encryption enabled: 1
Password encryption target principal: LapsAdministrators@contoso.com
Password encrypted history size: 12
Backup DSRM password on domain controllers: 0
Post authentication grace period (hours): 8
Post authentication actions: 1
```

When the policy is configured to back up the password to Microsoft Entra ID, a 10022 event is logged. Here's an example of a 10022 event:

```output
The current LAPS policy is configured as follows:

Policy source: CSP
Backup directory: Azure AD
Local administrator account name: ContosoLocalAdminAccount
Password age in days: 7
Password complexity: 4
Password length: 64
Post authentication grace period (hours): 8
Post authentication actions: 3
```

When Windows LAPS is configured to use a legacy Microsoft LAPS policy, a 10023 event is logged. Here's an example of a 10023 event:

```output
The current LAPS policy is configured as follows:

Policy source: Legacy LAPS
Backup directory: Active Directory
Local administrator account name:
Password age in days: 30
Password complexity: 4
Password length: 8
Password expiration protection enabled: 0
```

These specific policy setting values are examples and shouldn't be considered recommendations.

### Password update confirmation events

When Windows LAPS successfully updates the configured directory (Windows Server Active Directory or Microsoft Entra ID) with a new password, a success event is logged: 10018 for password updates in Windows Server Active Directory, and 10029 for password updates in Microsoft Entra ID.

Here's an example of a 10018 event:

```output
LAPS successfully updated Active Directory with the new password.
```

Here's an example of a 10029 event:

```output
LAPS successfully updated Azure Active Directory with the new password.
```

When the directory is updated with the new password, Windows LAPS also updates the managed local account. A 10020 event is logged on success.

Here's an example of a 10020 event:

```output
LAPS successfully updated the local admin account with the new password.

Account name: ContosoLocalAdminAccount
Account RID: 1087
```

### Blocked external password modification request

When Windows LAPS is enabled, it protects the password for the specified managed account from modification by any entity other than Windows LAPS. A 10031 event is logged when an attempt to change the password is blocked.

Here's an example of a 10031 event:

```output
LAPS blocked an external request that tried to modify the password of the current managed account.

Account name: ContosoLocalAdminAccount
Account RID: 1087
```

### Post-authentication action events

When post-authentication actions are configured, Windows LAPS monitors for successful authentications by the specified managed account. When an authentication is detected, a 10041 event is logged.

Here's an example of a 10041 event:

```output
LAPS detected a successful authentication for the currently managed account. A background task has been scheduled to execute the configured post-authentication actions after the configured grace period has expired.%n

Account name: ContosoLocalAdminAccount
Account RID: 1087
Password reset timer deadline: %3%n
```

When the deadline that's listed in the 10041 event is reached, Windows LAPS logs a 10042 event:

```output
The post-authentication grace period has expired per policy. The configured post-authentication actions will now be executed.

Account name: ContosoLocalAdminAccount
Account RID: 1087
```

Windows LAPS then attempts to rotate the password and execute any specified post-authentication actions. A 10044 event is logged when the password rotation succeeds.

Here's an example of a 10044 event:

```output
LAPS successfully reset the password for the currently managed account and completed all configured post-authentication actions.%n
%n
Account name: ContosoLocalAdminAccount
Account RID: 1087
```

If the password rotation fails, a 10043 event is logged. Here's an example of a 10043 event:

```output
LAPS failed to reset the password for the currently managed account. The password is considered expired due to an authentication event. LAPS will continue retrying the password reset operation until it succeeds.

Account name: ContosoLocalAdminAccount
Account RID: 1087
Password reset retry count: 1
Error code: 80070032
```

## Client event log versus AD domain controller event log

The Windows LAPS event log channel contains events related to the local machine acting as a client. The Windows LAPS event log channel on an Active Directory domain controller only contains events related to management of the local DSRM account (if enabled), and never contains any events related to domain-joined client behaviors.