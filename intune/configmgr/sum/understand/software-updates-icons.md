---
layout: Conceptual
title: Icons used for software updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/understand/software-updates-icons
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
description: The Configuration Manager console contains icons that indicate a state for the synchronized update or software update group.
ms.date: 2021-06-21T00:00:00.0000000Z
ms.topic: article
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: d81f39fe-02dd-6df3-f649-2389580d3fb8
document_version_independent_id: 801a84d4-989d-56f1-572e-7e8a385e5d2d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/understand/software-updates-icons.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/understand/software-updates-icons
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/understand/software-updates-icons.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e2c9f30c-00ec-44c0-846c-b20dbfb3283f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/702271fe-87d7-4493-828b-2d6fde3de8ab
platformId: 5e4ba244-6ba2-a401-06a0-92c6a054f6c6
---

# Icons used for software updates - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Synchronized software updates are displayed in the Configuration Manager console, and the first column for each software update contains an icon that indicates a specific state. Software update groups are also represented with an icon that provides information about the state of the software updates contained in the group. This section provides information about the software update icons and what each icon represents.

## Icons for Software Updates

Synchronized software updates are represented by one of the following icons.

### Normal Icon

![Normal icon](../media/normal.jpg) The icon with the green arrow represents a normal software update.

**Description:**

Normal software updates have been synchronized and are available for software deployment.

**Operational Concerns:**

There are no operational concerns.

### Expired Icon

![Expired icon](../media/expired.jpg) The icon with the black X represents an expired software update. You can also identify expired software updates by viewing the **Expired** column for the software update when it displays in the Configuration Manager console.

**Description:**

Expired software updates were previously deployable to client computers, but once a software update is expired, new deployments can no longer be created for the software updates. Expired software updates are removed from active deployments and will no longer be made available to clients.

**Operational Concerns:**

There are no operational concerns.

### Superseded Icon

![Superseded icon](../media/superseded.jpg) The icon with the yellow star represents a superseded software update. You can also identify superseded software updates by viewing the **Superseded** column for the software update when it displays in the Configuration Manager console.

**Description:**

Superseded software updates have been replaced with newer versions of the software update. Typically, a software update that supersedes another software update does one or more of the following things:

- Enhances, improves, or adds to the fix provided by one or more previously released software updates.
- Improves the efficiency of its software update file package, which clients install if the software update is approved for installation. For example, the superseded software update might contain files that are no longer relevant to the fix or to the operating systems now supported by the new software update, so those files aren't included in the superseding software update's file package.
- Updates newer versions of a product, or in other words, is no longer applicable to older versions or configurations of a product. Software updates can also supersede other software updates if modifications have been made to expand language support. For example, a later revision of a product update for Microsoft 365 Apps might remove support for an older operating system, but add additional support for new languages in the initial software update release.

    On the Supersedence Rules tab in the Software Update Point Component properties, you can specify how to manage superseded software updates. For more information, see [Supersedence rules](../plan-design/plan-for-software-updates#BKMK_SupersedenceRules).

    **Operational Concerns:** Configuration Manager can [automatically expire superseded updates](../get-started/install-a-software-update-point#supersedence-rules) based on a schedule you choose. The default setting is to wait 3 months before expiring a superseded update. The 3 month default is to give you time to verify the update is no longer needed by any of your client computers. It's recommended that you don't assume that superseded updates should be immediately expired in favor of the new, superseding update. You can display a list of the software updates that supersede the software update on the **Supersedence Information** tab in the software update properties.

### Invalid Icon

![Invalid icon](../media/invalid.jpg) The icon with the red X represents an invalid software update.

**Description:**

Invalid software updates are in an active deployment, but for some reason the content (software update files) isn't available. The following are scenarios in which this state can occur:

- You successfully deploy the software update, but the software update file is removed from the deployment package and is no longer available.
- You create a software update deployment at a site and the deployment object is successfully replicated to a child site, but the deployment package hasn't successfully replicated to the child site.

    **Operational Concerns:**

    When the content is missing for a software update, clients are unable to install the software update until the content becomes available on a distribution point. You can redistribute the content to distribution points by using the **Redistribute** action. When content is missing for a software update in a deployment created at a parent site, the software update must be replicated or redistributed to the child site. For more information about content redistribution, see [Manage the content you've distributed](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_manage).

### Metadata-Only Icon

![Metadata-only icon](../media/metadataonly.png) The icon with the blue arrow represents a metadata-only software update.

**Description:**

Metadata-only software updates are available in the Configuration Manager console for reporting. You can't deploy or download metadata-only software updates because a software update file isn't associated with the software updates metadata.

**Operational Concerns:**

Metadata-only software updates are available for reporting purposes and aren't intended for software update deployment.

## Icons for Software Update Groups

Software update groups are represented by one of the following icons.

### Normal Icon

![Software Update Groups - Normal icon](../media/normal.jpg) The icon with the green arrow represents a software update group that contains only normal software updates.

**Operational Concerns:**

There are no operational concerns.

### Expired Icon

![Software Update Groups - Expired icon](../media/expired.jpg) The icon with the black X represents a software update group that contains one or more expired software updates.

**Operational Concerns:**

Remove or replace expired software updates in the software update group when possible.

### Superseded Icon

![Software Update Groups - Superseded icon](../media/superseded.jpg) The icon with the yellow star represents a software update group that contains one or more superseded software updates.

**Operational Concerns:**

Replace the superseded software update in the software update group with the superseding software update when possible.

### Invalid Icon

![Software Update Groups - Invalid icon](../media/invalid.jpg) The icon with the red X represents a software update group that contains one or more invalid software updates.

**Operational Concerns:**

When the content is missing for a software update, clients are unable to install the software update until the content becomes available on a distribution point. You can redistribute the content to distribution points by using the **Redistribute** action. When content is missing for a software update in a deployment created at a parent site, the software update needs to be replicated or redistributed to the child site. For more information about content redistribution, see [Manage the content you've distributed](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_manage).