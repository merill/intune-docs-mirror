---
layout: Conceptual
title: Use Remediations to Detect and Fix Support Issues - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/tools/deploy-remediations
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Learn more about Remediations in Microsoft Intune, including what Remediations are and view any prerequisites and licensing requirements. Also, learn how to deploy built-in and custom remediation scripts, and learn how to monitor your scripts.
ms.date: 2025-09-08T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: jocallah
locale: en-us
document_id: abebfd57-b777-3d50-aa70-9377d880c872
document_version_independent_id: abebfd57-b777-3d50-aa70-9377d880c872
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/tools/deploy-remediations.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/tools/deploy-remediations
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/tools/deploy-remediations.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: cd2c24ef-bb7f-1486-9c01-85435be4937b
---

# Use Remediations to Detect and Fix Support Issues - Microsoft Intune | Microsoft Learn

Important

**Proactive Remediations** is renamed to **Remediations** and is available in the Microsoft Intune admin center at **Devices** &gt; **Manage devices** &gt; **Scripts and remediations**. All references to Proactive Remediations in this documentation are replaced with **Remediations**. However, the term Proactive Remediations might still appear in some blogs and other articles.

Remediations help you fix common support issues before end-users notice issues.

In this article, you learn how to:

- Review prerequisites for Remediations
- Deploy a built-in script package
- Deploy a custom script package
- Run a Remediation script on-demand (preview)
- Client policy retrieval and client reporting
- Monitor the script packages
- Export script output
- Monitor remediation status for a device

## About Remediations

Remediations are script packages that can detect and fix common support issues on a user's device before they even realize there's a problem. Remediations can help reduce support calls and tickets. You can create your own script package or deploy a built-in script package.

Each script package consists of a detection script, a remediation script, and metadata. When you use Intune, you can deploy these script packages and see reports on their effectiveness.

## Prerequisites

Whether enrolling devices via Intune or Configuration Manager, Remediation scripting has the following requirements:

- Devices must be Microsoft Entra joined or Microsoft Entra hybrid joined and meet one of the following conditions:

    - Device is Mobile Device Management (MDM) enrolled in Intune and runs Windows Enterprise, Professional, or Education edition.

        **OR**
    - Device is [co-managed](../../configmgr/comanage/overview) running Windows.

### Licensing

Remediations require users of the devices to have one of the following licenses:

- Windows Enterprise E3 or E5 (included in Microsoft 365 F3, E3, or E5)
- Windows Education A3 or A5 (included in Microsoft 365 A3 or A5)
- Windows Virtual Desktop Access (VDA) per user

### Permissions

