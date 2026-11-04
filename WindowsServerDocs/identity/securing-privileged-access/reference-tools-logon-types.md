---
layout: Conceptual
title: Administrative tools and logon types reference - Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/securing-privileged-access/reference-tools-logon-types
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Identify the risk of credential exposure associated with different administrative tools
ms.topic: reference
ms.date: 2024-05-30T00:00:00.0000000Z
ms.author: roharwoo
author: robinharwood
ms.reviewer: mas
locale: en-us
document_id: 45afe575-a51d-94ce-d81e-092768a67518
document_version_independent_id: 13d4632e-9671-41e8-24cf-0301aa503d56
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/securing-privileged-access/reference-tools-logon-types.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/securing-privileged-access/reference-tools-logon-types
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/securing-privileged-access/reference-tools-logon-types.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d3911ba3-0771-06a6-b414-2d43f5b64a70
---

# Administrative tools and logon types reference - Windows Server | Microsoft Learn

This reference information is provided to help identify the risk of credential exposure associated with different administrative tools for remote administration.

In a remote administration scenario, credentials are always exposed on the source computer so a trustworthy privileged access workstation (PAW) is always recommended for sensitive or high impact accounts. Whether credentials are exposed to potential theft on the target (remote) computer depends primarily on the windows logon type used by the connection method.

This table includes guidance for the most common administrative tools and connection methods:

| Connection method | Logon type | Reusable credentials on destination | Comments |
| --- | --- | --- | --- |
| Log on at console | Interactive | v | Includes hardware remote access / lights-out cards or network-based keyboard, video, and mouse (KVM) input. |
| RUNAS | Interactive | v |  |
| RUNAS /NETWORK | NewCredentials | v | Clones current LSA session for local access, but uses new credentials when connecting to network resources. |
| Remote Desktop (success) | RemoteInteractive | v | If the remote desktop client is configured to share local devices and resources, those devices might be compromised as well. |
| Remote Desktop (failure - logon type was denied) | RemoteInteractive | - | By default, if RDP logon fails credentials are only stored briefly. This might not be the case if the computer is compromised. |
| Net use \* \\SERVER | Network | - |  |
| Net use \* \\SERVER /u:user | Network | - |  |
| MMC snap-ins to remote computer | Network | - | Example: Computer Management, Event Viewer, Device Manager, Services |
| PowerShell WinRM | Network | - | Example: Enter-PSSession server |
| PowerShell WinRM with CredSSP | NetworkClearText | v | New-PSSession server-Authentication Credssp-Credential cred |
| PsExec without explicit credentials | Network | - | Example: PsExec \\server cmd |
| PsExec with explicit credentials | Network + Interactive | v | PsExec \\server -u user -p pwd cmdCreates multiple logon sessions. |
| Remote Registry | Network | - |  |
| Remote Desktop Gateway | Network | - | Authenticating to Remote Desktop Gateway. |
| Scheduled task | Batch | v | Password is also saved as LSA secret on disk. |
| Run tools as a service | Service | v | Password is also saved as LSA secret on disk. |
| Vulnerability scanners | Network | - | Most scanners default to using network logons, though some vendors may implement non-network logons and introduce more credential theft risk. |

For web authentication, use the reference from the following table:

| Connection method | Logon type | Reusable credentials on destination | Comments |
| --- | --- | --- | --- |
| IIS "Basic Authentication" | NetworkCleartext(IIS 6.0+)<br>Interactive(prior to IIS 6.0) | v |  |
| IIS "Integrated Windows Authentication" | Network | - | NTLM and Kerberos Providers. |

Column Definitions:

- **Logon type** - Identifies the logon type initiated by the connection.
- **Reusable credentials on destination**- Indicates that the following credential types are stored in LSASS process memory on the destination computer where the specified account is logged on locally:
    - LM and NT hashes
    - Kerberos TGTs
    - Plaintext password (if applicable).

The symbols in this table defined as follows:

- (-) denotes when credentials aren't exposed.
- (v) denotes when credentials are exposed.

For management applications that aren't in this table, you can determine the logon type from the logon type field in the audit logon events. For more information, see [Audit logon events](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc787567%28v=ws.10%29).

In Windows-based computers, all authentications are processed as one of several logon types, regardless of which authentication protocol or authenticator is used. This table includes most common logon types and their attributes relative to credential theft:

| Logon type | # | Authenticators accepted | Reusable credentials in LSA session | Examples |
| --- | --- | --- | --- | --- |
| Interactive (also known as, Logon locally) | 2 | Password, Smartcard,other | Yes | Console logon;RUNAS;Hardware remote control solutions (such as Network KVM or Remote Access / Lights-Out Card in server)IIS Basic Auth (before IIS 6.0) |
| Network | 3 | Password,NT Hash,Kerberos ticket | No (except if delegation is enabled, then Kerberos tickets present) | NET USE;RPC calls;Remote registry;IIS integrated Windows auth;SQL Windows auth; |
| Batch | 4 | Password (stored as LSA secret) | Yes | Scheduled tasks |
| Service | 5 | Password (stored as LSA secret) | Yes | Windows services |
| NetworkCleartext | 8 | Password | Yes | IIS Basic Auth (IIS 6.0 and newer);Windows PowerShell with CredSSP |
| NewCredentials | 9 | Password | Yes | RUNAS /NETWORK |
| RemoteInteractive | 10 | Password, Smartcard,other | Yes | Remote Desktop (formerly known as "Terminal Services") |

Column definitions:

- **Logon type** - The type of logon requested.
- **#** - The numeric identifier for the logon type that is reported in audit events in the Security event log.
- **Authenticators accepted** - Indicates which types of authenticators are able to initiate a logon of this type.
- **Reusable credentials in LSA session** - Indicates whether the logon type results in the LSA session holding credentials, such as plaintext passwords, NT hashes, or Kerberos tickets that could be used to authenticate to other network resources.
- **Examples** - List of common scenarios in which the logon type is used.

Note

For more information about Logon Types, see [SECURITY_LOGON_TYPE enumeration](/en-us/windows/win32/api/ntsecapi/ne-ntsecapi-security_logon_type).

**Next steps**

[AD DS Design and Planning](../ad-ds/plan/ad-ds-design-and-planning)