---
layout: Conceptual
title: What's new in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/whats-new/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
description: Find out what's new in Microsoft Intune.
ms.date: 2026-09-29T00:00:00.0000000Z
ms.topic: whats-new
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1023
ms.collection:
- M365-identity-device-management
locale: en-us
document_id: 215c0d3a-52dc-8b5e-b2cf-b0bc48e4fa30
document_version_independent_id: 215c0d3a-52dc-8b5e-b2cf-b0bc48e4fa30
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/whats-new/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: whats-new/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/whats-new/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: 5e3134c1-cb17-d9b3-ea93-be36e43875d6
---

# What's new in Microsoft Intune - Microsoft Intune | Microsoft Learn

Learn what's new each week in Microsoft Intune.

You can also read:

- **Important notices**
- [Past releases](archive) in the What's new archive
- Information about [how Intune service updates are released](../fundamentals/servicing-information)

Note

Each monthly [service update](../fundamentals/servicing-information) is rolled out gradually to help ensure quality and reliability. Updates are first validated in Microsoft internal environments, then to a small set of customer datacenters before expanding worldwide over the course of several days to a week. Some tenants might see changes before other tenants. The rollout is carefully monitored and might be paused or delayed to protect customers, which can affect timing.

Some features may gradually roll out over several weeks.

For a list of upcoming Intune feature releases, see [In development for Microsoft Intune](in-development).

For new information about Windows Autopilot solutions, see:

- [Windows Autopilot device preparation: What's new](/en-us/autopilot/device-preparation/whats-new)
- [Windows Autopilot: What's new](/en-us/autopilot/whats-new)

You can use RSS to be notified when this page is updated. For more information, see [How to use the docs](../fundamentals/use-docs#notifications).

## Week of September 28, 2026 (Service release 2609)

### Advanced capabilities (formerly "Microsoft Intune Suite")

#### Microsoft Cloud PKI support for US Government GCC High

Microsoft Cloud PKI is now available for Microsoft Intune tenants in the Microsoft Government Community Cloud High (GCC High) environment. You can create and manage a cloud-based public key infrastructure that automates certificate issuance, renewal, and revocation for Intune-managed devices without deploying an on-premises certification authority, Network Device Enrollment Service, or Intune Certificate Connector for device certificate delivery. Use these certificates for certificate-based authentication to organizational resources such as Wi-Fi, VPN, and applications. Support includes managed Windows, Android, iOS/iPadOS, and macOS devices. Cloud PKI isn't currently supported in the Department of Defense environment.

For more information, see [Overview of Microsoft Cloud PKI for Microsoft Intune](../cloud-pki/).

Applies to:

- Windows
- Android
- iOS/iPadOS
- macOS

#### Remote Help support for GCCH environments

Remote Help is now available in US Government Community Cloud High (GCCH) environments. This expansion extends the same secure, cloud-based remote assistance capabilities currently available in GCC to GCCH tenants.

IT support staff can establish Remote Help sessions with users on enrolled devices to provide real-time troubleshooting. Remote Help uses role-based access controls through Intune, and both helpers and sharers must sign in with their organization's Microsoft Entra ID accounts. DoD environments aren't supported.

For more information, see [Planning for Remote Help](../remote-help/plan).

Applies to:

- Android
- macOS
- Windows

### App management

#### Faster delivery of Win32 apps

Microsoft Intune now uses push notifications for admin-initiated and service-side changes to Win32 apps. Managed devices can check in sooner after app changes, reducing delivery and refresh delays compared with waiting for normal polling intervals. This update improves Win32 app deployment responsiveness without requiring a new admin workflow.

Applies to:

- Windows

#### Newly available protected app for Intune

Microsoft Dragon Copilot by Microsoft Corporation is now available as a protected app for Microsoft Intune. You can apply Intune app protection policies to the app on supported Android and iOS/iPadOS devices, helping protect organizational data while clinicians use its AI-assisted documentation capabilities.

For more information, see [Microsoft Intune protected apps](../app-management/ref-protected-apps).

Applies to:

- Android
- iOS/iPadOS

#### Require Managed Home Screen authentication for protected app activities

Microsoft Intune now helps prevent users from bypassing Managed Home Screen (MHS) authentication when they access protected activities in MAM-integrated apps. If MHS requires sign-in or a session PIN, the app redirects the user to MHS before allowing access to protected content. Assign an Intune app protection policy to both the app and the signed-in user; no specific app protection policy setting is required.

For more information, see [Configure the Microsoft Managed Home Screen app for Android Enterprise](../app-management/configuration/configure-managed-home-screen).

Applies to:

- Android Enterprise corporate-owned dedicated devices using Managed Home Screen with Microsoft Entra shared device mode

#### Faster Win32 app delivery after Windows enrollment

Microsoft Intune Management Extension now checks for Windows app assignments immediately after the Enrollment Status Page (ESP) completes. This reduces the delay before required Win32 apps that weren't installed during ESP begin installing on newly enrolled devices.

For more information, see [Intune Management Extension for Windows](../device-management/tools/management-extension-windows).

Applies to:

- Windows

### Device configuration

#### New Apple settings in the Settings Catalog for iOS/iPadOS and macOS

Microsoft Intune now includes new Apple Settings Catalog options for supported iOS/iPadOS and macOS devices. You can configure additional controls for areas such as app settings, Apple Intelligence, network and web-content filtering, and the macOS login window by using the same Settings Catalog policy workflow in the Microsoft Intune admin center.

For more information, see [Create a policy using settings catalog](../device-configuration/settings-catalog/).

Applies to:

- iOS/iPadOS
- macOS

#### Assignment filters for Android Settings Catalog policies

Microsoft Intune now supports assignment filters for Android Enterprise and Android Open Source Project (AOSP) Settings Catalog policies. You can include or exclude specific devices based on device properties, giving you more granular control over policy deployments and helping apply the right settings to the right Android devices.

For more information, see [Use assignment filters in Microsoft Intune](../fundamentals/filters/overview).

Applies to:

- Android Enterprise
- Android (AOSP)

### Device enrollment

#### Automatically launch Microsoft Defender for Endpoint during Android Enterprise device setup

Microsoft Intune now supports automatically opening Microsoft Defender for Endpoint during out-of-box setup for supported corporate-owned Android Enterprise devices. After you configure the Defender for Endpoint connector, turn on **Grant MTD role permissions**, and assign the Defender app as required, enable the experience from **Endpoint security** &gt; **Defender for Endpoint**. Intune opens Defender during enrollment so users can complete its initial configuration as part of device setup. If configuration isn't completed, the Intune setup step remains available so users can open Defender again.

For setup-time availability, assign Defender for Endpoint to user groups or all devices before enrollment. Assignment processing for a specific device group might not complete early enough for Defender to be available during setup.

Applies to:

- Android Enterprise corporate-owned fully managed devices (COBO)
- Android Enterprise corporate-owned devices with a work profile (COPE)

#### Skip the Device Features Tour during Apple enrollment

Microsoft Intune now includes the **Device features tour** Apple OS 27 Setup Assistant skip key in Automated Device Enrollment profiles. You can hide this pane to reduce setup interactions and provide a more streamlined enrollment experience on supported iPhone and iPad devices.

For more information, see [Set up automated device enrollment for iOS/iPadOS](../device-enrollment/apple/setup-automated-ios#setup-assistant-screen-reference).

Applies to:

- iOS/iPadOS

#### Upgrade an existing Android Enterprise connection to a managed Google domain

Microsoft Intune now supports an optional upgrade for tenants that connected Android Enterprise with a Gmail account. You can link the enterprise to a managed Google domain and manage the Google-Intune connection with your Microsoft Entra work account instead. Start at **Devices** &gt; **Enrollment**, select **Android**, and under **Prerequisites**, select **Managed Google Play**.

For more information, see [Connect your Intune account to your managed Google Play account](../device-enrollment/android/connect-managed-google-play#upgrade-to-a-managed-google-domain).

Applies to:

- Android Enterprise

### Device management

#### Updated minimum supported version for iOS and iPadOS

Microsoft Intune now requires iOS/iPadOS 18 or later for standard device-management, Company Portal, and app-protection scenarios. Administrators should identify and upgrade affected devices. Userless devices enrolled through Automated Device Enrollment have a separate support statement.

Applies to:

- iOS/iPadOS

#### New single device page becomes the default experience in the Intune admin center

Microsoft Intune now uses the new single device page as the default experience for all admins, and the previous device page is no longer available. In **Devices** &gt; **All devices**, select a device to view details and properties, monitor activity, access tools and reports, and perform supported actions from a consistent layout across platforms. Existing device-management capabilities remain available.

For more information, see [See device details in Microsoft Intune](../device-management/inventory-and-status/device-details).

Applies to:

- All platforms

### Device security

#### Configure MDE AI agent runtime protection for Windows

Microsoft Intune now includes Microsoft Defender for Endpoint AI agent runtime protection settings in the new endpoint security template for Windows. You can use **Audit** mode to detect and alert on unsafe AI agent activity without blocking it, or **Block** mode to stop threats before they execute. These settings support Windows devices managed through Intune or MDE security settings management.

For more information, see [AI agent runtime protection with Microsoft Defender for Endpoint](/en-us/defender-endpoint/ai-agent-runtime-protection-overview).

Applies to:

- Windows

#### Onboard MDM compliance partners with new self-service functionality

Microsoft Intune now supports bring-your-own connector functionality for MDM compliance partners. Partners can build, test, and onboard compliance connectors using Intune documentation, contracts, and validation hooks. As an admin, you can opt in to a partner connector by providing the vendor's information in the Microsoft Intune admin center, speeding partner onboarding and expanding the compliance solutions available to your organization.

For more information, see [Self-service onboarding for compliance partners](../device-security/compliance/third-party-partners#self-service-onboarding-for-compliance-partners).

Applies to:

- All supported platforms

## Week of September 21, 2026

### Device management

#### Stage app and policy rollout with deployment plans

Microsoft Intune now supports deployment plans, a new way to roll out apps and configuration policies in stages instead of all at once. From the new **Deployments** experience in the Intune admin center, you can stage a rollout across multiple rings, control rollout timing, and integrate with Multiple Admin Approval to reduce risk when deploying changes to large device fleets.

For more information, see [Deployment plans and deployments in Microsoft Intune](../device-management/deployments/overview).

Applies to:

- Windows
- Win32 and Enterprise app catalog apps
- Settings catalog and Endpoint security policies

## Week of September 14, 2026

### Device security

#### Faster compliance updates for Windows devices

Microsoft Intune now supports client-driven compliance evaluation for Windows devices. Supported devices can detect changes to compliance signals, including firewall, antivirus, BitLocker, Microsoft Defender status, operating system build, real-time protection, and Secure Boot, and proactively request reevaluation rather than waiting for a scheduled check-in. This provides faster compliance updates for remediation, reporting, and access decisions. Evaluation of compliance policies during check-in also occurs when a calculation is triggered.

For more information, see [Create a compliance policy in Microsoft Intune](../device-security/compliance/create-policy#client-driven-compliance-evaluation-preview).

Applies to:

- Windows

## Week of September 7, 2026

### Advanced capabilities (formerly "Microsoft Intune Suite")

#### New Remote Help for Windows version available

Remote Help for Windows version 5.2.1040.0 is now available. This release updates subscription metadata for E3, E5, and E7 licenses. Remote Help features are unchanged from version 5.2.1037.0.

Applies to:

- Windows

## Week of August 25, 2026 (Service release 2608)

### Advanced capabilities (formerly "Microsoft Intune Suite")

#### Unattended Remote Help sessions for Windows devices

Microsoft Intune now supports unattended Remote Help sessions on physical Windows devices. Authorized helpdesk agents can sign in to a remote device with their own credentials without requiring the user to be present or take action. Helpers can view and control the device to troubleshoot issues and complete support tasks remotely.

For more information, see [Planning for Remote Help](../remote-help/plan).

Applies to:

- Windows

### App management

#### Newly available protected apps for Intune

The following protected apps are now available for Microsoft Intune:

- Notion by Notion Labs
- Superhuman Mail by Superhuman Labs
- Calven by Calven Pty Limited
- Heijmans by Heijmans
- Notability by Ginger Labs, Inc. (iOS)
- Ben for Intune by Thanks Ben Ltd
- SDP - On Premises | Intune by Zoho Corporation

For more information about protected apps, see [Microsoft Intune protected apps](../app-management/ref-protected-apps).

#### Declarative Device Management for Apple volume purchase program apps

Microsoft Intune now supports Apple Declarative Device Management (DDM) for required volume purchase program (VPP) apps on devices running iOS/iPadOS 17.2 and later and macOS 26 and later. By changing the management type to DDM when you upload a new VPP token, you can deploy and configure apps using Apple's policy-based model, which improves delivery efficiency, provides real-time app status, and adds new per-app settings such as automatic app updates.

Applies to:

- iOS/iPadOS
- macOS

### Device configuration

#### Configure screen timeout for corporate Android devices

Microsoft Intune now supports a **Screen timeout** setting in the Android Enterprise settings catalog, letting you specify how many seconds pass before the screen turns off. Configure it under **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Android Enterprise** &gt; **Settings catalog**. The value must stay at or below **Time to lock screen** and applies to fully managed and dedicated devices on Android 9 and later, and corporate-owned work profile devices on Android 15 and later.

Applies to:

- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)
- Android Enterprise corporate-owned devices with a work profile (COPE)

#### Separate device and work profile passwords on Android Enterprise devices

Microsoft Intune now supports the **Block one lock for device and work profile** setting in the Android Enterprise settings catalog, letting you require separate locks for the device and work profile instead of a shared one. Set it to **True** after configuring a work profile password requirement. The default, **False**, allows a common lock. The setting supports Android 9 and later.

Applies to:

- Android Enterprise corporate-owned devices with a work profile (COPE)

#### Limit how long an Android work profile can stay off

Microsoft Intune now supports the **Number of days work profile is allowed to be switched off** setting in the Android Enterprise settings catalog, so you can limit how long a work profile stays turned off. Enter the maximum number of days, with a minimum of three, or enter **0** to disable the restriction. There's no documented upper limit, giving you flexibility for your organization's needs.

Applies to:

- Android Enterprise corporate-owned devices with a work profile (COPE)

#### Remove eSIMs during a device wipe with a settings catalog policy

Microsoft Intune now supports the **Remove all eSIMs during a device wipe** setting in the Android Enterprise settings catalog. Set it to **True** to request removal of all eSIMs when a corporate-owned device is wiped while the policy applies. The default, **False**, doesn't request removal, although the operating system might still remove eSIMs when required. The setting supports Android 15 and later.

Applies to:

- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)
- Android Enterprise corporate-owned devices with a work profile (COPE)

#### New updates to the Apple settings catalog

Microsoft Intune now supports new Settings Catalog options for testing on the OS 27 betas, covering Declarative Device Management areas such as **App Settings**, **Web Content Filter**, and **Siri Settings** for iOS/iPadOS and macOS. Configure them under **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **iOS/iPadOS** or **macOS** &gt; **Settings catalog**. This lets you test upcoming Apple management controls ahead of general availability.

For more information, see [Create a policy using settings catalog](../device-configuration/settings-catalog/).

Applies to:

- iOS/iPadOS
- macOS

#### Keep Android device screens on while charging

Microsoft Intune now includes a settings catalog option for keeping fully managed and dedicated Android device screens on while charging. Select one or more modes - **AC**, **USB**, or **Wireless** - to control when the screen stays on. AC and USB support Android 6.0 and later; wireless charging requires Android 8.1 and later. No modes are selected by default.

Applies to:

- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)

#### New policy settings for Windows

Microsoft Intune now includes new Windows settings catalog options across several administrative template refreshes. Highlights include **Turn on Protected Mode** controls for Internet Explorer security zones, new Microsoft Edge policies from the Edge 150 template refresh, and a **Disconnect if a Remote Desktop Services session when no smart card is present** option for interactive logon. The Microsoft Office templates also gained new settings. Create a Windows settings catalog profile to configure them.

Applies to:

- Windows

### Device enrollment

#### Skip new Apple Setup Assistant panes during enrollment

Microsoft Intune now includes Apple OS 27 Setup Assistant skip keys for Liquid Glass and Accessibility Appearance in Automated Device Enrollment profiles. You can hide these panes to reduce setup interactions and provide a more consistent enrollment experience on supported iPhone, iPad, and Mac devices.

Applies to:

- iOS/iPadOS
- macOS

### Device management

#### New single device page in the Intune admin center

The new single device page is turned on by default for all customers. You can use the **Preview new device view** toggle to turn it off and return to the original device page.

In the Intune admin center, when you go to **Devices** &gt; **All devices** and select a device, you can see device-specific information, including device properties, device activity, tools, and reports.

**Where to find common device information and actions in the new single device view:**

- Change the management name, primary user, or device category: Go to **Devices** &gt; **All devices** &gt; select a device &gt; **Properties** &gt; **Edit**.
- View hardware and operating system information: Go to **Devices** &gt; **All devices** &gt; select a device &gt; **Device details**. The **Device details** tab was previously called **Hardware**.
- Perform device actions: Go to **Devices** &gt; **All devices** and select a device. Some actions are organized in the **Remote actions**, **Secure**, and **Remove data** menus on the device command bar. The available actions depend on the device platform, management type, ownership, permissions, and supported capabilities.
- View the status of device actions: Go to **Devices** &gt; **All devices** &gt; select a device &gt; **Device action status**.
- View the status of Remediations: Go to **Devices** &gt; **All devices** &gt; select a device &gt; **Tools** &gt; **Remediations**.
- View scope tags: Go to **Devices** &gt; **All devices** &gt; select a device &gt; **Properties**.

**Return to the original device page:**

If you prefer to use the original device page, you can turn off the new experience:

1. In the Intune admin center, go to **Devices** &gt; **All devices**.
2. Move the **Preview new device view** toggle to **Off**.

Applies to:

- Android
- iOS/iPadOS
- macOS
- Windows

#### Operating system version property in assignment filters is generally available

The `operatingSystemVersion` property in assignment filters is now generally available for managed devices and managed apps. Use this property to create filter rules that scope your app and policy assignments to devices running a specific OS version or build range. For example, create an assignment filter that pilots a configuration on a newer build before rolling it out broadly or excludes devices that haven't yet updated.

You can build rules using the rule editor or the rule syntax text box, with the same operators available for other filter properties. Existing assignments continue to work without changes.

For more information, see:

- [Use assignment filters to assign apps, policies, and profiles](../fundamentals/filters/overview)
- [App and device properties, operators, and rule editing when creating assignment filters](../fundamentals/filters/ref-device-properties)

#### Collect enhanced diagnostic logs from supervised Apple devices

Microsoft Intune now supports Apple's Enhanced Logging device action on supported supervised devices running a compatible OS release. Administrators can start an AppleCare diagnostic-log collection session using an AppleCare-provided token and monitor device-reported status through Declarative Device Management, reducing the need to coordinate manual log collection with the device user.

Applies to:

- iOS/iPadOS
- macOS

#### View expanded SIM inventory for corporate-owned Android devices

Microsoft Intune now surfaces expanded SIM inventory for corporate-owned Android Enterprise devices, including EIDs, multiple ICCIDs, and activation state. View these details under **Devices** &gt; **All devices** &gt; select a device &gt; **Hardware**, and use the reported ICCID to identify the correct eSIM for a removal action. EID reporting requires Android 13 and later; full inventory requires Android 15 and later.

Applies to:

- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)
- Android Enterprise corporate-owned devices with a work profile (COPE)

#### Activate an eSIM on a corporate-owned Android device

Microsoft Intune now supports single-device eSIM activation for corporate-owned Android Enterprise devices running Android 15 and later. Turn on **Preview new device view**, select the device, then select **Activate eSIM** and enter the carrier activation code. Intune sends the request without first blocking it based on reported eSIM slot capacity and surfaces errors returned by Google. Personally owned work profile devices aren't supported.

Applies to:

- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)
- Android Enterprise corporate-owned devices with a work profile (COPE)

#### Remove an individual eSIM from a corporate-owned Android device

Microsoft Intune now lets you remove a single eSIM from a corporate-owned Android Enterprise device without wiping it. Turn on **Preview new device view**, select the device, copy the eSIM's ICCID from device inventory, then select **Remove eSIM** and enter the ICCID. The action supports fully managed and dedicated devices on Android 15 and later, and work profile devices on Android 17 and later.

Applies to:

- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)
- Android Enterprise corporate-owned devices with a work profile (COPE)

#### Choose whether to remove eSIMs when wiping one corporate-owned Android device

Microsoft Intune now lets you choose whether to preserve or remove eSIMs when wiping one corporate-owned Android Enterprise device. Turn on **Preview new device view**, select the device, then select **Wipe**. By default, the wipe preserves eSIMs; select the eSIM removal option only when you want the wipe to remove them. Personally owned work profile devices aren't supported.

Applies to:

- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)
- Android Enterprise corporate-owned devices with a work profile (COPE)

#### Device inventory for personally owned devices on Android Enterprise

Microsoft Intune now supports device inventory for personally owned Android Enterprise devices with a work profile managed by Android Management API. View these devices from the device's **Inventory** page alongside corporate-owned devices in Resource Explorer, and query them with Multi-Device Query. Inventory data is a subset of corporate-owned data; properties such as IMEI, ICCID, and MAC address aren't available. This gives you more consistent analytics across mixed corporate and BYOD environments.

Applies to:

- Android Enterprise personally owned devices with a work profile using Android Management API

### Device security

#### Audit mode for the Microsoft Defender Antivirus template for Linux

The Microsoft Defender Antivirus template for Linux, which is part of Intune's Endpoint Security Antivirus policy, now includes a new **Audit** value for the **Enforcement level** setting. When you set **Enforcement level** to **Audit**, the antivirus engine detects threats in real time but doesn't automatically remediate them. Malware detections are reported as alerts in the Microsoft Defender portal through real-time scanning, without quarantining the malicious files. Audit mode gives you visibility into the threat landscape before you turn on full protection.

The Microsoft Defender Antivirus template for Linux is supported for devices [managed by Intune](../device-configuration/endpoint-security/antivirus), and for devices managed only by Defender through the [Microsoft Defender for Endpoint security settings management](../device-security/microsoft-defender/security-settings-management) scenario (MDE attach).

Applies to:

- Linux

#### Windows 365 for Agents security baseline

Microsoft Intune now includes a security baseline for Windows 365 for Agents Cloud PCs. Administrators can deploy and customize recommended, device-scoped settings for Windows 11, Microsoft Edge, and Microsoft Defender for Endpoint to establish a consistent security posture for agentic workloads.

For more information, see [Manage security baseline profiles in Microsoft Intune](../device-security/security-baselines/configure-baselines) and [What is Windows 365 for Agents?](/en-us/windows-365/agents/introduction-windows-365-for-agents).

Applies to:

- Windows 365 for Agents Cloud PCs running Windows 11 and later

#### Memory scan setting for Microsoft Defender Antivirus on Linux

Microsoft Intune now supports a memory scan setting in the Microsoft Defender Antivirus template for Linux endpoint security antivirus policies. You can manage memory scan behavior on Linux devices managed through Microsoft Defender for Endpoint security settings management, giving you finer control over how Defender inspects memory on your Linux endpoints.

Applies to:

- Linux

## Week of July 27, 2026 (Service release 2607)

### Device configuration

#### Samsung Knox E-FOTA firmware update management for Android Enterprise devices

Microsoft Intune now integrates with Samsung Knox E-FOTA (Firmware Over-The-Air), so you can manage firmware updates for corporate-owned Samsung devices directly in the Microsoft Intune admin center. Control which firmware version each device receives, deploy updates without user interaction, and schedule downloads and installations to reduce downtime.

For more information, see [Samsung Knox E-FOTA integration with Microsoft Intune](../device-updates/android/setup-samsung-knox).

Applies to:

- Android Enterprise corporate-owned dedicated (COSU)
- Android Enterprise corporate-owned fully managed (COBO)
- Android Enterprise corporate-owned with a work profile (COPE)

#### New settings available in the Windows settings catalog

Microsoft Intune now includes new settings in the Windows settings catalog for Windows devices. You can configure options for camera behavior, Keyboard Filter controls (for Windows Insider devices), and Windows Subsystem for Linux (WSL). To find them, go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Windows 10 and later** &gt; **Settings catalog**.

Applies to:

- Windows 11
- Windows 10

#### New Microsoft Edge settings in the Windows settings catalog

The Microsoft Edge administrative templates were refreshed to Microsoft Edge 149 (version 149.0.4022.21), which adds the latest Microsoft Edge 148 and 149 policy settings to the Windows settings catalog. The new settings are:

- **[Allow Local Fonts permission on these sites](/en-us/deployedge/microsoft-edge-policies/localfontsallowedforurls)** (LocalFontsAllowedForUrls)
- **[Allow M365 authentication popups in work profiles](/en-us/deployedge/microsoft-edge-policies/m365authpopupsinworkenabled)** (M365AuthPopupsInWorkEnabled)
- **[Allow MAM enrollment when managed device has Purview DLP policy configured](/en-us/deployedge/microsoft-edge-policies/mamwithdevicedlpenabled)** (MAMWithDeviceDLP)
- **[Automatically open Copilot side pane with contextual insights for links opened from Outlook](/en-us/deployedge/microsoft-edge-policies/m365linksautoopencopilotenabled)** (M365LinksAutoOpenCopilotEnabled)
- **[Block Local Fonts permission on these sites](/en-us/deployedge/microsoft-edge-policies/localfontsblockedforurls)** (LocalFontsBlockedForUrls)
- **[Browsing with Copilot Allowed URLs](/en-us/deployedge/microsoft-edge-policies/browsingwithcopilotallowlist)** (BrowsingWithCopilotAllowList)
- **[Browsing with Copilot Blocked URLs](/en-us/deployedge/microsoft-edge-policies/browsingwithcopilotblocklist)** (BrowsingWithCopilotBlockList)
- **[Configure whether the Discover or Work feed tabs are shown on the Copilot new tab page](/en-us/deployedge/microsoft-edge-policies/configurentpfeedtabvisibility)** (ConfigureNTPFeedTabVisibility)
- **[Controls the availability of browsing with Copilot in Microsoft Edge](/en-us/deployedge/microsoft-edge-policies/allowbrowsingwithcopilot)** (AllowBrowsingWithCopilot)
- **[Default Local Fonts permission setting](/en-us/deployedge/microsoft-edge-policies/defaultlocalfontssetting)** (DefaultLocalFontsSetting)
- **[Enable Copilot address bar suggestions](/en-us/deployedge/microsoft-edge-policies/copilotaddressbarsuggestionsenabled)** (CopilotAddressBarSuggestionsEnabled)
- **[Enable opaque origins for data URLs in Web Workers](/en-us/deployedge/microsoft-edge-policies/dataurlinwebworkeropaqueoriginenabled)** (DataUrlInWebWorkerOpaqueOriginEnabled)
- **[Enable the Copilot new tab page](/en-us/deployedge/microsoft-edge-policies/copilotnewtabpageenabled)** (CopilotNewTabPageEnabled)
- **[Enable the extended lifetime option for SharedWorkers](/en-us/deployedge/microsoft-edge-policies/sharedworkerextendedlifetimeenabled)** (SharedWorkerExtendedLifetimeEnabled)
- **[Force foreground priority for specific URLs](/en-us/deployedge/microsoft-edge-policies/forceforegroundpriorityforurls)** (ForceForegroundPriorityForUrls)
- **[List of URL patterns for which developer tools are allowed to be opened](/en-us/deployedge/microsoft-edge-policies/developertoolsavailabilityallowlist)** (DeveloperToolsAvailabilityAllowlist)
- **[List of URL patterns for which developer tools are blocked](/en-us/deployedge/microsoft-edge-policies/developertoolsavailabilityblocklist)** (DeveloperToolsAvailabilityBlocklist)
- **[Maximum number of concurrent connections to the proxy server for WebSocket requests](/en-us/deployedge/microsoft-edge-policies/maxconnectionsperproxyforwebsocket)** (MaxConnectionsPerProxyForWebSocket)
- **[Override for the CPU performance tier](/en-us/deployedge/microsoft-edge-policies/cpuperformancetieroverride)** (CpuPerformanceTierOverride)
- **[Set the default Copilot new tab page feed tab to Work or Discover](/en-us/deployedge/microsoft-edge-policies/setntpdefaultfeedtab)** (SetNTPDefaultFeedTab)

For the full list of policies, see the [Microsoft Edge policies reference](/en-us/deployedge/microsoft-edge-policies).

Applies to:

- Windows

#### New Windows App (Azure Virtual Desktop) settings in the Windows settings catalog

There are new Windows App settings in the Windows settings catalog. To see and configure them in Intune, create a Windows settings catalog profile (**Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Windows 10 and later** &gt; **Settings catalog**). The new settings are:

- **Turn off automatic updates for Windows App** – controls whether Windows App automatically checks for and installs updates.
- **Automatically log off users after inactive interval** – signs users out of Windows App after a set period of inactivity.
- **Skip First Run Experience (FRE)** – skips the first-run experience so users go straight to their resources.
- **Admin Release Ring Policy** – sets the update release ring (channel) that Windows App follows.
- **Automatically create Windows App shortcuts to desktop** – creates desktop shortcuts for published Windows App resources. For more information, see [Configure updates for Windows App](/en-us/windows-app/configure-updates-windows).

Applies to:

- Windows

#### New option for the Remove Default Microsoft Store packages setting

The existing **Remove Default Microsoft Store packages** setting in the ApplicationManagement area has a new subsetting, **Specify additional package family names to remove**. It lets you provide a custom list of package family names (PFNs) to remove, in addition to the built-in default set of Microsoft Store packages. For more information, see the [ApplicationManagement policy CSP](/en-us/windows/client-management/mdm/policy-csp-applicationmanagement).

Applies to:

- Windows

#### New setting to disable the Get Started app

The new **Disable Get Started** setting prevents the Windows Get Started app from being available to users. For more information, see the [Experience policy CSP](/en-us/windows/client-management/mdm/policy-csp-experience).

Applies to:

- Windows

#### New OneDrive settings in the Windows settings catalog

There are new OneDrive settings in the Windows settings catalog:

- **Set a custom name for the OneDrive folder** – sets a custom name for the synced OneDrive folder on the user's device.
- **Enable OpenID Connect (OIDC) authentication for syncing content from an on-prem SharePoint Server using the OneDrive sync app** – lets the OneDrive sync app authenticate to an on-premises SharePoint Server using OpenID Connect when the server supports it.
- **Specify the Application ID URI for your Entra application for OIDC** – specifies the Application ID URI for your Microsoft Entra application used for OIDC when it differs from your SharePoint Server URL.
- **Prevent users at your organization from enabling offline mode in OneDrive on the web** – blocks users from turning on offline mode for OneDrive on the web.
- **Prevent users at your organization from enabling offline mode in OneDrive on the web for libraries and folders that are shared from other organizations** – blocks offline mode for libraries and folders shared from other organizations.
- **Hard-delete the contents of a folder shortcut when unmounted** – permanently deletes the contents of a folder shortcut when it is unmounted instead of moving them to the Recycle Bin.
- **Hard-delete contents of a folder shortcut when a user loses permissions to the folder** – permanently deletes the contents of a folder shortcut when the user loses permissions to that folder. For more information, see [Use Group Policy to control OneDrive sync app settings](/en-us/sharepoint/use-group-policy).

Applies to:

- Windows

#### Updated Visual Studio administrative templates in the Windows settings catalog

The Visual Studio administrative templates were refreshed to version 1.0.184.40051, which adds the latest Visual Studio policy settings to the Windows settings catalog. The new setting is:

