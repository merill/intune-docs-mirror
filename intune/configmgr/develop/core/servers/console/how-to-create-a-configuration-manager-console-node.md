---
layout: Conceptual
title: Create a Console Node - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-node
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: Learn how to create and start a configuration manager console node that displays available collections.
locale: en-us
document_id: 95d89de2-0c76-c208-6112-52691b82eeaa
document_version_independent_id: 87c19432-c99f-ba5a-e6a2-ce38275e7bfc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-node.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-node
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-node.md
cmProducts: []
platformId: 900202a5-f60c-bcf8-2c69-66a2b2298aab
---

# Create a Console Node - Configuration Manager | Microsoft Learn

In Configuration Manager, to create a Configuration Manager console node, you create an XML description of the node and add it to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\Extensions\Nodes\&lt;GUID&gt; folder. GUID is the GUID namespace for the parent node.

The following procedure shows how to add a new node to the Configuration Manager**Site Configuration** node. The new node displays the available collections.

### To create a Configuration Manager console node

1. If the Configuration Manager console is open, close it.
2. In the Configuration Manager SDK, locate the XML file, CollectionsNode.XML.
3. If it does not already exist, create a folder named Nodes in %*ProgramFiles*%\AdminConsole\XmlStorage\Extensions\.
4. In the Nodes folder, create a folder named `d61498cb-7b3f-4748-ae3e-026674fb0cbd`. This GUID identifies the **Site Configuration** node.
5. Copy the XML file to the GUID folder.
6. Start the Configuration Manager console, and in the console tree, navigate to the **Site Configuration** node. You should see a new **Collections** node.