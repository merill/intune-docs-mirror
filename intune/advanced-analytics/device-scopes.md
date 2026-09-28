---
layout: Conceptual
title: Device Scopes - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/advanced-analytics/device-scopes
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: suite
description: Learn how to use device scopes in Microsoft Intune with scope tags for custom device reporting and targeted insights.
ms.date: 2026-03-24T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 5e046374-2889-4c7c-560d-093e7f56afdb
document_version_independent_id: 5e046374-2889-4c7c-560d-093e7f56afdb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/advanced-analytics/device-scopes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: advanced-analytics/device-scopes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/advanced-analytics/device-scopes.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d5594e5c-6077-6524-72c7-44c8fc5ac37c
---

# Device Scopes - Microsoft Intune | Microsoft Learn

Device scopes use scope tags to filter endpoint analytics reports to a subset of devices, allowing you to see scores, insights, and recommendations for a specific subset of devices.

Device scopes are supported on the following endpoint analytics reports:

- [Startup performance](../endpoint-analytics/startup-performance)
- [Work from anywhere](../endpoint-analytics/work-from-anywhere)
- [Application reliability](../endpoint-analytics/app-reliability)
- [Battery health](battery-health)

## Before you begin

- Confirm that your environment meets all [prerequisites](./#prerequisites).

Additional prerequisites for custom device scopes:

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To create custom device scopes, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Endpoint Security Manager](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Read Only Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#read-only-operator)
> - [Intune Role Administrator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#intune-role-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Roles/Read**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 
> 
> Note
> 
> After custom device scopes are created, other users with access to endpoint analytics can use them. Only the user who created the custom device scopes or a Global Administrator can delete the custom device scopes.

## Create and manage custom device scopes

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), open one of the reports within endpoint analytics, for example startup performance. Select **Reports** &gt; **Endpoint analytics** &gt; **Startup performance**.
2. Select **Device scope**.
3. Select **Manage device scopes** to open the flyout where you can create and modify your custom device scopes.

To create custom device scopes:

1. Open the **Manage device scopes**.
2. Select a scope tag from the dropdown and select **Save**.
3. Give the new custom device scope a name and select **OK**.

The new custom device scope appears in your list of saved device scopes. By default, custom devices scopes are in the *Off* state. To activate custom device scopes, toggle the **State** setting to *On*. Data processing starts for the selected device scope.

Note

Once activated, custom device scopes can take up to 24 hours to process. During this period, custom device scopes that are still processing are not usable. Additionally, custom device scopes require 10 devices at minimum to populate supported reports. Otherwise **Insufficient Data** might show when trying to select a custom scope.

To delete custom device scopes:

1. Open the **Manage device scopes** menu.
2. Find the custom device scope you would like to delete and select the menu.
3. Select **Delete**.
4. Select **Yes** to confirm.

Important

If a custom device scope is associated with a Scope tag that gets deleted from your tenant, the custom device scope will no longer function. You see an error message in the **Manage device scopes** menu. Edit the impacted device scope to use a valid Scope tag or delete it to clear the error.

## Use custom device scopes

Custom device scopes can be used in any supported endpoint analytics report. To use a custom device scope:

1. Ensure that the device scope you would like to use is active.
2. Navigate to a supported report in endpoint analytics, such as **Startup performance**.
3. Select **Device scope** menu in the page.
4. From the dropdown menu, select your desired custom device scope.
5. Select **Apply**.

The page is automatically updated to show scores, data, and insights specific to the subset of devices defined by your chosen custom device scope. As you navigate through endpoint analytics, your chosen device scope remains selected on all supported reports and pages.

To return to viewing all devices, navigate to the **Device scope** menu, select **All Devices** from the dropdown menu, and select **Apply**.

## Limitations

- You can save up to 100 custom device scopes, and up to 20 can be active at a time.
- Only one Scope tag can be used to create a custom device scope. To create a custom device scope that includes devices from multiple Scope tags, you must create a new Scope tag and assign it to the full set of devices that you require.