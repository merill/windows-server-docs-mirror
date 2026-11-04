---
layout: Conceptual
title: Slmgr.vbs Options for Obtaining Volume Activation Information | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/activation-slmgr-vbs-options
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Provides a list of options available for the Slmgr.vbs script and describes usage cases.
ms.topic: best-practice
author: robinharwood
ms.author: roharwoo
ms.date: 2025-07-07T00:00:00.0000000Z
locale: en-us
document_id: dc8d11e2-15b0-9874-30b7-ad8e84c6473f
document_version_independent_id: b1acb901-eacd-d491-10ee-2b90a47921db
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/activation-slmgr-vbs-options.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/activation-slmgr-vbs-options
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/activation-slmgr-vbs-options.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0dd50ac8-91e7-5ba6-94d9-6f842f122596
---

# Slmgr.vbs Options for Obtaining Volume Activation Information | Microsoft Learn

Slmgr.vbs is a Visual Basic script included in Windows that serves as a command-line tool for managing the operating system's licensing and activation. It allows you to install and change product keys, activate Windows, and check its current activation or licensing status. It also supports tasks such as extending the activation grace period (rearming) and troubleshooting activation-related issues.

The syntax of the Slmgr.vbs script and tables in this article describe each command-line option.

```cmd
slmgr.vbs [<ComputerName> [<User> <Password>]] [<Options>]
```

Note

In this article, square brackets ([ ]) enclose optional arguments, and angle brackets (&lt; &gt;) enclose placeholders. When you type these statements, omit the brackets and replace the placeholders by using corresponding values.

For information about other software products that use volume activation, see the documents written for those applications.

## Using Slmgr on remote computers

To manage remote clients, use the Volume Activation Management Tool (VAMT) version 1.2 or later, or create custom WMI scripts that are aware of the differences between platforms. For more information, see [WMI Properties and Methods for Volume Activation](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn502536%28v=ws.11%29).

Important

Because of WMI changes in Windows 7 and Windows Server 2008 R2, the Slmgr.vbs script isn't intended to work across platforms. Using Slmgr.vbs to manage a Windows 7 or Windows Server 2008 R2 system from the Windows Vista operating system isn't supported. Trying to manage an older system from Windows 7 or Windows Server 2008 R2 generates a specific version mismatch error. For example, running **cscript slmgr.vbs &lt;vista\_machine\_name&gt; /dlv** produces the following output:

```
Microsoft (R) Windows Script Host Version 5.8
Copyright (C) Microsoft Corporation. All rights reserved.

The remote machine does not support this version of SLMgr.vbs
```

## General Slmgr.vbs options

| Option | Description |
| --- | --- |
| [&lt;ComputerName&gt;] | Name of a remote computer. (The default is the local computer.) |
| [&lt;User&gt;] | Account that has the required privilege on the remote computer. |
| [&lt;Password&gt;] | Password for the account that has the required privileges on the remote computer. |

## Global options

| Option | Description |
| --- | --- |
| /ipk &lt;ProductKey&gt; | Tries to install a 5×5 product key. The product key provided by the parameter is confirmed valid and applicable to the installed operating system.If it's not, an error is returned.If the key is valid and applicable, the key is installed. If a key is already installed, it's silently replaced.To prevent instability in the license service, the system should be restarted or the Software Protection Service should be restarted.This operation must be run from an elevated Command Prompt window, or the Standard User Operations registry value must be set to allow unprivileged users extra access to the Software Protection Service. |
| /ato [&lt;Activation ID&gt;] | For retail editions and volume systems that have a KMS host key or a Multiple Activation Key (MAK) installed, **/ato** prompts Windows to try online activation.For systems that have a Generic Volume License Key (GVLK) installed, **/ato** prompts a KMS activation attempt. Systems that are set to suspend automatic KMS activation attempts (**/stao**) still try KMS activation when **/ato** is run.**Note:** Starting in Windows 8 (and Windows Server 2012), the **/stao** option is deprecated. Use the **/act-type** option instead.The parameter &lt;**Activation ID**&gt; expands **/ato** support to identify a Windows edition installed on the computer. Specifying the &lt;**Activation ID**&gt; parameter isolates the effects of the option to the edition associated with that Activation ID. Run **slmgr.vbs /dlv all** to get the activation IDs for the installed version of Windows. If you need to support other applications, see the guidance provided by the application for further instruction.KMS activation doesn't require elevated privileges. However, online activation does require elevation, or the Standard User Operations registry value must be set to allow unprivileged users extra access to the Software Protection Service. |
| /dli [&lt;Activation ID&gt; | All] | Display license information.By default, **/dli** displays the license information for the installed active Windows edition. Specifying the &lt;**Activation ID**&gt; parameter displays the license information for the specified edition that's associated with that activation ID. Specifying **All** as the parameter displays license information for all applicable installed products.This operation doesn't require elevated privileges. |
| /dlv [&lt;Activation ID&gt; | All] | Display detailed license information.By default, **/dlv** displays the license information for the installed operating system. Specifying the &lt;**Activation ID**&gt; parameter displays the license information for the specified edition associated with that activation ID. Specifying the **All** parameter displays license information for all applicable installed products.This operation doesn't require elevated privileges. |
| /xpr [&lt;Activation ID&gt;] | Display the activation expiration date for the product. By default, the date refers to the current Windows edition and is primarily useful for KMS clients, because MAK and retail activation is perpetual.Specifying the &lt;**Activation ID**&gt; parameter displays the activation expiration date of the specified edition that's associated with that activation ID. This operation doesn't require elevated privileges. |

