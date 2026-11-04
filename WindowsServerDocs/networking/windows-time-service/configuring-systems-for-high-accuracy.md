---
layout: Conceptual
title: Configuring systems for high accuracy in Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/windows-time-service/configuring-systems-for-high-accuracy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Improve Windows Time synchronization tuning under reasonable operating conditions where systems can be configured to maintain 1 ms (millisecond) accuracy or better with respect to UTC.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-02-25T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5ae7984f-3233-b06b-c37c-5cf5042d3249
document_version_independent_id: 9667685a-aaa5-af79-2598-cd5b4d411045
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/windows-time-service/configuring-systems-for-high-accuracy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/windows-time-service/configuring-systems-for-high-accuracy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/windows-time-service/configuring-systems-for-high-accuracy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: ce066749-f9a2-eca2-868d-0857ed686409
---

# Configuring systems for high accuracy in Windows | Microsoft Learn

Time synchronization in Windows 10 and Windows Server 2016 is enhanced. Under optimal conditions, these systems can be configured to achieve and maintain an accuracy of 1 millisecond (ms) or better with respect to UTC.

Warning

Windows Server 2012 R2 and previous releases doesn't meet the same high accuracy objectives. These operating systems aren't supported for high accuracy. In these versions, the Windows Time service satisfied the following requirements:

- Provided the necessary time accuracy to satisfy Kerberos version 5 authentication requirements.
- Provided loosely accurate time for Windows clients and servers joined to a common Active Directory forest.

Greater tolerances on 2012 R2 and previous releases are outside the design specification of the Windows Time service.

## Windows 10 and Windows Server 2016 default configuration

While we support accuracy up to 1 ms on Windows 10 or Windows Server 2016, most customers don't require highly accurate time.

As such, the **default configuration** is intended to satisfy the same requirements as prior operating systems that:

- Provide the necessary time accuracy to satisfy Kerberos version 5 authentication requirements.
- Provide loosely accurate time for Windows clients and servers joined to a common Active Directory forest.

## How to configure systems for high accuracy

Time accuracy entails the end-to-end distribution of accurate time from the authoritative time source to the end device. Anything that adds asymmetry in measurements along this path negatively influences the accuracy achievable on your devices.

For this reason, the [Support boundary to configure the Windows Time service for high-accuracy environments](support-boundary) is documented outlining the environmental requirements that must also be satisfied to reach high accuracy targets.

### Operating System requirements

High accuracy configurations require Windows 10 or Windows Server 2016. All Windows devices in the time topology must meet this requirement including higher stratum Windows time servers, and in virtualized scenarios, the Hyper-V Hosts that run the time-sensitive virtual machines. All of these devices must be at least Windows 10 or Windows Server 2016.

In the following illustration, the virtual machines requiring high accuracy are running Windows 10 or Windows Server 2016. Likewise, the Hyper-V Host on which the virtual machines reside, and the upstream Windows time server must also run Windows Server 2016.

![A diagram that shows three virtual machines connected to a Windows Server 2016 Hyper-V host utilizing the Windows Time service.](../media/windows-time-service/configuring-systems-for-high-accuracy/topology-2016.png)

Tip

You can run the `winver` command in a command prompt or through PowerShell to view the OS version and build number:

![A screenshot of the w i n v e r command displaying Windows Server 2016 version 1607 and operating system build 14393.](../media/windows-time-service/configuring-systems-for-high-accuracy/winver-2016.png)

### System configuration

Reaching high accuracy targets requires system configuration. There are various ways to perform this configuration, including directly in the registry or through group policy. More information for each of these settings can be found in the [Windows Time Service Technical Reference: Windows Time Service Tools](windows-time-service-tools-and-settings#windows-time-service-tools-and-settings).

### Windows Time service startup type

To ensure the Windows Time service (W32Time) runs continuously, set its startup type to **Automatic**.

![A screenshot of the Windows Time service properties box displaying its startup type set to automatic.](../media/windows-time-service/configuring-systems-for-high-accuracy/automatic-service.png)

### Cumulative one-way network latency

Measurement uncertainty and "noise" increases network latency. As such, it's imperative that a network latency be within a reasonable boundary. The specific requirements are dependent on your target accuracy and are outlined in the [Support boundary to configure the Windows Time service for high-accuracy environments](support-boundary) article.

To calculate the cumulative one-way network latency, add the individual one-way delays between pairs of Network Time Protocol (NTP) client-server nodes in the time topology, starting with the target and ending at the high-accuracy stratum 1 time source.

For example: Consider a time sync hierarchy with a highly accurate source, two intermediary NTP servers A and B, and the target machine in that order. To obtain the cumulative network latency between the target and source, measure the average individual NTP roundtrip times (RTTs) between:

- The target and time server B
- Time server B and time server A
- Time server A and the Source

This measurement can be obtained using the inbox `w32tm.exe` tool by performing the following steps:

1. Perform the calculation from the target and time server B.

    ```cmd
    w32tm /stripchart /computer:TimeServerB /rdtsc /samples:450 > c:\temp\Target_TsB.csv
    ```
2. Perform the calculation from time server B against (pointed at) time server A.

    ```cmd
    w32tm /stripchart /computer:TimeServerA /rdtsc /samples:450 > c:\temp\Target_TsA.csv
    ```
3. Perform the calculation from time server A against the source.
4. Next, add the average RoundTripDelay measured in the previous step and divide by 2 to obtain the cumulative network delay between target and source.

## Registry settings

### MinPollInterval

Configures the smallest interval in log2 seconds allowed for system polling.

| Description | Value |
| --- | --- |
| Key location | HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Config |
| Setting | 6 |
| Outcome | The minimum polling interval is now 64 seconds. |

### MaxPollInterval

Configures the largest interval in log2 seconds allowed for system polling.

| Description | Value |
| --- | --- |
| Key location | HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Config |
| Setting | 6 |
| Outcome | The maximum polling interval is now 64 seconds. |

### UpdateInterval

The number of clock ticks between phase correction adjustments.

| Description | Value |
| --- | --- |
| Key location | HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Config |
| Setting | 100 |
| Outcome | The number of clock ticks between phase correction adjustments is now 100 ticks. |

### SpecialPollInterval

Configures the poll interval in seconds when the SpecialInterval 0x1 flag is enabled.

| Description | Value |
| --- | --- |
| Key location | HKLM\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\NtpClient |
| Setting | 64 |
| Outcome | The poll interval is now 64 seconds. |

### FrequencyCorrectRate

| Description | Value |
| --- | --- |
| Key location | HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Config |
| Setting | 2 |

### UtilizeSslTimeData

| Description | Value |
| --- | --- |
| Key location | HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Config |
| Setting | 0 |
| Outcome | Secure Time Seeding feature is disabled. |

## Applying modified registry settings

The following command signals Windows Time to pick up the updated settings:

```cmd
w32tm /config /update
```

The following command restarts Windows Time to pick up the updated settings:

```cmd
net stop w32time && net start w32time
```

Applying UtilizeSslTimeData setting change requires system restart.

Note

To learn more about the W32Time registry settings, see [W32Time registry reference](windows-time-service-tools-and-settings#w32time-registry-reference)