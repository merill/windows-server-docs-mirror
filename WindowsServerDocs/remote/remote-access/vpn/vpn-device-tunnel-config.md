---
layout: Conceptual
title: Configure the VPN device tunnel in Windows client | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/vpn/vpn-device-tunnel-config
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to create a VPN device tunnel in Windows client.
ms.date: 2023-01-25T00:00:00.0000000Z
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
locale: en-us
document_id: cc584192-594f-3633-21e1-6881bf186c01
document_version_independent_id: 7ec2db2e-cb49-90e5-4d71-209e9754666c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/vpn/vpn-device-tunnel-config.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/vpn/vpn-device-tunnel-config
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/vpn/vpn-device-tunnel-config.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 82727429-6a91-a675-9319-52aec417991f
---

# Configure the VPN device tunnel in Windows client | Microsoft Learn

Always On VPN gives you the ability to create a dedicated VPN profile for device or machine. Always On VPN connections include two types of tunnels:

- *Device tunnel* connects to specified VPN servers before users log on to the device. Pre-login connectivity scenarios and device management purposes use device tunnel.
- *User tunnel* connects only after a user logs on to the device. User tunnel allows users to access organization resources through VPN servers.

Unlike *user tunnel*, which only connects after a user logs on to the device or machine, *device tunnel* allows the VPN to establish connectivity before the user logs on. Both *device tunnel* and *user tunnel* operate independently with their VPN profiles, can be connected at the same time, and can use different authentication methods and other VPN configuration settings as appropriate. User tunnel supports SSTP and IKEv2, and device tunnel supports IKEv2 only with no support for SSTP fallback.

User tunnel is supported on domain-joined, nondomain-joined (workgroup), or Microsoft Entra ID–joined devices to allow for both enterprise and BYOD scenarios. It is available in all Windows editions, and the platform features are available to third parties by way of UWP VPN plug-in support.

Device tunnel can only be configured on domain-joined devices running Windows 10 Enterprise or Education version 1709 or later. There is no support for third-party control of the device tunnel. If only a Device Tunnel is used on a system, you can configure a Name Resolution Policy table (NRPT). If a User Tunnel and a Device Tunnel are used on a system, you can use the Name Resolution Policy table (NRPT) only on the User Tunnel.

Device tunnel does not support Force tunnel. You must configure it as Split tunnel. |

## Prerequisites

You must enable machine certificate authentication for VPN connections and define a root certification authority for authenticating incoming VPN connections.

```PowerShell
$VPNRootCertAuthority = "Common Name of trusted root certification authority"
$RootCACert = (Get-ChildItem -Path cert:LocalMachine\root | Where-Object {$_.Subject -Like "*$VPNRootCertAuthority*" })
Set-VpnAuthProtocol -UserAuthProtocolAccepted Certificate, EAP -RootCertificateNameToAccept $RootCACert -PassThru
```

![Device Tunnel Features and Requirements](../../media/device-tunnel-feature-and-requirements.png)

## VPN Device Tunnel Configuration

The sample profile XML below provides good guidance for scenarios where only client initiated pulls are required over the device tunnel. Traffic filters are leveraged to restrict the device tunnel to management traffic only. This configuration works well for Windows Update, typical Group Policy (GP) and Microsoft Endpoint Configuration Manager update scenarios, as well as VPN connectivity for first logon without cached credentials, or password reset scenarios.

For server-initiated push cases, like Windows Remote Management (WinRM), Remote GPUpdate, and remote Configuration Manager update scenarios – you must allow inbound traffic on the device tunnel, so traffic filters cannot be used. If in the device tunnel profile you turn on traffic filters, then the Device Tunnel denies inbound traffic. This limitation is going to be removed in future releases.

### Sample VPN profileXML

Following is the sample VPN profileXML.

```xml
<VPNProfile>
  <NativeProfile>
<Servers>vpn.contoso.com</Servers>
<NativeProtocolType>IKEv2</NativeProtocolType>
<Authentication>
  <MachineMethod>Certificate</MachineMethod>
</Authentication>
<RoutingPolicyType>SplitTunnel</RoutingPolicyType>
 <!-- disable the addition of a class based route for the assigned IP address on the VPN interface -->
<DisableClassBasedDefaultRoute>true</DisableClassBasedDefaultRoute>
  </NativeProfile>
  <!-- use host routes(/32) to prevent routing conflicts -->
  <Route>
<Address>10.10.0.2</Address>
<PrefixSize>32</PrefixSize>
  </Route>
  <Route>
<Address>10.10.0.3</Address>
<PrefixSize>32</PrefixSize>
  </Route>
<!-- traffic filters for the routes specified above so that only this traffic can go over the device tunnel -->
  <TrafficFilter>
<RemoteAddressRanges>10.10.0.2, 10.10.0.3</RemoteAddressRanges>
  </TrafficFilter>
<!-- need to specify always on = true -->
  <AlwaysOn>true</AlwaysOn>
<!-- new node to specify that this is a device tunnel -->
 <DeviceTunnel>true</DeviceTunnel>
<!--new node to register client IP address in DNS to enable manage out -->
<RegisterDNS>true</RegisterDNS>
</VPNProfile>
```

Depending on the needs of each particular deployment scenario, another VPN feature that can be configured with the device tunnel is [Trusted Network Detection](/en-us/answers/topics/windows-server-infrastructure.html).

```
 <!-- inside/outside detection -->
  <TrustedNetworkDetection>corp.contoso.com</TrustedNetworkDetection>
```

## Deployment and Testing

You can configure device tunnels by using a Windows PowerShell script and using the Windows Management Instrumentation (WMI) bridge. The Always On VPN device tunnel must be configured in the context of the **LOCAL SYSTEM** account. To accomplish this, it will be necessary to use [PsExec](/en-us/sysinternals/downloads/psexec), one of the [PsTools](/en-us/sysinternals/downloads/pstools) included in the [Sysinternals](/en-us/sysinternals/) suite of utilities.

For guidelines on how to deploy a per device `(.\Device)` vs. a per user `(.\User)` profile, see [Using PowerShell scripting with the WMI Bridge Provider](/en-us/windows/client-management/mdm/using-powershell-scripting-with-the-wmi-bridge-provider).

Run the following Windows PowerShell command to verify that you have successfully deployed a device profile:

```powershell
Get-VpnConnection -AllUserConnection
```

The output displays a list of the device-wide VPN profiles that are deployed on the device.

### Example Windows PowerShell Script

You can use the following Windows PowerShell script to assist in creating your own script for profile creation.

```PowerShell
Param(
[string]$xmlFilePath,
[string]$ProfileName
)

$a = Test-Path $xmlFilePath
echo $a

$ProfileXML = Get-Content $xmlFilePath

echo $XML

$ProfileNameEscaped = $ProfileName -replace ' ', '%20'

$Version = 201606090004

$ProfileXML = $ProfileXML -replace '<', '&lt;'
$ProfileXML = $ProfileXML -replace '>', '&gt;'
$ProfileXML = $ProfileXML -replace '"', '&quot;'

$nodeCSPURI = './Vendor/MSFT/VPNv2'
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_VPNv2_01"

$session = New-CimSession

try
{
$newInstance = New-Object Microsoft.Management.Infrastructure.CimInstance $className, $namespaceName
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ParentID", "$nodeCSPURI", 'String', 'Key')
$newInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("InstanceID", "$ProfileNameEscaped", 'String', 'Key')
$newInstance.CimInstanceProperties.Add($property)
$property = [Microsoft.Management.Infrastructure.CimProperty]::Create("ProfileXML", "$ProfileXML", 'String', 'Property')
$newInstance.CimInstanceProperties.Add($property)

$session.CreateInstance($namespaceName, $newInstance)
$Message = "Created $ProfileName profile."
Write-Host "$Message"
}
catch [Exception]
{
$Message = "Unable to create $ProfileName profile: $_"
Write-Host "$Message"
exit
}
$Message = "Complete."
Write-Host "$Message"
```