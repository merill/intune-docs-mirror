---
layout: Conceptual
title: Configuration Manager Report Action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/report-action
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
description: Learn how to use report action in the configuration manager to display reports in the configuration manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ca626ed9-0e9c-8524-6b19-b00db1f9288e
document_version_independent_id: 56bc5f10-9c3b-503f-e0d0-d5b2e0ecca0f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/report-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/report-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/report-action.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4436d262-f7bb-d290-fd7f-754daf68fa53
---

# Configuration Manager Report Action - Configuration Manager | Microsoft Learn

The report action displays a Configuration Manager report in the Configuration Manager console.

The following attributes and elements are specific to an action that opens a report box:

- The `ActionDescription` element `Class` attribute is set to **Report**.
- The `ReportDescription` element `ReportName` attribute is the GUID of the report to be displayed. The GUID maps to the `SMS_Report` class `ReportGUID` property.

Note

An alternative method to load a report is to use the executable action to launch the report's URL. This will display the report in a new window rather than in the Configuration Manager console.

## Sample Report Action XML

The following XML demonstrates how to display a report, identified by its GUID, in the Configuration Manager console:

```
<ActionDescription Class="Report" DisplayName="Test Action (report)" MnemonicDisplayName="Mnemonic" Description="Description"> <ShowOn>      <string>DefaultContextualTab</string> <!-- RIBBON -->     <string>ContextMenu</string> <!-- Context Menu -->   </ShowOn>
 <ReportDescription ReportName="05874720-1D08-4CF7-B182-5F9D065BEAE5">
 </ReportDescription>
</ActionDescription>
```