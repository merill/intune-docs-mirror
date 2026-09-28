---
layout: Conceptual
title: 'Device Action: Send Custom Notification - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/send-custom-notification
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.reviewer: mattcall
ms.subservice: remote-actions
zone_pivot_group_filename: device-management/actions/zone-pivot-groups.json
description: Use Intune to create and send custom notifications to users of iOS/iPadOS and Android devices.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
zone_pivot_groups: 22f7442d-9384-49c8-abff-aaa058b30589
locale: en-us
document_id: 897125f9-b527-62f2-f5f4-e0fb0f4090ba
document_version_independent_id: 897125f9-b527-62f2-f5f4-e0fb0f4090ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/send-custom-notification.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/send-custom-notification
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/send-custom-notification.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 97c211b4-7072-2eda-e0b5-a368bdc42e23
---

# Device Action: Send Custom Notification - Microsoft Intune | Microsoft Learn

Use the *send custom notification* action in Intune to deliver short messages directly to users of managed devices. Notifications appear as standard push alerts from the Company Portal or Intune app, similar to messages from other mobile applications.

You can send notifications to individual devices or to users in groups. Custom notifications are useful for general communication, such as:

- Informing users of schedule changes, like building closures due to weather.
- Sending targeted messages to individual users, such as prompting a device restart to complete an update.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This action supports the following platforms:
> 
> - Android Enterprise personally-owned work profile (BYOD)
> - iOS/iPadOS
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

::: zone pivot="android"

> 
> To use this action, make sure devices meet the following requirements:
> 
> - The Company Portal app or Microsoft Intune app is installed.
> - Push notification permissions for the apps are granted by the user.
> 
> 
> Note
> 
> Battery optimization settings on some devices can prevent notifications from being delivered. Consider disabling battery optimization for the Company Portal or Intune app to ensure reliable notification delivery.

::: zone-end

::: zone pivot="ios"

> 
> To use this action, make sure devices meet the following requirements:
> 
> - The Company Portal app is installed.
> - Push notification permissions for the app is granted by the user.
> 

::: zone-end

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Remote tasks/Send custom notifications**—to send notifications to devices
>     - The permission **Organization/Update**—to send notifications to groups
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to send custom notifications from the Intune admin center

You can send custom notifications in Intune to individual devices or to users in groups. Keep the following limitations and behaviors in mind:

- When targeting groups, notifications are sent to the users in the group—not the devices. Each supported device enrolled by the user receives the message.
- You can target up to 25 groups per notification. Nested groups don't count toward this limit.
- You can send up to 25 group-targeted notifications per hour. This limit applies at the tenant level.
- When sending to individual devices, you can send up to 10 notifications per hour to the same device.
- Intune doesn't store previously sent notification text. To resend a message, you must recreate it.
- Intune doesn't track sent custom notifications, and devices don't log receipt outside of the device's notification center. The notification might appear in a temporary diagnostic log if the user requests support through the Company Portal or Intune app.

::: zone pivot="android"

Caution

Other apps might have access to the data in your custom notifications. Avoid using them for sensitive communications.

::: zone-end

### Send a custom notification to a single device

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) &gt; [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Send Custom Notification**.
4. On the **Send Custom Notification**pane, specify the following message details:
    - **Title**: Specify a title for this notification. Titles are limited to 50 characters.
    - **Body**: Specify the message. Messages are limited to 500 characters.
5. Select **Send** to send the custom notification to the device. Unlike notifications you send to groups, you don't configure an assignment or review the message before sending it.

Intune processes the message immediately. The only confirmation is a notification in the admin center showing the message content.

### Send a custom notification to a group

Group notifications target users, not devices. Each supported device enrolled by the user receives the message. Devices that are member of the group are ignored.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Custom notifications**.
2. On the **Basics** tab, specify the following, and then select **Next**to continue.
    - **Title**: Specify a title for this notification. Titles are limited to 50 characters.
    - **Body**: Specify the message. Messages are limited to 500 characters.
3. On the **Assignments** tab, select the groups to which you'd like to send this custom notification, and then select **Next** to continue.
4. On the **Review + Create** tab, review the information and when ready to send the notification, select **Create**.

Intune processes the message immediately. A confirmation appears in the admin center once the notification is sent.

Note

Intune doesn't track sent custom notifications, and devices don't log receipt outside of the notification center. The message might appear in a temporary diagnostic log if the user requests support through the Company Portal or Intune app.

## User experience

::: zone pivot="ios"

When a custom notification is sent, users receive it as a push alert from the Company Portal on their enrolled device. The experience varies slightly depending on the app state.

- Intune sends messages to the Company Portal app, which then generates the push notification. Users don't need to be signed in to the app, but the device must be enrolled by the targeted user.
- Delivery isn't guaranteed. Notifications might be delayed or not delivered at all, so they shouldn't be used for urgent communication.
- Users might still receive notifications even after being removed from a group or unenrolling a device. Similarly, users added to a group after a notification is sent might receive that previously sent message.
- Notification visibility depends on device settings. Messages might appear on the lock screen or within the app.
- If the app is open when the notification is received, it displays in-app rather than as a push notification. Users can view it by navigating to the **Notifications** tab and pulling to refresh.

[![Locked device iOS/iPadOS custom notification.](media/send-custom-notification/ios-custom-notification.png)](media/send-custom-notification/ios-custom-notification.png#lightbox)

::: zone-end

::: zone pivot="android"

When a custom notification is sent, users receive it as a push alert from the Company Portal or Intune app on their enrolled device. The experience varies slightly depending on platform and app state.

- Intune sends messages to the user's Company Portal or Intune app, which then generates the push notification. Users don't need to be signed in to the app, but the device must be enrolled by the targeted user.
- Delivery isn't guaranteed. Notifications might be delayed or not delivered at all, so they shouldn't be used for urgent communication.
- Users might still receive notifications even after being removed from a group or unenrolling a device. Similarly, users added to a group after a notification is sent might receive that previously sent message.
- Notification visibility depends on device settings. Messages might appear on the lock screen or within the app.
- If the app is open when the notification is received, it displays in-app rather than as a push notification.

[![Locked device Android custom notification.](media/send-custom-notification/android-custom-notification.png)](media/send-custom-notification/android-custom-notification.png#lightbox)

::: zone-end

## Reference links

- Microsoft Graph API: [sendCustomNotificationToCompanyPortal action](/en-us/graph/api/intune-devices-manageddevice-sendcustomnotificationtocompanyportal)