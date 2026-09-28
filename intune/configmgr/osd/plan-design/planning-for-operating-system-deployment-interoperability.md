---
layout: Conceptual
title: OS deployment interoperability - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/plan-design/planning-for-operating-system-deployment-interoperability
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
description: Understand interoperability issues when different Configuration Manager sites in a single hierarchy use different versions.
ms.date: 2021-10-01T00:00:00.0000000Z
ms.subservice: osd
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: e57764df-5212-751d-f9d4-e3b1175ef393
document_version_independent_id: 55e02d62-e61b-d22b-1bdd-f9e25c15365c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/plan-design/planning-for-operating-system-deployment-interoperability.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/plan-design/planning-for-operating-system-deployment-interoperability
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/plan-design/planning-for-operating-system-deployment-interoperability.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 963fbc65-3e1a-56d3-674b-4f200be7683a
---

# OS deployment interoperability - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When different Configuration Manager sites in a single hierarchy use different versions, some Configuration Manager functionality isn't available. Typically, functionality from the newer version of Configuration Manager isn't accessible at sites or by clients that run a lower version. For more information, see [Interoperability between different versions of Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions).

## Objects

Consider the following objects when you upgrade the top-level site in your hierarchy and other sites in your hierarchy run Configuration Manager with a lower version:

### Client installation package

- The source for the default client installation package is automatically upgraded. All distribution points in the hierarchy are updated with the new client installation package. This behavior happens even on distribution points at sites in the hierarchy that are at a lower version.
- You can't assign new version clients to sites that you haven't yet upgraded to the new version. Assignment is blocked at the management point.

### Boot images

- When you upgrade the top-level site to the latest version of Configuration Manager, it automatically updates the default boot images (x86 and x64). The update uses the version of the Windows ADK and Windows PE that you've installed. The files that are associated with the default boot images are updated with the latest Configuration Manager version of the files. The site doesn't automatically update custom boot images. You need to manually update custom boot images, which include older Windows PE versions.
- When your site hierarchy contains sites with different versions of Configuration Manager, avoid the use of dynamic media. Instead, use site-based media to contact a specific management point. After you update all sites to the same version of Configuration Manager, you can use dynamic media again.
- Verify that the latest Configuration Manager boot images include your customizations. Then update all distribution points at the new version sites with the latest version of the new boot images.

### User State Migration Tool (USMT)

When you upgrade the top-level site to the latest version of Configuration Manager, it automatically updates the default USMT package to the latest version. It doesn't automatically update any custom USMT packages. You need to manually update these packages.

### New task sequence steps

Periodically, new task sequence steps are introduced with new versions of Configuration Manager. When you deploy a task sequence with a new step to older clients, the task sequence step fails. Before you deploy a task sequence with a new step, make sure the clients in the target collection are updated to the new version.

### OS deployment media

When the site is updated to a new version, update all media with the new Configuration Manager client package. These media types include bootable, capture, prestaged, and stand-alone.

### Third-party extensions to OS deployment

When you have third-party extensions to OS deployment and you have different versions of Configuration Manager sites or Configuration Manager clients, there might be issues with the extensions.

## Latest version of Configuration Manager sites in a mixed hierarchy

When you upgrade a site to latest version of Configuration Manager, task sequences that reference the default client installation package automatically start to deploy the latest Configuration Manager client version.

Task sequences that reference a custom client installation package continue to deploy the version of the client that's contained in that custom package. Custom packages likely include an earlier version of the Configuration Manager client. To avoid task sequence deployment failures, update any custom client installation packages to the latest version.

When you configure a task sequence to use a custom client installation package, do one of the following actions:

- Update the task sequence step to use the latest Configuration Manager version of the client installation package
- Update the custom package to use the latest Configuration Manager client installation source

Important

Don't deploy a task sequence that references the latest Configuration Manager client installation package to clients in an older Configuration Manager site. When clients assigned to an older Configuration Manager site are upgraded to the latest Configuration Manager client version, Configuration Manager blocks the assignment to the older Configuration Manager site. These clients are no longer assigned to any site. Until you manually assign the client to the latest Configuration Manager site, or reinstall the older Configuration Manager version of the client on the computer, these clients are unmanaged.

## Older versions of Configuration Manager in a mixed hierarchy

When you upgrade your central administration site to the latest version of Configuration Manager, make sure that OS deployment task sequences that you deploy don't leave those clients in an unmanaged state. For example, if you deploy to clients assigned to an older Configuration Manager site that you haven't yet upgraded to the latest version of Configuration Manager.

Make a copy of a task sequence that you use to deploy to clients in the latest version of Configuration Manager site. Then modify the task sequence so you can deploy it to clients in an older Configuration Manager site. Configure the task sequence to reference a custom client installation package that uses the older Configuration Manager client installation source. If you don't already have a custom client installation package that references the older Configuration Manager client installation source, manually create one.