- For Remediations, the user needs permissions appropriate to their role under the **Device configurations** category. For more information, see [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
- An [Intune Service Administrator](/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles#intune-service-administrator-permissions) is required to confirm licensing requirements before using Remediations for the first time.

### Script requirements

- You can have up to 200 script packages.
- A script package can contain a detection script only or both a detection script and a remediation script.
    - A remediation script only runs if the detection script uses exit code `exit 1`, meaning the issue was detected.
- Ensure the scripts are encoded in UTF-8.
    - In the Settings page of creating a script package, if the **Enforce script signature check** option is enabled, then make sure that the scripts are encoded in UTF-8, not UTF-8 BOM (Byte Order Mark).
- The maximum allowed output size limit is 2,048 characters.
- In the Settings page of creating a script package, if the **Enforce script signature check** option is enabled, then the script runs using the device's PowerShell execution policy. The default execution policy for Windows client computers is **Restricted**. The default execution for Windows Server devices is **RemoteSigned**. For more information, see [PowerShell execution policies](/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies).
    - Scripts built into Remediations are signed and the certificate is added to the **Trusted Publishers** certificate store of the device.
    - When using non-Microsoft scripts that are signed, make sure the certificate is in the **Trusted Publishers** certificate store. As with any certificate, the device must trust the certificate authority.
    - Scripts without **Enforce script signature check** use the **Bypass** execution policy.
- Don't put reboot commands in detection or remediations scripts.
- Don't include any type of sensitive information in scripts (such as passwords)
- Don't include personal data in scripts
- Don't use scripts to collect personal data from devices
- Always follow privacy best practices

## Deploy built-in script packages

There are built-in script packages you can use to get started with Remediations. The **Microsoft Intune Management Extension** service gets the scripts from Intune and runs them. The following built-in script packages just need to be assigned:

- **Update stale Group Policies** – Stale Group Policies can lead to helpdesk tickets related to connectivity and internal resource access.
- **Restart Office Click-to-run service** – When the Click-to-run service is stopped, Office apps fail to start leading to helpdesk calls.

To assign the script package:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Manage devices** &gt; **Scripts and remediations** node, select one of the built-in script packages.
2. Select **Properties**, then next to the **Assignments** heading, select **Edit**.
3. Choose the groups you want to **Assign to** and any **Excluded groups** for the script package.
4. To change the **Scope tags**, select **Edit** then **Select scope tags**.
5. To change the schedule, select the ellipses and choose **Edit** to specify your settings. Select **Apply** to save your changes.
6. When you're done, select **Review + save**.

### Schedule options for assignments

When you configure the assignment of a script package, you can define how often the remediation runs using one of the following **Schedule** options:

- **Once** – Execute the remediation one time only, at a specified date and time.
- **Hourly** – Run the remediation on an hourly basis, with a configurable interval, like every *n* hours. The value must be less than 24 hours.
- **Daily** – Execute the remediation daily at a specified time.

#### Execution behavior:

- Remediations run based on the device's local time, by default. To schedule by Coordinated Universal Time, select **Use UTC**.
- If a scheduled run is missed, the remediation runs when the device is online, and as soon as possible.
- For nonurgent or resource-heavy scripts, use less frequent schedules (such as every seven days) to reduce performance effects on the device.

### Performance recommendations

To reduce the effect of Remediations on device performance:

- Assign only the script packages that each device requires. Every script runs in PowerShell and consumes CPU and battery resources.
- Avoid resource-intensive scripts and frequent schedules. For nonurgent or resource-intensive scripts, use a less frequent schedule, such as every 7 days.
- Configure detection scripts to return stable, actionable results. Avoid values that change with every run, such as timestamps.

## Create and deploy custom script packages

The **Microsoft Intune Management Extension** service gets the scripts from Intune and runs them. The scripts are rerun every 24 hours. You can copy the provided scripts and deploy them, or you can create your own script packages. To deploy script packages, follow the instructions in the next section.

### Copy the provided detection and remediation scripts

1. Copy the scripts from the [PowerShell scripts](ref-remediation-scripts#powershell-scripts-for-remediations)article.
    - Script files whose names start with `Detect` are detection scripts. Remediation scripts start with `Remediate`.
    - For a description of the scripts, see the [Script descriptions](ref-remediation-scripts#script-descriptions).
2. Save each script using the provided name. The name is also in the comments at the top of each script. Ensure the saved scripts are encoded in UTF-8.
    - You can use a different script name, but it won't match the name listed in the [Script descriptions](ref-remediation-scripts#script-descriptions).

### Deploy the script packages

Remediation scripts need to be encoded in UTF-8. Uploading these scripts rather than editing them directly in your browser helps ensure that the script encoding is correct so your devices can execute them.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Manage devices** &gt; **Scripts and remediations**.
2. Choose the **Create script package** button to create a script package.

    [![Screenshot that shows the create script package button in the Remediations page in Microsoft Intune.](media/deploy-remediations/remediations-create.png)](media/deploy-remediations/remediations-create.png#lightbox)
3. In the **Basics** step, give the script package a **Name** and optionally, a **Description**. The **Publisher** field can be edited, but defaults to your name. **Version** can't be edited.
4. On the **Settings** step, upload both the **Detection script file** and the **Remediation script file** by doing the following steps:

    1. Select the folder icon.
    2. Browse to the `.ps1` file.
    3. Choose the file and select **Open** to upload it.

    The detection script must use exit code `exit 1` if the target issue is detected. If there's any other exit code, the remediation script won't run. Including an empty output, since it results in an *issue isn't found* state. Review the [Sample detection script](ref-remediation-scripts#script-descriptions) for an example of exit code usage.

    You need the corresponding detection and remediation script to be in the same package. For example, the `Detect_Expired_User_Certificates.ps1` detection script corresponds with the `Remediate_Expired_User_Certificates.ps1` remediation script.

    [![Screenshot that shows the custom script settings in the Remediations page in Microsoft Intune.](media/deploy-remediations/remediations-script-settings.png)](media/deploy-remediations/remediations-script-settings.png#lightbox)
5. Finish the options on the **Settings** page with the following recommended configurations:

    - **Run this script using the logged-on credentials**: This setting is dependent on the script. For more information, see the [Script descriptions](ref-remediation-scripts#script-descriptions).
    - **Enforce script signature check**: No
    - **Run script in 64-bit PowerShell**: No

    For information about enforcing script signature checks, see Script requirements.
6. Select **Next** then assign any **Scope tags** you need.
7. In the **Assignments** step, select the device groups to which you want to deploy the script package. When you're ready to deploy the packages to your users or devices, you can also use filters. For more information, see [Create filters in Microsoft Intune](../../fundamentals/filters/overview).

    Note

    Don't mix user and device groups across include and exclude assignments.
8. Complete the **Review + Create** step for your deployment.

## Run a remediation script on-demand (preview)

You can use the **Run remediation** device action to run a remediation script on-demand to a single Windows device.

### Prerequisites for running a remediation script on-demand

- Remediations must already be configured before a remediation script can be used on-demand.
- The built-in or custom script packages must be available for users to run a remediation on-demand. However, they don't need to be assigned to a user or device. You can use **Scope tags** to limit which remediation script packages a user can see.
- Users must be Intune Admins or have a role with the **Run remediation** permission (available under **Remote tasks**). During the public preview, the user must also have Organization: Read.
- Devices are online and able to communicate with Intune and [Windows Push Notification Service (WNS)](../../fundamentals/endpoints#windows-push-notification-services-wns-dependencies) during the remote action.
- The [Intune Management Extension](management-extension-windows) must be installed on devices. The installation is done automatically when a Win32 app, PowerShell script, or Remediation is assigned to a user or device.

### How to run a Remediation script on-demand

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Navigate to **Devices** &gt; **By platform** &gt; **Windows** &gt; select a supported device.
3. On the device's **Overview** page, select **...** &gt; **Run remediation (preview).**
4. In the **Run remediation (preview)** pane, select the **Script package** you want to run from the list. Select **View details** to see properties of the script package like detection and remediation script contents, description, and configured settings.
5. To run the remediation on-demand, select **Run remediation**.

Note

- Only a single **Run remediation** device action can be issued at a time for the same device. If you run multiple **Run remediation** device actions in a short period of time to a device, they can overwrite each other.
- The device will not receive the **Run remediation** device action if the device is offline or can't successfully communicate with Intune or Windows Push Notification Service (WNS) when the device action is sent.

## Client policy retrieval and client reporting

The client retrieves policy for Remediation scripts at the following times:

- After a restart of the device or Intune management extension service
- After a user signs into the client
- Once every 8 hours

    - The 8 hour script retrieval schedule is fixed based on when the Intune management extension service starts. User sign-ins don't alter the schedule.

The client reports Remediation information at the following times:

- When a script is set to run once, the results are reported after the script runs.
- Recurring scripts follow a seven day reporting cycle:

    - Within the first six days, the client reports only if a change occurs. The first time the script runs would be considered a change.
    - Every seven days the client sends a report even if there wasn't a change.

## Monitor your script packages

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Manage devices** &gt; **Scripts and remediations**, you can see an overview of your detection and remediation status.

    [![Screenshot that shows the Remediations report overview page in Microsoft Intune.](media/deploy-remediations/remediations-report-overview.png)](media/deploy-remediations/remediations-report-overview.png#lightbox)
2. Select **Device status** to get status details for each device in your deployment.

    [![Screenshot that shows the Remediations device status page in Microsoft Intune.](media/deploy-remediations/remediations-device-status.png)](media/deploy-remediations/remediations-device-status.png#lightbox)

## Export script output

To help you easily analyze returned outputs, use the **Export** option to save the output as a `.csv` file. Exporting the output to a `.csv` file allows you to analyze the returned outputs when Remediations run on devices with issues. Exporting also allows you to share the results with others for more analysis.

## Monitor remediation status for a device

You can view the status of Remediations that are assigned or run on-demand to a device.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Navigate to **Devices** &gt; **By platform** &gt; **Windows** &gt; select a supported device.
3. Select **Remediations** in the **Monitor** section.

## Known Issues

When you apply filters such as "Author" or "Status," or using the **Export** option on the **Remediations** page of **Scripts and remediations**, only the currently loaded script packages are included. To include all scripts, scroll until the full list is loaded.

Note

Device status exports from the Intune admin center for Platform scripts now use the Intune Export API, and CSV column names align with the API schema.