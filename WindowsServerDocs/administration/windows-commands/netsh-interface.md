---
layout: Conceptual
title: netsh interface | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-interface
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh interface command suite configures, manages, routes, and troubleshoots IPv4 and IPv6 network interfaces and protocol tunneling in Windows.
ms.topic: reference
ms.author: alalve
author: Xelu86
ms.date: 2025-10-24T00:00:00.0000000Z
locale: en-us
document_id: ba23d97a-06d5-38dc-0370-ae39d2a32fa5
document_version_independent_id: ba23d97a-06d5-38dc-0370-ae39d2a32fa5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-interface.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-interface
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-interface.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/a101c485-5d78-47d4-acb8-5cecd163b5b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43a4fac3-c2aa-4267-87e4-add0300397fa
platformId: 7209a9b6-0899-17d2-05a0-5dacc611142f
---

# netsh interface | Microsoft Learn

The `netsh interface` command provides a comprehensive set of tools for configuring and managing network interfaces in Windows. Using this command, you can enable or disable network adapters, assign static or dynamic IP addresses, configure DNS and WINS servers, rename interfaces, and monitor interface statistics. The interface context is useful for troubleshooting connectivity issues, optimizing network settings, and automating network configuration tasks across physical and virtual adapters.

Additionally, `netsh interface` supports advanced features such as configuring port proxies, managing IPv4 and IPv6 settings, and controlling tunneling protocols like 6to4, ISATAP, and Teredo. You can also use it to adjust TCP and UDP parameters, set routing policies, and manage global network behaviors. These capabilities make `netsh interface` a powerful tool for both admins and power users who need granular control over network configuration and diagnostics.

## Syntax

```
netsh interface [6to4 | clat | dump | fl48 | fl68 | help | httpstunnel | ipv4 | ipv6 | isatap | portproxy | set | show | tcp | teredo | udp | ?]
```

```
netsh interface 6to4 dump
netsh interface 6to4 set interface [name=]<string> [routing=](enabled|disabled|default)
netsh interface 6to4 set relay [name=]<string>|default [state=]enabled|disabled|automatic|default [interval=]<integer>
netsh interface 6to4 set routing [routing=]enabled|disabled|automatic|default [sitelocals=]enabled|disabled|default
netsh interface 6to4 set state [state=]enabled|disabled|default [undoonstop=]enabled|disabled|default
netsh interface 6to4 show <interface> <relay> <routing> <state>

```

```
netsh interface clat dump
netsh interface clat set global [permit=]disabled|enabled [pref64fromdns=]disabled|enabled [pref64fromra=]disabled|enabled
netsh interface clat show global
```

```
netsh interface fl48 dump
netsh interface fl48 show virtualinterfaces
```

```
netsh interface fl68 dump
netsh interface fl68 show virtualinterfaces
```

```
netsh interface httpstunnel add interface [type=]server|client [url=]<string> [state=]enabled|disabled|default
                                          [authmode=]none|certificates
netsh interface httpstunnel delete interface
netsh interface httpstunnel dump
netsh interface httpstunnel reset
netsh interface httpstunnel set interface [url=]<string> [state=]enabled|disabled|default [authmode=]none|certificates
netsh interface httpstunnel show interfaces [store=]active|persistent
netsh interface httpstunnel show statistics [interface=]<string>
```

```
netsh interface ipv4 add address [name=]<string> [address=]<IPv4 address>[/<integer> [mask=]<IPv4 mask>]
                                 [type=]unicast|anycast [gateway=]<IPv4 address> [gwmetric=]<integer>
                                 [validlifetime=]<integer>|infinite [preferredlifetime=]<integer>|infinite
                                 [subinterface=]<string> [store=]active|persistent [skipassource=]true|false
netsh interface ipv4 add dnsservers [name=]<string> [address=]<IPv4 address> [index=]<integer> [validate=]yes|no
netsh interface ipv4 add excludedportrange [protocol=]tcp|udp [startport=]<integer> [numberofports=]<integer>
                                           [store=]active|persistent
netsh interface ipv4 add neighbors [interface=]<string> [address=]<IPv4 address> [neighbor=]<string>
                                   [subinterface=]<string> [store=]active|persistent
netsh interface ipv4 add route [prefix=]<IPv4 address>/<integer> [interface=]<string> [nexthop=]<IPv4 address>
                               [siteprefixlength=]<integer> [metric=]<integer> [publish=]no|age|yes
                               [validlifetime=]<integer>|infinite [preferredlifetime=]<integer>|infinite
                               [store=]active|persistent
netsh interface ipv4 add winsservers [name=]<string> [address=]<IP address> [index=]<integer>
netsh interface ipv4 delete address [name=]<string> [address=]<IPv4 address> [gateway=]<IPv4 address>|all
                                    [store=]active|persistent
netsh interface ipv4 delete arpcache [name=]<string> [address=]<IPv4 address> [subinterface=]<string>
                                     [store=]active|persistent
netsh interface ipv4 delete destinationcache [interface=]<string> [address=]<IP address>
netsh interface ipv4 delete dnsservers [name=]<string> [address=]<IPv4 address> [validate=]yes|no
netsh interface ipv4 delete excludedportrange [protocol=]tcp|udp [startport=]<integer> [numberofports=]<integer>
                                              [store=]active|persistent
netsh interface ipv4 delete neighbors [name=]<string> [address=]<IPv4 address> [subinterface=]<string>
                                      [store=]active|persistent
netsh interface ipv4 delete route [prefix=]<IPv4 address>/<integer> [interface=]<string> [nexthop=]<IPv4 address>
                                  [store=]active|persistent
netsh interface ipv4 delete winsservers [name=]<string> [address=]<IP address>|all
netsh interface ipv4 dump
netsh interface ipv4 install
netsh interface ipv4 reset
netsh interface ipv4 set address [name=]<string> [source=]dhcp|static [address=]<IPv4 address>[/<integer>]
                                 [mask=]<IPv4 mask> [gateway=]<IPv4 address>|none [gwmetric=]<integer>
                                 [type=]unicast|anycast [subinterface=]<string> [store=]active|persistent
netsh interface ipv4 set compartment [compartment=]<integer> [defaultcurhoplimit=]<integer>
                                     [store=]active|persistent
netsh interface ipv4 set dnsservers [name=]<string> [source=]dhcp|static [address=]<IP address>|none
                                    [register=]none|primary|both [validate=]yes|no
netsh interface ipv4 set dynamicportrange [protocol=]tcp|udp [startport=]<integer> [numberofports=]<integer>
                                          [store=]active|persistent
netsh interface ipv4 set global [defaultcurhoplimit=]<integer> [neighborcachelimit=]<integer>
                                [routecachelimit=]<integer> [reassemblylimit=]<integer>
                                [icmpredirects=]enabled|disabled [sourceroutingbehavior=]drop|forward|dontforward
                                [taskoffload=]enabled|disabled [dhcpmediasense=]enabled|disabled
                                [mediasenseeventlog=]enabled|disabled [mldlevel=]none|sendonly|all
                                [mldversion=]version1|version2|version3 [multicastforwarding=]enabled|disabled
                                [groupforwardedfragments=]enabled|disabled [randomizeidentifiers=]enabled|disabled
                                [store=]active|persistent [addressmaskreply=]enabled|disabled [minmtu=]<integer>
                                [flowlabel=]enabled|disabled [loopbacklargemtu=]enabled|disabled
                                [loopbackworkercount=]enabled|disabled [loopbackexecutionmode=]inline|adaptive|worker
                                [sourcebasedecmp=]enabled|disabled [reassemblyoutoforderlimit=]<integer>
                                [slaacprivacylevel=]<integer> [slaacmaxdadattempts=]<integer>
                                [routepolicies=]enabled|disabled [recursivereassembly=]enabled|disabled
                                [icmpjumbograms=]enabled|disabled
netsh interface ipv4 set interface [interface=]<string> [[forwarding=]enabled|disabled]
                                   [advertise=]enabled|disabled [mtu=]<integer> [siteprefixlength=]<integer>
                                   [nud=]enabled|disabled [basereachabletime=]<integer>
                                   [retransmittime=]<integer> [dadtransmits=]<integer>
                                   [routerdiscovery=]enabled|disabled|dhcp [managedaddress=]enabled|disabled
                                   [otherstateful=]enabled|disabled [weakhostsend=]enabled|disabled
                                   [weakhostreceive=]enabled|disabled [ignoredefaultroutes=]enabled|disabled
                                   [advertisedrouterlifetime=]<0-65535> [advertisedefaultroute=]enabled|disabled
                                   [currenthoplimit=]<0-255> [store=]active|persistent
                                   [forcearpndwolpattern=]enabled|disabled [enabledirectedmacwolpattern=]enabled|disabled
                                   [ecncapability=]ecndisabled|ect1|ect0|application [rabaseddnsconfig=]enabled|disabled
                                   [dhcpstaticipcoexistence=]enabled|disabled
netsh interface ipv4 set neighbors [interface=]<string> [address=]<IPv4 address> [neighbor=]<string> [store=]active|persistent
netsh interface ipv4 set route [prefix=]<IPv4 address>/<integer> [interface=]<string> [nexthop=]<IPv4 address>
                               [siteprefixlength=]<integer> [metric=]<integer> [publish=]no|age|yes
                               [validlifetime=]<integer>|infinite [preferredlifetime=]<integer>|infinite
                               [store=]active|persistent
netsh interface ipv4 set subinterface [interface=]<string> [mtu=]<integer> [subinterface=]<string> [store=]active|persistent
netsh interface ipv4 set winsservers [name=]<string> [source=]dhcp|static [address=]<IP address>|none
netsh interface ipv4 show addresses [name=]<string>
netsh interface ipv4 show compartments [compartment=]<integer> [level=]normal|verbose [store=]active|persistent
netsh interface ipv4 show config [name=]<string>
netsh interface ipv4 show destinationcache [interface=]<string> [address=]<IP address> [level=]normal|verbose
netsh interface ipv4 show dnsservers [name=]string
netsh interface ipv4 show dynamicportrange [protocol=]tcp|udp [store=]active|persistent
netsh interface ipv4 show excludedportrange [protocol=]tcp|udp [store=]active|persistent
netsh interface ipv4 show global [store=]active|persistent
netsh interface ipv4 show icmpstats [rr=]<integer>
netsh interface ipv4 show interfaces [interface=]<string> [rr=]<integer> [level=]normal|verbose [store=]active|persistent
netsh interface ipv4 show ipaddresses [interface=]<string> [level=]normal|verbose [store=]active|persistent
netsh interface ipv4 show ipnettomedia [rr=]<integer>
netsh interface ipv4 show ipstats [rr=]<integer>
netsh interface ipv4 show joins [interface=]<string> [level=]normal|verbose
netsh interface ipv4 show neighbors [interface=]<string> [address=]<IP address> [subinterface=]<string>
                                    [level=]normal|verbose [store=]active|persistent
netsh interface ipv4 show offload [name=]<string>
netsh interface ipv4 show route [level=]normal|verbose [store=]active|persistent
netsh interface ipv4 show subinterfaces [interface=]<string> [subinterface=]<string> [level=]normal|verbose
                                        [store=]active|persistent
netsh interface ipv4 show tcpconnections [localaddress=]<IPv4 address> [localport=]<integer> [remoteaddress=]<IPv4 address>
                                         [remoteport=]<integer> [rr=]<integer>
netsh interface ipv4 show tcpstats [rr=]<integer>
netsh interface ipv4 show udpconnections [localaddress=]<IPv4 address> [localport=]<integer> [rr=]<integer>
netsh interface ipv4 show udpstats [rr=]<integer>
netsh interface ipv4 show winsservers [name=]string
netsh interface ipv4 uninstall
```

