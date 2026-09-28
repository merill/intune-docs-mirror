---
layout: Conceptual
title: Help Desk Troubleshooting Dashboard - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/it-pro-support/help-desk-operators
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Help desk staff use the troubleshooting pane to solve users' technical problems.
ms.date: 2024-06-14T00:00:00.0000000Z
ms.topic: troubleshooting
ms.reviewer: jlynn
locale: en-us
document_id: c654c29d-c564-689b-2cbc-420a86546820
document_version_independent_id: c654c29d-c564-689b-2cbc-420a86546820
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/it-pro-support/help-desk-operators.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/it-pro-support/help-desk-operators
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/it-pro-support/help-desk-operators.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 177ea2d1-02c5-b21b-82b2-86f5c3fa14cc
---

# Help Desk Troubleshooting Dashboard - Microsoft Intune | Microsoft Learn

The troubleshooting pane lets help desk operators and Intune administrators view user information to address user help requests. Organizations that include a help desk can assign the [Help desk operator role](../role-based-access-control/overview#built-in-roles) to a group of Intune users. The help desk operator role can use the **Troubleshooting + support** pane help end users.

The **Troubleshooting + support** pane provides three options:

- **Troubleshooting** to help determine any issues with **Assignments**, **App protection status**, and **Enrollment failures**.
- [Help and support](get-support-admin-center) to provide global technical, pre-sales, billing, and subscription support for device management cloud-based services related to Intune. For more information, see [Help and support](get-support-admin-center).

Details about the issue and suggested remediation steps can help administrators and help desk operators troubleshoot problems. Certain enrollment issues aren't captured and some errors might not have remediation suggestions.

Note

For steps on adding a help desk operator role, see [Role-based administration control (RBAC) with Intune](../role-based-access-control/overview)

When a user contacts support with a technical issue with Intune, the help desk operator enters and finds the user's name. Additionally, the help desk operator can filter by device if the user has multiple managed devices.

The **Troubleshooting** pane provides the following tabs for a selected user and allows you to quickly narrow the troubleshooting focus:

- **Summary** - Provides specific counts of issues related to policy, compliance, app protection, applications, devices, roles, and scopes.
- **Devices** - Provides details for devices, such as OS, OS Version, Intune compliance, and last check-in.
- **Groups** - Provides details for groups, such as membership type.
- **Policy** - Provides policy details, such as assignment, type, platform, and last modified.
- **Applications** - Provides app install status, assigned, platform, type, and last modified.
- **App protection policy** - Provides the name, platform, and enrollment details for app protection policies.
- **Updates** - Provides the name, platform, and update type.
- **Enrollment restrictions** - Provides the policy type, name, platform, and device limit.
- **Diagnostics** - Provides the device name or application, platform, created date, and diagnostic log.
- **ServiceNow incidents** - Provides a list of associated incidents for the selected user. For more information, go to [ServiceNow integration with Intune](../../device-management/tools/setup-servicenow).

## View user troubleshooting details

In the **Troubleshooting** pane provides specific details for each Intune end-user. User information can help you understand the current state of users and their devices.

1. Sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Troubleshooting + support** &gt; **Troubleshoot**.
3. Find and select a **User** by entering a display name or email.
4. If the user has multiple devices, filter by **Device**.
5. Review the provided information to help troubleshoot end-user issues.

## Areas of the troubleshooting dashboard

You can use the **Troubleshooting + support** pane to review a variety of managed user and device information.

[![Screenshot of the Intune troubleshooting dashboard.](media/help-desk-operators/help-desk-operators-01.png)](media/help-desk-operators/help-desk-operators-01.png#lightbox)

### Summary

The **Summary** tab provides overall details for the user who is managed by Intune.

| Column | Description |
| --- | --- |
| Policy | The status of the policies available for the user or device. |
| Compliance | The compliance status for the user or device. |
| App protection | App protection details. |
| Applications | The state of the applications for the user or device. |
| Devices | The status of the device(s) related to the user. |
| Role and scope | The role and scope for the user. |

### Devices

The **Devices** tab provides details for devices, such as OS, OS Version, Intune compliance, and last check-in.

| Column | Description |
| --- | --- |
| Name | The name of the device. |
| Managed by | Identifies how the device is managed. For more information, see [Available details by management type](../../device-management/manage-endpoint-security-devices#available-details-by-management-type). |
| Ownership | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Intune compliant | Identifies whether the device is compliant with Intune. Should be **Yes**. If **No** is shown, there may be an issue with compliance policies, or the device isn't connecting to the Intune service. For example, the device may be turned off, or may not have a network connection. Eventually, the device becomes non-compliant, possibly after 30 days. For more information, see [Use compliance policies to set rules for devices you manage with Intune](../../device-security/compliance/overview). |
| Microsoft Entra compliant | Identifies whether the device is compliant with Microsoft Entra ID. Should be **Yes**. If **No** is shown, there may be an issue with compliance policies, or the device isn't connecting to the Intune service. For example, the device may be turned off, or may not have a network connection. Eventually, the device becomes non-compliant, possibly after 30 days. For more information, see [Use compliance policies to set rules for devices you manage with Intune](../../device-security/compliance/overview). |
| App lifecycle status | Denotes whether an app install failure or success has occurred on the individual device. |
| OS | The Operating System installed on the device. |
| OS version | The Operating System version number of the device. |
| Last check-in | The timestamp of the last time the device checked in. |

### Groups

The **Groups** tab provides the group membership of all Microsoft Entra groups for a specific managed device. For related information, see [Device group membership report](../../device-management/reports/overview#device-group-membership-report-organizational).

| Column | Description |
| --- | --- |
| Name | The name of the group. |
| Object ID | The Object ID is used by Microsoft Entra ID. Intune commonly refers to them as Group ID. |
| Membership type | Provides how you assign and add users. **Assigned** denotes you manually assign users or devices to the group, and manually remove users or devices. **Dynamic User** denotes you create membership rules to automatically add and remove members. **Dynamic Device** denotes you create dynamic group rules to automatically add and remove devices. |
| Direct or Transitive | Identifies whether the device is a direct member or a transitive member. |

### Policy

The **Policy** tab provides the policies applied to devices, which include policy details, such as assignment, type, platform, and last modified.

| Column | Description |
| --- | --- |
| Name | The name of the device policy. |
| Assignment | Identifies the assignment status of the device. |
| Type | The type of policy. |
| Platform | The type of device platform. |
| Last Modified | The timestamp of the last time the device synchronized with Intune. |

### Applications

The **Applications** tab provides managed app install status, assigned, platform, type, and last modified.

| Column | Description |
| --- | --- |
| Name | The name of the application. |
| App install status | The installation status of the app. |
| Assigned | Provides whether the app has been assigned. |
| Platform | The type of device platform. |
| Type | You can choose an assignment type for each app. **Available** denotes that users install the app from the Company Portal app or website. **Not Applicable** denotes that the app is not installed or shown in the Company Portal. **Uninstall** denotes that the app is uninstalled from devices in the selected groups. **Available with or without enrollment** denotes that this app is assigned to groups of users whose devices are not enrolled with Intune. |
| Last modified | The timestamp of the last time the device synchronized with Intune. |

### App protection policy

The **App protection policy** tab provides the name, platform, and enrollment details for app protection policies. An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps.

| Column | Description |
| --- | --- |
| Name | The name of the app protection policy. |
| Platform | The platform of the device. |
| Enrollment | The enrollment status of the device. |

### Updates

The **Updates** tab provides an overall view of updates that are deployed to users. This information also provides filtering, searching, paging, and sorting.

| Column | Description |
| --- | --- |
| Name | The update name. |
| Platform | The platform of the device intended for the update. |
| Update type | The type of update. |

## Enrollment restrictions

The **Enrollment restrictions** tab provides the policy type, name, platform, and device limit. Enrollment restrictions are use to prevent (block) personally owned devices from enrolling, you will need to add the devices using corporate device identifiers, prior to enrollment.

### Properties

| Column | Description |
| --- | --- |
| Policy type | The type of policy. |
| Name | The name of the policy. |
| Platform | The platform of the device. |
| Device limit | The enrollment restriction to limit the number of devices a user can enroll in Microsoft Intune. |

### Diagnostics

The **Diagnostics** tab provides the device name or application, platform, created date, and diagnostic log.

Note

To collect and access diagnostics you must have the Collect diagnostics permission added to your role. For more information, see [Role-based administration control (RBAC) with Intune](../role-based-access-control/overview).

| Column | Text |
| --- | --- |
| Device name or application | The name of the device or application. |
| Platform | The platform of the device. |
| Created date | The timestamp of when the event occurred. |
| Diagnostic log | The diagnostic log file. |

## Collect available data from mobile device

Use the following resources to help collect device data when troubleshooting user's device issues:

- [Report a problem in Company Portal for iOS](../../user-help/diagnostics/collect-logs-ios)
- [Report a problem in Company Portal or Intune app for Android](../../user-help/diagnostics/collect-logs-android)

You can access and download user-submitted logs under **Diagnostics**.