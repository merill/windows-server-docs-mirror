---
layout: Conceptual
title: netsh mbn | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-mbn
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh mbn command manages Mobile Broadband (MBN) interfaces, cellular modems, and SIM-based network connections in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-10-09T00:00:00.0000000Z
locale: en-us
document_id: 558847f1-1134-13ff-f2ea-d783e3b2ce00
document_version_independent_id: 558847f1-1134-13ff-f2ea-d783e3b2ce00
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-mbn.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-mbn
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-mbn.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: d1fb31f7-6932-552a-7088-bfd92a9665a9
---

# netsh mbn | Microsoft Learn

The `netsh mbn` command is used to configure, monitor, and troubleshoot Mobile Broadband (MBN) interfaces, including cellular modems and SIM-based network connections. It provides a range of options for managing profiles, connections, radio states, and advanced settings for mobile broadband devices on Windows.

The **WWAN AutoConfig** service must be running on your device for certain commands and parameters to function.

## Syntax

```
netsh mbn [add | connect | delete | disconnect | dump | help | set | show | test | ?]
```

```
netsh mbn add dmprofile [interface=]<string> [name=]<string>
netsh mbn add profile [interface=]<string> [name=]<string>
```

```
netsh mbn connect [interface=]<string> [connmode=]tmp|name [name=]<string>
```

```
netsh mbn delete dmprofile [interface=]<string> [name=]<string>
netsh mbn delete profile [interface=]<string> [name=]<string>
```

```
netsh mbn disconnect [interface=]<string>
```

```
netsh mbn set acstate [interface=]<string> [state=]autooff|autoon|manualoff|manualon
netsh mbn set dataenablement [interface=]<string> [profileset=]internet|mms|all [mode=]yes|no
netsh mbn set dataroamcontrol [interface=]<string> [profileset=]internet|mms|all [state=]none|partner|all
netsh mbn set enterpriseapnparams [interface=]<string> [allowusercontrol=]yes|no|nc [allowuserview=]yes|no|nc
                                  [profileaction=]add|delete|modify|nc
netsh mbn set highestconncategory [interface=]<string> [highestcc=]admim|user|operator|device
netsh mbn set powerstate [interface=]<string> [state=]on|off
netsh mbn set profileparameter [name=]<string> [[interface=]<string>] [cost]=default|unrestricted|fixed|variable
netsh mbn set slotmapping [interface=]<string> [slotindex=]<integer>
netsh mbn set tracing [mode=]yes|no
```

```
netsh mbn show acstate [interface=]<string>
               basestationinfo [interface=]<string>
               capability [interface=]<string>
               connection [interface=]<string>
               d3cold [interface=]<string>
               dataenablement [interface=]<string>
               dataroamcontrol [interface=]<string>
               dmprofiles [name=]<string> [interface=]<string>
               enterpriseapnparams [interface=]<string>
               highestconncategory [interface=]<string>
               homeprovider [interface=]<string>
               interfaces
               McmInfo [interface=]<string>
               netlteattachinfo [interface=]<string>
               pin [interface=]<string>
               pinlist [interface=]<string>
               preferredproviders [interface=]<string>
               profiles [name=]<string> [interface=]<string> [purpose=]<string>
               profilestate [interface=]<string> [name=]<string>
               provisionedcontexts [interface=]<string> [name=]<string>
               purpose
               radio [interface=]<string>
               readyinfo [interface=]<string> [slotindex=]<integer>
               signal [interface=]<string>
               slotmapping [interface=]<string>
               slotstatus [interface=]<string>
               smsconfig [interface=]<string>
               tracing
               UICCCardAdditionalInfoWithEFHPLMNwAct [interface=]<string>
               visibleproviders [interface=]<string>
```

```
netsh mbn test [feature=<feature area>] [testPath=<path>] [taefPath=<path>] [param=<test input params>]
```

## Parameters

