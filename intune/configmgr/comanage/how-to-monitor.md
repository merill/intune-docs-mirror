---
layout: Conceptual
title: Monitor co-management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-monitor
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Use the co-management dashboard to review information about co-managed devices.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 38f3684c-7f3f-ba2b-93eb-565640777161
document_version_independent_id: d666e010-2bea-3559-7dda-fb2e79bd8733
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/how-to-monitor.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/how-to-monitor
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/how-to-monitor.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cdff63d4-09c7-eb88-3b56-c2e4335420b9
---

# Monitor co-management - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you enable co-management, monitor co-management devices using the following methods:

- Co-management dashboard
- Deployment policies
- WMI device data

## Co-management dashboard

This dashboard helps you review machines that are co-managed in your environment. The graphs can help identify devices that might need attention.

In the Configuration Manager console, go to the **Monitoring** workspace, and select the **Cloud Attach** node.

- For version 2103 and earlier, select the **Co-management** node.

![Screenshot of the co-management dashboard](media/co-management-dashboard.png)

### Client OS distribution

Shows the number of client devices per OS by version. It uses the following groupings:

- Windows 7 & 8.x
- Windows 10 lower than 1709
- Windows 10 1709 and later

Hover over a graph section to show the percentage of devices in that OS group.

![Client OS distribution tile](media/co-management-dashboard/co-management-os-distribution-graph.png)

### Co-management status

A funnel chart that shows the number of devices with the following states from the enrollment process:

- Eligible devices
- Scheduled
- Enrollment initiated
- Enrolled

![Co-management status (funnel) tile](media/co-management-dashboard/1358980-status-funnel.png)

### Co-management enrollment status

Shows the breakdown of device status in the following categories:

- Success, Microsoft Entra hybrid joined
- Success, Microsoft Entra joined
- Enrolling, Microsoft Entra hybrid joined
- Failure, Microsoft Entra hybrid joined
- Failure, Microsoft Entra joined
- Pending user sign in
    - To reduce the number of devices in this pending state, a new co-managed device automatically enrolls to the Microsoft Intune service based on its Microsoft Entra ID *device* token. It doesn't need to wait for a user to sign in to the device for auto-enrollment to start. To support this behavior, the device needs to be running Windows 10, version 1803 or later. If the device token fails, it falls back to previous behavior with the user token. Look in the **ComanagementHandler.log** for the following entry: 

> 
> `Enrolling device with RegisterDeviceWithManagementUsingAADDeviceCredentials`

Select a state in the tile to drill through to a list of devices in that state.

![Co-management enrollment status tile](media/co-management-dashboard/1358980-enrollment-status.png)

### Workload transition

Displays a bar chart with the number of devices that you've transitioned to Microsoft Intune for the available workloads. For more information, see [Workloads able to be transitioned to Intune](workloads).

Hover over a chart section to show the number of devices transitioned for the workload.

![Workload transition bar graph](media/co-management-dashboard/workload-transition.png)

### Enrollment errors

This table is a list of enrollment errors from devices. These errors can come from the MDM component in Windows, the core Windows OS, or the Configuration Manager client.

There are hundreds of possible errors. The following table lists the most common errors.

