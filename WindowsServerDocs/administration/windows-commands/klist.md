---
layout: Conceptual
title: klist | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/klist
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the klist command, which displays a list of currently cached Kerberos tickets.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b48f1669-7f0c-d4fd-8458-9f7261362c0b
document_version_independent_id: 3f1c3c60-188f-301d-73c7-247512a53628
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/klist.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/klist
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/klist.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 46c44687-8eb3-c361-0c9a-373659be6d78
---

# klist | Microsoft Learn

Displays a list of currently cached Kerberos tickets.

Important

You must be at least a **Domain Admin**, or equivalent, to run all the parameters of this command.

## Syntax

```
klist [-lh <logonID.highpart>] [-li <logonID.lowpart>] tickets | tgt | purge | sessions | kcd_cache | get | add_bind | query_bind | purge_bind
```

### Parameters

| Parameter | Description |
| --- | --- |
| -lh | Denotes the high part of the user's locally unique identifier (LUID), expressed in hexadecimal. If neither **-lh** nor **-li** are present, the command defaults to the LUID of the user who is currently signed in. |
| -li | Denotes the low part of the user's locally unique identifier (LUID), expressed in hexadecimal. If neither **-lh** nor **-li** are present, the command defaults to the LUID of the user who is currently signed in. |
| tickets | Lists the currently cached ticket-granting-tickets (TGTs), and service tickets of the specified logon session. This is the default option. |
| tgt | Displays the initial Kerberos TGT. |
| purge | Allows you to delete all the tickets of the specified logon session. |
| sessions | Displays a list of logon sessions on this computer. |
| kcd\_cache | Displays the Kerberos constrained delegation cache information. |
| get | Allows you to request a ticket to the target computer specified by the service principal name (SPN). |
| add\_bind | Allows you to specify a preferred domain controller for Kerberos authentication. |
| query\_bind | Displays a list of cached preferred domain controllers for each domain that Kerberos has contacted. |
| purge\_bind | Removes the cached preferred domain controllers for the domains specified. |
| kdcoptions | Displays the Key Distribution Center (KDC) options specified in RFC 4120. |
| /? | Displays Help for this command. |

#### Remarks

- If no parameters are provided, **klist** retrieves all the tickets for the currently logged on user.
- The parameters display the following information:

    - **tickets** - Lists the currently cached tickets of services that you have authenticated to since logon. Displays the following attributes of all cached tickets:

        - **LogonID:** The LUID.
        - **Client:** The concatenation of the client name and the domain name of the client.
        - **Server:** The concatenation of the service name and the domain name of the service.
        - **KerbTicket Encryption Type:** The encryption type that is used to encrypt the Kerberos ticket.
        - **Ticket Flags:** The Kerberos ticket flags.
        - **Start Time:** The time from which the ticket is valid.
        - **End Time:** The time the ticket becomes no longer valid. When a ticket is past this time, it can no longer be used to authenticate to a service or be used for renewal.
        - **Renew Time:** The time that a new initial authentication is required.
        - **Session Key Type:** The encryption algorithm that is used for the session key.
    - **tgt** - Lists the initial Kerberos TGT and the following attributes of the currently cached ticket:

        - **LogonID:** Identified in hexadecimal.
        - **ServiceName:** krbtgt
        - **TargetName `<SPN>`:** krbtgt
        - **DomainName:** Name of the domain that issues the TGT.
        - **TargetDomainName:** Domain that the TGT is issued to.
        - **AltTargetDomainName:** Domain that the TGT is issued to.
        - **Ticket Flags:** Address and target actions and type.
        - **Session Key:** Key length and encryption algorithm.
        - **StartTime:** Local computer time that the ticket was requested.
        - **EndTime:** Time the ticket becomes no longer valid. When a ticket is past this time, it can no longer be used to authenticate to a service.
        - **RenewUntil:** Deadline for ticket renewal.
        - **TimeSkew:** Time difference with the Key Distribution Center (KDC).
        - **EncodedTicket:** Encoded ticket.
    - **purge** - Allows you to delete a specific ticket. Purging tickets destroys all tickets that you have cached, so use this attribute with caution. It might stop you from being able to authenticate to resources. If this happens, you'll have to log off and log on again.

        - **LogonID:** Identified in hexadecimal.
    - **sessions** - Allows you to list and display the information for all logon sessions on this computer.

        - **LogonID:** If specified, displays the logon session only by the given value. If not specified, displays all the logon sessions on this computer.
    - **kcd\_cache** - Allows you to display the Kerberos constrained delegation cache information.

        - **LogonID:** If specified, displays the cache information for the logon session by the given value. If not specified, displays the cache information for the current user's logon session.
    - **get** - Allows you to request a ticket to the target that is specified by the SPN.

        - **LogonID:** If specified, requests a ticket by using the logon session by the given value. If not specified, requests a ticket by using the current user's logon session.
        - **kdcoptions:** Requests a ticket with the given KDC options
    - **add\_bind** - Allows you to specify a preferred domain controller for Kerberos authentication.
    - **query\_bind** - Allows you to display cached, preferred domain controllers for the domains.
    - **purge\_bind** - Allows you to remove cached, preferred domain controllers for the domains.
    - **kdcoptions** - For the current list of options and their explanations, see [RFC 4120](https://datatracker.ietf.org/doc/rfc4120/).

### Examples

To query the Kerberos ticket cache to determine if any tickets are missing, if the target server or account is in error, or if the encryption type is not supported due to an Event ID 27 error, type:

```
klist
```

```
klist -li 0x3e7
```

To learn about the specifics of each ticket-granting-ticket that is cached on the computer for a logon session, type:

```
klist tgt
```

To purge the Kerberos ticket cache, log off, and then log back on, type:

```
klist purge
```

```
klist purge -li 0x3e7
```

To diagnose a logon session and to locate a logonID for a user or a service, type:

```
klist sessions
```

To diagnose Kerberos constrained delegation failure, and to find the last error that was encountered, type:

```
klist kcd_cache
```

To diagnose if a user or a service can get a ticket to a server, or to request a ticket for a specific SPN, type:

```
klist get host/%computername%
```

To diagnose replication issues across domain controllers, you typically need the client computer to target a specific domain controller. To target the client computer to the specific domain controller, type:

```
klist add_bind CONTOSO KDC.CONTOSO.COM
```

```
klist add_bind CONTOSO.COM KDC.CONTOSO.COM
```

To query which domain controllers were recently contacted by this computer, type:

```
klist query_bind
```

To rediscover domain controllers, or to flush the cache before creating new domain controller bindings with `klist add_bind`, type:

```
klist purge_bind
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)