| Command | Description |
| --- | --- |
| mbn `add` | `dmprofile` - Adds a Mobile Broadband Device Management Config Profile for the given interface for all users: `interface` - The interface name. `name` - The XML profile name. `profile` - Adds a Mobile Broadband Network Profile for the given interface for all users: `interface` - The interface name. `name` - The XML profile name.  The `interface` and `name` parameters are required. |
| mbn `connect` | Connects to a Mobile Broadband Network using a specified profile. The device must be registered before running this command. The `interface` parameter is required. `connmode` - Determines how connection parameters are provided:  - `tmp`: Use a profile XML file for a temporary connection.  - `name`: Use a profile that was previously stored with the `netsh mbn add profile` command. `name` - If `connmode` is set to `tmp`, specify the profile XML file name. If `connmode` is set to `name`, specify the stored profile name. |
| mbn `delete` | `dmprofile` - Removes a Mobile Broadband Device Management Config Profile for the given interface. `interface` - The interface name. `name` - The XML profile name. `profile` - Removes a Mobile Broadband Network Profile from the given interface: `interface` - The interface name. `name` - The XML profile name.  The `interface` and `name` parameters are required. |
| mbn `disconnect` | Disconnects from the Mobile Broadband Network on the specified interface: `interface` - The interface name.  The `interface` parameter is required. |
| mbn `dump` | Creates a script containing the current context configuration. The script can be saved to a file and used to restore settings if they're altered or need to be replicated on another system. |
| mbn `set` | Configures one of the following settings: `acstate` - Configures the auto-connect behavior for Mobile Broadband data on the interface. The parameters `interface` and `state` are required. `state` - Configures one of the following values:  - `autooff`: Turns auto connect token off.  - `autoon`: Turns auto-connect token on.  - `manualoff`: Turns off the manual connect token.  - `manualon`: Turns on the manual connect token. `dataenablement` - Enables or disables Mobile Broadband data for a specified profile set and interface. The parameters `interface`, `profileset`, and `mode` are required. `profileset` - Is the name of the profile set:  - `internet`, `mms`, or `all` - `mode`: Enables (`yes`) or disables (`no`) the target profile set. `dataroamcontrol` - Adjusts data roaming settings for Mobile Broadband on the selected profile set and interface. The parameters `interface`, `profileset`, and `mode` are required. `profileset` - Is the name of the profile set:  - `internet`, `mms`, or `all` - `state`: Applies changes to the home carrier only (`none`), home and partner carriers only (`partner`), or home, partner, and roaming carriers (`all`). `enterpriseapnparams` - Modifies enterprise Access Point Name (APN) parameters for Mobile Broadband on the specified interface. The parameters `interface`, `allowusercontrol`, `allowuserview`, and `profileaction` are required.  - `allowusercontrol`: Allows (`yes`) or disallows (`no`) end user control of enterpriseAPN. Use `nc` to leave at default state.  - `allowuserview`: Allows (`yes`) or disallows (`no`) end user view of enterpriseAPN. Use `nc` to leave at default state.  - `profileaction`: Adds (`add`), deletes (`delete`) or modifies (`modify`) an enterpriseAPN profile. Use `nc` to leave at default state. `highestconncategory` - Specifies the highest allowed connection category for Mobile Broadband on the given interface. The parameters `interface` and `highestcc` are required.  - Sets one of the provisioned profile types:  - `admin` - `user` - `operator` - `device``powerstate` - Switches the Mobile Broadband radio on or off for the specified interface. The parameters `interface` and `state` are required. `state`: Enables (`yes`) or disables (`no`) the radio transceiver. `profileparameter` - Updates parameters within a Mobile Broadband Network Profile. The `name` parameter and at least one other parameter, such as `interface` or `cost`, must be specified.  - `name`: The profile name to be modified.  - `interface`: The interface name.  - `cost`: The cost associated with the profile. `slotmapping` - Assigns modem slot mapping for Mobile Broadband on the specified interface. The parameters `interface` and `slotindex` are required.  - `interface`: The interface name.  - `slotindex`: The interface slot index number to be set. `tracing` - Turns tracing on or off for Mobile Broadband operations. The `mode` parameter is required.  - `mode`: Enables (`yes`) or (`disables`) tracing for the Mobile Broadband. |
| mbn `show` | Displays on of the following information: `acstate interface=` - Displays the auto connect state for Mobile Broadband data on the specified interface. `basestationinfo interface=` - Displays base station information for the specified interface. `capability interface=` - Displays capability details for the specified interface. `connection interface=` - Displays current connection details for the specified interface. `d3cold interface=` - Indicates whether the modem supports D3Cold power state for the specified interface. `dataenablement interface=` - Displays the data enablement status for the specified interface. `dataroamcontrol interface=` - Displays the data roaming control status for the specified interface. `dmprofiles` - Lists Direct Management Config profiles configured on the system. Use the `name` and `interface` parameters to filter for specific profiles on certain interfaces. `enterpriseapnparams interface=` - Displays enterprise APN parameters for the specified interface. `highestconncategory interface=` - Displays the highest connection category for the specified interface. `homeprovider interface=` - Displays home provider details for the specified interface. `interfaces` - Lists all Mobile Broadband interfaces on the system. `McmInfo interface=` - Displays MCM-related information for the specified interface. `netlteattachinfo interface=` - Displays LTE attach information for the specified interface. `pin interface=` - Displays PIN information for the specified interface. `pinlist interface=` - Displays the list of PINs for the specified interface. `preferredproviders interface=` - Displays the list of preferred providers for the specified interface. `profiles` - Lists all configured profiles on the system. Use the `name` and `interface` parameters to filter for specific profiles on certain interfaces. If `purpose` is provided, only profiles with the matching purpose GUID are displayed. The following strings are acceptable:  - `GUID` - `internet` - `supl` - `mms` - `ims` - `allhost``profilestate` - Displays the state of a profile for the specified interface. The `interface` and `name` parameters are required. `provisionedcontexts interface=` - Displays provisioned context information for the specified interface. `purpose` - Displays available purpose group GUIDs. `radio interface=` - Displays radio state information for the specified interface. `readyinfo` - Displays readiness information for the specified interface. The `interface` parameter is required while `slotindex` is optional. `signal interface=` - Displays signal strength and quality for the specified interface. `slotmapping interface=` - Displays modem slot mapping for the specified interface. `slotstatus interface=` - Displays modem slot status for the specified interface. `smsconfig interface=` - Displays SMS configuration details for the specified interface. `tracing` - Indicates whether tracing is enabled or disabled. `UICCCardAdditionalInfoWithEFHPLMNwAct interface=` - Displays EFInfo in UICC for the specified interface. `visibleproviders interface=` - Displays the list of visible providers for the specified interface. |
| mbn `test` | Performs mobile broadband testing operations. `feature` (required) - Is the feature area:  - `connectivity` - `power` - `radio` - `esim` - `esimhlk` - `sms` - `dssa` - `lte` - `bringup` - `nr``testpath` - Is the path containing the test binaries. `taefpath` - Is the path containing the TAEF binaries. `param` - Tests other fields using colon separated values:  - `connectivity`, `radio`, or `bringup`: The `AccessString` or `UserName` (if applicable), and `Password` (if applicable).  - `esim`: The `ActivationCode`.  The `testPath` and `taefPath` parameters are optional on amd64 devices where HLK Server is installed. |
| mbn `help` or `?` | Displays a list of commands and their descriptions in the current context. |

