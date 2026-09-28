---
layout: Conceptual
title: Reports for Windows Update Ring Policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-update-rings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn about the reports available for Windows update ring policies in Intune. Discover how to access and interpret these reports to monitor update deployments.
ms.date: 2026-01-12T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: zadvor
locale: en-us
document_id: 9b529585-8c54-48d4-357d-8d8302018f7b
document_version_independent_id: 9b529585-8c54-48d4-357d-8d8302018f7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/monitor-update-rings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/monitor-update-rings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/monitor-update-rings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 530cf3fd-befc-021c-494f-5877c43ccfc4
---

# Reports for Windows Update Ring Policies - Microsoft Intune | Microsoft Learn

Intune offers integrated report views for the Windows update ring policies you deploy. These views display details about the update ring deployment and status.

To access update ring policies reports:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Windows**
2. Under **Manage updates**, select **Windows updates**
3. Select the **Update rings** tab
4. Select an update ring policy:

    [![Screen capture of the default view for update ring policy.](media/shared/update-rings.png)](media/shared/update-rings.png#lightbox)

On the policy page view:

- **Device and user check-in status**: The default report view for this policy. This default view includes a high-level bar chart that displays a count of devices reporting four status values for this policy, and a color bar that visually represents the percentage of devices reporting each status by color. This view displays the following four status results for the policy:

    - Succeeded
    - Error
    - Conflict
    - Not applicable
- **View report**: This button opens a more detailed report view for *Device and user check-in status*. The detailed report view includes a chart and color bar similar to that from the preceding high-level view, but reports one the additional status of **In progress**.

    This view also includes device specific details that include:

    - Device name
    - Logged in user
    - Check-in status
    - Last report modification time

    ![Screen capture that shows details available from the View report action.](media/monitor-update-rings/report-view-details.png)

    From this report view, you can select a device to drill in to view the list of the settings in the policy, and the status of the selected device for each of those settings. Additional drill-in is available by selecting a setting to open the *Setting details*. The *Setting details* display the name of the setting, the devices status (State) for that setting, and a list of profiles that manage the setting and that are assigned to the device. This is useful to help identify the source of a settings conflict.
- **Two additional report tiles**: You can select the tiles for the following reports to view additional details:

    - **Device assignment status**: This report shows all the devices that are targeted by the policy, including devices in a pending policy assignment state.

        For this report, you can select one or more status details you are interested in, and then select *Generate report* to update the view with only that information. In this following image, we have generated a report that displays only the devices that were successfully assigned this policy:

        ![Image of the results of the Assignment status report.](media/monitor-update-rings/successful-assignment-view.png)

        This report supports drilling in to view the list of settings, with subsequent drill-in as seen in for the full report view available from the *View report* button.
    - **Per setting status**: View the configuration status of each setting for this policy across all devices and users. This view present a simple view of each setting in the policy, and the count of assigned devices that have success, error, or conflict. This report view doesn't support drilling in for additional detail.

## Windows Update for Business reports

You can also monitor Windows update rollouts by using Windows Update for Business reports. Windows Update for Business reports is a cloud-based solution that provides information about your Microsoft Entra joined devices' compliance with Windows updates. It's offered through the Azure portal, and it's included as part of the Windows licenses.

To use this solution, you can use Intune to configure the required settings on your Windows devices.

For more information, see [Windows Update for Business reports overview](/en-us/windows/deployment/update/wufb-reports-overview).