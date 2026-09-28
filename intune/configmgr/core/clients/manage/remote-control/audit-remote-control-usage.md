---
layout: Conceptual
title: Audit remote control usage - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/audit-remote-control-usage
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
description: Audit remote control use in Configuration Manager.
ms.date: 2017-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b18bf96e-daab-f544-2806-d39c15f8b223
document_version_independent_id: 511c9078-bd72-c073-713e-21577e5613ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/remote-control/audit-remote-control-usage.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/remote-control/audit-remote-control-usage
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/remote-control/audit-remote-control-usage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 316f77d1-4686-9d2b-0045-f84d92662d10
---

# Audit remote control usage - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can use Configuration Manager reports to view audit information for remote control.

For more information about how to configure reporting in Configuration Manager, see [Introduction to reporting](../../../servers/manage/introduction-to-reporting).

The following two reports are available with the category **Status Messages - Audit**:

- **Remote Control - All computers remote controlled by a specific user** - Displays a summary of remote control activity that a specific user initiated.
- **Remote Control - All remote control information** - Displays a summary of status messages about remote control of client computers.

### To run the report Remote Control - All computers remote controlled by a specific user

1. In the Configuration Manager console, click **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then click **Reports**.
3. In the **Reports** node, click the **Category** column to sort the reports so that you can more easily find the reports in the category **Status Messages - Audit**.
4. Select the report **Remote Control - All computers remote controlled by a specific user**, and then, on the **Home** tab, in the **Report Group**, click **Run**.
5. In the **User Name** list of the **Remote Control - All computers remote controlled by a specific user**, specify the user that you want to report audit information for, and then click **View Report**.
6. When you have finished viewing the data in the report, close the report window.

### To run the report Remote Control - All remote control information

1. In the Configuration Manager console, click **Monitoring**.
2. In the **Monitoring** workspace, expand **Reporting**, and then click **Reports**.
3. In the **Reports** node, click the **Category** column to sort the reports so that you can more easily find the reports in the category **Status Messages - Audit**.
4. Select the report **Remote Control - All remote control information**, and then, on the **Home** tab, in the **Report Group**, click **Run** to open the **Remote Control - All remote control information** window.
5. When you have finished viewing data in the report, close the report window.