---
layout: Conceptual
title: Kiosk settings for Windows in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-kiosk-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Configure your Windows 10/11 client devices as single-app and multi-app kiosks, customize the start menu, add apps, show the task bar, and configure a web browser in Microsoft Intune.
ms.date: 2025-02-20T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mikedano
locale: en-us
document_id: c579711e-1282-7ce9-60d3-9a72185f2202
document_version_independent_id: c579711e-1282-7ce9-60d3-9a72185f2202
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-kiosk-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-kiosk-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-kiosk-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: f15cedcd-38a9-bda5-0630-e2a319a1e0f0
---

# Kiosk settings for Windows in Microsoft Intune - Microsoft Intune | Microsoft Learn

Note

Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](../settings-catalog/).

On Windows devices, you can configure these devices to run in single-app kiosk mode. On Windows 10 devices, you can configure these devices to run in multi-app kiosk mode. To configure multi-app kiosk on Windows 11, go to [Set up a multi-app kiosk on Windows 11 devices](/en-us/windows/configuration/lock-down-windows-11-to-specific-apps).

This article describes some of the settings you can control on Windows client devices. As part of your mobile device management (MDM) solution, use these settings to configure your Windows client devices to run in kiosk mode.

As an Intune administrator, you can create and assign these settings to your devices.

To learn more about the Windows kiosk feature in Intune, see [configure kiosk settings](configure-kiosk).

## Before you begin

