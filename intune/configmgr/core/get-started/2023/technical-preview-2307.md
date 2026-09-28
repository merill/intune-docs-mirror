---
layout: Conceptual
title: Technical preview 2307 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2023/technical-preview-2307
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2307.
ms.date: 2023-07-28T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 20e1c3bb-c393-716a-f446-5f6cfacd97ef
document_version_independent_id: 20e1c3bb-c393-716a-f446-5f6cfacd97ef
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2023/technical-preview-2307.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2023/technical-preview-2307
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2023/technical-preview-2307.md
platformId: b51f97d8-d96b-bb5c-3406-92947286d981
---

# Technical preview 2307 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2307. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Windows 11 Edition Upgrade using Configuration Manager policy settings

Administrator can now create a policy using edition upgrade in Configuration Manager to update the Windows 11 edition.

[![Screenshot of windows 11 edition upgrade wizard.](media/17668419-edition-upgrade-windows11.png)](media/17668419-edition-upgrade-windows11.png#lightbox)

## Windows 11 Upgrade Readiness Dashboard

Administrators can use this dashboard to devise their Windows 11 upgrade strategy and discover the devices in the organization, which are ready for Windows 11 Upgrade. This Dashboard also provides a count by installed Feature update version and a view of all Windows devices inside the organization. Administrators can create a collection of Windows 11 ready for upgrading devices and roll out feature updates to them.

[![Screenshot of UX of windows 11 readiness dashboard.](media/17668425-windows11-dashboard.png)](media/17668425-windows11-dashboard.png#lightbox)

Following four charts are offered in this dashboard:

- Windows Device Information- Shows count of Windows 7, 8 , 10 and 11 devices in your organization.
- Feature Update Version – Shows count of each feature update Version in your organization.
- Upgrade Experience Indicators – Shows information for each device, which can be in any of these states:
    - Cannot Upgrade (Red Color) devices that cannot be upgraded to windows 11.
    - App Upgrade/Uninstall required (Yellow Color) devices that need an application update or uninstall before upgrading to Windows 11.
    - App/Driver upgrade required (Orange Color) devices that need application upgrade to windows 11.
    - Ready for Upgrade (Green Color) devices that are capable of Windows 11 upgrade.
- Windows 11 Minimum Hardware Requirement – Showcases the minimum hardware and software requirements needed to support Windows 11.

## Option to schedule scripts' runtime

The Run Script wizard now offers a scheduling option which enables administrators to schedule the future execution time of the scripts. It provides a convenient way to automate the running of scripts on managed devices according to specified schedules.

[![Screenshot of Run script wizard to schedule script.](media/17668435-schedule-script.png)](media/17668435-schedule-script.png#lightbox)

## External service notification Run details from Azure Logic application

This integration enables the monitoring and management of Azure Logic App notifications directly within the Configuration Manager console, providing a centralized location for tracking critical events, taking appropriate actions and maintains a high level of operational efficiency.

Note

To use this feature a valid Microsoft Entra web app is required. Please deploy the Azure services for Administration service management under \Administration\Overview\Cloud Services\Azure Services. If the service is already deployed, admin can use the existing web application to view Run details from Azure logic app.

View Status wizard

[![Screenshot of external service notification monitoring wizard.](media/17668438-external-service.png)](media/17668438-external-service.png#lightbox)

> 
> Known issue :- An unexpected error can occur while configuring the Azure service web app for Administration service management which can be ignored as it does not affect the service creation.

## Maintenance window creation using PowerShell cmdlet

Maintenance windows are recurring periods of time when the Configuration Manager client can run tasks. PowerShell Commandlet: `New-CMMaintenanceWindow ` is used to create a maintenance window for a collection. Earlier, the Offset parameter could be set only between 0 and 4. Now, it has been extended between 0 and 7.

## Update Orchestrator Service (USO) for Windows 11 22H2 or later with windows native reboot experience

When installing software updates from Configuration Manager, administrators can now choose to use the native Windows Update restart experience. To use this feature, client devices must be running Windows build 22H2 or later. From the Computer Restart client device settings, ensure that Windows is selected as the restart experience. Branding information will be included in the Windows restart notification for updates that require restart.

Steps to enable Client settings

[![Screenshot of the client settings for reboot.](media/4316341-client-settings.png)](media/4316341-client-settings.png#lightbox)

Reboot Notification

[![Screenshot of the reboot experience on client machine.](media/4316341-reboot-experience.png)](media/4316341-reboot-experience.png#lightbox)