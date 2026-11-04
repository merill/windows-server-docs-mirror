---
layout: Conceptual
title: Enable SAM Client Event Logging in Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/enable-sam-client-logging-diagnostics
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to enable Security Account Manager (SAM) client event logging and tracing to diagnose SAM client activity in Windows 11.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.reviewer: sanaray
ms.date: 2026-07-16T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 89351ab2-eb5f-b8c3-9cb0-088b08fe1f54
document_version_independent_id: 89351ab2-eb5f-b8c3-9cb0-088b08fe1f54
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/enable-sam-client-logging-diagnostics.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/enable-sam-client-logging-diagnostics
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/enable-sam-client-logging-diagnostics.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 236bf716-23d7-cfe8-5bb4-e0bac79b4f1b
---

# Enable SAM Client Event Logging in Windows | Microsoft Learn

Security Account Manager (SAM) client event logging is a diagnostic capability in Windows that helps identify sources of excessive SAM traffic that can cause domain controller high central processing unit (CPU) usage and authentication delays. It records SAM client operations, such as account lookups and domain enumeration, through a dedicated event log channel.

When you troubleshoot an overloaded domain controller, you need to know which clients are generating the SAM traffic behind it. Enabling SAM client event logging pinpoints the processes, services, and executables responsible and reveals unexpected usage patterns, so you can target the actual source instead of guessing.

In this article, you enable and disable the SAM client event log, configure its logging options, and review the events it records and where to find them.

## Prerequisites

- Windows 11 with the [2026-06 Security Update (KB5095093)](https://support.microsoft.com/help/5095093) or later
- Administrator or equivalent access to the Windows system.

## Enable the SAM client event log

The SAM client event logging feature uses a dedicated event log channel that records SAM client operations in a consistent, administrator-friendly format.

To help protect potentially sensitive diagnostic data, only users with appropriate administrative privileges can enable the feature and access the resulting logs.

The SAM client event log records activity from any Windows system that generates SAM traffic toward a domain controller. This activity includes client and server stock keeping units (SKUs) and both domain-joined and non-domain-joined systems.

To enable SAM client logging, follow these steps:

1. Select the **Start** button, type **Event Viewer**, and open **Event Viewer** from the best match list.
2. In Event Viewer, go to **Applications and Services Logs** &gt; **Microsoft** &gt; **Windows** &gt; **SAMLIB**.
3. Select and hold (or right-click) **Debug**, and then select **Enable Log**.

    [![Screenshot of Event Viewer showing the SAMLIB Debug log with the Enable Log option highlighted in the context menu.](media/enable-sam-client-logging-diagnostics/enable-samlib-debug-log.png)](media/enable-sam-client-logging-diagnostics/enable-samlib-debug-log.png#lightbox)

When you enable the SAM client event log, it records operations such as connections, handle operations, domain lookups, and enumeration requests.

To stop logging, repeat these steps and select **Disable Log** in step 3.

## Review SAM client events

SAM client events record the operation and the process responsible for the call. The following table summarizes the common event IDs in the SAM client event log (the **SAMLIB** &gt; **Debug** channel in Event Viewer).

| Event ID | Operation | Event text | Description |
| --- | --- | --- | --- |
| 1000 | `SamConnect` | SamConnect called:ServerName: `<server>`DesiredAccess: `<access>`Calling process: `<process>` | Indicates a client connecting to a SAM server. Captures the target server and calling process. |
| 1002 | `SamCloseHandle` | SamCloseHandle called:SamHandle: `<handle>`Calling process: `<process>` | Records cleanup of SAM handles. Useful for validating proper client behavior. |
| 1010 | `SamLookupDomainInSamServer` | SamLookupDomainInSamServer called:ServerHandle: `<handle>`Name: `<name>`Calling process: `<process>` | Records domain lookup operations. Useful when correlating name resolution and lookup behavior. |
| 1012 | `SamEnumerateDomainsInSamServer` | SamEnumerateDomainsInSamServer called:ServerHandle: `<handle>`PreferredMaximumLength: `<length>`Calling process: `<process>` | Indicates enumeration of available domains. Often appears during group or account queries. |
| 1014 | `SamOpenDomain` | SamOpenDomain called:ServerHandle: `<handle>`DesiredAccess: `<access>`DomainId: `<domain ID>`Calling process: `<process>` | Indicates that a client opens a domain handle. Helps identify access patterns and permission-related activity. |
| 1100 | `SamGetCompatibilityMode` | SamGetCompatibilityMode called:Handle: `<handle>`Calling process: `<process>` | Records the compatibility checks the client performs. Useful for understanding client behavior during initialization. |

Use these events to correlate process-level activity with observed behavior on domain controllers. The following screenshot shows an example of Event 1000 (SamConnect) in Event Viewer, including the server name, desired access, and calling process.

[!\[Screenshot of Event Viewer showing Event 1000 for SAMLIB with SamConnect details.\](media/enable-sam-client-logging-diagnostics/sam-event-1000-samconnect.png)
 The Event 1000 properties show: SamConnect called, ServerName (blank for local), DesiredAccess 0x30, and the calling process path (for example, `C:\Windows\system32\lsass.exe`). The Log Name is Microsoft-Windows-SAMLIB/Debug, Source is SAMLIB, and Level is Information.](media/enable-sam-client-logging-diagnostics/sam-event-1000-samconnect.png#lightbox)

## Manage command-line argument logging

By default, SAM client events identify the calling executable but omit command-line arguments. This default behavior protects against inadvertent exposure of sensitive data. For advanced scenarios, you can enable command-line argument logging by using a registry key.

Caution

Because command-line arguments can contain sensitive information such as credentials or user data, enable this setting only when necessary for targeted diagnostics and disable it immediately after data collection.

To enable command-line argument logging, follow these steps:

1. Open Registry Editor.
2. Go to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SAMLIB`.
3. Set the `IncludeArguments``REG_DWORD` value to `1` to enable command-line argument logging.

    [![Screenshot of Registry Editor showing the SAMLIB registry key with the IncludeArguments REG_DWORD value set to 0.](media/enable-sam-client-logging-diagnostics/samlib-includearguments-registry.png)](media/enable-sam-client-logging-diagnostics/samlib-includearguments-registry.png#lightbox)
4. To disable command-line argument logging, set `IncludeArguments` back to `0`.

After you change the registry value, restart the computer for the new setting to take effect.

The following table summarizes the `IncludeArguments` registry value behavior:

| Value | Behavior |
| --- | --- |
| `0` (default) | Events show the calling process without command-line arguments. |
| `1` | Events include the full command line of the calling process. |