```
netsh interface ipv6 6to4 dump
netsh interface ipv6 6to4 set interface [name=]<string> [routing=]enabled|disabled|default
netsh interface ipv6 6to4 set relay [name=]<string>|default [state=]enabled|disabled|automatic|default [interval=]<integer>
netsh interface ipv6 6to4 set routing [routing=]enabled|disabled|automatic|default [sitelocals=]enabled|disabled|default
netsh interface ipv6 6to4 set state [state=]enabled|disabled|default [undoonstop=]enabled|disabled|default
netsh interface ipv6 6to4 show <interface> <relay> <routing> <state>
netsh interface ipv6 add address [interface=]<string> [address=]<IPv6 address>[/<integer>] [type=]unicast|anycast
                                 [validlifetime=]<integer>|infinite [preferredlifetime=]<integer>|infinite
                                 [store=]active|persistent [skipassource=]true|false
netsh interface ipv6 add dnsservers [name=]<string> [address=]<IPv6 address> [index=]<integer> [validate=]yes|no
netsh interface ipv6 add excludedportrange [protocol=]tcp|udp [startport=]<integer> [numberofports=]<integer>
                                           [store=]active|persistent
netsh interface ipv6 add neighbors [interface=]<string> [address=]<IPv6 address> [neighbor=]<string> [subinterface=]<string>
                                   [store=]active|persistent
netsh interface ipv6 add potentialrouter [interface=]<string> [address=]<IPv6 address>
netsh interface ipv6 add prefixpolicy [prefix=]<IPv6 address>/<integer> [precedence=]<integer> [label=]<integer>
                                      [store=]active|persistent
netsh interface ipv6 add route [prefix=]<IPv6 address>/<integer> [interface=]<string> [nexthop=]<IPv6 address>
                               [siteprefixlength=]<integer> [metric=]<integer> [publish=]no|age|yes
                               [validlifetime=]<integer>|infinite [preferredlifetime=]<integer>|infinite
                               [store=]active|persistent
netsh interface ipv6 add v6v4tunnel [interface=]<string> [localaddress=]<IPv4 address> [remoteaddress=]<IPv4 address>
netsh interface ipv6 delete address [interface=]<string> [address=]<IPv6 address> [store=]active|persistent
netsh interface ipv6 delete destinationcache [interface=]<string> [address=]<IP address>
netsh interface ipv6 delete dnsservers [name=]<string> [address=]<IPv6 address>|all [validate=]yes|no
netsh interface ipv6 delete excludedportrange [protocol=]tcp|udp [startport=]<integer> [numberofports=]<integer>
                                              [store=]active|persistent
netsh interface ipv6 delete interface [interface=]<string>
netsh interface ipv6 delete neighbors [interface=]<string> [address=]<IPv6 address> [subinterface=]<string>
                                      [store=]active|persistent
netsh interface ipv6 delete potentialrouter [interface=]<string> [address=]<IPv6 address>
netsh interface ipv6 delete prefixpolicy [prefix=]<IPv6 address>/<integer> [store=]active|persistent
netsh interface ipv6 delete route [prefix=]<IPv6 address>/<integer> [interface=]<string> [nexthop=]<IPv6 address>
                                  [store=]active|persistent
netsh interface ipv6 dump
netsh interface ipv6 isatap dump
netsh interface ipv6 isatap set router [name=]<string>|default [state=]enabled|disabled|default [interval=]<integer>
netsh interface ipv6 isatap set state [state=]enabled|disabled|default
netsh interface ipv6 isatap show <router> <state>
netsh interface ipv6 reset
netsh interface ipv6 set address [interface=]<string> [address=]<IPv6 address> [type=]unicast|anycast
                                 [validlifetime=]<integer>|infinite [preferredlifetime=]<integer>|infinite
                                 [store=]active|persistent
netsh interface ipv6 set compartment [compartment=]<integer> [defaultcurhoplimit=]<integer> [store=]active|persistent
netsh interface ipv6 set dnsservers [name=]<string> [source=]dhcp|static [address=]<IP address>|none
                                    [register=]none|primary|both [validate=]yes|no
netsh interface ipv6 set dynamicportrange [protocol=]tcp|udp [startport=]<integer> [numberofports=]<integer>
                                          [store=]active|persistent
netsh interface ipv6 set global [defaultcurhoplimit=]<integer> [neighborcachelimit=]<integer>
                                [routecachelimit=]<integer> [reassemblylimit=]<integer>
                                [icmpredirects=]enabled|disabled [sourceroutingbehavior=]drop|forward|dontforward
                                [taskoffload=]enabled|disabled [dhcpmediasense=]enabled|disabled
                                [mediasenseeventlog=]enabled|disabled [mldlevel=]none|sendonly|all
                                [mldversion=]version1|version2|version3 [multicastforwarding=]enabled|disabled
                                [groupforwardedfragments=]enabled|disabled [randomizeidentifiers=]enabled|disabled
                                [store=]active|persistent [addressmaskreply=]enabled|disabled [minmtu=]<integer>
                                [flowlabel=]enabled|disabled [loopbacklargemtu=]enabled|disabled
                                [loopbackworkercount=]enabled|disabled [loopbackexecutionmode=]inline|adaptive|worker
                                [sourcebasedecmp=]enabled|disabled [reassemblyoutoforderlimit=]<integer>
                                [slaacprivacylevel=]<integer> [slaacmaxdadattempts=]<integer>
                                [routepolicies=]enabled|disabled [recursivereassembly=]enabled|disabled
                                [icmpjumbograms=]enabled|disabled
netsh interface ipv6 set interface [interface=]<string> [[forwarding=]enabled|disabled]
                                   [advertise=]enabled|disabled [mtu=]<integer> [siteprefixlength=]<integer>
                                   [nud=]enabled|disabled [basereachabletime=]<integer>
                                   [retransmittime=]<integer> [dadtransmits=]<integer>
                                   [routerdiscovery=]enabled|disabled|dhcp [managedaddress=]enabled|disabled
                                   [otherstateful=]enabled|disabled [weakhostsend=]enabled|disabled
                                   [weakhostreceive=]enabled|disabled [ignoredefaultroutes=]enabled|disabled
                                   [advertisedrouterlifetime=]<0-65535> [advertisedefaultroute=]enabled|disabled
                                   [currenthoplimit=]<0-255> [store=]active|persistent
                                   [forcearpndwolpattern=]enabled|disabled [enabledirectedmacwolpattern=]enabled|disabled
                                   [ecncapability=]ecndisabled|ect1|ect0|application [rabaseddnsconfig=]enabled|disabled
                                   [dhcpstaticipcoexistence=]enabled|disabled
netsh interface ipv6 set neighbors [interface=]<string> [address=]<IPv6 address> [neighbor=]<string> [store=]active|persistent
netsh interface ipv6 set prefixpolicy [prefix=]<IPv6 address>/<integer> [precedence=]<integer> [label=]<integer>
                                      [store=]active|persistent
netsh interface ipv6 set privacy [prefix=]<IPv6 address>/<integer> [precedence=]<integer> [label=]<integer>
                                 [store=]active|persistent
netsh interface ipv6 set route [prefix=]<IPv6 address>/<integer> [interface=]<string> [nexthop=]<IPv6 address>
                               [siteprefixlength=]<integer> [metric=]<integer> [publish=]no|age|yes
                               [validlifetime=]<integer>|infinite [preferredlifetime=]<integer>|infinite
                               [store=]active|persistent
netsh interface ipv6 set slaacsecretkey [key=]<string>
netsh interface ipv6 set subinterface [interface=]<string> [mtu=]<integer> [subinterface=]<string> [store=]active|persistent
netsh interface ipv6 set teredo [type]=disabled|client|enterpriseclient|natawareclient|server|default
                                [servername=]<hostname>|<IPv4 address>|default [refreshinterval=]<integer>|default
                                [clientport=]<integer>|default [servervirtualip=]<IPv4 address>|default
netsh interface ipv6 show addresses [interface=]<string> [level=]normal|verbose [store=]active|persistent
netsh interface ipv6 show compartments [compartment=]<integer> [level=]normal|verbose [store=]active|persistent
netsh interface ipv6 show destinationcache [interface=]<string> [address=]<IP address> [level=]normal|verbose
netsh interface ipv6 show dnsservers [name=]string
netsh interface ipv6 show dynamicportrange [protocol=]tcp|udp [store=]active|persistent
netsh interface ipv6 show excludedportrange [protocol=]tcp|udp [store=]active|persistent
netsh interface ipv6 show global [store=]active|persistent
netsh interface ipv6 show interfaces [interface=]<string> [rr=]<integer> [level=]normal|verbose [store=]active|persistent
netsh interface ipv6 show ipstats [rr=]<integer>
netsh interface ipv6 show joins [interface=]<string> [level=]normal|verbose
netsh interface ipv6 show neighbors [interface=]<string> [address=]<IP address> [subinterface=]<string>
                                    [level=]normal|verbose [store=]active|persistent
netsh interface ipv6 show offload [name=]<string>
netsh interface ipv6 show potentialrouters [interface=]<string>
netsh interface ipv6 show prefixpolicies [store=]active|persistent
netsh interface ipv6 show privacy [store=]active|persistent
netsh interface ipv6 show route [level=]normal|verbose [store=]active|persistent
netsh interface ipv6 show siteprefixes
netsh interface ipv6 show slaacsecretkey [store=]active|persistent
netsh interface ipv6 show subinterfaces [interface=]<string> [subinterface=]<string> [level=]normal|verbose
                                        [store=]active|persistent
netsh interface ipv6 show tcpstats [rr=]<integer>
netsh interface ipv6 show teredo
netsh interface ipv6 show tfofallback
netsh interface ipv6 show udpstats [rr=]<integer>
```

```
netsh interface isatap dump
netsh interface isatap set router [name=]<string>|default [state=]enabled|disabled|default [interval=]<integer>
netsh interface isatap set state [state=]enabled|disabled|default
netsh interface isatap show <router> <state>
```

```
netsh interface portproxy add v4tov4 [listenport=]<integer>|<servicename> [connectaddress=]<IPv4 address>|<hostname>
                                     [connectport=]<integer>|<servicename> [listenaddress=]<IPv4 address>|<hostname>
                                     [protocol=]tcp
netsh interface portproxy add v4tov6 [listenport=]<integer>|<servicename> [connectaddress=]<IPv6 address>|<hostname>
                                     [connectport=]<integer>|<servicename> [listenaddress=]<IPv4 address>|<hostname>
                                     [protocol=]tcp
netsh interface portproxy add v6tov4 [listenport=]<integer>|<servicename> [connectaddress=]<IPv4 address>|<hostname>
                                     [connectport=]<integer>|<servicename> [listenaddress=]<IPv6 address>|<hostname>
                                     [protocol=]tcp
netsh interface portproxy add v6tov6 [listenport=]<integer>|<servicename> [connectaddress=]<IPv6 address>|<hostname>
                                     [connectport=]<integer>|<servicename> [listenaddress=]<IPv6 address>|<hostname>
                                     [protocol=]tcp
netsh interface portproxy delete v4tov4 [listenport=]<integer>|<servicename> [listenaddress=]<IPv4 address>|<hostname>
                                         [protocol=]tcp
netsh interface portproxy delete v4tov6 [listenport=]<integer>|<servicename> [listenaddress=]<IPv4 address>|<hostname>
                                         [protocol=]tcp
netsh interface portproxy delete v6tov4 [listenport=]<integer>|<servicename> [listenaddress=]<IPv6 address>|<hostname>
                                         [protocol=]tcp
netsh interface portproxy delete v6tov6 [listenport=]<integer>|<servicename> [listenaddress=]<IPv6 address>|<hostname>
                                         [protocol=]tcp
netsh interface portproxy dump
netsh interface portproxy reset
netsh interface portproxy set v4tov4 [listenport=]<integer>|<servicename> [connectaddress=]<IPv4 address>|<hostname>
                                     [connectport=]<integer>|<servicename> [listenaddress=]<IPv4 address>|<hostname>
                                     [protocol=]tcp
netsh interface portproxy set v4tov6 [listenport=]<integer>|<servicename> [connectaddress=]<IPv6 address>|<hostname>
                                     [connectport=]<integer>|<servicename> [listenaddress=]<IPv4 address>|<hostname>
                                     [protocol=]tcp
netsh interface portproxy set v6tov4 [listenport=]<integer>|<servicename> [connectaddress=]<IPv4 address>|<hostname>
                                     [connectport=]<integer>|<servicename> [listenaddress=]<IPv6 address>|<hostname>
                                     [protocol=]tcp
netsh interface portproxy set v6tov6 [listenport=]<integer>|<servicename> [connectaddress=]<IPv6 address>|<hostname>
                                     [connectport=]<integer>|<servicename> [listenaddress=]<IPv6 address>|<hostname>
                                     [protocol=]tcp
netsh interface portproxy show all
netsh interface portproxy show <v4tov4> <v4tov6> <v6tov4> <v6tov6>
```

```
netsh interface set interface [name=]IfName [admin=]ENABLED|DISABLED [connect=]CONNECTED|DISCONNECTED [newname=]NewName
```

```
netsh interface show interface [name=]string
```

```
netsh interface tcp add supplementalport [template=]internet|datacenter|automatic|custom|compat [localport=]*|<integer>
                                         [remoteport=]*|<integer>
netsh interface tcp add supplementalsubnet [template=]internet|datacenter|automatic|custom|compat [family=]ipv4|ipv6
                                           [address=]<IPv4 or IPv6 address>/<prefix length>
netsh interface tcp delete supplementalport [localport=]*|<number> [remoteport=]*|<number>
netsh interface tcp delete supplementalsubnet [family=]ipv4|ipv6 [address=]<IPv4 or IPv6 address>/<prefix length>
netsh interface tcp dump
netsh interface tcp reload
netsh interface tcp rundown
netsh interface tcp set global [rss=]disabled|enabled|default
                               [autotuninglevel=]disabled|highlyrestricted|restricted|normal|experimental
                               [ecncapability=]disabled|enabled|default [timestamps=]disabled|enabled|default
                               [initialrto=]<300-3000> [rsc=]disabled|enabled|default
                               [nonsackrttresiliency=]disabled|enabled|default [maxsynretransmissions=]<2-8>
                               [fastopen=]disabled|enabled|default [fastopenfallback=]disabled|enabled|default
                               [hystart=]disabled|enabled|default [prr=]disabled|enabled|default
                               [pacingprofile=]off|initialwindow|slowstart|always|default
netsh interface tcp set heuristics [wsh=]disabled|enabled|default [forcews=]disabled|enabled|default
netsh interface tcp set security [mpp=]disabled|enabled|default [startport=]<integer> [numberofports=]<integer>
                                 [profiles=]disabled|enabled|default
netsh interface tcp set supplemental [template=]automatic|datacenter|internet|compat|custom [minrto=]<integer>
                                     [icw=]<integer> [congestionprovider=]none|ctcp|dctcp|cubic|bbr2|default
                                     [enablecwndrestart=]disabled|enabled|default [delayedacktimeout=]<integer>
                                     [delayedackfrequency=]<integer> [rack=]disabled|enabled|default
                                     [taillossprobe=]disabled|enabled|default
netsh interface tcp show global [store=]active|persistent
netsh interface tcp show heuristics [heuristics=]wsh|forcews
netsh interface tcp show rscstats [interface=]<string>
netsh interface tcp show security [store=]active|persistent
netsh interface tcp show supplemental [template=]automatic|datacenter|internet|compat|custom
netsh interface tcp show supplementalports [level=]normal|verbose
netsh interface tcp show supplementalsubnets [level=]normal|verbose
```

```
netsh interface teredo dump
netsh interface teredo set state [type]=disabled|client|enterpriseclient|natawareclient|server|default
                                 [servername=]<hostname>|<IPv4 address>|default [refreshinterval=]<integer>|default
                                 [clientport=]<integer>|default [servervirtualip=]<IPv4 address>|default
netsh interface teredo show state
```

```
netsh interface udp dump
netsh interface udp reset
netsh interface udp set global [uro=]disabled|enabled|default [uso=]disabled|enabled|default
netsh interface udp show global [store=]active|persistent
```

## Parameters

### interface 6to4

