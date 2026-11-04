---
layout: Conceptual
title: nslookup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup command, which displays information that you can use to diagnose Domain Name System (DNS) infrastructure.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-09-08T00:00:00.0000000Z
locale: en-us
document_id: 9eba5593-e098-79ad-d314-fde8f49b1aac
document_version_independent_id: 8b7dbf11-907c-85f3-07c2-681de5830324
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6da0293f-0c10-1450-e4d3-b3208543f1f1
---

# nslookup | Microsoft Learn

Displays information that you can use to diagnose Domain Name System (DNS) infrastructure. Before using this tool, you should be familiar with how DNS works. The nslookup command-line tool is available only if you have installed the TCP/IP protocol.

## Syntax

```
nslookup [exit | finger | help | ls | lserver | root | server | set | view] [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [nslookup exit](nslookup-exit-command) | Exits the nslookup command-line tool. |
| [nslookup finger](nslookup-finger-command) | Connects with the finger server on the current computer. |
| [nslookup help](nslookup-help) | Displays a short summary of subcommands. |
| [nslookup ls](nslookup-ls) | Lists information for a DNS domain. |
| [nslookup lserver](nslookup-lserver) | Changes the default server to the specified DNS domain. |
| [nslookup root](nslookup-root) | Changes the default server to the server for the root of the DNS domain name space. |
| [nslookup server](nslookup-server) | Changes the default server to the specified DNS domain. |
| [nslookup set](nslookup-set) | Changes configuration settings that affect how lookups function. |
| [nslookup set all](nslookup-set-all) | Prints the current values of the configuration settings. |
| [nslookup set class](nslookup-set-class) | Changes the query class. The class specifies the protocol group of the information. |
| [nslookup set d2](nslookup-set-d2) | Turns exhaustive Debugging mode on or off. All fields of every packet are printed. |
| [nslookup set debug](nslookup-set-debug) | Turns Debugging mode on or off. |
| [nslookup set domain](nslookup-set-domain) | Changes the default DNS domain name to the name specified. |
| [nslookup set port](nslookup-set-port) | Changes the default TCP/UDP DNS name server port to the value specified. |
| [nslookup set querytype](nslookup-set-querytype) | Changes the resource record type for the query. |
| [nslookup set recurse](nslookup-set-recurse) | Tells the DNS name server to query other servers if it doesn't have the information. |
| [nslookup set retry](nslookup-set-retry) | Sets the number of retries. |
| [nslookup set root](nslookup-set-root) | Changes the name of the root server used for queries. |
| [nslookup set search](nslookup-set-search) | Appends the DNS domain names in the DNS domain search list to the request until an answer is received. This applies when the set and the lookup request contain at least one period, but do not end with a trailing period. |
| [nslookup set srchlist](nslookup-set-srchlist) | Changes the default DNS domain name and search list. |
| [nslookup set timeout](nslookup-set-timeout) | Changes the initial number of seconds to wait for a reply to a request. |
| [nslookup set type](nslookup-set-type) | Changes the resource record type for the query. |
| [nslookup set vc](nslookup-set-vc) | Specifies to use or not use a virtual circuit when sending requests to the server. |
| [nslookup view](nslookup-view) | Sorts and lists the output of the previous **ls** subcommand or commands. |

### Remarks

- The nslookup command-line tool has two modes: interactive and noninteractive.

    - If you need to look up only a single piece of data, or you're using nslookup in scripts, command lines, or PowerShell, use the noninteractive mode. In noninteractive mode, also called command mode, the first command line parameter is the name or IP address of the computer that you want to look up. The second parameter is the name or IP address of a DNS name server. If you omit the second argument, nslookup uses the default DNS name server.
    - If you need to look up more than one piece of data or set several configurations, you can use interactive mode. To enter interactive mode, type a hyphen (-) instead of the first parameter in the nslookup command line. Enter the name or IP address of a DNS name server for the second parameter. If you omit the second argument, nslookup uses the default DNS name server. You can also invoke interactive mode by simply entering `nslookup` at the command prompt, and then entering names or IP addresses to search for in the interactive command line.
- Once you enter `nslookup -` or `nslookup` alone, the command prompt changes to the interactive prompt `>`. While in interactive mode, you can:

    - Enter names or IP addresses, `set` variables, and other options on separate lines.
    - Interrupt interactive commands at any time by pressing CTRL+B.
    - Exit, by entering `exit`.
    - Treat a built-in command as a computer name by preceding it with the escape character (`\`). An unrecognized command is interpreted as a computer name.
- If the computer to find is an IP address and the query is for an **A** or **PTR** resource record type, the name of the computer is returned.
- If the computer to find is a name and doesn't have a trailing period, the default DNS domain name is appended to the name. This behavior depends on the state of the following **set** subcommands: **domain**, **srchlist**, **defname**, and **search**.
- If the lookup request fails, the command-line tool provides one of the following error messages:

    | Error message | Description |
    | --- | --- |
    | timed out | The server didn't respond to a request after a certain amount of time and a certain number of retries. You can set the time-out period with the [nslookup set timeout](nslookup-set-timeout) command. You can set the number of retries with the [nslookup set retry](nslookup-set-retry) command. |
    | No response from server | No DNS name server is running on the server computer. |
    | No records | The DNS name server doesn't have resource records of the current query type for the computer, although the computer name is valid. The query type is specified with the [nslookup set querytype](nslookup-set-querytype) command. |
    | Nonexistent domain | The computer or DNS domain name doesn't exist. |
    | Connection refused or Network is unreachable | The connection to the DNS name server or finger server couldn't be made. This error commonly occurs with the **ls** and **finger** requests. |
    | Server failure | The DNS name server found an internal inconsistency in its database and couldn't return a valid answer. |
    | Refused | The DNS name server refused to service the request. |
    | format error | The DNS name server found that the request packet wasn't in the proper format. It may indicate an error in **nslookup**. |

## Examples

In nslookup noninteractive mode, you specify parameters and options in the Windows command line or script. In interactive mode, you specify arguments and options on separate lines at the interactive command prompt.

### Noninteractive mode

In nslookup noninteractive mode, the first parameter is the computer to find, and the second parameter is the DNS name server to use. If you don't specify a second parameter, nslookup uses the default DNS name server. The following examples use `nslookup` in noninteractive mode.

- The following example looks up the IP addresses for the domain name `mydomain.com` on the DNS name server at `1.1.1.1`:

    ```cmd
    nslookup mydomain.com 1.1.1.1
    ```
- The following example looks up the domain name for the IP address `4.4.4.4` on the default DNS name server:

    ```cmd
    nslookup 4.4.4.4
    ```
- To specify options, you can use `nslookup -<option>`. For example, the following command turns on the nslookup `debug` option to get more information about packets sent.

    ```cmd
    nslookup -debug mydomain.com
    ```
- To return certain types of records or information, use the `-type=<resourcerecordtype>` option. For example, the following command returns only IPv6 record types:

    ```cmd
    nslookup -type=AAAA mydomain.com
    ```
- You can combine options and resource record type queries in command lines. The following example enables debug output, retrieves both IPv6 and IPv4 addresses, doesn't attempt to use the search domain, uses recursive lookup, and uses the 1.1.1.1 DNS lookup server:

    ```cmd
    nslookup -debug -type=A+AAAA -nosearch -recurse mydomain.com 1.1.1.1
    ```

### Interactive mode

To use interactive mode, enter `-` instead of the first parameter of a nslookup command line, or simply enter `nslookup`. The command prompt then changes to the interactive prompt `>`. The following examples show interactive mode commands.

- The following command places nslookup in interactive mode and sets `1.1.1.1` as the default DNS lookup server:

    ```cmd
    nslookup - 1.1.1.1
    ```
- The following command at the interactive prompt returns nslookup option and parameter settings for the current server:

    ```cmd
    set all
    ```
- The following command at the interactive prompt returns the IP addresses for `mydomain.com`:

    ```cmd
    mydomain.com
    ```
- The following command at the interactive prompt changes the default DNS name server to `4.4.4.4`:

    ```cmd
    server 4.4.4.4
    ```
- The following command at the interactive prompt sets the query resource record type to `HINFO`:

    ```cmd
    set type=HINFO
    ```
- The following command at the interactive prompt exits interactive mode and returns to the Windows command prompt:

    ```cmd
    exit
    ```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)