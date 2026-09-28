---
layout: Conceptual
title: Manually Add the Windows Company Portal App - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-company-portal-windows
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
ms.reviewer: bryanke
ms.subservice: apps
description: Learn how your workforce can manually add the Windows Company Portal app to their PC from the Microsoft Store.
ms.date: 2026-01-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 520d1c3e-95c0-058c-8830-0c91559db004
document_version_independent_id: 520d1c3e-95c0-058c-8830-0c91559db004
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-company-portal-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-company-portal-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-company-portal-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b54e39d6-d661-694d-694b-a508b6e66010
---

# Manually Add the Windows Company Portal App - Microsoft Intune | Microsoft Learn

To manage devices and install apps, your users can install the Company Portal app themselves from the Microsoft Store. If your business needs require that you assign the Company Portal app to them, however, you can assign the Company Portal app for Windows directly from Intune.

Important

To deploy the Company Portal app for Windows Autopilot provisioned devices, see [Add Company Portal app for Windows Autopilot devices](add-company-portal-autopilot).

Note

The Company Portal supports Configuration Manager applications. This feature allows end users to see both Configuration Manager and Intune deployed applications in the Company Portal for co-managed customers. The Company Portal displays Configuration Manager deployed apps for all co-managed customers. This support helps administrators consolidate their different end user portal experiences. For more information, see [Use the Company Portal app on co-managed devices](../../configmgr/comanage/company-portal).

## Download the Company Portal app using Windows Package Manager

1. Use the [Windows Package Manager](/en-us/windows/package-manager/winget/download) command-line tool to download the Company Portal app for Windows with dependencies by entering the following command:

    ```powershell
    winget download "Company Portal" --source msstore
    ```

    By default, files are downloaded to the user's Downloads folder. Use the `--download-directory` option to specify a custom download path.
2. In the Microsoft Intune admin center, upload the Company Portal app as a new app.

    1. Go to **Apps** &gt; **Platforms** and select **Windows**.
    2. Select **Add**.
    3. For **App type**, choose **Other** &gt; **Line-of-business app**.
    4. Choose **Select** to continue.
    5. On the **App information** page, choose **Select app package file**.
    6. In the new pane, select the **File** upload button, and then upload the app package file. The file you want to select has the app package (.appxbundle) extension.
3. Detected dependencies appear. Under **Select dependency app files**, select all dependencies you downloaded in step 1.

    1. **Shift + click** to select all dependencies.
    2. Under the **Added** column, verify that **Yes** appears for the architectures you need.

    Note

    If you don't add the dependencies, installation could fail for the selected device types.
4. Select **OK**.
5. Under **App information**, enter any information about the app.
6. Select **Add**.
7. Assign the Company Portal app as a required app to selected users or device groups.

For more information about how Intune handles dependencies for Universal apps, see [Deploying an appxbundle with dependencies via Microsoft Intune MDM](/en-us/archive/blogs/configmgrdogs/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm).