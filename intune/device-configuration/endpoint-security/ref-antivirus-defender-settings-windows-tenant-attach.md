---
layout: Conceptual
title: Windows Antivirus policy settings from Microsoft Defender Antivirus for tenant attached devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach
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
description: See a list of the settings in the Microsoft Defender Antivirus profile for Windows devices managed by Configuration Manager. You can configure these settings as part of Endpoint security Antivirus policy in Microsoft Intune after you configure tenant attach for Configuration Manager.
ms.date: 2026-08-20T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mattcall
ms.custom: msecd-doc-authoring-1015
ai-usage: ai-assisted
locale: en-us
document_id: 8d3811c8-cc30-7d72-0727-817493f29f60
document_version_independent_id: 8d3811c8-cc30-7d72-0727-817493f29f60
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 231697be-b1f1-9ee0-edb7-b09c5669e37c
---

# Windows Antivirus policy settings from Microsoft Defender Antivirus for tenant attached devices - Microsoft Intune | Microsoft Learn

View the Microsoft Defender Antivirus settings you can manage with the **Microsoft Defender Antivirus Policy (ConfigMgr)** profile from Intune. The profile is available when you configure Intune [Endpoint security Antivirus policy](antivirus), and the policy deploys to devices you manage with Configuration Manager when you've configured the [tenant attach](../../fundamentals/tenant-attach) scenario. (Path in the Microsoft Intune admin center: *Endpoint security* &gt; *Antivirus* &gt; *+ Create Policy* &gt; Platform = *Windows (ConfigMgr)* &gt; Profile = *Microsoft Defender Antivirus*.)

## Cloud protection

- **Turn on cloud-delivered protection** CSP: [AllowCloudProtection](/en-us/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

    By default, Defender on Windows desktop devices sends information to Microsoft about any problems it finds. Microsoft analyzes that information to learn more about problems affecting you and other customers, to offer improved solutions.

    - **Not Configured** (*default*) - The setting is restored to the system default.
    - **No** Turns off the Microsoft Active Protection Service.
    - **Yes** Turns on the Microsoft Active Protection Service.
- **Cloud-delivered protection level** CSP: [CloudBlockLevel](/en-us/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)

    Configure how aggressive Defender Antivirus is in blocking and scanning suspicious files.

    - **Not Configured** (*default*) - Default Defender blocking level.
    - **High** - Aggressively block unknowns while optimizing client performance, which includes a greater chance of false positives.
    - **High Plus** - Aggressively block unknowns and apply extra protection measures that might impact client performance.
    - **Zero Tolerance** - Block all unknown executable files.
- **Defender Cloud Extended Timeout in Seconds** CSP: [CloudExtendedTimeout](/en-us/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)

    Defender Antivirus automatically blocks suspicious files for 10 seconds so it can scan the files in the cloud to make sure they're safe. With this setting, you can add up to 50 more seconds to this timeout.

## Microsoft Defender Antivirus Exclusions

Warning

**Defining exclusions lowers the protection offered by Microsoft Defender Antivirus**. Always evaluate the risks that are associated with implementing exclusions. Only exclude files you know aren't malicious.

For more information, see [Exclusions overview](/en-us/defender-endpoint/navigate-defender-endpoint-antivirus-exclusions) in the Microsoft Defender documentation.

For each setting in this group, you can expand the setting, select **Add**, and then specify a value for the exclusion.

- **Defender Processes To Exclude** CSP: [ExcludedProcesses](/en-us/windows/client-management/mdm/policy-csp-defender#defender-excludedprocesses)

    Specify a list of files opened by processes to ignore during a scan. The process itself isn't excluded from the scan.
- **File extensions to exclude from scans and real-time protection** CSP: [ExcludedExtensions](/en-us/windows/client-management/mdm/policy-csp-defender#defender-excludedextensions)

    Specify a list of file type extensions to ignore during a scan.
- **Defender Files And Folders To Exclude** CSP: [ExcludedPaths](/en-us/windows/client-management/mdm/policy-csp-defender#defender-excludedpaths)

    Specify a list of files and directory paths to ignore during a scan.

## Real-time protection

- **Turn on real-time protection** CSP: [AllowRealtimeMonitoring](/en-us/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

    Require Defender on Windows desktop devices to use the real-time Monitoring functionality.

    - **Not Configured** (*default*) - The setting is restored to the system default
    - **No** Turns off the real-time monitoring service.
    - **Yes** Turns on and runs the real-time monitoring service.
- **Enable on access protection** CSP: [AllowOnAccessProtection](/en-us/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection)

    Configure virus protection that's continuously active, as opposed to on demand.

    - **Not Configured** (*default*) - This policy doesn't alter the state of this setting on a device. The existing state on the device remains unchanged.
    - **No** Turns off the real-time monitoring service.
    - **Yes**
- **Monitoring for incoming and outgoing files** CSP: [Defender/RealTimeScanDirection](/en-us/windows/client-management/mdm/policy-csp-defender)

    Configure this setting to determine which NTFS file and program activity is monitored.

    - **Monitor all files (bi-directional)** (*default*)
    - **Monitor incoming files**
    - **Monitor outgoing files**
- **Turn on behavior monitoring** CSP: [AllowBehaviorMonitoring](/en-us/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

    By default, Defender on Windows desktop devices uses the Behavior Monitoring functionality.

    - **Not Configured** (*default*) - The setting is restored to the system default.
    - **No** Turns off behavior monitoring.
    - **Yes** Turns on real-time behavior monitoring.
- **Allow Intrusion Prevention System**

    Configure Defender to allow or disallow Intrusion Prevention functionality.

    - **Not Configured** (*default*) - The setting is restored to the system default.
    - **No** - Intrusion Prevention System is not allowed.
    - **Yes** - Intrusion Prevention System is allowed.
- **Scan all downloaded files and attachments** CSP: [EnableNetworkProtection](/en-us/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

    Configure Defender to scan all downloaded files and attachments.

    - **Not Configured** (*default*) - The setting is restored to the system default.
    - **No**
    - **Yes**
- **Scan scripts that are used in Microsoft browsers** CSP: [AllowScriptScanning](/en-us/windows/client-management/mdm/policy-csp-defender)

    Configure Defender to scan scripts.

    - **Not Configured** (*default*) - The setting is restored to the system default.
    - **No**
    - **Yes**
- **Scan network files** CSP: [AllowScanningNetworkFiles](/en-us/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

    Configure Defender to scan network files.

    - **Not Configured** (*default*) - The setting is restored to the system default.
    - **No** Turns off scanning of network files.
    - **Yes** Scans network files.
- **Scan emails** CSP: [AllowEmailScanning](/en-us/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

    Configure Defender to scan incoming email.

    - **Not Configured** (*default*) - The setting is restored to the system default.
    - **No** Turns off email scanning.
    - **Yes** Turns on email scanning.

## Remediation

- **Number of days (0-90) to keep quarantined malware** CSP: [DaysToRetainCleanedMalware](/en-us/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

    Specify a number of days from zero to 90 that the system stores quarantined items before they're automatically removed. A value of zero keeps items in quarantine and does not automatically remove them.
- **Submit Samples Consent**

    - **Not Configured** (*default*)
    - **Always prompt**
    - **Send safe samples automatically**
    - **Never send**
    - **Send all samples automatically**
- **Action to take on potentially unwanted apps** CSP: [PUAProtection](/en-us/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

    Specify the level of detection for potentially unwanted applications (PUAs). Defender alerts users when potentially unwanted software is being downloaded or attempts to install on a device.

    - **Not Configured** (*default*) - The setting is restored to the system default, which is PUA Protection OFF.
    - **Disabled** - Windows Defender will not protect against potentially unwanted applications.
    - **Enabled** - Detected items are blocked. They will show in history along with other threats.
    - **Audit mode** - Defender detects potentially unwanted applications, but takes no action. You can review information about the applications Defender would have taken action against by searching for events that are created by Defender in the Event Viewer.
- **Create a system restore point before computers are cleaned**

    - **Not Configured** (*default*)
    - **No**
    - **Yes**
- **Actions for detected threats** CSP: [ThreatSeverityDefaultAction](/en-us/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

    Specify the action that Defender takes for detected malware based on the malware's threat level.

    Defender classifies malware that it detects as one of the following severity levels:

    - **Low threat**
    - **Moderate threat**
    - **High threat**
    - **Severe threat**

    For each level, specify the action to take. The default for each severity level is *Not configured*.

    - **Not Configured** (*default*)
    - **Clean** - The service tries to recover files and try to disinfect.
    - **Quarantine** - Moves files to quarantine.
    - **Remove** - Removes files from the device.
    - **Allow** - Allows the file and doesn't take other actions.
    - **User defined** - The device user makes the decision on which action to take.
    - **Block** - Blocks file execution.

## Scan

- **Scan archive files** CSP: [AllowArchiveScanning](/en-us/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

    Configure Defender to scan archive files, like ZIP or CAB files.

    - **Not Configured** (*default*) - The setting returns to the client default, which is to scan archived files, however the user may disable the scan. Learn more
    - **No** Turns off scanning on archived files.
    - **Yes** Scans the archive files.
- **Enable low CPU priority for scheduled scans** CSP: [EnableLowCPUPriority](/en-us/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)

    Configure CPU priority for scheduled scans.

    - **Not Configured** (*default*) - The setting returns to the system default, in which no changes to CPU priority are made.
    - **No**
    - **Yes**
- **Disable Catch-up Full Scan** CSP: [DisableCatchupFullScan](/en-us/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)

    Configure whether Defender runs a catch-up full scan after a device misses scheduled full scans. Because the setting name begins with *Disable*, **Yes** disables catch-up full scans, and **No** enables them.

    - **Not Configured** (*default*) - The setting uses the client default, which disables catch-up full scans.
    - **No** - The **Disable catch-up full scan** setting is disabled, so catch-up full scans are enabled. If a device misses two consecutive scheduled full scans, a catch-up scan starts the next time someone signs in. Catch-up scans require a configured scheduled scan.
    - **Yes** - The **Disable catch-up full scan** setting is enabled, so catch-up full scans are disabled.
- **Disable Catchup Quick Scan** CSP: [DisableCatchupQuickScan](/en-us/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)

    Configure whether Defender runs a catch-up quick scan after a device misses scheduled quick scans. Because the setting name begins with *Disable*, **Yes** disables catch-up quick scans, and **No** enables them.

    - **Not Configured** (*default*) - The setting uses the client default, which enables catch-up quick scans.
    - **No** - The **Disable catch-up quick scan** setting is disabled, so catch-up quick scans are enabled. If a device misses two consecutive scheduled quick scans, a catch-up scan starts the next time the device powers on or resumes from sleep or hibernation. Catch-up scans require a configured scheduled scan.
    - **Yes** - The **Disable catch-up quick scan** setting is enabled, so catch-up quick scans are disabled.
- **CPU usage limit (0-100 percent) per scan** CSP: [AvgCPULoadFactor](/en-us/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)

    Specify as a percent from zero to 100, the average CPU load factor for the Defender scan.
- **Enable mapped network drives be scanned during a full scan** CSP: [AllowFullScanOnMappedNetworkDrives](/en-us/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

    Configure Defender to scan mapped network drives.

    - **Not Configured** (*default*) - The setting is restored to the system default, which disables scanning on mapped network drives.
    - **Not allowed** Disables scanning on mapped network drives.
    - **Allowed** Scans mapped network drives.
- **Run daily quick scan at** CSP: [ScheduleQuickScanTime](/en-us/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

    Select the time of day that Defender quick scans run. By default, this option is **Not Configured**
- **Scan Type** CSP: [ScanParameter](/en-us/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)

    Select the type of scan that Defender runs.

    - **Not Configured** (*default*)
    - **Quick scan**
    - **Full scan**
- **Day of week to run a scheduled scan**

    - **Not Configured** (*default*)
- **Time of day to run a scheduled scan**

    - **Not Configured** (*default*)
- **Check For Signature Updates Before Running Scan (Device)**

    - **Not Configured** (*default*)
    - **No**
    - **Yes**
- **Randomize scheduled scan and security intelligence update start times** -**Not Configured** (*default*) -**Yes** -**No**
- **Scan removable drives during full scan**

    - **Not Configured** (*default*)
    - **No** Turns off scanning on removable drives.
    - **Yes** Scans removable drives.

## Updates

- **Enter how often (0-24 hours) to check for security intelligence updates** CSP: [SignatureUpdateInterval](/en-us/windows/client-management/mdm/policy-csp-defender)

    Specify the interval from zero to 24 (in hours) that is used to check for signatures. A value of zero results in no check for new signatures. A value of 2 will check every two hours, and so on.

    - **Signature Update Fallback Order (Device)**
    - **Signature Update File Shares Sources (Device)**
- **Security Intelligence Location (Device)**

## User experience

- **Block user access to Microsoft Defender app**

    - **Not Configured** (*default*)
    - **Not allowed** Prevents users from accessing UI.
    - **Allowed** Lets users access UI.
- **Allow users to view the full History results**

    - **Not Configured** (*default*)
    - **Yes**
    - **No**