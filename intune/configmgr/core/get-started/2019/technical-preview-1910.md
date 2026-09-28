---
layout: Conceptual
title: Technical preview 1910 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2019/technical-preview-1910
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn about new features available in the Configuration Manager technical preview branch version 1910.
ms.date: 2019-10-18T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 7f34a75d-52ff-9fe7-baf1-e3d998bb92e4
document_version_independent_id: ac5f31ec-5b62-60db-47be-9bf3e8765c4a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2019/technical-preview-1910.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2019/technical-preview-1910
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2019/technical-preview-1910.md
platformId: 2ec6833f-9747-6d93-17da-b7b589444abe
---

# Technical preview 1910 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1910. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Deploy Microsoft Edge, version 77 and later

The all-new Microsoft Edge is ready for business. You can now deploy [Microsoft Edge, version 77 and later](/en-us/deployedge/) to your users. Admins can pick the Beta or Dev channel, along with a version of the Microsoft Edge client to deploy. Each release incorporates learnings and improvements from our customers and community.

### Prerequisites

The device running the Configuration Manager console needs access to the following endpoints:

| Location | Use |
| --- | --- |
| `https://edgeupdates.azurewebsites.net/api/products?view=enterprise` | Information about releases of Microsoft Edge version 77 and later |
| `http://dl.delivery.mp.microsoft.com` | Content for Microsoft Edge releases, version 77 and later |

Clients targeted with a Microsoft Edge, version 77 and later deployment:

- PowerShell [Execution Policy](/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies)can't be set to Restricted.
    - PowerShell is executed to perform the installation.

### Log files

| Location | Log | Use |
| --- | --- | --- |
| Site server | SMSProv.log | Shows details if the creation of the app or deployment fails. |
| [Varies](../../plan-design/hierarchy/log-files) | PatchDownloader.log | Shows details if the content download fails |
| Client | AppEnforce.log | Shows installation information |

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

Create a Microsoft Edge, version 77 and later application using the built-in application experience, which makes Microsoft Edge easier to manage:

1. In the console, under **Software Library**, there's a new node called **Microsoft Edge Management**.
2. Select **Create Microsoft Edge Application** from either the ribbon, or by right-clicking on the **Microsoft Edge Management** node.

    ![Microsoft Edge Management node right-click action](media/4561024-create-microsoft-edge-application.png)
3. On the **Application Settings** page of the wizard, specify a name, description, and location for the content for the app.
4. On the **Microsoft Edge Settings** page, you select a channel and version to deploy. The Learn More link takes you to the [Microsoft Edge Insiders page](https://www.microsoftedgeinsider.com/).

    ![Microsoft Edge Settings page in the deployment wizard](media/4561024-edge-settings-wizard.png)
5. On the **Deployment** page, decide if you want to deploy the application. If you select **Yes**, you can specify your deployment settings for the application.
6. In **Software Center** on the client device, the user can see and install the application.

    ![Install Microsoft Edge in Software Center](media/4561024-software-center-install-edge.png)

## Include custom configuration baselines as part of compliance policy assessment

You can now add evaluation of custom configuration baselines as a compliance policy assessment rule. When you create or edit a configuration baseline, you have a new option, **Evaluate this baseline as part of compliance policy assessment**. When adding or editing a compliance policy rule, you have a new condition called **Include configured baselines in compliance policy assessment**.

When a user is part of a collection targeted with a compliance policy that includes the rule condition **Include configured baselines in compliance policy assessment**, any baselines with the **Evaluate this baseline as part of compliance policy assessment** option selected that are deployed to the user or the user's device are evaluated for compliance. For example:

- `User1` is part of `User Collection 1`.
- `User1` uses `Device1`, which is in `Device Collection 1` and `Device Collection 2`.
- `Compliance Policy 1` has the **Include configured baselines in compliance policy assessment** rule condition and is deployed to `User Collection 1`.
- `Configuration Baseline 1` has **Evaluate this baseline as part of compliance policy assessment** selected and is deployed to `Device Collection 1`.
- `Configuration Baseline 2` has **Evaluate this baseline as part of compliance policy assessment** selected and is deployed to `Device Collection 2`.

In this scenario, when `Compliance Policy 1` evaluates for `User1` using `Device1`, both `Configuration Baseline 1` and `Configuration Baseline 2` are evaluated too.

- `User1` sometimes uses `Device2`.
- `Device2`is a member of `Device Collection 2` and `Device Collection 3`.
- `Device Collection 3` has `Configuration Baseline 3` deployed to it, but **Evaluate this baseline as part of compliance policy assessment** isn't selected.

When `User1` uses `Device2`, only `Configuration Baseline 2` gets evaluated when `Compliance Policy 1` evaluates.

### Log files

- ComplianceHandler.log
- SettingsAgent.log
- DCMAgent.log
- CIAgent.log

### Known issues

If the compliance policy evaluates a new baseline that has never been evaluated on the client before, it may report non-compliance. This occurs if the baseline evaluation is still running when the compliance is evaluated. To workaround this issue, click **Check compliance** in the **Software Center**.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

#### Prerequisites when the devices are co-managed

- Make sure the [Compliance policies workload](../../../comanage/workloads#compliance-policies) is moved to either Pilot or Intune.
- From Intune's Windows 10 compliance policy, make sure that **Require** is set for [**Configuration Manager Compliance**](../../../../device-security/compliance/ref-windows-settings#configuration-manager-compliance).

#### Create and deploy a compliance policy with a rule for baseline compliance policy assessment

1. In the **Assets and Compliance** workspace, expand **Compliance Settings**, then select the **Compliance Policies** node.
2. Click **Create Compliance Policy** in the ribbon to bring up the **Create Compliance Policy Wizard**.
3. On the **General** page, select **Compliance rules for devices managed with the Configuration Manager client**.

    - Devices must be managed with the Configuration Manager client to include custom configuration baselines as part of compliance policy assessment.
4. Select your platforms on the **Supported Platforms** pages.
5. On the **Rules** page, select **New**, then select the **Include configured baselines in compliance policy assessment** condition.

    ![Include configured baselines in compliance policy assessment condition](media/3608345-create-compliance-policy-rule.png)
6. Click **OK**, then **Next** to get to the **Summary** page.
7. Verify your selections and click **Next** then **Close**.
8. In the **Compliance Policies** node, right-click on the policy you created, and select **Deploy**.
9. Choose your collection, alert generation settings, and your compliance evaluation schedule for the policy.
10. Click **OK** to deploy the compliance policy.

#### Select a configuration baseline and check "Evaluate this baseline as part of compliance policy assessment"

1. In the **Assets and Compliance** workspace, expand **Compliance Settings**, then select the **Configuration Baselines** node.
2. Right-click on an existing baseline that's deployed to a device collection, then select **Properties**.
    - The baseline must be deployed to a device collection, not a user collection.
3. Enable the **Evaluate this baseline as part of compliance policy assessment** setting.
4. Click **OK** to save the changes to your configuration baseline.

![Configuration Baseline Properties dialog box](media/3608345-configuration-baseline-properties.png)

## Improvements to application groups

Starting in current branch version 1906, you can create a group of applications to send to a device collection as a single deployment. This technical preview release improves upon this feature:

- Users can **Uninstall** the app group in Software Center.
- You can deploy an app group to a **user collection**.

For more general information, see [Create application groups](../../../apps/deploy-use/create-app-groups).

## Reclaim SEDO lock

If the Configuration Manager console stops responding, you can be locked out of making further changes until the lock expires after 30 minutes. This lock is part of the Configuration Manager SEDO (Serialized Editing of Distributed Objects) system. For more information, see [Configuration Manager SEDO](../../../develop/core/understand/sedo).

Starting in [current branch version 1906](../../plan-design/changes/whats-new-in-version-1906#reclaim-sedo-lock-for-task-sequences), you could clear your lock on a task sequence. Starting in this technical preview release, you can clear your lock on any object in the Configuration Manager console.

This action only applies to your user account that has the lock, and on the same device from which the site granted the lock. When you attempt to access a locked object, you can now **Discard Changes**, and continue editing the object. These changes would be lost anyway when the lock expired.

## Attach files to feedback

You can now choose to attach log and diagnostic files when you use [Send a Frown](../../understand/product-feedback) in the Configuration Manager console to send feedback to Microsoft. This additional information can help us more quickly determine the cause of the problem. Files included with feedback are transmitted and stored using Microsoft Error Reporting (also known as Windows Error Reporting).

Microsoft uses the reported information to improve Microsoft software and services. For more information about how the information is used, see the [Privacy Statement for the Microsoft Error Reporting Service](/en-us/troubleshoot/windows-client/system-management-components/windows-error-reporting-diagnostics-enablement-guidance) and [Additional information about privacy for Configuration Manager](../../plan-design/security/additional-privacy).

### Prerequisites

- The device running the Configuration Manager console, must be able to reach the Microsoft Error Reporting Service endpoint: `https://watson.microsoft.com/`
- [Enable Windows Error Reporting](/en-us/powershell/module/windowserrorreporting).

### To attach files to feedback

1. In the upper right corner of the console, click on the smiley face.
2. In the drop-down menu, select **Send a frown**.
3. Use the text box to explain what you didn't like.
4. Choose if you would like to share your e-mail address and a screenshot.
5. Click **Add file to feedback**, then choose a file to submit.

    - Attach up to 100 files
    - 1 GB maximum size for the upload
6. Click **Submit Feedback**

![Include diagnostic files when you send a frown](media/3556011-feedback-add-files.png)

## Client diagnostic actions

Based on feedback, there are new device actions for **Client Diagnostics** in the Configuration Manager console. This release includes the following actions:

- **Enable verbose logging**: Change the global log level for the CCM component to verbose, and enable debug logging.
- **Disable verbose logging**: Change the global log level to default, and disable debug logging.

Important

These actions only change the log verbosity, not the size or history. More verbose logging can generate more log content.

For more information about these settings, see [About log files](../../plan-design/hierarchy/about-log-files#client-and-management-point-logging-options).

Note

The management point role also uses the CCM component. If the targeted device is also a management point, this action also applies to that role.

### Prerequisites

- Update the target client to the latest version.
- Your Configuration Manager administrative user needs the **Notify resource** permission. For more information, see [Client notification](../../clients/manage/client-notification#client-notification).

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, select the **Devices** node, and choose a target device.
2. In the ribbon, on the **Home** tab, in the **Device** group, select **Client Diagnostics**. Choose one of the available actions.

Track the status of the task in the **diagnostics.log** on the client.

## Office 365 ProPlus Pilot and Health Dashboard

There's a new experience to help admins create pilot collections for getting started with Microsoft 365 Apps for enterprise deployments. We know from customer feedback that many enterprises don't immediately deploy Microsoft 365 Apps for enterprise. Instead, they prefer to run a pilot on a small set of devices before completing their rollout. The **Office 365 ProPlus Pilot and Health Dashboard** provides a recommendation for pilot devices based on add-in inventory. The following tiles are in the dashboard:

- Generate pilot
- Recommended pilot devices
- Deploy pilot
- Devices sending health data
- Devices not meeting health goals
- Add-ins not meeting health goals
- Macros not meeting health goals

To access the dashboard, go to **Software Library** &gt; **Office 365 Client Management** &gt; **Office 365 Pilot and Health**.

![Office 365 Pilot and Health Dashboard screenshot](media/4488272-office-365-pro-plus-pilot.png)

### Generate pilot

Generate a pilot recommendation from a limiting collection at the click of a button. As soon as the action is launched, a background task starts calculating your pilot collection. Your limiting collection must contain at least one device with an Office version that isn't ProPlus.

### Recommended pilot devices

**Recommended pilot devices** are a minimal set of devices representing all installed add-ins across the limiting collection you used when generating the pilot. Drill down to get a list of these devices. Then use the details to exclude any devices from the pilot if needed. If all of your add-ins are already on Microsoft 365 Apps for enterprise devices, then devices with those add-ins won't be included in the calculation. This also means it's possible that you won't get any results in your pilot collection since all of your add-ins have been seen on devices where Microsoft 365 Apps for enterprise is installed.

### Deploy pilot

Once you accept your pilot devices, deploy Microsoft 365 Apps for enterprise to the pilot collection using the phased deployment wizard. Admins can define the pilot and limiting collection in the wizard to manage deployments.

### Health data

Once Microsoft 365 Apps for enterprise is installed, enable health data on your pilot devices. The health data gives you insight into which add-ins and macros don't meet health goals. The **Devices ready to deploy** chart identifies non-pilot devices that are ready for deployment by using the health insights. Get a count of devices that are sending health data from the **Devices sending health data** chart.

### Devices not meeting health goals

This tile summarizes devices that have issues with add-ins, macros, or both.

### Add-ins not meeting health goals

- Load failures: The add-in failed to start.
- Crashes: The add-in failed while it was running.
- Error: The add-in reported an error.
- Multiple issues: The add-in has more than one of the above issues.

### Macros not meeting health goals

- Load failures: The document failed to load.
- Runtime errors: An error happened while the macro was running. These errors can be dependent on the inputs so may not always occur.
- Compile errors: The macro didn't compile correctly so it won't attempt to run.
- Multiple issues: The macro has more than one of the above issues.

### Known issues

If a standard prefix is used in naming Office files, it may be difficult to tell files apart when troubleshooting a problem, such as a macro issue. Configuration Manager obfuscates the file names, meaning files named `2019_Q3_Results.xlsm` and `2019_Q4_Results.xlsm` will both be identified as `20*.xlsm`.

## Improvements to console search

This release includes the following improvements to search in the Configuration Manager console based on your feedback:

- You can now use the **All Subfolders** search option from the **Driver Packages** and **Queries** nodes.
- When a search returns more than 1,000 results, now select the **OK** button on the notice bar to view more results.

    ![Screenshot of notice bar for too many search results](media/4640570-search-too-many-results.png)

    Tip

    The default limit on search results is 1,000. You can change this default value. In the Configuration Manager console, go to the **Search** tab of the ribbon. In the **Options** group, select **Search Settings**. Change the **Search Results** value. A larger number of search results might take longer to display.

    By default, the upper maximum limit is 100,000. To change this limit, set the DWORD value **QueryResultCountMaximum** in the following registry key:

    `HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\AdminUI`

    The in-console setting corresponds to the **QueryResultCountLimit** value in the same key. An administrator can configure these values in the HKLM hive for all users of the device. The HKCU value overrides the HKLM setting.

## New variable for Windows 10 in-place upgrade

Some customers have reported timing issues with the Window 10 in-place upgrade task sequence on high performance devices when Windows setup is complete:

- The TSManager component records entries similar to the following errors in the **smsts.log**:

    ```log
    Failed to initate policy evaluation for namespace 'root\ccm\policy\machine', hr=0x80041010
    Error compiling client config policies. code 80041010
    Task Sequence Manager could not initialize Task Sequence Environment. code 80041010
    ```
- Windows setup records entries similar to the following errors in the **setupcomplete.log**:

    ```log
    Running C:\windows\CCM\\TSMBootstrap.exe to resume task sequence
    ERRORLEVEL = -1073741701
    TSMBootstrap did not request reboot, resetting registry
    Exiting setupcomplete.cmd
    ```

To address these issues, you can now set a new task sequence variable **SetupCompletePause**. When you assign a value in seconds to this variable, the Windows setup process delays that amount of time before it starts the task sequence. This timeout provides the Configuration Manager client additional time to initialize. The specific timeout value will vary depending upon the hardware. A conservative value of `30` or `60` seconds generally resolves the issue, but a shorter timeout may work in your environment.

## Improvements to Windows Virtual Desktop support

Configuration Manager current branch version 1906 introduced support for [Windows Virtual Desktop](../../plan-design/configs/supported-operating-systems-for-clients-and-devices#azure-virtual-desktop). If you require user policy in this scenario, and accept any potential performance impact, you can now configure a client setting to enable user policy. In the **Client Policy** group, configure the following setting: **Enable user policy for multiple user sessions**.

## General known issues

### Task sequences aren't available to PXE or media

If you deploy a task sequence for PXE or media (USB or DVD), the client doesn't receive the policy. The following message is in **smsts.log**:

`There are no task sequences available to this computer.`

#### Workaround

Start the task sequence from Software Center.