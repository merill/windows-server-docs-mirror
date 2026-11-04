---
layout: Conceptual
title: change port | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/change-port
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the change port command, which lists or changes the COM port mappings to be compatible with MS-DOS applications.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f73f2c4e-37ba-e2c8-0862-f96f8a3ecdc9
document_version_independent_id: a52f26d6-4055-6a28-26a5-32371df4572b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/change-port.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/change-port
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/change-port.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 27f425b3-3a50-63b2-5ad5-55f908e49f73
---

# change port | Microsoft Learn

Lists or changes the COM port mappings to be compatible with MS-DOS applications.

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
change port [<portX>=<portY>| /d <portX> | /query]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<portX>`=`<portY>` | Maps COM `<portX>` to `<portY>` |
| /d `<portX>` | Deletes the mapping for COM `<portX>` |
| /query | Displays the current port mappings. |
| /? | Displays help at the command prompt. |

#### Remarks

- Most MS-DOS applications support only COM1 through COM4 serial ports. The **change port** command maps a serial port to a different port number, allowing apps that don't support high-numbered COM ports to access the serial port. Remapping works only for the current session and is not retained if you log off from a session and then log on again.
- Use **change port** without any parameters to display the available COM ports and their current mappings.

## Examples

- To map COM12 to COM1 for use by an MS-DOS-based application, type:

    ```
    change port com12=com1
    ```
- To display the current port mappings, type:

    ```
    change port /query
    ```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [change command](change)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)