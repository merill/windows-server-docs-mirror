---
layout: Conceptual
title: Manage Software Inventory Logging | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/software-inventory-logging/manage-software-inventory-logging
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Describes how to manage Software Inventory Logging
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2017-10-16T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 31fc65ae-7fc7-65f8-36d0-5d55acb4c9ee
document_version_independent_id: 6c37e44c-6e00-c692-a8a9-a63202a6b43a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/software-inventory-logging/manage-software-inventory-logging.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/software-inventory-logging/manage-software-inventory-logging
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/software-inventory-logging/manage-software-inventory-logging.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e5508f27-88c2-c147-38e7-8bce8be37ecc
---

# Manage Software Inventory Logging | Microsoft Learn

This document describes how to manage Software Inventory Logging, a feature that helps datacenter administrators easily log Microsoft software asset management data for their deployments over time. This document describes how to manage Software Inventory Logging. Before using Software Inventory Logging with Windows Server 2012 R2, make sure that Windows Update [KB 3000850](https://support.microsoft.com/kb/3000850) and [KB 3060681](https://support.microsoft.com/kb/3060681) are installed on each system needing to be inventoried. No Windows Updates are required for Windows Server 2016. This feature runs locally on each server to be inventoried. It does not collect data from remote servers.

The Software Inventory Logging feature can also be added to two versions of Windows Server prior to Windows Server 2012 R2. You can install the following updates to add Software Inventory Logging functionality to Windows Server 2012 and Windows Server 2008 R2 SP1:

- **Windows Server 2012 (Standard or Datacenter Edition)**

Note

Make sure you have [WMF 4.0](https://support.microsoft.com/en-us/topic/description-of-wmf-4-0-for-windows-7-sp1-windows-embedded-standard-7-sp1-and-windows-server-2008-r2-sp1-e3c830c7-269a-8ae0-d7e9-5ab4a0c37484) installed before applying the update package below.

- WMF 4.0 Update package for Windows Server 2012: [KB 3119938](https://support.microsoft.com/kb/3119938)
- **Windows Server 2008 R2 SP1**

Note

Make sure you have [WMF 4.0](https://support.microsoft.com/en-us/topic/description-of-wmf-4-0-for-windows-7-sp1-windows-embedded-standard-7-sp1-and-windows-server-2008-r2-sp1-e3c830c7-269a-8ae0-d7e9-5ab4a0c37484) installed before applying the update package below.

- Requires [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653)
- WMF 4.0 Update package for Windows Server 2008 R2: [KB 3109118](https://support.microsoft.com/kb/3109118)

There are two primary methods for inventorying using this feature:

1. Starting the SIL logging functionality to collect from SIL data sources and forward the payload over the network to a specified target (URI) on an hourly basis.
2. Manually querying the SIL data using PowerShell or WMI at any interval.

Starting SIL logging involves some planning and foresight, but has significant advantages compared to manually querying the data. Using SIL logging has the following three primary advantages for data center administrators:

- An ongoing history (log) can be collected over time, allowing flexible and comprehensive reports from a single source.
- Computer discovery challenges typical of many inventory tools can be overcome.
- Trust boundary challenges and the need for elevated user privileges typical of many inventory tools can be overcome while maintaining a level of security, since the data is encrypted over HTTPS with SSL.

Software Inventory Logging is installed by default, but logging is not started by default. All configuration of Software Inventory Logging is done with PowerShell cmdlets. There are only a few configuration options for Software Inventory Logging. This document describes these options and their intended purpose, as well as the cmdlets used for data collection (if using the second method above).

**In this document**

The configuration options covered in this document include:

- [Starting and Stopping Software Inventory Logging](manage-software-inventory-logging#BKMK_Step1)
- [Software Inventory Logging over time](manage-software-inventory-logging#BKMK_Step2)
- [Displaying Software Inventory Logging data](manage-software-inventory-logging#BKMK_Step3)
- [Deleting data logged by Software Inventory Logging](manage-software-inventory-logging#BKMK_Step4)
- [Backing up and restoring data logged by Software Inventory Logging]manage-software-inventory-logging.md#BKMK\_Step5)
- [Reading data logged and published by Software Inventory Logging](manage-software-inventory-logging#BKMK_Step6)
- [Software Inventory Logging Security](manage-software-inventory-logging#BKMK_Step7)
- [Working with date and time settings in Windows Server Software Inventory Logging](manage-software-inventory-logging#BKMK_Step8)
- [Enabling and Configuring Software Inventory Logging in a Mounted Virtual Hard Disk](manage-software-inventory-logging#BKMK_Step10)
- [Overview of Using Software Inventory Logging in Windows Server 2012 R2 without KB 3000850](manage-software-inventory-logging#BKMK_Step11)
- [Using Software Inventory Logging in a Windows Server 2012 R2 Hyper-V environment without KB 3000850](manage-software-inventory-logging#BKMK_Step12)

Note

This topic includes sample Windows PowerShell cmdlets that you can use to automate some of the procedures described. For more information, see Using Cmdlets.

## Starting and Stopping Software Inventory Logging

Software Inventory Logging daily collection and forward over the network must be enabled on a computer running Windows Server 2012 R2 to log software inventory.

Note

You can use the **[Get-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283396%28v=wps.630%29)** PowerShell cmdlet to retrieve information about the Software Inventory Logging Service, including whether it is running or stopped.

#### To Start Software Inventory Logging

1. Sign in to the server with an account that has local administrator privileges.
2. Open PowerShell as an Administrator.
3. At the PowerShell prompt, type **[Start-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283391%28v=wps.630%29)**

Note

It is possible to set the target without setting a certificate thumbprint, but if you do, the forwards will fail and data will be stored locally for up to a default value of 30 days (after which it will be deleted). Once a valid certificate hash is set for the target (and corresponding valid certificate installed in the LocalMachine/Personal store), data stored locally will be forwarded to the target as long as the target is configured to accept this data with this certificate (see [Software Inventory Logging Aggregator](software-inventory-logging-aggregator) for more information).

#### To Stop Software Inventory Logging

1. Sign in to the server with an account that has local administrator privileges.
2. Open PowerShell as an Administrator.
3. At the PowerShell prompt, type **[Stop-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283394%28v=wps.630%29)**

## Configuring Software Inventory Logging

There are three steps to configuring Software Inventory Logging to forward data to an aggregation server over time:

1. Use **Set-SilLogging –TargetUri** to specify the web address of your aggregation server (must start with "https://").
2. Use **Set-SilLogging –CertificateThumbprint** to specify the thumbprint hash of your valid SSL certificate to be used to authenticate the data transmissions to your aggregation server (your aggregation server will need to be configured to accept hash).
3. Install a valid SSL certificate (for your network) in the **Local Machine/Personal Store** (or **/LocalMachine/MY**) of the local server to forward data from.

It is best to complete these steps before using **Start-SilLogging**. If you want to use them after using **Start-SilLogging**, you simply need to stop and start SIL again. Or, you can use the Publish-SilData Cmdlet to ensure the aggregation server has a full complement of the data for this server.

For a comprehensive guide to setting up the SIL framework as a whole, see [Software Inventory Logging Aggregator](software-inventory-logging-aggregator). In particular, if **Publish-SilData** produces an error, or SIL Logging fails otherwise, see the troubleshooting section .

## Software Inventory Logging over time

If Software Inventory Logging was started by an administrator, hourly collection and forwarding of the data to the aggregation server (target URI) commences. The first forward will be a complete data set of the same data that [Get-SilData](/en-us/previous-versions/windows/powershell-scripting/dn283388%28v=wps.630%29) retrieves and displays on the console at a point in time. Thereafter, at each interval, SIL will make a check of the data and only forward a small identifying acknowledgment to the target aggregation server if there is no change in the data since the last collection. If any value has changed, SIL will again send a complete data set.

Important

If at any interval the target URI is unreachable or the data transfer over the network is unsuccessful for any reason, data collected will be stored locally for up to a default value of 30 days (after which time it will be deleted). On the next successful forward of data to the target aggregation server, all data stored locally will be forwarded and local cached data will be deleted.

## Displaying Software Inventory Logging data

In addition to the PowerShell cmdlets described in the previous section, six additional cmdlets can be used to collect Software Inventory Logging data:

- **[Get-SilComputer](/en-us/previous-versions/windows/powershell-scripting/dn283392%28v=wps.630%29)**: Displays the point in time values for specific server and operating system-related data, as well as the FQDN or hostname of the physical host, if available.
- **[Get-SilComputerIdentity (KB 3000850)](/en-us/previous-versions/windows/powershell-scripting/dn858074%28v=wps.630%29)**: Displays identifiers used by SIL for individual servers.
- **[Get-SilData](/en-us/previous-versions/windows/powershell-scripting/dn283388%28v=wps.630%29)**: Displays a point in time collection of all Software Inventory Logging data.
- **[Get-SilSoftware](/en-us/previous-versions/windows/powershell-scripting/dn283397%28v=wps.630%29)**: Displays the point in time identity of all software installed on the computer.
- **[Get-SilUalAccess](/en-us/previous-versions/windows/powershell-scripting/dn283389%28v=wps.630%29)**: Displays the total number of unique client device requests and client user requests of the server from two days prior.
- **[Get-SilWindowsUpdate](/en-us/previous-versions/windows/powershell-scripting/dn283393%28v=wps.630%29)**: Displays the point in time list of all Windows updates installed on the computer.

A typical use case scenario for Software Inventory Logging cmdlets would be for an administrator to query Software Inventory Logging for a point in time collection of all Software Inventory Logging data using [Get-SilSoftware](/en-us/previous-versions/windows/powershell-scripting/dn283397%28v=wps.630%29).

**Output Example**

```
PS C:\> Get-SilData

ID                 : 961FF8A1-8549-4BEC-8DF6-3B3E32C26FFA
UUID               : B49ACB4C-7D9C-4806-9917-AE750BB3DA84
VMGUID             : E84CCCBD-0D0F-486B-A424-9780C7CF92E4
Name               : Server01Guest.Test.Contoso.com
HypervisorHostName : Server01.Test.Contoso.com

ID          : {F0C3E5D1-1ADE-321E-8167-68EF0DE699A5}
Name        : Microsoft Visual C++ 2010  x86 Redistributable - 10.0.40219
InstallDate : 12/5/2013
Publisher   : Microsoft Corporation
Version     : 10.0.40219

ID          : {89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
Name        : Microsoft Silverlight
InstallDate : 3/20/2014
Publisher   : Microsoft Corporation
Version     : 5.1.30214.0

ChassisSerialNumber       : 4452-0564-0284-2290-0113-6804-05
CollectedDateTime         : 10/27/2014 4:01:33 PM
Model                     : Virtual Machine
Name                      : Server01Guest.Test.Contoso.com
NumberOfCores             : 1
NumberOfLogicalProcessors : 1
NumberOfProcessors        : 1
OSName                    : Microsoft Windows Server 2012 R2 Datacenter
OSSku                     : 8
OSSuite                   : 400
OSSuiteMask               : 400
OSVersion                 : 6.3.9600
ProcessorFamily           : 179
ProcessorManufacturer     : GenuineIntel
ProcessorName             : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
SystemManufacturer        : Microsoft Corporation

```

Note

Output from this cmdlet is the same as all other **Get-Sil** cmdlets for this feature combined, but is provided to the console asynchronously so the order of the objects may not always be the same.

It is not necessary to have Software Inventory Logging started to use the **Get-Sil** cmdlets.

## Deleting data logged by Software Inventory Logging

Software Inventory Logging is not intended to be a mission critical component. Its design is intended to impact local system operations as little as possible while maintaining a high level of reliability. This also allows the administrator to manually delete Software Inventory Logging database and supporting files (every file in \Windows\System32\LogFiles\SIL directory) to meet operational needs.

#### To delete data logged by Software Inventory Logging

1. In PowerShell, stop Software Inventory Logging with the **[Stop-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283394%28v=wps.630%29)** command.
2. Open Windows Explorer.
3. Go to **\Windows\System32\Logfiles\SIL\**
4. Delete all files in the folder.

## Backing up and restoring data logged by Software Inventory Logging

Software Inventory Logging will temporarily store hourly collections of data if forwards over the network are failing. The log files are stored in the \Windows\System32\LogFiles\SIL\ directory. Backups of this Software Inventory Logging data can be made with your regularly scheduled server backups.

Important

If for any reason a repair installation or upgrade of the operating system is necessary, any log files stored locally will be lost. If this data is critical for operations, it is recommended to be backed up prior to new operating system installation. After repair or upgrade, simply restore to the same location.

Note

If for any reason managing the retention duration of data logged locally by SIL becomes important, this can be configured by changing the registry value here: \HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows\SoftwareInventoryLogging. The default is ‘30' for 30 days.

## Reading data logged and published by Software Inventory Logging

Data logged by SIL, but stored locally (if the forward to the target URI fails), or data that is successfully forwarded to the target aggregation server, is stored in a binary file (for each day's data). To display this data in PowerShell, use the [Import-BinaryMiLog](/en-us/powershell/module/cimcmdlets/import-binarymilog) cmdlet.

## Software Inventory Logging Security

Administrative privileges on the local server are required to successfully retrieve data from Software Inventory Logging WMI and PowerShell APIs.

To successfully leverage the full capability of the Software Inventory Logging feature to forward data to an aggregation point continually over time (at hourly intervals), an administrator needs to employ client certificates to ensure secure SSL sessions for transfer of data over HTTPS. A basic overview of HTTPS authentication can be found here: [HTTPS authentication](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc736680%28v=ws.10%29).

Any data stored locally on a Windows Server (only occurs if the feature is started but the target is unreachable for any reason) is only accessible with administrative privileges on the local server.

## Working with date and time settings in Windows Server 2012 R2 Software Inventory Logging

- When using [Set-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283387%28v=wps.630%29) -TimeOfDay to set the time SIL logging runs, you must specify a date and time. The calendar date will be set and logging will not occur until the date is reached, in local system time.
- When using [Get-SilSoftware](/en-us/previous-versions/windows/powershell-scripting/dn283397%28v=wps.630%29), or [Get-SilWindowsUpdate](/en-us/previous-versions/windows/powershell-scripting/dn283393%28v=wps.630%29), "InstallDate" will always show 12:00:00AM, a meaningless value.
- When using [Get-SilUalAccess](/en-us/previous-versions/windows/powershell-scripting/dn283389%28v=wps.630%29), "SampleDate" will always show 11:59:00PM, a meaningless value. Date is the pertinent data for these cmdlet queries.

## Enabling and Configuring Software Inventory Logging in a Mounted Virtual Hard Disk

Software Inventory Logging also supports configuration and enablement on offline virtual machines. The practical uses for this are intended to cover both ‘gold image' setup for wide deployment across data centers, as well as configuring end user images going from a premises to a cloud deployment.

To support these uses, Software Inventory Logging has registry entries associated with each configurable option. These registry values can be found under \HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows\SoftwareInventoryLogging.

| Function | Value Name | Data | Corresponding Cmdlet (available only in the running OS) |
| --- | --- | --- | --- |
| Start/Stop Feature | CollectionState | 1 or 0 | [Start-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283391%28v=wps.630%29), [Stop-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283394%28v=wps.630%29) |
| Specifies target aggregation point on the network | TargetUri | string | [Set-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283387%28v=wps.630%29) -TargetURI |
| Specifies Certificate Thumbprint or Hash of the certificate used for SSL authentication for the target web server | CertificateThumbprint | string | [Set-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283387%28v=wps.630%29) -CertificateThumbprint |
| Specifies the date and time that the feature should start (if value set is in the future according to local system time) | CollectionTime | Default: 2000-01-01T03:00:00 | [Set-SilLogging](/en-us/previous-versions/windows/powershell-scripting/dn283387%28v=wps.630%29) -TimeOfDay |

To modify these values on an offline VHD (VM OS not running), a VHD must be first mounted and then the following commands can be used to make changes:

- [Reg load](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742053%28v=ws.11%29)
- [Reg delete](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742145%28v=ws.11%29)
- [Reg add](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742162%28v=ws.11%29)
- [Reg unload](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742043%28v=ws.11%29)

Software Inventory Logging will check these values when the OS starts, and execute accordingly.

## Overview of Using Software Inventory Logging in Windows Server 2012 R2 without KB 3000850

The following changes to Software Inventory Logging capability and default settings were made with [KB 3000850](https://support.microsoft.com/kb/3000850):

- The default interval for collection and forward over the network when SIL logging is started changed from daily to hourly (at random within each hour).
- The default data payload was reduced to only include objects from Get-SilComputer, Get-SilComputerIdentity, and Get-SilSoftware.
- Guest to host channel communication in Hyper-V environments was removed.

## Using Software Inventory Logging in a Windows Server 2012 R2 Hyper-V environment without KB 3000850

Note

This functionality is removed with the installation of the [KB 3000850](https://support.microsoft.com/kb/3000850) update.

When using Software Inventory Logging on a Windows Server 2012 R2 Hyper-V host, it is possible to retrieve SIL data from Windows Server 2012 R2 guests that are running locally, if SIL logging has been started in the guest(s). However, this is only possible when using the Get-SilData and Publish-SilData Powershell cmdlets, and only possible with Windows Server 2012 R2 in both host and guest. The purpose of this capability is to allow data center administrators that provide guest VMs to tenants, or other entities of a large corporation, to capture software inventory data at the hypervisor host and subsequently forward all of this data to an aggregator (or target URI).

Below are two examples of what the output on the PowerShell console would look like (much abbreviated) on a Windows Server 2012 R2 Hyper-V host running one Windows Server 2012 R2 guest VM with SIL logging started. You will notice the first example, which uses Get-SilData alone, will output all data from the host as expected. Also included is all SIL data from the guest, but in a collapsed format. To expand and view this data from the guest, simply cut and paste the snippet used in the second example below. SIL data objects from the guest will always have the VM GUID associated within the object.

Note

Since SIL data is output on the console, when using the Get-SilData cmdlet, in data streams, objects will not always be output in a predictive order. In the two examples below, the text has been color coded (blue for physical host data and green for virtual guest data) only as an illustrative tool for this document.