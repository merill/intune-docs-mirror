---
layout: Conceptual
title: Upgrade clients on Windows - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade/upgrade-clients-for-windows-computers
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
description: Upgrade clients on Windows computers in Configuration Manager.
ms.date: 2022-04-12T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: 4614fdad-6894-1768-3b54-3349951ad0ab
document_version_independent_id: f6eb50a9-fca3-1734-14eb-ead1ef7e1a9f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/upgrade/upgrade-clients-for-windows-computers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 96594989-3a34-77a6-21a0-b473d140cf1f
---

# Upgrade clients on Windows - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Upgrade the Configuration Manager client on Windows computers using client installation methods or the automatic client upgrade feature. The following client installation methods are valid ways to upgrade client software on Windows computers:

- Group policy installation
- Logon script installation
- Manual installation
- Upgrade installation

For more information, see [How to deploy clients to Windows computers](../../deploy/deploy-clients-to-windows-computers).

Exclude clients from upgrade by specifying an exclusion collection. For more information, see [How to exclude clients from upgrade](exclude-clients-windows). Excluded clients still download and run CCMSETUP, but won't upgrade.

Tip

If upgrade your server infrastructure from a previous version of Configuration Manager, complete the server upgrades before upgrading the Configuration Manager clients. This process includes installing all current branch updates. The latest current branch update contains the latest version of the client. Upgrade clients after you have installed all of the Configuration Manager updates.

Note

If you plan to reassign the site for the clients during upgrade, specify the new site using the `SMSSITECODE` client.msi property. If you use the value of `AUTO` for the `SMSSITECODE`, also specify `SITEREASSIGN=TRUE`. This property allows for automatic site reassignment during upgrade. For more information, see [Client installation properties - SMSSITECODE](../../deploy/about-client-installation-properties#smssitecode).

## About automatic client upgrade

Configure the site to automatically upgrade clients to the latest Configuration Manager version. When Configuration Manager identifies an assigned client's version is earlier than the hierarchy version, it automatically upgrades the client. This scenario includes upgrading the client to the latest version when it attempts to assign to a Configuration Manager site.

A client can automatically upgrade in the following scenarios:

- The client version is earlier than the version used in the hierarchy.
- The client on the central administration site (CAS) has a language pack installed and the existing client doesn't.
- A client prerequisite in the hierarchy is a different version than the one installed on the client.
- One or more of the client installation files are a different version.

Note

To identify the different versions of the Configuration Manager client in your hierarchy, use the report **Count of Configuration Manager clients by client versions** in the report folder **Site - Client Information**.

Configuration Manager creates an upgrade package by default. It automatically sends the package to all distribution points in the hierarchy. If you make changes to the client package on the CAS, Configuration Manager automatically updates the package, and redistributes it. An example change is when you add a client language pack. If you enable automatic client upgrade, every client automatically installs the new client language package.

Enable automatic client upgrade across your hierarchy. This configuration keeps your clients up to date with less effort.

If you also manage your Configuration Manager site systems as clients, determine whether to include them as part of the automatic upgrade process. You can exclude all servers, or a specific collection from client upgrade. Some Configuration Manager site roles share the client framework. For example, the management point and pull distribution point. These roles upgrade when you update the site, so the client version on these servers updates at the same time.

## Configure automatic client upgrade

Use the following procedure to configure automatic client upgrade at the CAS. This configuration applies to all clients in your hierarchy.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and then select the **Sites** node.
2. On the **Home** tab of the ribbon, in the **Sites** group, select **Hierarchy Settings**.
3. Switch to the **Client Upgrade** tab. Review the version and date of the production client. Make sure it's the version you want to use to upgrade your clients. If it's not the client version you expect, you may need to promote the pre-production client to production. For more information, see [How to test client upgrades in a pre-production collection](test-client-upgrades).
4. Select **Upgrade all clients in the hierarchy using the production client**. Select **OK** to confirm.
5. If you don't want client upgrades to apply to servers, select **Do not upgrade servers**.
6. Specify the number of days in which devices must upgrade the client. After the device receives policy, it upgrades the client at a random interval within this number of days. This behavior prevents a large number of clients simultaneously upgrading.

    Note

    A computer must be running to upgrade the client. If a computer isn't running when it's scheduled to receive the upgrade, the upgrade doesn't occur. When the computer turns on, and it receives policy, it schedules the upgrade for a random time within the allowed number of days. If this occurs after the number of days to upgrade has expired, it schedules the upgrade at a random time within 24 hours after the computer was turned on.

    Because of this behavior, computers that are routinely shut down may take longer to upgrade than expected if the randomly scheduled upgrade time isn't within the normal working hours.
7. To exclude clients from upgrade, select **Exclude specified clients from upgrade**, and specify the collection to exclude. For more information, see [Exclude clients from upgrade](exclude-clients-windows).
8. If you want the site to copy the client installation package to distribution points that you've enabled for [prestaged content](../../../plan-design/hierarchy/manage-network-bandwidth#BKMK_PrestagingContent), select the option to **Automatically distribute client installation package to distribution points that are enabled for prestaged content**.
9. Select **OK** to save the settings and close Hierarchy Settings Properties.

Clients receive these settings when they next download policy.

Note

Client upgrades honor any Configuration Manager maintenance windows you've configured. The ClientServicing thread only runs the client setup bootstrap program (ccmsetup.exe) during a maintenance window. For more information on a known issue, see Client upgrade and maintenance windows.

If the device runs an edition of Windows with a write filter, ccmsetup tries to download and install at the same time. Otherwise, ccmsetup randomizes a time to download content. After it downloads content and compiles the local policy, ClientServicing schedules the client upgrade during the next maintenance window.

## Known issues

### Client upgrade and maintenance windows

For clients version 2111 or earlier, when you upgrade them to a later version, the process only honors any *business hours* that the user defines. It doesn't use the administrator-defined maintenance window. For example:

- Administrator-defined maintenance window: 12 AM - 5 AM
- User-defined business hours: 5 AM - 10 PM

The client upgrade starts at 10 PM after the business hours. It doesn't wait until the start of the maintenance window at 12 AM.

This issue is fixed with the version 2203 client. When you upgrade clients from version 2203 to a later version, they will honor maintenance windows.