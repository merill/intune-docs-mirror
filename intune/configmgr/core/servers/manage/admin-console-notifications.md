---
layout: Conceptual
title: Configuration Manager console notifications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/admin-console-notifications
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
description: Learn about notifications from the Configuration Manager console.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 115dc45d-44ff-bcc0-b4ab-2c13162dc64a
document_version_independent_id: 9fceb0ed-f0b3-6d40-d92e-14f728dd2f6d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/admin-console-notifications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/admin-console-notifications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/admin-console-notifications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 3010749d-0ca2-62d1-b354-c98638a96939
---

# Configuration Manager console notifications - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Configuration Manager console notifies you for specific events that occur. You can configure some of the event notifications for your Configuration Manager sites.

- Non-configurable event notifications:
    - When an update is available for Configuration Manager itself
    - When lifecycle and maintenance events occur in the environment
- Configurable event notifications:
    - Non-critical site health changes
    - Messages from Microsoft

This notification is a bar at the top of the console window below the ribbon. It replaces the previous experience when Configuration Manager updates are available. These in-console notifications still display critical information, but don't interfere with your work in the console. You can't dismiss critical notifications. The console displays all notifications in a new notification area of the title bar.

![Notification bar and flag in console](media/1318035-notify-eval-version-expired.png)

## About console notifications

Notifications follow the permissions of role-based administration. For example, if a user doesn't have permissions to see Configuration Manager updates, they won't see those notifications.

Some notifications have a related action. For example, if the console version doesn't match the site version, select **Install the new console version**. This action launches the console installer.

The following notifications reevaluate every five minutes:

- Site is in maintenance mode
- Site is in recovery mode
- Site is in upgrade mode

The following notifications are most applicable to the technical preview branch:

- Evaluation version is within 30 days of expiration (Warning): the current date is within 30 days of the expiration date of the evaluation version
- Evaluation version is expired (Critical): the current date is past the expiration date of the evaluation version
- Console version mismatch (Critical): the console version doesn't match the site version
- Site upgrade is available (Warning): there's a new update package available

Most console notifications are per session. The console evaluates queries when a user launches it. To see changes in the notifications, restart the console. If a user dismisses a non-critical notification, it notifies again when the console restarts if it's still applicable.

- Dismissing or snoozing a notification is persistent for your user across consoles starting in version 2010.

## Console notification improvements

### Improvements starting in version 2010

Starting in Configuration Manager 2010, you have an updated look and feel for in-console notifications. Notifications are more readable and the action link is easier to find. The age of the notification is displayed to help you find the latest information. If you dismiss or snooze a notification, that action is now persistent for your user across consoles.

Right-click or select `...` on the notification to take one of the following actions:

- **Translate text**: Launches [Bing Translator](https://www.bing.com/translator/) for the text.
- **Copy text**: Copies the notification text to the clipboard.
- **Snooze**: Snoozes the notification for the specified duration:
    - One hour
    - One day
    - One week
    - One month
- **Dismiss**: Dismisses the notification.

To see these improvements for notifications, update the Configuration Manager console to the latest version.

#### New notifications in version 2010

To help you manage security risk in your environment, you'll be notified in-console about devices with operating systems that are past the end of support date and that are no longer eligible to receive security updates.

![Screenshot of in-console notifications for operating systems past the end of support date](media/7520646-notification.png)

Environments with the following operating systems installed on client devices receive a notification:

- [Windows 7](/en-us/lifecycle/products/windows-7), [Windows Server 2008 (non-Azure)](/en-us/lifecycle/products/windows-server-2008), and [Windows Server 2008 R2 (non-Azure)](/en-us/lifecycle/products/windows-server-2008-r2) without ESU.

    - Selecting **More info** takes you to the [Management insights](management-insights#security)**Security** group to review the **Update clients running Windows 7 and Windows Server 2008** rule.
- Versions of Windows 10 Semi-Annual Channel that are past the end-of-support date for [Enterprise and Education](/en-us/lifecycle/products/windows-10-enterprise-and-education) and [Home and Pro](/en-us/lifecycle/products/windows-10-home-and-pro) editions.

    - Selecting **More info** takes you to the [Management insights](management-insights#simplified-management)**Simplified Management** group to review the **Update clients to a supported Windows 10 version** rule.

You can also view the [Product Lifecycle Dashboard](../../clients/manage/asset-intelligence/product-lifecycle-dashboard) to see information about which operating systems are out of support. This information (such as the support lifecycle for Windows 10 versions) is provided for your convenience and only for use internally within your company. You should not solely rely on this information to confirm update compliance. Be sure to verify the accuracy of the information provided to you.

### Improvements starting in version 2006

- You have an option to receive Messages from Microsoft
- If you configure Azure services to cloud-attach your site, you'll see notifications with an action to [renew the secret key](../deploy/configure/azure-services-wizard#bkmk_renew).The site evaluates the state of the following alerts once per hour:
    - One or more Microsoft Entra app secret keys will expire soon
    - One or more Microsoft Entra app secret keys have expired

Important

When you use an [imported Microsoft Entra app](../deploy/configure/azure-services-wizard#import-apps-dialog-server), you aren't notified of an upcoming expiration date from console notifications. 

## Configure a site to show non-critical notifications

You can configure each site to show non-critical notifications in the properties of the site.

1. In the **Administration** workspace, expand **Site Configuration**, then select the **Sites** node.
2. Select the site you want to configure for non-critical notifications.
3. In the ribbon, select **Properties**.
4. On the **Alerts** tab, select the option to **Enable console notifications for non-critical site health changes**.
    - If you enable this setting, all console users see critical, warning, and information notifications. This setting is enabled by default.
    - If you disable this setting, console users only see critical notifications.

## Configure a site to receive messages from Microsoft

Starting in version 2006, you can choose to receive notifications from Microsoft in the Configuration Manager console. These notifications help you stay informed about new or updated features, changes to Configuration Manager and attached services, and issues that require action to remediate.

Note

For push notifications from Microsoft to show in the console, the service connection point needs access to `configmgrbits.azureedge.net`. It also needs access to this endpoint for [updates and servicing](../../plan-design/network/internet-endpoints#updates-and-servicing), so you may have already allowed it.

### Configure notification settings for Microsoft messages

1. Navigate to **Administration** &gt; **Site Configuration** &gt; **Sites**.
2. Select a site, and then in the ribbon, select **Properties**.
3. In the **Alerts** tab, enable the notifications by selecting **Receive messages from Microsoft**. You can deselect any of the following notifications if you prefer not to receive them:

    - **Prevent/fix**: Known issues affecting your organization that may require you to take action.
    - **Plan for change**: Changes to Configuration Manager that may require you to take action.
    - **Stay informed**: Informs you of new or updated features that are available.

[![Notification from Microsoft options in site properties](media/3953121-microsoft-notifications.png)](media/3953121-microsoft-notifications.png#lightbox)

## Console extension installation notifications

(*Introduced in version 2103*)

Users are notified when console extensions are approved for installation. These notifications occur for users in the following scenarios:

- The Configuration Manager console requires a built-in extension, such as WebView2, to be installed or updated.
- Console extensions are approved and notifications are enabled from **Administration** &gt; **Overview** &gt; **Updates and Servicing** &gt; **Console Extensions**.
    - When notifications are enabled, users within the [security scope](../../understand/fundamentals-of-role-based-administration#security-scopes) for the extension receive the following prompts:

1. In the upper-right corner of the console, select the bell icon to display Configuration Manager console notifications.

    ![Notifications in the Configuration Manager console](media/3555909-notification.png)
2. The notification will say **New custom console extensions are available**.

    ![New custom console extensions are available notification](media/3555909-extension-notification.png)
3. Select the link **Install custom console extensions** to launch the install.
4. When the install completes, select **Close** to restart the console and enable the new extension.

    ![Console extension completed install](media/3555909-extension-installed.png)

Note

When you upgrade to Configuration Manager 2107, you will be prompted to install the WebView2 console extension again. For more information about the WebView2 installation, see the [WebView2 installation](community-hub#bkmk_webview2) section if the Community hub article. 

For more information, see [Manage console extensions](admin-console-extensions).

## Log files

For more information and troubleshooting assistance, see the **SmsAdminUI.log** file on the console computer. By default, this log file is at the following path: `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\AdminUILog\SmsAdminUI.log`.