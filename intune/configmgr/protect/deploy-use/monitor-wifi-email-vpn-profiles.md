---
layout: Conceptual
title: Monitor Email, Wi-Fi and VPN profiles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/monitor-wifi-email-vpn-profiles
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
description: Learn how to monitor the compliance status of email, Wi-Fi, and VPN profiles in Configuration Manager.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 9fd12cd1-58c8-9fbf-0f6f-f8f7bd52b73b
document_version_independent_id: 98ca1ffb-38e8-91f2-10ea-6f0b40cfaf97
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/monitor-wifi-email-vpn-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/monitor-wifi-email-vpn-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/monitor-wifi-email-vpn-profiles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: a021eaac-2de3-3912-59a5-209daf8c1be9
---

# Monitor Email, Wi-Fi and VPN profiles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../plan-design/resource-access-deprecation-faq).

After you have deployed Configuration Manager Email, Wi-Fi or VPN profiles to users in your hierarchy, you can use the following procedures to monitor the compliance status of the profile:

- How to View Compliance Results in the Configuration Manager Console
- How to View Compliance Results by Using Reports

## How to View Compliance Results in the Configuration Manager Console

Use this procedure to view details about the compliance of deployed profiles in the Configuration Manager console.

#### To view compliance results in the Configuration Manager console

1. In the Configuration Manager console, click **Monitoring**.
2. In the **Monitoring** workspace, click **Deployments**.
3. In the **Deployments** list, select the profile deployment for which you want to review compliance information.
4. You can review summary information about the compliance of the profile deployment on the main page. To view more detailed information, select the profile deployment, and then, on the **Home** tab, in the **Deployment** group, click **View Status** to open the **Deployment Status** page.

    The **Deployment Status** page contains the following tabs:

    - **Compliant:** Displays the compliance of the profile that is based on the number of affected assets. You can double-click a rule to create a temporary node under the **Users** node in the **Assets and Compliance** workspace, which contains all users that are compliant with this profile. The **Asset Details** pane displays the users that are compliant with the profile. Double-click a user in the list to display additional information.

        Important

        A profile is not evaluated if it is not applicable on a client device; however, it is returned as compliant.
    - **Error:** Displays a list of all errors for the selected profile deployment that is based on the number of affected assets. You can double-click a rule to create a temporary node under the **Users** node of the **Assets and Compliance** workspace, which contains all users that generated errors with this profile. When you select a user, the **Asset Details** pane displays the users that are affected by the selected issue. Double-click a user in the list to display additional information about the issue.
    - **Non-Compliant:** Displays a list of all noncompliant rules within the profile that is based on the number of affected assets. You can double-click a rule to create a temporary node under the **Users** node of the **Assets and Compliance** workspace, which contains all users that are not compliant with this profile. When you select a user, the **Asset Details** pane displays the users that are affected by the selected issue. Double-click a user in the list to display further information about the issue.
    - **Unknown:** Displays a list of all users that did not report compliance for the selected profile deployment together with the current client status of the devices.
5. On the **Deployment Status** page, you can review detailed information about the compliance of the deployed profile. A temporary node is created under the **Deployments** node that helps you find this information again quickly.

## How to View Compliance Results by Using Reports

Compliance settings, which include profiles in Configuration Manager, also includes a number of built-in reports that let you monitor information about profiles. These reports have the report category of **Compliance and Settings Management**.

Important

You must use a wildcard (%) character when you use the parameters **Device filter** and **User filter** in the compliance settings reports.

For more information about how to configure reporting in Configuration Manager, see [Introduction to reporting](../../core/servers/manage/introduction-to-reporting).