| Error | Description |
| --- | --- |
| 2147549183 (0x8000FFFF) | MDM enrollment hasn't been configured yet on Microsoft Entra ID, or the enrollment URL isn't expected.[Enable automatic enrollment](../../device-enrollment/windows/enable-automatic-mdm) |
| 2149056536 (0x80180018)MENROLL\_E\_USERLICENSE | License of user is in bad state blocking enrollment[Assign licenses to users](../../fundamentals/assign-licenses) |
| 2149056555 (0x8018002B)MENROLL\_E\_MDM\_NOT\_CONFIGURED | When trying to automatically enroll to Intune, but the Microsoft Entra configuration isn't fully applied. This issue should be transient, as the device retries after a short time. |
| 2149056554 (0x‭8018002A‬) | The user canceled the operationIf MDM enrollment requires multi-factor authentication, and the user hasn't signed in with a supported second factor, Windows displays a toast notification to the user to enroll. If the user doesn't respond to toast notification, this error occurs. This issue should be transient, as Configuration Manager will retry and prompt the user. Users should use multi-factor authentication when they sign in to Windows. Also educate them to expect this behavior, and if prompted, take action. |
| 2149056532 (0x80180014)MENROLL\_E\_DEVICENOTSUPPORTED | Mobile device management isn't supported. Check device restrictions. |
| 2149056533 (0x80180015)MENROLL\_E\_NOTSUPPORTED | Mobile device management isn't supported. Check device restrictions. |
| 2149056514 (0x80180002)MENROLL\_E\_DEVICE\_AUTHENTICATION\_ERROR | Server failed to authenticate the user There's no Microsoft Entra token for the user. Make sure the user can authenticate to Microsoft Entra ID. |
| 2147942450 (0x‭80070032‬) | MDM auto-enrollment is only supported on Windows RS3 and above.Make sure the device meets the [minimum requirements](overview#windows) for co-management. |
| 3400073293 | ADAL user realm account response unknownCheck your Microsoft Entra configuration, and make sure that users can successfully authenticate. |
| 3399548929 | Need user sign-inThis issue should be transient. It occurs when the user quickly signs out before the enrollment task happens. |
| 3400073236 | ADAL security token request failed.Check your Microsoft Entra configuration, and make sure that users can successfully authenticate. |
| 2149122477 | Generic HTTP issue |
| 3400073247 | ADAL-integrated Windows authentication is only supported in federated flow[Plan your Microsoft Entra hybrid join implementation](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan) |
| 3399942148 | The server or proxy wasn't found.This issue should be transient, when the client can't communicate with cloud. If it persists, make sure the client has consistent connectivity to Azure. |
| 2149056532 | Specific platform or version is not supportedMake sure the device meets the [minimum requirements](overview#windows) for co-management. |
| 2147943568 | Element not foundThis issue should be transient. If it persists, contact Microsoft Support. |
| 2192179208 | Not enough memory resources are available to process this command.This issue should be transient, it should resolve itself when the client retries. |
| 3399614467 | ADAL Authorization grant failed for this assertionCheck your Microsoft Entra configuration, and make sure that users can successfully authenticate. |
| 2149056517 | Generic Failure from management server, such as DB access errorThis issue should be transient. If it persists, contact Microsoft Support. |
| 2149134055 | Winhttp name not resolvedThe client can't resolve the name of the service. Check the DNS configuration. |
| 2149134050 | internet timeoutThis issue should be transient, when the client can't communicate with cloud. If it persists, make sure the client has consistent connectivity to Azure. |

For more information, see [MDM Registration Error Values](/en-us/windows/desktop/mdmreg/mdm-registration-constants).

## Deployment policies

Two policies are created in the **Deployments** node of the **Monitoring** workspace. One policy is for the pilot group and one for production. These policies report only the number of devices where Configuration Manager has applied the policy. They don't consider how many devices are enrolled in Intune, which is a requirement before devices can be co-managed.

The production policy (CoMgmtSettingsProd) is targeted to the **All Systems** collection. It has an applicability condition that checks the OS type and version. If the client runs a server OS or isn't Windows 10 or later, the policy doesn't apply, and no action is taken.

Tip

For an example collection query for co-managed devices see, [Create queries in Configuration Manager](../core/servers/manage/create-queries#bkmk_comgmt).

## WMI device data

Query the **SMS\_Client\_ComanagementState** WMI class in the **ROOT\SMS\site\_&lt;SITECODE&gt;** namespace on the site server. You can create custom collections in Configuration Manager, which help determine the status of your co-management deployment. For more information on creating custom collections, see [How to create collections](../core/clients/manage/collections/create-collections).

The following fields are available in the WMI class:

- **MachineId**: A unique device ID for the Configuration Manager client
- **MDMEnrolled**: Specifies whether the device is MDM-enrolled
- **Authority**: The authority for which the device is enrolled
- **ComgmtPolicyPresent**: Specifies whether the Configuration Manager co-management policy exists on the client. If the **MDMEnrolled** value is `0`, the device isn't co-managed whatever co-management policy exists on the client.

A device is co-managed when the **MDMEnrolled** field and **ComgmtPolicyPresent** fields both have a value of `1`.