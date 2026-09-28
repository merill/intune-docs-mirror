---
layout: Conceptual
title: Manage configuration data - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/management-tasks-for-configuration-data
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
description: After you create configuration items and baselines in Configuration Manager, you can use other commands to perform various actions.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 503b3153-1c74-3d63-40dc-c450c49affcd
document_version_independent_id: ba40aecd-ac1e-8917-2321-eb5f4b147a7d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/deploy-use/management-tasks-for-configuration-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/deploy-use/management-tasks-for-configuration-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/deploy-use/management-tasks-for-configuration-data.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 53aa18c4-2023-dbd1-86f7-f43d8e118de9
---

# Manage configuration data - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you have created configuration items and configuration baselines in Configuration Manager, further commands are available to help you perform various actions.

## Manage configuration items

- In the **Assets and Compliance** workspace, expand **Compliance Settings** &gt; **Configuration Items**, select the configuration item to manage, and then select a management task.

| Management task | Details |
| --- | --- |
| **Create Child Configuration Item** | Opens the **Create Child Configuration Item Wizard** where you can create a child configuration item from the selected configuration item. You cannot create a child configuration item from a mobile device configuration item. For details, see [Create child configuration items](create-child-configuration-items). |
| **Revision History** | Opens the **Configuration Item Revision History** dialog box where you can view and manage previous revisions of the selected configuration item. |
| **View XML Definition** | Displays the XML definition file for the selected configuration item in a new window. This information can be useful when you want to author configuration data manually. |
| **Export** | Exports a configuration item in a cabinet (.cab) file format, providing that it was created at that site. You can then import it to the same or a different Configuration Manager site. Configuration data is converted to DCM Digest. |
| **Copy** | Creates a copy of the selected configuration item with a name you specify. The new configuration item does not retain any relationship to the original configuration item. This means that the duplicate configuration item does not continue to inherit configuration information from the original configuration item. |
| **Delete** | Opens the **Delete Configuration Item** dialog box where you can review any references to this configuration item. You must remove all references to a configuration item before you can delete the configuration item. |

## Manage configuration baselines

- In the **Assets and Compliance** workspace, expand **Compliance Settings** &gt; **Configuration Baselines**, select the configuration baseline to manage, and then select a management task.

| Management task | Details |
| --- | --- |
| **Show Members** | Displays all of the configuration items that are referenced by the configuration baseline. |
| **Schedule Summarization** | Configures the schedule by which the data shown in the **Configuration Baselines** node in the Configuration Manager console is updated with the latest information from the site database. |
| **Run Summarization** | Summarization causes the data in the **Configuration Baselines** node to be refreshed with the latest data from the site database. This action might take several minutes to complete. You might have to click **Refresh** before you can see the latest data in the console. |
| **View XML Definition** | Displays the XML definition file for the selected configuration baseline in a new window. This information can be useful when you want to author configuration data manually. |
| **Enable** | Enables a configuration baseline for compliance monitoring. |
| **Disable** | Disables a configuration baseline so it is no longer evaluated for compliance on client computers. Configuration baselines that reference this configuration baseline will also be disabled. |
| **Export** | Exports a configuration baseline in a cabinet (.cab) file format, providing that it was created at that site. You can then import it to the same or a different Configuration Manager site. Configuration data is converted to DCM Digest. For information about how to import configuration data, see [Import configuration data](import-configuration-data). |
| **Copy** | Creates a copy of the selected configuration baseline with a name that you specify. The new configuration baseline does not retain any relationship to the original configuration baseline. |
| **Delete** | Opens the **Delete Configuration Baseline** dialog box where you can review any references to this configuration baseline. You must remove all references to a configuration baseline before you can delete the configuration baseline. |
| **Deploy** | Opens the **Deploy Configuration Baseline** dialog box where you can deploy one or more configuration baselines to devices in your hierarchy. For details, see [Deploy configuration baselines](deploy-configuration-baselines). |