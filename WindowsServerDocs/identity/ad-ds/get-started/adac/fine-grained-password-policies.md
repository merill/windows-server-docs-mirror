---
layout: Conceptual
title: Configure fine grained password policies for Active Directory Domain Services in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/adac/fine-grained-password-policies
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to create, view, edit, and delete fine grained password policies in Active Directory Domain Services on Windows Server.
ms.author: roharwoo
author: Orin-Thomas
ms.date: 2025-06-16T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 0062e1aa-fedb-d809-2101-3580b5f03805
document_version_independent_id: 0062e1aa-fedb-d809-2101-3580b5f03805
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/get-started/adac/fine-grained-password-policies.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/get-started/adac/fine-grained-password-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/get-started/adac/fine-grained-password-policies.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 600f91f6-afc9-4cdf-c837-670c2a124b55
---

# Configure fine grained password policies for Active Directory Domain Services in Windows Server | Microsoft Learn

Fine Grained Password Policies provide you with a way to define different password and account lockout policies for different sets of users in a domain. You can use fine grained password policies to specify multiple password policies within a single domain. You can also apply different restrictions for password and account lockout policies to different sets of users in a domain. For example, you can apply stricter settings to privileged accounts and less strict settings to the accounts of other users.

Fine-grained password policies apply only to global security groups and user objects. By default, only members of the Domain Admins group can set fine grained password policies. However, you can also delegate the ability to set these policies to other users.

## Prerequisites

Before you can create fine grained password policies, you need to complete the following prerequisites.

- The domain functional level must be Windows Server 2012 or higher.
- You must be a member of the Domain Admins group.
- You must have either of the following Remote Server Administration Tools (RSAT) installed:

    - Active Directory Administrative Center (ADAC), **or** Active Directory module for Windows PowerShell.

## Create a fine grained password policy

To create a new fine grained password policy, perform the following steps:

# [Active Directory Administrative Center](#tab/adac)
Here's how to create a fine grained password policy using ADAC:

1. Open Active Directory Administrative Center, either from the **Tools** menu of the Server Manager console or by running an elevated PowerShell session and typing **dsac.exe**.
2. If the appropriate target domain isn't selected, choose **Manage**, choose **Add Navigation Nodes**, and select the appropriate target domain in the **Add Navigation Nodes** dialog box and then choose **OK**.
3. In the ADAC navigation pane, open the **System** container, and then choose **Password Settings Container**.
4. In the **Tasks** pane, choose **New**, and then choose **Password Settings**.
5. Fill in or edit fields inside the property page to create a new **Password Settings** object. The **Name** and **Precedence** fields are required.
6. Under **Directly Applies To**, choose **Add**, type the name of the group to which the fine grained password policy, and then choose **OK**.
7. Choose **OK** to submit the creation.

# [PowerShell](#tab/powershell)
Here's how to create a fine grained password policy using the [New-ADFineGrainedPasswordPolicy](/en-us/powershell/module/activedirectory/new-adfinegrainedpasswordpolicy) cmdlet.

1. To open an elevated PowerShell session, right-click on the *Start* button, choose **Windows PowerShell (Admin)**.
2. To create a new fine grained password policy named `PasswordPolicy`, use the following example. Adjust the settings as needed and run the command:

    ```powershell
    $policyParams = @{
        Name = "PasswordPolicy"
        ComplexityEnabled = $true
        LockoutDuration = "00:30:00"
        LockoutObservationWindow = "00:30:00"
        LockoutThreshold = "0"
        MaxPasswordAge = "42.00:00:00"
        MinPasswordAge = "1.00:00:00"
        MinPasswordLength = "7"
        PasswordHistoryCount = "24"
        Precedence = "1"
        ReversibleEncryptionEnabled = $false
        ProtectedFromAccidentalDeletion = $true
    }
    
    New-ADFineGrainedPasswordPolicy @policyParams
    ```
3. Assign the new policy to a group using the [Add-ADFineGrainedPasswordPolicySubject](/en-us/powershell/module/activedirectory/add-adfinegrainedpasswordpolicysubject) cmdlet. For example, to assign the `PasswordPolicy` policy to the `group1` group, run the following command:

    ```powershell
    Add-ADFineGrainedPasswordPolicySubject PasswordPolicy -Subjects group1
    ```

---

## View a resultant set of policies for a user

To view the resultant policy that applies to a specific user, perform the following steps:

# [Active Directory Administrative Center](#tab/adac)
Here's how to view the resultant policy that applies to a specific user using ADAC:

