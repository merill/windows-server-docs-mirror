---
layout: Conceptual
title: bitsadmin setproxysettings | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setproxysettings
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setproxysettings command, which sets the proxy settings for the specified job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d535d65d-2839-f055-1da1-a805886ad949
document_version_independent_id: 830a16ce-3db2-c9ec-2e69-9ac9808564b6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setproxysettings.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setproxysettings
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setproxysettings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9582b215-e04b-35a7-69b7-67b24a47562a
---

# bitsadmin setproxysettings | Microsoft Learn

Sets the proxy settings for the specified job.

## Syntax

```
bitsadmin /setproxysettings <job> <usage> [list] [bypass]
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| usage | Sets the proxy usage, including:<br>- **PRECONFIG.** Use the owner's Internet Explorer defaults.<br>- **NO\_PROXY.** Don't use a proxy server.<br>- **OVERRIDE.** Use an explicit proxy list and bypass list. The proxy list and proxy bypass information must follow.<br>- **AUTODETECT.** Automatically detects proxy settings. |
| list | Used when the *Usage* parameter is set to OVERRIDE. Must contain a comma-delimited list of proxy servers to use. |
| bypass | Used when the *Usage* parameter is set to OVERRIDE. Must contain a space-delimited list of host names or IP addresses, or both, for which transfers are not to be routed through a proxy. This can be `<local>` to refer to all servers on the same LAN. Values of NULL may be used for an empty proxy bypass list. |

## Examples

To set the proxy settings using the various usage options for the job named *myDownloadJob*:

```
bitsadmin /setproxysettings myDownloadJob PRECONFIG
```

```
bitsadmin /setproxysettings myDownloadJob NO_PROXY
```

```
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1:80
```

```
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1,proxy2,proxy3 NULL
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)