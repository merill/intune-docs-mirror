---
layout: Conceptual
title: Find a Console Node GUID - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid
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
description: Learn how to determine the correct Globally Unique Identifiers (GUIDs) for a Configuration Manager console node.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8a825af9-8b5b-b6ba-0c80-31587b899ead
document_version_independent_id: 150447cf-f45e-3f07-f724-d1b2712589a8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4628cbd9-6f47-4ae1-b371-d34636609eaf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/be21deb8-8c64-44b0-b71f-2dc56ca7364f
platformId: d1170155-0953-d7b0-763b-3242cdfa6741
---

# Find a Console Node GUID - Configuration Manager | Microsoft Learn

Globally Unique Identifiers (GUIDs) are used to identify parts of the Configuration Manager console. For example, the action you create in [How to Create a Configuration Manager Action](how-to-create-a-configuration-manager-action) is placed on the **Site Configuration** node in the console tree view by using the GUID 9770fc1b-0885-40e7-8a83-5dfc5eaaa8c2.

Elements that contain the `namespaceGuid` attribute are part of the console. For example, the following element declares the software updates node:

`<RootNodeDescription NamespaceGuid="392b72f3-1c83-42e1-90ed-611798bc0dd0" Id="SmsSoftwareUpdatesNode" DisplayName="SUMName" Description="SUMDescription" HelpTopic="9af099dc-3713-463d-bd50-0e4cd07c48fb">`

Determining the correct GUID for your Configuration Manager console extension to use can be difficult because you must navigate through console root XML files to the correct element.

One approach is to open any of the console root XML files in Visual Studio and collapse all the XML nodes. After the XML is collapsed, expand `ConsoleNodesRootDescription` and then `RootNodeDescription`.

`RootNodeDescription` contains further `RootNodeDescription` elements for each of the major Configuration Manager features displayed in the Configuration Manager console tree view. By expanding these nodes, you can navigate to the required part of the Configuration Manager console and get the GUID from the appropriate XML element.

Namespace GUIDs can be associated with several types of elements. For more information, see [Configuration Manager Console Node XML](console-node-xml).

### See also

[About console nodes](about-configuration-manager-console-nodes)[Configuration Manager Console Node XML](console-node-xml)