| Command | Description |
| --- | --- |
| interface `6to4 set interface` | Configures settings for a specified 6to4 interface in the legacy IPv4-based context. `name` - Specifies the interface name or index. `routing` - Sets whether the interface acts as a router:  - `enabled`: Turns on routing for this interface.  - `disabled`: Turns off routing for this interface.  - `default`: Uses the system’s default routing setting. |
| interface `6to4 set relay` | Configures the relay server for 6to4 tunneling in the legacy IPv4-based context. `name` - Specifies the name of the 6to4 relay or use `default` for the system default. `state` - Sets the state of relay name resolution:  - `enabled`: Forces the relay to be active and handle 6to4 traffic.  - `disabled`: Turns off the relay. It doesn't process any 6to4 traffic.  - `automatic`: Lets Windows decide when to enable or disable the relay based on network conditions.  - `default`: Resets the relay state to its default configuration. `interval` - Sets the relay name resolution interval in minutes. |
| interface `6to4 set routing` | Configures routing options for 6to4 tunneling in the legacy IPv4-based context. `routing` - Controls how 6to4 routing is handled:  - `enabled`: Forces 6to4 routing to be active.  - `disabled`: Turns off 6to4 routing.  - `automatic`: Lets Windows decide when to enable/disable routing based on network conditions.  - `default`: Resets routing to the system default. `sitelocals` - Manages the use of site-local addresses in 6to4 routing:  - `enabled`: Allows site-local addresses.  - `disabled`: Blocks site-local addresses.  - `default`: Resets to the system default for site-local address handling. |
| interface `6to4 set state` | Configures the 6to4 service in the legacy IPv4-based context `state` - Specifies the operational mode for the 6to4 service:  - `disabled`: Disables the 6to4 service; no 6to4 interfaces are created.  - `enabled`: Enables the 6to4 service and configures 6to4 addresses for each public IPv4 address.  - `automatic`: Enables the 6to4 service to automatically configure itself for each available public IPv4 address.  - `default`: Restores the default 6to4 behavior, equivalent to `disabled`. `undoonstop` - Determines whether 6to4 is disabled when the service stops. |
| interface `6to4 show` | Displays the 6to4 interface configuration and status in the legacy IPv4-based context. `interface` - Displays the configuration details of the 6to4 interface. `relay` - Displays information about the 6to4 relay server. `routing` - Displays the current routing state for 6to4. `state` - Displays the current operational state of the 6to4 service. |

### interface clat

| Command | Description |
| --- | --- |
| interface `clat set global` | Configures global Customer-side Translator (CLAT) settings, including enabling or disabling CLAT and setting DNS or RA preferences. If both `pref64fromdns` and `pref64fromra` are disabled, CLAT can't be activated because this combination is invalid. `permit` - Specifies if CLAT is allowed on noncellular interfaces. `pref64fromdns` - Determines whether DNS is used as the source for prefix information. If `pref64fromra` is also enabled, DNS is used only as a fallback. `pref64fromra` - Determines whether router advertisements (RA) are used as the source for prefix information. |
| interface `clat show global` | Displays the current global CLAT configuration settings. |

### interface dump

| Command | Description |
| --- | --- |
| interface `dump` interface `6to4 dump` interface `clat dump` interface `fl48 dump` interface `fl68 dump` interface `httpstunnel dump` interface `ipv4 dump` interface `ipv6 6to4 dump` interface `ipv6 dump` interface `ipv6 isatap dump` interface `isatap dump` interface `portproxy dump` interface `tcp dump` interface `teredo dump` interface `udp dump` | Creates a script containing the current context configuration. The script can be saved to a file and used to restore settings if they're altered or need to be replicated on another system. |

### interface fl48

| Command | Description |
| --- | --- |
| interface `fl48 show virtualinterfaces` | Displays a list of all FL48 virtual interfaces. |

### interface fl68

| Command | Description |
| --- | --- |
| interface `fl68 show virtualinterfaces` | Displays a list of all FL68 virtual interfaces. |

### interface httpstunnel

| Command | Description |
| --- | --- |
| interface `httpstunnel add interface` | Creates and configures an IPHTTPS client or server interface, allowing you to specify connection properties and authentication settings. `type` - Specifies the interface type:  - `client`: Configures a client interface.  - `server`: Configures a server interface (valid only on Windows Server). `url` - For a server interface, the URL to listen for HTTP(S) requests. For a client interface, the URL to send HTTP(S) requests. `state` - Sets the operational state:  - `default`: Server interface is always configured. Client interface is configured on demand (default for client).  - `enabled`: Interface is always configured (default for server).  - `disabled`: Disables the interface. `authmode` - Specifies authentication mode:  - `none`: No client authentication during SSL handshake (default).  - `certificates`: Uses client certificates for authentication (server interface only, valid only for Windows Server). |
| interface `httpstunnel delete interface` | Removes an existing IPHTTPS client or server interface configuration. |
| interface `httpstunnel reset` | Removes all IPHTTPS client and server interface configurations from the local system. |
| interface `httpstunnel set interface` | Modifies the configuration of an existing IPHTTPS client or server interface. `url` - For a server interface, the URL to listen for HTTP(S) requests. For a client interface, the URL to send HTTP(S) requests. `state` - Sets the operational state:  - `default`: Server interface is always configured. Client interface is configured on demand (default for client).  - `enabled`: Interface is always configured (default for server).  - `disabled`: Disables the interface. `authmode` - Specifies authentication mode:  - `none`: No client authentication during SSL handshake (default).  - `certificates`: Uses client certificates for authentication (server interface only, valid only for Windows Server). |
| interface `httpstunnel show interfaces` | Displays details for all network interfaces, or for a specified interface if provided. `store` - Specifies which interfaces to display:  - `active`: Shows only active interfaces.  - `persistent`: Shows all interfaces (default). |
| interface `httpstunnel show statistics` | Shows IPHTTPS interface statistics. `interface` - Specifies the interface name for which statistics are displayed. |

### interface ipv4

