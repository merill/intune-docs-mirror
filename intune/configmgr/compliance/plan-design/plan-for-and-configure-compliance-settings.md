---
layout: Conceptual
title: Plan for and configure compliance settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/plan-design/plan-for-and-configure-compliance-settings
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
description: Learn about the prerequisites and configuration tasks for working with compliance settings in Configuration Manager.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 43bf7bca-7468-18d6-e9cb-f64e5a3be8dd
document_version_independent_id: dc603ec2-7ef2-6fb6-4fe4-a6de42f97d46
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/plan-design/plan-for-and-configure-compliance-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/plan-design/plan-for-and-configure-compliance-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/plan-design/plan-for-and-configure-compliance-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0039217d-f2f8-26f6-bcf5-e8f2c6269a75
---

# Plan for and configure compliance settings - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you start working with Configuration Manager compliance settings, there are a few prerequisites you need to know about, and some configuration tasks you'll need to perform.

## Prerequisites for compliance settings

| Prerequisite | More information |
| --- | --- |
| Windows Configuration Manager clients must be enabled and configured for compliance evaluation. | See below |
| If you want to run reports, then you must configure reporting for your site. | [Introduction to reporting](../../core/servers/manage/introduction-to-reporting) |
| Required security permissions. | The **Compliance Settings Manager** security role includes the necessary permissions to manage compliance settings, user data and profiles configuration items, and remote connection profiles.[Configure role-based administration](../../core/servers/deploy/configure/configure-role-based-administration) |

## Enable and configure compliance settings (for Windows PCs only)

This procedure configures the default client settings for compliance settings and applies to all computers in your hierarchy. If you want these settings to apply to only some computers, create a custom device client setting and assign it to a collection that contains the computers for which you want to use compliance settings. For more information about how to create custom device settings, see [How to configure client settings](../../core/clients/deploy/configure-client-settings).

Tip

Other device types require no specific configuration to evaluate compliance settings.

1. In the Configuration Manager console, click **Administration** &gt; **Client Settings** &gt; **Default Settings**.
2. On the **Home** tab, in the **Properties** group, click **Properties**.
3. In the **Default Settings** dialog box, click **Compliance Settings**.
4. Configure the following client settings for compliance settings:
    - **Enable compliance evaluation on clients** - Set to **True** if you want to evaluate compliance on client devices.
    - **Schedule compliance evaluation** - Click **Schedule** if you want to modify the default compliance evaluation schedule on client devices.
    - **Enable User Data and Profiles** - Enable this option if you want to create and deploy user data and profiles configuration items to Windows computers. For details, see [Create user data and profiles configuration items](../deploy-use/create-remote-connection-profiles).
5. Click **OK** to close the **Default Settings** dialog box.

Client computers are configured with these settings the next time they download client policy.