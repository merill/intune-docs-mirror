---
layout: Conceptual
title: View enrollment reports - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/monitor-reports
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Monitor and troubleshoot issues with enrollment restrictions and enrollment status page assignments.
ms.date: 2025-10-20T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: maholdaa
locale: en-us
document_id: dbcaa17f-f70e-92f2-78f1-9697e4fe6d0e
document_version_independent_id: dbcaa17f-f70e-92f2-78f1-9697e4fe6d0e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/monitor-reports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/monitor-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/monitor-reports.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: fa896756-fd48-73f1-22fe-8e127acc559f
---

# View enrollment reports - Microsoft Intune | Microsoft Learn

Use the following reports in the Microsoft Intune admin center to monitor and troubleshoot issues with enrollment restrictions and enrollment status page assignments:

- Enrollment failures report
- Troubleshooting + support page
- Device enrollment page

This article describes each report and how to access them in the admin center. The reports show details for the following platforms:

- Android
- iOS
- macOS
- Windows

## Enrollment failures report

Use the enrollment failures report to view enrollment failures for all users or for select users. This report shows each failed enrollment attempt along with the date it occurred, reason for failure, OS, OS version, username, and enrollment method.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **Monitor**.
3. Select the **Enrollment failures** report.
4. Select **All users** or **Select user**, depending on the scenario you're troubleshooting.
5. Select a row in the table for more details about the failure and recommended remediation steps.

![Example image of the enrollment failures report, showing the enrollment failure details for a selected row.](media/restrictions/enrollment-failure-report-details-2112.png)

## Troubleshooting + support page

Use the enrollment failures report on the Troubleshooting + support page to view enrollment failures for a select user. This report shows every failed enrollment attempt the user encountered along with the date it occurred, reason for failure, OS, OS version, username, and enrollment method. You can also view other data about the user on this page, including all assignments, devices, and app protection statuses they're associated with. To see enrollment failures for unlicensed users, select **Filter**, and then choose **User not found or licensed**.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Troubleshooting + support**.
2. Search for the user by name or email address.
3. Select the **Enrollment failures** metric for more information about detected failures and recommended remediation steps.

## Device enrollment page

The device enrollment page shows the enrollment policies (both enrollment restriction and enrollment status page policies) applied to a device when it was first enrolled in Microsoft Intune. Use this report to help pinpoint the source of the failure, such as an unexpected policy, target, or filter. Data is available for iOS/iPadOS, macOS, and Windows devices, and includes:

- Profile name
- User principal name
- Profile type (includes enrollment status page, device type enrollment restriction, or Windows Backup and Restore profile)
- Priority
- Target (either user or device)
- Filters, with a link to the filter evaluation results (only available if the enrollment policy was assigned using an assignment filter)

To access report data:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **All devices**.
2. Select an enrolled iOS/iPadOS, macOS, or Windows device.
3. From the **Monitor** options, select **Enrollment**.
4. Review the report data.

![Example image of the Device enrollment page, showing a table of enrollment profiles.](media/restrictions/enrollment-page-report-2112.png)