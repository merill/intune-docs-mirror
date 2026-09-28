---
layout: Conceptual
title: Create and Assign an App Protection Policy - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/quickstart-create-assign-policy
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_Protect
ms.subservice: apps
description: Learn how to create and assign an app protection policy in Microsoft Intune to protect your organization's data. Get step-by-step guidance.
ms.topic: how-to
ms.date: 2026-01-20T00:00:00.0000000Z
ms.reviewer: dagerrit
locale: en-us
document_id: 39bfc432-37cb-756b-4669-96a481e387b9
document_version_independent_id: 39bfc432-37cb-756b-4669-96a481e387b9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/quickstart-create-assign-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/quickstart-create-assign-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/quickstart-create-assign-policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f58b462d-c463-52b5-9071-c9803e64272e
---

# Create and Assign an App Protection Policy - Microsoft Intune | Microsoft Learn

In this article, you learn how to create and assign an app protection policy in Microsoft Intune to protect apps on user devices. App protection policies help ensure your apps meet your organization's data protection requirements, keeping corporate data secure.

This article is [part of an Evaluate and Try series](../../fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

## Prerequisites

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - A Microsoft Intune subscription. [Sign up for a free trial account](../../fundamentals/free-trial-sign-up).
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Application Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#application-manager)** Microsoft Intune role
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To complete this step, you must:
> 
> - [Create a user](../../fundamentals/tenant-administration/quickstart-create-user).
> - [Create a group](../../fundamentals/tenant-administration/quickstart-create-group).
> - [Enroll a device](../../device-enrollment/windows/quickstart-automatic-mdm)
> - [Add and assign an app](../deployment/quickstart-add-assign).
> 

## Create an app protection policy

Use the following steps to create an app protection policy:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select **Apps** &gt; **Windows** &gt; **Create**.
2. Enter the following details:

    - **Name**: *Windows content protection*
    - **Description**: *Users associated with this policy can't cut, copy, or paste any content between the assigned app and other nonmanaged apps on the device.*
    - **Enrollment state**: *With enrollment*
3. Under **Protected apps**, select **Add**. The **Add apps** pane is displayed.
4. Choose the apps that must adhere to this policy and select **OK**.
5. Select **Next** to display the **Required settings**.
6. Select **Allow Overrides** to set the Windows Information Protection mode. Selecting this option blocks enterprise data from leaving the protected app.
7. Select **Next** to display the **Advanced settings**.
8. Select **Next** to display the **Assignments**.
9. Select **Select groups to include**, select the users group, and select **Select**.

    You can only apply app protection policies to groups that contain users, not groups that contain devices.
10. Select **Next** to display the **Review + create** step.
11. Select **Create** to create your policy.

You see the app protection policy in Intune.