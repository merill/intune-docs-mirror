---
layout: Conceptual
title: Create child configuration items - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/create-child-configuration-items
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
description: Create child configuration items in Configuration Manager.
ms.date: 2019-05-07T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d79b60de-08cd-97ae-c1e1-739ee0848ed9
document_version_independent_id: 3669ac41-09a9-7aab-687c-b1813a47138d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/deploy-use/create-child-configuration-items.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/deploy-use/create-child-configuration-items
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/deploy-use/create-child-configuration-items.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4141f93d-5c72-34b3-a60f-d9fb084193f7
---

# Create child configuration items - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Child configuration items in Configuration Manager are copies of configuration items that retain a relationship to the original configuration item in that they inherit the original configuration from the parent configuration item.

When you view the properties of a child configuration item in the Configuration Manager console, you cannot edit the inherited objects and settings with their validation criteria. However, you can add and then edit additional validation criteria to the child configuration item, and you can also add new objects and settings to the child configuration item. An example for creating and editing a child configuration item is to refine the original configuration item to meet your business requirements.

Note

You can only create child configuration items from configuration items of the type **Windows Desktops and Servers (custom)**.

## To create a child configuration item

1. In the Configuration Manager console, click **Assets and Compliance** &gt; **Compliance Settings** &gt; **Configuration Items**.
2. In the **Configuration Items** list, select the configuration item for which you want to create a child configuration item, and then in the **Home** tab, in the **Configuration Item** group, click **Create Child Configuration Item**.
3. On the **General** page of the **Create Child Configuration Item Wizard**, you can choose a specific revision of the parent configuration item to use to create the child. Other steps in this wizard are identical to those you would use to create a standard configuration item. For more information, see [How to create custom configuration items for Windows desktop and server computers](create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client).
4. Complete the wizard. The new child configuration item displays in the **Configuration Items** list.