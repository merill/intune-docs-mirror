---
layout: Conceptual
title: Unique Identifier Value for a Resource - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/about-the-unique-identifier-value-for-a-resource
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
description: An optional property that reports inventory data for a resource.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 7078d92d-78da-c450-92c0-80032997c897
document_version_independent_id: 28e0ef06-6abe-db7f-2c19-8b9cc846c3ee
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/about-the-unique-identifier-value-for-a-resource.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/about-the-unique-identifier-value-for-a-resource
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/about-the-unique-identifier-value-for-a-resource.md
cmProducts: []
platformId: 4c84444c-db7c-6d30-31e3-04a094d32f1c
---

# Unique Identifier Value for a Resource - Configuration Manager | Microsoft Learn

In Configuration Manager, the Configuration Manager unique identifier property for a new resource class is optional. If you report inventory data for the resource, you must include this property. The Configuration Manager unique identifier value must be unique — it relates your resource discovery data to your inventory data (SMS\_G\_xxx). Typically, hardware resources use a GUID to uniquely identify individual resources.

The format of the Configuration Manager unique identifier value is as follows.

```
<ID Type>:<ID Value>
```

For example, Configuration Manager uses a GUID to identify Configuration Manager clients.

```
GUID:4976DCD4-CAAE-11D2-8E00-00104BCC3648
```

You can use any &lt;ID Type&gt; and &lt;ID Value&gt; values to identify a new resource. However, when discovering data for an existing resource type, you should follow the convention that is used by that resource type.