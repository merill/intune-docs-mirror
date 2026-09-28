---
layout: Conceptual
title: Test client upgrades - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/test-client-upgrades
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
description: Test client upgrades in a pre-production collection in Configuration Manager.
ms.date: 2022-04-12T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 1720f2c1-a4d6-e0f5-e804-21d054a5f8c5
document_version_independent_id: 3d5fb678-e510-04b2-1f9c-9be148160b13
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/upgrade/test-client-upgrades.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/upgrade/test-client-upgrades
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/upgrade/test-client-upgrades.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 15fbc22d-5423-b272-f587-2f1f12c7b1a7
---

# Test client upgrades - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can test a new Configuration Manager client version in a pre-production collection before upgrading the rest of the site with it. When you do this process, the site only updates devices that are part of the test collection. Once you've had a chance to test the client, you can promote the client. Client promotion makes the new version of the client software available to the rest of the site.

Note

Only a user with the **Full Administrator** security role and the **All** security scope can promote a test client to production. For more information, see [Fundamentals of role-based administration](../../../understand/fundamentals-of-role-based-administration). This action is only available when connected to the central administration site (CAS) or a standalone primary site.

There are three steps to test clients in pre-production:

1. Configure automatic client upgrades to use a pre-production collection.
2. Install a Configuration Manager update that includes a new version of the client.
3. Promote the new client to production.

## Configure automatic client upgrades to use a pre-production collection

Important

Pre-production client deployment isn't supported for workgroup computers. They can't use the authentication required for the distribution point to access the pre-production client package. They'll receive the latest client when it's promoted to be the production client.

1. [Set up a collection](../collections/create-collections) that contains the computers to which you want to deploy the pre-production client.
2. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node. In the ribbon, select **Hierarchy Settings**.
3. Switch to the **Client Upgrade** tab, and configure the following settings:

    - Select **Upgrade all clients in the pre-production collection automatically using pre-production client**.
    - Select a collection to use as the **Pre-production collection**.

![Hierarchy settings window, client upgrade tab, highlighting pre-production collection.](media/test-client-upgrades.png)

Note

Only a user with the **Full Administrator** security role and the **All** security scope can change these settings.

## Configure client upgrades during site update

1. In the Configuration Manager console, go to the **Administration** workspace, and select the **Updates and Servicing** node. Select an available update, and then in the ribbon select **Install Update Pack**.

    For more information on installing updates, see [Updates for Configuration Manager](../../../servers/manage/updates).
2. During installation of the update, on the **Client Options** page of the wizard, select **Test in pre-production collection**.
3. Complete the rest of the wizard and install the update pack.

After the wizard complete, clients in the pre-production collection will begin to deploy the updated client. You can monitor the deployment of upgraded clients in the console. Go to the **Monitoring** workspace, expand **Client Status**, and select the **Pre-production Client Deployment** node. For more information, see [How to monitor client deployment status](../../deploy/monitor-client-deployment-status).

Note

For computers in a pre-production collection that also host site system roles, their deployment status may report as **Not compliant**. This state may show even when the client was successfully updated. When you promote the client to production, the deployment status reports correctly.

## Promote a new client to production

1. In the Configuration Manager console, go to the **Administration** workspace, and select the **Updates and Servicing** node. In the ribbon, select **Promote Pre-production Client**.

    Tip

    The **Promote Pre-production Client** action is also available when you monitor client deployments in the console at **Monitoring** &gt; **Client Status** &gt; **Pre-production Client Deployment**.
2. Review the client versions in production and pre-production, and make sure the correct pre-production collection is specified. When ready, select **Promote**, and then select **Yes** to confirm.

The updated client version now replaces the client version in use in your hierarchy. You can then upgrade the clients for your whole site. For more information, see [How to upgrade clients for Windows computers](upgrade-clients-for-windows-computers).

Note

To enable the pre-production client, or to promote a pre-production client to a production client, your account must be a member of a security role that has **Read** and **Modify** permissions for the **Update Packages** object.

Client upgrades honor any Configuration Manager maintenance windows you configure. For more information on a known issue, see [Client upgrade and maintenance windows](upgrade-clients-for-windows-computers#client-upgrade-and-maintenance-windows).

## Known issues

### Pre-production client and site server high availability

Consider the following scenario:

- You enable the pre-production client.
- The site has a [site server in passive mode](../../../servers/deploy/configure/site-server-high-availability).
- You update the site to the latest version.
- You promote the passive mode site server to the active site server.

After you promote the site server, the pre-production client version shows as the production version. Depending on your configuration, it may automatically deploy to all systems.

When you install an update, Configuration Manager currently updates the **Client** folder of the site server in passive mode with the pre-production client version.

To work around this issue:

- Wait to promote the site server in passive mode until after you promote the pre-production client version to production version.
- If you have to fail over for high availability, manually correct the client version in the **Client** folder.