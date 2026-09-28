---
layout: Conceptual
title: Plan Education device grouping and targeting - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/grouping-and-targeting
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Plan how you'll group devices and users and target policies and applications.
ms.date: 2026-05-19T00:00:00.0000000Z
ms.topic: tutorial
zone_pivot_groups: platforms-windows-ios
locale: en-us
document_id: 072e07bd-5f50-b6d3-ed8e-1e70918ff339
document_version_independent_id: 072e07bd-5f50-b6d3-ed8e-1e70918ff339
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/grouping-and-targeting.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/grouping-and-targeting
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/grouping-and-targeting.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 06c254d1-2372-b71d-8e47-69628e572497
---

# Plan Education device grouping and targeting - Microsoft Intune | Microsoft Learn

![](../../../media/icons/16/check.svg) Organize devices and users

By organizing devices, students, classrooms, or learning curricula into groups, you can provide students with the resources and configurations they need.

## Grouping and targeting overview

Intune has four targeting methods. Organizations typically use a combination of these targeting methods.

| Grouping type | Description | Benefits | Disadvantages |
| --- | --- | --- | --- |
| Virtual groups | Created by Intune and allow you to target *All devices* and *All users* | Always up to date automatically | Can only be scoped using filters |
| Assigned groups | Used when you want to manually add users or devices to a group. | Easily manage unique group membership | Membership are manually maintained |
| Dynamic groups | Groups based on rules that you create to assign students or devices to groups. | Automates the membership maintenance of those groups | Can take between several minutes to 24 hours to update |
| Assignment filters \* Available in the Intune admin center. | Allows you to further narrow the assignment scope of a policy or app when targeting a group. | Intune quickly evaluates filters on each check-in | Needs to be applied to virtual, assigned, or dynamic groups |

If you use **Microsoft School Data Sync (SDS)**, two extra groups are precreated - **All teachers** and **All students**. SDS can also be configured to automatically create and maintain groups of students and teachers for each school.

Beyond the defaults, groups can be customized to suit various needs. For example, if you have both *Windows 10* and *Windows 11* devices in your school, you can create groups, such as *Windows 10 devices* and *Windows 11 devices*, to assign different policies and applications to them.

Note

- For more information on grouping and targeting options, see [Performance recommendations for Grouping, Targeting, and Filtering in large Microsoft Intune environments](../../../fundamentals/filters/performance-recommendations).
- For tips on avoiding policy conflicts, see [Avoid policy conflicts](policy-conflicts).
- On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

## Choose grouping methods

![](../../../media/icons/16/check.svg) Select the best option for grouping

The way you target configuration and apps can depend on many factors and the enrollment type.

::: zone pivot="windows"

The following table provides guidance about which Windows device grouping options to use based on the enrollment method and desired behavior.

| Enrollment type | Behavior | Best grouping options |
| --- | --- | --- |
| Windows Autopilot user driven | Fastest application during enrollment | ![](../../../media/icons/16/check.svg)*Device dynamic group* based on [a Windows Autopilot *Group Tag*](/en-us/autopilot/enrollment-autopilot), manufacturer or model ![](../../../media/icons/16/check.svg)*User dynamic group*![](../../../media/icons/16/check.svg) Assigned groups |
| Windows Autopilot self-deploying mode | Fastest application during enrollment | ![](../../../media/icons/16/check.svg)*Device dynamic group* based on [a Windows Autopilot *Group Tag*](/en-us/autopilot/enrollment-autopilot), manufacturer or model ![](../../../media/icons/16/check.svg) Assigned groups |
| All enrollment types | Fastest application during enrollment | ![](../../../media/icons/16/check.svg)*All devices* group![](../../../media/icons/16/check.svg)*All devices* group with a filter |
| All enrollment types | Applies after enrollment | ![](../../../media/icons/16/check.svg)*Device dynamic group* based on other attributes |

::: zone-end

::: zone pivot="ios"

The following table provides guidance about which iOS device grouping options to use based on the enrollment method and desired behavior.

| Enrollment type | Behavior | Best grouping options |
| --- | --- | --- |
| Automated device enrollment | Fastest application during enrollment | ![](../../../media/icons/16/check.svg)*All devices* group![](../../../media/icons/16/check.svg)*All devices* group with a filter |
| Automated device enrollment with user affinity | Fastest application during enrollment | ![](../../../media/icons/16/check.svg) Assigned or dynamic user groups |
| Company portal | Fastest application during enrollment | ![](../../../media/icons/16/check.svg) Assigned or dynamic user groups |
| All enrollment types | Applies after enrollment | ![](../../../media/icons/16/check.svg) Device dynamic group![](../../../media/icons/16/check.svg) Assigned device groups |

::: zone-end

Tip

For more information on grouping and targeting options, see [Performance recommendations for Grouping, Targeting, and Filtering in large Microsoft Intune environments](../../../fundamentals/filters/performance-recommendations).

For Intune-only device targeting based on properties like OS type, manufacturer, model, or device category, assignment filters are preferred over dynamic device groups. Filters evaluate at check-in without depending on group membership processing. Use dynamic groups when you need group membership for cross-workload scenarios (Conditional Access, licensing) or Autopilot profile assignment.

