---
layout: Conceptual
title: Windows Antivirus policy settings from Windows security settings for tenant attached devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-windows-security-settings-tenant-attach
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
description: Review the settings in the *Windows Security experience* profile for tenant attached devices. To use this Endpoint security Antivirus policy, you must first configure tenant attach for Configuration Manager for Microsoft Intune.
ms.date: 2025-03-28T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mattcall
locale: en-us
document_id: fbad8cda-78cc-521f-a1b6-402772aad10b
document_version_independent_id: fbad8cda-78cc-521f-a1b6-402772aad10b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-windows-security-settings-tenant-attach.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-windows-security-settings-tenant-attach
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-windows-security-settings-tenant-attach.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/691e3042-55ad-4ce1-b5e9-649b1cc47b5c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b7d11190-096c-4ddb-87db-63764f603aac
platformId: 27acc274-3109-56bb-605b-49b5e8c60cdf
---

# Windows Antivirus policy settings from Windows security settings for tenant attached devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

View the Windows Security experience settings you can manage with the **Windows Security experience (preview)** profile from Intune.

The profile is available when you configure [Intune Endpoint security Antivirus policy](antivirus). This profile supports devices you manage with Configuration Manager after configuring the [tenant attach](../../fundamentals/tenant-attach) scenario for Intune.

## Windows Security

- **Enable tamper protection to prevent Microsoft Defender being disabled**[Prevent changes to security settings with Tamper Protection](https://go.microsoft.com/fwlink/?linkid=2066083)

    - **Not configured**
    - **Enabled**
    - **Disabled**
- **Hide the Account protection area in the Windows Security app** CSP: [DisableAccountProtectionUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disableaccountprotectionui)

    - **Not configured** (*default*)
    - **(Disable)** The users can see the display of the Account protection area in Windows Defender Security Center.
    - **(Enable)** The users can see the display of the Account protection area in Windows Defender Security Center.
- **Hide the App and browser control area in the Windows Security app** CSP: [DisableAppBrowserUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disableappbrowserui)

    - **Not configured** (*default*)
    - **(Disable)** The users can see the display of the app and browser protection area in Windows Defender Security Center.
    - **(Enable)** The users cannot see the display of the app and browser protection area in Windows Defender Security Center.
- **Disable the Clear TPM option in the Windows Security app** CSP: [DisableClearTpmButton](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

    - **Not configured** (*default*)
    - **(Disable)** The security processor troubleshooting page shows a button that initiates the process to clear the security processor (TPM).
    - **(Enable)** The security processor troubleshooting page will not show a button that initiates the process to clear the security processor (TPM).
- **Hide the Family options area in the Windows Security app** CSP: [DisableFamilyUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablefamilyui)

    - **Not configured** (*default*)
    - **(Disable)** The users can see the display of the family options area in Windows Defender Security Center.
    - **(Enable)** The users cannot see the display of the family options area in Windows Defender Security Center.
- **Hide the Device security area in the Windows Security app** CSP: [DisableDeviceSecurityUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disabledevicesecurityui)

    - **Not configured** (*default*)
    - **(Disable)** The users can see the display of the Device security area in Windows Defender Security Center.
    - **(Enable)** The users cannot see the display of the Device security area in Windows Defender Security Center.
- **Hide the Device performance and health area in the Windows Security app** CSP: [DisableHealthUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablehealthui)

    - **Not configured** (*default*)
    - **(Disable)** The users can see the display of the device performance and health area in Windows Defender Security Center.
    - **(Enable)** The users cannot see the display of the device performance and health area in Windows Defender Security Center.
- **Hide the Firewall and network protection area in the Windows Security app** CSP: [DisableNetworkUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablenetworkui)

    - **Not configured** (*default*)
    - **(Disable)** The users can see the display of the firewall and network protection area in Windows Defender Security Center.
    - **(Enable)** The users cannot see the display of the firewall and network protection area in Windows Defender Security Center.
- **Hide the Windows Security icon from the notification area** CSP: [HideWindowsSecurityNotificationAreaControl](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

    - **Not configured** (*default*)
    - **Enabled**
- **Hide the Ransomware data recovery option in the Windows Security app** CSP: [HideRansomwareDataRecovery](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-hideransomwaredatarecovery)

    - **Not configured** (*default*)
    - **(Disable)** The Ransomware data recovery area will be visible.
    - **(Enable)** The Ransomware data recovery area is hidden.
- **Hide the Virus and threat protection area in the Windows Security app** CSP: [DisableVirusUI](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablevirusui)

    - **Not configured** (*default*)
    - **(Disable)** The users can see the display of the virus and threat protection area in Windows Defender Security Center.
    - **(Enable)** The users cannot see the display of the virus and threat protection area in Windows Defender Security Center.
- **Prompt users to update TPM firmware if vulnerability is discovered** CSP: [DisableTpmFirmwareUpdateWarning](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

    - **Not configured** (*default*)
    - **(Disabled or Not configured)** A warning will be displayed if the firmware of the security processor (TPM) should be updated for TPMs that have a vulnerability.
    - **(Enabled)** No warning will be displayed if the firmware of the security processor (TPM) should be updated.
- **Organization's support email address** CSP: [EnableCustomizedToasts](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-enablecustomizedtoasts)
- **Organization's support phone number** CSP: [EnableCustomizedToasts](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-enablecustomizedtoasts)
- **Organization's support web address** CSP: [EnableCustomizedToasts](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-enablecustomizedtoasts)
- **Organization's support contact name** CSP: [EnableCustomizedToasts](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-enablecustomizedtoasts)
- **Disable Notifications** CSP: [DisableNotifications](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablenotifications)

    - **Not configured** (*default*)
    - **(Disable)** The users can see the display of Windows Defender Security Center notifications.
    - **(Enable)** The users cannot see the display of Windows Defender Security Center notifications.
- **Disable Enhanced Notifications** CSP: [DisableEnhancedNotifications](/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disableenhancednotifications)

    - **Not configured** (*default*)
    - **(Disable)** Windows Defender Security Center will display critical and non-critical notifications to users.
    - **(Enable)** Windows Defender Security Center only displays notifications that are considered critical on clients.