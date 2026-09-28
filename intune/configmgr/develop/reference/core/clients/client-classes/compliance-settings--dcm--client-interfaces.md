---
layout: Conceptual
title: Compliance Settings Client Interfaces - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces
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
description: Learn about the configuration management COM automation classes and related types used by client applications to manage configuration items on the client computer.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 843ae7cb-2ad3-4aa2-804c-9b9eb49789c6
document_version_independent_id: 151b54ae-a8b7-fd05-fa33-c4cb4a070336
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: c0f4edf8-c246-24e0-bf00-7d50d3f57dc1
---

# Compliance Settings Client Interfaces - Configuration Manager | Microsoft Learn

In Configuration Manager, the desired configuration management COM automation classes and related types are used by client applications to manage configuration items on the client computer. They concern client-side behavior only and are called externally by the Desired Configuration Management Agent, which is enabled by default on the client computer. For more information about the agent, see [Enable or disable the compliance settings agent](../../../../compliance/how-to-enable-or-disable-the-compliance-settings--dcm--agent).

Before the Desired Configuration Management Client Agent can call the desired configuration management client COM automation objects in your application, Configuration Manager must send a policy to the client computers for the site. The policy requests desired configuration management components to be enabled. The Desired Configuration Management Client Agent properties are site-wide client settings.

When the policy is received, the Desired Configuration Management Agent can call the COM automation objects in the client application to handle configuration items as needed. For example, the agent calls an [IDCMSDK Interface](idcmsdk-interface) object to access and query baseline configuration items.

For more information about developing applications by using the desired configuration management client COM automation classes, see [Configuration Manager Development Environment](../../../../core/reqs/about-configuration-manager-sdk-requirements).

| Term | Definition |
| --- | --- |
| [ICIINFO Interface](iciinfo-interface) | Represents the properties of a baseline configuration item in a Desired Configuration Management Agent job in the client data store. |
| [IDCMAgentCallback Interface](idcmagentcallback-interface) | Represents the callback for the Desired Configuration Management Agent. |
| [IDCMSDK Interface](idcmsdk-interface) | Represents the Desired Configuration Management SDK and defines methods that are used to handle baseline configuration items. |
| [CIDetectInfo Structure](cidetectinfo-structure) | Contains information for baseline configuration item detection. |
| [CIPackageInfo Structure](cipackageinfo-structure) | Contains package information for a configuration item. |
| [CIEvalState Enumeration](cievalstate-enumeration) | Defines configuration item evaluation states. |
| [CIJobState Enumeration](cijobstate-enumeration) | Defines configuration item agent job states. |
| [CIPresence Enumeration](cipresence-enumeration) | Defines configuration item presence types used in the discovery process. |