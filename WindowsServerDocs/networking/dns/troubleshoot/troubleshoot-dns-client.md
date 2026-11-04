---
layout: Conceptual
title: Troubleshooting DNS clients | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/dns/troubleshoot/troubleshoot-dns-client
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This article introduces how to troubleshoot DNS issue from client-side.
ms.topic: troubleshooting-general
ms.author: roharwoo
ms.date: 2019-08-08T00:00:00.0000000Z
author: robinharwood
locale: en-us
document_id: 527b5e1a-b014-c9a1-d223-78f40f5164ed
document_version_independent_id: 931bfc40-fd69-d58e-9e13-552a6f64e58b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/dns/troubleshoot/troubleshoot-dns-client.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/dns/troubleshoot/troubleshoot-dns-client
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/dns/troubleshoot/troubleshoot-dns-client.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8975dbfd-4367-2b5f-fe71-221ac693b498
---

# Troubleshooting DNS clients | Microsoft Learn

This article discusses how to troubleshoot issues from DNS clients.

## Check IP configuration

1. Open a Command Prompt window as an administrator on the client computer.
2. Run the following command:

    ```cmd
    ipconfig /all
    ```
3. Verify that the client has a valid IP address, subnet mask, and default gateway for the network to which it is attached and being used.
4. Check the DNS servers that are listed in the output, and verify that the IP addresses listed are correct.
5. Check the connection-specific DNS suffix in the output and verify that it is correct.

If the client does not have a valid TCP/IP configuration, use one of the following methods:

- For dynamically configured clients, use the `ipconfig /renew` command to manually force the client to renew its IP address configuration with the DHCP server.
- For statically configured clients, modify the client TCP/IP properties to use valid configuration settings or complete its DNS configuration for the network.

## Check network connection

### Ping test

Verify that the client can contact a preferred (or alternate) DNS server by pinging the preferred DNS server by its IP address.

For example, if the client uses a preferred DNS server of 10.0.0.1, run this command at a command prompt:

```cmd
ping 10.0.0.1
```

If no configured DNS server responds to a direct pinging of its IP address, this indicates that the source of the problem is more likely network connectivity between the client and the DNS servers. If this is the case, follow basic TCP/IP network troubleshooting steps to fix the problem. Keep in mind that ICMP traffic must be allowed through the firewall in order for the ping command to work.

### DNS query tests

If the DNS client can ping the DNS server computer, try to use the following `nslookup` commands to test whether the server can respond to DNS clients. Because nslookup doesn't use the client's DNS cache, name resolution will use the client's configured DNS server.

#### Test a client

```cmd
nslookup <client>
```

For example, if the client computer is named **client1**, run this command:

```cmd
nslookup client1
```

If a successful response is not returned, try to run the following command:

```cmd
nslookup <fqdn of client>
```

For example, if the FQDN is **client1.corp.contoso.com**, run this command:

```cmd
nslookup client1.corp.contoso.com.
```

Note

You must include the trailing period when you run this test.

If Windows successfully finds the FQDN but cannot find the short name, check the DNS Suffix configuration on the DNS tab of the Advanced TCP/IP Settings of the NIC. For more information, see [Configuring DNS Resolution](/en-us/previous-versions/tn-archive/dd163570%28v=technet.10%29#configuring-dns-resolution).

#### Test the DNS server

```cmd
nslookup <DNS Server>
```

For example, if the DNS server is named DC1, run this command:

```cmd
nslookup dc1
```

If the previous tests were successful, this test should also be successful. If this test is not successful, verify the connectivity to the DNS server.

#### Test the failing record

```cmd
nslookup <failed internal record>
```

For example, if the failing record was **app1.corp.contoso.com**, run this command:

```cmd
nslookup app1.corp.contoso.com
```

#### Test a public Internet address

```cmd
nslookup <external name>
```

For example:

```cmd
nslookup bing.com
```

If all four of these tests were successful, run `ipconfig /displaydns` and check the output for the name that failed. If you see "Name does not exist" under the failing name, a negative response was returned from a DNS server and was cached on the client.

To resolve the issue, clear the cache by running `ipconfig /flushdns`.