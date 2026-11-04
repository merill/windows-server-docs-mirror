---
layout: Conceptual
title: Using ETW to troubleshoot LDAP connections | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/troubleshoot/troubleshoot-ldap-using-etw
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: How to turn on and use ETW to trace LDAP connections between AD DS domain controllers.
author: robinharwood
audience: Admin
ms.author: roharwoo
ms.topic: troubleshooting-general
ms.date: 2019-11-22T00:00:00.0000000Z
locale: en-us
document_id: 247423d5-a2ec-f3b3-33ca-ca4b370b6c2a
document_version_independent_id: bbb20ad2-0df1-8d72-2834-81d0b1c6ed93
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/troubleshoot/troubleshoot-ldap-using-etw.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/troubleshoot/troubleshoot-ldap-using-etw
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/troubleshoot/troubleshoot-ldap-using-etw.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 93dec363-c2f7-2cdf-b0c6-3b778e41232c
---

# Using ETW to troubleshoot LDAP connections | Microsoft Learn

[Event Tracing for Windows (ETW)](/en-us/windows/win32/etw/event-tracing-portal) can be a valuable troubleshooting tool for Active Directory Domain Services (AD DS). You can use ETW to trace the Lightweight Directory Access Protocol ([LDAP](/en-us/previous-versions/windows/desktop/ldap/lightweight-directory-access-protocol-ldap-api)) communications between Windows clients and LDAP servers, including AD DS domain controllers.

## How to turn on ETW and start a trace

**To turn on ETW**

1. Open Registry Editor, and create the following registry subkey:

    **HKEY\_LOCAL\_MACHINE\System\CurrentControlSet\Services\ldap\Tracing\*ProcessName***

    In this subkey, *ProcessName* is the full name of the process that you want to trace, including its extension (for example, "Svchost.exe").
2. (**Optional**) Under this subkey, create a new entry that is named **PID**. To use this entry, assign a process ID as a DWORD value.

    If you specify a process ID, ETW traces only the instance of the application that has this process ID.

**To start a tracing session**

- Open a Command Prompt window, and run the following command:

    ```cmd
    tracelog.exe -start <SessionName> -guid \#099614a5-5dd7-4788-8bc9-e29f43db28fc -f <FileName> -flag <TraceFlags>
    ```

    The placeholders in this command represent the following values.

    - &lt;*SessionName*&gt; is an arbitrary identifier that is used to label the tracing session.

    Note

    You will have to refer to this session name later when you stop the tracing session.

    - &lt;*FileName*&gt; specifies the log file to which events will be written.
    - &lt;*TraceFlags*&gt; should be one or more of the values that are listed in the trace flags table.

## How to end a tracing session and turn off Event Tracing

**To stop tracing**

- At the command prompt, run the following command:

    ```cmd
    tracelog.exe -stop <SessionName>
    ```

    In this command, &lt;*SessionName*&gt; is the same name that you used in the **tracelog.exe -start** command.

**To turn off ETW**

- In Registry Editor, delete the **HKEY\_LOCAL\_MACHINE\System\CurrentControlSet\Services\ldap\Tracing\*ProcessName*** subkey.

## Values for trace flags

To use a flag, substitute the flag value for the &lt;*TraceFlags*&gt; placeholder in the arguments of the **tracelog.exe -start** command.

Note

You can specify multiple flags by using the sum of the appropriate flag values. For example, to specify the **DEBUG\_SEARCH** (0x00000001) and **DEBUG\_CACHE** (0x00000010) flags, the appropriate &lt;*TraceFlags*&gt; value is **0x00000011**.

