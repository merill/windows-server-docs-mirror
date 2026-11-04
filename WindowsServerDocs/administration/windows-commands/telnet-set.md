---
layout: Conceptual
title: telnet set | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/telnet-set
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the telnet set command, which sets options.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9360c931-b818-1733-2546-e5f2f9bf9eda
document_version_independent_id: f9d1fc89-021d-2da6-e8a5-28783a8036b1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/telnet-set.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/telnet-set
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/telnet-set.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 42b93f4d-f796-9b46-d72a-0d528530ff7f
---

# telnet set | Microsoft Learn

Sets options. You can use the [telnet unset command](telnet-unset) to turn off an option that was previously set.

## Syntax

```
set [bsasdel] [crlf] [delasbs] [escape <char>] [localecho] [logfile <filename>] [logging] [mode {console | stream}] [ntlm] [term {ansi | vt100 | vt52 | vtnt}] [?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| bsasdel | Sends **backspace** as a **delete**. |
| crlf | Sends CR & LF (0x0D, 0x 0A) when the **Enter** key is pressed. Known as **New line mode**. |
| delasbs | Sends **delete** as a **backspace**. |
| escape `<character>` | Sets the escape character used to enter the telnet client prompt. The escape character can be a single character, or it can be a combination of the **CTRL** key plus a character. To set a control-key combination, hold down the **CTRL** key while you type the character that you want to assign. |
| localecho | Turns on local echo. |
| logfile `<filename>` | Logs the current telnet session to the local file. Logging begins automatically when you set this option. |
| logging | Turns on logging. If no log file is set, an error message appears. |
| mode `{console | stream}` | Sets the operation mode. |
| ntlm | Turns on NTLM authentication. |
| term `{ansi | vt100 | vt52 | vtnt}` | Sets the terminal type. |
| ? | Displays help for this command. |

#### Remarks

- On non-English versions of telnet, the **codeset**`<option>` is available. **Codeset**`<option>` sets the current code set to an option, which can be any one of the following: **shift JIS**, **Japanese EUC**, **JIS Kanji**, **JIS Kanji (78)**, **DEC Kanji**, **NEC Kanji**. You should set the same code set on the remote computer.

## Example

To set the log file and to begin logging to the local file *tnlog.txt*, type:

```
set logfile tnlog.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)