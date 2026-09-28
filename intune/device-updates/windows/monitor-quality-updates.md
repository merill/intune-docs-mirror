---
layout: Conceptual
title: Reports for Windows Quality Update Policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-quality-updates
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn about the reports available for Windows quality update policies in Microsoft Intune.
ms.date: 2026-01-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: zadvor
locale: en-us
document_id: 13b95c50-7587-8770-7baf-92a48cdb6825
document_version_independent_id: 13b95c50-7587-8770-7baf-92a48cdb6825
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/monitor-quality-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/monitor-quality-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/monitor-quality-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a2b882c9-80c4-78e1-62ce-89acf1c52ff4
---

# Reports for Windows Quality Update Policies - Microsoft Intune | Microsoft Learn

The Windows update distribution report in Intune provide a summarized report to show the number of devices that are on each quality update level and the percentage coverage for each update across devices managed by Intune (including co-managed devices).

The report provides a drill down for each quality update that aggregates devices based on Windows feature version and the update statuses. The admins can get the list of devices that aggregate to the numbers shown in the previous two reports, which they can export and use for troubleshooting and analysis.

The report includes Intune managed and co-managed devices, and is based on the OS version updated at every device check-in. The report can slice the data based on device scope tags.

Note

The Windows update distribution report can be used if you are using Update Rings, or not using any update policies in Intune.

The Windows update distribution report comprises distinct organizational reports that function sequentially to provide insights on devices and their corresponding Windows update versions. To access this feature, navigate to **Reports** &gt; **Windows Updates** &gt; **Reports tab** &gt; **Windows Update Distribution Report**.

The Windows update distribution report includes three nested reports:

- Windows quality update distribution report
- Windows quality update distribution per feature version report
- Windows quality update device version report

Select a tab to learn more about each report.

# [QU distribution](#tab/distribution)
The report displays the distribution of devices against different quality updates for the selected scope. It shows the counts of devices corresponding to the displayed quality updates. Select one or more scope tags from the drop-down list to generate the report. The drop-down list shows all the scope tags the user has access to, based on the user's assigned scope tags.

[![Screen capture of the Windows quality update distribution report.](media/monitor-quality-updates/quality-update-distribution.png)](media/monitor-quality-updates/quality-update-distribution.png#lightbox)

The report shows the number of devices under each QU level corresponding to the current month and the last 3 months from the day of reporting. The top rows typically represent the last three months, followed by other device data distributions.

**Column details**:

- **Update**: Monthly quality update version. The update format corresponds to YYYY-MM-UpdateType. For example, 2024-02-B.
    - **Older releases**: All windows devices running valid feature version (non-preview/insider) and running older than 3 months of quality update level are combined into a single entity shown as *Older releases*.
    - **Windows insider or other releases**: All those devices whose OS version does not align with the Windows generally available feature release version and not on documented QU level, are combined under *Windows insider or other releases*.
- **Update Type**: Monthly quality update type. For more information, go to [Windows monthly update explained](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/windows-monthly-updates-explained/ba-p/3773544)
    - B: Security Updates (released on patch Tuesday)
    - D: Non-Security Updates (released on 4th week of month)
    - OOB: Out of band updates
- **Release Date**: Release date of the monthly quality update.
- **Devices on this update**: Number of devices where the target quality update is installed.
- **% of all devices**: Number of devices running a particular quality update represented in percentage of total managed devices in Intune.

All QUs from this page are hyperlinked:

- When you select one of the current or last 3 months quality update (B, D or OOB), the *Windows quality update distribution per feature version* report is displayed.
- When you select **Older releases**, the *Windows quality update device version* report is displayed with a list of devices that are on an older quality update level excluding insider builds and unknown builds.
- When you select **Windows insider or other releases**, the *Windows quality update device version* report is displayed with a list of devices whose feature version is insider release, or the quality update of the device cannot be mapped to documented quality update version in Windows release information.

# [QU distribution per feature version](#tab/feature-version)
The report provides the distribution of devices against Windows feature releases. The distribution of devices that are eligible to receive the selected quality update shown based on the Windows feature versions that are generally available. The report aids IT administrators in making informed decisions for devices and managing devices that need attention.

[![Screen capture of the Windows quality update distribution per feature version.](media/monitor-quality-updates/quality-update-per-feature-version.png)](media/monitor-quality-updates/quality-update-per-feature-version.png#lightbox)

The stacked chart displays the counts of devices that are up to date, those that need updates, and those for which the chosen quality update does not apply. Together, these counts make up the total Windows devices that Intune manages, including co-managed devices.

The table lists each supported feature version that the selected quality update affects.

Select **Columns** at the top of the table to toggle the visibility of columns, including the **Devices on this update** column, which is hidden by default. You can sort the data by the **Windows version** and **Build number** columns.

**Column details**:

- **Windows version**: Shows the Windows feature version.
- **Total devices**: Total managed devices corresponding to the Windows feature version.
- **Build Number**: Build number of the windows feature version. Devices running supported Windows feature versions that the selected quality update does not cover are marked as **Not applicable**. Devices running unsupported Windows feature versions, insider versions, or those with an unknown OS version, are grouped under one line item and marked as **Not applicable**.
- **Devices on this update or later**: Number of devices where the target quality update or later is installed.
- **Devices on this update**: Number of devices where the target quality update is installed.
- **Devices need update**: Number of devices that are applicable for the update but do not currently have it installed. KB article: External link to target quality update's KB Article for the corresponding Windows feature version.

When you select any device count, the *Windows quality update device version* report is displayed.

# [QU device version](#tab/device-version)
The report presents a list of devices based on the selections from the previous 2 reports. The criteria that you selected in the previous reports are displayed at the top of the page. The report offers sortable columns and search options, along with an export feature allowing high volume data to be downloaded in CSV format.

[![Screen capture of the Windows quality update device version.](media/monitor-quality-updates/quality-update-device-version.png)](media/monitor-quality-updates/quality-update-device-version.png#lightbox)

**Column details**:

- **Device Name**: The name of the device.
- **Intune Device Id**: Intune device identifier.
- **Entra Device Id**: Microsoft Entra identifier for device.
- **Primary UPN**: Intune user identifier (email).
- **OS version**: Operating System (OS) version build number. The OS version corresponds to the Windows feature Version (For example, Windows 11 24H2) and the quality Update level (For example, 2024-08 B).
- **Windows feature version**: Windows feature version.
- **Windows quality version**: Windows quality update.
- **Managed by**: Management agent.
- **Last check-in**: Device last check-in date time

The search bar enables the search for a specific device or UPN. Select a device from the list to view the device's details.

---

All these reports are cached, and have an expiry time of three days, after which you must generate a new report. Select **Generate Again** to get fresh data.