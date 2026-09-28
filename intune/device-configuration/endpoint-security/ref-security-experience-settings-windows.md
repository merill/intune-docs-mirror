---
layout: Conceptual
title: Antivirus policy settings for Windows Security experience policy for Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-security-experience-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Endpoint security Antivirus policy settings for the Windows Security app in Microsoft Intune
ms.date: 2025-03-28T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mattcall
locale: en-us
document_id: 24749d15-6a9d-96e6-ad0f-6a0c2faf00a3
document_version_independent_id: 24749d15-6a9d-96e6-ad0f-6a0c2faf00a3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-security-experience-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-security-experience-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-security-experience-settings-windows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/691e3042-55ad-4ce1-b5e9-649b1cc47b5c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b7d11190-096c-4ddb-87db-63764f603aac
platformId: 8e1b4f48-86cd-4fdf-547d-a0dff619c095
---

# Antivirus policy settings for Windows Security experience policy for Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Note

This article details the settings in the Windows Security experience profile for the *Windows 10 and later* platform for endpoint security Antivirus policy. Beginning on April, 5 2022, the *Windows 10 and later* platform was replaced by the *Windows* platform. Although you can no longer create new instances of the original profile, you can continue to edit and use your existing profiles.

**Windows Security**:

- **Enable tamper protection to prevent Microsoft Defender being disabled**[Prevent changes to security settings with Tamper Protection](https://go.microsoft.com/fwlink/?linkid=2066083)

    - **Not configured** (*default*) - When the *Enable* or *Disable* state exists on a client, deploying *Not configured* has no impact on the setting.
    - **Enable** - Enable the Tamper Protection restriction. To change the state from either enabled or disabled, deploy the opposite setting to have effect.
    - **Disable** - Disable the Tamper Protection restrictions. To change the state from either enabled or disabled, deploy the opposite setting to have effect.

    **Hide the Virus and threat protection area in the Windows Security app** CSP: [DisableVirusUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablevirusui)

    - **Not configured** (*default*) - The setting returns to the client default, which is to allow user access and notifications.
    - **Yes** - The virus and threat protection area in the Windows Security app is hidden from end-users. Virus and threat protection-related notifications are suppressed.
    - **No** - Behavior is the same as *Not configured*.

    When this setting is configured as *No* or *Not configured*, the following setting is available:

    - **Hide the Ransomware data recovery option in the Windows Security app** CSP: [HideRansomwareDataRecovery](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-hideransomwaredatarecovery)

        This setting is only available when *Hide the Virus and threat protection area in the Windows Security app* is set to *No* or *Not configured*.

        - **Not configured** (*default*) - The setting returns to the client default, which is to allow user access and notifications.
        - **Yes** - The ransomware data recovery area in the Windows Security app is hidden from end-users. Ransomware related notifications are suppressed.
        - **No** - Behavior is the same as *Not configured*.
- **Hide the Account protection area in the Windows Security app** CSP: [DisableAccountProtectionUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disableaccountprotectionui)

    - **Not configured** (*default*) - The setting returns to the client default, which is to allow user access and notifications.
    - **Yes** - The account protection area in the Windows Security app is hidden from end-users. Account protection-related notifications are suppressed.
    - **No** - Behavior is the same as *Not configured*.
- **Hide the Firewall and network protection area in the Windows Security app** CSP: [DisableNetworkUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablenetworkui)

    - **Not configured** (*default*) - The setting returns to the client default, which is to allow user access and notifications.
    - **Yes** - The firewall and network protection area in the Windows Security are hidden from end-users. Firewall and network protection-related notifications are suppressed.
    - **No** - Behavior is the same as *Not configured*.
- **Hide the App and browser control area in the Windows Security app** CSP: [DisableAppBrowserUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disableappbrowserui)

    - **Not configured** (*default*) - The setting returns to the client default, which is to allow user access and notifications.
    - **Yes** - The app and browser control area in the Windows Security is hidden from end-users. App and browser control related notifications are suppressed.
    - **No** - Behavior is the same as *Not configured*.
- **Hide the Device security area in the Windows Security app** CSP: [DisableDeviceSecurityUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disabledevicesecurityui)

    - **Not configured** (*default*) - The setting returns to the client default, which is to allow user access and notifications.
    - **Yes** - The hardware protection area in the Windows Security app is hidden from end-users. Hardware protection-related notifications will be suppressed.
    - **No** - Behavior is the same as *Not configured*.
- **Hide the Device performance and health area in the Windows Security app** CSP: [DisableHealthUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablehealthui)

    - **Not configured** (*default*) - The setting returns to the client default, which is to allow user access and notifications.
    - **Yes** - The device performance and health area in the Windows Security app are hidden from end-users. Device performance and health-related notifications ware suppressed
    - **No** - Behavior is the same as *Not configured*.
- **Hide the Family options area in the Windows Security app** CSP: [DisableFamilyUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablefamilyui)

    - **Not configured** (*default*) - The setting returns to the client default, which is to allow user access and notifications.
    - **Yes** - The family options area in the Windows Security app is hidden from end-users. Also, notifications related to family options are suppressed.
    - **No** - Behavior is the same as *Not configured*.
- **Windows Security app notifications** CSP: [DisableNotifications](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablenotifications)

    Use this setting to block Windows Security notifications to your users for all of the preceding feature settings. Alternatively, you can manage the Windows Security app notifications per feature by using the proceeding settings.

    - **Not configured** (*default*) - This setting doesn't enforce a block of any settings and all Windows Security app notifications that are not controlled by another setting are allowed.
    - **Block non-critical notification** - Notifications such as scan completions are blocked.
    - **Block all notifications** - Critical and non-critical notifications are blocked for all Windows Security features.
- **Hide the Windows Security icon from the notification area** CSP: [HideWindowsSecurityNotificationAreaControl](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

    For this setting to take effect, the user needs to either sign out and back in, or reboot the computer.

    - **Not configured** (*default*) - The setting returns the client to the default, which is to show the icon.
    - **Yes** - Hide the Windows Security icon from the notification area.
    - **No** - Behavior is the same as *Not configured*.
- **Disable the Clear TPM option in the Windows Security app** CSP: [DisableClearTpmButton](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

    - **Not configured** (*default*) - The setting returns to the client default, which allows access to the button.
    - **Yes** - Disable access to the clear TPM button in the Windows Security app.
    - **No** - Behavior is the same as *Not configured*.
- **Prompt users to update TPM firmware if vulnerability is discovered** CSP: [DisableTpmFirmwareUpdateWarning](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

    - **Not configured** (*default*) - The setting returns to the client default, which is to not prompt users.
    - **Yes** - Allow Windows to prompt end-users when a potential vulnerability is found in their TPM firmware. Users are then encouraged to run firmware updates to resolve the vulnerability.
    - **No** - Behavior is the same as *Not configured*.
- **Organization's support contact information** CSP: [EnableCustomizedToasts](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-enablecustomizedtoasts)

    Declare where you would like your IT organization information displayed in the Windows Security app and notifications.

    - **Not configured** (*default*)
    - **Display in app and in notifications**
    - **Display only in app**
    - **Display only in notifications**