---
layout: Conceptual
title: Create a Windows Health Monitoring profile in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-health-monitoring-windows
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
description: Add a Windows Health Monitoring profile to collect endpoint analytics and software update events on Windows 10/11 devices in Microsoft Intune. Use this data to recommend software, review startup performance, and fix support issues.
ms.date: 2025-02-19T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: 
locale: en-us
document_id: 713dc0c9-a6a1-6a1d-6392-8a5835e76d02
document_version_independent_id: 713dc0c9-a6a1-6a1d-6392-8a5835e76d02
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-health-monitoring-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-health-monitoring-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-health-monitoring-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 1351d909-c7aa-6699-90f2-3dcbd2d7af64
---

# Create a Windows Health Monitoring profile in Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft can collect event data, and provide recommendations to improve performance on your Windows devices. [Endpoint analytics](../../endpoint-analytics/) analyzes this data, and can recommend software, help improve startup performance, and fix common support issues.

In Intune, you can create a Windows Health Monitoring device configuration profile to enable this data collection, and then deploy this profile to your devices.

To help optimize your Windows devices, use this profile as part of your mobile device management (MDM) solution.

This feature applies to:

- Windows devices enrolled in Intune

This article shows you how to create the profile, and enable the monitoring.

## Before you begin

- Endpoint Analytics has its own prerequisites. For more information, including enrollment requirements, see [Endpoint Analytics Overview](../../endpoint-analytics/).
- If you use co-management, then to use this profile, the Device Configuration workload must be in Intune. For more information on these features, go to [What is co-management?](../../configmgr/comanage/overview) and [Switch Configuration Manager workloads to Intune](../../configmgr/comanage/how-to-switch-workloads).
- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Windows health monitoring**.

    Note

    If you don't see **Windows health monitoring** in the list, then:

    1. Go to **Reports** &gt; **Endpoint Analytics** &gt; **Settings**.
    2. Select **Intune data collection policy**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your policies so you can easily identify them later. For example, a good profile name is **Windows devices: Windows Health Monitoring profile**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, configure the following settings:

    - **Health monitoring**: This setting turns on health monitoring to track events. Your options:

        - **Not configured**: Intune doesn't change or update this setting.
        - **Enable**: Event information is collected from the devices, and sent to Microsoft for analytics and insights.
        - **Disable**: Event information isn't collected from the devices.

        [DeviceHealthMonitoring/AllowDeviceHealthMonitoring CSP](/en-us/windows/client-management/mdm/policy-csp-devicehealthmonitoring#allowdevicehealthmonitoring)
    - **Scope**: Choose the event information you want collected and evaluated. Your option:

        - **Endpoint analytics**

        [DeviceHealthMonitoring/ConfigDeviceHealthMonitoringScope CSP](/en-us/windows/client-management/mdm/policy-csp-devicehealthmonitoring#configdevicehealthmonitoringscope)
8. Select **Next**.
9. In **Assignments**, select the devices or device groups that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
10. In **Applicability Rules**, use the **Rule**, **Property**, and **Value** options to define how this profile applies within assigned groups. Intune applies the profile to devices that meet the rules you enter. For more information about applicability rules, go to [Applicability rules](../create-device-profile#applicability-rules).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in, the policy is applied.