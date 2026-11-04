---
layout: Conceptual
title: bitsadmin util and setieproxy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-util-and-setieproxy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin util and setieproxy command, which sets the proxy settings to use when transferring files using a service account.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 00d264db-e570-0653-a7b6-3db7af7ad92c
document_version_independent_id: 3261d7d7-d13b-1ad2-c569-55d2de85fb23
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-setieproxy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-util-and-setieproxy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-setieproxy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: c4b83f2a-a428-6a0b-6af5-7be86d3b1f6a
---

# bitsadmin util and setieproxy | Microsoft Learn

Set the proxy settings to use when transferring files using a service account. You must run this command from an elevated command prompt for it to complete successfully.

Note

This command isn't supported by BITS 1.5 and earlier.

## Syntax

```
bitsadmin /util /setieproxy <account> <usage> [/conn <connectionname>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| account | Specifies the service account whose proxy settings you want to define. Possible values include:<br>- LOCALSYSTEM<br>- NETWORKSERVICE<br>- LOCALSERVICE. |
| usage | Specifies the form of proxy detection to use. Possible values include:<br>- **NO\_PROXY.** Don't use a proxy server.<br>- **AUTODETECT.** Automatically detect the proxy settings.<br>- **MANUAL\_PROXY.** Use a specified proxy list and bypass list. You must specify your lists immediately after the usage tag. For example, `MANUAL_PROXY proxy1,proxy2 NULL`.<br>    - **Proxy list.** A comma-delimited list of proxy servers to use.<br>    - **Bypass list.** A space-delimited list of host names or IP addresses, or both, for which transfers are not to be routed through a proxy. This can be &lt;local&gt; to refer to all servers on the same LAN. Values of NULL or may be used for an empty proxy bypass list.<br>- **AUTOSCRIPT.** Same as **AUTODETECT**, except it also runs a script. You must specify the script URL immediately after the usage tag. For example, `AUTOSCRIPT http://server/proxy.js`. |
| connectionname | Optional. Used with the **/conn** parameter to specify which modem connection to use. If you don't specify the **/conn** parameter, BITS uses the LAN connection. |

### Remarks

Each successive call using this switch replaces the previously specified usage, but not the parameters of the previously defined usage. For example, if you specify **NO\_PROXY**, **AUTODETECT**, and **MANUAL\_PROXY** on separate calls, BITS uses the last supplied usage, but keeps the parameters from the previously defined usage.

## Examples

To set the proxy usage for the LOCALSYSTEM account:

```
bitsadmin /util /setieproxy localsystem AUTODETECT
```

```
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1,proxy2,proxy3 NULL
```

```
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1:80
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin util command](bitsadmin-util)
- [bitsadmin command](bitsadmin)