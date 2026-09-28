---
layout: Conceptual
title: About Compliance Settings Extensibility - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-compliance-settings--dcm--extensibility
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
description: The content in this section provides information about extending the functionality of desired configuration management configuration items in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 59cacd8e-fc9c-4408-6164-0b8080f18331
document_version_independent_id: fc7e224f-2745-3ea8-c54f-9b50a9538df2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/about-compliance-settings--dcm--extensibility.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/about-compliance-settings--dcm--extensibility
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/about-compliance-settings--dcm--extensibility.md
cmProducts: []
platformId: 61ba015f-b8bb-74d8-9ea0-349e1f6236f8
---

# About Compliance Settings Extensibility - Configuration Manager | Microsoft Learn

The content in this section provides information about extending the functionality of desired configuration management configuration items in Configuration Manager.

In application configuration items, it's possible to detect applications or settings by using a script.

If the script returns a non-zero exit code, the result is a discovery failure.

If the script returns a zero exit code, the script output is evaluated.

It's the echoed output of a script that is detected and evaluated. For example:

- No echoed output equals no instances detected.
- "n" lines of output equals "n" instances detected.

    In there's an application detection, two lines of output would indicate that two instances of the application are detected.

    If there's a settings detection, no lines of output would indicate that no instances of the setting are detected.

    In all cases, the evaluation of the script output is determined by the rule.

Note

In the case of settings detection, the script output is cast to the type of setting being detected. If the cast of the script output fails, a discovery failure is returned. For example, a script that reads and returns registry values, passes a set of values back to the rule; however, one value is a string (1, 2, x). If the rule is expecting only integer values back, it will cast all of the values to integers, causing a failure. In this case, the rule returns an evaluation failure.