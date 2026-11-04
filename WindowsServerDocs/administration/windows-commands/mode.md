---
layout: Conceptual
title: mode | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/mode
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the mode command, which displays system status, changes system settings, or reconfigures ports or devices.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c7f512a7-41c3-176f-2d32-401af16acbb5
document_version_independent_id: 2c754a97-4ce2-a43f-336e-ae4cfc1c0eae
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/mode.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/mode.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
platformId: 05ed0dbe-d602-f689-81b6-c7d5daeb1fc1
---

# mode | Microsoft Learn

Displays system status, changes system settings, or reconfigures ports or devices. If used without parameters, **mode** displays all the controllable attributes of the console and the available COM devices.

## Serial port

Configures a serial communications port and sets the output handshake.

### Syntax

```
mode com<m>[:] [baud=<b>] [parity=<p>] [data=<d>] [stop=<s>] [to={on|off}] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| `com<m>[:]` | Specifies the number of the async Prncnfg.vbshronous communications port. |
| `baud=<b>` | Specifies the transmission rate in bits per second. The valid values include:<br>- **11** - 110 baud<br>- **15** - 150 baud<br>- **30** - 300 baud<br>- **60** - 600 baud<br>- **12** - 1200 baud<br>- **24** - 2400 baud<br>- **48** - 4800 baud<br>- **96** - 9600 baud<br>- **19** - 19,200 baud |
| `parity=<p>` | Specifies how the system uses the parity bit to check for transmission errors. The valid values include:<br>- **n** - none<br>- **e** - even (default value)<br>- **o** - odd<br>- **m** - mark<br>- **s** - space<br><br>Not all devices support using the **m** or **s** parameters. |
| `data=<d>` | Specifies the number of data bits in a character. Valid values range from **5** through **8**. The default value is **7**. Not all devices support the values **5** and **6**. |
| `stop=<s>` | Specifies the number of stop bits that define the end of a character: **1**, **1.5**, or **2**. If the baud rate is **110**, the default value is **2**. Otherwise, the default value is **1**. Not all devices support the value **1.5**. |
| `to={on | off}` | Specifies whether the device uses infinite time out processing. The default value is **off**. Turning this option **on** means that the device will never stop waiting to receive a response from a host or client computer. |
| `xon={on | off}` | Specifies whether the system allows the XON/XOFF protocol. This protocol provides flow control for serial communications, enhancing reliability, but reducing performance. |
| `odsr={on | off}` | Specifies whether the system turns on the Data Set Ready (DSR) output handshake. |
| `octs={on | off}` | Specifies whether the system turns on the Clear to Send (CTS) output handshake. |
| `dtr={on | off | hs}` | Specifies whether the system turns on the Data Terminal Ready (DTR) output handshake. Setting this value to **on** mode, provides a constant signal to show the terminal is ready to send data. Setting this value to **hs** mode provides a handshake signal between the two terminals. |
| `rts={on | off | hs | tg}` | Specifies whether the system turns on the Request to Send (RTS) output handshake. Setting this value to **on** mode, provides a constant signal to show the terminal is ready to send data. Setting this value to **hs** mode provides a handshake signal between the two terminals. Setting this value to **tg** mode provides a way to toggle between ready and not ready states. |
| `idsr={on | off}` | Specifies whether the system turns on the DSR sensitivity. You must turn this option on to use DSR handshaking. |
| /? | Displays help at the command prompt. |

## Device status

Displays the status of a specified device. If used without parameters, **mode** displays the status of all devices installed on your system.

### Syntax

```
mode [<device>] [/status]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| `<device>` | Specifies the name of the device for which you want to display the status. Standard names include, LPT1: through LPT3:, COM1: through COM9:, and CON. |
| /status | Requests the status of any redirected parallel printers. You can also use **/sta** as an abbreviated version of this command. |
| /? | Displays help at the command prompt. |

## Redirect printing

Redirects printer output. You must be a member of the Administrators group to redirect printing.

