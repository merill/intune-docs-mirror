---
layout: Conceptual
title: Set up automatic enrollment in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/windows/quickstart-automatic-mdm
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: maholdaa
ms.subservice: enrollment
description: Enable Intune automatic enrollment of Windows devices that join or register with your Microsoft Entra ID.
services: microsoft-intune
ms.topic: how-to
ms.date: 2026-01-27T00:00:00.0000000Z
locale: en-us
document_id: 0510b1ae-dbc5-242e-575c-15085a232f5d
document_version_independent_id: 0510b1ae-dbc5-242e-575c-15085a232f5d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/windows/quickstart-automatic-mdm.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/windows/quickstart-automatic-mdm
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/windows/quickstart-automatic-mdm.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 6b5c11e0-6cf1-1710-e6c4-eaeedd14e459
---

# Set up automatic enrollment in Intune - Microsoft Intune | Microsoft Learn

In this article, you set up Microsoft Intune to automatically enroll Windows corporate-owned devices, and user-owned devices for bring-your-own-device (BYOD) deployments. You can scope automatic enrollment to some Microsoft Entra users, all users, or no users.

This article is [part of an Evaluate and Try series](../../fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../../fundamentals/free-trial-sign-up).
> - [Microsoft Entra ID P1 or P2](/en-us/azure/active-directory/active-directory-get-started-premium) or the [Premium trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845). You can activate a free Premium trial subscription during setup.
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)** Microsoft Entra role
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To complete this step, you must:
> 
> - [Create a user](../../fundamentals/tenant-administration/quickstart-create-user).
> - [Create a group](../../fundamentals/tenant-administration/quickstart-create-group).
> 

## Set up automatic enrollment

In this example, you configure Microsoft Intune mobile device management (MDM) enrollment settings so that corporate-owned and personal devices automatically enroll in Microsoft Intune. *MDM user scope* enables automatic enrollment for Microsoft Intune device management.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Enrollment**.
2. Go to the **Windows** tab. Then select **Automatic Enrollment**.

    Important

    Automatic MDM enrollment is a premium Microsoft Entra feature available for Microsoft Entra ID Premium subscribers. If you can't see the automatic enrollment settings, select **Automatic MDM enrollment is available only for Microsoft Entra ID Premium subscribers** to activate a free trial.
3. Select **Microsoft Intune**.
4. Configure the MDM and WIP user scope.

    1. For **MDM user scope** select **All**. Or you can select **Some** and select **Contoso Testers** as the group. Make sure users aren't members of a group targeted by the WIP user scope.
    2. For **WIP user scope**, select **None**. You're only setting up automatic enrollment for mobile device management.
5. Use the default values for the remaining settings on the page.
6. Choose **Save**.

Important

If you configure both user scope types for the same user:

- The MDM user scope takes precedence if they're on a corporate-owned device. The device automatically enrolls in Microsoft Intune when they set it up for work.
- The WIP user scope takes precedence if they bring their own device. The device doesn't enroll in Microsoft Intune for device management. Microsoft Purview Information Protection policies are applied if you configured them.

## Clean up resources

To reconfigure Intune automatic enrollment, see [Set up enrollment for Windows devices](enable-automatic-mdm).