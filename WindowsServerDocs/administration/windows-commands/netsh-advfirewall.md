---
layout: Conceptual
title: netsh advfirewall | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-advfirewall
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the netsh command, which is a command-line scripting utility that allows you to display or modify the network configuration of a currently running computer locally or remotely.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-24T00:00:00.0000000Z
locale: en-us
document_id: 1e98af0a-fbdb-de25-fde6-670e2ce347c1
document_version_independent_id: 1e98af0a-fbdb-de25-fde6-670e2ce347c1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-advfirewall.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-advfirewall
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-advfirewall.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 2eeedee5-43db-324d-5c5d-99c448b7d255
---

# netsh advfirewall | Microsoft Learn

The `netsh advfirewall` command configures and manages the Windows Firewall with Advanced Security utility. This tool allows administrators to configure firewall rules, security policies, and monitor various aspects of the firewall's behavior.

## Syntax

The `netsh advfirewall` command provides various subcommands and contexts based on the specific operation you want to perform.

```
netsh advfirewall consec | dump | export | firewall | help | import | mainmode | monitor | reset | set | show | ?
```

```
netsh advfirewall [consec | firewall | mainmode] <add> <delete> <dump> <help> <set> <show> <?>
```

```
netsh advfirewall [monitor] <delete> <dump> <help> <show> <?>
```

```
netsh advfirewall export <path\filename>
netsh advfirewall import <path\filename>
netsh advfirewall reset [export <path\filename>]
```

```
netsh advfirewall set [allprofiles | currentprofile | domainprofile | privateprofile | publicprofile] state <on> <off> <notconfigured>
netsh advfirewall set firewallpolicy <blockinbound> <blockinboundalways> <allowinbound> <allowoutbound> <blockoutbound> <notconfigured>
netsh advfirewall set settings <localfirewallrules> <localconsecrules> <inboundusernotification> <remotemanagement> <unicastresponsetomulticast>
netsh advfirewall set logging <allowedconnections> <droppedconnections> <filename> <maxfilesize>
netsh advfirewall set global [statefulftp | statefulpptp] <enable> <disable> <notconfigured>
netsh advfirewall set global ipsec [strongcrlcheck <value>] [saidletimemin <value>] [defaultexemptions <value>] [ipsecthroughnat <value>] [authzcomputergrp <value>] [authzusergrp <value>]
netsh advfirewall set global mainmode [mmkeylifetime <value>] [mmsecmethods <value>] [mmforcedh <value>]
```

```
netsh advfirewall show [allprofiles | currentprofile | domainprofile | privateprofile | publicprofile] <state> <firewallpolicy> <settings> <logging>
netsh advfirewall show global <ipsec> <statefulftp> <statefulpptp> <mainmode> <categories>
netsh advfirewall show <store>
```

## Parameters

