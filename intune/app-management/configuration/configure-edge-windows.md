---
layout: Conceptual
title: Configure Microsoft Edge for Windows with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-edge-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Windows
ms.subservice: apps
description: Use Intune configuration policies with Edge for Windows to ensure corporate websites are always accessed with safeguards in place.
ms.date: 2024-08-08T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: demerson
locale: en-us
document_id: ab768b84-b8e0-7d18-e194-bb902509c3bf
document_version_independent_id: ab768b84-b8e0-7d18-e194-bb902509c3bf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/configuration/configure-edge-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/configuration/configure-edge-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/configuration/configure-edge-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 30e74378-90f8-870b-e7d0-7326dd671733
---

# Configure Microsoft Edge for Windows with Intune - Microsoft Intune | Microsoft Learn

Edge for Windows is designed to enable users to browse the web and supports multi-identity. Users can add a work account, as well as a personal account, for browsing. There is complete separation between the two identities, which is also offered in other Microsoft mobile apps.

This feature applies to:

- Applies to Windows 11 22H2

Note

Edge for Windows doesn't consume settings that users set for the native browser on their devices, because Edge for Windows can't access these settings.

The richest and broadest protection capabilities for Microsoft 365 data are available when you subscribe to the Enterprise Mobility + Security suite, which includes Microsoft Intune and Microsoft Entra ID P1 or P2 features.

## Add an app configuration policy for Edge as a managed app on Windows devices

To create a **Managed apps** app configuration policy for Microsoft Edge on Windows, see [Add an app configuration policy for managed apps on Windows devices](configure-managed-apps#add-an-app-configuration-policy-for-managed-apps-on-windows-devices). Select the **Microsoft Edge for Windows** application when creating the app configuration policy. After the configuration is created, you can assign the policy to groups of users.

Note

For more information about policies for Microsoft Edge for Windows, see [Microsoft Edge - Policies](/en-us/deployedge/microsoft-edge-policies).