---
layout: Conceptual
title: Import configuration data - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/import-configuration-data
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
description: Import configuration data if it's contained in a cabinet file format and adheres to the supported Service Modeling Language schema.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4368f97b-a015-3a2b-4b0c-12bf1ae90193
document_version_independent_id: bf7c01a5-d775-4211-403a-9a3f73ba37be
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/deploy-use/import-configuration-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/deploy-use/import-configuration-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/deploy-use/import-configuration-data.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: d38ca230-566b-54ae-8dc9-c0c022ad0328
---

# Import configuration data - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

In addition to creating configuration baselines and configuration items in the Configuration Manager console, you can import configuration data if it's contained in a cabinet (.cab) file format and adheres to the supported Service Modeling Language (SML) schema. You can import configuration data from:

- Best practice configuration data (Configuration Packs) that has been downloaded from Microsoft or from other software vendor sites.
- Configuration data that has been exported from System Center 2012 Configuration Manager and later.
- Configuration data that was externally authored and that conforms to the SML schema.

When you import a configuration baseline, some or all of the configuration items that are referenced in the configuration baseline might also be included in the cabinet file. During the import process, Configuration Manager verifies that all of the configuration items that are referenced in the configuration baseline are either also included in the cabinet file or already exist in the Configuration Manager site. The import process fails if you attempt to import a configuration baseline that references configuration data that Configuration Manager can't locate.

Other scenarios where the import process might fail include the following:

- The configuration data references configuration data that Configuration Manager can't locate, either in its database or in the cabinet file itself.
- The configuration data is already present in the Configuration Manager database with the same name and configuration data version, but the content version differs.
- The configuration data is already present in the Configuration Manager database with the same content version, but the hash calculation identifies it as being different.
- A newer version of the configuration data with same name is already present or has recently been deleted in the Configuration Manager database.
- In a multi-site Configuration Manager hierarchy, the configuration data was originally imported from a parent site. You must update it from the same site and not a child site.

### Import configuration data

1. In the Configuration Manager console, click **Assets and Compliance** &gt; **Configuration Items** or **Configuration Baselines**
2. In the **Home** tab, in the **Create** group, click **Import Configuration Data**.
3. On the **Select Files** page of the **Import Configuration Data Wizard**, click **Add**, and then in the **Open** dialog box, select the .cab files you want to import.
4. Select the **Create a new copy of the imported configuration baselines and configuration items** check box if you want the imported configuration data to be editable in the Configuration Manager console.
5. On the **Summary** page, review the actions that will be taken, and then complete the wizard.

The imported configuration data displays in the **Compliance Settings** node of the **Assets and Compliance** workspace.