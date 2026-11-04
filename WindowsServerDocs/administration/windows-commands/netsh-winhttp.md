---
layout: Conceptual
title: netsh winhttp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-winhttp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh winhttp command configures and manages WinHTTP settings for network communications for applications that use WinHTTP in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-19T00:00:00.0000000Z
locale: en-us
document_id: 6dfb53fd-b418-9bae-01cf-08021439b2c8
document_version_independent_id: 6dfb53fd-b418-9bae-01cf-08021439b2c8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-winhttp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-winhttp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-winhttp.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b95d69a9-25b9-ff85-f267-ace14da5fb83
---

# netsh winhttp | Microsoft Learn

The `netsh winhttp` command configures and manages the WinHTTP (Windows HTTP Services) settings. WinHTTP is a Microsoft API used by applications to make HTTP requests which allows administrators to manage network communications for applications that use WinHTTP.

## Syntax

```
netsh winhttp [dump | help | import | reset | set| show | ?]
```

```
netsh winhttp dump
```

```
netsh winhttp import proxy [source=]ie
```

```
netsh winhttp reset <autoproxy> <proxy> <tracing>
```

```
netsh winhttp set advproxy <settings-scope> <settings-file> <settings>
netsh winhttp set proxy [proxy-server=]<server name> [bypass-list=]<hosts list>
netsh winhttp set tracing
```

```
netsh winhttp show <advproxy> <proxy> <tracing>
```

## Parameters

| Command | Description |
| --- | --- |
| http `dump` | Creates a script containing the current context configuration. The script can be saved to a file and used to restore settings if they're altered or need to be replicated on another system. |
| winhttp `import proxy source=ie` | Import proxy settings into the WinHTTP configuration from the Internet Explorer (IE) settings. There isn't any direct built-in support for importing settings from other browsers using this command. |
| winhttp `reset``<autoproxy>` | `<proxy>` | `<tracing>` | Provides options to reset various components of the WinHTTP configuration, such as: - `autoproxy` - Resets the WinHTTP proxy autodiscovery service. This is used to clear any settings or cache related to the automatic detection of proxy servers.<br>- `proxy` - Resets the WinHTTP proxy setting to `DIRECT`, effectively removing any configured proxy server and allowing direct internet access without a proxy.<br>- `tracing` - For this operation, the system advises using the `netsh trace stop` command, which is intended to stop and reset any tracing activities. |
| winhttp `set advproxy` | Configures advanced proxy settings for WinHTTP, providing detailed configurations like bypass lists or multiple proxy settings. `setting-scope` - Specifies the scope of the settings. Acceptable values are: - `user` - Applies the settings to the current user.<br>- `machine` - Applies the settings system-wide. `settings-file` - Specifies a path to a JSON file containing the proxy configuration settings. This file should contain a JSON object with the relevant properties. `settings` - Specifies the proxy settings directly in JSON format. The JSON object must include the following properties:<br>- `Proxy` - A string value representing the proxy server.<br>- `ProxyBypass` - A string value listing hosts that should bypass the proxy.<br>- `AutoconfigUrl` - A string value for the URL of an automatic configuration script.<br>- `AutoDetect` - A boolean value indicating whether to automatically detect proxy settings (true or false). |
| winhttp `set proxy` | Configures the basic proxy settings for WinHTTP by specifying a proxy server and an optional list of hosts that should bypass the proxy. - `proxy-server=` - Specifies the proxy server to be used for both HTTP and HTTPS protocols. You can designate a single server, and optionally, a port number (for example, `proxy.example.com:8080`).<br>- `bypass-list=` - Provides a list of hostnames or IP addresses that should not use the proxy server and instead be accessed directly. The list should be separated by semicolons. Use an empty string (`""`) to bypass the proxy for all short-name hosts (non-fully qualified domain names). |
| winhttp `set tracing` | Related to starting network tracing activities for troubleshooting or monitoring purposes. It suggests using the following to initiate tracing, `netsh trace start scenario=InternetClient`, which starts tracing network traffic activities specifically for internet client scenarios. |
| winhttp `show``<advproxy>` | `<proxy>` | `<tracing>` | Provides options to display various WinHTTP configurations, such as: - `advproxy` - Displays the current advanced proxy settings for WinHTTP. This includes any detailed proxy configurations that have been set.<br>- `proxy` - Displays the current basic proxy settings for WinHTTP. This reveals the proxy server in use and any bypass lists that have been configured.<br>- `tracing` - Displays tracing information. It's advised to use the `netsh trace show` command. |
| `help`*or*`?` | Displays a list of commands and their descriptions in the current context. |

## Examples

To import proxy settings from Internet Explorer into WinHTTP, run the following command:

```cmd
netsh winhttp import proxy source=ie
```

To reset the WinHTTP proxy settings to their default state, run the following command:

```cmd
netsh winhttp reset proxy
```

To set advanced proxy settings for WinHTTP at the machine level using a JSON configuration string, run the following command:

```cmd
netsh winhttp set advproxy setting-scope=machine settings="{\"Proxy\":\"proxy.example.com:8080\",\"ProxyBypass\":\"*.example.com\",\"AutoconfigUrl\":\"http://config.example.com/proxy.pac\",\"AutoDetect\":true}"
```

To display the current WinHTTP proxy settings, run the following command:

```cmd
netsh winhttp show proxy
```