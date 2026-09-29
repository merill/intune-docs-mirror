---
layout: Conceptual
title: Manage devices with endpoint security in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/endpoint-security-devices
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: protect
description: Learn how Security Administrators can use the Endpoint Security node to view devices and manage them in Microsoft Intune.
ms.date: 2026-08-10T00:00:00.0000000Z
ms.topic: article
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.reviewer: mattcall
locale: en-us
document_id: 723b40be-25ec-4449-87d8-c4097da568ab
document_version_independent_id: 723b40be-25ec-4449-87d8-c4097da568ab
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/endpoint-security-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/endpoint-security-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/endpoint-security-devices.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: bac315df-8eab-6bf6-4103-fa17bb9db571
---

# Manage devices with endpoint security in Microsoft Intune - Microsoft Intune | Microsoft Learn

As a security administrator, use the *All devices* view in the Microsoft Intune admin center to review and manage your devices. The view displays a list of all your devices from your Microsoft Entra ID, including devices managed by:

- Intune
- Configuration Manager
- [Co-management](/en-us/configmgr/comanage/overview)*(by both Intune and Configuration Manager)*
- [Defender for Endpoint security settings management](microsoft-defender/security-settings-management)*(for devices that aren't enrolled with Intune)*

Devices can be in the cloud and from your on-premises infrastructure when integrated with your Microsoft Entra ID.

To find the view, open the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select **Endpoint security** &gt; **All devices**.

The initial *All devices* view displays your devices and includes key information about each:

- How the device is managed
- Compliance status
- Operating system details
- When the device last checked in
- And more

[![The all device view in the admin center.](media/endpoint-security-devices/all-device-view.png)](media/endpoint-security-devices/all-device-view.png#lightbox)

While viewing device details, you can select a device to drill-in for more information.

## Available details by management type

When viewing devices in the Microsoft Intune admin center, consider how the device is managed. The management source affects what information is presented in the admin center and which actions are available to manage the device.

Consider the following fields:

- **Managed by** – This column identifies how the device is managed. Managed by options include:

    - **MDM** – Intune manages these devices. Intune collects and reports the device's compliance data to the admin center.
    - **ConfigMgr** – These devices appear in the Microsoft Intune admin center when you use *tenant attach* to add the devices you manage with Configuration Manager. To be managed, the device must run the Configuration Manager client and be:

        - In a Workgroup (Microsoft Entra joined and otherwise)
        - Domain Joined
        - Microsoft Entra hybrid joined (joined to the AD and Microsoft Entra ID)

        Compliance status for devices that are managed by Configuration Manager isn't visible in the Microsoft Intune admin center.

        For more information, see [Enable tenant attach](/en-us/configmgr/tenant-attach/device-sync-actions) in the Configuration Manager documentation.
    - **MDM/ConfigMgr Agent** – These devices are under co-management between Intune and Configuration Manager.

        With co-management, you [choose different co-management workloads](/en-us/configmgr/comanage/how-to-switch-workloads) to determine which aspects are managed by Configuration Manager or by Intune. These choices affect which policies the device applies, and how compliance data is reported to the admin center.

        For example, you can use Intune to configure policies for Antivirus, Firewall, and Encryption. These policies are all considered policy for *Endpoint Protection*. To have a co-managed device use the Intune policies and not the Configuration Manager policies, set the co-management slider for Endpoint Protection to either *Intune* or *Pilot Intune*. If the slider is set to Configuration Manager, the device uses the policies and settings from Configuration Manager instead.
    - **MDE** – These devices aren't enrolled with Intune. Instead, they onboard to Defender for Endpoint and can process many of the [Intune endpoint security policies](microsoft-defender/security-settings-management#which-solution-should-i-use). Devices enrolled with security settings management appear both in the Intune admin center and in the Defender portal. In the admin center, the *Managed by* field displays MDE for these devices.
- **Compliance**: Compliance is evaluated against the compliance policies that are assigned to the device. The source of these policies and what information is in the console depends on how the device is managed; Intune, Configuration Manager, or co-management. For co-managed devices to report compliance, set the co-management slider for Device Compliance to *Intune* or to *Pilot Intune*.

    After compliance is reported to the admin center for a device, you can drill into the details to view more details. When a device isn't compliant, drill into its details to information about which policies aren't compliant. That information can help you investigate and help you bring the device into compliance.
- **Last check-in**: This field identifies the last time the device reported its status.

## Review a devices policy

To view information about the device configuration policies that apply to a device that's managed by MDM and Intune, see [**Security reports**](../device-management/reports/overview#security-reports). Both *endpoint security* and *security baseline* policies are device configuration policies.

To view the report, select a device and then select **Device configuration**, which is found below the *Monitor* category.

![View endpoint security policy details](media/endpoint-security-devices/view-policy-details.png)

Devices that are managed by Configuration Manager don't display policy details in the report. To view additional information for these devices, use the Configuration Manager console.

## Review your profiles for endpoint security policies

From the *Endpoint security* node in the admin center, you can select the *Summary* tab of a specific policy type to view, select, and then edit all the profiles you've created for that policy type. In this view:

- *Policy type* identifies the profile.
- *Platform* identifies the device platform.

In addition to the different endpoint security policy views, you can go to **Devices** &gt; *All devices* and below *Manage devices*, select **Configuration** to view and edit your endpoint security profiles for the macOS and Windows platforms along side your Device Configuration profiles. In this view, endpoint security policies are identified by their template type, like *Microsoft Defender Antivirus* in the *Policy type* column. See [Monitor device configuration policies in Microsoft Intune](../device-configuration/monitor-device-profile).

## Remote actions for devices

Remote actions are actions you can start or apply to a device from the Microsoft Intune admin center. When you view details for a device, you can access remote actions that apply to the device.

Remote actions display across the top of the devices *Overview* page. Actions that can't display because of limited space on your screen are available by selecting the ellipsis on the right side:

![View additional actions](media/endpoint-security-devices/view-additional-actions.png)

The remote actions that are available depend on how the device is managed:

- **Intune**: All [Intune remote actions](../device-management/actions/) that apply to the device platform are available.
- **Configuration Manager**: You can use the following Configuration Manager actions:

    - Sync Machine Policy
    - Sync User Policy
    - App Evaluation Cycle
- **Co-management**: You can access both Intune remote actions and Configuration Manager actions.
- **Defender for Endpoint security settings management** – These devices aren't managed by Intune and don't support remote actions.

Some of the Intune remote actions can help secure devices or safeguard data that might be on the device. With remote actions you can:

- Lock a device
- Reset a device
- Remove company data
- Scan for malware outside of a scheduled run
- Rotate BitLocker keys

The following Intune remote actions are of interest to the security admin, and are a subset of the [full list](../device-management/actions/#available-device-actions). Not all actions are available for all device platforms. The links go to content that provides in-depth details for each action.

- [Synchronize device](../device-management/actions/sync) – Have the device immediately check-in with Intune. When a device checks in, it receives any pending actions or policies that are assigned to it.
- [Restart](../device-management/actions/restart) – Force a Windows device to restart, within five minutes. The device owners aren't automatically notified of the restart and might lose work.
- [Quick Scan](../device-configuration/templates/ref-device-restrictions-windows) – Have Defender run a quick scan of the device for malware and then submit the results to Intune. A quick scan looks at common locations where there could be malware registered, such as registry keys and known Windows startup folders.
- [Full scan](../device-configuration/templates/ref-device-restrictions-windows) – Have Defender run a scan of the device for malware and then submit the results to Intune. A full scan looks at common locations where there could be malware registered, and also scans every file and folder on the device.
- Update Windows Defender security intelligence – Have the device update its malware definitions for Microsoft Defender Antivirus. This action doesn't start a scan.
- [BitLocker key rotation](../device-configuration/endpoint-security/encrypt-bitlocker-windows#rotate-bitlocker-recovery-keys) – Remotely rotate the BitLocker recovery key of a device that runs Windows 10 version 1909 or later, or Windows 11.

    Important

    On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

You can also use *bulk device actions* to manage some actions like *Retire* and *Wipe* for multiple devices at the same time. To learn more, see [bulk device actions](../device-management/actions/#bulk-device-actions).

![Select bulk actions](media/endpoint-security-devices/select-bulk-actions.png)

Options you manage for devices don't take effect until the device checks in with Intune.