- Create a [Windows kiosk device configuration profile](configure-kiosk#create-the-profile).

    Important

    On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.
- This kiosk profile is directly related to the device restrictions profile you create using the [Microsoft Edge kiosk settings](ref-device-restrictions-windows#microsoft-edge-legacy-version-45-and-older). To summarize:

    1. Create this kiosk profile to run the device in kiosk mode.
    2. Create the [device restrictions profile](ref-device-restrictions-windows#microsoft-edge-legacy-version-45-and-older), and configure specific features and settings allowed in Microsoft Edge.
- Be sure that any files, scripts, and shortcuts are on the local system. For more information, including other Windows requirements, see [Customize and export Start layout](/en-us/windows/configuration/customize-and-export-start-layout).
- The kiosk profile loads for standard user accounts. The kiosk profile doesn't load for members in the local admin group.

Important

Be sure to assign this kiosk profile to the same devices as your [Microsoft Edge profile](ref-device-restrictions-windows#microsoft-edge-legacy-version-45-and-older).

## Single app, full-screen kiosk

Runs only one app on the device, such as a web browser or Store app.

- **Select a kiosk mode**: Choose **Single app, full-screen kiosk**.
- **User logon type**: Select the account type that runs the app. Your options:

    - **Auto logon (Windows 10 version 1803 and newer)**: Use on kiosks in public-facing environments that don't require the user to sign in, similar to a guest account. This setting uses the [AssignedAccess CSP](/en-us/windows/client-management/mdm/assignedaccess-csp).
    - **Local user account**: Enter the local (to the device) user account. The account you enter signs in to the kiosk.
    - **Microsoft Entra user or group (Windows 10 version 1803 and later)**: Select **Add**, and choose Microsoft Entra users or groups from the list. You can select multiple users and groups. Choose **Select** to save your changes.
- **Application type**: Select the application type. Your options:

    - **Add Microsoft Edge browser**: Select this option for Microsoft Edge version 87 and newer.

        Note

        These settings enable the Microsoft Edge browser on the device. To configure Microsoft Edge settings, use the [settings catalog](../settings-catalog/configure-edge).

        - **Edge Kiosk URL**: Enter a default webpage that opens when Microsoft Edge browser opens and restarts. For example, enter `https://www.contoso.com` or `http://bing.com`.
        - **Microsoft Edge kiosk mode type**: Select the kiosk mode type. Both options help protect user data.
            - **Public Browsing (InPrivate)**: Runs a limited multi-tab version of Microsoft Edge. Users can browse publicly, or end their browsing session.
            - **Digital/Interactive Signage (InPrivate)**: Opens a URL full screen, and only shows the content on that website. [Set up digital signs](/en-us/windows/configuration/setup-digital-signage) provides more information on this feature.

        For more information on these options, see [Support policies for kiosk mode](/en-us/deployedge/microsoft-edge-configure-kiosk-mode#support-policies-for-kiosk-mode).

        - **Refresh browser after idle time**: Enter the idle time when the browser should restart, from 0-1440 minutes. The idle time is the user's last interaction.
    - **Add Microsoft Edge Legacy browser**: Select this option for Microsoft Edge version 77, and version 45 and older.

        Note

        This setting enables the Microsoft Edge browser on the device.

        - To configure Microsoft Edge version 77 and newer settings, use the [settings catalog](../settings-catalog/configure-edge).
        - To configure Microsoft Edge version 45 and older, create a [device restrictions profile](configure-device-restrictions), and [configure the settings](ref-device-restrictions-windows#microsoft-edge-legacy-version-45-and-older).

        - **Microsoft Edge kiosk mode type**: Select the kiosk mode type. Both options help protect user data.

            - **Digital/Interactive signage**: Opens a URL full screen, and only shows the content on that website. [Set up digital signs](/en-us/windows/configuration/setup-digital-signage) provides more information on this feature.
            - **Public browsing (InPrivate)**: Runs a limited multi-tab version of Microsoft Edge. Users can browse publicly, or end their browsing session.

        For more information on these options, see [Deploy Microsoft Edge kiosk mode](/en-us/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).
    - **Add Kiosk browser**: Select **Kiosk browser settings**. These settings control a web browser app on the kiosk. Be sure you get the [Kiosk browser app](https://apps.microsoft.com/detail/9ngb5s5xg2kp?) from the Store, add it to Intune as a [Client App](../../app-management/deployment/). Then, assign the app to the kiosk devices.

        Enter the following settings:

        - **Default home page URL**: Enter the default URL shown when the kiosk browser opens, or when the browser restarts. For example, enter `http://bing.com` or `http://www.contoso.com`.
        - **Home button**: **Show** or **hide** the kiosk browser's home button. By default, the button isn't shown.
        - **Navigation buttons**: **Show** or **hide** the forward and back buttons. By default, the navigation buttons aren't shown.
        - **End session button**: **Show** or **hide** the end session button. When shown, the user selects the button, and the app prompts to end the session. When confirmed, the browser clears all browsing data (cookies, cache, and so on), and then opens the default URL. By default, the button isn't shown.
        - **Refresh browser after idle time**: Enter the amount of idle time, from 1-1440 minutes, until the kiosk browser restarts in a fresh state. Idle time is the number of minutes since the user's last interaction. By default, the value is empty or blank, which means there isn't any idle timeout.
        - **Allowed websites**: Use this setting to allow specific websites to open. In other words, use this feature to restrict or prevent websites on the device. For example, you can allow all websites at `http://contoso.com` to open. By default, all websites are allowed.

            To allow specific websites, upload a file that includes a list of the allowed websites on separate lines. If you don't add a file, all websites are allowed. By default, Intune allows all subdomains of the website. For example, you enter the `sharepoint.com` domain. Intune automatically allows all subdomains, such as `contoso.sharepoint.com`, `my.sharepoint.com`, and so on. Don't enter wildcards, such as the asterisk (`*`).

            Your sample file should look similar to the following list:

            `http://bing.com``https://bing.com``http://contoso.com``https://contoso.com``office.com`

        Note

        Windows Kiosks with Autologon enabled using Microsoft Kiosk Browser must use an offline license from the Microsoft Store for Business. This requirement is because Autologon uses a local user account with no Microsoft Entra credentials. So, online licenses can't be evaluated. For more information, see [Distribute offline apps](/en-us/microsoft-store/distribute-offline-apps).
    - **Add Store app**: Select **Add a store app**, and choose an app from the list.

        Don't have any apps listed? Add some using the steps at [Client Apps](../../app-management/deployment/).
- **Specify Maintenance Window for App Restarts**: Some apps require a restart to complete the app installation, or complete the installation of updates. **Require** creates a maintenance window. If the app requires a restart, then it's restarted during this window.

    Also enter:

    - **Maintenance Window Start Time**: Select the date and time of day to begin checking clients for any app updates that require restart. The default start time is midnight, or zero minutes. If blank, then apps restart at an unscheduled time 3 days after an app update is installed.
    - **Maintenance Window Recurrence**: Default is daily. Select how often Maintenance windows for app updates take place. To avoid unscheduled app restarts, the recommendation is **Daily**.

    When set to **Not configured** (default), Intune doesn't change or update this setting.

    [ApplicationManagement/ScheduleForceRestartForUpdateFailures CSP](/en-us/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures)

## Multi-app kiosk

Note

Currently, you can use Intune to configure a multi-app kiosk on Windows 10 devices. To configure multi-app kiosk on Windows 11, go to [Set up a multi-app kiosk on Windows 11 devices](/en-us/windows/configuration/lock-down-windows-11-to-specific-apps).

Runs multiple apps on the device. Apps in this mode are available on the start menu. These apps are the only apps the user can open. If an app has a dependency on another app, then add both apps to the allowed apps list. For example, Internet Explorer 64-bit has a dependency on Internet Explorer 32-bit. So, you must allow `C:\Program Files\internet explorer\iexplore.exe` and `C:\Program Files (x86)\Internet Explorer\iexplore.exe`.

- **Select a kiosk mode**: Select **Multi app kiosk**.
- **Target Windows 10 in S mode devices**:

    - **Yes**: Allows store apps and AUMID apps in the kiosk profile. It excludes Win32 apps.
    - **No**: Allows store apps, Win32 apps, and AUMID apps in the kiosk profile. This kiosk profile isn't deployed to S-mode devices.
- **User logon type**: Select the account type that runs your apps. Your options:

    - **Auto logon (Windows 10 version 1803 and later)**: Use on kiosks in public-facing environments that don't require the user to sign in, similar to a guest account. This setting uses the [AssignedAccess CSP](/en-us/windows/client-management/mdm/assignedaccess-csp).
    - **Local user account**: **Add** the local (to the device) user account. The account you enter signs in to the kiosk.
    - **Microsoft Entra user or group (Windows 10 version 1803 and later)**: Select **Add**, and choose Microsoft Entra users or groups from the list. You can select multiple users and groups. Choose **Select** to save your changes.
    - **HoloLens visitor**: The visitor account is a guest account that doesn't require any user credentials or authentication, as described in [shared PC mode concepts](/en-us/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).
- **Browser and Applications**: Add the apps to run on the kiosk device. Remember, you can add several apps.

    ![Add browsers or apps to multi-app kiosk profile in Microsoft Intune.](media/ref-kiosk-settings-windows/multi-app-kiosk-add-applications-browser.png)

    - **Browsers**

        - **Add Microsoft Edge Legacy**: Select this option for Microsoft Edge version 77, and version 45 and older. Microsoft Edge is added to the app grid, and all applications can run on this kiosk. Select the **Microsoft Edge kiosk mode type**:

            - **Normal mode (full version of Microsoft Edge)**: Runs a full-version of Microsoft Edge with all browsing features. User data and state are saved between sessions.
            - **Public browsing (InPrivate)**: Runs a multi-tab version of Microsoft Edge InPrivate with a tailored experience for kiosks that run in full-screen mode.

            For more information on these options, see [Deploy Microsoft Edge kiosk mode](/en-us/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

            Note

            This setting enables the Microsoft Edge browser on the device.

            - To configure Microsoft Edge version 77 and newer settings, use the [settings catalog](../settings-catalog/configure-edge)
            - To configure Microsoft Edge version 45 and older, create a [device restrictions profile](configure-device-restrictions), and [configure the settings](ref-device-restrictions-windows#microsoft-edge-legacy-version-45-and-older).
        - **Add Kiosk browser**: These settings control a web browser app on the kiosk. Be sure you deploy a web browser app to the kiosk devices using [Client Apps](../../app-management/deployment/).

            Enter the following settings:

            - **Default home page URL**: Enter the default URL shown when the kiosk browser opens, or when the browser restarts. For example, enter `http://bing.com` or `http://www.contoso.com`.
            - **Home button**: **Show** or **hide** the kiosk browser's home button. By default, the button isn't shown.
            - **Navigation buttons**: **Show** or **hide** the forward and back buttons. By default, the navigation buttons aren't shown.
            - **End session button**: **Show** or **hide** the end session button. When shown, the user selects the button, and the app prompts to end the session. When confirmed, the browser clears all browsing data (cookies, cache, and so on), and then opens the default URL. By default, the button isn't shown.
            - **Refresh browser after idle time**: Enter the amount of idle time (1-1440 minutes) until the kiosk browser restarts in a fresh state. Idle time is the number of minutes since the user's last interaction. By default, the value is empty or blank, which means there isn't any idle timeout.
            - **Allowed websites**: Use this setting to allow specific websites to open. In other words, use this feature to restrict or prevent websites on the device. For example, you can allow all websites at `contoso.com*` to open. By default, all websites are allowed.

                To allow specific websites, upload a .csv file that includes a list of the allowed websites. If you don't add a .csv file, all websites are allowed.

            Note

            Windows 10 Kiosks with Autologon enabled using Microsoft Kiosk Browser must use an offline license from the Microsoft Store for Business. This requirement is because Autologon uses a local user account with no Microsoft Entra credentials. So, online licenses can't be evaluated. For more information, see [Distribute offline apps](/en-us/microsoft-store/distribute-offline-apps).
    - **Applications**

        - **Add store app**: Add an app from the Microsoft Store for Business. If you don't have any apps listed, then you can get apps, and [add them to Intune](../../app-management/deployment/add-microsoft-store-legacy). For example, you can add Kiosk Browser, Excel, OneNote, and more.
        - **Add Win32 App**: A Win32 app is a traditional desktop app, such as Visual Studio Code or Google Chrome. Enter the following properties:

            - **Application name**: Required. Enter a name for the application.
            - **Local path to app executable file**: Required. Enter the path to the executable, such as `C:\Program Files (x86)\Microsoft VS Code\Code.exe` or `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
            - **Application user model ID (AUMID) for the Win32 app**: Enter the Application user model ID (AUMID) of the Win32 app. This setting determines the start layout of the tile on the desktop. To get this ID, see [Get-StartApps](/en-us/powershell/module/startlayout/get-startapps).
        - **Add by AUMID**: Use this option to add inbox Windows apps, such as Notepad or Calculator. Enter the following properties:

            - **Application name**: Required. Enter a name for the application.
            - **Application user model ID (AUMID)**: Required. Enter the Application user model ID (AUMID) of the Windows app. To get this ID, see [find the Application User Model ID of an installed app](/en-us/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
        - **AutoLaunch**: Optional. After you add your apps and browser, select one app or browser to automatically open when the user signs in. Only a single app or browser can be autolaunched.
        - **Tile size**: Required. After you add your apps, select a Small, Medium, Wide, or Large app tile size.

            ![Automatically launch the app or browser, and select the tile size in a multi-app kiosk profile in Microsoft Intune.](media/ref-kiosk-settings-windows/multi-app-kiosk-autolaunch-tiles.png)

    Tip

    After you add all the apps, you can change the display order by clicking-and-dragging the apps in the list.
- **Use alternative Start layout**: Select **Yes** to enter an XML file that describes how the apps appear on the start menu, including the order of the apps. Use this option if you require more customization in your start menu. [Customize and export Start layout](/en-us/windows/configuration/customize-and-export-start-layout) has some guidance, and sample XML.
- **Windows Taskbar**: Choose to **Show** or **hide** the taskbar. By default, the taskbar isn't shown. Icons, such as the Wi-Fi icon, are shown, but end users can't change the settings.
- **Allow Access to Downloads Folder**: Choose **Yes** to allow users to access the Downloads folder in Windows Explorer. By default, access to the Downloads folder is disabled. This feature is commonly used for end users to access items downloaded from a browser.
- **Specify Maintenance Window for App Restarts**: Some apps require a restart to complete the app installation, or complete the installation of updates. **Require** creates a maintenance window. If apps require a restart, then they're restarted during this window.

    Also enter:

    - **Maintenance Window Start Time**: Select the date and time of day to begin checking clients for any app updates that require restart. The default start time is midnight, or zero minutes. If blank, then apps restart at an unscheduled time 3 days after an app update is installed.
    - **Maintenance Window Recurrence**: Default is daily. Select how often Maintenance windows for app updates take place. To avoid unscheduled app restarts, the recommendation is **Daily**.

    When set to **Not configured** (default), Intune doesn't change or update this setting.

    [ApplicationManagement/ScheduleForceRestartForUpdateFailures CSP](/en-us/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures)