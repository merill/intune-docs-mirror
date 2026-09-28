---
layout: Conceptual
title: Download definitions from a network share - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-definitions-network
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
description: Learn how to manually download the latest definition updates from Microsoft and then configure clients to download these definitions.
ms.date: 2019-11-18T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 35ca8119-89b6-165d-b576-72b45b296986
document_version_independent_id: 38916d46-6603-1d85-1200-1ee95eb43d26
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-definitions-network.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-definitions-network
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-definitions-network.md
cmProducts: []
platformId: fd1d5fb1-97c4-47c0-76f0-426f2d39e8fb
---

# Download definitions from a network share - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can manually download the latest definition updates from Microsoft and then configure clients to download these definitions from a shared folder on the network. Users can also initiate definition updates when you use this update source.

Note

Clients must have read access to the shared folder to be able to download definition updates.

For more information about how to download the definition and engine updates to store on the file share, see [Install the latest Microsoft antimalware and antispyware software](https://www.microsoft.com/wdsi/definitions).

## To configure definition downloads from a file share

1. In the Configuration Manager console, click **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, expand **Endpoint Protection**, and then click **Antimalware Policies**.
3. Open the properties page of the **Default Antimalware Policy** or create a new antimalware policy. For more information about how to create antimalware policies, see [How to create and deploy antimalware policies for Endpoint Protection](endpoint-antimalware-policies).
4. In the **Security Intelligence updates** section of the antimalware properties dialog box, click **Set Source**.

    - The **Definition updates** section was renamed to **Security Intelligence updates** starting in Configuration Manager version 1902.
5. In the **Configure Definition Update Sources** dialog box, select **Updates from UNC file shares**.
6. Click **OK** to close the **Configure Definition Update Sources** dialog box.
7. Click **Set Paths**. Then, in the **Configure Definition Update UNC Paths** dialog box, add one or more UNC paths to the location of the definition updates files on a network share.
8. Click **OK** to close the **Configure Definition Update UNC Paths** dialog box.

[Next step &gt;](endpoint-antimalware-policies)

[Back &gt;](endpoint-configure-alerts)