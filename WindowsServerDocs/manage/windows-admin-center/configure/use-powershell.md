---
layout: Conceptual
title: Use PowerShell to manage Windows Admin Center settings | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/configure/use-powershell
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how to use PowerShell to Manage Windows Admin Center Settings and Configuration
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2019-11-21T00:00:00.0000000Z
locale: en-us
document_id: a55e66a4-3641-dca0-f126-5923925dec0c
document_version_independent_id: 84c57a39-31eb-77c3-1b3d-ed43d5a607e0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/configure/use-powershell.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/configure/use-powershell
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/configure/use-powershell.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: dd5cef5d-2ff5-fef7-e834-67ad18fc3ac4
---

# Use PowerShell to manage Windows Admin Center settings | Microsoft Learn

If you have a large organization with multiple Windows Admin Center servers, you can use PowerShell to configure the list of connections and extensions on multiple servers at a time.

## Use PowerShell to import or export your connections (with tags)

```powershell
# Load the module
Import-Module "$env:'Program Files'\WindowsAdminCenter\PowerShellModules\Microsoft.WindowsAdminCenter.ConnectionTools"
# Available cmdlets: Export-WACConnection, Import-WACConnection

# Export connections (including tags) to a .csv file
Export-WACConnection "https://wac.contoso.com" -fileName "WAC-connections.csv"
# Import connections (including tags) from a .csv file
Import-WACConnection "https://wac.contoso.com" -fileName "WAC-connections.csv" -AccessKey "<key string>"
# Import connections (including tags) from .csv files, and remove any connections that are not explicitly in the imported file by using the -prune switch parameter 
Import-WACConnection "https://wac.contoso.com" -fileName "WAC-connections.csv" -AccessKey "<key string>" -prune
```

Important

The `-AccessKey` field is required when importing connections, but it's not required for exporting connections. Your can find your Windows Admin Center access key can be found in the **Advanced** tab in Windows Admin Center settings.

When you use form login authentication to access Windows Admin Center, you need to provide credentials to import and export connections. You can pass credentials by using the following command:

```powershell
# Export connections by using credentials
Export-WACConnection "https://wac.contoso.com" -fileName "WAC-connections.csv" -AccessKey "<key string>" -Credentials (Get-Credential)
# Import connections by using credentials
Import-WACConnection -Endpoint "https://wac.contoso.com" -FileName "WAC-connections.csv" -AccessKey "<key string>" -Credentials (Get-Credential)
```

### CSV file format for importing connections

The format of the CSV file starts with the following four headings, followed by each connection on a new line.

- `name`: The FQDN of the connection.
- `type`: The connection type. For the default connections included with Windows Admin Center, use one of the following strings:

    | Connection type | Connection string |
    | --- | --- |
    | Windows Server | `msft.sme.connection-type.server` |
    | Failover cluster | `msft.sme.connection-type.cluster` |
- `tags`: Pipe-separated tags.
- `groupId`: The column for shared connections. Use the value `global` in this column to make a shared connection.

Note

Modifying the shared connections is limited to gateway administrators. Any user can use PowerShell to modify their personal connection list.

### Example CSV file for importing connections

```
"name","type","tags","groupId"
"myServer.contoso.com","msft.sme.connection-type.server","hyperv"
"myDesktop.contoso.com","msft.sme.connection-type.windows-server","hyperv"
"teamcluster.contoso.com","msft.sme.connection-type.cluster","legacyCluster|WS2016","global"
"myHCIcluster.contoso.com,"msft.sme.connection-type.cluster","myHCIcluster|hyperv|JIT|WS2019"
"teamclusterNode.contoso.com","msft.sme.connection-type.server","legacyCluster|WS2016","global"
"myHCIclusterNode.contoso.com","msft.sme.connection-type.server","myHCIcluster|hyperv|JIT|WS2019"
```

Note

The CSV file is case-sensitive.

## Import RDCMan connections

