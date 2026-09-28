---
layout: Conceptual
title: Guided Update Supersedence for Enterprise App Management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/update-enterprise-supersedence
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_EAM
ms.reviewer: nicolezhao
ms.subservice: apps
description: Learn how to update an Enterprise App Catalog app using supersedence with Microsoft Intune.
ms.date: 2025-11-06T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 
locale: en-us
document_id: 34d8a83f-8e3b-3f0f-d911-a5b6275915d9
document_version_independent_id: 34d8a83f-8e3b-3f0f-d911-a5b6275915d9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/update-enterprise-supersedence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/update-enterprise-supersedence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/update-enterprise-supersedence.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
platformId: a3414d05-c576-a7f2-69ea-20327bb2bf71
---

# Guided Update Supersedence for Enterprise App Management - Microsoft Intune | Microsoft Learn

Guided update supersedence for Enterprise App Management allows you to check for updates of Windows (Win32) Enterprise App Catalog apps. You can view an available update for the app and select the option to create a new app with a supersedence relationship for the app it’s updating. Prepopulated attributes are provided when creating the new app.

## View available updates

In the **Overview** pane for a selected Enterprise App Catalog app, you can view the available updates by selecting the tile **Enterprise App Catalog apps with available updates**.

Note

Microsoft has established Service Level Objectives (SLOs) for app update availability. Most app updates are available within 24 hours of vendor release, while those requiring manual validation typically become available within seven days. For details, see [Enterprise App Management overview](enterprise-app-management).

The **Enterprise App Catalog apps with updates** pane provides a list of Enterprise App Catalog apps that can be updated. This list provides the following app details:

- **App name**: - The name of the app.
- **Publisher**: - The publisher of the app.
- **Provisioned version**: - The currently installed app version.
- **Latest available version**: - The new version that is available.

[![Screenshot the Enterprise App Catalog app list with available updates.](media/update-enterprise-supersedence/apps-eam-supersedence-02.png)](media/update-enterprise-supersedence/apps-eam-supersedence-02.png#lightbox)

## Update an Enterprise App Catalog app

1. To update an Enterprise App Catalog app, select the *app name* to display additional options.

    You can update a specific app. This option allows you to update the app with a newer app version. Intune uses information from the Enterprise App Catalog to define properties and settings. You can review and define custom settings as needed. You should consider downloading and exporting the properties of the app before updated.

    Superseding an app creates a new app with the latest app package and sets up the supersedence relationship. Some settings, such as scope tags and assignments won't be copied to the new app.
2. Select the **Update** option for the specific app. The **Update application** pane is displayed.

    [![Screenshot an Enterprise App Catalog app list the supersedence option.](media/update-enterprise-supersedence/apps-eam-supersedence-04.png)](media/update-enterprise-supersedence/apps-eam-supersedence-04.png#lightbox)
3. Select **Supersede app**.
4. Select your app **Assignments**, then **Review + create** the superseded app.