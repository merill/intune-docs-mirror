---
layout: Conceptual
title: Manage devices with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/manage-overview
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Overview of device management capabilities in Intune for Education, including remote actions, remote assistance, and inventory/reporting.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 0c21b225-ec65-52b8-81d7-ca573496b2b1
document_version_independent_id: 0c21b225-ec65-52b8-81d7-ca573496b2b1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/manage-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/manage-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/manage-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 2c14aea5-ada9-36bc-7ef1-a85e48668c18
---

# Manage devices with Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune offers a streamlined remote device management experience throughout the school year. IT administrators can optimize device settings, deploy new applications, updates, ensuring that security and privacy are maintained.

![The device lifecycle for Intune-managed devices - protect and manage devices](media/manage-overview/protect-manage.png)

With Intune, there are several ways to manage students' devices. Groups can be created to organize devices and students, to facilitate remote management. You can determine which applications students have access to, and fine tune device settings and restrictions. You can also monitor which devices students sign in to, and troubleshoot devices remotely.

## Remote actions

![](../../../media/icons/16/check.svg) Remotely trigger actions on devices

Intune allows you to perform actions on devices without having to sign in to the devices. For example, you can send a command to a device to restart or to turn off, or you can locate a device.

# [Intune](#tab/intune)
[![Remote actions available in Intune for Education when selecting a Windows device](media/manage-overview/intune-remote-actions-windows.png)](media/manage-overview/intune-remote-actions-windows.png#lightbox)

Remote actions can be performed on one or multiple devices at once.

To learn more about remote actions in Intune, see [Remote actions](/en-us/intune/intune-service/remote-actions/device-management).

# [Intune For Education](#tab/intune-for-education)
[![Remote actions available in Intune for Education when selecting a Windows device](media/manage-overview/remote-actions.png)](media/manage-overview/remote-actions.png#lightbox)

With bulk actions, remote actions can be performed on multiple devices at once.

To learn more about remote actions in Intune for Education, see [Remote actions](/en-us/intune-education/edu-device-remote-actions).

---

## Remote assistance

![](../../../media/icons/16/check.svg) View and control remote devices

With devices managed by Intune, you can remotely assist students and teachers that are having issues with their devices.

For more information, see [Remote assistance for managed devices](/en-us/intune-education/remote-assist-mobile-devices).

## Device inventory and reporting

![](../../../media/icons/16/check.svg) View device information and reporting

With Intune, it's possible view and report on current devices, applications, settings, and overall health. You can also download reports to review or share offline.

# [Intune](#tab/intune)
Here are some examples of the reports available in Intune:

- Device compliance reports
- Device configuration reports
- Device enrollment reports
- Update reports
- Security reports
- Application reports

To learn more about reports in Intune, see [Reports in Intune](../../../device-management/reports/overview).

# [Intune For Education](#tab/intune-for-education)
Here are the steps for generating reports in Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Reports**.
3. Select between one of the report types:
    - Device inventory
    - Device actions
    - Application inventory
    - Settings errors
    - Windows Defender
    - Windows Autopilot deployment
4. If needed, use the search box to find specific devices, applications, and settings.
5. To download a report, select **Download**. The report downloads a comma-separated value (CSV) file, which you can view and modify in a spreadsheet app like Microsoft Excel. ![Reporting options available in Intune for Education when selecting the reports blade](media/manage-overview/inventory-reporting.png)

To learn more about reports in Intune for Education, see [Reports in Intune for Education](/en-us/intune-education/what-are-reports).

---