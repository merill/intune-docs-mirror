---
layout: Conceptual
title: Windows Antivirus policy settings for Microsoft Defender Antivirus for Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-windows
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
description: See a list of the settings in the Microsoft Defender Antivirus profile for Windows devices. You can configure these settings as part of Endpoint security Antivirus policy in Microsoft Intune.
ms.date: 2026-08-20T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: laarrizz
ms.custom: msecd-doc-authoring-1015
ai-usage: ai-assisted
locale: en-us
document_id: 5338366e-8fab-d84c-9bb0-8ac666cce750
document_version_independent_id: 5338366e-8fab-d84c-9bb0-8ac666cce750
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-antivirus-defender-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-windows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 1b5d1ea8-9742-452e-cb18-17cdbbb5ff17
---

# Windows Antivirus policy settings for Microsoft Defender Antivirus for Intune - Microsoft Intune | Microsoft Learn

View details about the [endpoint security](manage-policies) antivirus policy settings you can configure for the Microsoft Defender Antivirus profile for Windows in Microsoft Intune.

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Note

This article details the settings you can find in Microsoft Defender Antivirus and Microsoft Defender Antivirus Exclusions profiles created before April 5, 2022, for the *Windows 10 and later* platform for endpoint security Antivirus policy. On April 5, 2022, the *Windows 10 and later* platform was replaced by the *Windows* platform. Profiles created after that date use a new settings format as found in the Settings Catalog. With this change you can no longer create new versions of the old profile and they are no longer being developed. Although you can no longer create new instances of the older profile, you can continue to edit and use instances of it that you previously created.

For profiles that use the new settings format, Intune no longer maintains a list of each setting by name. Instead, the name of each setting, its configuration options, and its explanatory text you see in the Microsoft Intune admin center are taken directly from the settings authoritative content. That content can provide more information about the use of the setting in its proper context. When viewing a settings information text, you can use its *Learn more* link to open that content.

The following settings details for Windows profiles apply to those deprecated profiles.

## Cloud protection