| Command | Description |
| --- | --- |
| consec `<add>``<delete>``<help>``<set>``<show>` rule name=`<string>` consec `<dump>` | Switches to the `netsh advfirewall consec` context to configure connection security rules. - add - Adds a new connection security rule.<br>- delete - Deletes all matching connection security rules.<br>- dump - Displays a configuration script.<br>- help - Displays a list of commands.<br>- set - Sets new values for properties of an existing rule.<br>- show - Displays a specified connection security rule. |
| dump | Displays a configuration script that can be used to restore the current configuration. |
| export `<path\filename>` | Exports the current firewall policy settings to a specified file. |
| firewall `<add>``<delete>``<help>``<set>``<show>` rule name=`<string>` firewall `<dump>` | Switches to the `netsh advfirewall firewall` context to configure firewall rules. - add - Adds a new inbound or outbound firewall rule.<br>- delete - Deletes all matching firewall rules.<br>- dump - Displays a configuration script.<br>- help - Displays a list of commands.<br>- set - Sets new values for properties of an existing rule.<br>- show - Displays a specified firewall rule. |
| help *or* ? | Displays a list of commands and their descriptions in the current context. |
| import `<path\filename>` | Imports firewall policy settings from a specified file into the current policy store. |
| mainmode `<add>``<delete>``<help>``<set>``<show>` rule name=`<string>` mainmode `<dump>` | Switches to the `netsh advfirewall mainmode` context to configure main mode settings. - add - Adds a new mainmode rule.<br>- delete - Deletes all matching mainmode rules.<br>- dump - Displays a configuration script.<br>- help - Displays a list of commands.<br>- set - Sets new values for properties of an existing rule.<br>- show - Displays a specified mainmode rule. |
| monitor delete `mmsa \| qmsa``<source destination \| all>` monitor `<help>` monitor show `<consec>``<currentprofile>``<firewall>``<mainmode>``<mmsa>``<qmsa>` monitor `<dump>` | Switches to the `netsh advfirewall monitor` context to display monitoring information. - delete - Deletes all matching security associations. The source destination is one or more IP addresses. `All` specifies that the operation should apply to all entries.<br>- dump - Displays a configuration script.<br>- help - Displays a list of commands.<br>- show - Shows the runtime Firewall policy settings:  - `consec` displays current consec state information.  - `currentprofile` displays the currently active profiles.  - `firewall` displays current firewall state information.  - `mainmode` displays current mainmode state information.  - `mmsa` displays the main mode SAs.  - `qmsa` displays the quick mode SAs. |
| reset `<export path\filename>` | Resets the Windows Defender Firewall with Advanced Security policies to the default settings. The current active policy can be optionally exported to a specified file.  In a Group Policy object, this command returns all settings to `notconfigured` and deletes all connection security and firewall rules. |
| set allprofiles | currentprofile | domainprofile | privateprofile | publicprofile | `parameter``<value>` | Configures per-profile or global settings for the firewall. - allprofiles - Sets properties in all profiles.<br>- currentprofile - Sets properties in the active profile.<br>- domainprofile - Sets properties in the domain profile.<br>- global - Sets the global properties.<br>- privateprofile - Sets properties in the private profile.<br>- publicprofile - Sets properties in the public profile.<br> The `notconfigured` value is valid only for a Group Policy store.  The available `parameter` and `<value>` are as follows: `state` - Configures the firewall state. - `<on>` - Enables the firewall. When the firewall is on, it actively filters network traffic based on the configured rules.<br>- `<off>` - Disables the firewall. No filtering or protection is applied, and all network traffic is allowed.<br>- `<notconfigured>` - sets the firewall state to its default configuration as per the system policy or administrative template settings.<br>`firewallpolicy` - Configures the default *inbound* and *outbound* behavior. - `<blockinbound>` - Blocks inbound connections that don't match an inbound rule.<br>- `<blockinboundalways>` - Blocks all inbound connections even if the connection matches a rule.<br>- `<allowinbound>` - Allows inbound connections that don't match a rule.<br>- `<allowoutbound>` - Allows outbound connections that don't match a rule.<br>- `<blockoutbound>` - Blocks outbound connections that don't match a rule.<br>- `<notconfigured>` - Returns the value to its unconfigured state.<br>`settings` - Configures the firewall settings. - `localfirewallrules` - Merge local firewall rules with Group Policy rules. Valid when configuring a Group Policy store.<br>- `localconsecrules` - Merge local connection security rules with Group Policy rules. Valid when configuring a Group Policy store.<br>- `inboundusernotification` - Notify user when a program listens for inbound connections.<br>- `remotemanagement` - Allow remote management of Windows Firewall.<br>- `unicastresponsetomulticast` - Control stateful unicast response to multicast.<br>- `<enable>` - Turns on the specified setting.<br>- `<disable>` - Turns off the specified setting.<br>- `<notconfigured>` - Restores the setting to the systems default configuration.<br>`logging` - Configures logging settings. - `allowedconnections` - Determines whether successful inbound and outbound connections are recorded in the logs. `<on>` - Logs successful connections. `<off>` - Doesn't log connections. `<notconfigured>` - Reverts to the system's default behavior for logging successful connections.<br>- `droppedconnections` - Specifies whether connections blocked by the firewall are logged. `<on>` - Logs all blocked connections. `<off>` - Don't log blocked connections. `<notconfigured>` - Reverts to the system's default behavior for logging blocked connections.<br>- `filename` - Sets the name and location for storing the log file. `<string>` - The file path and file name designated for the log file, such as `C:\Logs\firewall.log`. `<notconfigured>` - Uses the default file path and name provided by the system.<br>- `maxfilesize` - Sets the maximum size of the log file in kilobytes (KB). If the file exceeds this size, the oldest entries are overwritten. Acceptable file size is between 1 KB and 32,767 KB. `<notconfigured>` - Adopts the system's default maximum file size. |
| set global [statefulftp | statefulpptp] `<enable>``<disable>``<notconfigured>` | Configures the global settings including advanced IPsec options. The use of DES, MD5, and DHGroup1 isn't recommended. These cryptographic algorithms are provided for backward compatibility only.  The mmsecmethods keyword default sets the policy to dhgroup2-aes128-sha1,dhgroup2-3des-sha1 `statefulftp` - This option controls the firewall's behavior regarding FTP (File Transfer Protocol) traffic. `statefulpptp` - This option manages the handling of PPTP (Point-to-Point Tunneling Protocol) traffic. `<enable>` - Activates stateful inspection for the selected protocol. This ensures that the firewall can dynamically adjust rules to correctly handle corresponding traffic. `<disable>` - Deactivates stateful inspection for the selected protocol. This might lead to issues with correctly handling protocol-specific traffic as the firewall doesn't dynamically adjust its rules. `<notconfigured>` - Resets the setting to the default behavior as determined by the system's policy or configuration. This allows the system to apply its default rules without user-specified changes. |
| set global ipsec `parameter``<value>` | `strongcrlcheck` - Configures the enforcement level of Certificate Revocation List (CRL) checking. `<0>` - Disables CRL checking (default setting). `<1>` - Fails the connection if the certificate is revoked. `<2>` - Fails the connection on any CRL-related error. `<notconfigured>` - Resets the value to the not configured state. `saidletimemin` - Sets the idle time in minutes for a Security Association (SA) before it's considered inactive. Acceptable values range from `5` to `60` minutes. `<notconfigured>` - Defaults to `5` minutes. `defaultexemptions` - Manages default protocols exempted from IPsec protection. The default is to exempt IPv6 neighbordiscovery protocol and DHCP from IPsec. Acceptable values include: `<none>``<neighbordiscovery>``<icmp>``<dhcp>``<notconfigured>``ipsecthroughnat` - Configures the conditions under which IPsec can establish security associations with devices behind a Network Address Translator (NAT). Acceptable values include: `<never>` - Associations aren't permitted (default). `<serverbehindnat>` - Only if the server is behind a NAT. `<serverandclientbehindnat>` - If both the server and client are behind a NAT. `<notconfigured>` - Defaults to `<never>`. `authzcomputergrp` - Specifies computer groups authorized to establish tunnel mode connections. `<none>` - No specific computer group is authorized to establish tunnel mode connections. `<SDDL string>` - Specifies a Security Descriptor Definition Language (SDDL) string that defines the group of computers authorized to establish connections. `<notconfigured>` - Specifies default settings. `authzusergrp` - Specifies user groups authorized to establish tunnel mode connections. `<none>` - No specific user group is authorized to establish tunnel mode connections. `<SDDL string>` - Defines the specific user groups authorized to establish connections. `<notconfigured>` - Specifies default settings. |
| set global mainmode `parameter``<value>` | `<notconfigured>` | `mmkeylifetime` - Sets the duration for which the keys in Main Mode are valid. Key lifetime is defined by time in minutes [&lt;num&gt; min], number of sessions [&lt;num&gt; sess], or both.  The minimum *lifetime* of the keys in minutes range from `1` minute and maximum of `2880` minutes.  The minimum number of *sessions* for which the keys are valid range from `0` sessions to a maximum of `2,147,483,647` sessions. `mmsecmethods` - Configures the list of security proposals for the Main Mode IPsec negotiations, which includes key exchange, encryption, and integrity algorithms. You can use a comma-separated list of proposals in the format `keyexch:enc-integrity`. Each proposal consists of a set of algorithms from each category. - **keyexch**: Specifies the Diffie-Hellman (DH) or Elliptic Curve Diffie-Hellman groups used for the key exchange. Acceptable values are: `<dhgroup1>``<dhgroup2>``<dhgroup14>``<dhgroup24>``<ecdhp256>``<ecdhp384>`<br>- **enc**: Specifies the encryption algorithm used for securing the data. Acceptable values are: `<3des>``<des>``<aes128>``<aes192>``<aes256>`<br>- **integrity**: Specifies the algorithm used to ensure the data integrity. Acceptable values are: `<md5>``<sha1>``<sha256>``<sha384>``mmforcedh` - Enforces the use of DH for key exchanges during IPsec main mode negotiations. `<yes>` - Forces the use of DH for key exchange. `<no>` - Doesn't force the use of DH for key exchange (default setting). |
| show allprofiles | currentprofile | domainprofile | privateprofile | publicprofile | `parameter` | Displays the current profile or global properties for the firewall. - allprofiles - Displays the properties for all profiles.<br>- currentprofile - Displays the properties for the active profile.<br>- domainprofile - Displays the properties in the domain profile.<br>- global - Displays the global properties.<br>- privateprofile - Displays the properties for the private profile.<br>- publicprofile - Displays the properties for the public profile.<br>- store - Displays the current policy store.<br> If a parameter isn't specified for the profiles, all properties are displayed.  The available parameters are as follows: `state`: Displays whether the Windows Defender Firewall with Advanced Security is currently enabled or disabled for each profile. `firewallpolicy`: Shows the default actions for inbound and outbound connections, indicating whether such connections are allowed or blocked by default for each profile. `settings`: Provides detailed properties of the firewall, including configuration settings for each profile. `logging`: Shows the current logging configuration, including log file location, size, and logging options for dropped packets and successful connections. |
| show global `parameter` | Displays the global settings for Windows Defender Firewall with Advanced Security. If no parameter is specified, all properties are displayed.  The available parameters are as follows: `ipsec`: Displays the specific IPsec settings. `statefulftp`: Displays the configuration for Stateful FTP support. `statefulpptp`: Shows the configuration for Stateful PPTP support. `mainmode`: Displays the configuration for Main Mode, a phase in the IPsec negotiation process where both parties authenticate each other and establish a secure channel for further communication. `categories`: Displays the configuration related to Firewall Categories. |

## Remarks

### Consec parameter remarks

# [add](#tab/consecadd)
```
- The rule name should be unique and can't be "all".
- When mode=tunnel, tunnel endpoints must be specified unless the action is "noauthentication". If specific IP addresses are used, they must belong to the same IP version.
  - For dynamic tunnels, tunnel endpoints can be set to "any".
  - Local tunnel endpoints aren't required for Client policies, for example, "any".
  - Remote tunnel endpoints aren't required for Gateway policies, for example, "any". Additionally, the action must be one of the following: requireinrequireout, requireinclearout, or noauthentication.
- requireinclearout isn't valid when mode=Transport.
- At least one authentication must be specified.
- Auth1 and auth2 can be comma-separated lists of options.
- Computerpsk and computerntlm methods can't be specified together for auth1.
- Computercert can't be specified with user credentials for auth2.
- Certsigning options ecdsap256 and ecdsap384 are only supported on Windows Vista SP1 and later.
- Qmsecmethods can be a list of proposals separated by a ",".
- For qmsecmethods, integrity=md5|sha1|sha256|aesgmac128|aesgmac192|aesgmac256|aesgcm128|aesgcm192|aesgcm256 and encryption=3des|des|aes128|aes192|aes256|aesgcm128|aesgcm192|aesgcm256.
- If aesgcm128, aesgcm192, or aesgcm256 is specified, it must be used for both ESP integrity and encryption.
- Aesgmac128, aesgmac192, aesgmac256, aesgcm128, aesgcm192, aesgcm256, sha256 are only supported on Windows Vista SP1 and later.
- Qmpfs=mainmode uses the main mode key exchange setting for PFS.
- The use of DES, MD5, and DHGroup1 isn't recommended. These cryptographic algorithms are provided for backward compatibility only.
- The default value for certmapping and excludecaname is "no".
- The " characters within CA name must be replaced with \'
- For auth1ca and auth2ca, the CA name must be prefixed by "CN=".
- catype can be used to specify the Certification authority type "catype=root/intermediate".
- authnoencap is supported on Windows 7 and later.
- authnoencap means that the computers will only use authentication, and won't use any per packet encapsulation or encryption algorithms to protect subsequent network packets exchanged as part of this connection.
- QMPFS and authnoencap can't be used together on the same rule.
- AuthNoEncap must be accompanied by at least one AH or ESP integrity suite.
- applyauthz can only be specified for tunnel mode rules.
- exemptipsecprotectedconnections can only be specified for tunnel mode rules. By setting this flag to "Yes", ESP traffic is exempted from the tunnel. AH only traffic won't be exempted from the tunnel.
- Valuemin, when specified, for a qmsecmethod should be between 5 to 2880 minutes. Valuekb, when specified, for a qmsecmethod should be between 20480 KB to 2147483647 KB.
- Certhash specifies the thumbprint, or hash of the certificate.
- Followrenewal specifies whether to automatically follow renewal links in certificates. Only applicable for certificate section (requires certhash).
- Certeku specifies the comma separated list of EKU OIDs to match in the certificate.
- Certname specifies the string to match for certificate name (requires certnametype).
- Certnametype specifies the certificate field for the certname to be matched against (requires certname).
- Certcriteriatype specifies whether to take the action with the certificate when selecting the local certificate, validating the peer certificate, or both.
- Within a computercert authentication mapping, multiple certificates can be referenced by separating each entry by using the "|" character.
```