## Advanced options

| Option | Description |
| --- | --- |
| /cpky | Some servicing operations require the product key to be available in the registry during Out of Box Experience (OOBE) operations. The **/cpky** option removes the product key from the registry to prevent this key from being stolen by malicious code.For retail installations that deploy keys, the best practice is to run this option. This option isn't required for MAK and KMS host keys, because this is the default behavior for those keys. This option is required only for other types of keys whose default behavior isn't to clear the key from the registry.This operation must be run in an elevated Command Prompt window. |
| /ilc &lt;license\_file&gt; | This option installs the license file specified by the required parameter. These licenses might be installed as a troubleshooting measure, to support token-based activation, or as part of a manual installation of an on-boarded application.Licenses aren't validated during this process: License validation is out of scope for Slmgr.vbs. Instead, validation is handled by the Software Protection Service at runtime.This operation must be run from an elevated Command Prompt window, or the Standard User Operations registry value must be set to allow unprivileged users extra access to the Software Protection Service. |
| /rilc | This option reinstalls all licenses stored in %SystemRoot%\system32\oem and %SystemRoot%\System32\spp\tokens. These are "known-good" copies that were stored during installation.Any matching licenses in the Trusted Store are replaced. Any additional licenses—for example, Trusted Authority (TA) Issuance Licenses (ILs), licenses for applications—aren't affected.This operation must be run in an elevated Command Prompt window, or the Standard User Operations registry value must be set to allow unprivileged users extra access to the Software Protection Service. |
| /rearm | This option resets the activation timers. The **/rearm** process is also called by **sysprep /generalize**.This operation does nothing if the **HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform\SkipRearm** registry entry is set to **1**. See [Registry Settings for Volume Activation](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn502532%28v=ws.11%29) for details about this registry entry.This operation must be run in an elevated Command Prompt window, or the Standard User Operations registry value must be set to allow unprivileged users extra access to the Software Protection Service. |
| /rearm-app &lt;Application ID&gt; | Resets the licensing status of the specified app. |
| /rearm-sku &lt;Application ID&gt; | Resets the licensing status of the specified SKU. |
| /upk [&lt;Application ID&gt;] | This option uninstalls the product key of the current Windows edition. After a restart, the system will be in an Unlicensed state unless a new product key is installed.Optionally, you can use the &lt;**Activation ID**&gt; parameter to specify a different installed product.This operation must be run from an elevated Command Prompt window. |
| /dti [&lt;Activation ID&gt;] | Displays installation ID for offline activation. |
| /atp &lt;Confirmation ID&gt; | Activate product by using user-provided confirmation ID. |

## KMS client options

| Option | Description |
| --- | --- |
| /skms &lt;Name[:Port] | : Port&gt; [&lt;Activation ID&gt;] | This option specifies the name and, optionally, the port of the KMS host computer to contact. Setting this value disables auto-detection of the KMS host.If the KMS host uses Internet Protocol version 6 (IPv6) only, the address must be specified in the format &lt;hostname&gt;:&lt;port&gt;. IPv6 addresses contain colons (:), which the Slmgr.vbs script doesn't parse correctly.This operation must be run in an elevated Command Prompt window. |
| /skms-domain &lt;FQDN&gt; [&lt;Activation ID&gt;] | Sets the specific DNS domain in which all KMS SRV records can be found. This setting has no effect if the specific single KMS host is set by using the **/skms** option. Use this option, especially in disjoint namespace environments, to force KMS to ignore the DNS suffix search list and look for KMS host records in the specified DNS domain instead. |
| /ckms [&lt;Activation ID&gt;] | This option removes the specified KMS host name, address, and port information from the registry and restores KMS autodiscovery behavior.This operation must be run in an elevated Command Prompt window. |
| /skhc | This option enables KMS host caching (default). After the client discovers a working KMS host, this setting prevents the Domain Name System (DNS) priority and weight from affecting further communication with the host. If the system can no longer contact the working KMS host, the client tries to discover a new host.This operation must be run in an elevated Command Prompt window. |
| /ckhc | This option disables KMS host caching. This setting instructs the client to use DNS autodiscovery each time it tries KMS activation (recommended when using priority and weight).This operation must be run in an elevated Command Prompt window. |

