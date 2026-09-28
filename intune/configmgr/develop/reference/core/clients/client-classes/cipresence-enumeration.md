---
layout: Conceptual
title: CIPresence Enumeration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipresence-enumeration
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
description: Learn how to define configuration item presence types used in the discovery process with CIPresence enumeration.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2b63f3aa-08e3-ead0-7c73-7808dbb7df54
document_version_independent_id: b78afabf-d592-4713-7955-99ffd550c249
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/cipresence-enumeration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/cipresence-enumeration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/cipresence-enumeration.md
cmProducts: []
platformId: 5b1b4bd7-e48f-2f22-ad08-ee38fa8f9dc9
---

# CIPresence Enumeration - Configuration Manager | Microsoft Learn

In Configuration Manager, the `CIPresence` enumeration defines configuration item presence types used in the discovery process.

## Syntax

```
typedef enum tagCIPresence
{
  ciNotPresent = 0,ciNonCompliant = 0,
  ciPresent = 1,ciCompliant = 1,
  ciNotApplicable = 2,
  ciPresenceUnknown = 3,ciComplianceUnknown = 3,
  ciEvaluationError = 4,
  ciNotEvaluated = 5
} CIPresence;
```

## Elements

`ciNotPresent, ciNonCompliant` Configuration item not present or not compliant.

`ciPresent, ciCompliant` Configuration item present or compliant.

`ciNotApplicable` Configuration item not applicable.

`ciPresenceUnknown, ciComplianceUnknown` Configuration item presence or compliance unknown.

`ciEvaluationError` Configuration item evaluation error.

`ciNotEvaluated` Configuration item not evaluated.

## Remarks

This enumeration is used by the [ICIINFO Interface](iciinfo-interface).