# [delete](#tab/consecdelete)
```
- Deletes a rule identified by name and optionally by profiles, endpoints, ports, protocol, and type.
- If multiple matches are found, all matching rules are deleted.
```

# [set](#tab/consecset)
```
- Sets a new parameter value on an identified rule. The command fails if the rule does not exist. To create a rule, use the "add" command.
- Values after the new keyword are updated in the rule. If there are no values, or keyword new is missing, no changes are made.
- A group of rules can only be enabled or disabled.
- If multiple rules match the criteria, all matching rules will be updated.
- Rule name should be unique and can't be "all".
- Auth1 and auth2 can be comma-separated lists of options.
- Computerpsk and computerntlm methods can't be specified together for auth1.
- Computercert can't be specified with user credentials for auth2.
- Certsigning options ecdsap256 and ecdsap384 are only supported on Windows Vista SP1 and later.
- Qmsecmethods can be a list of proposals separated by a ",".
- For qmsecmethods, integrity=md5|sha1|sha256|aesgmac128|aesgmac192|aesgmac256|aesgcm128|aesgcm192|aesgcm256 and encryption=3des|des|aes128|aes192|aes256|aesgcm128|aesgcm192|aesgcm256.
- If aesgcm128, aesgcm192, or aesgcm256 is specified, it must be used for both ESP integrity and encryption.
- Aesgmac128, aesgmac192, aesgmac256, aesgcm128, aesgcm192, aesgcm256, sha256 are only supported on Windows Vista SP1 and later.
- If qmsemethods are set to default, qmpfs will be set to default as well.
- Qmpfs=mainmode uses the main mode key exchange setting for PFS.
- The use of DES, MD5 and DHGroup1 is not recommended. These cryptographic algorithms are provided for backward compatibility only.
- The " characters within CA name must be replaced with \'
- For auth1ca and auth2ca, the CA name must be prefixed by "CN=".
- catype can be used to specify the Certification authority type "catype=root/intermediate".
- authnoencap is supported on Windows 7 and later.
- authnoencap means that the computers will only use authentication, and will not use any per packet encapsulation or encryption algorithms to protect subsequent network packets exchanged as part of this connection.
- QMPFS and authnoencap can't be used together on the same rule.
- AuthNoEncap must be accompanied by at least one AH or ESP integrity suite.
- When mode=tunnel action must be requireinrequireout, requireinclearout or noauthentication.
- requireinclearout is not valid when mode=Transport.
- applyauthz can only be specified for tunnel mode rules.
- exemptipsecprotectedconnections can only be specified for tunnel mode rules. By setting this flag to "Yes", ESP traffic will be exempted from the tunnel. AH only traffic will NOT be exempted from the tunnel.
- Port1, Port2 and Protocol can only be specified when mode=transport.
- Valuemin, when specified, for a qmsecmethod should be between 5 to 2880 minutes. Valuekb, when specified, for a qmsecmethod should be between 20480 KB to 2147483647 KB.
- Certhash specifies the thumbprint, or hash of the certificate.
- Followrenewal specifies whether to automatically follow renewal links in certificates. Only applicable for certificate section (requires certhash).
- Certeku specifies the comma separated list of EKU OIDs to match in the certificate.
- Certname specifies the string to match for certificate name (requires certnametype).
- Certnametype specifies the certificate field for the certname to be matched against (requires certname).
- Certcriteriatype specifies whether to take the action with the certificate when selecting the local certificate, validating the peer certificate, or both.
```