| Command | Description |
| --- | --- |
| interface `ipv4 add address` | Assigns a static IPv4 address and default gateway to a specified interface. If the interface is currently configured for DHCP, DHCP is disabled when this command is executed. `name` - Specifies the interface name or index. `address` - The IPv4 address to assign. Optionally, include a subnet prefix length (example: `192.168.1.10/24`). `mask` - Specifies the subnet mask for the IP address. `type` - Specifies the address type. Use `unicast` to assign a unicast address (default), or `anycast` to assign an anycast address. `gateway` - The IPv4 address of the default gateway. `gwmetric` - The metric value for the default gateway. `validlifetime` - Duration of the address or route that remains valid. Default is `infinite`. `preferredlifetime` - Duration of the address or route that's preferred. Default is `infinite`. `subinterface` - Specifies the LUID of the subinterface for the default gateway. Required only for interfaces with multiple subinterfaces. `store` - Specifies the address persistence. Use `active` for a temporary address removed on reboot, or `persistent` to retain the address after reboot (default). `skipassource` - If `true`, the address isn't used as the source for outgoing packets unless explicitly specified. Default is `false`. |
| interface `ipv4 add dnsservers` | Adds a new DNS server IP address to the static list for the specified interface. By default, the new DNS server is appended to the end of the list. If an index is provided, the server is inserted at that position, shifting others as needed. If the interface previously used DHCP for DNS, the static address replaces the DHCP-assigned list. When the `validate` option is set to `yes`, the new DNS server is verified before being added. `name` - Specifies the name or index of the interface where the DNS server is added. `address` - The IPv4 address of the DNS server to add. `index` - Sets the preference order for the DNS server address. `validate` - Indicates whether to validate the DNS server setting using `yes` (default) or `no`. |
| interface `ipv4 add excludedportrange` | Excludes a specified range of consecutive ports from being used by the system. `protocol` - Specifies the protocol to exclude. Use `tcp` to exclude TCP ports or `udp` to exclude UDP ports. `startport` - The starting port number for the exclusion range. `numberofports` - The total number of consecutive ports to exclude, beginning with `startport`. `store` - Determines the persistence of the exclusion. Use `active` for a temporary exclusion until the next reboot, or `persistent` to retain the exclusion after reboot (default). |
| interface `ipv4 add neighbors` | Adds a neighbor entry to the specified network interface. This is typically used to associate an IP address with a link-layer (MAC) address. `interface` - The name or index of the network interface where the neighbor entry will be added. `address` - The IPv4 address of the neighbor. `neighbor` - The link-layer (MAC) address to associate with the specified IP address. `subinterface` - The LUID of the subinterface, required only for interfaces with multiple subinterfaces. `store`: Determines whether the entry is temporary (`active`, removed on next reboot) or permanent (`persistent`, retained after reboot; this is the default). |
| interface `ipv4 add route` | Adds a network route for a specified IP prefix, allowing traffic to be directed through a chosen interface and gateway. `prefix` - The IP prefix for which to add a route. `interface` - The name or index of the interface to use for the route. `nexthop` - The gateway address, if the prefix isn't on-link. `siteprefixlength` - The prefix length for the entire site, if on-link. `metric` - The metric value for the route. `publish` - Controls advertisement in Route Advertisements. Use `no` (default) to not advertise, `age` to advertise with a finite lifetime, or `yes` to advertise with an infinite lifetime. `validlifetime` - The duration for which the route remains valid. Default is `infinite`. `preferredlifetime` - The duration for which the route is preferred. Default is equal to `validlifetime`. `store` - Determines persistence. Use `active` for a temporary change (until next boot), or `persistent` for a change that remains after reboot (default). |
| interface `ipv4 add winsservers` | Adds a new WINS server IP address to the static list for the specified interface. By default, the server is appended to the end of the list. If an index is provided, the server is inserted at that position, shifting other entries as needed. If the interface previously received WINS servers via DHCP, the new address replaces the DHCP-assigned list. `name` - The name or index of the interface to which the WINS server is added. `address` - The IP address of the WINS server to add. `index` - Sets the preference order for the specified WINS server address. |
| interface `ipv4 delete address` | Removes a static IPv4 address or default gateway from the specified interface. `name` - The interface name or index. `address` - The static IPv4 address to delete. `gateway` - Specify either a particular default gateway IP address to delete, or use `all` to delete all default gateway IP addresses on the interface. `store` - Use `active` to make the deletion temporary (until next boot), or `persistent` to make it permanent (default). |
| interface `ipv4 delete arpcache` | Deletes entries from the Address Resolution Protocol (ARP) cache. Flushing the ARP cache removes all ARP entries. If an interface is specified, only that interface's cache is flushed. If an address is specified, only the matching ARP entry is deleted. `name` - Specifies the interface name or index. `address` - The IPv4 address of the neighbor to remove. `subinterface` - The LUID of the subinterface. `store` - Determines which store to delete from. By default, entries in both stores are deleted:  - `active`: Entry may reappear on next boot.  - `persistent`: Entry is removed permanently. |
| interface `ipv4 delete destinationcache` | Flushes the destination cache, which stores routing information for IPv4 destinations. If an interface is specified, only that interface's cache is flushed. If an address is also specified, only that destination cache entry is deleted. `interface` - The name or index of the interface. `address` - The destination address. |
| interface `ipv4 delete dnsservers` | Deletes statically configured DNS server IP addresses for a specific interface. If `validate` is set to `yes`, the remaining DNS servers are validated. `name` - The name or index of the interface where DNS servers are deleted. `address` - The IP address of the DNS server to delete, or `all` to delete all configured DNS server addresses. `validate` - Specifies whether to validate the DNS server setting after deletion, `yes` (default) or `no`. |
| interface `ipv4 delete excludedportrange` | Deletes a previously set exclusion for a range of TCP or UDP ports. The`startport` and `numberofports` must match the previously created exclusion. `protocol` - `tcp` to delete a TCP exclusion, or `udp` for UDP. `startport` - The starting port number of the exclusion.`numberofports` - The number of consecutive ports to delete, starting from `startport`. `store` - `active` for a temporary deletion (until next boot), or `persistent` for a permanent deletion (default). |
| interface `ipv4 delete neighbors` | Deletes entries from the IPv4 neighbor cache. By default, entries in both stores are deleted. `name` - The interface name or index. `address` - The neighbor's IP address. `subinterface` - The subinterface LUID. `store` - `active` for a temporary deletion (entry may reappear on next boot), or `persistent` for a permanent deletion. |
| interface `ipv4 delete route` | Deletes an IPv4 route from the routing table. `prefix` - The IP prefix of the route to delete (for example, `192.168.1.0/24`). `interface` - The name or index of the interface associated with the route. `nexthop` - The gateway address for the route, if the prefix isn't on-link. `store` - Specifies whether the deletion is temporary (`active`, until next boot) or permanent (`persistent`). By default, entries in both stores are deleted. |
| interface `ipv4 delete winsservers` | Deletes statically configured WINS server IP addresses for a specific interface. `name` - The name or index of the interface where WINS servers are deleted. `address` - The IP address of the WINS server to delete, or use `all` to delete all configured WINS server addresses for the interface. |
| interface `ipv4 install` | Installs the IP protocol. A system restart is required for the changes to take effect. |
| interface `ipv4 reset` | Removes all user-configured settings. You must restart your computer for the default settings to take effect. |
| interface `ipv4 set address` | Enables or disables DHCP for IP address configuration. Removes any previous static IP addresses and default gateways, and can add a new static IP address and default gateway. `name` - Interface name or index. `source` - `dhcp` enables DHCP for configuring IP addresses for the specified interface. `static` disables DHCP and must be specified if an address or gateway is being configured. `address` - IPv4 address to add or modify, optionally followed by the subnet prefix length. `mask` - The IP subnet mask for the specified IP address. `gateway` - Either a specific IPv4 address for the default gateway or `none` (default, no gateway). `gwmetric` - The metric value for the default gateway. Set only if gateway is specified. `type` - `unicast` (default) marks the address as a unicast address while `anycast` marks it as anycast. `subinterface` - The LUID of the subinterface on which the default gateway exists. Needed only for interfaces with multiple subinterfaces. `store` - Determines whether the configuration change is temporary (`active`, lasts until the next reboot) or permanent (`persistent`, remains after reboot; default). |
| interface `ipv4 set compartment` | Modifies compartment settings for a network interface. `compartment` - Specifies the compartment ID to configure. `defaultcurhoplimit` - Sets the default hop limit for outgoing packets in the compartment. `store` - Determines persistence:  - `active`: Applies until next reboot.  - `persistent`: Retains the setting after reboot. |
| interface `ipv4 set dnsservers` | Sets DNS server configuration to either DHCP or static mode. When `source` is `static`, the `address` option is available for configuring a static list of DNS server IP addresses for the specified interface. If `validate` is `yes`, the newly set DNS server is validated. `name` - Name or index of the interface. `source` - `dhcp` sets DHCP as the source for configuring DNS servers. `static` sets the source to local static configuration. `address` - IP address for a DNS server or `none` to clear the list. `register` - `none` disables Dynamic DNS registration, `primary` registers under the primary DNS suffix only, `both` registers under both the primary and connection-specific suffixes. `validate` - Specifies whether validation of the DNS server setting is performed, `yes` (default) or `no`. |
| interface `ipv4 set dynamicportrange` | Modifies the range of ports used for dynamic port assignment (wildcard port assignment). `protocol` - Determines the protocol type:  - `tcp` modifies the dynamic port range for TCP.  - `udp` for UDP. `startport` - Starting port for dynamic port assignment. `numberofports` - Number of ports available for dynamic port assignment. `store` - Determines whether the configuration change is temporary (`active`, lasts until the next reboot) or permanent (`persistent`, remains after reboot (default)). |
| interface `ipv4 set global` | Configures the global IPv4 stack settings. `addressmaskreply` - Enables (`enabled`) or disables (`disabled`) responding to ICMP address mask packets. `defaultcurhoplimit` - Sets the default hop limit for outgoing packets. `dhcpmediasense` - Enables (`enabled`) or disables (`disabled`) media sense (network connection detection). `flowlabel` - Enables (`enabled`) or disables (`disabled`) flow label support. `groupforwardedfragments` - Enables (`enabled`) or disables (`disabled`) grouping of fragments before forwarding. `icmpjumbograms` - Enables (`enabled`) or disables (`disabled`) ICMP jumbograms (IPv6 only). `icmpredirects` - Enables (`enabled`) or disables (`disabled`) updating the path cache in response to ICMP redirect packets. `loopbackexecutionmode` - Sets execution mode for loopback processing:  - `inline`: Loopback packet processing happens directly in the context of the thread that sends the packet. This is the simplest and fastest mode, but it can block the sending thread if processing takes time.  - `adaptive`: The system dynamically chooses between inline and worker modes based on current load and performance.  - `worker`: Loopback packet processing is offloaded to a separate worker thread. This prevents blocking the sending thread, which can improve responsiveness under heavy load, but may introduce a slight delay. `loopbacklargemtu` - Enables (`enabled`) or disables (`disabled`) large IP MTU for the loopback path. `loopbackworkercount` - Number of worker threads (1-16) for loopback processing in adaptive mode. `mediasenseeventlog` - Enables (`enabled`) or disables (`disabled`) media sense (network connection detection) event logging. `minmtu` - Sets the minimum IP MTU to avoid fragmentation. For IPv4, range is 352-576. For IPv6, it's fixed at 1280. `mldlevel` - Sets multicast support level:  - `none`: Multicast packets can't be sent or received.  - `sendonly`: Multicast packets can be sent but not received.  - `all`: Multicast packets can be sent and received. `mldversion` - The maximum Multicast Listener Discovery (MLD) version supported by the host. `multicastforwarding` - Enables (`enabled`) or disables (`disabled`) forwarding of multicast packets. `neighborcachelimit` - The maximum number of neighbor cache entries no longer referenced. `randomizeidentifiers` - Enables (`enabled`) or disables (`disabled`) randomization of interface identifiers. `reassemblylimit` - The maximum size of the reassembly buffer. `reassemblyoutoforderlimit` - The maximum number of out-of-order fragments for reassembly. `recursivereassembly` - Enables (`enabled`) or disables (`disabled`) recursive reassembly of fragments (IPv6 only). `routecachelimit` - The maximum number of route cache entries. `routepolicies` - Enables (`enabled`) or disables (`disabled`) route policies. `slaacmaxdadattempts` - The number of duplicate address detection attempts for SLAAC addresses (IPv6 only). `slaacprivacylevel` - The privacy level for SLAAC address suffixes (IPv6 only):  - `0`: Use EUI-64.  - `1`: Use randomized EUI-64.  - `2`: Use randomized EUI-64, prefix, and secret key. `sourcebasedecmp` - Enables (`enabled`) or disables (`disabled`) source-based Equal-Cost Multi-Path (ECMP). `sourceroutingbehavior` - Controls behavior for source-routed packets. Per [RFC 5095](https://datatracker.ietf.org/doc/html/rfc5095), forwarding of source-routed IPv6 packets is removed. `forward` is equivalent to `dontforward`. `store` - Specifies persistence:  - `active`: Setting lasts until next boot.  - `persistent`: Setting is retained after reboot (default). `taskoffload` - Enables (`enabled`) or disables (`disabled`) task offload. |
| interface `ipv4 set interface` | Modifies the configuration of an IPv4 network interface. `advertise` - Enables (`enabled`) or disables (`disabled`) whether the interface sends RA. By default, advertisements are disabled. `advertisedefaultroute` - Determines whether the interface is advertised as a default router. `advertisedrouterlifetime` - Sets the router lifetime (in seconds) advertised in RA with a value of **0** to **65535**. Default is 1,800 seconds. `basereachabletime` - Sets the base time (in milliseconds) that a neighbor is considered reachable. `currenthoplimit` - Sets the hop limit for outbound IPv4 traffic. Valid range is **0** to **255**. `dadtransmits` - Sets the number of Duplicate Address Detection (DAD) attempts. A value of **0** disables DAD. `dhcpstaticipcoexistence` - Enables (`enabled`) or disables (`disabled`) whether DHCP and static IP addresses are allowed to coexist on the interface. `ecncapability` - Controls Explicit Congestion Notification (ECN) marking for outgoing packets:  - `ecndisabled`: Disables ECN marking. Outgoing packets won't use ECN bits, so congestion is signaled only by packet loss.  - `ect0`: Sets ECN bits to ECT(0), indicating the packet is ECN-capable. Routers can mark congestion without dropping packets.  - `ect1`: Sets ECN bits to ECT(1), another ECN-capable codepoint (rarely used; functionally similar to ECT(0)).  - `application`: Leaves ECN marking up to the application. The application decides whether and how to set ECN bits. `enabledirectedmacwolpattern` - Enables (`enabled`) or disables (`disabled`) directed MAC packet patterns to wake the computer. `forcearpndwolpattern` - Enables (`enabled`) or disables (`disabled`) address resolution and neighbor discovery packet patterns to wake the computer from sleep. `forwarding` - Enables (`enabled`) or disables (`disabled`) packet forwarding on this interface. When enabled, the interface can route packets to other interfaces. `ignoredefaultroutes` - When set to `enabled`, default routes on this interface are ignored. Default is `disabled`. `interface` - Specifies the name or index of the network interface to configure. `managedaddress` - Enables (`enabled`) or disables (`disabled`) managed address configuration, allowing addresses to be assigned via DHCPv6. This setting may be overridden if router discovery is enabled and advertising is disabled. `mtu` - Sets the Maximum Transmission Unit (MTU) for the interface. If not specified, the link's default MTU is used. `nud` - Enables (`enabled`) or disables (`disabled`) Neighbor Unreachability Detection (NUD), which helps determine if a neighbor is reachable. `otherstateful` - Enables (`enabled`) or disables (`disabled`) other stateful configuration options, such as obtaining additional settings via DHCPv6. This may also be overridden by router discovery settings. `rabaseddnsconfig` - Enables (`enabled`) or disables (`disabled`) DNS configuration via RA as defined in [RFC 6106](https://datatracker.ietf.org/doc/html/rfc6106). `retransmittime` - Specifies the time (in milliseconds) between retransmissions of neighbor solicitation messages. `routerdiscovery` - Enables, disables, or allows DHCP to control router discovery on the interface. `siteprefixlength` - Defines the default length of the global IPv6 prefix for the site. `store` - Specifies whether the configuration change is temporary (`active`, until next reboot) or persistent (`persistent`, remains after reboot). `weakhostreceive` - Enables weak host receive behavior, allowing the interface to receive packets for IP addresses not assigned to it. `weakhostsend` - Enables weak host send behavior, allowing the interface to send packets even if the source IP doesn't belong to the interface. |
| interface `ipv4 set neighbors` | Configures a static neighbor entry for an IPv4 interface. `interface` - The name or index of the network interface to configure. `address` - IPv4 address of the neighbor. `neighbor` - Link-layer (MAC) address to associate with the specified IPv4 address. `store` - Determines persistence:  - `active` Entry is removed on next boot.  - `persistent`: Entry remains after reboot (default). |
| interface `ipv4 set route` | Modifies parameters for an IPv6 route. When `publish` is set to `no` or `age`, the route is deleted after the valid lifetime expires. If `publish` is `age`, RAs include the remaining valid lifetime. If `publish` is set to `yes`, the route is never deleted and RAs always show the specified valid lifetime. `prefix` - The IPv6 prefix of the route to modify. `interface` - The name or index of the interface for the route. `nexthop` - The gateway IPv6 address, if the prefix isn't on-link. `siteprefixlength` - The prefix length for the entire site if on-link. `metric` - The metric value for the route. `publish` - Controls advertisement in RA:  - `no`: Not advertised (default).  - `age`: Advertised with finite lifetime.  - `yes`: Advertised with infinite lifetime. `validlifetime` - The duration value of the route to remain valid (default is infinite). `preferredlifetime` - The duration of the route that's preferred (default is infinite). `store` - Determines persistence:  - `active` Entry is removed on next boot.  - `persistent`: Entry remains after reboot (default).  Time values can be expressed in days, hours, minutes, and seconds (`1d2h3m4s`). |
| interface `ipv4 set subinterface` | Modifies the subinterface configuration parameters. `interface` - The name or index of the interface to configure. `mtu` - Sets the MTU for the subinterface. Defaults to the link's natural MTU if not specified. `subinterface` - The LUID of the subinterface. Required only for interfaces with multiple subinterfaces. `store` - Specifies persistence:  - `active`: Setting lasts until next boot. `persistent`: Setting is retained after reboot. |
| interface `ipv4 set winsservers` | Configures the WINS server settings for a specified interface. Use `source=dhcp` to configure WINS servers via DHCP. Use `source=static` to specify a static list of WINS server IP addresses for the interface. The `address` option is available only when `source=static`. `name` - Specifies the interface name or index. `source` - Sets the source for WINS server configuration:  - `dhcp`: Uses DHCP to configure WINS servers.  - `static`: - Uses a static list of WINS server IP addresses. `address` - Specifies the WINS server IP address. `none` - Clears the WINS servers list. |
| interface `ipv4 show addresses` | Displays the IP address configuration for all interfaces or a specific interface. `name` - Specifies the interface name or index. |
| interface `ipv4 show compartments` | Displays information about all compartments, or details for a specified compartment. `compartment` - Specifies the compartment ID to display information for. `level` - Sets the output detail level. Use `normal` to show one line per compartment (default if no compartment is specified), or `verbose` to show detailed information (default if a compartment is specified). `store` - Chooses which compartments to display:  - `active`: Shows current compartments (default).  - `persistent`: Shows compartments saved for future use. |
| interface `ipv4 show config` | Displays the IP address and TCP/IP configuration details for one or more interfaces, including assigned DNS and WINS servers. `name` - Specifies the interface name or index. |
| interface `ipv4 show destinationcache` | Shows destination cache entries. If `interface` is specified, it displays the cache for that interface only. If `address` is also specified, shows only the matching destination cache entry. `interface` - Specifies the interface name or index. `address` - Sets the destination address. `level` - Chooses output detail:  - `normal`: Displays one line per entry (default if no address is given).  - `verbose`: Shows extra information for each entry (default if an address is given). |
| interface `ipv4 show dnsservers` | Displays the DNS server settings for one or more specified network interfaces. `name` - Specifies the interface name or index. |
| interface `ipv4 show dynamicportrange` | Shows the configuration parameters for dynamic port ranges. `protocol` - Specifies the protocol type:  - `tcp`: Displays the dynamic port range for TCP.  - `udp`: Displays the range for UDP. `store` - Selects which configuration to show:  - `active`: Displays current stack settings (default).  - `persistent`: Displays saved settings. |
| interface `ipv4 show excludedportrange` | Shows all excluded port ranges. `protocol` - Specifies the protocol type:  - `tcp`: Displays the dynamic port range for TCP.  - `udp`: Displays the range for UDP. `store` - Selects which configuration to show:  - `active`: Displays current stack settings (default).  - `persistent`: Displays saved settings. |
| interface `ipv4 show global` | Shows the global configuration parameters. `store` - Selects which configuration to show:  - `active`: Displays current stack settings (default).  - `persistent`: Displays saved settings. |
| interface `ipv4 show icmpstats` | Displays the ICMP statistics information. `rr` - Specifies the interval, in seconds, at which the interface ICMP statistics are refreshed. |
| interface `ipv4 show interfaces` | Shows information about all interfaces, or about a specified interface if provided. `interface` - Specifies the name or index of the network interface. `rr` - Sets the refresh interval, in seconds, for updating interface statistics. `level` - Sets the detail level for output.  - `normal`: Shows one line per interface (default if no interface is specified).  - `verbose`: Displays detailed information (default if an interface is specified). `store` - Chooses which interfaces to display:  - `active`: Shows currently active interfaces (default).  - `persistent`: Shows interfaces saved for future use. |
| interface `ipv4 show ipaddresses` | Shows information about all IPv4 addresses, or about a specified interface if provided. `interface` - Specifies the name or index of the network interface. `level` - Sets the detail level for output.  - `normal`: Shows one line per interface (default if no interface is specified).  - `verbose`: Displays detailed information (default if an interface is specified). `store` - Chooses which interfaces to display:  - `active`: Shows currently active interfaces (default).  - `persistent`: Shows interfaces saved for future use. |
| interface `ipv4 show ipnettomedia` | Displays the IP network to physical media mappings information. `rr` - Specifies the refresh interval, in seconds, for updating interface IP net-to-media mappings. |
| interface `ipv4 show ipstats` | Displays the IP statistics information. `rr` - Specifies the refresh interval, in seconds, for updating IP statistics. |
| interface `ipv4 show joins` | Shows IP multicast groups joined on one or more interfaces. If no interface is specified, multicast groups for all interfaces are displayed. `interface` - Specifies the name or index of the network interface. `level` - Sets the output detail level:  - `normal`: Shows one line per interface (default if no interface is specified).  - `verbose`: Displays detailed information (default if an interface is specified). |
| interface `ipv4 show neighbors` | Displays neighbor cache entries for IPv4 interfaces. If you specify an interface, only its cache is shown. If you also specify a subinterface, only entries for that subinterface are displayed. If you provide an address, only the entry for that specific neighbor is shown. `interface` - The name or index of the network interface. `address` - The IPv4 address of the neighbor. `subinterface` - The LUID of the subinterface. `level` - Specifies the output detail:  - `normal`: Shows one line per subinterface (default if no subinterface is given).  - `verbose`: Shows extra details (default if a subinterface is given). `store` - Chooses which interfaces to display:  - `active`: Shows currently active interfaces (default).  - `persistent`: Shows interfaces saved for future use. |
| interface `ipv4 show offload` | Displays the offload information of a specific interface or interfaces. `name` - Specifies the interface name or index. |
| interface `ipv4 show route` | Shows entries in the route table. `level` - Specifies the detail of route information to display:  - `normal`: Shows standard routes (default).  - `verbose`: Includes loopback routes. `store` - Selects which route table to display. Use `active` for current stack information (default), or `persistent` for saved configuration. |
| interface `ipv4 show subinterfaces` | Shows information about all subinterfaces, or about all subinterfaces on a specified interface if provided. `interface` - Specifies the interface name or index. `subinterface` - Specifies the LUID of the subinterface, used only for interfaces with multiple subinterfaces. `level` - Sets the output detail:  - `normal`: Shows one line per subinterface (default if no subinterface is specified).  - `verbose`: Displays detailed information for each subinterface (default if a subinterface is specified). `store` - Selects which subinterfaces to display:  - `active`: Shows currently active subinterfaces (default).  - `persistent`: Shows persistent subinterfaces. |
| interface `ipv4 show tcpconnections` | Displays the status of TCP connections. `localaddress` - Specifies the local IP address for the connection. `localport` - Specifies the local port number for the connection. `remoteaddress` - Specifies the remote IP address for the connection. `remoteport` - Specifies the remote port number for the connection. `rr` - Sets the refresh rate, in seconds, for displaying TCP connection information. |
| interface `ipv4 show tcpstats` | Displays the TCP connection statistics. `rr` - Specifies the refresh interval, in seconds, for updating TCP statistics information. |
| interface `ipv4 show udpconnections` | Displays the UDP connection status information. `localaddress` - Specifies the local IP address of the UDP endpoint. `localport` - Specifies the local port number of the UDP endpoint. `rr` - Sets the refresh interval, in seconds, for displaying UDP connection information. |
| interface `ipv4 show udpstats` | Displays the UDP connection statistics. `rr` - Sets the refresh interval, in seconds, for displaying UDP statistics information. |
| interface `ipv4 show winsservers` | Displays the WINS server configuration for a specific interface or interfaces. `name` - Specifies the interface name or index. |
| interface `ipv4 uninstall` | Removes the IPv4 protocol from the system. A system restart is required for the changes to take effect. |

### interface ipv6

| Command | Description |
| --- | --- |
| interface `ipv6 6to4 set interface` | Configures settings for a specified 6to4 interface within the IPv6 context. `name` - Specifies the interface name or index. `routing` - Sets whether the interface acts as a router:  - `enabled`: Turns on routing for this interface.  - `disabled`: Turns off routing for this interface.  - `default`: Uses the system’s default routing setting. |
| interface `ipv6 6to4 set relay` | Configures the 6to4 relay server for IPv6 tunneling. `name` - Specifies the name of the 6to4 relay or use `default` for the system default. `state` - Sets the state of relay name resolution:  - `enabled`: Forces the relay to be active and handle 6to4 traffic.  - `disabled`: Turns off the relay. It doesn't process any 6to4 traffic.  - `automatic`: Lets Windows decide when to enable or disable the relay based on network conditions.  - `default`: Resets the relay state to its default configuration. `interval` - Sets the relay name resolution interval in minutes. |
| interface `ipv6 6to4 set routing` | Configures routing options for 6to4 tunneling in the IPv6 configuration context. `routing` - Controls how 6to4 routing is handled:  - `enabled`: Forces 6to4 routing to be active.  - `disabled`: Turns off 6to4 routing.  - `automatic`: Lets Windows decide when to enable/disable routing based on network conditions.  - `default`: Resets routing to the system default. `sitelocals` - Manages the use of site-local addresses in 6to4 routing:  - `enabled`: Allows site-local addresses.  - `disabled`: Blocks site-local addresses.  - `default`: Resets to the system default for site-local address handling. |
| interface `ipv6 6to4 set state` | Configures the 6to4 service in the IPv6 configuration context. `state` - Specifies the operational mode for the 6to4 service:  - `disabled`: Disables the 6to4 service; no 6to4 interfaces are created.  - `enabled`: Enables the 6to4 service and configures 6to4 addresses for each public IPv4 address.  - `automatic`: Enables the 6to4 service to automatically configure itself for each available public IPv4 address.  - `default`: Restores the default 6to4 behavior, equivalent to `disabled`. `undoonstop` - Determines whether 6to4 is disabled when the service stops. |
| interface `ipv6 6to4 show` | Displays the 6to4 interface configuration and status in the IPv6 configuration context. `interface` - Displays the configuration details of the 6to4 interface. `relay` - Displays information about the 6to4 relay server. `routing` - Displays the current routing state for 6to4. `state` - Displays the current operational state of the 6to4 service. |
| interface `ipv6 add address` | Assigns a static IPv4 address and default gateway to a specified interface. If the interface is currently configured for DHCP, DHCP is disabled when this command is executed. `interface` - Specifies the interface name or index. `address` - The IPv6 address to assign. Optionally, include a subnet prefix length (example: `192.168.1.10/24`). `type` - Specifies the address type. Use `unicast` to assign a unicast address (default), or `anycast` to assign an anycast address. `validlifetime` - Duration of the address or route that remains valid. Default is `infinite`. `store` - Specifies the address persistence. Use `active` for a temporary address removed on reboot, or `persistent` to retain the address after reboot (default). `skipassource` - If `true`, the address isn't used as the source for outgoing packets unless explicitly specified. Default is `false`. |
| interface `ipv6 add dnsservers` | Adds a new DNS server IPv6 address to the static list for the specified interface. By default, the new DNS server is appended to the end of the list. If an index is provided, the server is inserted at that position, shifting others as needed. If the interface previously used DHCP for DNS, the static address replaces the DHCP-assigned list. When the `validate` option is set to `yes`, the new DNS server is verified before being added. `name` - Specifies the name or index of the interface where the DNS server is added. `address` - The IPv6 address of the DNS server to add. `index` - Sets the preference order for the DNS server address. `validate` - Indicates whether to validate the DNS server setting using `yes` (default) or `no`. |
| interface `ipv6 add excludedportrange` | Excludes a specified range of consecutive ports from being used by the system for IPv6 traffic. `protocol` - Specifies the protocol to exclude. Use `tcp` to exclude TCP ports or `udp` to exclude UDP ports. `startport` - The starting port number for the exclusion range. `numberofports` - The total number of consecutive ports to exclude, beginning with `startport`. `store` - Determines the persistence of the exclusion. Use `active` for a temporary exclusion until the next reboot, or `persistent` to retain the exclusion after reboot (default). |
| interface `ipv6 add neighbors` | Adds a neighbor entry to the specified IPv6 network interface. This is typically used to associate an IP address with a link-layer (MAC) address. `interface` - The name or index of the network interface where the neighbor entry is added. `address` - The IPv6 address of the neighbor. `neighbor` - The link-layer (MAC) address to associate with the specified IP address. `subinterface` - The LUID of the subinterface, required only for interfaces with multiple subinterfaces. `store`: Determines whether the entry is temporary (`active`, removed on next reboot) or permanent (`persistent`, retained after reboot; this is the default). |
| interface `ipv6 add potentialrouter` | Adds a potential router to the specified interface. `interface` - Name or index of the interface. `address` - The IPv6 address of the potential router. |
| interface `ipv6 add prefixpolicy` | Adds a policy that influences how source and destination IPv6 addresses are selected for a specified prefix. `prefix` - The IPv6 prefix to which the policy applies. `precedence` - The precedence value used to sort destination addresses. `label` - The label used to match source and destination address prefixes. `store` - Determines persistence:  - `active`: The policy is temporary and removed on reboot.  - `persistent`: The policy remains after reboot (default). |
| interface `ipv6 add route` | Adds a network route for a specified IPv6 prefix. `prefix` - The IP prefix for which to add a route. `interface` - The name or index of the interface to use for the route. `nexthop` - The gateway address, if the prefix isn't on-link. `siteprefixlength` - The prefix length for the entire site, if on-link. `metric` - The metric value for the route. `publish` - Controls advertisement in Route Advertisements. Use `no` (default) to not advertise, `age` to advertise with a finite lifetime, or `yes` to advertise with an infinite lifetime. `validlifetime` - The duration for which the route remains valid. Default is `infinite`. `preferredlifetime` - The duration for which the route is preferred. Default is equal to `validlifetime`. `store` - Determines persistence. Use `active` for a temporary change (until next boot), or `persistent` for a change that remains after reboot (default). |
| interface `ipv6 add v6v4tunnel` | Creates an IPv6-over-IPv4 tunnel interface. &lt;rb&gt; `interface` - The friendly name for the tunnel interface. `localaddress` - The IPv4 address of the local tunnel endpoint. `remoteaddress` - The IPv4 address of the remote tunnel endpoint. |
| interface `ipv6 delete address` | Removes a static IPv6 address or default gateway from the specified interface. `interface` - The interface name or index. `address` - The static IPv6 address to delete. `store` - Use `active` to make the deletion temporary (until next boot), or `persistent` to make it permanent (default). |
| interface `ipv6 delete destinationcache` | Flushes the destination cache, which stores routing information for IPv6 destinations. If an interface is specified, only that interface's cache is flushed. If an address is also specified, only that destination cache entry is deleted. `interface` - The name or index of the interface. `address` - The destination address. |
| interface `ipv6 delete dnsservers` | Deletes statically configured DNS server IP addresses for a specific interface. If `validate` is set to `yes`, the remaining DNS servers are validated. `name` - The name or index of the interface where DNS servers are deleted. `address` - The IPv6 address of the DNS server to delete, or `all` to delete all configured DNS server addresses. `validate` - Specifies whether to validate the DNS server setting after deletion, `yes` (default) or `no`. |
| interface `ipv6 delete excludedportrange` | Deletes a previously set exclusion for a range of TCP or UDP ports. The`startport` and `numberofports` must match the previously created exclusion. `protocol` - `tcp` to delete a TCP exclusion, or `udp` for UDP. `startport` - The starting port number of the exclusion.`numberofports` - The number of consecutive ports to delete, starting from `startport`. `store` - `active` for a temporary deletion (until next boot), or `persistent` for a permanent deletion (default). |
| interface `ipv6 delete interface` | Removes a specified interface from the IPv6 stack. Only point-to-point interfaces that were manually configured can be deleted. `interface` - Name or index of the interface to delete. |
| interface `ipv6 delete neighbors` | Deletes entries from the IPv6 neighbor cache. By default, entries in both stores are deleted. `interface` - The interface name or index. `address` - The neighbor's IP address. `subinterface` - The subinterface LUID. `store` - `active` for a temporary deletion (entry may reappear on next boot), or `persistent` for a permanent deletion. |
| interface `ipv6 delete potentialrouter` | Removes a potential router from the specified interface. `interface` - Name or index of the interface. `address` - The IPv6 address of the potential router. |
| interface `ipv6 delete prefixpolicy` | Removes a policy that influences how source and destination IPv6 addresses are selected for a specified prefix. `prefix` - The IPv6 prefix to which the policy applies. `store` - Determines persistence:  - `active`: The policy is temporary and removed on reboot.  - `persistent`: The policy remains after reboot (default). |
| interface `ipv6 delete route` | Deletes an IPv6 route from the routing table. `prefix` - The IP prefix of the route to delete (for example, `192.168.1.0/24`). `interface` - The name or index of the interface associated with the route. `nexthop` - The gateway address for the route, if the prefix isn't on-link. `store` - Specifies whether the deletion is temporary (`active`, until next boot) or permanent (`persistent`). By default, entries in both stores are deleted. |
| interface `ipv6 isatap set router` | Configures the ISATAP router settings. `name` - Specifies the ISATAP router name or use `default` for the system default. `state` - Sets the router name resolution state:  - `enabled`: Enables router name resolution for ISATAP.  - `disabled`: Disables router name resolution for ISATAP.  - `default`: Restores the default router name resolution state. `interval` - Sets the router name resolution interval in minutes. |
| interface `ipv6 isatap set state` | Sets the operational state of the ISATAP service. `state` - Specifies the ISATAP service state:  - `disabled`: Disables the ISATAP service. No ISATAP interfaces are created.  - `enabled`: Enables the ISATAP service and configures a link-local address on each ISATAP interface. Additional addresses may be assigned by the ISATAP server.  - `default`: Attempts to contact the ISATAP server. If unreachable, no addresses are configured on the ISATAP interface. |
| interface `ipv6 isatap show` | Displays the following information: `router` - Displays information about the configured ISATAP router. `state` - Displays the current operational state of the ISATAP service. |
| interface `ipv6 reset` | Removes all user-configured IPv6 settings and restores defaults after a system restart. |
| interface `ipv6 set address` | Modifies the IPv6 address configuration for a specified interface. `interface` - Interface name or index. `address` - The IPv6 address to add or modify. `type` - Specifies the address type. `unicast` (default) marks the address as a unicast address while `anycast` marks it as anycast. `validlifetime` - The duration value of the route to remain valid (default is infinite). `preferredlifetime` - The duration of the route that's preferred (default is infinite). `store` - Determines whether the configuration change is temporary (`active`, lasts until the next reboot) or permanent (`persistent`, remains after reboot; default). |
| interface `ipv6 set compartment` | Updates compartment settings for a network interface. `compartment` - Specifies the compartment ID to configure. `defaultcurhoplimit` - Sets the default hop limit for outgoing packets in the compartment. `store` - Determines persistence:  - `active`: Applies until next reboot.  - `persistent`: Retains the setting after reboot. |
| interface `ipv6 set dnsservers` | Sets DNS server configuration to either DHCP or static mode. When `source` is `static`, the `address` option is available for configuring a static list of DNS server IP addresses for the specified interface. If `validate` is `yes`, the newly set DNS server is validated. `name` - Name or index of the interface. `source` - `dhcp` sets DHCP as the source for configuring DNS servers. `static` sets the source to local static configuration. `address` - IP address for a DNS server or `none` to clear the list. `register` - `none` disables Dynamic DNS registration, `primary` registers under the primary DNS suffix only, `both` registers under both the primary and connection-specific suffixes. `validate` - Specifies whether validation of the DNS server setting is performed, `yes` (default) or `no`. |
| interface `ipv6 set dynamicportrange` | Modifies the range of ports used for dynamic port assignment (wildcard port assignment). `protocol` - Determines the protocol type:  - `tcp` modifies the dynamic port range for TCP.  - `udp` for UDP. `startport` - Starting port for dynamic port assignment. `numberofports` - Number of ports available for dynamic port assignment. `store` - Determines whether the configuration change is temporary (`active`, lasts until the next reboot) or permanent (`persistent`, remains after reboot (default)). |
| interface `ipv6 set global` | Configures the global IPv6 stack settings. `addressmaskreply` - Enables (`enabled`) or disables (`disabled`) responding to ICMP address mask packets. `defaultcurhoplimit` - Sets the default hop limit for outgoing packets. `dhcpmediasense` - Enables (`enabled`) or disables (`disabled`) media sense (network connection detection). `flowlabel` - Enables (`enabled`) or disables (`disabled`) flow label support. `groupforwardedfragments` - Enables (`enabled`) or disables (`disabled`) grouping of fragments before forwarding. `icmpjumbograms` - Enables (`enabled`) or disables (`disabled`) ICMP jumbograms (IPv6 only). `icmpredirects` - Enables (`enabled`) or disables (`disabled`) updating the path cache in response to ICMP redirect packets. `loopbackexecutionmode` - Sets execution mode for loopback processing:  - `inline`: Loopback packet processing happens directly in the context of the thread that sends the packet. This is the simplest and fastest mode, but it can block the sending thread if processing takes time.  - `adaptive`: The system dynamically chooses between inline and worker modes based on current load and performance.  - `worker`: Loopback packet processing is offloaded to a separate worker thread. This prevents blocking the sending thread, which can improve responsiveness under heavy load, but may introduce a slight delay. `loopbacklargemtu` - Enables (`enabled`) or disables (`disabled`) large IP MTU for the loopback path. `loopbackworkercount` - Number of worker threads (1-16) for loopback processing in adaptive mode. `mediasenseeventlog` - Enables (`enabled`) or disables (`disabled`) media sense (network connection detection) event logging. `minmtu` - Sets the minimum IP MTU to avoid fragmentation. For IPv4, range is 352-576. For IPv6, it's fixed at 1280. `mldlevel` - Sets multicast support level:  - `none`: Multicast packets can't be sent or received.  - `sendonly`: Multicast packets can be sent but not received.  - `all`: Multicast packets can be sent and received. `mldversion` - The maximum Multicast Listener Discovery (MLD) version supported by the host. `multicastforwarding` - Enables (`enabled`) or disables (`disabled`) forwarding of multicast packets. `neighborcachelimit` - The maximum number of neighbor cache entries no longer referenced. `randomizeidentifiers` - Enables (`enabled`) or disables (`disabled`) randomization of interface identifiers. `reassemblylimit` - The maximum size of the reassembly buffer. `reassemblyoutoforderlimit` - The maximum number of out-of-order fragments for reassembly. `recursivereassembly` - Enables (`enabled`) or disables (`disabled`) recursive reassembly of fragments (IPv6 only). `routecachelimit` - The maximum number of route cache entries. `routepolicies` - Enables (`enabled`) or disables (`disabled`) route policies. `slaacmaxdadattempts` - The number of duplicate address detection attempts for SLAAC addresses (IPv6 only). `slaacprivacylevel` - The privacy level for SLAAC address suffixes (IPv6 only):  - `0`: Use EUI-64.  - `1`: Use randomized EUI-64.  - `2`: Use randomized EUI-64, prefix, and secret key. `sourcebasedecmp` - Enables (`enabled`) or disables (`disabled`) source-based Equal-Cost Multi-Path (ECMP). `sourceroutingbehavior` - Controls behavior for source-routed packets. Per [RFC 5095](https://datatracker.ietf.org/doc/html/rfc5095), forwarding of source-routed IPv6 packets is removed. `forward` is equivalent to `dontforward`. `store` - Specifies persistence:  - `active`: Setting lasts until next boot.  - `persistent`: Setting is retained after reboot (default). `taskoffload` - Enables (`enabled`) or disables (`disabled`) task offload. |
| interface `ipv6 set interface` | Modifies the configuration of an IPv6 network interface. `advertise` - Enables (`enabled`) or disables (`disabled`) whether the interface sends RA. By default, advertisements are disabled. `advertisedefaultroute` - Determines whether the interface is advertised as a default router. `advertisedrouterlifetime` - Sets the router lifetime (in seconds) advertised in RA with a value of **0** to **65535**. Default is 1,800 seconds. `basereachabletime` - Sets the base time (in milliseconds) that a neighbor is considered reachable. `currenthoplimit` - Sets the hop limit for outbound IPv6 traffic. Valid range is **0** to **255**. `dadtransmits` - Sets the number of Duplicate Address Detection (DAD) attempts. A value of **0** disables DAD. `dhcpstaticipcoexistence` - Enables (`enabled`) or disables (`disabled`) whether DHCP and static IP addresses are allowed to coexist on the interface. `ecncapability` - Controls Explicit Congestion Notification (ECN) marking for outgoing packets:  - `ecndisabled`: Disables ECN marking. Outgoing packets won't use ECN bits, so congestion is signaled only by packet loss.  - `ect0`: Sets ECN bits to ECT(0), indicating the packet is ECN-capable. Routers can mark congestion without dropping packets.  - `ect1`: Sets ECN bits to ECT(1), another ECN-capable codepoint (rarely used; functionally similar to ECT(0)).  - `application`: Leaves ECN marking up to the application. The application decides whether and how to set ECN bits. `enabledirectedmacwolpattern` - Enables (`enabled`) or disables (`disabled`) directed MAC packet patterns to wake the computer. `forcearpndwolpattern` - Enables (`enabled`) or disables (`disabled`) address resolution and neighbor discovery packet patterns to wake the computer from sleep. `forwarding` - Enables (`enabled`) or disables (`disabled`) packet forwarding on this interface. When enabled, the interface can route packets to other interfaces. `ignoredefaultroutes` - When set to `enabled`, default routes on this interface are ignored. Default is `disabled`. `interface` - Specifies the name or index of the network interface to configure. `managedaddress` - Enables (`enabled`) or disables (`disabled`) managed address configuration, allowing addresses to be assigned via DHCPv6. This setting may be overridden if router discovery is enabled and advertising is disabled. `mtu` - Sets the Maximum Transmission Unit (MTU) for the interface. If not specified, the link's default MTU is used. `nud` - Enables (`enabled`) or disables (`disabled`) Neighbor Unreachability Detection (NUD), which helps determine if a neighbor is reachable. `otherstateful` - Enables (`enabled`) or disables (`disabled`) other stateful configuration options, such as obtaining additional settings via DHCPv6. This may also be overridden by router discovery settings. `rabaseddnsconfig` - Enables (`enabled`) or disables (`disabled`) DNS configuration via RA as defined in [RFC 6106](https://datatracker.ietf.org/doc/html/rfc6106). `retransmittime` - Specifies the time (in milliseconds) between retransmissions of neighbor solicitation messages. `routerdiscovery` - Enables, disables, or allows DHCP to control router discovery on the interface. `siteprefixlength` - Defines the default length of the global IPv6 prefix for the site. `store` - Specifies whether the configuration change is temporary (`active`, until next reboot) or persistent (`persistent`, remains after reboot). `weakhostreceive` - Enables weak host receive behavior, allowing the interface to receive packets for IP addresses not assigned to it. `weakhostsend` - Enables weak host send behavior, allowing the interface to send packets even if the source IP doesn't belong to the interface. |
| interface `ipv6 set neighbors` | Configures a static neighbor entry for an IPv6 interface. `interface` - The name or index of the network interface to configure. `address` - IPv6 address of the neighbor. `neighbor` - Link-layer (MAC) address to associate with the specified IPv6 address. `store` - Determines persistence:  - `active` Entry is removed on next boot.  - `persistent`: Entry remains after reboot (default). |
| interface `ipv6 set prefixpolicy` | Modifies the source and destination address selection policy for a given IPv6 prefix. `prefix` - The IPv6 prefix for which to add or modify a policy. `precedence` - The precedence value used for address selection ordering. `label` - The label value for matching during address selection. `store` - Determines persistence:  - `active` Entry is removed on next boot.  - `persistent`: Entry remains after reboot (default). |
| interface `ipv6 set privacy` | Modifies parameters related to temporary IPv6 address generation. `state` - Enables (`enabled`) or disables (`disabled`) temporary address generation. `maxdadattempts` - The number of duplicate address detection attempts (default is 5). `maxvalidlifetime` - The maximum valid lifetime for a temporary address (default is seven days). `maxpreferredlifetime` - The maximum preferred lifetime for a temporary address (default is one day). `regeneratetime` - The time before deprecating a temporary address when a new address is generated (default is 5 seconds). `maxrandomtime` - The maximum random delay at startup (default is 10 minutes). `store` - Determines persistence:  - `active` Entry is removed on next boot.  - `persistent`: Entry remains after reboot (default).  Time values can be expressed in days, hours, minutes, and seconds (`1d2h3m4s`). |
| interface `ipv6 set route` | Modifies parameters for an IPv6 route. When `publish` is set to `no` or `age`, the route is deleted after the valid lifetime expires. If `publish` is `age`, RAs include the remaining valid lifetime. If `publish` is set to `yes`, the route is never deleted and RAs always show the specified valid lifetime. `prefix` - The IPv6 prefix of the route to modify. `interface` - The name or index of the interface for the route. `nexthop` - The gateway IPv6 address, if the prefix isn't on-link. `siteprefixlength` - The prefix length for the entire site if on-link. `metric` - The metric value for the route. `publish` - Controls advertisement in RA:  - `no`: Not advertised (default).  - `age`: Advertised with finite lifetime.  - `yes`: Advertised with infinite lifetime. `validlifetime` - The duration value of the route to remain valid (default is infinite). `preferredlifetime` - The duration of the route that's preferred (default is infinite). `store` - Determines persistence:  - `active` Entry is removed on next boot.  - `persistent`: Entry remains after reboot (default).  Time values can be expressed in days, hours, minutes, and seconds (`1d2h3m4s`). |
| interface `ipv6 set slaacsecretkey` | Sets the [RFC 7217](https://datatracker.ietf.org/doc/html/rfc7217) secret key for IPv6 SLAAC privacy. The key must be a 32-character hexadecimal string. This secret is used when the global SLAAC privacy level is set to 2 (`netsh interface ipv6 set global slaacprivacylevel=2`). `key` - A 32-character hexadecimal string used as the secret key for IPv6 SLAAC privacy. |
| interface `ipv6 set subinterface` | Modifies the subinterface configuration parameters. `interface` - The name or index of the interface to configure. `mtu` - Sets the MTU for the subinterface. Defaults to the link's natural MTU if not specified. `subinterface` - The LUID of the subinterface. Required only for interfaces with multiple subinterfaces. `store` - Specifies persistence:  - `active`: Setting lasts until next boot. `persistent`: Setting is retained after reboot. |
| interface `ipv6 set teredo` | Configures the Teredo operational state. Use `default` for any parameter to restore its system default. The `type=server` option is available only on Windows Server editions. `type` - Specifies the Teredo mode:  - `disabled`: Turns off the Teredo service.  - `client`: Enables the Teredo service on the client.  - `enterpriseclient`: Skips managed network detection.  - `natawareclient`: Enables Teredo client detection and NAT type.  - `server`: Enables the server (Windows Server only).  - `default`: Sets to the system default (client). `servername` - Sets the Teredo server name or IPv4 address. `refreshinterval` - Defines the client refresh interval in seconds. `clientport` - Sets the UDP port for the Teredo client. If omitted, the system chooses the port. `servervirtualip` - Specifies the IPv4 address for the server's virtual IP (not used in client mode). |
| interface `ipv6 show addresses` | Shows all IPv6 addresses, or only those for a specified interface if provided.`interface` - Specifies the interface name or index to display addresses for. `level` - Sets the output detail:  - `normal`: Displays one line per interface (default if no interface is specified).  -`verbose`: Displays detailed information (default if an interface is specified). `store` - Chooses which addresses to show: - `active`: Displays addresses currently in use (default).  -`persistent`: Displays addresses saved for future use. |
| interface `ipv6 show compartments` | Displays information about all compartments, or details for a specified compartment. `compartment` - Specifies the compartment ID to display information for. `level` - Sets the output detail level. Use `normal` to show one line per compartment (default if no compartment is specified), or `verbose` to show detailed information (default if a compartment is specified). `store` - Chooses which compartments to display:  - `active`: Shows current compartments (default).  - `persistent`: Shows compartments saved for future use. |
| interface `ipv6 show destinationcache` | Shows destination cache entries. If `interface` is specified, displays the cache for that interface only. If `address` is also specified, shows only the matching destination cache entry. `interface` - Specifies the interface name or index. `address` - Sets the destination address. `level` - Chooses output detail:  - `normal`: Displays one line per entry (default if no address is given).  - `verbose`: Shows extra information for each entry (default if an address is given). |
| interface `ipv6 show dnsservers` | Displays the DNS server settings for one or more specified network interfaces. `name` - Specifies the interface name or index. |
| interface `ipv6 show dynamicportrange` | Shows the configuration parameters for dynamic port ranges. `protocol` - Specifies the protocol type:  - `tcp`: Displays the dynamic port range for TCP.  - `udp`: Displays the range for UDP. `store` - Selects which configuration to show:  - `active`: Displays current stack settings (default).  - `persistent`: Displays saved settings. |
| interface `ipv6 show excludedportrange` | Shows all excluded port ranges. `protocol` - Specifies the protocol type:  - `tcp`: Displays the dynamic port range for TCP.  - `udp`: Displays the range for UDP. `store` - Selects which configuration to show:  - `active`: Displays current stack settings (default).  - `persistent`: Displays saved settings. |
| interface `ipv6 show global` | Shows the global configuration parameters. `store` - Selects which configuration to show:  - `active`: Displays current stack settings (default).  - `persistent`: Displays saved settings. |
| interface `ipv6 show interfaces` | Shows information about all interfaces, or about a specified interface if provided. `interface` - Specifies the name or index of the network interface. `rr` - Sets the refresh interval, in seconds, for updating interface statistics. `level` - Sets the detail level for output.  - `normal`: Shows one line per interface (default if no interface is specified).  - `verbose`: Displays detailed information (default if an interface is specified). `store` - Chooses which interfaces to display:  - `active`: Shows currently active interfaces (default).  - `persistent`: Shows interfaces saved for future use. |
| interface `ipv6 show ipstats` | Displays the IPv6 statistics information. `rr` - Specifies the refresh interval, in seconds, for updating IP statistics. |
| interface `ipv6 show joins` | Shows IPv6 multicast groups joined on one or more interfaces. If no interface is specified, multicast groups for all interfaces are displayed. `interface` - Specifies the name or index of the network interface. `level` - Sets the output detail level:  - `normal`: Shows one line per interface (default if no interface is specified).  - `verbose`: Displays detailed information (default if an interface is specified). |
| interface `ipv6 show neighbors` | Displays neighbor cache entries for IPv6 interfaces. If you specify an interface, only its cache is shown. If you also specify a subinterface, only entries for that subinterface are displayed. If you provide an address, only the entry for that specific neighbor is shown. `interface` - The name or index of the network interface. `address` - The IPv6 address of the neighbor. `subinterface` - The LUID of the subinterface. `level` - Specifies the output detail:  - `normal`: Shows one line per subinterface (default if no subinterface is given).  - `verbose`: Shows extra details (default if a subinterface is given). `store` - Chooses which interfaces to display:  - `active`: Shows currently active interfaces (default).  - `persistent`: Shows interfaces saved for future use. |
| interface `ipv6 show offload` | Displays the offload information of a specific interface or interfaces. `name` - Specifies the interface name or index. |
| interface `ipv6 show potentialrouters` | Lists all potential routers detected by the system, or only those associated with a specified interface if provided. `interface` - The name or index of the network interface. |
| interface `ipv6 show prefixpolicies` | Displays the prefix policy table, which determines how source and destination IPv6 addresses are selected for network connections. `store` - Specifies which set of prefix policies you want to view:  - `active`: Shows currently active interfaces (default).  - `persistent`: Shows interfaces saved for future use. |
| interface `ipv6 show privacy` | Displays the current IPv6 privacy settings. `store` - Specifies which configuration store to use when displaying privacy settings:  - `active`: Shows currently active interfaces (default).  - `persistent`: Shows interfaces saved for future use. |
| interface `ipv6 show route` | Shows entries in the route table. `level` - Specifies the detail of route information to display:  - `normal`: Shows standard routes (default).  - `verbose`: Includes loopback routes. `store` - Selects which route table to display. Use `active` for current stack information (default), or `persistent` for saved configuration. |
| interface `ipv6 show siteprefixes` | Displays the current IPv6 site prefix table. |
| interface `ipv6 show slaacsecretkey` | Displays the RFC 7217 secret key used for IPv6 SLAAC privacy when the privacy level is set to 2. `store` - Specifies which key to display:  - `active`: Shows the key currently in use by the stack (default).  - `persistent`: Shows the key saved for future use. |
| interface `ipv6 show subinterfaces` | Shows information about all subinterfaces, or about all subinterfaces on a specified interface if provided. `interface` - Specifies the interface name or index. `subinterface` - Specifies the LUID of the subinterface, used only for interfaces with multiple subinterfaces. `level` - Sets the output detail:  - `normal`: Shows one line per subinterface (default if no subinterface is specified).  - `verbose`: Displays detailed information for each subinterface (default if a subinterface is specified). `store` - Selects which subinterfaces to display:  - `active`: Shows currently active subinterfaces (default).  - `persistent`: Shows persistent subinterfaces. |
| interface `ipv6 show tcpstats` | Displays the TCP connection statistics. `rr` - Specifies the refresh interval, in seconds, for updating TCP statistics information. |
| interface `ipv6 show teredo` | Displays the current configuration and operational status of the Teredo tunneling protocol. |
| interface `ipv6 show tfofallback` | Displays the current status and statistics for TCP Fast Open (TFO) fallback on IPv6 interfaces. This helps determine if TFO is being used or if connections are falling back to standard TCP. |
| interface `ipv6 show udpstats` | Displays the UDP connection statistics. `rr` - Sets the refresh interval, in seconds, for displaying UDP statistics information. |

### interface isatap

| Command | Description |
| --- | --- |
| interface `isatap set router` | Configures the ISATAP router settings. `name` - Specifies the ISATAP router name or use `default` for the system default. `state` - Sets the router name resolution state:  - `enabled`: Enables router name resolution, allowing the system to resolve the ISATAP router name to an IPv6 address.  - `disabled`: Disables router name resolution, preventing the system from resolving the ISATAP router name.  - `default`: Restores the router name resolution state to the system default setting. `interval` - Sets the router name resolution interval in minutes. |
| interface `isatap set state` | Configures the operational state of the ISATAP service. `state` - Specifies the ISATAP service mode:  - `enabled`: Enables the ISATAP service and configures a link-local address on each ISATAP interface. Additional addresses may be assigned by the ISATAP server.  - `disabled`: Disables the ISATAP service. No ISATAP interfaces are created.  - `default`: Attempts to contact the ISATAP server. If unreachable, no addresses are configured on the ISATAP interface. |
| interface `isatap show router` | Displays information about the configured ISATAP router. |
| interface `isatap show state` | Displays the current operational state of the ISATAP service. |

### interface portproxy

| Command | Description |
| --- | --- |
| interface `portproxy add v4tov4` | Adds a proxy rule to listen on an IPv4 address and port, forwarding incoming TCP connections to another IPv4 address and port. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `connectaddress` - The IPv4 address, or hostname, to which incoming connections are forwarded. `connectport` - The IPv4 TCP port number (1-65535) or service name on the destination address. `listenaddress` - The local IPv4 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy add v4tov6` | Adds a proxy rule to listen on an IPv4 address and port, forwarding incoming TCP connections to an IPv6 address and port. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `connectaddress` - The IPv6 address, or hostname, to which incoming connections are forwarded. `connectport` - The IPv6 TCP port number (1-65535) or service name on the destination address. `listenaddress` - The local IPv4 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy add v6tov4` | Adds a proxy rule to listen on an IPv6 address and port, forwarding incoming TCP connections to an IPv4 address and port. `listenport` - The IPv6 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `connectaddress` - The IPv4 address, or hostname, to which incoming connections are forwarded. `connectport` - The IPv4 TCP port number (1-65535) or service name on the destination address. `listenaddress` - The local IPv6 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy add v6tov6` | Adds a proxy rule to listen on an IPv6 address and port, forwarding incoming TCP connections to another IPv6 address and port. `connectaddress` - The IPv6 address, or hostname, to which incoming connections are forwarded. `connectport` - The IPv6 TCP port number (1-65535) or service name on the destination address. `listenaddress` - The local IPv6 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy delete v4tov4` | Deletes a proxy rule that listens on an IPv4 address and port, forwarding TCP connections to another IPv4 address and port. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `listenaddress` - The local IPv6 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy delete v4tov6` | Deletes a proxy rule that listens on an IPv4 address and port, forwarding TCP connections to an IPv6 address and port. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `listenaddress` - The local IPv6 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy delete v6tov4` | Deletes a proxy rule that listens on an IPv6 address and port, forwarding TCP connections to an IPv4 address and port. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `listenaddress` - The local IPv6 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy delete v6tov6` | Deletes a proxy rule that listens on an IPv6 address and port, forwarding TCP connections to another IPv6 address and port. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `listenaddress` - The local IPv6 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy reset` | Resets all port proxy rules and restores the port proxy configuration to its default state. |
| interface `portproxy set v4tov4` | Updates an existing proxy rule that listens on an IPv4 address and port, forwarding TCP connections to another IPv4 address and port. Use this to change the destination or listening parameters for a v4-to-v4 proxy. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `connectaddress` - The IPv4 address, or hostname, to which incoming connections are forwarded. `connectport` - The IPv4 TCP port number (1-65535) or service name on the destination address. `listenaddress` - The local IPv4 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy set v4tov6` | Updates an existing proxy rule that listens on an IPv4 address and port, forwarding TCP connections to an IPv6 address and port. Use this to modify the forwarding details for a v4-to-v6 proxy. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `connectaddress` - The IPv4 address, or hostname, to which incoming connections are forwarded. `connectport` - The IPv4 TCP port number (1-65535) or service name on the destination address. `listenaddress` - The local IPv4 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy set v6tov4` | Updates an existing proxy rule that listens on an IPv6 address and port, forwarding TCP connections to an IPv4 address and port. Use this to change the destination or listening parameters for a v6-to-v4 proxy. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `connectaddress` - The IPv4 address, or hostname, to which incoming connections are forwarded. `connectport` - The IPv4 TCP port number (1-65535) or service name on the destination address. `listenaddress` - The local IPv4 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy set v6tov6` | Updates an existing proxy rule that listens on an IPv6 address and port, forwarding TCP connections to another IPv6 address and port. Use this to modify the forwarding details for a v6-to-v6 proxy. `listenport` - The IPv4 TCP port number (1-65535) or service name on which the proxy listens for incoming connections. `connectaddress` - The IPv4 address, or hostname, to which incoming connections are forwarded. `connectport` - The IPv4 TCP port number (1-65535) or service name on the destination address. `listenaddress` - The local IPv4 address or hostname to listen on. `protocol` - The protocol to use. Only `tcp` is supported. |
| interface `portproxy show all` | Displays all configured port proxy rules. |
| interface `portproxy show v4tov4` | Displays the configuration details for proxy rules forwarding IPv4 connections to IPv4. |
| interface `portproxy show v4tov6` | Displays the configuration details for proxy rules forwarding IPv4 connections to IPv6. |
| interface `portproxy show v6tov4` | Displays the configuration details for proxy rules forwarding IPv6 connections to IPv4. |
| interface `portproxy show v6tov6` | Displays the configuration details for proxy rules forwarding IPv6 connections to IPv6. |

Note

See the following remarks for the `portproxy` command usage:

- All parameters except `protocol` are required.
- If you omit `listenaddress`, it defaults to `0.0.0.0`.
- Port numbers *must* be valid integers in the range 1-65535.
- Service names (for example, `listenport=MyService`) are resolved using the system's services file, which also applies to `connectport`.

### interface set

| Command | Description |
| --- | --- |
| interface `set interface` | Changes the configuration of a network interface. `name` - The current name of the network interface you want to modify. `admin` - Controls whether the interface is `enabled` or `disabled`. `connect` - Sets the connection state, `connected` or `disconnected`, for non-LAN interfaces. `newname` - Assigns a new name to the interface (LAN only).  You must specify at least one subparameter other than `name`. If you use `connect=CONNECTED`, the interface is enabled even if you also specify `admin=DISABLED`. |

### interface show

| Command | Description |
| --- | --- |
| interface `show interface` | Displays the parameters and status of network interfaces. `name` - Specifies the name of a particular interface to display its current settings. If omitted, information for all interfaces is shown. |

### interface tcp

| Command | Description |
| --- | --- |
| interface `tcp add supplementalport` | Adds a TCP template for a specific source and destination port pair. `template` - Specifies the TCP template to apply:  - `internet`: Configures the port for typical internet-facing scenarios.  - `datacenter`: Optimizes the port for use in a datacenter environment.  - `automatic`: Lets the system choose the most appropriate template based on detected environment or other heuristics.  - `custom`: Allows you to specify your own settings instead of using a predefined template.  - `compat`: Uses compatibility settings, typically for legacy systems or applications that require older networking behaviors. `localport` - Sets the source port. Use `*` for all ports or specify a port number. `remoteport` - Sets the destination port. Use `*` for all ports or specify a port number. |
| interface `tcp add supplementalsubnet` | Adds a TCP template filter for traffic destined to a specific subnet. `template` - Specifies the TCP template to apply:  - `internet`: Configures the port for typical internet-facing scenarios.  - `datacenter`: Optimizes the port for use in a datacenter environment.  - `automatic`: Lets the system choose the most appropriate template based on detected environment or other heuristics.  - `custom`: Allows you to specify your own settings instead of using a predefined template.  - `compat`: Uses compatibility settings, typically for legacy systems or applications that require older networking behaviors. `family` - Sets the address family, either `ipv4` or `ipv6`. `address` - Specifies the subnet address in IPv4 or IPv6 notation, optionally followed by a prefix length. |
| interface `tcp delete supplementalport` | Removes the specified port entry from the TCP supplemental filter table. `localport` - Specifies the source port to remove. Use `*` to match all ports or provide a specific port number. `remoteport` - Specifies the destination port to remove. Use `*` to match all ports or provide a specific port number. |
| interface `tcp delete supplementalsubnet` | Removes a TCP template filter for a specific subnet. `family` - Specifies the address family, either `ipv4` or `ipv6`. `address` - Specifies the subnet address in IPv4 or IPv6 notation, optionally followed by a prefix length. |
| interface `tcp reload` | Reloads persisted TCP configuration state from disk. This is an experimental command and **isn't** intended for production use. **Don't use**. |
| interface `tcp rundown` | Forces a connection rundown on all active TCP trace sessions. |
| interface `tcp set global` | Configures system-wide TCP settings that apply to all network connections. `rss` - Sets receive-side scaling (RSS):  - `disabled`: Disables RSS.  - `enabled`: Enables RSS.  - `default`: Restores the system default. `autotuninglevel` - Sets how the TCP receive window automatically adjusts:  - `disabled`: Keeps the receive window fixed at its default size.  - `highlyrestricted`: Allows limited growth of the receive window, conservatively.  - `restricted`: Allows some growth, but with restrictions in certain cases.  - `normal`: Lets the receive window expand for most network conditions.  - `experimental`: Enables maximum growth for testing or unusual scenarios. `ecncapability` - Turns on ECN (Explicit Congestion Notification) (`enabled`) or off (`disabled`). Use `default` to reset to the system setting. `timestamps` - Controls the use of TCP timestamps:  - `disabled`: Disables timestamps.  - `enabled`: Negotiates timestamps for outgoing connections and enables them for incoming if the peer supports it.  - `allowed`: Enables timestamps for incoming connections if the peer supports it (default). `initialrto` - Sets the initial timeout (in milliseconds) for TCP SYN retransmissions. Default is `3000`. `rsc` - Enables (`enabled`) or disables (`disabled`) receive segment coalescing. Use `default` to restore the system setting. `nonsackrttresiliency` - Enables (`enabled`) or disables (`disabled`) round-trip time resiliency for clients that don't support SACK. Default is `disabled`. `maxsynretransmissions` - Sets how many times TCP retransmits SYN packets when trying to connect. Default is `2`. `fastopen` - Enables (`enabled`) or disables (`disabled`) TCP Fast Open. Use `default` to restore the system setting. `fastopenfallback` - Enables (`enabled`) or disables (`disabled`) fallback behavior for TCP Fast Open. Use `default` to restore the system setting. `hystart` - Enables (`enabled`) or disables (`disabled`) the HyStart algorithm for slow start. Use `default` to restore the system setting. `prr` - Enables (`enabled`) or disables (`disabled`) the Proportional Rate Reduction algorithm. Use `default` to restore the system setting. `pacingprofile` - Controls when TCP packet pacing is used:  - `off`: Disables pacing.  - `initialwindow`: Paces only the initial congestion window.  - `slowstart`: Paces during slow start.  - `always`: Pacing is always enabled.  - `default`: Same as `off`. |
| interface `tcp set heuristics` | Configures TCP heuristics for all connections. `wsh` - This setting isn't used and has no effect. `forcews` - Controls force window scaling on retransmit:  - `disabled`: Disables forced window scaling.  - `enabled`: Enables forced window scaling.  - `default`: Restores the window scaling to the system default (enabled). |
| interface `tcp set security` | Sets the TCP security parameters, including memory pressure protection (MPP). Use `mpp` to enable or disable MPP globally or for a specific port range. If no port range is specified, the setting applies globally. Port range settings are effective only when MPP is enabled system-wide. `mpp` - Controls memory pressure protection:  - `disabled`: Disables MPP.  - `enabled`: Enables MPP.  - `default`: Restores to the system default. `startport` - Sets the starting port number (1-65535) for the port range. `numberofports` - Specifies how many ports to include, starting from `startport`. `profiles` - Controls profile usage for memory pressure protection:  - `disabled`: Disables profile usage.  - `enabled`: Enables profile usage.  - `default`: Restores the system default. |
| interface `tcp set supplemental` | Configures TCP supplemental template settings for specific port or subnet filters. Use this command to fine-tune TCP behavior for different network scenarios. If only the `template` parameter is specified, the default global template is modified. If additional parameters are included, the specified template is updated with those values. When setting `minrto`, ensure `delayedacktimeout` is less than `minrto`. For best results, enable both `rack` and `taillossprobe` together to improve loss recovery. `template` - Specifies the TCP template to apply:  - `internet`: Configures the port for typical internet-facing scenarios.  - `datacenter`: Optimizes the port for use in a datacenter environment.  - `automatic`: Lets the system choose the most appropriate template based on detected environment or other heuristics.  - `custom`: Allows you to specify your own settings instead of using a predefined template.  - `compat`: Uses compatibility settings, typically for legacy systems or applications that require older networking behaviors. `minrto` - Sets the minimum retransmission timeout in milliseconds (20-300 ms). `icw` - Sets the initial congestion window size in multiples of the maximum segment size (2-64 MSS). `congestionprovider` - Selects the congestion control algorithm:  - `none`: No specific algorithm is set.  - `ctcp`: Compound TCP improves throughput on high-speed networks.  - `dctcp`: Data Center TCP, optimized for data center environments.  - `cubic`: Default in many Linux systems, good for high-bandwidth, high-latency networks.  - `bbr2`: Bottleneck Bandwidth and Round-trip propagation time, aims for high throughput and low latency.  - `default`: Uses the system’s default algorithm. `enablecwndrestart` - Enables (`enabled`) or disables (`disabled`) restarting the congestion window after idle periods. Use `default` to use the system’s default behavior. `delayedacktimeout` - Sets the delayed acknowledgment timeout in milliseconds (10-600 ms). `delayedackfrequency` - Sets how many segments are received before sending an ACK (1-255). `rack` - Enables (`enabled`) or disables (`disabled`) Recent Acknowledgment (RACK) time-based loss recovery. Use `default` to use the system’s default behavior. `taillossprobe` - Enables (`enabled`) or disables (`disabled`) Tail Loss Probe for faster recovery from packet loss at the end of a transfer. Use `default` to use the system’s default behavior. |
| interface `tcp show global` | Displays global TCP parameters such as autotuning and congestion control. `store` - Selects which configuration to show:  - `active`: Displays the current in-memory configuration (default).  - `persistent`: Displays settings that are saved and persist after reboot. |
| interface `tcp show heuristics` | Displays TCP heuristics, which are algorithms that adjust TCP behavior based on network conditions. `wsh` - Displays Windows Scaling heuristics. `forcews` - Displays forced window scaling settings. |
| interface `tcp show rscstats` | Displays Receive Segment Coalescing (RSC) statistics for a specified network interface. `interface` - The name or index of the network interface. |
| interface `tcp show security` | Displays TCP security settings such as SYN attack protection. `store` - Selects the level of security to show:  - `active`: Displays the current in-memory configuration (default).  - `persistent`: Displays settings that are saved and persist after reboot. |
| interface `tcp show supplemental` | Displays the current TCP supplemental template settings. If no parameters are specified, the default global TCP template is shown. If a `template=` parameter is provided, details for that specific template are displayed. `template` - Specifies the TCP template to display:  - `automatic`: Uses system-selected settings based on environment.  - `datacenter`: Optimized for datacenter workloads.  - `internet`: Optimized for typical internet scenarios.  - `compat`: Provides legacy compatibility settings.  - `custom`: Shows user-defined custom settings. |
| interface `tcp show supplementalports` | Displays which ports are using supplemental TCP settings. `level` - Sets the output detail:  - `normal`: Displays basic information for supplemental ports.  - `verbose`: Displays detailed information for supplemental ports. |
| interface `tcp show supplementalsubnets` | Displays which subnets are using supplemental TCP settings. `level` - Sets the output detail:  - `normal`: Displays basic information for supplemental subnets.  - `verbose`: Displays detailed information for supplemental subnets. |

### interface teredo

| Command | Description |
| --- | --- |
| interface `teredo set state` | Configures the Teredo operational state. Use `default` for any parameter to restore its system default. The `type=server` option is available only on Windows Server editions. `type` - Specifies the Teredo mode:  - `disabled`: Turns off the Teredo service.  - `client`: Enables the Teredo service on the client.  - `enterpriseclient`: Skips managed network detection.  - `natawareclient`: Enables Teredo client detection and NAT type.  - `server`: Enables the server (Windows Server only).  - `default`: Sets to the system default (client). `servername` - Sets the Teredo server name or IPv4 address. `refreshinterval` - Defines the client refresh interval in seconds. `clientport` - Sets the UDP port for the Teredo client. If omitted, the system chooses the port. `servervirtualip` - Specifies the IPv4 address for the server's virtual IP (not used in client mode). |
| interface `teredo show state` | Displays the current configuration and operational status of the Teredo tunneling protocol. |

### interface udp

| Command | Description |
| --- | --- |
| interface `udp reset` | Removes all user-configured UDP settings and restores all UDP parameters to their default values. |
| interface `udp set global` | Configures the global UDP offload settings for all network connections. `uro` - Enables (`enabled`), disables (`disabled`), or restores (`default`) UDP Receive Offload (URO), which allows the network adapter to offload UDP *receive* processing from the CPU. `uso` - Enables (`enabled`), disables (`disabled`), or restores (`default`) UDP Segmentation Offload (USO), which allows the network adapter to offload UDP *send* processing from the CPU. |
| interface `udp show global` | Displays the global UDP offload settings for all network connections. `store` - Specifies which configuration to display:  - `active`: Shows the current in-memory settings (default).  - `persistent`: Shows settings that persist after reboot. |

### interface help

| Command | Description |
| --- | --- |
| `help`*or*`?` | Displays a list of commands and their descriptions in the current context. |

## Examples

To enable routing on the 6to4 interface named "MyInterface", run the following command:

```cmd
netsh interface 6to4 set interface name=MyInterface routing=enabled
```

To enable CLAT and allow IPv6 prefix discovery from DNS and RAs, run the following command:

```cmd
netsh interface clat set global permit=enabled pref64fromdns=enabled pref64fromra=enabled
```

To add a new HTTPS tunnel interface as a client with the URL `https://tunnel.example.com`, set its state to enabled and use certificate authentication, run the following command:

```cmd
netsh interface httpstunnel add interface type=client url="https://tunnel.example.com" state=enabled authmode=certificates
```

To modify an existing HTTPS tunnel interface with the URL `https://tunnel.example.com`, set its state to disabled and authentication mode to none, run the following command:

```cmd
netsh interface httpstunnel set interface url="https://tunnel.example.com" state=disabled authmode=none
```

To add the IPv4 address 192.168.1.10 with subnet mask 255.255.255.0 as a unicast address on the interface "Ethernet", set the default gateway to 192.168.1.1 and make the configuration persistent, run the following command:

```cmd
netsh interface ipv4 add address name="Ethernet" address=192.168.1.10 mask=255.255.255.0 type=unicast gateway=192.168.1.1 store=persistent
```

To delete an excluded TCP port range starting at port 5000 with a total of 20 ports from the active configuration, run the following command:

```cmd
netsh interface ipv4 delete excludedportrange protocol=tcp startport=5000 numberofports=20 store=active
```

To set the IPv4 address source to DHCP on the interface named "Wi-Fi", run the following command:

```cmd
netsh interface ipv4 set address name="Wi-Fi" source=dhcp
```

To set a static IPv4 address of 10.0.0.2 with subnet mask 255.255.255.0 and gateway 10.0.0.1 on the interface "LAN1", and save the settings persistently, run the following command:

```cmd
netsh interface ipv4 set address name="LAN1" source=static address=10.0.0.2 mask=255.255.255.0 gateway=10.0.0.1 store=persistent
```

To enable 6to4 routing and allow site-local addresses, run the following command:

```cmd
netsh interface ipv6 6to4 set routing routing=enabled sitelocals=enabled
```

To add a prefix policy for the IPv6 prefix 2001:db8::/32 with precedence 40 and label "2", and store it persistently, run the following command:

```cmd
netsh interface ipv6 add prefixpolicy prefix=2001:db8::/32 precedence=40 label=2 store=persistent
```

To delete the neighbor entry for address fe80::1 on the interface named "Ethernet" from the active configuration, run the following command:

```cmd
netsh interface ipv6 delete neighbors interface="Ethernet" address=fe80::1 store=active
```

To enable ISATAP state, run the following command:

```cmd
netsh interface ipv6 isatap set state state=enabled
```

To set the DNS IPv6 server address to 2001:4860:4860::8888 on the network interface "Wi-Fi", with static configuration and enable DNS registration with both primary and alternate suffixes, run the following command:

```cmd
netsh interface ipv6 set dnsservers name="Wi-Fi" source=static address=2001:4860:4860::8888 register=both validate=yes
```

To set the IPv6 interface "Ethernet" to disable forwarding, enable advertisement, set MTU to 1400, and make the configuration persistent, run the following command:

```cmd
netsh interface ipv6 set interface interface="Ethernet" forwarding=disabled advertise=enabled mtu=1400 store=persistent
```

To configure Teredo as a client and set the server name to `teredo.example.com`, run the following command:

```cmd
netsh interface ipv6 set teredo type=client servername=teredo.example.com
```

To display IPv6 interface information with verbose details for the interface named "Ethernet", run the following command:

```cmd
netsh interface ipv6 show interfaces interface="Ethernet" level=verbose
```

To set the ISATAP router to `isatap.example.com` and enable the state with a router discovery interval of 30 seconds, run the following command:

```cmd
netsh interface isatap set router name=isatap.example.com state=enabled interval=30
```

To add a TCP port proxy that listens on port 8080 at address 127.0.0.1 and forwards connections to 192.168.1.10 on port 80, run the following command:

```cmd
netsh interface portproxy add v4tov4 listenport=8080 listenaddress=127.0.0.1 connectaddress=192.168.1.10 connectport=80 protocol=tcp
```

To delete an existing v6tov4 TCP port proxy listening on address "2001:db8::1" at port 5000, run the following command:

```cmd
netsh interface portproxy deleted v6tov4 listenport=5000 listenaddress=2001:db8::1 protocol=tcp
```

To disable the interface named "Wi-Fi", run the following command:

```cmd
netsh interface set interface name="Wi-Fi" admin=DISABLED
```

To rename the interface "Ethernet" to "WiredLAN", run the following command:

```cmd
netsh interface set interface name="Ethernet" newname="WiredLAN"
```

To add a supplemental TCP port configuration for the `Internet` template, for local port 443 and *any* remote port, run the following command:

```cmd
netsh interface tcp add supplementalport template=internet localport=443 remoteport=*
```

To delete a supplemental subnet for IPv6 address 2001:db8::/64, run the following command:

```cmd
netsh interface tcp delete supplementalsubnet family=ipv6 address=2001:db8::/64
```

To set the global TCP settings to enable RSS, use normal autotuning level, enable ECN capability, and set maximum SYN retransmissions to 5, run the following command:

```cmd
netsh interface tcp set global rss=enabled autotuninglevel=normal ecncapability=enabled maxsynretransmissions=5
```

To enable TCP heuristics for Windows Scaling Hint and Force Window Scaling, run the following command:

```cmd
netsh interface tcp set heuristics wsh=enabled forcews=enabled
```

To configure Teredo state to `natawareclient` with server name `teredo.example.com`, refresh interval of 60, and client port 3544, run the following command:

```cmd
netsh interface teredo set state type=natawareclient servername=teredo.example.com refreshinterval=60 clientport=3544
```

To enable URO and USO globally, run the following command:

```cmd
netsh interface udp set global uro=enabled uso=enabled
```