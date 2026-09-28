---
layout: Conceptual
title: View reports for Windows LAPS policies in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/laps/monitor
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.subservice: protect
description: Use the Microsoft Intune admin center to view reports and details for Windows Local Administrator Policy Solution (LAPS)  policies.
ms.date: 2024-07-31T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: laarrizz
locale: en-us
document_id: 09d715e0-969a-9b5d-81ff-bbebd5e4023f
document_version_independent_id: 09d715e0-969a-9b5d-81ff-bbebd5e4023f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/laps/monitor.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/laps/monitor
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/laps/monitor.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 20c940ab-876d-36ab-b1c1-e507c685784a
---

# View reports for Windows LAPS policies in Microsoft Intune - Microsoft Intune | Microsoft Learn

After devices are assigned Microsoft Intune [policy for Windows LAPS](deploy-policy), you can view policy details from within the Microsoft Intune admin center. Reports for LAPS include details about devices and users that are assigned LAPS policies, the status of the policy settings like success, errors, or conflicts, and which devices are pending the submission of device status for assigned policy.

Reports for Windows LAPS policies are found in the Endpoint security node for Account protection policies. The Reports node of the Intune admin center doesn't have dedicated reports for Windows LAPS.

## LAPS policy report

You can use the LAPS policy report to view the configuration and assignments for a LAPS policy, and to drill in and identify the source of conflicts that prevent devices from applying your policies.

To use the report, sign in to the Intune admin center and navigate to the Account protection policy node. (**Endpoint security** &gt; **Account protection**). Here you can view a list of all Account protection policies, including the policies for LAPS that use the *Local admin password solution (Windows LAPS)* profile. You can identify the profile by the *Policy type* column:

[![Screen shot of the policy list for Account protection policies.](media/monitor/laps-policy-list.png)](media/monitor/laps-policy-list.png#lightbox)

When you select any row from the list of policies, Intune displays details for that policy that include:

- A summarization of the *Device and user check-in status* that displays the count of devices that the policy targets and that successfully report a status, have errors or conflicts, and so forth.
- A link labeled **View report** that opens a detailed report for each device or user that’s been assigned the policy. This report can help you understand the policy configuration and identify the source of conflicts that might prevent the policy from applying to a device.
- Each policy includes tiles you can use to investigate specific aspects of the LAPS report:

    - **Device assignment status** - This tile opens a customized report you can use to review details for a subset of assignment status, like devices with a status of *Success*, *Conflict*, or devices that are *Pending* and have yet to report a status.

        To use this report option, select one or more *Assignment status* options and then select **Generate again** to run the report for current details.

        The results you see are a subset of the results that are available from the *View report* option. This custom view includes support to drill in to device details to view more information about the selected assignment status that was selected for this report.
    - **Per setting status** - A report that lists each setting in policy, and the count of devices that have Success in applying the setting, have an Error, or a Conflict. This report view doesn’t support drilling in for more detail.

The following image displays a policy instance named *LAPSSHTest*. We use this policy as we examine what you can learn by using the **View report** button to drill in for more information:

[![Screen shot of the Device and user check-in status view for a Windows LAPS policy.](media/monitor/check-in-status.png)](media/monitor/check-in-status.png#lightbox)

While viewing the details for a policy, select the **View report** button to view a list that identifies each device that is assigned the policy. The device list includes the following information:

- Device name - Devices that are assigned this policy.
- Logged in user – Identifies the name of the user logged into the device at the time the policy last reported status.
- Check-in status - The policy status for the device. In the following example, the device shows a status of *Conflict*. Conflicts indicate that one or more other policies that are assigned to this device uses a different configuration for a setting.
- Filter
- Last report modification time – When the policy was last updated.

In the following image, we see that our example policy is assigned to a single device. The view also shows that there's a conflict for the devices *Check-in status*:

[![Screen shot of the list of devices that are assigned a Windows LAPS policy.](media/monitor/view-report-details.png)](media/monitor/view-report-details.png#lightbox)

When you select the name of a device from the *Device name* column Intune displays details about the settings assigned to that device. In the following image, we see that the device we selected has two assigned settings. Of the twos settings, *Password Age Days* is identified as being in conflict per the Setting status column. When you select a setting from the setting name column, Intune opens the *Settings Details* pane where you can view details about that setting.

In the following image, *Password Age Days* is selected so we can learn more about its conflict:

[![Screen shot of settings from a LAPS policy, with the Settings Details pane.](media/monitor/profile-settings.png)](media/monitor/profile-settings.png#lightbox)

The Settings Details pane shows us that the selected setting, *Password Age Days*, is configured through two profiles, one named *LAPSSHTest* (the profile we have been viewing), and the other named *Lapsshtestapril*.

With the *source profiles* that are in conflict now identified by name, you can go back to the list of policies to view the *Password Age Days*, setting from each, and resolve the conflict.

## Events and Audit logs

When you use Intune policies to manage Windows LAPS, the following events are audited and logged in Microsoft Entra ID:

- Automatic password rotation managed by policy
- Manual password rotation through a device action.
- Requests to view the password for an account.

For information about Microsoft Entra event logs, see [What are Microsoft Entra audit logs](/en-us/azure/active-directory/reports-monitoring/concept-audit-logs).