---

### Firewall parameter remarks

# [add](#tab/firewalladd)
```
- Add a new inbound or outbound rule to the firewall policy.
- Rule name should be unique and can't be "all".
- If a remote computer or user group is specified, security must be: authenticate, authenc, authdynenc, or authnoencap.
- Setting security to authdynenc allows systems to dynamically negotiate the use of encryption for traffic that matches a given Windows Defender Firewall rule. Encryption is negotiated based on existing connection security rule properties. This option enables the ability of a machine to accept the first TCP or UDP packet of an inbound IPsec connection as long as it's secured, but not encrypted, using IPsec. Once the first packet is processed, the server renegotiates the connection and upgrade it so that all subsequent communications are fully encrypted.
- If action=bypass, the remote computer group must be specified when dir=in.
- If service=any, the rule applies only to services.
- ICMP type or code can be "any".
- Edge can only be specified for inbound rules.
- AuthEnc and authnoencap can't be used together.
- Authdynenc is valid only when dir=in.
- When authnoencap is set, the security=authenticate option becomes an optional parameter.
```

# [delete](#tab/firewalldelete)
```
- Deletes a rule identified by name and optionally by endpoints, ports, protocol, and type.
- If multiple matches are found, all matching rules are deleted.
- If name=all is specified, all rules are deleted from the specified type and profile.
```