## KMS host configuration options

| Option | Description |
| --- | --- |
| /sai &lt;Interval&gt; | This option sets the interval, in minutes, for unactivated clients to try to connect to KMS. The activation interval must be between 15 minutes and 30 days, although the default value (two hours) is recommended.The KMS client initially picks up this interval from the registry but switches to the KMS setting after it receives the first KMS response.This operation must be run in an elevated Command Prompt window. |
| /sri &lt;Interval&gt; | This option sets the renewal interval, in minutes, for activated clients to try to connect to KMS. The renewal interval must be between 15 minutes and 30 days. This option is set initially on both the KMS server and client sides. The default value is 10,080 minutes (7 days).The KMS client initially picks up this interval from the registry but switches to the KMS setting after it receives the first KMS response.This operation must be run in an elevated Command Prompt window. |
| /sprt &lt;Port&gt; | This option sets the port on which the KMS host listens for client activation requests. The default TCP port is 1688.This operation must be run from an elevated Command Prompt window. |
| /sdns | Enable DNS publishing by the KMS host (default).This operation must be run in an elevated Command Prompt window. |
| /cdns | Disable DNS publishing by the KMS host.This operation must be run in an elevated Command Prompt window. |
| /spri | Set the KMS priority to normal (default).This operation must be run in an elevated Command Prompt window. |
| /cpri | Set the KMS priority to low.Use this option to minimize contention from KMS in a co-hosted environment, which can cause KMS starvation depending on what other applications or server roles are active. Use this option with care.This operation must be run in an elevated Command Prompt window. |
| /act-type [&lt;Activation-Type&gt;] [&lt;Activation ID&gt;] | This option sets a value in the registry that limits volume activation to a single type. Activation type **1** limits activation to Active Directory only. **2** limits it to KMS activation. **3** limits it to token-based activation. The **0** option allows any activation type and is the default value. |

## Token-based activation configuration options

| Option | Description |
| --- | --- |
| /lil | List the installed token-based activation issuance licenses. |
| /ril &lt;ILID&gt; &lt;ILvID&gt; | Remove an installed token-based activation issuance license.This operation must be run from an elevated Command Prompt window. |
| /stao | Set the **Token-based Activation Only** flag, disabling automatic KMS activation.This operation must be run in an elevated Command Prompt window.This option was removed in Windows Server 2012 R2 and Windows 8.1. Use the **/act–type** option instead. |
| /ctao | Clear the **Token-based Activation Only** flag (default), enabling automatic KMS activation.This operation must be run in an elevated Command Prompt window.This option was removed in Windows Server 2012 R2 and Windows 8.1. Use the **/act–type** option instead. |
| /ltc | List valid token-based activation certificates that can activate installed software. |
| /fta &lt;Certificate Thumbprint&gt; [&lt;PIN&gt;] | Force token-based activation by using the identified certificate. The optional personal identification number (PIN) is provided to unlock the private key without a PIN prompt if you use certificates that are protected by hardware (for example, smart cards). |

## Active Directory-based activation configuration options

| Option | Description |
| --- | --- |
| /ad-activation-online &lt;Product Key&gt; [&lt;Activation Object name&gt;] | Collects Active Directory data and starts Active Directory forest activation using the credentials that the command prompt is running. Local administrator access isn't required. However, Read/Write access to the activation object container in the root domain of the forest is required. |
| /ad-activation-get-IID &lt;Product Key&gt; | This option starts Active Directory forest activation in phone mode. The output is the installation ID (IID) that can be used to activate the forest over the telephone if internet connectivity isn't available. When the IID is provided in the activation phone call, a CID is returned that's used to complete activation. |
| /ad-activation-apply-cid &lt;Product Key&gt; &lt;Confirmation ID&gt; [&lt;Activation Object name&gt;] | When you use this option, enter the CID that was provided in the activation telephone call to complete activation |
| [/name: &lt;AO\_Name&gt;] | Optionally, you can append the **/name** option to any of these commands to specify a name for the activation object stored in Active Directory. The name must not exceed 40 Unicode characters. Use double quotation marks to explicitly define the name string.In Windows Server 2012 R2 and Windows 8.1, you can append the name directly after **/ad-activation-online &lt;Product Key&gt;** and **/ad-activation-apply-cid** without having to use the **/name** option. |
| /ao-list | Displays all of the activation objects that are available to the local computer. |
| /del-ao &lt;AO\_DN&gt;/del-ao &lt;AO\_RDN&gt; | Deletes the specified activation object from the forest. |