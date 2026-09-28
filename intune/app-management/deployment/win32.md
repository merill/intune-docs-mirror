---
layout: Conceptual
title: Win32 App Management in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/win32
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_Win32
ms.reviewer: bryanke
ms.subservice: apps
description: Learn how to manage Win32 apps with Microsoft Intune. This article provides an overview of the Intune Win32 app delivery and management capabilities.
ms.date: 2026-02-06T00:00:00.0000000Z
ms.topic: overview
ai-usage: ai-assisted
locale: en-us
document_id: 0f2f19ed-3f0b-2d16-55b5-58bb90b4eb83
document_version_independent_id: 0f2f19ed-3f0b-2d16-55b5-58bb90b4eb83
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/win32.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/win32
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/win32.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 51221317-b04a-cc7d-0623-603a4c05ced0
---

# Win32 App Management in Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune enables Windows Win32 app management. Win32 app management in Intune allows you to install, configure, protect, and monitor your Windows applications on devices at your organization. Win32 apps are deployed using the Microsoft Intune management extension (IME), which is installed automatically when a PowerShell script or a Win32 app is assigned to the user or device using Intune.

In addition to supporting extensive management capabilities, Win32 app management in Microsoft Intune provides support for the following capabilities:

- Management of large traditional desktop apps
- Support for several app types
- Control for complex app installations
- Support for detection rules, dependencies, and requirements
- Support for 32-bit Windows, 64-bit Windows, and ARM64 operating system architecture
- Support for Windows S mode devices

Although it's possible for cloud-connected customers to use Microsoft Configuration Manager for Windows app management, Intune-only customers have greater management capabilities for their Win32 apps. This article provides an overview of the Intune Win32 app management features and related information.

Note

For information about Enterprise App Catalog apps, see [Add an Enterprise App Catalog app (Win32) to Microsoft Intune](add-enterprise-catalog-app).

Important

When you're deploying Windows Win32 apps, consider using the Win32 app type in Intune exclusively, particularly when you have a multiple-file Win32 app installer. If you mix the installation of Win32 apps and line-of-business apps during Windows Autopilot enrollment, the app installation might fail as they both may attempt to use the Trusted Installer service at the same time which causes a failure due to this conflict. However, mixing of Win32 and line-of-business apps during Windows Autopilot device preparation is supported.

Important

Microsoft Intune does not support interactive application installations. Applications deployed through Intune must install silently and cannot require user interaction, such as dialog boxes, prompts, or UI input during installation. Techniques that attempt to force interaction with the signed-in user session (for example, using tools like serviceui.exe or similar workarounds) are not supported and may result in inconsistent or unpredictable behavior.

## Prerequisites

To use Win32 app management, be sure the following criteria are met:

- Use a [supported Windows version](../../fundamentals/ref-supported-platforms) (Enterprise, Pro, or Education editions).
- Devices must be enrolled in Intune and either:

    - [Microsoft Entra registered](/en-us/azure/active-directory/devices/concept-azure-ad-register)
    - [Microsoft Entra joined](/en-us/azure/active-directory/devices/concept-azure-ad-join)
    - [Microsoft Entra hybrid joined](/en-us/azure/active-directory/devices/concept-azure-ad-join-hybrid)
- Windows application size must not be greater than 30 GB per app.

    Note

    The [Microsoft Intune management extension (IME)](../../device-management/tools/management-extension-windows) provides Intune's Win32 app type capabilities on managed clients. It's installed automatically when a PowerShell script or Win32 app is assigned to the user or device. Additionally, the Intune management extension agent checks every hour (or on service or device restart) for any new Win32 app assignments.

## PowerShell script installer

When adding a Win32 app, you can upload a PowerShell script to serve as the installer instead of specifying a command line. Intune packages the script with the app content and runs it in the same context as the app installer. This capability enables richer setup workflows, including:

- Prerequisite checks before installation
- Configuration changes during installation
- Post-install actions and validation
- Complex conditional logic based on device state

The PowerShell script runs in place of the standard install command, and installation results appear in the Intune admin center based on the script's return code.

### Script requirements

- Scripts are limited to 50 KB in size
- Scripts run in the same context as the app installer (system or user context)
- Return codes from the script determine installation success or failure status
- Scripts should run silently without user interaction

Note

If Multi-Admin Approval (MAA) is enabled for your tenant, you can't upload PowerShell scripts during app creation. You must first create the app, then add or modify scripts afterward. Currently, script properties like `enforceSignatureCheck` and `runAs32Bit` can be edited without MAA requests, but this behavior will change in a future update to require MAA approval.

### When to use script installers

Consider using PowerShell script installers when:

- Your app requires prerequisite validation before installation
- You need to perform configuration changes alongside app installation
- The installation process requires conditional logic
- Post-installation actions are needed (like registry modifications or service configuration)

For command line installations, you can continue using the traditional Install command field.

For more information about adding Win32 apps with script installers, see [Add, assign, and monitor a Win32 app in Microsoft Intune](add-win32).

## Prepare the Win32 app content for upload

Before you can add a Win32 app to Microsoft Intune, you must prepare the app by using the Microsoft Win32 Content Prep Tool. You use the Microsoft Win32 Content Prep Tool to preprocess Windows classic (Win32) apps. The tool converts application installation files into the *.intunewin* format. For more information and steps, see [Prepare Win32 app content for upload](create-win32-package).

## Add, assign, and monitor a Win32 app

After you have [prepared a Win32 app to be uploaded to Intune](create-win32-package) by using the Microsoft Win32 Content Prep Tool, you can add the app to Intune. For more information and steps, see [Add, assign, and monitor a Win32 app in Microsoft Intune](add-win32).

Note

Windows application size is limited to 30 GB per app.

## Delivery optimization

Windows devices can download Intune Win32 app content by using the delivery optimization component of Windows. Delivery optimization provides peer-to-peer functionality that's turned on by default.

You can configure Delivery Optimization to download Win32 app content in either background or foreground mode based on assignment. Delivery optimization can be configured using Intune device configuration (or by group policy). For more information, see [Delivery Optimization for Windows](/en-us/windows/deployment/update/waas-delivery-optimization).

Note

