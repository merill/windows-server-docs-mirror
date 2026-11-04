---
layout: Conceptual
title: Deploy Claims Across Forests (Demonstration Steps) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/deploy-claims-across-forests--demonstration-steps-
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Deploy Claims Across Forests (Demonstration Steps)'
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c8418724-2b56-cd2d-01b2-0513e7fa4b23
document_version_independent_id: 009d5ab1-4c0b-1723-d647-4f0c77337dd9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Deploy-Claims-Across-Forests--Demonstration-Steps-.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/deploy-claims-across-forests--demonstration-steps-
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Deploy-Claims-Across-Forests--Demonstration-Steps-.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: d2880cb1-2ad1-a230-4b09-3097da9950a4
---

# Deploy Claims Across Forests (Demonstration Steps) | Microsoft Learn

In this topic, we'll cover a basic scenario that explains how to configure claims transformations between trusting and trusted forests. You will learn how claims transformation policy objects can be created and linked to the trust on the trusting forest and the trusted forest. You will then validate the scenario.

## Scenario overview

Adatum Corporation provides financial services to Contoso, Ltd. Each quarter, Adatum accountants copy their account spreadsheets to a folder on a file server located at Contoso, Ltd. There is a two-way trust set up from Contoso to Adatum. Contoso, Ltd. wants to protect the share so that only Adatum employees can access the remote share.

In this scenario:

1. [Set up the prerequisites and the test environment](deploy-claims-across-forests--demonstration-steps-#BKMK_1.1)
2. [Set up claims transformation on trusted forest (Adatum)](deploy-claims-across-forests--demonstration-steps-#BKMK_3)
3. [Set up claims transformation in the trusting forest (Contoso)](deploy-claims-across-forests--demonstration-steps-#BKMK_4)
4. [Validate the scenario](deploy-claims-across-forests--demonstration-steps-#BKMK_5)

## Set up the prerequisites and the test environment

The test configuration involves setting up two forests: Adatum Corporation and Contoso, Ltd, and having a two-way trust between Contoso and Adatum. "adatum.com" is the trusted forest and "contoso.com" is the trusting forest.

The claims transformation scenario demonstrates transformation of a claim in the trusted forest to a claim in the trusting forest. To do this, you need to set up a new forest called adatum.com and populate the forest with a test user with a company value of 'Adatum'. You then have to set up a two-way trust between contoso.com and adatum.com.

Important

When setting up the Contoso and Adatum forests, you must ensure that both the root domains are at the Windows Server 2012 Domain Functional Level for claims transformation to work.

You need to set up the following for the lab. These procedures are explained in detail in [Appendix B: Setting Up the Test Environment](appendix-b--setting-up-the-test-environment)

You need to implement the following procedures to set up the lab for this scenario:

1. [Set Adatum as trusted forest to Contoso](appendix-b--setting-up-the-test-environment)
2. [Create the 'Company' claim type on Contoso](appendix-b--setting-up-the-test-environment#BKMK_2.8)
3. [Enable the 'Company' resource property on Contoso](appendix-b--setting-up-the-test-environment#BKMK_2.55)
4. [Create the central access rule](appendix-b--setting-up-the-test-environment#BKMK_2.9)
5. [Create the central access policy](appendix-b--setting-up-the-test-environment#BKMK_2.10)
6. [Publish the new policy through Group Policy](appendix-b--setting-up-the-test-environment#BKMK_2.11)
7. [Create the Earnings folder on the file server](appendix-b--setting-up-the-test-environment#BKMK_2.12)
8. [Set classification and apply the central access policy on the new folder](appendix-b--setting-up-the-test-environment#BKMK_2.13)

Use the following information to complete this scenario:

| Objects | Details |
| --- | --- |
| Users | Jeff Low, Contoso |
| User claims on Adatum and Contoso | ID: ad://ext/Company:ContosoAdatum,<br>Source attribute: company<br><br>Suggested values: Contoso, Adatum **Important:** You must set the ID on the 'Company' claim type on both Contoso and Adatum to be the same for the claims transformation to work. |
| Central access rule on Contoso | AdatumEmployeeAccessRule |
| Central access policy on Contoso | Adatum Only Access Policy |
| Claims Transformation policies on Adatum and Contoso | DenyAllExcept Company |
| File folder on Contoso | D:\EARNINGS |

## Set up claims transformation on trusted forest (Adatum)

In this step you create a transformation policy in Adatum to deny all claims except 'Company' to pass to Contoso.

The Active Directory module for Windows PowerShell provides the **DenyAllExcept** argument, which drops everything except the specified claims in the transformation policy.

To set up a claims transformation, you need to create a claims transformation policy and link it between the trusted and trusting forests.

### Create a claims transformation policy in Adatum

##### To create a transformation policy Adatum to deny all claims except 'Company'

1. Sign in to the domain controller, adatum.com as Administrator with the password **pass@word1**.
2. Open an elevated command prompt in Windows PowerShell, and type the following:

    ```
    New-ADClaimTransformPolicy `
    -Description:"Claims transformation policy to deny all claims except Company"`
    -Name:"DenyAllClaimsExceptCompanyPolicy" `
    -DenyAllExcept:company `
    -Server:"adatum.com" `
    
    ```

### Set a claims transformation link on Adatum's trust domain object

In this step, you apply the newly created claims transformation policy on Adatum's trust domain object for Contoso.

##### To apply the claims transformation policy

1. Sign in to the domain controller, adatum.com as Administrator with the password **pass@word1**.
2. Open an elevated command prompt in Windows PowerShell, and type the following:

    ```
    
      Set-ADClaimTransformLink `
    -Identity:"contoso.com" `
    -Policy:"DenyAllClaimsExceptCompanyPolicy" `
    '"TrustRole:Trusted `
    
    ```

## Set up claims transformation in the trusting forest (Contoso)

In this step you create a claims transformation policy in Contoso (the trusting forest) to deny all claims except 'Company.' You need to create a claims transformation policy and link it to the forest trust.

### Create a claims transformation policy in Contoso

##### To create a transformation policy Adatum to deny all except 'Company'

1. Sign in to the domain controller, contoso.com as Administrator with the password **pass@word1**.
2. Open an elevated command prompt in Windows PowerShell and type the following:

    ```
    New-ADClaimTransformPolicy `
    -Description:"Claims transformation policy to deny all claims except company" `
    -Name:"DenyAllClaimsExceptCompanyPolicy" `
    -DenyAllExcept:company `
    -Server:"contoso.com" `
    
    ```

### Set a claims transformation link on Contoso's trust domain object

In this step, you apply the newly created claims transformation policy on the contoso.com trust domain object for Adatum to allow "Company" be passed through to contoso.com. The trust domain object is named adatum.com.

##### To set the claims transformation policy

1. Sign in to the domain controller, contoso.com as Administrator with the password **pass@word1**.
2. Open an elevated command prompt in Windows PowerShell and type the following:

    ```
    
      Set-ADClaimTransformLink
    -Identity:"adatum.com" `
    -Policy:"DenyAllClaimsExceptCompanyPolicy" `
    -TrustRole:Trusting `
    
    ```

## Validate the scenario

In this step you try to access the D:\EARNINGS folder that was set up on the file server FILE1 to validate that the user has access to the shared folder.

#### To ensure that the Adatum user can access the shared folder

1. Sign in to the Client machine, CLIENT1 as Jeff Low with the password **pass@word1**.
2. Browse to the folder \\FILE1.contoso.com\Earnings.
3. Jeff Low should be able to access the folder.

## Additional scenarios for claims transformation policies

Following is a list of additional common cases in claims transformation.

| Scenario | Policy |
| --- | --- |
| Allow all claims that come from Adatum to go through to Contoso Adatum | Code - New-ADClaimTransformPolicy ` -Description:"Claims transformation policy to allow all claims" `-Name:"AllowAllClaimsPolicy" `-AllowAll `-Server:"contoso.com" `Set-ADClaimTransformLink `-Identity:"adatum.com" `-Policy:"AllowAllClaimsPolicy" `-TrustRole:Trusting `-Server:"contoso.com" ` |
| Deny all claims that come from Adatum to go through to Contoso Adatum | Code - New-ADClaimTransformPolicy `-Description:"Claims transformation policy to deny all claims" `-Name:"DenyAllClaimsPolicy" ` -DenyAll `-Server:"contoso.com" `Set-ADClaimTransformLink `-Identity:"adatum.com" `-Policy:"DenyAllClaimsPolicy" `-TrustRole:Trusting `-Server:"contoso.com"` |
| Allow all claims that come from Adatum except "Company" and "Department" to go through to Contoso Adatum | Code - New-ADClaimTransformationPolicy `-Description:"Claims transformation policy to allow all claims except company and department" ` -Name:"AllowAllClaimsExceptCompanyAndDepartmentPolicy" `-AllowAllExcept:company,department `-Server:"contoso.com" `Set-ADClaimTransformLink ` -Identity:"adatum.com" `-Policy:"AllowAllClaimsExceptCompanyAndDepartmentPolicy" ` -TrustRole:Trusting `-Server:"contoso.com" ` |

## See also

- For a list of all Windows PowerShell cmdlets that are available for claims transformation, see [Active Directory PowerShell Cmdlet Reference](/en-us/powershell/module/activedirectory).
- For advanced tasks that involve export and import of DAC configuration information between two forests, use the [Dynamic Access Control PowerShell Reference](/en-us/powershell/module/activedirectory)
- [Deploy Claims Across Forests](deploy-claims-across-forests)
- [Claims Transformation Rules Language](claims-transformation-rules-language)
- [Dynamic Access Control: Scenario Overview](dynamic-access-control--scenario-overview)