Use the following script to export saved connections in [RDCMan](https://blogs.technet.microsoft.com/rmilne/2014/11/19/remote-desktop-connection-manager-download-rdcman-2-7/) to a file. You can then import the file into Windows Admin Center and maintain your RDCMan grouping hierarchy by using tags.

1. Copy and paste the following code into your PowerShell session:

    ```powershell
    #Helper function for RdgToWacCsv
    function AddServers {
     param (
     [Parameter(Mandatory = $true)]
     [Xml.XmlLinkedNode]
     $node,
     [Parameter()]
     [String[]]
     $tags,
     [Parameter(Mandatory = $true)]
     [String]
     $csvPath
     )
     if ($node.LocalName -eq 'server') {
         $serverName = $node.properties.name
         $tagString = $tags -join "|"
         Add-Content -Path $csvPath -Value ('"'+ $serverName + '","msft.sme.connection-type.server","'+ $tagString +'"')
     } 
     elseif ($node.LocalName -eq 'group' -or $node.LocalName -eq 'file') {
         $groupName = $node.properties.name
         $tags+=$groupName
         $currNode = $node.properties.NextSibling
         while ($currNode) {
             AddServers -node $currNode -tags $tags -csvPath $csvPath
             $currNode = $currNode.NextSibling
         }
     } 
     else {
         # Node type isn't relevant to tagging or adding connections in Windows Admin Center
     }
     return
    }
    
    <#
    .SYNOPSIS
    Convert an .rdg file from Remote Desktop Connection Manager into a .csv that can be imported into Windows Admin Center, maintaining groups via server tags. This will not modify the existing .rdg file and will create a new .csv file
    
     .DESCRIPTION
     This converts an .rdg file into a .csv that can be imported into Windows Admin Center.
    
     .PARAMETER RDGfilepath
     The path of the .rdg file to be converted. This file will not be modified, only read.
    
     .PARAMETER CSVdirectory
     Optional. The directory you want to export the new .csv file. If it's not provided, the new file is created in the same directory as the .rdg file.
    
     .EXAMPLE
     C:\PS> RdgToWacCsv -RDGfilepath "rdcmangroup.rdg"
     #>
    function RdgToWacCsv {
     param(
         [Parameter(Mandatory = $true)]
         [String]
         $RDGfilepath,
         [Parameter(Mandatory = $false)]
         [String]
         $CSVdirectory
     )
     [xml]$RDGfile = Get-Content -Path $RDGfilepath
     $node = $RDGfile.RDCMan.file
     if (!$CSVdirectory){
         $csvPath = [System.IO.Path]::GetDirectoryName($RDGfilepath) + [System.IO.Path]::GetFileNameWithoutExtension($RDGfilepath) + "_WAC.csv"
     } else {
         $csvPath = $CSVdirectory + [System.IO.Path]::GetFileNameWithoutExtension($RDGfilepath) + "_WAC.csv"
     }
     New-item -Path $csvPath
     Add-Content -Path $csvPath -Value '"name","type","tags"'
     AddServers -node $node -csvPath $csvPath
     Write-Host "Converted $RDGfilepath `nOutput: $csvPath"
    }
    ```
2. To create a CSV file, run the following command:

    ```powershell
    RdgToWacCsv -RDGfilepath "path\to\myRDCManfile.rdg"
    ```
3. Import the resulting CSV file into Windows Admin Center. Tags in the connection list represent your RDCMan grouping hierarchy.

## Manage Windows Admin Center extensions with PowerShell

```powershell
# Add the module to the current session
Import-Module "$env:ProgramFiles\windows admin center\PowerShell\Modules\ExtensionTools"
# Available cmdlets: Get-Feed, Add-Feed, Remove-Feed, Get-Extension, Install-Extension, Uninstall-Extension, Update-Extension

# List feeds
Get-Feed "https://wac.contoso.com"

# Add a new extension feed
Add-Feed -GatewayEndpoint "https://wac.contoso.com" -Feed "\\WAC\our-private-extensions"

# Remove an extension feed
Remove-Feed -GatewayEndpoint "https://wac.contoso.com" -Feed "\\WAC\our-private-extensions"

# List all extensions
Get-Extension "https://wac.contoso.com"

# Install an extension (locate the latest version from all feeds and install it)
Install-Extension -GatewayEndpoint "https://wac.contoso.com" "msft.sme.containers"

# Install an extension (latest version from a specific feed, if the feed is not present, it will be added)
Install-Extension -GatewayEndpoint "https://wac.contoso.com" "msft.sme.containers" -Feed "https://aka.ms/sme-extension-feed"

# Install an extension (install a specific version)
Install-Extension "https://wac.contoso.com" "msft.sme.certificate-manager" "0.133.0"

# Uninstall-Extension
Uninstall-Extension "https://wac.contoso.com" "msft.sme.containers"

# Update-Extension
Update-Extension "https://wac.contoso.com" "msft.sme.containers"
```

Note

You must be gateway administrator to modify Windows Admin Center extensions with PowerShell.

### Additional References

- [Deploy a highly available Windows Admin Center gateway on a cluster](../deploy/high-availability)
- [Deploy a Windows Admin Center gateway in Azure using Cloud Shell](../azure/deploy-wac-in-azure)