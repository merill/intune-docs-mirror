---
layout: Conceptual
title: Configure client settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-settings
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
description: Learn how to configure client settings in Configuration Manager.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: badfb52f-9c42-c09c-a693-2eeaed16dfe7
document_version_independent_id: 9a135a58-0296-8b0c-8b2d-5c7ec61ade8f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/configure-client-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/configure-client-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/configure-client-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f01eafe7-0e6e-37ad-5d2b-3857ae88d9e1
---

# Configure client settings - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You manage all client settings in Configuration Manager from the **Client Settings** node of the **Administration** workspace in the console. When you want to configure settings for all users and devices in the hierarchy, modify the default settings. If you want to apply different settings to just some users or devices, create custom settings and deploy to collections. Custom client settings override the default settings.

For information about each client setting, see [About client settings](about-client-settings).

Note

You can also use configuration items to manage clients to assess, track, and remediate the configuration compliance of devices. For more information, see [Ensure device compliance](../../../compliance/understand/ensure-device-compliance).

## Configure default client settings

1. In the Configuration Manager console, go to the **Administration** workspace, and select the **Client Settings** node.
2. Select **Default Client Settings**. On the **Home** tab of the ribbon, select **Properties**.
3. View and configure the client settings for each group of settings in the navigation pane.

Tip

Configuration Manager configures clients with these settings when they next download policy. To start policy retrieval for a single client, see [Start policy retrieval for a Configuration Manager client](../manage/manage-clients#start-policy-retrieval).

## Create and deploy custom client settings

When you deploy these custom settings, they override the default client settings. Before you begin this procedure, make sure that you have a collection the deployment. The collection should contain the users or devices that require these custom client settings.

1. In the Configuration Manager console, go to the **Administration** workspace, and select the **Client Settings** node.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Create Custom Client Settings**. Then choose either **Create Custom Client Device Settings** or **Create Custom Client User Settings**.

    1. Specify a unique name and optional description.
    2. Select one or more of the settings groups.
    3. Select each group of settings from the navigation pane, configure the available settings, and then select **OK** to save the settings.
3. Select the custom client setting that you created. On the **Home** tab of the ribbon, in the **Client Settings** group, choose **Deploy**.
4. In the **Select Collection** window, select the appropriate collection, and then choose **OK**. To verify the targeted collection, switch to the **Deployments** tab in the details pane of the **Client Settings** node.
5. View the order of the custom client setting that you created. When you have multiple custom client settings, they're applied according to their order number. If there are any conflicts between settings, the setting that has the lowest order number overrides the other settings. To change the order number, on the **Home** tab of the ribbon, in the **Client Settings** group, choose **Move Item Up** or **Move Item Down**.

Tip

Configuration Manage configures clients with these settings when they next download policy. To start policy retrieval for a single client, see [Start policy retrieval for a Configuration Manager client](../manage/manage-clients#start-policy-retrieval).

## View client settings

When you deploy multiple client settings to the same device, user, or user group, the prioritization and combination of settings is complex.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select either the **Devices** or **Users** node.
2. Select a device or user, and in the **Client Settings** group of the ribbon, select **Resultant Client Settings**.
3. Select a client setting from the left pane, and it displays the settings. In this view, the settings are read-only.

    Note

    To view the client settings, your account needs **Read** access to client settings.

## Automate with PowerShell

Optionally, you can use the Configuration Manager PowerShell cmdlets to automate client settings. For more information, see the following articles in the PowerShell documentation:

- [Get-CMClientSetting](/en-us/powershell/module/configurationmanager/Get-CMClientSetting): Get an existing client settings object.
- [New-CMClientSetting](/en-us/powershell/module/configurationmanager/New-CMClientSetting): Create a new client settings object.
- [Remove-CMClientSetting](/en-us/powershell/module/configurationmanager/Remove-CMClientSetting): Remove a client settings object.

Use the following cmdlets to configure client settings for the specific group:

- [Set-CMClientSettingBackgroundIntelligentTransfer](/en-us/powershell/module/configurationmanager/Set-CMClientSettingBackgroundIntelligentTransfer)
- [Set-CMClientSettingClientCache](/en-us/powershell/module/configurationmanager/Set-CMClientSettingClientCache)
- [Set-CMClientSettingClientPolicy](/en-us/powershell/module/configurationmanager/Set-CMClientSettingClientPolicy)
- [Set-CMClientSettingCloudService](/en-us/powershell/module/configurationmanager/Set-CMClientSettingCloudService)
- [Set-CMClientSettingComplianceSetting](/en-us/powershell/module/configurationmanager/Set-CMClientSettingComplianceSetting)
- [Set-CMClientSettingComputerAgent](/en-us/powershell/module/configurationmanager/Set-CMClientSettingComputerAgent)
- [Set-CMClientSettingComputerRestart](/en-us/powershell/module/configurationmanager/Set-CMClientSettingComputerRestart)
- [Set-CMClientSettingDeliveryOptimization](/en-us/powershell/module/configurationmanager/Set-CMClientSettingDeliveryOptimization)
- [Set-CMClientSettingEndpointProtection](/en-us/powershell/module/configurationmanager/Set-CMClientSettingEndpointProtection)
- [Set-CMClientSettingEnrollment](/en-us/powershell/module/configurationmanager/Set-CMClientSettingEnrollment)
- [Set-CMClientSettingGeneral](/en-us/powershell/module/configurationmanager/Set-CMClientSettingGeneral)
- [Set-CMClientSettingHardwareInventory](/en-us/powershell/module/configurationmanager/Set-CMClientSettingHardwareInventory)
- [Set-CMClientSettingMeteredInternetConnection](/en-us/powershell/module/configurationmanager/Set-CMClientSettingMeteredInternetConnection)
- [Set-CMClientSettingPowerManagement](/en-us/powershell/module/configurationmanager/Set-CMClientSettingPowerManagement)
- [Set-CMClientSettingRemoteTool](/en-us/powershell/module/configurationmanager/Set-CMClientSettingRemoteTool)
- [Set-CMClientSettingSoftwareCenter](/en-us/powershell/module/configurationmanager/Set-CMClientSettingSoftwareCenter)
- [Set-CMClientSettingSoftwareDeployment](/en-us/powershell/module/configurationmanager/Set-CMClientSettingSoftwareDeployment)
- [Set-CMClientSettingSoftwareInventory](/en-us/powershell/module/configurationmanager/Set-CMClientSettingSoftwareInventory)
- [Set-CMClientSettingSoftwareMetering](/en-us/powershell/module/configurationmanager/Set-CMClientSettingSoftwareMetering)
- [Set-CMClientSettingSoftwareUpdate](/en-us/powershell/module/configurationmanager/Set-CMClientSettingSoftwareUpdate)
- [Set-CMClientSettingStateMessaging](/en-us/powershell/module/configurationmanager/Set-CMClientSettingStateMessaging)
- [Set-CMClientSettingUserAndDeviceAffinity](/en-us/powershell/module/configurationmanager/Set-CMClientSettingUserAndDeviceAffinity)

Use the following cmdlets to manage deployments of custom client settings:

- [New-CMClientSettingDeployment](/en-us/powershell/module/configurationmanager/New-CMClientSettingDeployment)
- [Remove-CMClientSettingDeployment](/en-us/powershell/module/configurationmanager/Start-CMClientSettingDeployment)