Note

To set up your system so that it sends parallel printer output to a serial printer, you must use the **mode** command twice. The first time, you must use **mode** to configure the serial port. The second time, you must use **mode** to redirect parallel printer output to the serial port you specified in the first **mode** command.

### Syntax

```
mode LPT<n>[:]=COM<m>[:]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| LPT`<n>`[:] | Specifies the number of the LPT to configure. Typically, this means providing a value from **LTP1: through LTP3:**, unless your system includes special parallel port support. This parameter is required. |
| COM`<m>`[:] | Specifies the COM port to configure. Typically, this means providing a value from **COM1: through COM9:**, unless your system has special hardware for additional COM ports. This parameter is required. |
| /? | Displays help at the command prompt. |

#### Examples

To redirect a serial printer that operates at 4800 baud with even parity, and is connected to the COM1 port (the first serial connection on your computer), type:

```
mode com1 48,e,,,b
mode lpt1=com1
```

To redirect parallel printer output from LPT1 to COM1, and then to print a file using LPT1, type the following command before you print the file:

```
mode lpt1
```

This command prevents the redirection the file from LPT1 to COM1.

## Select code page

Configures or queries the code page info for a selected device.

### Syntax

```
mode <device> codepage select=<yyy>
mode <device> codepage [/status]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| `<device>` | Specifies the device for which you want to select a code page. CON is the only valid name for a device. This parameter is required. |
| codepage | Specifies which code page to use with the specified device. You can also use **cp** as an abbreviated version of this command. This parameter is required. |
| select=`<yyy>` | Specifies the number of the code page to use with the device. The supported code pages, by country/region or language, include:<br>- **437:** United States<br>- **850:** Multilingual (Latin I)<br>- **852:** Slavic (Latin II)<br>- **855:** Cyrillic (Russian)<br>- **857:** Turkish<br>- **860:** Portuguese<br>- **861:** Icelandic<br>- **863:** Canadian-French<br>- **865:** Nordic<br>- **866:** Russian<br>- **869:** Modern Greek<br><br> This parameter is required. |
| /status | Displays the numbers of the current code pages selected for the specified device. You can also use **/sta** as an abbreviated version of this command. Regardless whether you specify **/status**, the **mode codepage** command will display the numbers of the code pages that are selected for the specified device. |
| /? | Displays help at the command prompt. |

## Display mode

Changes the size of the command prompt screen buffer

### Syntax

```
mode con[:] [cols=<c>] [lines=<n>]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| con[:] | Indicates that the change applies to the Command Prompt window. This parameter is required. |
| cols=`<c>` | Specifies the number of columns in the command prompt screen buffer. The default setting is 80 columns, but you can set this to any value. If you don't use the default, typical values are 40 and 135 columns. Using non-standard values can result in the command prompt app problems. |
| lines=`<n>` | Specifies the number of lines in the command prompt screen buffer. The default value is 25, but you can set this to any value. If you don't use the default, the other typical value is 50 lines. |
| /? | Displays help at the command prompt. |

## Typematic rate

Sets the keyboard typematic rate. The typematic rate is the speed at which Windows can repeat a character when you press the key on a keyboard.

Note

Some keyboards don't recognize this command.

### Syntax

```
mode con[:] [rate=<r> delay=<d>]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| con[:] | Specifies the keyboard. This parameter is required. |
| rate=`<r>` | Specifies the rate at which a character is repeated on the screen when you hold down a key. The default value is 20 characters per second for IBM AT-compatible keyboards, and 21 for IBM PS/2-compatible keyboards, but you can use any value from 1 through 32. If you set this parameter, you must also set the **delay** parameter. |
| delay=`<d>` | Specifies the amount of time that will elapse after you press and hold down a key before the character output repeats. The default value is 2 (.50 seconds), but you can also use 1 (.25 seconds), 3 (.75 seconds), or 4 (1 second). If you set this parameter, you must also set the **rate** parameter. |
| /? | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)