- **Turn on cloud-delivered protection** CSP: [AllowCloudProtection](/en-us/windows/client-management/mdm/policy-csp-defender#allowcloudprotection)

    By default, Defender on Windows desktop devices sends information to Microsoft about any problems it finds. Microsoft analyzes that information to learn more about problems affecting you and other customers, to offer improved solutions.

    - **Not configured** (*default*) - The setting is restored to the system default.
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Cloud-delivered protection is turned on. Device users can't change this setting.
- **Cloud-delivered protection level** CSP: [CloudBlockLevel](/en-us/windows/client-management/mdm/policy-csp-defender#cloudblocklevel)

    Configure how aggressive Defender Antivirus is in blocking and scanning suspicious files.

    - **Not configured** (*default*) - Default Defender blocking level.
    - **High** - Aggressively block unknowns while optimizing client performance, which includes a greater chance of false positives.
    - **High plus** - Aggressively block unknowns and apply additional protection measures that might affect client performance.
    - **Zero tolerance** - Block all unknown executable files.
- **Defender cloud extended timeout in seconds** CSP: [CloudExtendedTimeout](/en-us/windows/client-management/mdm/policy-csp-defender#cloudextendedtimeout)

    Defender Antivirus automatically blocks suspicious files for 10 seconds while it scans them in the cloud to make sure they're safe. You can add up to 50 additional seconds to this timeout.

## Microsoft Defender Antivirus Exclusions

Warning

**Defining exclusions lowers the protection offered by Microsoft Defender Antivirus**. Always evaluate the risks that are associated with implementing exclusions. Only exclude files you know aren't malicious.

For more information, see [Exclusions overview](/en-us/defender-endpoint/navigate-defender-endpoint-antivirus-exclusions) in the Microsoft Defender documentation.

The following settings are available in the Microsoft Defender Antivirus profile:

- **Defender local admin merge** CSP: [Configuration/DisableLocalAdminMerge](/en-us/windows/client-management/mdm/defender-csp)

    This setting controls if exclusion list settings that are configured by a local administrator merge with managed settings from Intune policy. This setting applies to lists such as threats and exclusions.

    - **Not configured***(default)* - Unique items defined in preference settings that are configured by a local administrator merge into the resulting effective policy. If there are conflicts, management settings from Intune policy override local preference settings.
    - **No** - Behavior is the same as *Not configured*.
    - **Yes** - Only items defined by management are used in the resulting effective policy. Managed settings override preference settings that are configured by the local administrator.

The following settings are available in the following profiles:

- Microsoft Defender Antivirus
- Microsoft Defender Antivirus Exclusions

For each setting in this group, you can expand the setting, select **Add**, and then specify a value for the exclusion.

- **Defender processes to exclude** CSP: [ExcludedProcesses](/en-us/windows/client-management/mdm/policy-csp-defender#excludedprocesses)

    Specify a list of files opened by processes to ignore during a scan. The process itself isn't excluded from the scan.
- **File extensions to exclude from scans and real-time protection** CSP: [ExcludedExtensions](/en-us/windows/client-management/mdm/policy-csp-defender#excludedextensions)

    Specify a list of file type extensions to ignore during a scan.
- **Defender files and folders to exclude** CSP: [ExcludedPaths](/en-us/windows/client-management/mdm/policy-csp-defender#excludedpaths)

    Specify a list of files and directory paths to ignore during a scan.

## Real-time protection

These settings are available in the following profiles:

- Microsoft Defender Antivirus

**Settings**:

- **Turn on real-time protection** CSP: [AllowRealtimeMonitoring](/en-us/windows/client-management/mdm/policy-csp-defender#allowrealtimemonitoring)

    Require Defender on Windows desktop devices to use the real-time Monitoring functionality.

    - **Not configured** (*default*) - The setting is restored to the system default
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Enforce use of real-time monitoring. Device users can't change this setting.
- **Enable on access protection** CSP: [AllowOnAccessProtection](/en-us/windows/client-management/mdm/policy-csp-defender#allowonaccessprotection) Configure virus protection that's continuously active, as opposed to on demand.

    - **Not Configured** (*default*) - The setting is restored to the system default.
    - **No** - Block On Access Protection on devices. Device users can't change this setting.
    - **Yes** - On Access Protection is active on devices.
- **Monitoring for incoming and outgoing files** CSP: [Defender/RealTimeScanDirection](/en-us/windows/client-management/mdm/policy-csp-defender)

    Configure this setting to determine which NTFS file and program activity is monitored.

    - **Monitor all files** (*default*)
    - **Only monitor incoming files**
    - **Only monitor outgoing files**
- **Turn on behavior monitoring** CSP: [AllowBehaviorMonitoring](/en-us/windows/client-management/mdm/policy-csp-defender#allowbehaviormonitoring)

    By default, Defender on Windows desktop devices uses the Behavior Monitoring functionality.

    - **Not configured** (*default*) - The setting is restored to the system default.
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Enforce use of real-time behavior monitoring. Device users can't change this setting.
- **Turn on network protection** CSP: [EnableNetworkProtection](/en-us/windows/client-management/mdm/policy-csp-defender#enablenetworkprotection)

    Protect device users using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. Protection includes preventing third-party browsers from connecting to dangerous sites.

    - **Not configured** (*default*) - The setting is restored to the system default.
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Network protection is turned on. Device users can't change this setting.
- **Scan all downloaded files and attachments** CSP: [AllowIOAVProtection](/en-us/windows/client-management/mdm/policy-csp-defender#allowioavprotection)

    Configure Defender to scan all downloaded files and attachments.

    - **Not configured** (*default*) - The setting is restored to the system default.
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Defender scans all downloaded files and attachments. Device users can't change this setting.
- **Scan scripts that are used in Microsoft browsers** CSP: [AllowScriptScanning](/en-us/windows/client-management/mdm/policy-csp-defender)

    Configure Defender to scan scripts.

    - **Not configured** (*default*) - The setting is restored to the system default.
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Defender scans scripts. Device users can't change this setting.
- **Scan network files** CSP: [AllowScanningNetworkFiles](/en-us/windows/client-management/mdm/policy-csp-defender#allowscanningnetworkfiles)

    Configure Defender to scan network files.

    - **Not configured** (*default*) - The setting is restored to the system default.
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Turn on scanning of network files. Device users can't change this setting.
- **Scan emails** CSP: [AllowEmailScanning](/en-us/windows/client-management/mdm/policy-csp-defender#allowemailscanning)

    Configure Defender to scan incoming email.

    - **Not configured** (*default*) - The setting is restored to the system default.
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Turn on email scanning. Device users can't change this setting.

## Remediation

These settings are available in the following profiles:

- Microsoft Defender Antivirus

**Settings**:

- **Number of days (0-90) to keep quarantined malware** CSP: [DaysToRetainCleanedMalware](/en-us/windows/client-management/mdm/policy-csp-defender#daystoretaincleanedmalware)

    Specify the number of days from zero to 90 that the system stores quarantined items before they're automatically removed. A value of zero keeps items in quarantine and doesn't automatically remove them.
- **Submit samples consent**

    - **Not configured** (*default*)
    - **Send safe samples automatically**
    - **Always prompt**
    - **Never send**
    - **Send all samples automatically**
- **Action to take on potentially unwanted apps** CSP: [PUAProtection](/en-us/windows/client-management/mdm/policy-csp-defender#puaprotection)

    Specify the level of detection for potentially unwanted applications (PUAs). Defender alerts users when potentially unwanted software is being downloaded or attempts to install on a device.

    - **Not configured** (*default*) - The setting is restored to the system default, which is PUA Protection OFF.
    - **Disable**
    - **Enable** - Detected items are blocked, and show in history along with other threats.
    - **Audit mode** - Defender detects potentially unwanted applications, but takes no action. You can review information about the applications Defender would have taken action against by searching for events that are created by Defender in the Event Viewer.
- **Actions for detected threats** CSP: [ThreatSeverityDefaultAction](/en-us/windows/client-management/mdm/policy-csp-defender#threatseveritydefaultaction)

    Specify the action that Defender takes for detected malware based on the malware's threat level.

    Defender classifies malware that it detects as one of the following severity levels:

    - **Low severity**
    - **Moderate severity**
    - **High severity**
    - **Severe severity**

    For each level, specify the action to take. The default for each severity level is *Not configured*.

    - **Not configured** - When not configured, action based on the security intelligence update definition is applied.
    - **Clean** - The service tries to recover files and try to disinfect.
    - **Quarantine** - Moves files to quarantine.
    - **Remove** - Removes files from the device.
    - **Allow** - Allows the file and doesn't take other actions.
    - **User defined** - The device user makes the decision on which action to take.
    - **Block** - Blocks file execution.

## Scan

These settings are available in the following profiles:

- Microsoft Defender Antivirus

**Settings**:

- **Scan archive files** CSP: [AllowArchiveScanning](/en-us/windows/client-management/mdm/policy-csp-defender#allowarchivescanning)

    Configure Defender to scan archive files, like ZIP or CAB files.

    - **Not configured** (*default*) - The setting returns to the client default, which is to scan archived files, however the user may disable setting. Learn more
    - **No** - File archives aren't scanned. Device users can't change this setting.
    - **Yes** - Enable scans of archive files. Device users can't change this setting.
- **Use low CPU priority for scheduled scans** CSP: [EnableLowCPUPriority](/en-us/windows/client-management/mdm/policy-csp-defender#enablelowcpupriority)

    Configure CPU priority for scheduled scans.

    - **Not configured** (*default*) - The setting returns to the system default, in which no changes to CPU priority are made.
    - **No** - The setting is disabled. Device users can't change this setting.
    - **Yes** - Low CPU priority will be used during scheduled scans. Device users can't change this setting.
- **Disable catch-up full scan** CSP: [DisableCatchupFullScan](/en-us/windows/client-management/mdm/policy-csp-defender#disablecatchupfullscan)

    Configure whether Defender runs a catch-up full scan after a device misses scheduled full scans. Because the setting name begins with *Disable*, **Yes** disables catch-up full scans, and **No** enables them.

    - **Not configured** (*default*) - The setting uses the client default, which disables catch-up full scans.
    - **No** - The **Disable catch-up full scan** setting is disabled, so catch-up full scans are enabled. If a device misses two consecutive scheduled full scans, a catch-up scan starts the next time someone signs in. Catch-up scans require a configured scheduled scan. Device users can't change this setting.
    - **Yes** - The **Disable catch-up full scan** setting is enabled, so catch-up full scans are disabled. Device users can't change this setting.
- **Disable catchup quick scan** CSP: [DisableCatchupQuickScan](/en-us/windows/client-management/mdm/policy-csp-defender#disablecatchupquickscan)

    Configure whether Defender runs a catch-up quick scan after a device misses scheduled quick scans. Because the setting name begins with *Disable*, **Yes** disables catch-up quick scans, and **No** enables them.

    - **Not configured** (*default*) - The setting uses the client default, which enables catch-up quick scans.
    - **No** - The **Disable catch-up quick scan** setting is disabled, so catch-up quick scans are enabled. If a device misses two consecutive scheduled quick scans, a catch-up scan starts the next time the device powers on or resumes from sleep or hibernation. Catch-up scans require a configured scheduled scan. Device users can't change this setting.
    - **Yes** - The **Disable catch-up quick scan** setting is enabled, so catch-up quick scans are disabled. Device users can't change this setting.
- **CPU usage limit per scan** CSP: [AvgCPULoadFactor](/en-us/windows/client-management/mdm/policy-csp-defender#avgcpuloadfactor)

    Specify as a percent from zero to 100, the average CPU load factor for the Defender scan.
- **Scan mapped network drives during full scan** CSP: [AllowFullScanOnMappedNetworkDrives](/en-us/windows/client-management/mdm/policy-csp-defender#allowfullscanonmappednetworkdrives)

    Configure Defender to scan mapped network drives.

    - **Not configured** (*default*) - The setting is restored to the system default, which disables scanning on mapped network drives.
    - **No** - The setting is disabled. Device users can't change the setting.
    - **Yes** - Enable scans of mapped network drives. Device users can't change this setting.
- **Run daily quick scan at** CSP: [ScheduleQuickScanTime](/en-us/windows/client-management/mdm/policy-csp-defender#schedulequickscantime)

    Select the time of day that Defender quick scans run. This setting applies only when a device runs a quick scan and doesn't interact with the following three settings:

    - Scan type
    - Day of week to run a scheduled scan
    - Time of day to run a scheduled scan

    By default, *Run daily quick scan at* is set to **Not configured**.
- **Scan type** CSP: [ScanParameter](/en-us/windows/client-management/mdm/policy-csp-defender#scanparameter)

    Select the type of scan that Defender runs. This setting interacts with the settings *Day of week to run a scheduled scan* and *Time of day to run a scheduled scan*.

    - **Not Configured** (*default*)
    - **Quick scan**
    - **Full scan**
- **Day of week to run a scheduled scan**

    - **Not Configured** (*default*)
- **Time of day to run a scheduled scan**

    - **Not Configured** (*default*)
- **Check for signature updates before running scan**

    - **Not Configured** (*default*)
    - **No**
    - **Yes**

## Updates

These settings are available in the following profiles:

- Microsoft Defender Antivirus

**Settings**:

- **Enter how often (0-24 hours) to check for security intelligence updates** CSP: [SignatureUpdateInterval](/en-us/windows/client-management/mdm/policy-csp-defender)

    Specify the interval from zero to 24 (in hours) that is used to check for signatures. A value of zero results in no check for new signatures. A value of 2 will check every two hours, and so on.
- **Define file shares for downloading definition updates** CSP: [SignatureUpdateFallbackOrder](/en-us/windows/client-management/mdm/policy-csp-defender#signatureupdatefallbackorder)

    Manage locations, like a UNC file share, as a download source location to get definition updates. After definition updates successfully download from a specified source, the remaining sources in the list won't be contacted.

    You can **Add** individual locations, or **Import** a list of locations as a .csv file.
- **Define the order of sources for downloading definition updates** CSP: [SignatureUpdateFileSharesSources](/en-us/windows/client-management/mdm/policy-csp-defender#signatureupdatefilesharessources)

    Specify in which order to contact source locations you've specified, to get definition updates. After definition updates have successfully downloaded from one specified source, the remaining sources in the list won't be contacted.

## User experience

These settings are available in the following profiles:

- Microsoft Defender Antivirus

**Settings**:

- **Allow user access to Microsoft Defender app** CSP: [AllowUserUIAccess](/en-us/windows/client-management/mdm/policy-csp-defender#allowuseruiaccess)
- **Not Configured** (*default*) - The setting returns to client default in which UI and notifications are allowed.
- **No** - The Defender User Interface (UI) is inaccessible and notifications ware suppressed.
- **Yes**