## Create groups and filters

![](../../../media/icons/16/check.svg) Create your organization groups

With your enrollment and grouping plan in place, you can create your groups.

# [Intune](#tab/intune)
- [Create groups in Microsoft Entra](/en-us/entra/fundamentals/how-to-manage-groups)
- [Use filters when assigning your apps, policies, and profiles in Microsoft Intune](../../../fundamentals/filters/overview)
- [Create or update a dynamic group in Microsoft Entra ID](/en-us/entra/fundamentals/concept-learn-about-groups)
- [Dynamic membership rules for groups in Microsoft Entra ID](/en-us/entra/fundamentals/concept-learn-about-groups)
- [Create simpler, more efficient rules for dynamic groups in Microsoft Entra ID](/en-us/entra/fundamentals/concept-learn-about-groups)

# [Intune for Education](#tab/intune-for-education)
- [Create groups in Intune for Education](/en-us/intune-education/create-groups)
- [Manually add or remove users and devices to an existing assigned group](/en-us/intune-education/edit-groups-intune-for-edu)
- [Edit dynamic group rules to accommodate for new devices, locations, or school years](/en-us/intune-education/edit-groups-intune-for-edu#edit-dynamic-group-rules)
- [Create Filters](../../../fundamentals/filters/overview)

---

## Example groups

![](../../../media/icons/16/check.svg) See examples of common grouping by enrollment type

This section includes targeting methods commonly seen in Education organizations.

::: zone pivot="windows"

### Windows Autopilot

When devices are imported into Windows Autopilot, they include the manufacturer and model of the device. A group tag can also be added to each device imported. The group tag can be used to create groups for targeting. Some customers use group tags to create groups for different autopilot profiles, to target different apps or profiles and also for assigning scope tags for role-based access control.

This table contains common groups used for devices that are enrolled using Windows Autopilot.

| Name | Type | Query |
| --- | --- | --- |
| All Windows devices | Dynamic membership rules | (device.deviceOSType -startsWith "Windows") |
| All Windows Autopilot devices | Dynamic membership rules | (device.devicePhysicalIDs -any \_ -startsWith "[ZTDId]") |
| All non-Windows Autopilot devices | Dynamic membership rules | (device.deviceOSType -startsWith "Windows") -and (device.deviceOwnership -eq "Company") -and -not(device.devicePhysicalIds -any (\_ -startsWith "[ZTDId]")) |
| All Windows Autopilot Student devices | Dynamic membership rules | (device.devicePhysicalIds -any (\_ -eq "[OrderID]:*`Student`*")) |

Note

The "All Windows Autopilot Student devices" group example is assuming the Windows Autopilot Group Tag is set to "Student". You could use another Group Tag and update the membership rule accordingly.

Note

- If you plan to create groups or filters based on enrollmentProfileName, make sure you create the enrollment profile with the name that matches the rules.
- If you use Windows Autopilot group tags to group devices, make sure the group tags added to device objects match the dynamic group rules.
- On Windows, apps and policies can also be targeted at user groups. However, most apps and policies on Windows devices are device-based. As a result, each user of a Windows device receives device-based apps and policies assigned to any previous user of the device - unless the new user has different configurations for settings previously applied.

### Provisioning packages

This table contains common groups used for devices that are enrolled using provisioning packages.

| Name | Type | Query |
| --- | --- | --- |
| All Windows devices | Dynamic membership rules | (device.deviceOSType -startsWith "Windows") |
| All Student devices | Dynamic membership rules | (device.displayName -startsWith "*`STU-`*") |

Note

The "All Student devices" group example is assuming the device name prefix in the provisioning package is set to "STU-". You could use another prefix and update the membership rule accordingly.

### All enrollment types

Filters can be used to further include or exclude devices from groups. For example:

- Devices running Windows 10 (osVersion *starts with* 10.0.1)
- Devices running Windows 11 (osVersion *starts with* 10.0.2)

::: zone-end

::: zone pivot="ios"

### Automated Device Enrollment

When devices are enrolled with Automated Device Enrollment, the devices are stamped with the enrollment profile name used during enrollment. Devices can be associated with different enrollment profiles in the Automated Device Enrollment token section under enrollment. Some customers use enrollment profile names to create groups or filters for different enrollment settings, to target different apps or profiles and also for assigning scope tags for role-based access control.

Here are examples of queries commonly used for dynamic security groups.

| Name | Type | Query |
| --- | --- | --- |
| All iOS devices | Dynamic membership rules | (device.deviceOSType -startsWith "iOS") |
| All *'use case'* devices | Dynamic membership rules | (device.enrollmentProfileName -eq "'*use case*'") |

To apply settings as quickly as possible during enrollment without waiting for dynamic group updates, some customers use a filter based on enrollmentProfileName and target configuration at the *All Devices* virtual group.

- Devices with a specific enrollmentProfileName (enrollmentProfileName *equals* *'use case*')

Note

If you plan to create groups or filters based on enrollmentProfileName make sure you create the enrollment profile with the name that matches the rules.

Warning

Each time an iOS device enrolls it creates a new Entra device object, so *assigned group* memberships aren't maintained after a device is reset.

::: zone-end