You can also install a Microsoft Connected Cache server on your Configuration Manager distribution points to cache delivery optimization aware content like Intune Win32 app content. For more information, see [Microsoft Connected Cache in Configuration Manager](/en-us/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

## Install required and available apps on devices

The user will see Windows notifications for the required and available app installations. The following image shows an example notification where the app installation isn't complete until the device is restarted.

![Screenshot of Windows notifications for an app installation.](media/apps-win32-app-management/apps-win32-app-08.png)

The following image notifies the user that app changes are being made to the device.

![Screenshot notifying the user that app changes are being made.](media/apps-win32-app-management/apps-win32-app-09.png)

Additionally, the Company Portal app shows more app installation status messages to users. The following conditions apply to Win32 dependency features:

- App failed to be installed. Dependencies defined by the admin weren't met.
- App was installed successfully but requires a restart.
- App is in the process of being installed but requires a restart to continue.

## Set Win32 app availability and notifications

You can configure the start time and deadline time for a Win32 app. At the start time, the Intune management extension will start the app content download and cache it for the required intent. The app will be installed at the deadline time.

For available apps, the start time will dictate when the app is visible in the company portal, and content will be downloaded when the user requests the app from the company portal. You can also enable a restart grace period.

On a device where a Win32 app with grace period settings has been deployed, low-rights users with non-administrative privileges can interact with the grace period UX. Admins on the device are also able to interact with the grace period UX on the device.

Important

The **Restart grace period** setting in the **Assignment** section is available only when **Device restart behavior** of the **Program** section is set to either of the following options:

- **Determine behavior based on return codes** - Commonly set to Hard Reboot, however if return code is mapped to Soft Reboot, the user will only get a reboot notification and restart grace period settings won't be applied.
- **Intune will force a mandatory device restart**

Win32 apps installed by Intune on a managed device won't be automatically uninstalled from that device if it's unenrolled from Intune management. Admins should restrict app assignment and installation to corporate managed devices to reduce the risk of applications and data becoming unmanaged.

Set the app availability and other app assignment properties using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** or **Apps** &gt; **Windows**.
3. Select an app from the list with **Windows app (Win32)** as its **Type**.
4. From the app pane, select **Properties** and then **Edit** next to the **Assignments** section. Then select **Add group**, **Add all users**, or **Add all devices** below one of the assignment types.

    **Assignment type** options include the following:

    - **Required**
    - **Available for enrolled devices**
    - **Uninstall**

    Note

    Win32 apps installed using the **Available for enrolled devices** assignment won't be automatically reinstalled by Intune if they're uninstalled from a device in any way.
5. If **Add group** was used, select a group on the **Select groups** pane to specify which groups will be assigned the app.
6. To modify additional properties of the assignment, select the corresponding text under one of the assignment headings, including **Group mode**, **End user notifications**, **Availability**, **Installation deadline**, **Restart grace period**, or **Delivery optimization priority**.
7. In the **Edit assignment** pane, you can set the following properties:

    - **Mode** to **Include** or **Exclude**
    - **End user notifications** to one of the following options:

        - **Show all toast notifications**
        - **Show toast notifications for computer restarts**
        - **Hide all toast notifications**.
    - **Time zone** to **UTC** or **Device time zone**
    - **App availability** to **As soon as possible** or **A specific date and time** and specify your date and time. This date and time specify when the app is downloaded to the user's device.
    - **App installation deadline** to **As soon as possible** or **A specific date and time** and select your date and time. This date and time specify when the app is installed on the targeted device. When more than one assignment is made for the same user or device, the app installation deadline time is picked based on the following conditions:

        - A specific deadline is picked over the earliest time possible.
        - An earlier specific deadline is picked over a later specific deadline.

        Note

        If a win32 app is configured with a deadline to install, it will be downloaded but it won't install until the deadline. The Company Portal doesn't provide this level of detail. The Company Portal will show an **Installing** status for the app as soon as it's downloaded. Once the app is installed, the Company Portal will show the app installation status as **Installed**. The time between showing an **Installing** status verses an **Installed** status depends on the configuration for the deadline in Intune.
    - **Restart grace period** to **Enabled** or **Disabled**. The restart grace period starts as soon as the app installation has finished on the device. When the setting is disabled, the device can restart without warning.

        You can customize the following options:

        - **Device restart grace period (minutes)**: The default value is 1,440 minutes (24 hours). This value can be a maximum of 2 weeks.
        - **Select when to display the restart countdown dialog box before the restart occurs (minutes)**: The default value is 15 minutes.
        - **Allow user to snooze the restart notification**: You can choose **Yes** or **No**.
            - **Select the snooze duration (minutes)**: The default value is 240 minutes (4 hours). The snooze value can't be more than the reboot grace period.

        Important

        The **Restart grace period** assignment setting is available only when **Device restart behavior** in the **Program** section of the app is set to either of the following options:

        - **Determine behavior based on return codes**
        - **Intune will force a mandatory device restart**
8. Select **Review + save**.

## Notifications for Win32 apps

If needed, you can suppress showing user notifications per app assignment. Follow the steps above and choose either **Show toast notifications for computer restarts** or **Hide all toast notifications** for the **End user notifications** option in the **Edit assignment** pane based on the level of notification suppression that you require.

## App relationship viewer

By selecting a Win32 app in Intune, you'll be able to view which apps are directed connected to the selected app. These connected apps are child apps. Child apps are designated as dependent applications and superseded applications. The apps in the view are clickable and can be navigated to directly from the selected app.

The relationship viewer is available for two app types:

- Windows app (Win32)
- Windows catalog app (Win32)

To view an app using the relationship viewer:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **All Apps** or **Apps** &gt; **Windows**.
3. Select an app from the list with **Windows app (Win32)** or **Windows catalog app (Win32)** as the **Type**.
4. From the app pane, select **Relationship viewer**.

![Screenshot of the Relationship viewer.](media/apps-win32-app-management/relationship-viewer.png)

For related information, see the following resources:

- [Add Win32 app supersedence](configure-win32-supersedence)
- [App relationship viewer](win32#app-relationship-viewer)
- [Microsoft Intune Enterprise Application Management](enterprise-app-management)