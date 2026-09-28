---
layout: FAQ
title: Windows Autopilot device preparation troubleshooting FAQ | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/troubleshooting-faq
summary: >
  <p><strong>Applies to:</strong></p>

  <ul>

  <li><a href="/windows/release-health/supported-versions-windows-client#windows-11-supported-versions">Windows 11</a>.</li>

  </ul>

  <p>This article provides troubleshooting for common Windows Autopilot device preparation issues.</p>
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Troubleshooting of common Windows Autopilot device preparation issues
ms.date: 2026-08-28T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: faq
locale: en-us
document_id: b8f2b988-a367-f387-b7f1-f6897cf6cacd
document_version_independent_id: b8f2b988-a367-f387-b7f1-f6897cf6cacd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/troubleshooting-faq.yml
site_name: Docs
depot_name: MSDN.autopilot
page_type: faq
toc_rel: ../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/troubleshooting-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/troubleshooting-faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: af4bbec9-fc0a-321f-fe16-ec4897d08d9a
---

# Windows Autopilot device preparation troubleshooting FAQ | Microsoft Learn

**Applies to:**

- [Windows 11](/en-us/windows/release-health/supported-versions-windows-client#windows-11-supported-versions).

This article provides troubleshooting for common Windows Autopilot device preparation issues.

## Export device information fails with "Export of device link information timed out. Please try again."

When exporting device information for [Windows Autopilot device association](tutorial/user-driven/entra-join-device-association#export-device-information-from-oobe) during the out-of-box experience (OOBE), the export might fail with the following message:

**`Export of device link information timed out. Please try again.`**

This issue can occur when the USB drive is formatted as FAT32 or contains both FAT32 and NTFS partitions. Use a separate USB drive that contains a single partition formatted with the NTFS file system, and then try the export again.

## Device isn't being added to the device group specified in the Windows Autopilot device preparation policy.

- Verify that **Intune Provisioning Client** is set as the owner for the device group specified in the Windows Autopilot device preparation policy. For more information, [Create an assigned device group](tutorial/user-driven/entra-join-device-group#create-an-assigned-device-group).
- Verify that the correct device group is specified in the Windows Autopilot device preparation policy. For more information, see [Create a Windows Autopilot device preparation policy](tutorial/user-driven/entra-join-autopilot-policy#create-user-driven-microsoft-entra-join-windows-autopilot-device-preparation-policy) and [Create an assigned device group](tutorial/user-driven/entra-join-device-group).
- Verify that **Microsoft Entra roles can be assigned to the group** setting in the device group is set to **No**. For more information, see [Create an assigned device group](tutorial/user-driven/entra-join-device-group#create-an-assigned-device-group).
- Verify that the admin creating the Windows Autopilot device preparation policy has the **Enrollment time device membership assignment** RBAC permission. For more information, see [Required RBAC permissions](requirements?tabs=rbac#required-rbac-permissions).

## Priority column in the list of device preparation policies is grayed out.

Device preparation policies in automatic mode don't honor priority as they're assigned directly within the Cloud PC provisioning policy.

## Windows Autopilot device preparation experience never launches during the out-of-box experience (OOBE).

- Verify that the minimum version of Windows is being used as documented in [Software requirements](requirements?tabs=software#software-requirements). This requirement includes that the minimum required update is installed before starting the device for the first time:

    - Verify with OEMs that devices shipped from the OEM have the minimum required update installed.
    - If installing Windows from installation media, verify that the media has the minimum required update installed. Updated Windows installation media with the latest cumulative update already installed is available in the [Microsoft Microsoft 365 admin center](https://admin.microsoft.com/adminportal/home#/subscriptions/vlnew).
- Windows Autopilot device preparation doesn't use the Enrollment Status Page (ESP). Since Windows Autopilot device preparation doesn't use the ESP, the ESP shouldn't display during a Windows Autopilot device preparation deployment. If the ESP displays during the deployment, then the device isn't running a Windows Autopilot device preparation deployment. Instead, the device might be:

    - A Windows Autopilot registered device.
    - A Windows Autopilot profile is assigned to the device.

    Verify that the device isn't registered as a Windows Autopilot device and that a Windows Autopilot profile isn't assigned to the device. Windows Autopilot profiles take precedence over Windows Autopilot device preparation policies.

    If a device needs to be removed as a Windows Autopilot device, see [Deregister a device](../registration-overview#deregister-a-device).
- Verify that the user signing into the device during OOBE is a member of the user group specified in the Windows Autopilot device preparation policy. For more information, see [Create a Windows Autopilot device preparation policy](tutorial/user-driven/entra-join-autopilot-policy#create-user-driven-microsoft-entra-join-windows-autopilot-device-preparation-policy) and [Create a user group](tutorial/user-driven/entra-join-user-group).
- Verify that a device group is selected in the Windows Autopilot device preparation policy. A Windows Autopilot device preparation policy can be created without selecting a device group. For more information, see [Create a Windows Autopilot device preparation policy](tutorial/user-driven/entra-join-autopilot-policy#create-user-driven-microsoft-entra-join-windows-autopilot-device-preparation-policy) and [Create an assigned device group](tutorial/user-driven/entra-join-device-group).
- If using corporate identifiers in Intune, make sure that a corporate identifier is added for the device. For more information, see [Add Windows corporate identifiers](/en-us/intune/intune-service/enrollment/corporate-identifiers-add#add-windows-corporate-identifiers).
- Verify that Windows automatic Intune enrollment is configured.
- Verify that users are allowed to join device to Microsoft Entra ID.

## Applications or PowerShell scripts aren't getting installed.

- If the applications or PowerShell scripts are showing **Skipped** in the details of the Windows Autopilot device preparation deployment report, verify that they're assigned to the device group specified in the Windows Autopilot device preparation policy. For more information, see [Windows Autopilot device preparation policy configuration settings](tutorial/user-driven/entra-join-autopilot-policy#configuration-settings) and [Create an assigned device group](tutorial/user-driven/entra-join-device-group).
- Verify that the application or PowerShell script is configured to install in the **System** context. During OOBE, applications are installed and PowerShell scripts run when no user is signed in. For this reason, they must be configured to install in the **System** context.

## Device security group isn't saving in Windows Autopilot device preparation policy.

This issue usually occurs if **Intune Provisioning Client** with AppID of **f1346770-5b25-470b-88bd-d5744ab7952c** isn't the owner of the device group specified in the Windows Autopilot device preparation policy. When the issue occurs, one of the following error messages might display when saving the Windows Autopilot device preparation policy:

- **`There was a problem with the device security group for <policy_name>. Check the group meets the requirements.`**
- **`Failed to update security group device preparation setting: Updating security group for device preparation setting <policy_name> failed. Something went wrong.`**

Additionally, **Device group** in the Windows Autopilot device preparation policy shows **0 groups assigned**.

To fix the issue, add the **Intune Provisioning Client** service principal with AppID of **f1346770-5b25-470b-88bd-d5744ab7952c** as the owner of the device security group specified in the Windows Autopilot device preparation policy. For more information, see [Create an assigned device group](tutorial/user-driven/entra-join-device-group#create-an-assigned-device-group).

## Unable to find Intune Provisioning Client with AppID of f1346770-5b25-470b-88bd-d5744ab7952c when trying to set the owner of the Windows Autopilot device preparation policy device group.

- In some tenants, the service principal might have the name of **Intune Autopilot ConfidentialClient** instead of **Intune Provisioning Client**. As long as the AppID of the service principal is **f1346770-5b25-470b-88bd-d5744ab7952c**, it's the correct service principal.
- If either **Intune Provisioning Client** or **Intune Autopilot ConfidentialClient** with AppID of **f1346770-5b25-470b-88bd-d5744ab7952c** doesn't exist in the tenant, it must be added via PowerShell commands. For more information, see [Adding the Intune Provisioning Client service principal](tutorial/user-driven/entra-join-device-group#adding-the-intune-provisioning-client-service-principal).

## Multiple Windows Autopilot device preparation policies exist and the device is getting the wrong policy.

If multiple Windows Autopilot device preparation policies are deployed to a user, the policy with the highest priority gets priority. Policy priorities are displayed at the **Home** &gt; **Enroll devices | Windows enrollment** &gt; **Device preparation policies** screen. The policy with the highest priority is higher in the list and has the smallest number under the **Priority** column. To change a policy's priority, move it in the list by dragging the policy within the list.