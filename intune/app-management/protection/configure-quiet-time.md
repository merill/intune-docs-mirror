---
layout: Conceptual
title: Create Quiet Time Policies in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/configure-quiet-time
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection: 
ms.subservice: apps
description: Learn how to create quiet time policies for iOS/iPadOS and Android apps.
ms.date: 2026-04-29T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: cdemello
locale: en-us
document_id: 2416c2bb-a11a-8370-6e29-209f50f881fa
document_version_independent_id: 2416c2bb-a11a-8370-6e29-209f50f881fa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/configure-quiet-time.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/configure-quiet-time
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/configure-quiet-time.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/3e34b70d-bca0-4369-a01b-71d1edfd427b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8ca32b3f-fa14-46df-b09a-9c4a591d6396
platformId: d3226f04-e0ee-9a26-9b78-cb4cf1b9cd86
---

# Create Quiet Time Policies in Microsoft Intune - Microsoft Intune | Microsoft Learn

The global quiet time settings allow you to create policies to schedule quiet time for your end users. These settings automatically mute Microsoft Outlook email and Teams notifications on iOS/iPadOS and Android platforms. These policies can be used to limit end user notifications received after work hours.

Important

Quiet time policies are not supported in sovereign cloud environments, including US Government Community Cloud (GCC), GCC High, Department of Defense (DoD), and Microsoft Azure operated by 21Vianet.

## Quiet time policy types

There are three quiet time policy types available. The following table describes each policy type.

| Policy Type | Description |
| --- | --- |
| Date Range | Select this option to automatically mute Microsoft Outlook email and Teams notifications on iOS/iPadOS and Android platforms during the specified range. |
| Days of the week | Select this option to automatically mute Microsoft Outlook email and Teams notifications on iOS/iPadOS and Android platforms during certain hours or all day on selected days of the week. |
| Non-working time | Select this option to automatically mute Microsoft Teams notifications on iOS/iPadOS and Android platforms when the managed account is in non-working time.<br>**Note**: This setting must only be configured if the tenant has been integrated with the **Working Time API**. For more information on integrating with the **Working Time API**, see [Limit access to Microsoft Teams when frontline workers are off shift](/en-us/microsoft-365/frontline/flw-working-time). Configuring this setting without integrating with the Working Time API could result in accounts missing Teams app notifications due to missing working time status for the managed account. |

## Create an iOS/iPadOS and Android quiet time policy

To create a quiet time policy, use the following steps:

1. Sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Quiet Time** &gt; **Policies**.
3. Select **Create policy**.
4. Select **Policy Type**. You can choose the **Date Range** or the **Days of the week** policy types. For more information, see, Quiet time policy types.
5. Select **Create** to display the **Basics** page.
6. On the **Basics** page, add a **Name** and optional **Description** for the quiet time policy. The **Platform** value is prepopulated with “Android; iOS/iPadOS.”Select **Next** to display the **Configuration settings** page.
7. On the **Configuration settings** page, select how you want to apply quiet time settings. Each type of Quiet Time policy has different configuration values. For more information, see Quiet time policy configuration settings.Select **Next** to display the **Scope tags** page.
8. The **Scope tags** page allows you to optionally add scope tags for the app. For more information, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).Select **Next** to display the **Assignments** page.
9. The **Assignments** page allows you to assign the app protection policy to groups of users. You must apply the policy to a group of users to have the policy take effect.Select **Next** to display the **Review + create** page.
10. The **Review + create** page allows you to review the values and settings you entered for this quiet time policy.
11. When you're ready, click **Create** to create the quiet time policy in Intune.

## Change existing quiet time policies

You can edit an existing quiet time policy and apply it to the targeted users. However, when you change existing policies, users won't see the changes for a 24-hour period.

To change the list of user groups, use the following steps:

1. In the **Quiet Time** &gt; **Policies** pane, select the policy you want to change.
2. Next to the section titled **Assignments**, select **Edit**.
3. To add a new user group to the policy, under the **Included groups** section, choose **Add groups**. Then, find and select the user group. Choose **Select** to add the group.
4. To exclude a user group, under the **Excluded groups** section, choose **Add groups**. Then, find and select the user group.Choose **Select** to exclude the user group.
5. To delete groups that were previously added, in either the **Included groups** or **Excluded groups** section, select **Remove**.
6. Select **Review + save** to review the user groups selected for this policy.
7. After your changes to the assignments are ready, select **Save** to save the configuration and deploy the policy to the new set of users. If you select **Cancel** before you save your configuration, you'll discard all changes you have made to the **Included groups** and **Excluded groups** sections.

To change policy configuration settings, use the following steps:

1. In the **Quiet Time** &gt; **Policies** pane, select the policy you want to change.
2. Next to the section titled **Configuration settings**, select **Edit**. Then change the settings to new values.
3. Select **Review + save** to review the updated settings for this policy.
4. Select **Save** to save your changes. If you select **Cancel** before you save your configuration, you'll discard all changes you have made to the Configuration settings pane.

## Quiet time policy configuration settings

### Date Range policy

The **Date Range** policy has a **Range Settings** configuration section.

**Range Settings** section:

| Policy setting | Description |
| --- | --- |
| Start | Specify **Start** date and time to mute notifications. |
| End | Specify **End** date and time to mute notifications. |

![Screenshot of the Microsoft Intune quiet time - Configure Date Range policy](media/configure-quiet-time/apps-quiet-time-policies-01.png)

### Days of week policy

The **Days of week** policy has the **Allday**, **Certain Hours**, and **End User Overrides** configuration settings sections.

**Allday** section:

| Policy setting | Description |
| --- | --- |
| Mute notifications all day | Set to **Require** to enable muting notifications for a full 24 hours on specific days of the week. |
| Days of the week | Set to **Configured** and then select one or more days of the week that notifications must be muted for a full 24 hours. |

**Certain Hours** section:

| Policy setting | Description |
| --- | --- |
| Mute notifications daily | Set to **Require** to enable muting notifications for certain hours on specific days of the week. |
| Start time | Set the start time for muting notifications for certain hours on specific days of the week. |
| End time | Set the end time for muting notifications for certain hours on specific days of the week. |
| Days of the week | Set to **Configured** and then select one or more days of the week that notifications must be muted for certain hours. |

**End User Overrides** section:

| Policy setting | Description |
| --- | --- |
| Allow user to change settings | Select **Yes** to allow end users to make changes to this setting by editing their global quiet time settings. Select **No** to disallow end users from changing this setting by editing their global quiet time settings. |

![Screenshot of the Microsoft Intune quiet time - Configure days of the week policy](media/configure-quiet-time/apps-quiet-time-policies-02.png)