---
layout: Conceptual
title: netsh rpc | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-rpc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh rpc command configures and manages Remote Procedure Call (RPC) service settings in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-20T00:00:00.0000000Z
locale: en-us
document_id: 831b2027-85f9-c99b-263f-cc55caddb14f
document_version_independent_id: 831b2027-85f9-c99b-263f-cc55caddb14f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-rpc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-rpc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-rpc.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e35426a9-e165-ef73-514d-0e3363843cea
---

# netsh rpc | Microsoft Learn

The `netsh rpc` command enables administrators to configure, manage, and troubleshoot Remote Procedure Call (RPC) service settings, including selective binding, firewall filtering, and access control for RPC traffic.

## Syntax

```
netsh rpc [add | delete | dump | filter | help | reset | show | ?]
```

```
netsh rpc add <subnet>
```

```
netsh rpc delete <subnet>
```

```
netsh rpc dump
```

```
netsh rpc filter add condition [field=]<string> [matchtype=]<string> [data=]<string>
netsh rpc filter add filter
netsh rpc filter add rule [layer=]<string> [actiontype=]<string> [[filterkey=]<string>]
                          [persistence=]volatile [audit=]enable [auditparameters=]enable
```

```
netsh rpc reset
```

```
netsh rpc show
```

## Parameters

| Command | Description |
| --- | --- |
| rpc `add` | Adds one or more subnets (IP address) to an "add" list managed by the RPC service. |
| rpc `delete` | Adds one or more subnets (IP address) to a "delete" list, implying these subnets are to be removed from existing configurations. |
| rpc `dump` | Creates a script containing the current context configuration. The script can be saved to a file and used to restore settings if they're altered or need to be replicated on another system. |
| rpc `filter add condition` | Creates precise firewall rules to control RPC traffic based on specific conditions. `field=<string>` - Specifies the aspect of the RPC communication where the condition applies. For `um` (User Mode), acceptable values are: - `if_uuid` - Interface UUID<br>- `if_version` - Interface version<br>- `if_flag` - Interface flag<br>- `dcom_app_id` - DCOM Application ID<br>- `image_name` - The executable image involved in the RPC call<br>- `protocol` - Protocol used (like TCP)<br>- `auth_type` - Type of authentication used<br>- `auth_level` - Level of authentication enforced<br>- `sec_encrypt_alg` - Security encryption algorithm<br>- `sec_key_size` - Size of the security key<br>- `remote_user_token` - Token for remote user authentication<br>- `local_addr_v4` - Local IPv4 address<br>- `local_addr_v6` - Local IPv6 address<br>- `remote_addr_v4` - Remote IPv4 address<br>- `remote_addr_v6` - Remote IPv6 address<br>- `local_port` - Local communication port<br>- `pipe` - Named pipe used in the connection<br>- `opnum` - Operation number<br> For `epmap` (Endpoint Mapper), acceptable values are: - Similar values as user mode but without `opnum`.  For `ep_add` (Endpoint Address), acceptable values are:<br>- `process_with_if_uuid` - Process associated with the interface UUID<br>- `protocol`: Protocol used<br>- `ep_value` - Endpoint value<br>- `ep_flags` - Flags related to the endpoint.<br> For `proxy_conn` (Proxy Connection), acceptable values are: `server_name`: Name of the server involved - `server_port` - Port on the server<br>- `proxy_auth_type` - Type of proxy authentication<br>- `client_token` - Token for client authentication<br>- `client_cert_key_name` - Name of the client's certificate key<br>- `client_cert_oid` - OID of the client's certificate<br> For `proxy_if` (Proxy Interface), acceptable values are: - Similar to `proxy_conn`, with some overlapping fields. `matchtype=<string>` - Determines the type of comparison or match conducted on the field's value. Acceptable values are:<br>- `equal` - Exact match<br>- `greater` - Greater than a specified value<br>- `less` - Less than a specified value<br>- `greater_or_equal` - Greater than or equal to a specified value<br>- `less_or_equal` - Less than or equal to a specified value<br>- `range` - Within a specified range<br>- `all_set` - Bitwise matching commonly used for flags or settings that use bit fields<br>- `any_set` - Bitwise matching commonly used for flags or settings that use bit fields<br>- `none_set` - Bitwise matching commonly used for flags or settings that use bit fields<br>`data=<string>` - The actual value used in the condition that corresponds to the specified field. |
| rpc `filter add filter` | Adds an RPC firewall filter. Before you can add a filter, you must first define at least one rule and one or more conditions. |
| rpc `filter add rule` | Adds an RPC firewall filter rule. `layer=<string>` - Specifies the layer where the filter is applied. Acceptable values are: - `um` - User Mode<br>- `epmap` - Endpoint Mapper<br>- `ep_add` - Endpoint Address<br>- `proxy_conn` - Proxy Connection<br>- `proxy_if` - Proxy Interface<br>`actiontype=<string>` - Defines the action to take when the filter matches. Acceptable values are: - `block` - Blocks the RPC traffic<br>- `permit` - Allows the RPC traffic.<br>- `continue` - Continues to the next filter for evaluation.<br>`filterkey=<string>` - Specifies a unique UUID that identifies the RPC firewall filter. Useful for managing or referencing specific filters. `persistence` - Determines whether the filter remains after a reboot. By default, filters are persistent. `audit` - Enables auditing for this filter. Only filters with the "permit" action type can have auditing enabled. Auditing isn't supported at the `ep_add` layer. `auditparameters` - Enables auditing of RPC call parameter buffers for this filter. Requires `audit` to be enabled. Auditing of parameters is only supported at the `um` layer. |
| rpc `reset` | Resets the selective binding configuration so that the system listens on all network interfaces (no subnets are restricted). |
| rpc `show` | Displays the current selective binding configuration, listing each subnet and its binding state on the system. |
| `help`*or*`?` | Displays a list of commands and their descriptions in the current context. |

## Examples

To add the specified subnet `192.168.1.0` to the RPC "add list", run the following command:

```cmd
netsh rpc add 192.168.1.0
```

To add a filter condition that applies to RPC traffic where the local IPv4 address is exactly `192.168.1.10`, run the following command:

```cmd
netsh rpc filter add condition field=local_addr_v4 matchtype=equal data=192.168.1.10
```

To apply a rule to the Endpoint Mapper layer permitting traffic for a specific UUID, along with persistence after a reboot and logged for auditing, run the following command:

```cmd
netsh rpc filter add rule layer=epmap actiontype=permit filterkey={Your-UUID} persistence=yes audit=yes
```