# [set](#tab/firewallset)
```
- Sets a new parameter value on an identified rule. The command fails if the rule does not exist. To create a rule, use the add command.
- Values after the new keyword are updated in the rule. If there are no values, or the new keyword is missing, no changes are made.
- A group of rules can only be enabled or disabled.
- If multiple rules match the criteria, all matching rules will be updated.
- Rule name should be unique and cannot be "all."
- If a remote computer or user group is specified, security must be: authenticate, authenc, or authdynenc.
- Setting security to authdynenc allows systems to dynamically negotiate the use of encryption for traffic that matches a given Windows Defender Firewall rule. Encryption is negotiated based on existing connection security rule properties. This option enables the ability of a machine to accept the first TCP or UDP packet of an inbound IPsec connection as long as it's secured, but not encrypted, using IPsec. Once the first packet is processed, the server will renegotiate the connection and upgrade it so that all subsequent communications are fully encrypted.
- authdynenc is valid only when dir=in.
- If action=bypass, the remote computer group must be specified when dir=in.
- If service=any, the rule applies only to services.
- ICMP type or code can be "any."
- Edge can only be specified for inbound rules.
```

---

### Mainmode parameter remarks

# [add](#tab/mainmodeadd)
```
- Add a new mainmode rule to the firewall policy.
- Rule name should be unique and can't be "all".
- Computerpsk and computerntlm methods can't be specified together for auth1.
- The use of DES, MD5, and DHGroup1 isn't recommended. These cryptographic algorithms are provided for backward compatibility only.
- The minimum main mode keylifetime is mmkeylifetime=1min. The maximum main mode mmkeylifetime=2880min. The minimum number of sessions=0 sessions. The maximum=2,147,483,647 sessions.
- The mmsecmethods keyword default sets the policy to: dhgroup2-aes128-sha1,dhgroup2-3des-sha1
- Certhash specifies the thumbprint, or hash of the certificate.
- Followrenewal specifies whether to automatically follow renewal links in certificates. Only applicable for certificate section (requires certhash).
- Certeku specifies the comma separated list of EKU OIDs to match in the certificate.
- Certname specifies the string to match for certificate name (requires certnametype).
- Certnametype specifies the certificate field for the certname to be matched against (requires certname).
- Certcriteriatype specifies whether to take the action with the certificate when selecting the local certificate, validating the peer certificate, or both.
```