## Remarks

- Values given to the `interface` parameter must be wrapped in double quotes (**" "**) for interface names containing a space.
- If you're in the `mbn` context, you can run `show interfaces` to display all interface names.

## Examples

To add a Device Management profile for the mobile broadband interface named "Cellular", with the profile name "EnterpriseDM", run the following command:

```cmd
netsh mbn add dmprofile interface=Cellular name=EnterpriseDM
```

To connect the mobile broadband interface "Cellular" using a temporary profile XML file named "temp\_profile.xml", run the following command:

```cmd
netsh mbn connect interface=Cellular connmode=tmp name=temp_profile.xml
```

To disconnect the mobile broadband interface "Cellular", run the following command:

```cmd
netsh mbn disconnect interface=Cellular
```

To turn on auto-connect for the "Cellular" interface, run the following command:

```cmd
netsh mbn set acstate interface=Cellular state=autoon
```

To add an enterprise APN profile for the "Cellular" interface, allowing user control, and view, run the following command:

```cmd
netsh mbn set enterpriseapnparams interface=Cellular allowusercontrol=yes allowuserview=yes profileaction=add
```

To display the tracing status for Mobile Broadband commands, run the following command:

```cmd
netsh mbn show tracing
```

To perform a connectivity test with the AccessString "internet", run the following command:

```cmd
netsh mbn test feature=connectivity param="AccessString=internet"
```

To perform an eSIM test that selects the DSSA category, run the following command:

```cmd
netsh mbn test feature=esim param="/select:\"(@Category='DSSA')\""
```