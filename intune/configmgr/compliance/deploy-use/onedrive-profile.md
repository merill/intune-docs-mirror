---
layout: Conceptual
title: OneDrive for Business Profiles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/deploy-use/onedrive-profile
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
description: Redirect Windows known folders to OneDrive for Business using a OneDrive for Business profile in Configuration Manager.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: c5453486-e657-0e95-f0cf-73c06928ed40
document_version_independent_id: 7e9fe802-25b6-c3c1-2257-7f5003a4f3d7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/deploy-use/onedrive-profile.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/deploy-use/onedrive-profile
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/deploy-use/onedrive-profile.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7428317a-e6c2-4461-ad3e-8a8ad3608734
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e4f59707-f107-48f2-8d75-0afd91868cd7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7643bda6-7ece-af67-6c74-e1ca23f26a6b
---

# OneDrive for Business Profiles - Configuration Manager | Microsoft Learn

Starting in Configuration Manager version 1902, you can create OneDrive for Business Profiles for moving Windows known folders to OneDrive for Business. These folders include Desktop, Documents, and Pictures. In each profile, you can specify settings for moving the Windows known folders. For more information on OneDrive for Business, see [Redirect and move Windows known folders to OneDrive](/en-us/onedrive/redirect-known-folders). 

## Prerequisites

- [Find your Microsoft 365 tenant ID](/en-us/onedrive/find-your-office-365-tenant-id)
- Deploy the OneDrive sync client version 18.111.0603.0004 or later. For more information, see [Deploy OneDrive apps by using Configuration Manager](/en-us/onedrive/deploy-on-windows).

## Move Windows known folders to OneDrive

Use Configuration Manager to move Windows known folders to OneDrive for Business. These folders include Desktop, Documents, and Pictures. To simplify your Windows upgrades, deploy these settings to Windows 7 clients before deploying a task sequence.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Compliance Settings**, and select the **OneDrive for Business Profiles** node.

    ![OneDrive for Business Profiles node](media/onedrive-for-business-profiles-node.png)
2. In the ribbon, select **Create OneDrive for Business Profile**.
3. Specify a name to identify this policy, and select **Next**.
4. Select the platforms that will be provisioned with the OneDrive for Business profile. When you're finished selecting the platforms, click **Next**.

    ![Select platforms for the OneDrive for Business profile](media/onedrive-for-business-profile-select-platforms.png)
5. On the **Settings** page:

    1. Specify your Microsoft 365 tenant ID.
    2. Select one of the following options to move the known folders to OneDrive:

        - **Prompt users to move Windows known folders to OneDrive**: With this option, the user sees a wizard to move their files. If they choose to postpone or decline moving their folders, OneDrive periodically reminds them.
        - **Silently move Windows known folders to OneDrive**: When this policy applies to the device, the OneDrive client automatically redirects the known folders to OneDrive for Business.

            - **Show notification to users after folders have been redirected**: If you enable this option, the OneDrive client notifies the user after it moves their folders.
    3. **Prevent users from redirecting their Windows known folders back to their PC**: Disables the option in OneDrive for Business on the client for users to move these folders back to the device.

        ![OneDrive for Business Known Folder Move Settings](media/onedrive-for-business-profile-move-folder-settings.png)
6. Complete the wizard, then deploy the policy.

## Deploy the OneDrive for Business Profile

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Compliance Settings**, and select the **OneDrive for Business Profiles** node.
2. Select the profile, then select **Deploy** in the ribbon.
3. Specify the following settings for your deployment:

    1. **Collection**: Click **Browse...**, then select the collection for which you want to deploy the profile.
    2. **Generate an alert**:

        - **When compliance is below**: Minimum percentage of client compliance to maintain otherwise an alert is generated.
        - **Date and time**: The date alerts first start being generated based on profile compliance.
        - **Generate System Center Operations Manager alert**: Send a compliance alert to System Center Operations Manager.
    3. **Schedule**:

        - **Simple schedule**: By default, this setting uses a simple schedule to start the compliance evaluation every seven days.
        - **Custom schedule**: Define when to run the compliance evaluation. The start time is based on the local time for the computer that runs the Configuration Manager console at the time you create the schedule or you can use UTC.

        ![Deploy OneDrive for Business profile](media/onedrive-for-business-deploy-profile.png)
4. Click **OK** to deploy the OneDrive for Business profile.