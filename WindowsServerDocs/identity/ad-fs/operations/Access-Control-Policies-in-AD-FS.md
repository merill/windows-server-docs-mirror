---
layout: Conceptual
title: Access Control Policies in AD FS Windows Server 2016 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/access-control-policies-in-ad-fs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Access Control Policies in Windows Server 2016 AD FS'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
ms.custom:
- inhenkel
- sfi-image-nochange
locale: en-us
document_id: f036d934-8b6b-b5a4-113b-518c684d357e
document_version_independent_id: eddd6501-43c4-2338-ab48-1b687833caee
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Access-Control-Policies-in-AD-FS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/access-control-policies-in-ad-fs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Access-Control-Policies-in-AD-FS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ced6071c-54f6-4279-5e0c-58fa8756cbd7
---

# Access Control Policies in AD FS Windows Server 2016 | Microsoft Learn

## Access Control Policy Templates in AD FS

Active Directory Federation Services now supports the use of access control policy templates. By using access control policy templates, an administrator can enforce policy settings by assigning the policy template to a group of relying parties (RPs). Administrator can also make updates to the policy template and the changes will be applied to the relying parties automatically if there is no user interaction needed.

## What are Access Control Policy Templates?

The AD FS core pipeline for policy processing has three phases: authentication, authorization and claim issuance. Currently, AD FS administrators have to configure a policy for each of these phases separately. This also involves understanding the implications of these policies and if these policies have inter-dependency. Also, administrators have to understand the claim rule language and author custom rules to enable some simple/common policy (ex. block external access).

What access control policy templates do is replace this old model where administrators have to configure Issuance Authorization Rules using claims language. The old PowerShell cmdlets of issuance authorization rules still apply but it is mutually exclusive of the new model. Administrators can choose either to use the new model or the old model. The new model allows administrators to control when to grant access, including enforcing multi-factor authentication.

Access control policy templates use a permit model. This means by default, no one has access and that access must be explicitly granted. However, this is not just an all or nothing permit. Administrators can add exceptions to the permit rule. For example, an administrator may wish to grant access based on a specific network by selecting this option and specifying the IP address range. But the administrator may add and exception, for instance, the administrator may add an exception from a specific network and specify that IP address range.

![Screenshot that shows where to view the Access Control Policies.](media/access-control-policies-in-ad-fs/adfsacp2.png)

## Built-in access control policy templates vs custom access control policy templates

AD FS includes several built-in access control policy templates. These target some common scenarios which have the same set of policy requirements, for example client access policy for Office 365. These templates cannot be modified.

![Screenshot that shows the built-in Access Control Policies.](media/access-control-policies-in-ad-fs/adfsacp3.png)

To provide increased flexibility to address your business needs, administrators can create their own access policy templates. These can be modified after creation and changes to custom policy template will apply to all the RPs which are controlled by those policy templates. To add a custom policy template simply click Add Access Control Policy from within AD FS management.

To create a policy template, an administrator needs to first specify under which conditions a request will be authorized for token issuance and/or delegation. Condition and action options are shown in the table below. Conditions in bold can be further configured by the administrator with different or new values. Admin can also specify exceptions if there is any. When a condition is met, a permit action will not be triggered if there is an exception specified and the incoming request matches the condition specified in the exception.

| Permit Users | Except |
| --- | --- |
| From **specific** network | From **specific** network<br>From **specific** groups<br><br>From devices with **specific** trust levels<br><br>With **specific** claims in the request |
| From **specific** groups | From **specific** network<br>From **specific** groups<br><br>From devices with **specific** trust levels<br><br>With **specific** claims in the request |
| From devices with **specific** trust levels | From **specific** network<br>From **specific** groups<br><br>From devices with **specific** trust levels<br><br>With **specific** claims in the request |
| With **specific** claims in the request | From **specific** network<br>From **specific** groups<br><br>From devices with **specific** trust levels<br><br>With **specific** claims in the request |
| And require multi-factor authentication | From **specific** network<br>From **specific** groups<br><br>From devices with **specific** trust levels<br><br>With **specific** claims in the request |

If an administrator selects multiple conditions, they are of **AND** relationship. Actions are mutually exclusive and for one policy rule you can only choose one action. If admin selects multiple exceptions, they are of an **OR** relationship. A couple of policy rule examples are shown below:

| **Policy** | **Policy rules** |
| --- | --- |
| Extranet access requires MFA<br>All users are permitted | **Rule #1**<br>from **extranet**<br><br>and with MFA<br><br>Permit<br><br>**Rule#2**<br><br>from **intranet**<br><br>Permit |
| External access are not permitted except non-FTE<br>Intranet access for FTE on workplace joined device are permitted | **Rule #1**<br>From **extranet**<br><br>and from **non-FTE** group<br><br>Permit<br><br>**Rule #2**<br><br>from **intranet**<br><br>and from **workplace joined** device<br><br>and from **FTE** group<br><br>Permit |
| Extranet access requires MFA except "service admin"<br>All users are permitted to access | **Rule #1**<br>from **extranet**<br><br>and with MFA<br><br>Permit<br><br>Except **service admin group**<br><br>**Rule #2**<br><br>always<br><br>Permit |
| non-work place joined device accessing from extranet requires MFA<br>Permit AD fabric for intranet and extranet access | **Rule #1**<br>from **intranet**<br><br>And from **AD Fabric** group<br><br>Permit<br><br>**Rule #2**<br><br>from **extranet**<br><br>and from **non-workplace joined** device<br><br>and from **AD Fabric** group<br><br>and with MFA<br><br>Permit<br><br>**Rule #3**<br><br>from **extranet**<br><br>and from **workplace joined** device<br><br>and from **AD Fabric** group<br><br>Permit |

