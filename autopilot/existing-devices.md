---
layout: Conceptual
title: Windows Autopilot for existing devices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/existing-devices
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Modern desktop deployment with Windows Autopilot enables easily deploying the latest version of Windows to existing devices.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: e65e0e7e-a5ea-755d-031b-e777ca97d2eb
document_version_independent_id: e65e0e7e-a5ea-755d-031b-e777ca97d2eb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/existing-devices.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: existing-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/existing-devices.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: ca7dae4a-7e2f-4e9e-6aaa-cdd5c6ca1912
---

# Windows Autopilot for existing devices | Microsoft Learn

Modern desktop deployment with Windows Autopilot helps easily deploy the latest version of Windows to existing devices. Apps used by the organization can be automatically installed. If Windows user data is managed with OneDrive for work or school, data is synchronized, so users can resume working right away.

**Windows Autopilot for existing devices** allows reimaging and provisioning a Windows device for Windows Autopilot user-driven mode using a single, native Configuration Manager task sequence. The existing device can be on-premises domain-joined. The end result is a Windows device joined to either Microsoft Entra ID or Active Directory (Microsoft Entra hybrid join).

Note

The JSON file for Windows Autopilot for existing devices only supports user-driven Microsoft Entra ID and user-driven hybrid Microsoft Entra Windows Autopilot profiles. Self-deploying and pre-provisioning Windows Autopilot profiles aren't supported with JSON files due to these scenarios requiring TPM attestation.

However, during the Windows Autopilot for existing devices deployment, if the following conditions are true:

- Device is already a Windows Autopilot device before the deployment begins
- Device has a Windows Autopilot profile assigned to it

then the assigned Windows Autopilot profile takes precedence over the JSON file installed by the task sequence. In this scenario, if the assigned Windows Autopilot profile is either a self-deploying or pre-provisioning Windows Autopilot profile, then the self-deploying and pre-provisioning scenarios are supported.

Tip

Using Windows Autopilot for existing devices could be used as a method to convert existing hybrid Microsoft Entra devices into Microsoft Entra devices. Using the setting **Convert all targeted devices to Autopilot** in the Windows Autopilot profile doesn't automatically convert existing hybrid Microsoft Entra device in the assigned groups into a Microsoft Entra device. The setting only registers the devices in the assigned groups for the Windows Autopilot service.

## Requirements

- A currently supported version of Microsoft Configuration Manager current branch.
- Assigned Microsoft Intune licenses.
- Microsoft Entra ID P1 or P2.
- A [supported version of Windows](/en-us/windows/release-health/supported-versions-windows-client) imported into Configuration Manager as an [OS image](/en-us/intune/configmgr/osd/get-started/manage-operating-system-images).
- Enrollment restrictions aren't configured to block personal devices. For more information, see [What are enrollment restrictions?: Blocking personal Windows devices](/en-us/intune/intune-service/enrollment/enrollment-restrictions-set#blocking-personal-windows-devices). 

    Important

    Any devices registered using a .json file during a hybrid join scenario are normally enrolled as a Corporate device.

## Configure the Enrollment Status Page (optional)

If desired, an [enrollment status page](enrollment-status) (ESP) for Windows Autopilot can be set up using Intune.