# [delete](#tab/mainmodedelete)
```
- Deletes an existing main mode setting that matches the name specified. Optionally, profile can be specified. Command fails if setting with the specified name doesn't exist.
- If name=all is specified, all rules are deleted from the specified type and profile. If profile isn't specified, the delete applies to all profiles.
```

# [set](#tab/mainmodeset)
```
- Sets a new parameter value on an identified rule. The command fails if the rule doesn't exist. To create a rule, use the add command.
- Values after the new keyword are updated in the rule. If there are no values, or keyword new is missing, no changes are made.
- If multiple rules match the criteria, all matching rules are updated.- Rule name should be unique and can't be "all".
- Auth1 can be comma-separated lists of options. Computerpsk and computerntlm methods can't be specified together for auth1.
- The use of DES, MD5, and DHGroup1 isn't recommended. These cryptographic algorithms are provided for backward compatibility only.
- The minimum main mode keylifetime is mmkeylifetime=1min. The maximum main mode mmkeylifetime=2880min. The minimum number of sessions=0 sessions. The maximum=2,147,483,647 sessions.
- The mmsecmethods keyword default sets the policy to: dhgroup2-aes128-sha1,dhgroup2-3des-sha1.
- Certhash specifies the thumbprint, or hash of the certificate.
- Followrenewal specifies whether to automatically follow renewal links in certificates. Only applicable for certificate section (requires certhash).
- Certeku specifies the comma separated list of EKU OIDs to match in the certificate.
- Certname specifies the string to match for certificate name (requires certnametype).
- Certnametype specifies the certificate field for the certname to be matched against (requires certname).
- Certcriteriatype specifies whether to take the action with the certificate when selecting the local certificate, validating the peer certificate, or both.
```

---

### Monitor parameter remarks

# [delete](#tab/monitordelete)
```
- This command deletes the matching security association as specified by the source destination pair.
- Source and destination are each a single IPv4 or IPv6 address.
```

# [show consec  show mainmode](#tab/monitorshowconsec)
```
- Displays the Connection Security configuration for all available network profiles.
- The [profile=] command enables the administrator to filter the output to specific profiles on the system or to only return results from Active or Inactive profiles.
- The [rule] command allows the administrator to scope the rule output to certain rule names and status to scope the output.
- The Verbose command adds support for displaying detailed security and advanced rule 'source name' information.
```