- **[Disable Model Context Protocol (MCP)](/en-us/visualstudio/ide/visual-studio-github-copilot-admin#configure-copilot-group-policy)** (DisableMCP) For more information, see the [Visual Studio administrative templates documentation](/en-us/visualstudio/install/administrative-templates).

Applies to:

- Windows

### Device enrollment

#### Skip Setup Assistant screens for tvOS and visionOS enrollment

Microsoft Intune now supports hiding or showing new Setup Assistant screens during automated device enrollment (ADE) for tvOS and visionOS devices. When you configure an enrollment profile, you can choose which screens, such as **Apple ID**, **Diagnostics Data**, and **Location Services**, appear during setup. By default, these screens are shown.

For more information, see [Set up ADE for tvOS](../device-enrollment/apple/setup-automated-tv-os) and [Set up ADE for visionOS](../device-enrollment/apple/setup-automated-vision-os).

Applies to:

- tvOS
- visionOS

#### Dedicated RBAC permission for zero-touch enrollment

Microsoft Intune now provides a dedicated role-based access control (RBAC) permission for Google zero-touch enrollment portal access. Previously, the zero-touch enrollment iframe in the Microsoft Intune admin center required the **Update app sync** permission, which also grants rights to manage Managed Google Play app sync. With the dedicated permission, you can grant zero-touch enrollment portal access independently from app management permissions.

For more information, see [Enroll by using Google Zero Touch](../device-enrollment/android/ref-corporate-methods#enroll-by-using-google-zero-touch).

Applies to:

- Android Enterprise

### Device management

#### Collect Windows registry data with the properties catalog

Microsoft Intune now lets you collect Windows registry data through the properties catalog. When you create a device inventory policy, you can define specific registry keys and values to collect from enrolled Windows devices, including a single value, all values directly under a key, or the same value across subkeys under **HKEY\_LOCAL\_MACHINE**. This gives you richer device state visibility and advanced querying without custom scripts.

For more information, see [Use the Intune properties catalog to get device hardware properties](../device-configuration/collect-device-properties).

Applies to:

- Windows

#### Improved on-demand device sync for Windows devices

Microsoft Intune now supports a more comprehensive on-demand sync for Windows devices. When you select the **Sync** device action in the Microsoft Intune admin center, Intune initiates a full synchronization across key workloads, including configuration policies, apps, and scripts, so devices reflect your latest changes faster. This capability is especially useful during troubleshooting, incident response, and high-priority rollouts.

For more information, see [Device action: sync](../device-management/actions/sync).

Applies to:

- Windows

### Device security

#### Custom compliance settings for macOS

Microsoft Intune now supports custom compliance settings for macOS. As an admin, you can define compliance checks using scripts and JSON rules, similar to existing support for Windows and Linux. This capability lets you evaluate device configuration, security posture, and other custom attributes not covered by built-in settings. Results appear alongside standard compliance reporting in the Intune admin center.

For more information, see [Custom compliance settings in Microsoft Intune](../device-security/compliance/custom-settings).

Applies to:

- macOS

#### Controlled Configuration for Microsoft Defender antivirus settings (preview)

In preview, Microsoft Intune now supports Controlled Configuration for Microsoft Defender antivirus settings. When you enable it, the Defender antivirus settings delivered by Intune or Microsoft Defender for Endpoint security settings management become authoritative and override configurations from other channels, such as Group Policy, Configuration Manager, and local scripts. Extending Tamper Protection, this capability locks settings to your defined values for consistent and predictable device states.

For more information, see [Controlled configuration for Microsoft Defender settings](../device-configuration/endpoint-security/antivirus#controlled-configuration-for-microsoft-defender-settings-preview).

Applies to:

- Windows

### Intune apps

#### Regional support for Microsoft Store apps

Microsoft Intune now supports regional selection for Microsoft Store apps. When you add a Microsoft Store app, you can choose the region (market) whose Store catalog to search and deploy from. Previously, Intune searched only the United States catalog. Now you can deploy apps published for specific markets, such as Japan or Spain, that aren't available in the US catalog.

For more information, see [Add Microsoft Store apps to Microsoft Intune](../app-management/deployment/add-microsoft-store).

Applies to:

- Windows

## Week of July 13, 2026

### App management

#### APP Multiple Managed Accounts

Microsoft Intune mobile application management now extends support for Multiple Managed Accounts to Microsoft Outlook on iOS/iPadOS (v5.2626.0 or later), letting users add and manage more than one managed account within the same app.

Note

This feature is gradually rolling out and may not yet be available in your tenant.

To learn more, see [Multiple managed accounts for app protection policies](../app-management/protection/multiple-managed-accounts).

Applies to:

- iOS/iPadOS

## Week of June 29, 2026 (Service release 2606)

### App management

#### Available macOS PKG apps update automatically when you upload a new version

For available macOS PKG apps, updates now deploy to devices automatically when the same app policy was updated with a new app version, so users no longer need to select **Install** or **Reinstall** in Company Portal to get the latest version. When you edit an existing available app policy with a newer version of the app that uses the same bundle ID, Intune deploys the update to the device automatically.

Automatic updates apply when both of the following are true:

- You upload an updated version of the app to Intune.
- The user already installed the app on the device.

This behavior requires the Microsoft Intune management agent for macOS version `2606.013` or later.

For more information, see [Add an unmanaged macOS PKG app to Microsoft Intune](../app-management/deployment/add-unmanaged-pkg-macos).

Applies to:

- macOS

#### Newly available protected app for Intune

ChatGPT is now available as a protected app for Microsoft Intune.

For more information about protected apps, see [Microsoft Intune protected apps](../app-management/ref-protected-apps).

#### Enterprise App Management support for GCC High and DoD

Microsoft Intune now extends Enterprise App Management (EAM) to the GCC High (GCCH) and DoD cloud environments. Government organizations can use the EAM enterprise catalog to discover, deploy, and keep prepackaged Microsoft and third-party apps up to date without manual repackaging. A secure cross-cloud integration model maintains the compliance boundaries and authentication requirements expected for government tenants.

For more information, see [Microsoft Intune Enterprise Application Management](../app-management/deployment/enterprise-app-management).

Applies to:

- Windows

#### Auto-update for Enterprise App Management applications

Microsoft Intune now supports automatic updates for Enterprise App Management (EAM) applications. When you enable auto-update for an EAM app with a required assignment, Intune detects when a newer version is available in the EAM catalog and automatically updates the app on targeted devices. This eliminates manual packaging and supersedence workflows, reduces update maintenance at scale, and helps keep devices secure with timely updates.

For more information, see [Microsoft Intune Enterprise Application Management](../app-management/deployment/enterprise-app-management).

Applies to:

- Windows

### Device configuration

#### New Android Enterprise settings in the Intune settings catalog

The settings catalog lists all the settings you can configure in a device policy, and all in one place. The following new Android Enterprise settings are available in the Microsoft Intune settings catalog (**Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Android Enterprise** for platform &gt; **Settings catalog** for profile type).

##### Applications

| Setting | Description | Applies to |
| --- | --- | --- |
| **Block apps from exposing app functions** | This setting controls whether managed apps can expose app functions — programmatic actions that other apps and on-device assistants or AI agents can invoke inside the app. If **True**, apps on fully managed devices and apps in the work profile on corporate-owned devices are blocked from exposing app functions. If **False** (default OS behavior), apps are allowed to expose app functions. | COBO, COSU, COPE |
| **Block widgets from work profile apps** | If **True**, allows users to access widgets exposed by apps in the work profile on the device's home screen. If **False**, prevents access to these widgets. By default, the OS might allow widget access. | COPE |

##### Connectivity

| Setting | Description | Applies to |
| --- | --- | --- |
| **Allow selection of a preferential network service** | If **True**, the device gives priority to the specified network service over other available options, such as an enterprise slice on 5G networks. If **False**, the device connects using its default network selection process. | COBO, COSU, COPE |
| **Block airplane mode** | If **True**, the device is prevented from enabling airplane mode. If **False**, the device follows the default airplane mode behavior of the OS. | COBO, COSU, COPE |
| **Block cellular 2G** | If **True**, the device prevents cellular 2G functionality, restricting user access to the setting. If **False** (default), the device follows the default cellular 2G behavior of the OS. Supported on Android 14 and later. | COBO, COSU, COPE |
| **Block configuring cell broadcasts** | If **True**, the device is prevented from receiving cell broadcast messages, such as emergency alerts. If **False** (default), Intune doesn't change or update this setting, and the OS might allow the reception of cell broadcast messages. | COBO, COSU, COPE |
| **Block configuring mobile networks** | **True** prevents users from configuring or modifying mobile network settings on the device. If **False** (default), Intune doesn't change or update this setting and the OS might allow users to adjust mobile network settings. | COBO, COSU, COPE |
| **Block configuring VPN** | If **True**, users can't add, edit, or remove VPN configurations on the device. If **False** or not configured, the device follows the default VPN configuration behavior of the OS. | COBO, COSU, COPE |
| **Block network reset** | If **True**, the device won't reset network settings even if a reset is attempted. If **False** (default), the device follows the default network reset behavior of the OS. | COBO, COSU, COPE |
| **Block outgoing calls** | If **True**, users are prevented from making outgoing calls on the device. If **False** (default), Intune doesn't change or update this setting, and the OS might allow outgoing calls. | COBO, COSU, COPE |
| **Block SMS** | If **True**, the device is prevented from sending or receiving SMS messages, restricting text communication. If **False** (default), the device follows the default SMS behavior of the OS. | COBO, COSU, COPE |
| **Block ultra wideband** | If **True**, the device prevents ultra wideband functionality, restricting user access to the setting. If **False** (default), the device follows the default ultra wideband behavior of the OS. Supported on Android 14 and later. | COBO, COSU, COPE |
| **Select minimum Wi-Fi security level** | Select the minimum Wi-Fi security level required for the device to connect to Wi-Fi networks. Options are **Open network security**, **Personal network security**, **Enterprise network security**, and **Enterprise 192-bit network security**. The default is **Open network security**, which allows the device to connect to all types of Wi-Fi networks. Supported on Android 13 and later. | COBO, COSU, COPE |

##### General

| Setting | Description | Applies to |
| --- | --- | --- |
| **Block printing** | If **True**, the device is prevented from printing documents. If **False** (default), the device follows the default printing behavior of the OS. | COBO, COSU, COPE |
| **Block setting user icon** | If **True**, users are prevented from changing their user icon or profile image on the device. If **False** (default), Intune doesn't change or update this setting, and the OS might allow users to modify their user icon. | COBO, COSU, COPE |
| **Block setting wallpaper** | If **True**, users are prevented from changing the wallpaper on the device. If **False** (default), Intune doesn't change or update this setting, and the OS might allow users to change the wallpaper. | COBO, COSU, COPE |
| **Block users from adding eSIM profiles** | If **True**, users can't add eSIM profiles to the device. If **False** (default), users can add eSIM profiles based on the default behavior of the OS. | COBO, COSU, COPE |

**Platform key:**

- **COBO** — Android Enterprise corporate-owned fully managed
- **COSU** — Android Enterprise corporate-owned dedicated devices
- **COPE** — Android Enterprise corporate-owned devices with a work profile (at work profile level)

For a list of all settings you can currently configure, see [Android Enterprise device settings list in the Intune settings catalog](../device-configuration/settings-catalog/ref-android-settings).

Applies to:

- Android Enterprise

#### Support for WPA3-Personal in iOS/iPadOS Wi-Fi profiles

Intune supports **WPA3-Personal** as a security-type option when configuring Wi-Fi device configuration profiles for iOS/iPadOS. Admins can now select WPA3-Personal alongside existing options such as WPA2-Personal.

This feature:

- Allows managed iOS/iPadOS devices to connect to networks that require the stronger WPA3 protocol.
- Brings iOS/iPadOS in line with the latest Wi-Fi Alliance security standards and helps organizations meet evolving network-security requirements.

Support for WPA3 on Windows, Android, and macOS platforms and for WPA3-Enterprise will be available in a future release (no ETA).

To learn more about the settings you can currently configure, see [Add Wi-Fi settings to Apple devices in Microsoft Intune](../device-configuration/templates/ref-wifi-settings-apple).

Applies to:

- iOS/iPadOS

#### New supported OEMConfig apps for Android Enterprise

The following OEMConfig apps are available in Intune for Android Enterprise:

- FCNT | com.fcnt.arrowsconfig
- FCNT | com.fcnt.arrowsconfig\_test

For more information about OEMConfig, see [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](../device-configuration/templates/configure-oemconfig-android).

Applies to:

- Android Enterprise

### Device management

#### Advanced Intune capabilities are being added to Microsoft 365 E3 and E5

Microsoft is adding several Intune Suite capabilities to Microsoft 365 E3 and Microsoft 365 E5 to enable more organizations to use advanced endpoint management and security without a separate add-on.

The following capabilities are added to Microsoft Enterprise Mobility + Security E3 (EMS E3), which is included with Microsoft 365 E3:

- Remote Help
- Advanced Analytics
- Intune Plan 2, which includes Microsoft Tunnel for mobile application management (MAM), specialty device management, and firmware over-the-air (FOTA) updates for supported devices

Microsoft 365 E5 includes all Microsoft 365 E3 capabilities, plus:

- Endpoint Privilege Management
- Enterprise Application Management
- Microsoft Cloud PKI

These capabilities are gradually rolling out. Eligible tenants are automatically provisioned, and no action is required. Before the change takes effect in your tenant, Microsoft posts a notification in the Microsoft 365 admin center 30 days in advance.

This update applies to commercial Microsoft 365 E3 and E5. There are no changes to the Education (EDU) or frontline worker (FLW) plans at this time. For Government plans, Intune Suite packaging is planned to align with the equivalent enterprise plans, subject to compliance and regulatory requirements. For the capabilities currently supported in GCC High and DoD, see [Supported Intune features in GCC High and DoD](../fundamentals/government-service#supported-intune-features-in-gcc-high-and-dod).

For more information, see [Microsoft Intune advanced capabilities](../fundamentals/advanced-capabilities) and the blog post [Microsoft 365 adds advanced Microsoft Intune solutions at scale](https://techcommunity.microsoft.com/blog/microsoftintuneblog/microsoft-365-adds-advanced-microsoft-intune-solutions-at-scale/4474272).

#### Intune support for Trustd Mobile as a mobile threat defense partner

You can now use Trustd Mobile as a mobile threat defense partner (MTD) for enrolled devices that run the following platforms:

- Android 9.0 and later
- iOS/iPadOS 15.0 and later

To learn more about this support, see [Use Trustd Mobile with Microsoft Intune](../device-security/mobile-threat-defense/trustd-mobile).

#### Remote Help support for RemoteApp in Azure Virtual Desktop

Remote Help supports RemoteApp in Azure Virtual Desktop (AVD), enabling help desk agents to securely view and control apps running within RemoteApp sessions. For more information, see [Launch Remote Help](../remote-help/start-session?tabs=windows,windowsnative#provide-help-in-azure-virtual-desktop-desktop-and-remoteapp-sessions).

### Device security

#### Microsoft Tunnel adds support for Red Hat Enterprise Linux 9.7

Microsoft Tunnel Gateway now supports Red Hat Enterprise Linux (RHEL) 9.7 as a Linux server distribution.

- This support requires the use of Podman 5.8.2 as its default container engine. Customers upgrading from environments using Podman v3 containers should recreate containers and reinstall Microsoft Tunnel, as those containers aren't compatible with newer Podman versions.
- Like other RHEL 9.x versions, RHEL 9.7 doesn't automatically load the *ip\_tables* module into the Linux kernel. When you use this version, plan to manually load *ip\_tables* before you install Tunnel.

For the full list of supported distributions and their container requirements, see [Prerequisites for the Microsoft Tunnel in Intune](../device-security/microsoft-tunnel/prerequisites#linux-server).

#### Updated security baseline for Microsoft 365 Apps for Enterprise

An updated security baseline for **Microsoft 365 Apps for Enterprise** is now available in Microsoft Intune. This baseline aligns with the most recent Microsoft 365 Apps security guidance and includes updated policy recommendations to help protect against evolving threats.

This release is version **v2512**, which skips the previously published version found in the Security Compliance Toolkit (v2412). Review the new baseline carefully before you adopt it.

The following three settings aren't available in this baseline release and are expected to be added in a future update. The parent setting to these three, (**VBA Macro Notification Settings** set to *Disable all except digitally signed macros*) is still included in the v2512 release:

- **Require macros to be signed by a trusted publisher**: Pending availability in the Settings Catalog.
- **Block certificates originating from the current user store only**: Pending availability in the Settings Catalog.
- **Require Extended Key Usage (EKU) for code signing**: Pending availability in the Settings Catalog.

Existing profiles don't automatically upgrade. To use the latest version, [create a new baseline profile](../device-security/security-baselines/configure-baselines#create-a-profile-for-a-security-baseline) or [update an existing profile to the latest version](../device-security/security-baselines/configure-baselines#update-a-baseline-profile-to-the-latest-version).

To view the full list of settings and their default values, see [Microsoft 365 Apps for Enterprise security baseline version 2512](../device-security/security-baselines/ref-v2-office-settings?pivots=v2512). For a detailed breakdown of setting changes, see the blog post [Security baseline for M365 Apps for enterprise v2512](https://techcommunity.microsoft.com/blog/Microsoft-Security-Baselines/security-baseline-for-m365-apps-for-enterprise-v2512/4487213).

Applies to:

- Windows

#### New Microsoft Defender Antivirus settings for Linux Server devices

The existing endpoint security [Antivirus](../device-configuration/endpoint-security/antivirus) policy for the **Microsoft Defender Antivirus** profile on Linux Server now includes new settings you can configure and deploy to your managed Linux devices:

- **Offline security intelligence update** - Manage how Microsoft Defender Antivirus keeps its security intelligence current on Linux Server devices, including updates while the device is offline.
- **Scheduled scan** - Manage when Microsoft Defender Antivirus runs scheduled scans on Linux devices.

These settings:

- Are added to the existing endpoint security **Antivirus** policy for the **Microsoft Defender Antivirus** profile on Linux. No new profile is required. By default, they're set to *Not configured*.
- Are supported for Linux Server devices enrolled with Intune, and for Linux devices managed through the [Microsoft Defender for Endpoint security settings management](../device-security/microsoft-defender/security-settings-management) scenario, which supports devices that are managed by Defender for Endpoint but not enrolled with Intune.

For details about the available Defender settings, see [Set preferences for Microsoft Defender for Endpoint on Linux](/en-us/defender-endpoint/linux-preferences) in the Microsoft Defender for Endpoint documentation.

Applies to:

- Linux

#### New setting added to the Windows security baseline version 25H2

The Intune security baseline for Windows, version 25H2, is updated to include one new setting, **Disable Internet Explorer 11 Launch Via COM Automation**, with a baseline default of **Enabled**.

This setting was excluded from the version 25H2 baseline at its initial release due to a known issue, which is now resolved. When enabled, the setting prevents Internet Explorer 11 from being launched through COM automation, which reduces the attack surface on managed devices.

This change is an update to an existing baseline version, not a new baseline version. The new setting isn't visible in a baseline profile's properties until you edit and save the profile:

- **Pre-existing baseline profiles**: To add the new setting to a profile you created before this update, select and then **Edit** the profile, and then **Save** it. When you open the profile for editing, the new setting appears with its baseline default configuration. You can reconfigure the setting before you save, or save with no changes to apply the baseline default. After you save, Intune deploys the setting to the assigned groups at the next device check-in. If you don't edit and save the profile, the setting doesn't take effect.
- **New baseline profiles**: When you create a profile that uses the Windows security baseline version 25H2, or update an existing profile to version 25H2, that profile includes the new setting along with all the previously available settings.

To view the setting and its baseline default, see [Windows MDM baseline settings](../device-security/security-baselines/ref-windows-mdm-settings?pivots=mdm-25h2).

Applies to:

- Windows 11

## Week of June 22, 2026

### App management

#### Microsoft Intune app for Android requires version 2025.11.01 or later

The minimum supported version of the Microsoft Intune app for Android is now version `2025.11.01`. This change took effect on May 1, 2026. Users running an older version might experience sign-in failures.

Most users have app updates set to automatic and receive the updated app without taking any action. Users not running a supported version should update the Microsoft Intune app to the latest version to resolve any sign-in issues.

To check which devices are affected, go to **Apps** &gt; **Monitor** &gt; **Discovered apps** and find the Microsoft Intune app to identify devices running older versions.

Applies to:

- Android

## Tenant administration

#### Multi Admin Approval now enforces on API calls made by automation

Multi Admin Approval (MAA) now applies to API calls made by automation through the Microsoft Graph API, not just interactive admin actions. If your tenant has MAA access policies configured and you use service principals, automation scripts, or third-party applications to modify protected Intune resources, those calls are now subject to the same approval workflow as interactive operations.

Calls that don't include the required approval headers return an HTTP 403 error. To maintain your automation, update your scripts to follow the MAA approval workflow. If an immediate code change isn't feasible for applications that use app-auth tokens, you can exclude specific applications from enforcement using the new Exclusions tab in the access policy wizard.

For more information, see [Use Multi Admin Approval with the Microsoft Graph API](../fundamentals/role-based-access-control/multi-admin-approval-graph-api).

## Week of June 15, 2026

### App management

#### Managed Win32 app content now requires HTTPS delivery

Intune now requires HTTPS delivery for managed Win32 app content. This change primarily affects organizations that use Microsoft Connected Cache and haven't configured their cache nodes for HTTPS delivery. Clients that previously pulled content from Connected Cache can still download Intune Win32 apps, but those requests bypass the cache nodes and fall back to the content delivery network (CDN). This behavior can increase internet traffic and bandwidth usage.

For more information, see the blog post [How to enable HTTPS support for Microsoft Connected Cache for Enterprise and Education](https://techcommunity.microsoft.com/blog/intunecustomersuccess/how-to-enable-https-support-for-microsoft-connected-cache-for-enterprise-and-edu/4496173).

For setup and validation guidance, see:

- [HTTPS support for Microsoft Connected Cache overview](/en-us/windows/deployment/do/mcc-ent-https-overview)
- [HTTPS setup on Windows](/en-us/windows/deployment/do/mcc-ent-https-windows-guide)
- [HTTPS setup on Linux](/en-us/windows/deployment/do/mcc-ent-https-linux-guide)

### Device enrollment

#### Enrollment time grouping for new Apple ADE enrollment policies generally available

Enrollment time grouping is now generally available for Apple automated device enrollment (ADE) on iOS/iPadOS and macOS. With enrollment time grouping, you can identify a device's Microsoft Entra security group during enrollment, so policies, apps, and settings can be applied earlier in the setup process.

Enrollment time grouping is supported in new Apple ADE enrollment policies. For requirements and setup details, see [Set up enrollment time grouping](../device-enrollment/setup-time-grouping). With the enrollment time grouping availability to iOS/iPadOS and macOS, we're also making the new Apple enrollment policies experience avaialble. Please check our previous blog post to learn more. (https://techcommunity.microsoft.com/blog/intunecustomersuccess/new-iosipados-visionos-tvos-and-macos-ade-enrollment-policies-experience/4393531)

### Device management

#### Android Enterprise personally owned devices with a work profile uses Android Management API (AMAPI)

When users enroll their personally owned Android devices in Intune, a work profile is created with a separate partition on the device for the user's work account. These devices are referred to as *personally owned devices with a work profile*.

As part of the Intune move to the [Android Management API](https://developers.google.com/android/management) (opens Android's web site), there are some updates for personally owned devices that enroll in Intune:

- Web based enrollment for an improved enrollment flow and experience - Users don't have to install an app to enroll in Intune. Web enrollment is tenant wide.
- New implementation for how Intune delivers policies - Modern update on how Intune delivers and monitors policies on Android personally owned devices with a work profile. This change also aligns with how Intune manages policies on corporate owned devices with a work profile, fully managed, and dedicated devices. You can scale your migration to targeted groups.

To use these features, opt in through the Microsoft Intune admin center:

- Web based enrollment: **Devices** &gt; **Device Onboarding** &gt; **Enrollment** &gt; **Android**&gt; **Personally owned devices with a work profile** &gt; **Use web enrollment for all users enrolling into Android personally-owned work profile management**
- Policy: **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Android Enterprise** &gt; **Move to Android Management API**

To learn more, see:

- [New policy implementation and web enrollment for Android personally owned work profile blog](https://techcommunity.microsoft.com/blog/intunecustomersuccess/new-policy-implementation-and-web-enrollment-for-android-personally-owned-work-p/4370417)
- [Use Android Management API for personally owned devices with work profiles](../device-enrollment/android/android-management-api-overview)

Applies to:

- Android Enterprise personally owned devices with a work profile

#### Improvements to the new Intune single device page (preview)

In the Intune admin center, the **Devices** &gt; **All Devices** &gt; select a device page is redesigned and available for you to preview. This feature was available in the 2604 service release.

After the initial 2604 release, we made the following improvements:

- After you select one of the following device actions, you can temporarily view passcodes and PINs in the **Device action status** table:

    - Reset passcode
    - Recover passcode
    - Remote Lock
    - Rotate BitLocker Keys
- Updates to Device actions:

    - Device actions work as expected when [multi admin approval](../fundamentals/role-based-access-control/multi-admin-approval) policies are enabled.
    - Device actions for supervised iOS devices are available when the action is supported.
    - Admins can enable and disable **Lost mode**.
- Updates to navigation:

    - Tools and reports have been moved to the left navigation menu.
    - The monitor tab is now the default landing tab.
- In the **Essentials** section:

    - The **Copy** button and the **User** and **Compliance** links are available.
    - Supervised iOS devices show a badge to help identify these devices.
- When preview is disabled, the feedback pane shows the correct text.
- Comanagement information is available.
- Admins can remove the primary user from an Azure domain joined device.

### Device security

#### Microsoft Windows 11 STIG SCAP Benchmark audit baseline

Intune now includes a STIG audit baseline that assesses Windows devices against the recommended configurations defined in the Security Technical Implementation Guides (STIGs) published by the Defense Information Systems Agency (DISA). The initial baseline audits against the **Microsoft Windows 11 STIG SCAP Benchmark***Version 2, Release 7 (benchmark date: January 5, 2026)*.

Unlike other Intune security baselines that configure and enforce settings, the STIG audit baseline is audit-only. It evaluates the current state of a device's configuration and generates detailed audit reports without changing any configured settings, helping organizations demonstrate compliance with DoD security recommendations. Audit results have a documented mapping to NIST XCCDF result categories for formal DISA compliance reporting, and Graph API support enables programmatic data retrieval and cross-tenant assessment aggregation.

The STIG audit baseline is available for [US Government Community Cloud High (GCC High)](../fundamentals/government-service) tenants and requires [Advanced Analytics](../advanced-analytics/) licensing.

For more information, see [Use STIG audit baselines to assess Windows device compliance](../device-security/security-baselines/stig-audit-baseline).

Applies to:

- Windows 10
- Windows 11

## Week of June 8, 2026 (Service release 2605)

### App management

#### Newly available protected apps for Intune

The following protected apps are now available for Microsoft Intune:

- Caju AI by Caju AI
- eYACHO for Biz 7 Intune by MetaMoJi Corporation (iOS)
- eYACHO Viewer 7 Intune by MetaMoJi Corporation (iOS)
- Harvey AI by Harvey AI (Android)
- Notta for Intune by Notta
- SwiftConnect Mobile by SwiftConnect

For more information about protected apps, see [Microsoft Intune protected apps](../app-management/ref-protected-apps).

#### APP Multiple Managed Accounts

Microsoft Intune mobile application management now supports Multiple Managed Accounts, letting users add and manage more than one managed account within the same app. App protection policies apply separately to each account, so you can tailor protection based on the account's organization or tenant. This capability helps consultants, acquisition teams, or users with multiple mailboxes stay productive without switching devices.

Currently we support Multiple Managed Accounts in Microsoft Teams on iOS/iPadOS (v8.10.0 or later). Support for additional apps and platforms is coming soon.

Note

This feature is gradually rolling out and may not yet be available in your tenant.

To learn more, see [Multiple managed accounts for app protection policies](../app-management/protection/multiple-managed-accounts).

Applies to:

- iOS/iPadOS

### Device configuration

### Custom top bar elements on Managed Home Screen

You have the option to display custom text in the top bar of the Managed Home Screen (MHS). In addition to the existing choices (serial number, device name, tenant name), you can now select **Custom** and enter a free-text string of up to 63 characters. Custom strings support dynamic variables: `{{SerialNumber}}`, `{{DeviceName}}`, and `{{TenantName}}`. This is useful for kiosk scenarios such as checkout devices, departmental tagging, or any case where staff need a quick visual identifier.

Applies to:

- Android Enterprise dedicated devices (COSU)
- Android Enterprise fully managed devices (COBO)

#### Managed Home Screen exit lock task mode password now requires a device configuration profile

You can no longer configure the Managed Home Screen exit lock task mode password by using an app configuration policy. To set or update the lock task mode password for Managed Home Screen, create or update a device configuration profile that defines the lock task mode password policy.

For more information, see [Configure the Microsoft Managed Home Screen app for Android Enterprise](../app-management/configuration/configure-managed-home-screen).

Applies to:

- Android Enterprise corporate-owned Fully Managed (COBO)
- Android Enterprise corporate-owned Dedicated (COSU)

#### New Block Bluetooth sharing setting in the Android Enterprise settings catalog

There's a new **Block Bluetooth sharing** setting in the [settings catalog](../device-configuration/settings-catalog/) (**Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Android Enterprise** for platform &gt; **Settings catalog** for profile type &gt; **General**). When set to **True**, the device can't share content over Bluetooth. When set to **False**, Intune doesn't change or update this setting. By default, the OS has the following behavior:

- Fully managed and dedicated devices allow Bluetooth sharing.
- Corporate-owned devices with a work profile block Bluetooth sharing.

For a list of existing settings you can configure in the settings catalog, see [Android Enterprise device settings list in the Intune settings catalog](../device-configuration/settings-catalog/ref-android-settings).

Applies to:

- Android Enterprise corporate-owned devices with a work profile (COPE)
- Android Enterprise corporate-owned fully managed (COBO)
- Android Enterprise corporate-owned dedicated devices (COSU)

#### Use DDM to manage Apple Intelligence settings on devices running 26.4 and later

With the release of 26.4, Apple deprecated several intelligence-related settings in the MDM restrictions payload. To manage these settings, use the DDM configurations released in March 2026 instead.

In the [settings catalog](../device-configuration/settings-catalog/), the following **Restrictions** are now deprecated:

- Allow Apple Intelligence Report
- Allow Assistant
- Allow Assistant User Generated Content
- Allow Assistant While Locked
- Allow Auto Correction
- Allow Continuous Path Keyboard
- Allow Definition Lookup
- Allow Dictation
- Allowed External Intelligence Workspace IDs
- Allow External Intelligence Integrations
- Allow External Intelligence Integrations Sign In
- Allow Genmoji
- Allow Image Playground
- Allow Image Wand
- Allow Keyboard Shortcuts
- Allow Mail Smart Replies
- Allow Mail Summary
- Allow Notes Transcription
- Allow Notes Transcription Summary
- Allow Personalized Handwriting Results
- Allow Predictive Keyboard
- Allow Safari Summary
- Allow Spell Check
- Allow Visual Intelligence Summary
- Allow Writing Tools
- Force Assistant Profanity Filter
- Force On Device Only Dictation
- Force On Device Only Translation

In the [device restrictions template](../device-configuration/templates/ref-device-restrictions-apple), the following settings are deprecated.

**Built-in apps**:

- Block Siri
- Block Siri while device is locked
- Block Siri for dictation
- Block Siri for translation
- Require Siri profanity filters
- Block user-generated content in Siri

**Keyboard and dictionary**:

- Block word definition lookup
- Block predictive keyboards
- Block auto-correction
- Block spell check
- Block keyboard shortcuts
- Block dictation

Applies to:

- iOS/iPadOS
- macOS

#### Silence apps on Managed Home Screen to prevent session PIN bypass

For devices using Managed Home Screen (MHS), you can now silence apps whenever MHS prompts the user for authentication, such as during sign-in or at the session PIN screen. When silenced, apps can't start activities, display notifications, appear in recent apps, or trigger toasts, dialogs, or device ringing. You can configure an allowlist of apps that remain unsilenced during the locked state, ensuring that critical communications like calls aren't interrupted. This feature is opt-in and configurable, allowing your organization to tailor the experience to its operational needs. Once the device is unlocked, all apps automatically return to their normal state.

For more information, see [Configure the Microsoft Managed Home Screen app for Android Enterprise](../app-management/configuration/configure-managed-home-screen).

Applies to:

- Android Enterprise

#### New Microsoft Edge settings in the Windows settings catalog

There are new Microsoft Edge 148 settings in the Windows settings catalog. To see and configure these settings in Intune, create a Windows settings catalog profile (**Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **Windows 10 and later** for platform &gt; **Settings catalog** for profile type).

The new policies include:

- **Microsoft Edge &gt; Startup, home page and new tab page &gt; Configure whether the Discover or Work feed tabs are shown on the New Tab Page**

    This policy configures whether the Discover or Work feed tabs are shown on the New Tab Page. By default, both Work and Discover tabs are enabled. Your options:

    - `EnableBothWorkDiscover`: If you set this value or don't configure this policy, Microsoft Edge shows both the Work and Discover feed tabs on the new tab page.
    - `EnableOnlyWork`: Microsoft Edge shows only the Work feed tab on the new tab page.
    - `EnableOnlyDiscover`: Microsoft Edge shows only the Discover feed tab on the new tab page.

    This policy works with the **[Set the default New Tab Page feed tab to Work or Discover](/en-us/deployedge/microsoft-edge-policies/SetNTPDefaultFeedTab)** policy, which controls which feed tab is selected by default when both tabs are available.

    [ConfigureNTPFeedTabVisibility](/en-us/deployedge/microsoft-edge-policies/ConfigureNTPFeedTabVisibility)
- **Microsoft Edge - Default Settings (users can override) &gt; Set the default New Tab Page feed tab to Work or Discover**

    This policy sets the default feed tab on the New Tab Page to Work or Discover. Your options:

    - `Work`: If you set this value or don't configure this policy, Microsoft Edge sets the default feed tab to Work.
    - `Discover`: Microsoft Edge sets the default feed tab to Discover.

    This policy only takes effect when **[Configure whether the Discover or Work feed tabs are shown on the New Tab Page](/en-us/deployedge/microsoft-edge-policies/ConfigureNTPFeedTabVisibility)** is set to `EnableBothWorkDiscover` or is not configured. If only one tab is visible, this policy has no effect.

    [SetNTPDefaultFeedTab](/en-us/deployedge/microsoft-edge-policies/SetNTPDefaultFeedTab)
- **Microsoft Edge &gt; Identity and sign-in &gt; Allow M365 authentication popups in work profiles**

    This policy controls whether Microsoft Edge allows Microsoft 365 authentication pop-ups to bypass the pop-up blocker in work profiles. When users are signed in with a work account, some Microsoft 365 sites, like `microsoft.com`, `cloud.microsoft.com`, and `visualstudio.com`, might open authentication pop-ups to `login.microsoftonline.com`, `login.live.com`, or `login.microsoft.com`. These pop-ups are required to complete sign-in.

    Your options:

    - If you enable this policy or don't configure it, Microsoft 365 authentication pop-ups are allowed in work profiles.
    - If you disable this policy, Microsoft 365 authentication pop-ups follow the default settings like other pop-ups. Users can choose to allow or block them, but they aren't automatically allowed.

    This policy only applies to work profiles. In personal profiles, Microsoft 365 authentication pop-ups are always allowed regardless of this policy's configuration.

    [M365AuthPopupsInWorkEnabled](/en-us/deployedge/microsoft-edge-policies/m365authpopupsinworkenabled)
- **Microsoft Edge &gt; Automatically open Copilot side pane with contextual insights for links opened from Outlook**

    This policy controls whether Microsoft Edge automatically opens the Microsoft Copilot side pane when users open web links from Outlook emails sent from the same tenant. Starting in Microsoft Edge version 148, when users open eligible links from Outlook emails sent from the same tenant, Microsoft Edge automatically opens the Copilot side pane with contextual insights. Copilot can use the originating Outlook email as context to surface relevant insights and suggested next steps alongside the web content.

    Your options:

    - If you enable this policy or don't configure it, the Copilot side pane opens automatically when users open links from Outlook emails sent from the same tenant.
    - If you disable this policy, the Copilot side pane doesn't open automatically when users open links from Outlook emails sent from the same tenant.

    This feature applies only to links opened from Outlook emails sent from the same tenant and requires Microsoft Copilot to be available for the user in Microsoft Edge. This feature is disabled if the **[Control Copilot access to page context for Microsoft Entra ID profiles](/en-us/deployedge/microsoft-edge-policies/CopilotPageContext)** policy or the **[Control Copilot access to Microsoft Edge page content for Entra account user profiles when using Copilot in the Microsoft Edge sidepane](/en-us/deployedge/microsoft-edge-policies/EdgeEntraCopilotPageContext)** policy is disabled, regardless of this policy's configuration. Copilot requires access to page content to provide contextual insights.

    [M365LinksAutoOpenCopilotEnabled](/en-us/deployedge/microsoft-edge-policies/M365LinksAutoOpenCopilotEnabled)
- **Microsoft Edge &gt; Enable the extended lifetime option for SharedWorkers**

    Controls whether Microsoft Edge keeps a SharedWorker running briefly after all tabs using it are closed, allowing background tasks to finish.

    Your options:

    - If you enable or don't configure this policy, SharedWorkers can use the extended lifetime option.
    - If you disable this policy, the extended lifetime option is ignored, even if it is requested by the page.

    This policy is temporary and will be removed in a future release.

    [SharedWorkerExtendedLifetimeEnabled](/en-us/deployedge/microsoft-edge-policies/sharedworkerextendedlifetimeenabled)
- **Microsoft Edge &gt; List of URL patterns for which developer tools are allowed to be opened**

    This policy controls where developer tools can be used in Microsoft Edge by specifying an allowlist of URL patterns. URL patterns are matched against the URL of every frame on the page being inspected.

    Your options:

    - If you configure this policy and don't configure the **[List of URL patterns for which developer tools are blocked](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailabilityBlocklist)** policy, developer tools are available only when every frame on the page matches a pattern in this allowlist. If any frame doesn't match, developer tools are blocked for the entire page. For information on the URL format, see [Filter formats for URL list-based policies](https://go.microsoft.com/fwlink/?linkid=2095322).
    - If you configure both this policy and the **[List of URL patterns for which developer tools are blocked](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailabilityBlocklist)** policy, this allowlist takes precedence. URLs that match this allowlist are allowed even if they also match the blocklist. URLs that match the blocklist but not this allowlist are blocked. URLs that match neither are governed by the **[Control where developer tools can be used](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailability)** policy.
    - If you disable or don't configure this policy, developer tools availability is determined by the **[List of URL patterns for which developer tools are blocked](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailabilityBlocklist)** and **[Control where developer tools can be used](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailability)** policies.

    This policy applies to developer tools opened for websites, extensions, and web applications. It supports up to 1,000 entries. Example value:

    ```text
    contoso.com
    https://ssl.server.com
    contoso.com/good_path
    https://server.contoso.com:8080/path
    .exact.hostname.com
    file://*
    ```

    [DeveloperToolsAvailabilityAllowlist](/en-us/deployedge/microsoft-edge-policies/developertoolsavailabilityallowlist)
- **Microsoft Edge &gt; List of URL patterns for which developer tools are blocked**

    This policy specifies URL patterns where developer tools are blocked. For information on the URL format, see [Filter formats for URL list-based policies](https://go.microsoft.com/fwlink/?linkid=2095322). URL patterns are evaluated against the URL of every frame on the page being inspected. If any frame matches a pattern in this policy, developer tools are blocked for the entire page.

    Your options:

    - If you configure this policy and don't configure the **[List of URL patterns for which developer tools are allowed to be opened](/en-us/deployedge/microsoft-edge-policies/developertoolsavailabilityallowlist)** policy, developer tools are blocked when any frame matches a pattern in this policy. If no frames match, availability is determined by the **[Control where developer tools can be used](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailability)** policy.
    - If you configure both this policy and the **[List of URL patterns for which developer tools are allowed to be opened](/en-us/deployedge/microsoft-edge-policies/developertoolsavailabilityallowlist)** policy, the allowlist takes precedence. URLs that match the allowlist are allowed, even if they also match this policy. URLs that match this policy (but not the allowlist) are blocked. If a URL matches neither, the **[Control where developer tools can be used](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailability)** policy determines availability.
    - If you disable or don't configure this policy, developer tools availability is determined by the **[List of URL patterns for which developer tools are allowed to be opened](/en-us/deployedge/microsoft-edge-policies/developertoolsavailabilityallowlist)** and **[Control where developer tools can be used](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailability)** policies.

    This policy supports up to 1,000 entries. Example value:

    ```text
    https://contoso.com
    contoso.com
    https://ssl.server.com
    contoso.com/bad_path
    https://server.contoso.com:8080/path
    .exact.hostname.com
    *
    file://*
    ```

    [DeveloperToolsAvailabilityBlocklist](/en-us/deployedge/microsoft-edge-policies/DeveloperToolsAvailabilityBlocklist)
- **Microsoft Edge &gt; Maximum number of concurrent connections to the proxy server for WebSocket requests**

    Specifies the maximum number of simultaneous connections to a proxy server for WebSocket requests. To configure limits for non-WebSocket requests, see the **[MaxConnectionsPerProxy](/en-us/deployedge/microsoft-edge-policies/MaxConnectionsPerProxy)** policy.

    If you don't configure this policy, the default value of 32 is used. Some web applications maintain multiple concurrent connections, like long-lived or hanging requests. Setting a value lower than the default may cause networking delays when many such applications are open. Some proxy servers can't handle a high number of concurrent connections per client. In these cases, reducing the value of this policy might improve reliability. The supported range is 6 to 256:

    - Values less than 6 are treated as 6.
    - Values greater than 256 are treated as 256.

    Modify this value only if required by your proxy server configuration or network environment.

    [MaxConnectionsPerProxyForWebSocket](/en-us/deployedge/microsoft-edge-policies/MaxConnectionsPerProxyForWebSocket)
- **Microsoft Edge &gt; Controls the availability of browsing with Copilot in Microsoft Edge**

    When browsing with Copilot is enabled, users can explicitly invoke it for a query. It isn't invoked automatically. Browsing with Copilot is available only on domains specified in the **[Browsing with Copilot Allowed URLs](/en-us/deployedge/microsoft-edge-policies/BrowsingWithCopilotAllowList)** policy and is blocked on domains specified in the **[Browsing with Copilot Blocked URLs](/en-us/deployedge/microsoft-edge-policies/BrowsingWithCopilotBlockList)** policy. If no domains are configured in the allow list, browsing with Copilot is effectively disabled.

    This feature is available only to users with an active Microsoft 365 Copilot subscription. For more information about configuring browsing with Copilot, see [Configure browsing with Copilot](https://go.microsoft.com/fwlink/?LinkId=2341535).

    Your options:

    - If you enable this policy, browsing with Copilot is turned on for all users who receive the policy, and users can't turn it off.
    - If you disable this policy, browsing with Copilot is turned off for all users who receive the policy, and users can't turn it on.
    - If you don't configure this policy, browsing with Copilot is off by default, and users can turn it on.

    [AllowBrowsingWithCopilot policy](/en-us/deployedge/microsoft-edge-policies/allowbrowsingwithcopilot)
- **Microsoft Edge &gt; Browsing with Copilot Allowed URLs**

    Allows you to define a list of URLs where browsing with Copilot is available. Users can't modify this list.

    Your options:

    - If you enable this policy, browsing with Copilot is available only on the sites specified in the list. To allow a broader set of sites while blocking specific exceptions, configure this policy together with the **[Browsing with Copilot Blocked URLs](/en-us/deployedge/microsoft-edge-policies/BrowsingWithCopilotBlockList)** policy. For example, you can include `*` to allow all sites, and then use the block list to restrict access to specific URLs. You can define exceptions based on schemes, subdomains, ports, or origins. When multiple filters apply, the most specific match determines whether a URL is allowed or blocked. The block list takes precedence over the allow list.
    - If you disable or don't configure this policy, browsing with Copilot is unavailable on all sites, even if the **[Controls the availability of browsing with Copilot in Microsoft Edge](/en-us/deployedge/microsoft-edge-policies/allowbrowsingwithcopilot)** policy is enabled.

    Browsing with Copilot supports only HTTP and HTTPS protocols. Wildcards (`*`) are supported, and subdomains are matched even without wildcards. This policy applies only to the site origin; any path specified in the URL pattern is ignored. For guidance on formatting URL patterns, see [Filter formats for URL list-based policies](https://go.microsoft.com/fwlink/?linkid=2095322). Example value:

    ```text
    https://www.contoso.com
    [*.]contoso.edu
    contoso.net
    login.contoso.us
    ```

    [BrowsingWithCopilotAllowList](/en-us/deployedge/microsoft-edge-policies/BrowsingWithCopilotAllowList)
- **Microsoft Edge &gt; Browsing with Copilot Blocked URLs**

    Controls the list of URLs where browsing with Copilot is blocked. Users can't modify this list. Use this policy to define exceptions to broader allowlists. For example, you can set **[Browsing with Copilot Allowed URLs](/en-us/deployedge/microsoft-edge-policies/BrowsingWithCopilotAllowList)** to `*` to allow all sites, and then use this policy to block access to specific URLs. This policy supports blocking by scheme, subdomain, or port. When multiple URL patterns apply, the most specific match determines whether access is allowed or blocked. Blocklist entries take precedence over allowlist entries.

    If you don't configure this policy, no exceptions are applied to **[Browsing with Copilot Allowed URLs](/en-us/deployedge/microsoft-edge-policies/BrowsingWithCopilotAllowList)**. Browsing with Copilot supports only HTTP and HTTPS protocols. Wildcards (`*`) are supported, and subdomains are matched even without wildcards. URL matching is based on the site origin only; any path specified in the pattern is ignored. For information about URL pattern format, see [Filter formats for URL list-based policies](https://go.microsoft.com/fwlink/?linkid=2095322). Example value:

    ```text
    https://www.contoso.com
    [*.]contoso.edu
    contoso.net
    login.contoso.us
    ```

    [BrowsingWithCopilotBlockList](/en-us/deployedge/microsoft-edge-policies/BrowsingWithCopilotBlockList)
- **Microsoft Edge &gt; Enable the Copilot new tab page**

    This policy configures the availability of the Copilot new tab page in Microsoft Edge for Business. The Copilot new tab page combines search and chat into a single input box and includes personalized cards that provide quick access to relevant files, calendar events, and suggested Copilot prompts. Users who don't have a Microsoft 365 Copilot license might experience limited relevance in Copilot prompt card content.

    Most policies that customize the New Tab Page are supported on the Copilot new tab page. For a complete list of supported and unsupported policies, see [Configure the Copilot new tab page](https://go.microsoft.com/fwlink/?linkid=2330462). This policy applies only to Microsoft Entra ID profiles and controls the Copilot new tab page experience in Microsoft Edge for Business. This policy doesn't apply to the Copilot new tab page on personal Microsoft account profiles.

    Your options:

    - If you enable this policy, the Copilot new tab page is turned on.
    - If you disable or don't configure this policy, the Copilot new tab page is turned off. When the policy isn't configured, users can turn it on via user settings.

    [CopilotNewTabPageEnabled](/en-us/deployedge/microsoft-edge-policies/CopilotNewTabPageEnabled)
- **Microsoft Edge &gt; Manageability &gt; Allow MAM enrollment when managed device has Purview DLP policy configured**

    Controls whether Microsoft Edge allows Mobile Application Management (MAM) enrollment on managed devices when Microsoft Purview Data Loss Prevention (DLP) is configured.

    Your options:

    - If you enable this policy, MAM enrollment is allowed even when Purview DLP is detected on the device.
    - If you disable or don't configure this policy, MAM enrollment is blocked when Purview DLP is detected on the device.

    [MAMWithDeviceDLPEnabled](/en-us/deployedge/microsoft-edge-policies/MAMWithDeviceDLPEnabled)

To learn more about the settings catalog, see [Use the Intune settings catalog to configure settings](../device-configuration/settings-catalog/).

Applies to:

- Windows

#### New Wired Networks device configuration profile for iOS/iPadOS

There's a new **802.1x Wired Networks** device configuration profile for iOS/iPadOS devices. The feature supports 802.1x Ethernet access controls, which is ideal for M-series iPads that support native resolution screen extension. It allows iPads to securely connect to hot desk docks and monitors using wired access.

This profile:

- Supports EAP protocols, like TLS, PEAP, and TTLS
- Is similar to the macOS wired network profile experience

This feature helps with secure enterprise deployments for iPads in education, finance, and other regulated industries.

To learn more about wired networks, see [Add and use wired networks settings on your devices](../device-configuration/templates/configure-wired-networks).

Applies to:

- iOS/iPadOS 17 and newer

### Device management

#### Detect and block Shadow AI using the properties catalog, device query, and a security baseline (preview)

Using Intune, you can detect and block a Local AI Agent, like OpenClaw, on Windows devices enrolled in Intune. Specifically, you can:

- Use a [Properties catalog](../device-configuration/collect-device-properties) policy to collect the Local AI Agent entity. Admins can use this information to identify devices where OpenClaw is present or active.
- Use [Device Query](../advanced-analytics/device-query-multiple-devices) to view devices with a Local AI Agent, like OpenClaw.
- Use the [Local AI Agent Baseline - OpenClaw (Preview)](../device-security/security-baselines/ref-openclaw-settings) to block users from using OpenClaw.

This feature is in [preview](../fundamentals/public-preview).

Applies to:

- Windows

### Device security

#### In-place renewal of Cloud PKI issuing certification authorities (CAs)

Microsoft Intune now supports in-place renewal of eligible Cloud PKI issuing certification authorities (CAs). Previously, renewing an issuing CA required creating a new CA and manually updating dependent SCEP certificate profiles, which increased operational overhead and configuration risk. With in-place renewal, certificate issuance continues uninterrupted for scenarios such as Wi-Fi, VPN, and email, without changes to existing SCEP profiles or device assignments.

For more information, see [Renew a certification authority in Cloud PKI](../cloud-pki/renew-ca).

#### Strict Tunnel Mode for Microsoft Tunnel on Android

Microsoft Tunnel now supports Strict Tunnel Mode on Android Enterprise devices. When Strict Tunnel Mode is enabled, all network traffic is forced through the VPN tunnel. If the VPN connection is unavailable or drops, all network traffic on the device is blocked until the VPN reconnects, preventing apps from accessing the public internet outside of the tunnel.

Strict Tunnel Mode is available when a Microsoft Tunnel VPN profile is configured with Always-on VPN. Admins can configure an app exclusion list to allow specific apps to bypass the tunnel and connect directly to the network, regardless of VPN connection status.

Strict Tunnel Mode requires devices enrolled through Android Management API (AM API). For unenrolled devices using Microsoft Tunnel for Mobile Application Management (MAM), Strict Tunnel Mode is available through the Microsoft Edge app configuration policy.

For more information about Microsoft Tunnel capabilities, see [Overview of Microsoft Tunnel](../device-security/microsoft-tunnel/overview#capabilities).

Applies to:

- Android Enterprise corporate-owned fully managed
- Android Enterprise corporate-owned work profile
- Android Enterprise personally owned work profile
- Android (MAM, unenrolled devices)

#### Grant enhanced security permissions to a Mobile Threat Defense app on Android

A new **Mobile Threat Defense role** category is available on the Mobile Threat Defense connector configuration page in the Microsoft Intune admin center. The **Grant MTD role permissions to *&lt;MTD partner name&gt;* on enrolled Android COBO and COPE devices** toggle lets you grant enhanced security permissions to one Mobile Threat Defense partner app, such as Microsoft Defender for Endpoint or a supported third-party partner, on enrolled Android Enterprise corporate-owned fully managed (COBO) and Android Enterprise corporate-owned work profile (COPE) devices.

When you turn on this toggle, the selected MTD app receives the following exemptions on targeted devices:

- **Suspension** — The app is prevented from being suspended.
- **Hibernation** — The app is prevented from entering hibernation.
- **Power restrictions** — The app is exempt from power-related restrictions such as app standby, and can start foreground services from the background.
- **User controls** — Users can't clear app data or force-stop the app.

These exemptions help the MTD app maintain continuous threat protection without interruption from system or user actions. Only one MTD partner can hold these permissions per tenant.

For Microsoft Defender for Endpoint, a second toggle is also available: **Automatically launch Microsoft Defender for Endpoint during setup on Android COBO and COPE devices**. When enabled, the Defender for Endpoint app automatically launches during device setup, allowing it to complete its initial configuration without requiring the user to manually open it.

For more information, see [Mobile Threat Defense role](../device-security/mobile-threat-defense/enable-connector#mobile-threat-defense-toggle-options).

Applies to:

- Android Enterprise corporate-owned fully managed
- Android Enterprise corporate-owned work profile

#### Vulnerability Remediation Agent now uses Microsoft Entra agentic identity (preview)

*This feature is rolling out to tenants gradually and may take several weeks to become available in your environment.*

**The Vulnerability Remediation Agent is now available to all customers in preview.** Previously, the agent was available only to a select group of customers in a limited preview.

The [Vulnerability Remediation Agent](../copilot/agents/vulnerability-remediation-agent) now uses [Microsoft Entra agentic identity](/en-us/entra/agent-id/) instead of a human user identity. When you set up a new agent instance, the setup process automatically provisions an agentic identity in your tenant's Entra directory. The agent runs under the permissions delegated to this agentic user, providing a more secure and scalable identity model.

**What this means for existing agents:** If you already have a Vulnerability Remediation Agent instance that uses a human user identity, your agent continues to work as-is for now. Human user identity support expires 90 days after this release, after which you must transition to an agentic identity. A banner on the agent page notifies you when agentic identity is available for your agent. For transition steps and details, see [Transition existing agents to agentic identity](../copilot/agents/vulnerability-remediation-agent#transition-existing-agents-to-agentic-identity).

**What's new for agentic identity:**

- New agent instances are provisioned with an agentic identity during setup.
- After setup, you must delegate the required permissions to the agentic user in the Microsoft Entra and Microsoft Defender admin centers.
- Use the **Run Readiness Check** button to verify that all required permissions are in place before running the agent.

For more information, see [Agent identity](../copilot/agents/vulnerability-remediation-agent#agent-identity).

## Week of June 1, 2026

### Device management

#### Remote Help for Windows updated with performance improvements

The latest version of Remote Help for Windows (version 5.2.1037.0) includes general bug fixes and performance improvements to enhance reliability.

## Week of May 26, 2026

### Role-based access control

#### Intune RBAC roles have access to Copilot in Intune

When Microsoft Intune is enabled as a data source in Security Copilot, by default:

- The Microsoft Entra ID **Intune Administrator** role automatically inherits **Security Copilot owner** access to Copilot in Intune.
- All the other built-in and custom Intune role-based access (RBAC) roles automatically inherit **Security Copilot contributor** access to Copilot in Intune.

Intune admins can use Security Copilot capabilities in Intune without requiring more role assignments.

Previously, access to Copilot in Intune required a separate role assignment in Security Copilot or a Microsoft Entra ID role, like the Intune Administrator role.

This update reduces access friction and simplifies Copilot onboarding for organizations.

To learn more, see:

- [Microsoft Copilot in Intune](../copilot/)
- [Roles and authentication in Microsoft Security Copilot](/en-us/copilot/security/authentication)

## Week of May 18, 2026

### Device security

#### Guidance for device-reported values in compliance reports

We updated documentation to clarify how to interpret device-reported values in compliance reports. Some compliance reports include a **Setting** column with values reported directly by the device, providing additional context for noncompliance in scenarios such as custom compliance and Android app configuration reporting. This update adds guidance on treating these values as informational only and highlights security considerations for reviewing device-reported data. For more information, see [Device-reported values in compliance reports](../device-security/compliance/monitor-policy#device-reported-values-in-compliance-reports).

## Week of May 11, 2026

### Device enrollment

#### Complete Platform SSO registration during macOS Automated Device Enrollment

On macOS devices enrolled with Automated Device Enrollment (ADE), you can run Platform SSO during device registration. Before you enroll, you:

1. Create an Intune [settings catalog policy](../device-configuration/settings-catalog/) and configure the **Enable Registration During Setup** setting.
2. Deploy the Company Portal (5.2604.0 and newer) as a line-of-business app.
3. Configure the Automated Device Enrollment policy to use Setup Assistant with modern authentication and enable await final configuration.

When this feature is enabled, users have access to Microsoft Entra ID resources immediately when they arrive at desktop.

To learn more, see [Configure Platform Single Sign-On (PSSO) during Automated Device Enrollment for macOS devices](../device-configuration/settings-catalog/configure-platform-sso-during-enrollment).

Applies to:

- macOS 26 and newer
- Company Portal 5.2604.0 and newer

## Week of May 4, 2026

### Monitor and troubleshoot

#### Enhanced app inventory with faster data updates

Intune enhanced app inventory brings faster, more detailed visibility into the apps in your environment to support identification of outdated or risky software. Improved data freshness and richer app metadata provide clearer insight into installed applications, while new controls let you specify which devices are included in inventory collection.

This feature is initially available for Windows, with additional platforms to follow.

Applies to:

- Windows 10/11

## Week of April 27, 2026 (Service release 2604)

### Advanced capabilities

#### Expanded support for Endpoint Privilege Management support approved elevation requests

Intune's Endpoint Privilege Management (EPM) now supports [support approved elevation requests](../epm/manage-support-approvals) from all users of a device. This update expands the utility of support approved file elevations and helps to improve scenarios that involve shared devices.

Previously, file elevation requests that require support approval were supported from only a device's primary user or the user who enrolled the device.

For more information about this type of elevation request, see [Support approved file elevations for Endpoint Privilege Management](../epm/manage-support-approvals).

### Device configuration

#### Configure credential manager permissions for Android Enterprise devices

You can now control which applications act as system-level credential providers on managed Android Enterprise devices running Android 14 and higher. Credential providers are responsible for password autofill and passkey storage.

To configure credential manager permissions, go to **Apps** &gt; **Android** &gt; **Configuration** &gt; **Managed Devices** and choose **Android Enterprise** as the platform type.

By default, Android blocks third-party credential providers on managed devices. This configuration setting lets you:

- Allow specific apps (such as Microsoft Authenticator or a third-party password manager) to act as credential providers
- Enable passkey-based sign-in across managed Android Enterprise devices
- Maintain control over which credential sources are trusted on corporate devices

A known limitation is that Google Password Manager can't act as a credential provider on corporate-owned work profile or personally owned work profile devices. It is blocked on the end user's device. Use a different credential app as a workaround.

For more information, see [Add app configuration policies for managed Android Enterprise devices](../app-management/configuration/configure-managed-android).

Applies to:

- Android fully managed devices (COBO)
- Android dedicated devices (COSU)
- Android corporate-owned devices with a work profile (COPE)
- Android personally owned devices with a work profile (BYOD) using Android Management API (AM API)

#### Block location setting for Android Enterprise can keep Location services enabled

On Android Enterprise devices, you can use the **General &gt; Block location** in the [settings catalog](../device-configuration/settings-catalog/ref-android-settings) to disable the location services on the device and prevent users from turning it on.

This setting is now called **Location** and has three options you can configure:

- Device default - Intune doesn't change or update this setting. By default, the OS allows end users to turn location services on or off.
- Location enabled - Requires location services to be on and prevents end users from turning them off.
- Location disabled - Requires location services to be off and prevents end users from turning them on.

For a list of all the settings you can configure, see [Android Intune settings catalog settings list](../device-configuration/settings-catalog/ref-android-settings).

Applies to:

- Android Enterprise corporate-owned devices with a work profile (COPE) running Android 10 and earlier
- Android Enterprise corporate owned fully managed (COBO)
- Android Enterprise corporate owned dedicated devices (COSU)

### Device enrollment

#### Access management for Apple services

You can now use Apple access management settings in Apple Business Manager and Apple School Manager to configure service access for Apple accounts on organization-owned devices. These controls let you choose what devices users can sign in to and which apps and services are available to them. For more information, see [Configure service access for Apple accounts](../device-enrollment/apple/setup-account-service-access).

Applies to:

- iOS/iPadOS
- macOS

#### Microsoft Intune supports userless ADE for visionOS and tvOS devices

Microsoft Intune has added support for userless Apple automated device enrollment (ADE) for visionOS and tvOS devices, enabling you to enroll and manage Apple Vision Pro and Apple TV through Apple Business Manager or Apple School Manager. This capability supports ADE without user affinity and includes custom configuration uploads for settings, default enrollment restrictions, and device actions. The feature is available with Microsoft Intune Plan 2 as part of the Microsoft 365 Suite.

Enrolled visionOS and tvOS devices appear alongside iOS and iPadOS devices in the Intune admin center within **Apple mobile** and can be filtered. Support requires tvOS 26 and later or visionOS 26 and later. We recommend that you keep these devices up to date to receive the latest security fixes.

For more information, see:

- [Overview of Apple ADE for Apple mobile](../device-enrollment/apple/overview-automated-enrollment-apple)
- [Use the Intune settings catalog to configure settings](../device-configuration/settings-catalog/)
- [Device actions](../device-management/actions/)

Applies to:

- tvOS 26 and later
- visionOS 26 and later

### Device management

#### Support for Ubuntu 26.04 LTS

Microsoft Intune now supports Ubuntu 26.04 LTS. Support for Ubuntu 22.04 LTS ends in August 2026. Devices already enrolled on Ubuntu 22.04 remain enrolled, but you should notify users to upgrade to a supported Ubuntu version. You can identify devices running Ubuntu 22.04 in the Intune admin center by going to **Devices** &gt; **All devices**, filtering by **Linux**, and adding the **OS version** column. For more information, see [Enroll Linux desktop devices in Microsoft Intune](../device-enrollment/guide-linux).

#### Preview the new device page in the Intune admin center (preview)

In the Intune admin center, when you go to **Devices** &gt; **All Devices** and select a device, you can see device-specific info, like device properties.

This page is redesigned and is available for you to preview. To enable the new experience:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **All Devices**.
2. Move the **Preview new device view** toggle to **On**.

The new experience is only available when you go to **Devices** &gt; **All Devices** and select a device. If you open a device page from a different part of the Intune admin center, like from a report, the original page view is shown, even with the toggle enabled.

When turned on, you see the new full page layout that gives you a single view of the device. Use this view to:

- Track device activity
- Access tools and reports
- Manage device information

The single device page has the following tabs:

- **Device action status**: Shows requested, in‑progress, and recently completed device actions. You can search, sort, and filter this list. You can quickly see what actions are running or have completed without leaving the device view.
- **Tools and reports**: This tab was previously called **Overview**. It shows monitoring reports, like compliance and device configuration status, tools, like remediations. These features were previously accessed in other parts of the Intune admin center.
- **Properties**: Contains admin‑modifiable device properties with visible scope tags and a dedicated editing view.
- **Device details**: This tab was previously called **Hardware**. It provides physical device information and key Intune and Microsoft Entra management details.

Other features:

- Device actions are grouped, ordered, and labeled consistently across platforms and device types, and only shows relevant and permitted actions. Destructive actions are separated and require confirmation, reducing unintentional actions.
- The updated layout uses a standard structure across device types and platforms, while adapting to platform‑specific capabilities.
- Improved labeling, hierarchy, and formatting make device information easier to scan and understand. The **Essentials** section elevates important device information and is accessible from any tab.

All existing device management capabilities remain available. This update focuses on making them easier to find and use.

#### New remote actions to suspend and restore Managed Home Screen on Android devices

Intune has two new remote actions that allow admins to temporarily suspend and restore Managed Home Screen (MHS) on Android devices. These actions let users exit MHS and access the device's default launcher for a defined period, without removing policies or requiring a PIN.

When the specified duration expires, or when the *restore managed home screen action* is triggered, MHS automatically re-locks the device into the kiosk experience. This helps maintain security while reducing disruption during troubleshooting or short-term use outside of MHS.

To learn more, see:

- [Suspend Managed Home Screen](../device-management/actions/suspend-managed-home-screen)
- [Restore Managed Home Screen](../device-management/actions/restore-managed-home-screen)

Applies to:

- Android Enterprise corporate-owned Fully Managed (COBO)
- Android Enterprise corporate-owned Dedicated (COSU)

#### Updated minimum version for Intune Management Extension on Windows

Windows devices managed by Intune need to run Intune Management Extension version 1.58.103.0 or later. Devices on earlier versions no longer receive configurations or updates that depend on the Intune Management Extension, including Win32 app deployments, PowerShell scripts, remediations, and platform scripts.

The Intune Management Extension updates automatically, so most managed devices should already have a compatible version. Verify that your devices can sync with Intune to receive updates.

Applies to:

- Windows 10/11

### Device security

#### Autopatch update risk visibility report

The *Autopatch update risk visibility* report extends the *security update status* dashboard with granular insight into patch compliance and risk across your managed devices. It classifies devices as *Current*, *Exposed*, or *Critical* and highlights policies contributing to risk, so you can identify and remediate issues faster.

For more information, see [Protect your estate: Reassess your Windows update policies](https://aka.ms/ReassessProtect).

Applies to:

- Windows

#### Updated security baseline for Microsoft Edge v139

Microsoft Edge version 139 security baseline is now available in Microsoft Intune. This baseline reflects current Microsoft security recommendations for the Microsoft Edge browser and is the latest available Edge security baseline in Intune.

The Edge v139 security baseline includes new settings, updated default values, and retired settings.

Existing security baseline profiles don't automatically update to the new version. To use this baseline, Intune admins can [create a new baseline profile](../device-security/security-baselines/configure-baselines#create-a-profile-for-a-security-baseline) or [update an existing profile to the latest version](../device-security/security-baselines/configure-baselines#update-a-baseline-profile-to-the-latest-version).

We recommend carefully reviewing the settings in the new baseline before moving from a previous baseline version, especially if existing profiles include customizations.

For a detailed breakdown of setting changes, see the blog post [Security baseline for Microsoft Edge version 139](https://techcommunity.microsoft.com/blog/microsoft-security-baselines/security-baseline-for-microsoft-edge-version-139/4441251).

To view the default configuration of settings in the updated baseline, see [Microsoft Edge security baseline settings reference](../device-security/security-baselines/ref-edge-settings?pivots=edge-v139).

### Intune apps

#### Direct Android line-of-business app management

You can now manage Android line-of-business (LOB) apps directly in Microsoft Intune without publishing them to Managed Google Play on Android Enterprise corporate-owned fully managed (COBO) and dedicated (COSU) devices.

With direct LOB app management, admins can upload APK files directly to Intune and deploy required apps to supported Android Enterprise enrollment types using a native Intune workflow.

Direct LOB app management enables you to:

- Deploy in-house LOB APKs to fully managed and dedicated devices without publishing them to Managed Google Play
- Manage the app lifecycle directly from Intune
- Create app configuration policies for directly deployed LOB apps, giving you the same configuration flexibility you have for Managed Google Play apps

For more information, see [Add an Android line-of-business app to Microsoft Intune](../app-management/deployment/add-lob-android).

Applies to:

- Android Enterprise

#### Newly available protected apps for Intune

The following protected apps are now available for Microsoft Intune:

- Harvey AI by Harvey AI Corporation (iOS)
- Continia Expense App by Continia Software A/S

For more information about protected apps, see [Microsoft Intune protected apps](../app-management/ref-protected-apps).

### Tenant administration

#### Change Review Agent suggestions available inline in Multi Admin Approval (preview)

The [Change Review Agent](../copilot/agents/change-review-agent) now provides risk-based recommendations directly in the Multi Admin Approval experience for Windows PowerShell scripts. On the *My requests* and *All requests* tabs, a new **Agent Response** column displays when a suggestion is available. You can then select the suggestion to open and complete the Change Review Agent's approval workflow for that request without leaving the Multi Admin Approval node.

Change Review Agent suggestions continue to be available in the agent's primary experience as well.

For more information, see [Change Review Agent suggestions in Multi Admin Approval](../fundamentals/role-based-access-control/multi-admin-approval#change-review-agent-suggestions-in-multi-admin-approval).

## Week of April 20, 2026

### Device security

#### New reporting considerations for compliance policies

New guidance has been added to the Microsoft Intune compliance policy reporting documentation to help explain how device compliance results appear in Intune reports. This update clarifies expected reporting behavior related to device check-in timing and user association, helping you better interpret compliance policy reports. For more information, see [Known reporting behaviors](../device-security/compliance/monitor-policy#known-reporting-behaviors).

### Monitor and troubleshoot

#### Intune Data Warehouse (beta) connector retirement in Power BI

The Intune Data Warehouse (beta) connector v1 in Power BI is retired. If you use Power BI reports that rely on this connector, you need to transition to Intune connector v2 or the OData Feed connector before the transition completes. Power BI reports created after November 2025 already use connector v2, while reports created before that date may still use the beta connector and need updating. This change improves the long-term reliability and supportability of Intune data access.

**Customer impact**: This change does not introduce new user interface experiences. Customers who still rely on the Intune Data Warehouse (beta) connector in Power BI may be affected if they have not transitioned to supported alternatives. Customers already using supported and documented data access options do not experience disruption.

**Required customer action**: Review the published guidance and transition away from the Intune Data Warehouse (beta) connector in Power BI before the transition completes. Customers who do not take action lose access to data through the beta connector after it is retired.

**Timing and rollout**: Customer communications begin in late April 2026. The transition occurs gradually over two weeks starting April 20, 2026.

For more information, see [Use the Microsoft Intune Data Warehouse](../developer/data-warehouse/create-reports).

Applies to:

- Windows
- iOS/iPadOS
- macOS
- Android

## Week of April 6, 2026

### Device enrollment

#### Support for Android XR devices

Microsoft Intune now supports management of Android XR devices using Android Enterprise dedicated and fully managed enrollment modes. You can enroll Android XR devices, deploy apps through managed Google Play, and apply core security and compliance policies. Android XR devices appear and are managed alongside other Android devices in the Intune admin center. For more information about supported scenarios and current limitations, see [Microsoft Intune announces Android Enterprise management support for Android XR](https://techcommunity.microsoft.com/blog/microsoftintuneblog/microsoft-intune-announces-android-enterprise-management-support-for-android-xr/4508499).

### Tenant administration

#### New TeamViewer connector experience in Microsoft Intune

There is a new TeamViewer integration in Microsoft Intune that simplifies onboarding and improves reliability for remote assistance workflows. The new connector replaces the existing TeamViewer connector experience and provides a more streamlined experience in the Intune admin center. If you're using the previous TeamViewer connector, you must migrate to the new connector within 12 months to maintain functionality. For more information about the new connector, see [Use the TeamViewer integration in Microsoft Intune](../device-management/tools/setup-teamviewer).

## Week of March 30, 2026 (Service release 2603)

### App management

#### Declarative Device Management for Apple line-of-business apps on iOS/iPadOS

Microsoft Intune now supports Apple Declarative Device Management (DDM) for required line-of-business apps on devices running iOS/iPadOS 18 and later. By changing the management type to DDM in App information, you can deploy and configure apps using Apple's policy-based model, which improves delivery efficiency, provides real-time app status, and expands per-app options such as associated domains.

Applies to:

- iOS/iPadOS

### Device configuration

#### Recovery lock features available for macOS devices

On macOS devices, you can configure a recovery OS password that prevents users from booting company-owned devices into recovery mode, reinstalling macOS, and bypassing remote management. Admins can also rotate this password.

There are two ways to use this feature:

- **Settings catalog policy** - In a [settings catalog](/en-us/intune/device-configuration/settings-catalog) policy, you can use the Recovery Lock settings to:

    - Turn on the recovery lock feature
    - Configure a password rotation schedule
- **Remote device action** - Use the [Recovery Lock device action](../device-management/actions/rotate-recovery-lock-passcode) to manually rotate the recovery lock password for a specific device.

The Recovery Lock password can be viewed in the per-setting status report &gt; **Passwords and keys**. To view the Recovery Lock password, the signed-in administrator needs the **Remote tasks/View macOS recovery lock password** permission.

Applies to:

- macOS

#### New supported OEMConfig app for Android Enterprise

The following OEMConfig app is available in Intune for Android Enterprise:

- Inventus | `com.inventus.oemconfig.gen`

For more information about OEMConfig, see [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](../device-configuration/templates/configure-oemconfig-android).

#### New settings in the Windows settings catalog

There are new settings in the Windows settings catalog. To see and configure these settings in Intune, create a Windows settings catalog profile (**Devices &gt; Configuration profiles &gt; Create profile &gt; Windows 10 and later &gt; Settings catalog**).

The new policies include:

- **Connectivity &gt; Disable Cross Device Resume**: This feature lets Windows suggest continuing an activity users start on a device, like a phone, to a PC. IT admins can use this policy to turn off this feature and prevent users from continuing tasks, like browsing files or continuing to use supported apps that require linking between a phone and PC.

    When set to **CrossDeviceResume is Disabled**, the Windows device doesn't receive any CrossDeviceResume notification. Users won't see any "resume from your phone" prompts. When you select **CrossDeviceResume is Enabled**, the Windows device does receive notification to resume activity from linked devices. If you don't configure this policy setting, the default behavior is that the CrossDeviceResume feature is turned on, which means users see the notification. Changes to this policy take effect on reboot.

    This policy:

    - Is available to Windows Insiders.
    - Uses the [DisableCrossDeviceResume](/en-us/windows/client-management/mdm/policy-csp-Connectivity#disablecrossdeviceresume) CSP.
- **Windows AI &gt; Remove Microsoft Copilot App**: This policy setting allows you to uninstall the Microsoft Copilot app from devices. It applies to devices and users that meet the following conditions:

    - The Microsoft 365 Copilot and Microsoft Copilot apps are both installed.
    - The Microsoft Copilot app was not installed by the user.
    - The Microsoft Copilot app was not opened in the last 14 days.

    If this policy is enabled, the Microsoft Copilot app is uninstalled. Users can still re-install if they choose to.

    [RemoveMicrosoftCopilotApp](/en-us/windows/client-management/mdm/policy-csp-WindowsAI#removemicrosoftcopilotapp) CSP

Applies to:

- Windows

To learn more about the settings catalog, see [Use the Intune settings catalog to configure settings](/en-us/intune/device-configuration/settings-catalog).

#### New updates to the Apple settings catalog

The [Settings Catalog](/en-us/intune/device-configuration/settings-catalog) lists all the settings you can configure in a device policy, and all in one place. For more information about configuring Settings Catalog profiles in Intune, see [Create a policy using settings catalog](/en-us/intune/device-configuration/settings-catalog).

There are new settings in the Settings Catalog. To see these settings, in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy** &gt; **iOS/iPadOS** or **macOS** for platform &gt; **Settings catalog** for profile type.

##### iOS/iPadOS

**Declarative Device Management (DDM) &gt; External Intelligence Settings**:

- Allow Sign In
- Allowed Workspace IDs

**Declarative Device Management (DDM) &gt; Intelligence Settings**:

- Allow Apple Intelligence Report
- Allow Genmoji
- Allow Image Playground
- Allow Image Wand
- Allow Personalized Handwriting Results
- Allow Visual Intelligence Summary
- Allow Writing Tools
- Mail &gt; Allow Smart Replies
- Mail &gt; Allow Summary
- Notes &gt; Allow Transcription
- Notes &gt; Allow Transcription Summary
- Safari &gt; Allow Summary
- Force On Device Only Dictation
- Force On Device Only Translation

**Declarative Device Management (DDM) &gt; Keyboard Settings**:

- Allow Definition Lookup
- Allow Auto Correction
- Allow Dictation
- Allow Predictive Text
- Allow Slide To Type
- Allow Spell Check
- Allow Text Replacement
- Allow Math Keyboard Suggestions

**Declarative Device Management (DDM) &gt; Siri Settings**:

- Allow User Generated Content
- Allow While Locked
- Force Profanity Filter

##### macOS

**Declarative Device Management (DDM) &gt; External Intelligence Settings**:

- Allow Sign In
- Allowed Workspace IDs

**Declarative Device Management (DDM) &gt; Intelligence Settings**:

- Allow Apple Intelligence Report
- Allow Genmoji
- Allow Image Playground
- Allow Writing Tools
- Mail &gt; Allow Smart Replies
- Mail &gt; Allow Summary
- Notes &gt; Allow Transcription
- Notes &gt; Allow Transcription Summary
- Safari &gt; Allow Summary
- Force On Device Only Dictation

**Declarative Device Management (DDM) &gt; Keyboard Settings**:

- Allow Definition Lookup
- Allow Dictation
- Allow Math Keyboard Suggestions

**Declarative Device Management (DDM) &gt; Siri Settings**:

- Force Profanity Filter

**System Configuration &gt; File Provider**:

- Management Allows Remote Syncing
- Management Remote Syncing Allow List
- Management Allows External Volume Syncing
- Management External Volume Syncing Allow List
- Management Domain Auto Enablement List

**Restrictions**:

- Allow Rosetta Usage Awareness

Applies to:

- iOS/iPadOS
- macOS

### Device management

#### Remote Help connectivity update for Windows devices

We've improved connectivity when using the [Launch Remote Help](../remote-help/start-session#provide-help) capability in the Intune admin center for Windows devices. For the best experience, we recommend updating firewall rules to include this new endpoint:

- `*.trouter.communications.svc.cloud.microsoft`

For the current list of required network endpoints, see [Network requirements for PowerShell scripts and Win32 apps](../fundamentals/endpoints?tabs=north-america#network-requirements-for-powershell-scripts-and-win32-apps) and [Remote Help](../fundamentals/endpoints#remote-help) in the Intune endpoints documentation.

With this endpoint addition, we've also added a new [Intune Management Extension log](../device-management/tools/management-extension-windows#ime-log-files), NotificationInfra.log, which tracks notifications sent through the Microsoft real-time communication channel.

Applies to:

- Windows

#### Support for Red Hat Enterprise Linux 9 and later

Microsoft Intune supports Red Hat Enterprise Linux (RHEL) 9 LTS and RHEL 10 LTS. Support for RHEL 8 LTS will end in July 2026. Devices already enrolled on RHEL 8 will remain enrolled. You can identify devices running RHEL 8 in the Intune admin center by going to **Devices** &gt; **All devices**, filtering OS by Linux, and adding OS version columns. Notify users to upgrade their devices to a supported RHEL version. For more information about enrolling Linux devices, see [Enrollment guide: Enroll Linux desktop devices in Microsoft Intune](../device-enrollment/guide-linux).

#### Microsoft Intune app for Linux now supports the Microsoft Identity Broker

The Microsoft Intune app for Linux now uses the Microsoft Identity Broker on supported Ubuntu and Red Hat Enterprise Linux (RHEL) distributions. Broker version 2.0.2 and later introduces a major architectural change from the previous Java-based broker. This update enables new single sign-on (SSO) experiences using phish-resistant MFA, smart card authentication, and certificate-based authentication with Microsoft Entra ID. For more information, see [Enabling Phish-Resistant MFA (PRMFA) on Linux devices](/en-us/entra/identity/devices/sso-linux?tabs=debian-install%2Cdebian-update%2Cdebian-uninstall#enabling-phish-resistant-mfa-prmfa-on-linux-devices-preview).

### Device security

#### Intune security baseline for Windows 11, version 25H2

The Windows security baseline for *Windows 11, version 25H2* is now available in Microsoft Intune. This baseline reflects current Microsoft security recommendations for supported Windows devices and is the latest available Windows security baseline in Intune.

The Windows 11, version 25H2 security baseline includes new settings, updated default values, retired settings, and revised security guidance. Existing security baseline profiles don't automatically update to the new version.

To use the Windows 11, version 25H2 security baseline, Intune admins can [create a new baseline profile](../device-security/security-baselines/configure-baselines#create-a-profile-for-a-security-baseline) or [update an existing profile to the latest version](../device-security/security-baselines/configure-baselines#update-a-baseline-profile-to-the-latest-version).

The following two settings aren't included in this baseline release and will be added in a future baseline update. Each change will be communicated to customers when available:

- **Disable Internet Explorer 11 launch via COM automation** - This setting isn't included at release due to a known issue. The Windows client team is addressing the issue, and the setting will be added in a future baseline update.
- **Configure NetBIOS settings** - This setting is pending availability in the Settings Catalog and will be added to the baseline in a future update.

We recommend carefully reviewing the settings in the new baseline before moving from a previous baseline version, especially if existing profiles include customizations.

For a detailed breakdown of setting changes, see the Windows blog post [Windows 11, version 25H2 security baseline](https://techcommunity.microsoft.com/blog/microsoft-security-baselines/windows-11-version-25h2-security-baseline/4456231).

To view the default configuration of the Intune baseline for Windows 11, version 25H2, see [Windows MDM baseline settings](../device-security/security-baselines/ref-windows-mdm-settings?pivots=mdm-25h2#security-baseline-for-windows-version-25h2).

Applies to:

- Windows 11

#### Hotpatching default enablement in Windows Autopatch

Starting with the May 2026 Windows security update, hotpatch updates are enabled by default for all eligible devices managed through Windows Autopatch. Hotpatch updates install faster and require fewer restarts, helping devices get secure sooner.

If your organization isn't ready for this change, you can opt out using either of the following options:

- **Tenant-level setting**: Opt out of hotpatch updates across all eligible devices in your tenant. This option becomes available April 1, 2026 in the Intune admin center.
- **Quality update policy**: Control hotpatch behavior for a specific group of devices. Hotpatch settings configured in a quality update policy override the tenant-level setting for devices assigned to that policy.

Key dates:

- **April 1, 2026**: Tenant-level opt-out setting available in the Intune admin center.
- **May 2026 security update**: Hotpatch updates enabled by default.

For more information, see the Windows IT Pro Blog (https://aka.ms/HotpatchByDefault).

### Intune apps

#### Newly available protected apps for Intune

The following protected apps are now available for Microsoft Intune:

- PerfectServe Clinical Collab by PerfectServe
- Synigo Pulse by Synigo B.V.
- DeepL for Intune by DeepL SE
- Foxit PDF Editor by Foxit Software Inc.
- EasyPlant QC Inspections by Technip Energies (Android)

For more information about protected apps, see [Microsoft Intune protected apps](../app-management/ref-protected-apps).

### Monitor and troubleshooting

#### Support Assistant access expanded to all authenticated users

All authenticated users can now access Support Assistant in the Intune admin center to find solutions and troubleshooting guidance. Creating and managing support tickets still requires a Microsoft Entra role that includes the *microsoft.office365.supportTickets* permission. For more information, see [How to get support in the Microsoft Intune admin center](../fundamentals/it-pro-support/get-support-admin-center).

#### Support for system proxy settings in endpoint analytics and Advanced Analytics

Devices configured with system-level (WinHTTP) proxy settings can now send telemetry to endpoint analytics and Advanced Analytics, enabling more comprehensive reporting. Endpoint Privilege Management (EPM) will also include elevation usage data from these devices.

No admin action is required. If endpoint analytics or EPM is enabled for a device, telemetry and events will automatically appear in the User Experience (Device blade), endpoint Analytics reports, and EPM.

For more details about displaying advanced proxy settings, see [Netsh.exe commands](/en-us/windows/win32/winhttp/netsh-exe-commands#show-advproxy).

Applies to:

- Windows

#### Improvements to device query for multiple devices

Device query for multiple devices now includes new capabilities to help you work with query results more efficiently.

You can use a search text box to search across all resulting rows of a query, use column headers to add filters for specific values, and create Microsoft Entra security groups directly from a query's device results.

For more information, see [Device query for multiple devices](../advanced-analytics/device-query-multiple-devices).

### Role-based access control

#### Scoped permissions for Role-based access control (preview)

Intune now includes an opt-in preview to enable **Scoped permissions**, making your role-based access control (RBAC) configuration more precise. Enabling Scoped permissions is a one-time choice that can't be undone. In the future, this will become the default behavior for all tenants.

Previously, when an admin had multiple role assignments using different scope tags for the same permission category, Intune merged permissions across those assignments, which could unintentionally grant broader access than intended. With Scoped permissions enabled, each role assignment's permissions apply only within its own scope tag context, so admins receive exactly the access you intended.

To help you prepare before enabling this change, Intune includes a new **Permissions Assessment Report**. The report details your tenant's current permissions and shows how they will change after enabling Scoped permissions. You can rerun the report as often as needed, adjust role assignments, and communicate any changes to affected admins before opting in.

For more information about the current default behavior, the Scoped permissions opt-in preview, and the new report, see [Permission behavior across role assignments](../fundamentals/role-based-access-control/scope-tags#permission-behavior-across-role-assignments).

## Week of March 24, 2026

### Tenant administration

#### Guided scenarios being removed from the Intune admin center

All guided scenarios except Windows 365 Boot are removed from the Microsoft Intune admin center. You can no longer access the guided scenario wizards, but any Intune objects previously created by these wizards remain available and manageable. The Windows 365 Boot guided scenario remains available from the Windows 365 overview page in the Intune admin center. No action is required.

For alternative step-by-step guidance, see the following resources:

- [Microsoft Intune documentation](https://go.microsoft.com/fwlink/?linkid=2310495)
- [Intune prescriptive guides](https://go.microsoft.com/fwlink/?linkid=2300666)
- Intune administration guides: https://m365accelerator.microsoft.com/intune
    - [Securing apps for mobile | Android](https://m365accelerator.microsoft.com/intune/manage-and-secure-apps-for-android)
    - [Securing apps for mobile | iOS](https://m365accelerator.microsoft.com/intune/manage-and-secure-apps-for-ios)
    - [Configuring Intune and Configuration Manager to co-manage devices](https://m365accelerator.microsoft.com/intune/microsoft-intune-and-configuration-manager-co-management-setup-guide)
    - [Manage and secure devices for Windows](https://m365accelerator.microsoft.com/intune/windows-device-management)
- [Microsoft Copilot in Intune](../copilot/)

Applies to:

- Windows 10/11
- iOS/iPadOS
- Android

For previous months, see the [What's new archive](archive).

## Notices

These notices provide important information that can help you prepare for future Intune changes and features.

### Plan for Change: Intune is moving to support iOS/iPadOS 18 and later

Later in calendar year 2026, we expect iOS 27 and iPadOS 27 to be released by Apple. Microsoft Intune, including the Intune Company Portal and Intune app protection policies (APP, also known as MAM), requires [iOS 17/iPadOS 17 and higher](../fundamentals/ref-supported-platforms) shortly after the iOS/iPadOS 27 release.

#### How does this change affect you or your users?

If you're managing iOS/iPadOS devices, you might have devices that won't be able to upgrade to the minimum supported version (iOS 18/iPadOS 18).

Given that Microsoft 365 mobile apps are supported on iOS 18/iPadOS 18 and higher, this change might not affect you. You likely already upgraded your OS or devices.

To check which devices support iOS 18 or iPadOS 18 (if applicable), see the following Apple documentation:

- [Supported iPhone models](https://support.apple.com/guide/iphone/iphone-models-compatible-with-ios-18-iphe3fa5df43/18.0/ios/18.0)
- [Supported iPad models](https://support.apple.com/guide/ipad/ipad-models-compatible-with-ipados-18-ipad213a25b2/18.0/ipados/18.0)

Note

Userless iOS and iPadOS devices enrolled through Automated Device Enrollment (ADE) have a slightly nuanced support statement due to their shared usage. The minimum supported OS version changes to iOS 18/iPadOS 18 while the allowed OS version changes to iOS 16/iPadOS 16 and later. For more information, see [this statement about ADE Userless support](https://aka.ms/ADE_userless_support).

#### How can you prepare?

Check your Intune reporting to see what devices or users might be affected. For devices with mobile device management (MDM), go to **Devices** &gt; **All devices** and filter by OS. For devices with app protection policies, go to **Apps** &gt; **Monitor** &gt; **App protection status** and use the *Platform* and *Platform version* columns to filter.

To manage the supported OS version in your organization, you can use Microsoft Intune controls for both MDM and APP. For more information, see [Manage operating system versions with Intune](../device-updates/manage-os-versions).

### Plan for change: Intune is moving to support macOS 15 and higher later this year

Later in calendar year 2026, we expect macOS Golden Gate 27 to be released by Apple. Microsoft Intune, the Company Portal app, and the Intune mobile device management agent support macOS 15 and later. Since the Company Portal app for iOS and macOS are a unified app, this change will occur shortly after the release of macOS 27. This change doesn't affect existing enrolled devices.

#### How does this change affect you or your users?

This change only affects you if you currently manage, or plan to manage, macOS devices with Intune. If your users have likely already upgraded their macOS devices, then this change might not affect you. For a list of supported devices, refer to [macOS Sequoia is compatible with these computers](https://support.apple.com/120282).

Note

Devices that are currently enrolled on macOS 14.x or below will continue to remain enrolled even when those versions are no longer supported. New devices are unable to enroll if they're running macOS 14.x or below.

#### How can you prepare?

Check your Intune reporting to see what devices or users might be affected. Go to **Devices** &gt; **All devices** and filter by macOS. You can add more columns to help identify who in your organization has devices running macOS 14.x or earlier. Ask your users to upgrade their devices to a supported OS version.

### Warning notifications for iOS apps running unsupported SDK versions

We're continuing improvements to the Microsoft Intune mobile application management (MAM) service to ensure applications remain secure, reliable, and aligned with the latest platform capabilities.

Starting in late June 2026, users opening iOS apps built with an Intune MAM SDK version earlier than 20.8.0 will see a warning message recommending they update to a supported app version for the best experience and continued compatibility.

#### How does this change affect you or your users?

Users running iOS apps with an Intune MAM SDK version lower than 20.8.0 will see a warning message. The warning will appear in iOS apps such as Microsoft Teams, Outlook, Edge and OneDrive. Note that this notification is non-blocking, users can dismiss the message and continue using the app.

#### How can you prepare?

Notify users to update to the latest versions of Microsoft and third-party apps as soon as possible. The latest versions are available in Apple's [App store](https://www.apple.com/app-store/). For example, you can find the latest version of Microsoft Teams [here](https://apps.apple.com/app/microsoft-teams/id1113153706) and Microsoft Outlook [here](https://apps.apple.com/app/microsoft-outlook/id951937596).

If applicable, notify your helpdesk and support teams about the warning message. Additionally, as an IT admin you can use [Conditional Launch](../app-management/protection/ref-settings-ios#conditional-launch) settings to block unsupported app or SDK versions that are still in use:

- The **Min SDK version** setting to block users if the app is using Intune SDK for iOS older than 20.8.0.
- The **Min app version** setting to warn or block users on older Microsoft apps. Note, this setting must be in a policy targeted to only the targeted app.

### Update to the latest Intune Company Portal for Android, Intune App SDK for iOS, and Intune App Wrapper for iOS

Starting **January 19, 2026**, or soon after, we're making updates to improve the Intune mobile application management (MAM) service. To stay secure and run smoothly, this update will require iOS wrapped apps, iOS SDK integrated apps, and the Intune Company Portal for Android to be updated to the latest versions.

Important

If you don't update to the latest versions, users will be blocked from launching your app.

The way Android updates, once one Microsoft application with the updated SDK is on the device and the Company Portal is updated to the latest version, Android apps will update, so this message is focused on iOS SDK/app wrapper updates. We recommend to always update your Android and iOS apps to the latest SDK or app wrapper to ensure that your app continues to run smoothly. Review the following GitHub announcements for more details on the specific effect:

- SDK for iOS: [Action Required: Update the MAM SDK in your application to avoid end user impact - microsoftconnect/ms-intune-app-sdk-ios Discussion #598 | GitHub](https://github.com/microsoftconnect/ms-intune-app-sdk-ios/discussions/598)
- Wrapper for iOS: [Action Required: Wrap your application with version 20.8.1+ to avoid end user impact - microsoftconnect/intune-app-wrapping-tool-ios Discussion #143 | GitHub](https://github.com/microsoftconnect/intune-app-wrapping-tool-ios/discussions/143)

If you have questions, leave a comment on the applicable GitHub announcement.

#### How does this change affect you or your users?

If your users haven't updated to the latest Microsoft or third-party app protection supported apps, they'll be blocked from launching their apps. If you have iOS line-of-business (LOB) applications that are using the Intune wrapper or Intune SDK, you must be on Wrapper/SDK version **20.8.0** or later for apps compiled with Xcode 16 and version **21.1.0** or later for apps compiled with Xcode 26 to avoid your users being blocked.

#### How can you prepare?

Plan to make the following changes before **January 19, 2026**:

- For apps using the Intune App SDK, you must update to the new version of the Intune App SDK for iOS:

    - For apps built with XCode 16 use [v20.8.0 - Release 20.8.0 - microsoftconnect/ms-intune-app-sdk-ios | GitHub](https://github.com/microsoftconnect/ms-intune-app-sdk-ios/releases/tag/20.8.0)
    - For apps built with XCode 26 use [v21.1.0 - Release 21.1.0 - microsoftconnect/ms-intune-app-sdk-ios | GitHub](https://github.com/microsoftconnect/ms-intune-app-sdk-ios/releases/tag/21.1.0)
- For apps using the wrapper, you must update to the new version of the Intune App Wrapping Tool for iOS:

    - For apps built with XCode 16 use [v20.8.1 - Release 20.8.1 - microsoftconnect/intune-app-wrapping-tool-ios | GitHub](https://github.com/microsoftconnect/intune-app-wrapping-tool-ios/releases/tag/20.8.1)
    - For apps built with XCode 26 use [v21.1.0 - Release 21.1.0 - microsoftconnect/intune-app-wrapping-tool-ios | GitHub](https://github.com/microsoftconnect/intune-app-wrapping-tool-ios/releases/tag/21.1.0)
- For tenants with policies targeted to iOS apps:

    - Notify your users that they need to upgrade to the latest version of the Microsoft apps. You can find the latest version of the apps in the [App store](https://www.apple.com/app-store/). For example, you can find the latest version of Microsoft Teams [here](https://apps.apple.com/app/microsoft-teams/id1113153706) and Microsoft Outlook [here](https://apps.apple.com/app/microsoft-outlook/id951937596).
    - Additionally, you can enable the following [conditional launch](../app-management/protection/ref-settings-ios#conditional-launch)settings:
        - The **Min SDK version** setting to block users if the app is using Intune SDK for iOS older than 20.8.0.
        - The **Min app version** setting to warn users on older Microsoft apps. Note, this setting must be in a policy targeted to only the targeted app.
- For tenants with policies targeted to Android apps:

    - Notify your users that they need to upgrade to the latest version (v5.0.6726.0) of the [Intune Company Portal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) app.
    - Additionally, you can enable the following [conditional launch](../app-management/protection/ref-settings-ios#conditional-launch) device condition setting:

        - The **Min Company Portal version** setting to warn users using a Company Portal app version older than 5.0.6726.0.

Note

Use Conditional Access policy to ensure that only apps with app protection policies can access corporate resources. For more information, see the [Require approved client apps or app protection policy with mobile devices](/en-us/entra/identity/conditional-access/policy-all-users-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices) on creating Conditional Access policies.

### Update firewall configurations to include new Intune network endpoints

As part of Microsoft's ongoing [Secure Future Initiative (SFI)](https://www.microsoft.com/trust-center/security/secure-future-initiative), starting on or shortly after **December 2, 2025**, the network service endpoints for Microsoft Intune will also use the Azure Front Door IP addresses. This improvement supports better alignment with modern security practices and over time will make it easier for organizations using multiple Microsoft products to manage and maintain their firewall configurations. As a result, customers might be required to add these network (firewall) configurations in third-party applications to enable proper function of Intune device and app management. This change will affect customers using a firewall allowlist that allows outbound traffic based on IP addresses or Azure service tags.

Don't remove any existing network endpoints required for Microsoft Intune. More network endpoints are documented as part of the Azure Front Door and service tags information referenced in the following files:

- Public clouds: Download Azure IP Ranges and Service Tags – [Public Cloud from Official Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=56519)
- Government clouds: Download Azure IP Ranges and Service Tags – [US Government Cloud from Official Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=57063)

The other ranges are in the JSON files linked above and can be found by searching for "AzureFrontDoor.MicrosoftSecurity".

#### How does this change affect you or your users?

If you've configured an outbound traffic policy for Intune IP address ranges or Azure service tags for your firewalls, routers, proxy servers, client-based firewalls, VPN, or network security groups, you'll need to update them to include the new Azure Front Door ranges with the "AzureFrontDoor.MicrosoftSecurity" tag.

Intune requires internet access for devices under Intune management, whether for mobile device management or mobile application management. If your outbound traffic policy doesn't include the new Azure Front Door IP address ranges, users can face sign-in issues, devices might lose connectivity with Intune, and access to apps like the Intune Company Portal or the apps protected by app protection policies could be disrupted.

#### How can you prepare?

Ensure that your firewall rules are updated and added to your firewall's allowlist with the other IP addresses documented under Azure Front Door by **December 2, 2025**.

Alternatively, you can add the `AzureFrontDoor.MicrosoftSecurity` service tag to your firewall rules to allow outbound traffic on port 443 for the addresses in the tag.

If you aren't the IT admin who can make this change, notify your networking team. If you're responsible for configuring internet traffic, see the following documentation for more details:

- [Azure Front Door](/en-us/azure/frontdoor/origin-security?tabs=app-service-functions&amp;pivots=front-door-classic)
- [Azure service tags](/en-us/azure/virtual-network/service-tags-overview)
- [Intune network endpoints](../fundamentals/endpoints#intune-core-service)
- [US government network endpoints for Intune](../fundamentals/endpoints-us-government)

If you have a helpdesk, inform them about this upcoming change.

### Update to support statement for Windows 10 in Intune

Windows 10 has reached end of support on **October 14, 2025**. Windows 10 no longer receives quality or feature updates. Security updates are only available to commercial customers who have enrolled devices into the Extended Security Updates (ESU) program. For more details, review the following additional information.

#### How does this change affect you or your users?

Microsoft Intune continues to maintain core management functionality for Windows 10, including:

- Continuity of device management.
- Support for updates and migration workflows to Windows 11.
- Ability for ESU customers to deploy Windows security updates and maintain secure patch levels.

The final release of Windows 10 (version 22H2) is designated as an "allowed" version in Intune. While updates and new features are not available, devices running this version can still enroll in Intune and use eligible features, but functionality is not guaranteed and can vary.

#### How can you prepare?

Use the **All devices** report in the Intune admin center to identify devices still running Windows 10 and upgrade eligible devices to Windows 11.

If devices cannot be upgraded in time, consider enrolling eligible devices in the Windows 10 ESU program to continue receiving critical security updates.

#### Additional information

- [Stay secure with Windows 11, Copilot+ PCs, and Windows 365 before support ends for Windows 10](https://blogs.windows.com/windowsexperience/2025/06/24/stay-secure-with-windows-11-copilot-pcs-and-windows-365-before-support-ends-for-windows-10/)
- [Windows 10 reaching end of support](/en-us/lifecycle/announcements/windows-10-end-of-support)
- [Enable Extended Security Updates (ESU)](/en-us/windows/whats-new/enable-extended-security-updates)
- [Windows 10 release information](/en-us/windows/release-health/release-information)
- [Windows 11 release information](/en-us/windows/release-health/windows11-release-information)
- [Lifecycle FAQ - Windows](/en-us/lifecycle/faq/windows)

### Plan for Change: Google Play strong integrity definition update for Android 13 or above

Google recently updated the definition of "Strong Integrity" for devices running Android 13 or above, requiring hardware-backed security signals and recent security updates. For more information, see the [Android Developers Blog: Making the Play Integrity API faster, more resilient, and more private](https://android-developers.googleblog.com/2024/12/making-play-integrity-api-faster-resilient-private.html). Microsoft Intune will enforce this change by **October 31, 2026**. Until then, we've adjusted app protection policy and compliance policy behavior to align with Google's recommended backward compatibility guidance to minimize disruption as detailed in [Improved verdicts in Android 13 and later devices | Google Play | Android Developers](https://developer.android.com/google/play/integrity/improvements#how_can_i_use_the_old_meets-strong-integrity_label_definition_across_all_android_sdk_versions).

#### How does this change affect you or your users?

If you have targeted users with app protection policies and/or compliance policies that are using devices running Android 13 or above without a security update in the past 12 months, these devices will no longer meet the "Strong Integrity" standard.

**User impact** - For users running devices on Android 13 or above after this change:

- Devices without the latest security updates might be downgraded from "Strong Integrity" to "Device Integrity", which could result in conditional launch blocks for affected devices.
- Devices without the latest security updates might see their devices become noncompliant in the Intune Company Portal app and could lose access to company resources based on your organization's Conditional Access policies.

Devices running Android versions 12 or below aren't affected by this change.

#### How can you prepare?

Review and update your policies as needed. Ensure users with devices running Android 13 or above are receiving timely security updates. You can use the [app protection status report](../app-management/protection/monitor-policies#view-the-app-protection-status-report) to monitor the date of the last Android Security Patch received by the device and notify users to update as needed. The following admin options are available to help warn or block users:

- For app protection policies, configure the **Min OS version** and **Min patch version** conditional launch settings. For more details, review [Android app protection policy settings in Microsoft Intune | Microsoft Learn](../app-management/protection/ref-settings-android#conditional-launch)
- For compliance policies, configure the **Minimum security patch level** compliance setting. For more details, review: [Device compliance settings for Android Enterprise in Intune](../device-security/compliance/ref-android-enterprise-settings)

### Plan for Change: New Intune connector for deploying Microsoft Entra hybrid joined devices using Windows Autopilot

As part of Microsoft's Secure Future Initiative, we recently released an update to the Intune Connector for Active Directory to use a Managed Service Account instead of a local SYSTEM account for deploying Microsoft Entra hybrid joined devices with Windows Autopilot. The new connector aims to enhance security by reducing unnecessary privileges and permissions associated with the local SYSTEM account.

Important

At the end of June 2025, we'll remove the old connector that uses the local SYSTEM account. At that point, we will stop accepting enrollments from the old connector. For more information, see the [Microsoft Intune Connector for Active Directory security update](https://aka.ms/Intune-connector-blog) blog.

#### How does this change affect you or your users?

If you have Microsoft Entra hybrid joined devices using Windows Autopilot, you need to transition to the new connector to continue deploying and managing devices effectively. If you don't update to the new connector, you won't be able to enroll new devices using the old connector.

#### How can you prepare?

Update your environment to the new connector by following these steps:

1. Download and install the new connector in the Intune admin center.
2. Sign in to set up the Managed Service Account (MSA).
3. Update the ODJConnectorEnrollmentWizard.exe.config file to include the required Organizational Units (OUs) for domain join.

For more detailed instructions, review: [Microsoft Intune Connector for Active Directory security update](https://aka.ms/Intune-connector-blog) and [Deploy Microsoft Entra hybrid joined devices by using Intune and Windows Autopilot](/en-us/autopilot/windows-autopilot-hybrid).

### Plan for Change: New settings for Apple AI features; Genmojis, Writing tools, Screen capture

Today, the Apple AI features for Genmojis, Writing tools, and screen capture are blocked when the app protection policy (APP) "Send Org data to other apps" setting is configured to a value other than "All apps". For more details on the current configuration, app requirements, and the list of current Apple AI controls review the blog: [Microsoft Intune support for Apple Intelligence](https://techcommunity.microsoft.com/blog/intunecustomersuccess/microsoft-intune-support-for-apple-intelligence/4254037)

In an upcoming release, Intune app protection policies have new standalone settings for blocking screen capture, Genmojis, and Writing tools. These standalone settings are supported by apps that have updated to version 19.7.12 or later for Xcode 15 and 20.4.0 or later for Xcode 16 of the Intune App SDK and App Wrapping Tool.

#### How does this change affect you or your users?

If you configured the APP "Send Org data to other apps" setting to a value other than "All apps", then the new "Genmoji", "Writing Tools" and "Screen capture" settings are set to **Block** in your app protection policy to prevent changes to your current user experience.

Note

If you configured an app configuration policy (ACP) to allow for screen capture, it overrides the APP setting. We recommend updating the new APP setting to **Allow** and removing the ACP setting. For more information about the screen capture control, review [iOS/iPadOS app protection policy settings | Microsoft Learn](../app-management/protection/ref-settings-ios#data-protection).

#### How can you prepare?

Review and update your app protection policies if you'd like more granular controls for blocking or allowing specific AI features. (**Apps** &gt; **Protection** &gt; *select a policy* &gt; **Properties** &gt; **Basics** &gt; **Apps** &gt; **Data protection**)

### Plan for change: User alerts on iOS for when screen capture actions are blocked

In an upcoming version (20.3.0) of the Intune App SDK and Intune App Wrapping Tool for iOS, support is added to alert users when a screen capture action (including recording and mirroring) is detected in a managed app. The alert is only visible to users if you have configured an app protection policy (APP) to block screen capture.

#### How does this change affect you or your users?

If APP has been configured to block screen capturing, users see an alert indicating that screen capture actions are blocked by their organization when they attempt to screenshot, screen record, or screen mirror.

For apps that have updated to the latest Intune App SDK or Intune App Wrapping Tool versions, screen capture is blocked if you configured "Send Org data to other apps" to a value other than "All apps". To allow screen capture for your iOS/iPadOS devices, configure the Managed apps app configuration policy setting "com.microsoft.intune.mam.screencapturecontrol" to **Disabled**.

#### How can you prepare?

Update your IT admin documentation and notify your helpdesk or users as needed. You can learn more about blocking screen capture in the blog: [New block screen capture for iOS/iPadOS MAM protected apps](https://aka.ms/Intune/iOS-screen-capture)

### Plan for Change: Blocking screen capture in the latest Intune App SDK for iOS and Intune App Wrapping Tool for iOS

We recently released updated versions of the Intune App SDK and the Intune App Wrapping Tool. Included in these releases (v19.7.5+ for Xcode 15 and v20.2.0+ for Xcode 16) is the support for blocking screen capture, Genmojis, and writing tools in response to the new AI features in iOS/iPadOS 18.2.

#### How does this change affect you or your users?

For apps that have updated to the latest Intune App SDK or Intune App Wrapping Tool versions screen capture will be blocked if you configured "Send Org data to other apps" to a value other than "All apps". To allow screen capture for your iOS/iPadOS devices, configure the [Managed apps app configuration policy](../app-management/configuration/configure-managed-apps) setting "com.microsoft.intune.mam.screencapturecontrol" to **Disabled**.

#### How can you prepare?

Review your app protection policies and if needed, create a [Managed apps app configuration policy](../app-management/configuration/configure-managed-apps) to allow screen capture by configuring the above setting *(Apps &gt; App configuration policies &gt; Create &gt; Managed apps &gt; Step 3 'Settings' under General configuration)*. For more information review, [iOS app protection policy settings – Data protection](../app-management/protection/ref-settings-ios#data-protection) and [App configuration policies - Managed apps](../app-management/configuration/overview#managed-apps).

### Plan for Change: Implement strong mapping for SCEP and PKCS certificates

With the May 10, 2022, Windows update ([KB5014754](https://support.microsoft.com/topic/kb5014754-certificate-based-authentication-changes-on-windows-domain-controllers-ad2c23b0-15d8-4340-a468-4d4f3b188f16)), changes were made to the Active Directory Kerberos Key Distribution (KDC) behavior in Windows Server 2008 and later versions to mitigate elevation of privilege vulnerabilities associated with certificate spoofing. Windows enforces these changes on **February 11, 2025**.

To prepare for this change, Intune has released the ability to include the security identifier to strongly map SCEP and PKCS certificates. For more information, review the blog: [Support tip: Implementing strong mapping in Microsoft Intune certificates](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-implementing-strong-mapping-in-microsoft-intune-certificates/4053376).

#### How does this change affect you or your users?

These changes will affect SCEP and PKCS certificates delivered by Intune for Microsoft Entra hybrid joined users or devices. If a certificate can't be strongly mapped, authentication will be denied. To enable strong mapping:

- SCEP certificates: Add the security identifier to your SCEP profile. We strongly recommend testing with a small group of devices and then slowly rollout updated certificates to minimize disruptions to your users.
- PKCS certificates: Update to the latest version of the Certificate Connector, change the registry key to enable the security identifier, and then restart the connector service. **Important:** Before you modify the registry key, review how to change the registry key and how to back up and restore the registry.

For detailed steps and more guidance, review the [Support tip: Implementing strong mapping in Microsoft Intune certificates](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-implementing-strong-mapping-in-microsoft-intune-certificates/4053376) blog.

#### How can you prepare?

If you use SCEP or PKCS certificates for Microsoft Entra Hybrid joined users or devices, you'll need to take action before February 11, 2025 to either:

- **(Recommended)** Enable strong mapping by reviewing the steps described in the blog: [Support tip: Implementing strong mapping in Microsoft Intune certificates](https://techcommunity.microsoft.com/blog/intunecustomersuccess/support-tip-implementing-strong-mapping-in-microsoft-intune-certificates/4053376)
- Alternatively, if all certificates can't be renewed before February 11, 2025, with the SID included, enable Compatibility mode by adjusting the registry settings as described in [KB5014754](https://support.microsoft.com/topic/kb5014754-certificate-based-authentication-changes-on-windows-domain-controllers-ad2c23b0-15d8-4340-a468-4d4f3b188f16). Compatibility mode is valid until September 2025.

### Update to the latest Intune App SDK and Intune App Wrapper for Android 15 support

We've recently released new versions of the Intune App SDK and Intune App Wrapping Tool for Android to support Android 15. We recommend upgrading your app to the latest SDK or wrapper versions to ensure applications stay secure and run smoothly.

#### How does this change affect you or your users?

If you have applications using the Intune App SDK or Intune App Wrapping Tool for Android, it's recommended that you update your app to the latest version to support Android 15.

#### How can you prepare?

If you choose to build apps targeting Android API 35, you need to adopt the new version of the Intune App SDK for Android (v11.0.0). If you wrapped your app and are targeting API 35, you need to use the new version of the App wrapper (v1.0.4549.6).

Note

As a reminder, while apps must update to the latest SDK if targeting Android 15, apps don't need to update the SDK to run on Android 15.

You should also plan to update your documentation or developer guidance if applicable to include this change in support for the SDK.

Here are the public repositories:

- [Intune App SDK for Android](https://github.com/microsoftconnect/ms-intune-app-sdk-android)
- [Intune App Wrapping Tool for Android](https://github.com/microsoftconnect/intune-app-wrapping-tool-android)

### Intune moving to support Android 10 and later for user-based management methods in October 2024

In October 2024, Intune supports Android 10 and later for user-based management methods, which includes:

- Android Enterprise personally owned work profile
- Android Enterprise corporate owned work profile
- Android Enterprise fully managed
- Android Open Source Project (AOSP) user-based
- Android device administrator
- App protection policies
- App configuration policies (ACP) for managed apps

Moving forward, we'll end support for one or two versions annually in October until we only support the latest four major versions of Android. You can learn more about this change by reading the blog: [Intune moving to support Android 10 and later for user-based management methods in October 2024](https://aka.ms/Intune/Android-10-support).

Note

Userless methods of Android device management (Dedicated and AOSP userless) and Microsoft Teams certified Android devices aren't affected by this change.

#### How does this change affect you or your users?

For user-based management methods (as listed above), Android devices running Android 9 or earlier won't be supported. For devices on unsupported Android OS versions:

- Intune technical support won't be provided.
- Intune won't make changes to address bugs or issues.
- New and existing features aren't guaranteed to work.

While Intune won't prevent enrollment or management of devices on unsupported Android OS versions, functionality isn't guaranteed, and use isn't recommended.

#### How can you prepare?

Notify your helpdesk, if applicable, about this updated support statement. The following admin options are available to help warn or block users:

- Configure a [conditional launch](../app-management/protection/ref-settings-android#conditional-launch) setting for APP with a minimum OS version requirement to warn and/or block users.
- Use a device compliance policy and set the action for noncompliance to send a message to users before marking them as noncompliant.
- Set [enrollment restrictions](../device-updates/manage-os-versions) to prevent enrollment on devices running older versions.

For more information, review: [Manage operating system versions with Microsoft Intune](../device-updates/manage-os-versions).