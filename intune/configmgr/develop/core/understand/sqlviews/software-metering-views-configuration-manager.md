---
layout: Conceptual
title: Software metering views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/software-metering-views-configuration-manager
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
description: Information such as the software metering rules that are created in the Configuration Manager hierarchy.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 18e46b61-a4a4-02e5-90e0-792fbc7d2559
document_version_independent_id: 61892fd7-8b94-ce80-be71-edaa0cac3ba4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/software-metering-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/software-metering-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/software-metering-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 6040205c-2489-b7d9-e208-e336a6a865d2
---

# Software metering views - Configuration Manager | Microsoft Learn

The software metering views contain information such as the software metering rules that are created in the Configuration Manager hierarchy, which files to meter, the products in which the files belong, the users that have used the metered files, and more. Several of the status and status summarizer views also provide information about file usage. Most often, the software metering views can be joined to other views by using the **FileID** and **ResourceID** columns.

The following sections provide detailed information about software metering views and software metering status views.

## Software metering views

The software metering views are described in this section.

### v\_GS\_SoftwareUsageData

Lists the Configuration Manager client computers, by resource ID, that have used metered files. The view contains the start time, end time, user name, file ID, file name, file description, file version, file size, product name, product version, and more. The view can be joined to other views by using the **ResourceID**, **FileID**, and **UserName** columns.

### v\_MeterData

Lists all software metering data, including the meter data ID, time span for the data, file ID, resource ID, user ID, and more. The view can be joined to other views by using the **FileID**, **ResourceID**, and **MeteredUserID** columns.

### v\_MeteredFiles

Lists all files that are configured in the software metering rules and metered on clients. The view contains the software metering rule ID, security key, product name, site code, file name, file version, metered file ID, metered product ID, and more. The view can be joined to other views by using the **RuleID**, **SecurityKey**, **MeteredProductID**, and **MeteredFileID** columns.

### v\_MeteredProductRule

Lists all software metering rules that have been configured in the Configuration Manager site hierarchy. The view contains the software metering rule ID, security key, product name, file name, file version, site code, and more. The view can be joined to other views by using the **RuleID** and **SecurityKey** columns.

### v\_MeteredUser

Lists all users who have used metered files. The view contains the metered user ID, full user name (domain\user name), domain, and user name. The view can be joined to other views by using the **MeteredUserID** and **FullName** columns.

### v\_MeterRuleInstallBase

Lists all metered files for system resources that match files by FileID that are also in software inventory. The view contains the rule ID, product name, metered file ID, and resource ID. The view can be joined to other views by using the **RuleID**, **MeteredFileID**, and **ResourceID** columns.

## Software metering status views

The software metering status views contain status summary information about the file usage for metered files. For more information about the status views, see [Status and Alert Views in Configuration Manager](status-alert-views-configuration-manager). The status views that contain software metering information are described in this section.

### v\_FileUsageSummary

Lists software metering summary status information for file usage by site. The view can be joined to other views by using the **FileID** column.

### v\_FileUsageSummaryIntervals

Lists software metering summary interval information for file usage. It is unlikely that this view will be joined to other views.

### v\_MonthlyUsageSummary

Lists the Configuration Manager client computers, by resource ID, and the usage summary for metered files, as well as the logged-on user name, usage time, and time of last usage. The view can be joined to other views by using the **ResourceID**, **FileID**, and **MeteredUserID** columns.