| Flag name | Flag value | Flag description |
| --- | --- | --- |
| **DEBUG\_SEARCH** | 0x00000001 | Logs search requests and the parameters that are passed to those requests. Responses are not logged here. Only the search requests are logged. (Use **DEBUG\_SPEWSEARCH** to log the responses to search requests.) |
| **DEBUG\_WRITE** | 0x00000002 | Logs write requests and the parameters that are passed to those requests. Write requests include the add, delete, modify, and extended operations. |
| **DEBUG\_REFCNT** | 0x00000004 | Logs reference counting data and operations for connections and requests. |
| **DEBUG\_HEAP** | 0x00000008 | Logs all memory allocations and memory releases. |
| **DEBUG\_CACHE** | 0x00000010 | Logs cache activity. This activity includes adds, removes, hits, misses, and so on. |
| **DEBUG\_SSL** | 0x00000020 | Logs SSL information and errors. |
| **DEBUG\_SPEWSEARCH** | 0x00000040 | Logs all server responses to search requests. These responses include the attributes that were requested, plus all data that was received. |
| **DEBUG\_SERVERDOWN** | 0x00000080 | Logs server-down and connection errors. |
| **DEBUG\_CONNECT** | 0x00000100 | Logs data that is related to establishing a connection.Use **DEBUG\_CONNECTION** to log other data that is related to connections. |
| **DEBUG\_RECONNECT** | 0x00000200 | Logs automatic reconnect activity. This activity includes reconnect attempts, failures, and related errors. |
| **DEBUG\_RECEIVEDATA** | 0x00000400 | Logs activity that is related to receiving messages from the server. This activity includes events such as "waiting on the response from the server" and the response that is received from the server. |
| **DEBUG\_BYTES\_SENT** | 0x00000800 | Logs all data sent by the LDAP client to the server. This function is essentially packet logging, but it always logs unencrypted data. (If a packet is sent over SSL, this function logs the unencrypted packet.) This logging can be verbose. This flag is probably best used on its own or combined with **DEBUG\_BYTES\_RECEIVED**. |
| **DEBUG\_EOM** | 0x00001000 | Logs events that are related to reaching the end of a message list. These events include information such as "message list cleared" and so on. |
| **DEBUG\_BER** | 0x00002000 | Logs operations and errors that are related to Basic Encoding Rules (BER). These operations and errors include problems in encoding, buffer size problems, and so on. |
| **DEBUG\_OUTMEMORY** | 0x00004000 | Logs failures to allocate memory. Also logs any failure to compute the required memory (for example, an overflow that occurs when computing the required buffer size). |
| **DEBUG\_CONTROLS** | 0x00008000 | Logs data that relates to controls. This data includes controls that are inserted, problems that affect controls, mandatory controls on a connection, and so on. |
| **DEBUG\_BYTES\_RECEIVED** | 0x00010000 | Logs all data that is received by the LDAP client. This behavior is essentially packet logging, but it always logs unencrypted data. (If a packet is sent over SSL, this option logs the unencrypted packet.) This type of logging can be verbose. This flag is probably best used on its own or combined with **DEBUG\_BYTES\_SENT**. |
| **DEBUG\_CLDAP** | 0x00020000 | Logs events that are specific to UDP and connectionless LDAP. |
| **DEBUG\_FILTER** | 0x00040000 | Logs events and errors that are encountered when you construct a search filter.**Note** This option logs client events only during filter construction. It does not log any responses from the server about a filter. |
| **DEBUG\_BIND** | 0x00080000 | Logs bind events and errors. This data includes negotiation information, bind success, bind failure, and so on. |
| **DEBUG\_NETWORK\_ERRORS** | 0x00100000 | Logs general network errors. This data includes send and receive errors.**Note** If a connection is lost or the server cannot be reached, **DEBUG\_SERVERDOWN** is the preferred tag. |
| **DEBUG\_VERBOSE** | 0x00200000 | Logs general messages. Use this option for any messages that tend to generate a large amount of output. For example, it logs messages such as "end of message reached," "server has not responded yet," and so on. This option is also useful for generic messages. |
| **DEBUG\_PARSE** | 0x00400000 | Logs general message events and errors plus packet parsing and encoding events and errors. |
| **DEBUG\_REFERRALS** | 0x00800000 | Logs data about referrals and chasing referrals. |
| **DEBUG\_REQUEST** | 0x01000000 | Logs tracking of requests. |
| **DEBUG\_CONNECTION** | 0x02000000 | Logs general connection data and errors. |
| **DEBUG\_INIT\_TERM** | 0x04000000 | Logs module initialization and cleanup (DLL Main, and so on). |
| **DEBUG\_API\_ERRORS** | 0x08000000 | Supports logging incorrect use of the API. For example, this option logs data if the bind operation is called two times on the same connection. |
| **DEBUG\_ERRORS** | 0x10000000 | Logs general errors. Most of these errors can be categorized as module initialization errors, SSL errors, or overflow or underflow errors. |
| **DEBUG\_PERFORMANCE** | 0x20000000 | Logs data about process-global LDAP activity statistics after receiving a server response for an LDAP request. |

## Example

Consider an application, App1.exe, that sets passwords for user accounts. Suppose that App1.exe produces an unexpected error. To use ETW to help diagnose this problem, you follow these steps:

1. In Registry Editor, create the following registry entry:

    **HKEY\_LOCAL\_MACHINE\System\CurrentControlSet\Services\ldap\Tracing\App1.exe**
2. To start a tracing session, open a Command Prompt window, and run the following command:

    ```cmd
    tracelog.exe -start ldaptrace -guid \#099614a5-5dd7-4788-8bc9-e29f43db28fc -f .\ldap.etl -flag 0x80000
    ```

    After this command starts, **DEBUG\_BIND** makes sure that ETW writes tracing messages to .\ldap.etl.
3. Start App1.exe, and reproduce the unexpected error.
4. To stop the tracing session, run the following command at the command prompt:

    ```cmd
     tracelog.exe -stop ldaptrace
    ```
5. To prevent other users from tracing the application, delete the **HKEY\_LOCAL\_MACHINE**\**System**\**CurrentControlSet**\**Services**\**ldap**\**Tracing**\**App1.exe** registry entry.
6. To review the information in the trace log, run the following command at the command prompt:

    ```cmd
     tracerpt.exe .\ldap.etl -o -report
    ```

    Note

    In this command, **tracerpt.exe** is a [trace consumer](/en-us/windows-hardware/drivers/devtest/trace-consumer) tool.