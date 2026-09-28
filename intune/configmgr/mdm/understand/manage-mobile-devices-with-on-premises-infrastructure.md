---
layout: Conceptual
title: On-premises MDM - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure
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
description: Learn about on-premises mobile device management (MDM) in Configuration Manager
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: b770bda3-426d-60f9-4fdf-b63223c62d8a
document_version_independent_id: 9b6c2f4b-278f-f980-9625-c6b3cd9088b0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 1b773ac3-ef4f-235f-b6ea-09159f75e1f4
---

# On-premises MDM - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in November 2021, this feature of Configuration Manager is [deprecated](../../core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

Configuration Manager on-premises mobile device management (MDM) is a device management solution that relies on the built-in management capabilities of Windows. This feature is based on the Open Mobile Alliance (OMA) Device Management (DM) standard. It uses your organization's Configuration Manager infrastructure to manage and maintain the devices. Your organization requires Microsoft Intune licenses to use this feature, but it doesn't require any cloud connection. Configuration Manager stores all data about your devices in your on-premises site database.

On-premises MDM differs from Microsoft Intune, which also relies on built-in OMA DM capabilities. All of the management functions in Intune are delivered through cloud services. On-premises MDM also differs from the client-based management solution traditionally offered by Configuration Manager. It relies on similar infrastructure, but doesn't use separately installed client software on the devices it manages.

## Comparison

The following sections list the advantages and disadvantages of on-premises MDM as compared to traditional client-based management:

### Advantages

- **Simplified infrastructure**: Fewer site system roles are required.
- **Easier to maintain**: Because management functionality is built in to the device OS, new versions of the Configuration Manager client aren't required when new management features are introduced to the site.
- **On-premises**: - All management and data are kept on-premises.

### Disadvantages

**Less client management functionality**: No orchestration, software metering, third-party integration, task sequencing, or Software Center support.

- **Limited device support**: on-premises MDM doesn't support as many OS versions as the Configuration Manager client. For more information, see [Supported OS versions for clients and devices](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_OnpremOS).