1. Open Active Directory Administrative Center, either from the Tools menu of the Server Manager console or by running an elevated PowerShell session and typing **dsac.exe**.
2. If the appropriate target domain isn't selected, choose **Manage**, choose **Add Navigation Nodes**, and select the appropriate target domain in the **Add Navigation Nodes** dialog box and then choose **OK**.
3. Navigate to the user for whom you wish to view the resultant policy settings.
4. Choose **View Resultant Password Settings** in the **Tasks** pane.
5. Examine the password setting policy and then choose **Cancel**.

# [PowerShell](#tab/powershell)
Here's how to use the [Get-ADUserResultantPasswordPolicy](/en-us/powershell/module/activedirectory/get-aduserresultantpasswordpolicy) cmdlet to view the policy that applies to a specific user.

1. To open an elevated PowerShell session, right-click on the *Start* button, choose **Windows PowerShell (Admin)**.
2. To view the resultant policy that applies to `user1`, run the command. Replace `user1` with the desired user.

    ```powershell
    Get-ADUserResultantPasswordPolicy -Identity test1
    ```

---

## Edit a fine grained password policy

Edit a fine grained password policy using the following steps:

# [Active Directory Administrative Center](#tab/adac)
Here's how to edit a fine grained password policy using ADAC:

1. Open Active Directory Administrative Center, either from the Tools menu of the Server Manager console or by running an elevated PowerShell session and typing **dsac.exe**.
2. If the appropriate target domain isn't selected, choose **Manage**, choose **Add Navigation Nodes**, and select the appropriate target domain in the **Add Navigation Nodes** dialog box and then choose **OK**.
3. In the ADAC **Navigation Pane**, expand **System** and then expand the **Password Settings Container**.
4. Select the fine grained password policy you wish to edit and choose **Properties** in the **Tasks** pane.
5. Modify the settings that you wish to change and choose **OK**.

# [PowerShell](#tab/powershell)
Here's how to use the [Set-ADFineGrainedPasswordPolicy](/en-us/powershell/module/activedirectory/set-adfinegrainedpasswordpolicy) cmdlet to modify an existing policy.

1. Open an elevated PowerShell session, right-click on the *Start* button. Choose **Windows PowerShell (Admin)**.
2. To change the password history setting of the `PasswordPolicy` policy, run the following command. Replace `PasswordPolicy` with the desired policy name.

    ```powershell
    Set-ADFineGrainedPasswordPolicy PasswordPolicy -PasswordHistoryCount:"30"
    ```
3. You can change other settings in the same way. For more information, review the [Set-ADFineGrainedPasswordPolicy](/en-us/powershell/module/activedirectory/set-adfinegrainedpasswordpolicy) reference article.

---

## Delete a fine grained password policy

Perform the following steps to delete a fine grained password policy:

# [Active Directory Administrative Center](#tab/adac)
Here's how to delete a fine grained password policy using ADAC:

1. Open Active Directory Administrative Center, either from the Tools menu of the Server Manager console or by running an elevated PowerShell session and typing **dsac.exe**.
2. If the appropriate target domain isn't selected, choose **Manage**, choose **Add Navigation Nodes**, and select the appropriate target domain in the **Add Navigation Nodes** dialog box and then choose **OK**.
3. In the ADAC Navigation Pane, expand **System** and then expand **Password Settings Container**.
4. Select the fine grained password policy you wish to remove and in the **Tasks** pane choose **Properties**.
5. Clear the **Protect from accidental deletion** checkbox and choose **OK**.
6. Select the fine grained password policy, and in the **Tasks** pane choose **Delete**.
7. Choose **OK** in the confirmation dialog to delete the policy.

# [PowerShell](#tab/powershell)
Here's how to use the [Remove-ADFineGrainedPasswordPolicy](/en-us/powershell/module/activedirectory/remove-adfinegrainedpasswordpolicy) cmdlet to delete a fine grained password policy.

1. Open an elevated PowerShell session by right-clicking on the *Start* button and choosing **Windows PowerShell (Admin)**.
2. Remove deletion protection from the policy by running the following command. Replace `PasswordPolicy` with the desired policy name.

    ```powershell
    Set-ADFineGrainedPasswordPolicy -Identity PasswordPolicy -ProtectedFromAccidentalDeletion $False
    ```
3. To remove the policy, run the following command. Replace `PasswordPolicy` with the desired policy name.

    ```powershell
    Remove-ADFineGrainedPasswordPolicy PasswordPolicy
    ```

---