# [show firewall](#tab/monitorshowfirewall)
```
- Displays the Windows Defender Firewall with Advanced Security properties for all available network profiles.
- The profile= argument enables the administrator to filter the output to specific profiles on the system.
- The Verbose argument adds support for displaying detailed security and advanced rule 'source name' information.
```

# [show mmsa  show qmsa](#tab/monitorshowmmsa)
```
- This command shows the security association, or as filtered by the source destination pair.
- Source and destination are each a single IPv4 or IPv6 address.
```

---

## Examples

Note

For detailed usage instructions and additional examples for all parameters, use the `help` or `?` commands. These commands provide syntax details and guidance for specific operations.

**consec**

To add a connection security rule requiring authentication, run the following command:

```cmd
netsh advfirewall consec add rule name="RequireAuth" endpoint1=any endpoint2=any action=requireinrequestout
```

To add a new connection security rule that uses Kerberos for authentication, run the following command:

```cmd
netsh advfirewall consec add rule name="KerberosAuthRule" endpoint1=any endpoint2=any action=requireinrequireout auth1=computerkerb
```

To delete a connection security rule by its name, run the following command:

```cmd
netsh advfirewall consec delete rule name="RuleName"
```

**dump**

To save the current advanced firewall configuration to a text file, run the following command:

```cmd
netsh advfirewall dump > "C:\path\to\firewall_dump.txt"
```

To display the current firewall configuration in CMD, run the following command:

```cmd
netsh advfirewall dump
```

To include the advanced firewall state in the main dump for diagnostics, run the following command:

```cmd
netsh advfirewall dump | findstr "State"
```

**export**

To export the current firewall policy for backup, run the following command:

```cmd
netsh advfirewall export "C:\folder\firewall_backup.wfw"
```

**firewall**

To add a rule allowing inbound traffic on port 8080, run the following command:

```cmd
netsh advfirewall firewall add rule name="Allow8080" protocol=TCP dir=in localport=8080 action=allow
```

To block outgoing traffic to a specific IP, run the following command:

```cmd
netsh advfirewall firewall add rule name="BlockOutIP" protocol=TCP dir=out remoteip=192.168.1.100 action=block
```

To remove a specific firewall rule by name, run the following command:

```cmd
netsh advfirewall firewall delete rule name="MyRule"
```

**help**

To get help for all firewall commands, run the following command:

```cmd
netsh advfirewall firewall ?
```

To find out syntax details for adding a firewall rule, run the following command:

```cmd
netsh advfirewall firewall add rule ?
```

**import**

To import a saved firewall configuration from a file, run the following command:

```cmd
netsh advfirewall import "C:\folder\firewall_config.wfw"
```

**mainmode**

To add a mainmode rule for security negotiation, run the following command:

```cmd
netsh advfirewall mainmode add rule name="MyMainmodeRule" auth1=computerkerb
```

To show detailed settings of mainmode rules, run the following command:

```cmd
netsh advfirewall mainmode show rule name=all
```

To remove a mainmode rule by specifying its name, run the following command:

```cmd
netsh advfirewall mainmode delete rule name="MyMainmodeRule"
```

**monitor**

To monitor active connection security associations, run the following command:

```cmd
netsh advfirewall monitor show mmsa
```

To display statistics and active connections, run the following command:

```cmd
netsh advfirewall monitor show firewall
```

**reset**

To reset the firewall settings without additional confirmation, run the following command:

```cmd
netsh advfirewall reset
```

**set**

To disable logging of dropped packets, run the following command:

```cmd
netsh advfirewall set currentprofile logging droppedconnections disable
```

To enable notifications for blocked applications, run the following command:

```cmd
netsh advfirewall set currentprofile settings allowunicastresponsetomulticast enable
```

**show**

To display all active firewall rules, run the following command:

```cmd
netsh advfirewall firewall show rule name=all
```

To show detailed information on a specific rule by name, run the following command:

```cmd
netsh advfirewall firewall show rule name="MyRuleName" verbose
```