1. Open the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Device onboarding** | **Enrollment**. Make sure **Windows** is selected at the top and then under **Windows Autopilot**, select **Enrollment Status Page** and [Set up the Enrollment Status Page](/en-us/intune/intune-service/enrollment/windows-enrollment-status).
3. Go to **Microsoft Entra ID** &gt; **Manage** | **Mobility (MDM and WIP)** &gt; **Microsoft Intune** and [enable Windows automatic enrollment](/en-us/intune/intune-service/enrollment/windows-enroll#enable-windows-automatic-enrollment). Configure the MDM user scope for some or all users.

## Install required modules

Note

The PowerShell code snippets in this section were updated in July of 2023 to use the Microsoft Graph PowerShell modules instead of the deprecated AzureAD Graph PowerShell modules. The Microsoft Graph PowerShell modules might require approval of additional permissions in Microsoft Entra ID when they're first used. It was also updated to force using an updated version of the WindowsAutoPilot module. For more information, see [AzureAD](/en-us/powershell/module/azuread/) and [Important: Azure AD Graph Retirement and PowerShell Module Deprecation](https://techcommunity.microsoft.com/t5/microsoft-entra-azure-ad-blog/important-azure-ad-graph-retirement-and-powershell-module/ba-p/3848270).

1. On an internet-connected Windows PC or server, open an elevated Windows PowerShell command window.
2. Enter the following commands to install and import the necessary modules:

    ```powershell
    Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force
    Install-Module -Name WindowsAutopilotIntune -MinimumVersion 5.4.0 -Force
    Install-Module -Name Microsoft.Graph.Groups -Force
    Install-Module -Name Microsoft.Graph.Authentication -Force
    Install-Module -Name Microsoft.Graph.Identity.DirectoryManagement -Force
    
    Import-Module -Name WindowsAutopilotIntune -MinimumVersion 5.4
    Import-Module -Name Microsoft.Graph.Groups
    Import-Module -Name Microsoft.Graph.Authentication
    Import-Module -Name Microsoft.Graph.Identity.DirectoryManagement
    ```
3. Enter the following commands and provide Intune administrative credentials:

    Make sure the specified user account has sufficient administrative rights.

    ```powershell
    Connect-MgGraph -Scopes "Device.ReadWrite.All", "DeviceManagementManagedDevices.ReadWrite.All", "DeviceManagementServiceConfig.ReadWrite.All", "Domain.ReadWrite.All", "Group.ReadWrite.All", "GroupMember.ReadWrite.All", "User.Read"
    ```

    Windows requests the username and password for the account with a standard Microsoft Entra ID form. Type the username and password, and then select **Sign in**.

    ![Windows form to sign in to a Microsoft Entra account.](images/pwd.png)

    The first time Intune Graph APIs are used on a device, it prompts to enable Microsoft Intune PowerShell read and write permissions. To enable these permissions, select **Consent on behalf or your organization** and then **Accept**.

## Get Windows Autopilot profiles for existing devices

Get all the Windows Autopilot profiles available in the Intune tenant, and display them in JSON format:

```powershell
Get-AutopilotProfile | ConvertTo-AutopilotConfigurationJSON
```

See the following sample output:

```powershell
PS C:\> Get-AutopilotProfile | ConvertTo-AutopilotConfigurationJSON
{
    "CloudAssignedTenantId": "1537de22-988c-4e93-b8a5-83890f34a69b",
    "CloudAssignedForcedEnrollment": 1,
    "Version": 2049,
    "Comment_File": "Profile Autopilot Profile",
    "CloudAssignedAadServerData": "{\"ZeroTouchConfig\":{\"CloudAssignedTenantUpn\":\"\",\"ForcedEnrollment\":1,\"CloudAssignedTenantDomain\":\"M365x373186.onmicrosoft.com\"}}",
    "CloudAssignedTenantDomain": "M365x373186.onmicrosoft.com",
    "CloudAssignedDomainJoinMethod": 0,
    "CloudAssignedOobeConfig": 28,
    "ZtdCorrelationId": "7F9E6025-1E13-45F3-BF82-A3E8C5B59EAC"
}
```

Each profile is encapsulated within braces (`{ }`). The previous example displays a single profile.

### JSON file properties

| Property | Type | Required | Description |
| --- | --- | --- | --- |
| **Version** | Number | Optional | The version number that identifies the format of the JSON file. |
| **CloudAssignedTenantId** | GUID | Required | The Microsoft Entra tenant ID that should be used. This property is the GUID for the tenant, and can be found in properties of the tenant. The value shouldn't include braces. |
| **CloudAssignedTenantDomain** | String | Required | The Microsoft Entra tenant name that should be used. For example: `tenant.onmicrosoft.com`. |
| **CloudAssignedOobeConfig** | Number | Required | This property is a bitmap that shows which Windows Autopilot settings were configured.<br>- 1: SkipCortanaOptIn<br>- 2: OobeUserNotLocalAdmin<br>- 4: SkipExpressSettings<br>- 8: SkipOemRegistration<br>- 16: SkipEula |
| **CloudAssignedDomainJoinMethod** | Number | Required | This property specifies whether the device should join Microsoft Entra ID or Active Directory (Microsoft Entra hybrid join).<br>- 0: Microsoft Entra joined<br>- 1: Microsoft Entra hybrid joined |
| **CloudAssignedForcedEnrollment** | Number | Required | Specifies that the device should require Microsoft Entra join and MDM enrollment.<br>- 0: Not required<br>- 1: required |
| **ZtdCorrelationId** | GUID | Required | A unique GUID (without braces) provided to Intune as part of the registration process. This ID is included in the enrollment message as the `OfflineAutopilotEnrollmentCorrelator`. This attribute is present only if enrollment happens on a device registered with Zero Touch Provisioning via offline registration. |
| **CloudAssignedAadServerData** | Encoded JSON string | Required | An embedded JSON string used for branding. It requires enabling Microsoft Entra organization branding. For example:`"CloudAssignedAadServerData": "{\"ZeroTouchConfig\":{\"CloudAssignedTenantUpn\":\"\",\"CloudAssignedTenantDomain\":\"tenant.onmicrosoft.com\"}}` |
| **CloudAssignedDeviceName** | String | Optional | The name automatically assigned to the computer. This name follows the naming pattern convention configured in the Intune Windows Autopilot profile. An explicit name can also be specified. |

## Create the JSON file

Save the Windows Autopilot profile as a JSON file in ASCII or ANSI format. Windows PowerShell defaults to Unicode format. If redirecting output of the commands to a file, also specify the file format. The following PowerShell example saves the file in ASCII format. The Windows Autopilot profiles appear in a subfolder under the folder specified by the `$targetDirectory` variable. By default, the `$targetDirectory` variable is `C:\AutoPilot`, but it can be changed to another location if desired. The subfolder has the name of the Windows Autopilot profile from Intune. If there are multiple Windows Autopilot profiles, each profile has its own subfolder. In each folder, there's a JSON file named **`AutopilotConfigurationFile.json`**

```powershell
Connect-MgGraph -Scopes "Device.ReadWrite.All", "DeviceManagementManagedDevices.ReadWrite.All", "DeviceManagementServiceConfig.ReadWrite.All", "Domain.ReadWrite.All", "Group.ReadWrite.All", "GroupMember.ReadWrite.All", "User.Read"
$AutopilotProfile = Get-AutopilotProfile
$targetDirectory = "C:\Autopilot"
$AutopilotProfile | ForEach-Object {
    New-Item -ItemType Directory -Path "$targetDirectory\$($_.displayName)"
    $_ | ConvertTo-AutopilotConfigurationJSON | Set-Content -Encoding Ascii "$targetDirectory\$($_.displayName)\AutopilotConfigurationFile.json"
}
```

Tip

When the PowerShell cmdlet **Out-File** is used to redirect the JSON output to a file, it uses Unicode encoding by default. This cmdlet might also truncate long lines. Use the **Set-Content** cmdlet with the `-Encoding ASCII` parameter to set the proper text encoding.

Important

The file name has to be `AutopilotConfigurationFile.json` and encoded as ASCII or ANSI.

The profile can also be saved to a text file and edit in Notepad. In Notepad, when choosing **Save as**, select the save as type: **All Files**, and then select **ANSI** for the **Encoding**.

![Save as ANSI encoding in Notepad.](images/notepad.png)

After saving the file, move it to a location for a Microsoft Configuration Manager package source.

Important

The configuration file can only contain one profile. Multiple JSON profile files can be used, but each one must be named `AutopilotConfigurationFile.json`. This requirement is for OOBE to follow the Windows Autopilot experience. To use more than one Windows Autopilot profile, create separate Configuration Manager packages.

Windows OOBE doesn't follow the Windows Autopilot experience if the file is saved with one of the following criteria:

- Unicode encoding.
- UTF-8 encoding.
- A file name other than `AutopilotConfigurationFile.json`.

## Create a package containing the JSON file

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Packages** node.
2. On the ribbon, select **Create Package**.
3. In the Create Package and Program Wizard, enter the following details for the package:

    - *Name*: **Windows Autopilot for existing devices config**
    - Select **This package contains source files**
    - *Source folder*: Specify the UNC network path that contains the `AutopilotConfigurationFile.json` file

    For more information, see [Packages and programs in Configuration Manager](/en-us/intune/configmgr/apps/deploy-use/packages-and-programs).
4. For the program, select the *Program Type*: **Don't create a program**
5. Complete the wizard.

Note

If the user-driven Windows Autopilot profile settings in Intune are changed at a later date, make sure to recreate and update the JSON file. After updating the JSON file, redistribute the associated Configuration Manager package.

## Create a target collection

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Device Collections** node.
2. On the ribbon, select **Create**, and then select **Create Device Collection**. An existing collection can also be used. If using an existing collection, proceed to the Create a task sequence section.
3. In the Create Device Collection Wizard, enter the following **General** details:

    - *Name*: **Windows Autopilot for existing devices collection**
    - *Comment*: Add an optional comment to further describe the collection
    - *Limiting collection*: **All Systems** or if desired, an alternate collection.
4. On the **Membership Rules** page, select **Add Rule**. Specify either a direct or query-based collection rule to add the target Windows devices to the new collection.

    For example, if the hostname of the computer to be wiped and reloaded is `PC-01`, and **Name** is being used as the attribute:

    1. Select **Add Rule**, select **Direct Rule** to open the Create Direct Membership Rule Wizard, and select **Next** on the Welcome page.
    2. On the **Search for Resources** page, enter **PC-01** as the **Value**.
    3. Select **Next**, and select **PC-01** in the **Resources**.
5. Complete the wizard with the default settings.

For more information, see [How to create collections in Configuration Manager](/en-us/intune/configmgr/core/clients/manage/collections/create-collections).

## Create a task sequence

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems** and select the **Task Sequences** node.
2. In the **Home** ribbon, select **Create Task Sequence**.
3. In the **Create new task sequence** page, select the option to **Deploy Windows Autopilot for existing devices**.
4. In the **Task sequence information** page, specify the following information:

    - A name for the task sequence. For example, **Windows Autopilot for existing devices**.
    - Optionally add a description to better describe the task sequence.
    - Select a boot image. For more information on supported boot image versions, see [Support for the Windows ADK in Configuration Manager](/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-adk).
5. In the **Install Windows** page, select the Windows **Image package**. Then configure the following settings:

    - **Image index**: Select either Enterprise, Education, or Professional, as required by the organization.
    - Enable the option to **Partition and format the target computer before installing the operating system**.
    - **Configure task sequence for use with Bitlocker**: If this option is enabled, the task sequence includes the steps necessary to enable BitLocker.
    - **Product key**: If a product key needs to be specified for Windows activation, enter it here.
    - Select one of the following options to configure the local administrator account in Windows:

        - **Randomly generate the local administrator password and disable the account on all support platforms (recommended)**
        - **Enable the account and specify the local administrator password**
6. In the **Install the Configuration Manager client** page, add any necessary Configuration Manager client installation properties for the environment. For example, since the device is a Workgroup device and not domain joined during the Windows Autopilot for existing devices task sequence, the [SMSMP](/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties#smsmp) or [SMSMPLIST](/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties#smsmplist) parameters might be needed to run certain tasks such as the **Install Application** or **Install Software Updates** tasks.
7. The **Include updates** page selects by default the option to **Do not install any software updates**.
8. In the **Install applications** page, applications to install during the task sequence can be selected. However, Microsoft recommends that to mirror the signature image approach with this scenario. After the device provisions with Windows Autopilot, apply all applications and configurations from Microsoft Intune or Configuration Manager co-management. This process provides a consistent experience between users receiving new devices and those using Windows Autopilot for existing devices.
9. In the **System Preparation** page, select the package that includes the Windows Autopilot configuration file. By default, the task sequence restarts the computer after it runs Windows Sysprep. The option to **Shutdown computer after this task sequence completes** can also be selected. This option allows preparation of a device and then delivery to a user for a consistent Windows Autopilot experience.
10. Complete the wizard.

The Windows Autopilot for existing devices task sequence results in a device joined to Microsoft Entra ID.

Note

For Windows Autopilot for existing devices task sequence, the **Create Task Sequence Wizard** purposely skips configuring and adding the **Apply Network Settings** task. If the **Apply Network Settings** task isn't specified in a task sequence, it uses Windows default behavior, which is to join a workgroup.

The Windows Autopilot for existing devices task sequence runs the **Prepare Windows for capture** step, which uses the Windows System Preparation Tool (Sysprep). If the device is joined to a domain, Sysprep fails, so therefore the Windows Autopilot for existing devices task sequence joins a workgroup. For this reason, it isn't necessary to add the **Apply Network Settings** task to a Windows Autopilot for existing devices task sequence.

For more information on creating the task sequence, including information on other wizard options, see [Create a task sequence to install an OS](/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-install-an-operating-system).

If the task sequence is viewed, it's similar to the default task sequence to apply an existing OS image. This task sequence includes the following extra steps:

- **Apply Windows Autopilot configuration**: This step applies the Windows Autopilot configuration file from the specified package. It's not a new type of step, it's a **Run Command Line** step to copy the file.
- **Prepare Windows for Capture**: This step runs Windows Sysprep, and has the setting to **Shutdown the computer after running this action**. For more information, see [Prepare Windows for Capture](/en-us/intune/configmgr/osd/understand/task-sequence-steps#prepare-windows-for-capture).

For more information on editing the task sequence, see [Use the task sequence editor](/en-us/intune/configmgr/osd/understand/task-sequence-editor) and [Task sequence steps](/en-us/intune/configmgr/osd/understand/task-sequence-steps).

Note

The **Prepare Windows for Capture** step deletes the `AutopilotConfigurationFile.json` file. For more information and a workaround, see [Modify the task sequence to account for Sysprep command line configuration](tutorial/existing-devices/create-autopilot-task-sequence#modify-the-task-sequence-to-account-for-sysprep-command-line-configuration) and [Windows Autopilot - known issues: Windows Autopilot for existing devices doesn't work](known-issues#windows-autopilot-for-existing-devices-doesnt-work).

To make sure the user's data is backed up before the Windows upgrade, use OneDrive for work or school [known folder move](/en-us/onedrive/redirect-known-folders).

## Distribute content to distribution points

Next distribute all content required for the task sequence to distribution points.

1. Select the **Windows Autopilot for existing devices** task sequence, and in the ribbon select **Distribute Content**.
2. On the **Specify the content destination** page, select **Add** to specify either a **Distribution Point** or **Distribution Point Group**.
3. Specify content destinations that let the devices get the content.
4. After specifying content distribution, complete the wizard.

For more information, see [Manage task sequences to automate tasks](/en-us/intune/configmgr/osd/deploy-use/manage-task-sequences-to-automate-tasks).

## Deploy the Windows Autopilot task sequence

1. Select the **Windows Autopilot for existing devices** task sequence, and in the ribbon select **Deploy**.
2. In the Deploy Software Wizard, specify the following details:

    - **General**

        - *Task Sequence*: **Windows Autopilot for existing devices**
        - *Collection*: **Windows Autopilot for existing devices collection**
    - **Deployment Settings**

        - *Action*: **Install**.
        - *Purpose*: **Available**.
        - *Make available to the following*: **Only Configuration Manager Clients**.

            Note

            Select the option here that is relevant for the context of testing. If the target client doesn't have the Configuration Manager agent or Windows installed, the task sequence needs to be started via PXE or Boot Media.
    - **Scheduling**

        - Set a time for when this deployment becomes available
    - **User Experience**

        - Select **Show Task Sequence progress**
    - **Distribution Points**

        - *Deployment options*: **Download content locally when needed by the running task sequence**
3. Complete the wizard.

## Complete the deployment process

1. On the target Windows device, go to the **Start** menu, enter `Software Center`, and open it.
2. In the Software Library, under **Operating Systems**, select **Windows Autopilot for existing devices**, and then select **Install**.

The task sequence runs and does the following actions:

1. Downloads content.
2. Restarts the device into WinPE.
3. Formats the drive.
4. Installs Windows from the specified OS image.
5. Prepares for Windows Autopilot.
6. After the task sequence completes, the device boots into OOBE for the Windows Autopilot experience:

Note

If devices need to be joined to Active Directory as part of a Microsoft Entra hybrid join scenario, don't do so through the task sequence and the **Apply Network Settings** Task. Instead, create a **Domain Join** device configuration profile. Since there's no Microsoft Entra device object for the computer to do group-based targeting, target the profile to **All Devices**. For more information, see [User-driven mode for Microsoft Entra hybrid join](user-driven#user-driven-mode-for-microsoft-entra-hybrid-join).

## Register the device for Windows Autopilot

Devices provisioned with Windows Autopilot only receive the guided OOBE Windows Autopilot experience on first boot.

After Windows is updated on an existing device, make sure to register the device so it has the Windows Autopilot experience when the PC resets. Automatic registration can be enabled for a device by using the **Convert all targeted devices to Autopilot** setting in the Windows Autopilot profile that is assigned to a group that the device is a member of. For more information, see [Create a Windows Autopilot deployment profile](profiles#create-a-windows-autopilot-deployment-profile).

Also see [Adding devices to Windows Autopilot](add-devices).

Note

- Typically, the target device isn't registered with the Windows Autopilot service. If the device is already registered, the assigned profile takes precedence. The Windows Autopilot for existing devices profile only applies if the online profile times out.

- When the assigned profile is applied, the **enrollmentProfileName** property of the device object in Microsoft Intune and Microsoft Entra ID match the Windows Autopilot profile name.
- When the Windows Autopilot for existing devices profile is applied, the **enrollmentProfileName** property of the device object in Microsoft Intune and Microsoft Entra ID are **OffilineAutoPilotProfile-&lt;ZtdCorrelationId&gt;**.

## How to speed up the deployment process

To speed up the deployment process, see [Windows Autopilot deployment for existing devices: Speed up the deployment process](tutorial/existing-devices/speed-up-deployment) section of the [Windows Autopilot Tutorial](tutorial/autopilot-scenarios).

## Tutorial

For a detailed tutorial on configuring Windows Autopilot for existing devices, see the following article:

[Step by step tutorial for Windows Autopilot deployment for existing devices in Intune and Configuration Manager](tutorial/existing-devices/existing-devices-workflow)