## Parameterized policy template vs non-parameterized policy template

A parameterized policy template is a policy template that has parameters. An Administrator needs to input the value for those parameters when assigning this template to RPs.An administrator cannot make changes to parameterized policy template after it has been created. An example of a parameterized policy is the built-in policy, Permit specific group. Whenever this policy is applied to an RP, this parameter needs to be specified.

![Screenshot that shows an example of a parameterized policy template.](media/access-control-policies-in-ad-fs/adfsacp5.png)

A non-parameterized policy template is a policy template that does not have parameters. An administrator can assign this template to RPs without any input needed and can make changes to a non-parameterized policy template after it has been created. An example of this is the built-in policy, Permit everyone and require MFA.

![Screenshot that shows an example of a non-parameterized policy template.](media/access-control-policies-in-ad-fs/adfsacp4.png)

## How to create a non-parameterized access control policy

To create a non-parameterized access control policy use the following procedure

#### To create a non-parameterized access control policy

1. From AD FS Management on the left select Access Control Policies and on the right click Add Access Control Policy.
2. Enter a name and a description. For example: Permit users with authenticated devices.
3. Under **Permit access if any of the following rules are met**, click **Add**.
4. Under permit, place a check in the box next to **from devices with specific trust level**
5. At the bottom, select the underlined **specific**
6. From the window that pops-up, select **authenticated** from the drop-down. Click **Ok**.

    ![Screenshot that shows how to select the device trust level.](media/access-control-policies-in-ad-fs/adfsacp6.png)
7. Click **Ok**. Click **Ok**.

    ![Screenshot that shows how to accept the policy change.](media/access-control-policies-in-ad-fs/adfsacp7.png)

## How to create a parameterized access control policy

To create a parameterized access control policy use the following procedure

#### To create a parameterized access control policy

1. From AD FS Management on the left select Access Control Policies and on the right click Add Access Control Policy.
2. Enter a name and a description. For example: Permit users with a specific claim.
3. Under **Permit access if any of the following rules are met**, click **Add**.
4. Under permit, place a check in the box next to **with specific claims in the request**
5. At the bottom, select the underlined **specific**
6. From the window that pops-up, select **Parameter specified when the access control policy is assigned**. Click **Ok**.

    ![Screenshot that shows the Parameter specified when the access control policy is assigned option.](media/access-control-policies-in-ad-fs/adfsacp8.png)
7. Click **Ok**. Click **Ok**.

    ![Screenshot that shows how to accept the selected option.](media/access-control-policies-in-ad-fs/adfsacp9.png)

## How to create a custom access control policy with an exception

To create a access control policy with an exception use the following procedure.

#### To create a custom access control policy with an exception

1. From AD FS Management on the left select Access Control Policies and on the right click Add Access Control Policy.
2. Enter a name and a description. For example: Permit users with authenticated devices but not managed.
3. Under **Permit access if any of the following rules are met**, click **Add**.
4. Under permit, place a check in the box next to **from devices with specific trust level**
5. At the bottom, select the underlined **specific**
6. From the window that pops-up, select **authenticated** from the drop-down. Click **Ok**.
7. Under except, place a check in the box next to **from devices with specific trust level**
8. At the bottom under except, select the underlined **specific**
9. From the window that pops-up, select **managed** from the drop-down. Click **Ok**.
10. Click **Ok**. Click **Ok**.

    ![Screenshot that shows the Screen Editor dialog box.](media/access-control-policies-in-ad-fs/adfsacp10.png)

## How to create a custom access control policy with multiple permit conditions

To create a access control policy with multiple permit conditions use the following procedure

#### To create a parameterized access control policy

1. From AD FS Management on the left select Access Control Policies and on the right click Add Access Control Policy.
2. Enter a name and a description. For example: Permit users with a specific claim and from specific group.
3. Under **Permit access if any of the following rules are met**, click **Add**.
4. Under permit, place a check in the box next to **from a specific group** and **with specific claims in the request**
5. At the bottom, select the underlined **specific** for the first condition, next to groups
6. From the window that pops-up, select **Parameter specified when the policy is assigned**. Click **Ok**.
7. At the bottom, select the underlined **specific** for the second condition, next to claims
8. From the window that pops-up, select **Parameter specified when the access control policy is assigned**. Click **Ok**.
9. Click **Ok**. Click **Ok**.

![access control policies](media/access-control-policies-in-ad-fs/adfsacp12.png)

## How to assign an access control policy to a new application

Assigning an access control policy to a new application is pretty straight forward and has now been integrated into the wizard for adding an RP. From the Relying Party Trust Wizard you can select the access control policy that you wish to assign. This is a requirement when creating a new relying party trust.

![Screenshot that shows the Choose Access Control Policy screen.](media/access-control-policies-in-ad-fs/adfsacp13.png)

## How to assign an access control policy to an existing application

Assigning an access control policy to a existing application simply select the application from Relying Party Trusts and on the right click **Edit Access Control Policy**.

![Screenshot that shows the Retrying Party Trusts application.](media/access-control-policies-in-ad-fs/adfsacp14.png)

From here you can select the access control policy and apply it to the application.

![Screenshot that shows how to edit the Access Control Policy.](media/access-control-policies-in-ad-fs/adfsacp15.png)