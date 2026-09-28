---
layout: Conceptual
title: What's new in version 2309 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2309
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
description: Get details about changes and new capabilities introduced in version 2309 of Configuration Manager current branch.
ms.date: 2023-11-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 6f5892cf-9bb3-2e65-73c1-0cb0a3dee6f1
document_version_independent_id: 6f5892cf-9bb3-2e65-73c1-0cb0a3dee6f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2309.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2309
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2309.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 2df83b31-17a7-775a-4074-4af6749d4308
---

# What's new in version 2309 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2309 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2207 or later. This article summarizes the changes and new features in Configuration Manager, version 2309.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2309](../../servers/manage/checklist-for-installing-update-2309). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2309#post-update-checklist).

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

## Site infrastructure

### Introducing SQL ODBC driver support for Configuration Manager

Starting with Configuration Manager 2309 release, Configuration Manager requires the installation of the ODBC driver for SQL server 18.1.0 or later as a prerequisite. This prerequisite is required when you create a new site or update an existing one and on all remote roles.

Important

Microsoft ODBC Driver for SQL Server 18.1.0 or later needs to be installed on Site Servers and site system roles before upgrading to 2309 version. Do not uninstall SQL native client 11 until we call out in further communications. Configuration Manager doesn't manage the updates for the ODBC driver, ensure that this component is up to date.

For minimum required versions, validated versions, and versions with known blocking issues, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### Option to schedule scripts' runtime

Starting in Configuration Manager current branch version 2309, you can now schedule scripts' runtime in UTC. The run Script Wizard now offers a scheduling option that enables administrators to schedule the execution of scripts. It provides a convenient way to automate the running of scripts on managed devices according to specified schedules.

![A screenshot of the schedule script wizard.](media/17668435-schedule-script.png)

For more information, see [Schedule scripts' runtime](../../../apps/deploy-use/create-deploy-scripts#schedule-scripts-runtime)

### External service notification Run details from Azure Logic application

Starting in Configuration Manager current branch version 2309, when Azure Logic App generates notifications related to specific events, CM can now capture and display these notifications. This integration enables the monitoring of Azure Logic App notifications directly within the MCM console, providing a centralized location for tracking critical events, taking appropriate actions and maintains a high level of operational efficiency.

![A screenshot of the run details of external service notification wizard.](media/17668438-external-service.png)

For more information, see [External service notification](../../servers/manage/external-notifications#monitor-the-workflow).

### New Site Maintenance task “Delete Aged Task Execution Status Messages” is now available on primary servers to clean up data older than 30 days or configured number of days

Starting in Configuration Manager current branch version 2309, you can now enable this feature by utilizing the Site Maintenance Window or using PowerShell Commandlet. By default, it has been set to run on Saturday and delete the data older than 30 days. It does so by cleaning up [dbo].TaskExecutionStatus Table 

Example: PowerShell Commandlet: `Set-CMSiteMaintenanceTask -Sitecode "XXX" -MaintenanceTaskName "Delete Aged Task Execution Status Messages" -DaysOfWeek Friday `

For more information, see [Delete Aged Task Execution Status Messages](../../servers/manage/reference-for-maintenance-tasks#delete-aged-task-execution-status-messages).

## Software updates

### Update Orchestrator Service (USO) for Windows 11 22H2 or later with windows native reboot experience

In Configuration Manager current branch version 2309, when installing software updates from Configuration Manager, administrators can now choose to use the **native Windows Update restart** experience.To use this feature, client devices must be running Windows build 22H2 or later. From the Computer Restart client device settings, ensure that Windows is selected as the restart experience. Branding information is included in the Windows restart notification for updates that require restart. 

For more information, see [Device restart notifications](../../clients/deploy/device-restart-notifications#device-restart-notifications-in-configuration-manager)

### Maintenance window creation using PS cmdlet

We've extended the Offset parameter for **Maintenance windows**.The cmdlet New-CMMaintenanceWindow is used to create a maintenance window for a collection. Earlier the Offset parameter could be set only between 0 and 4. Now it has been extended between 0 to 7.

Example: PowerShell Commandlet: `New-CMSchedule -Start (Get-Date) -DayOfWeek Monday -WeekOrder Second -RecurCount 1 -OffSetDay 6`

## OS deployment

### OSD preferred MP option for PXE boot scenario

Starting in Configuration Manager current branch version 2309, Preferred Management Point (MP) option will now allow **PXE clients** to communicate to an initial lookup MP and receive the list of MP(s) to be used for further communication. When the option is enabled, it allows an MP to redirect the PXE client to another MP, based on the client location in the site boundaries.

![A screenshot of the management point option in console.](media/2839966-osd-mp-pxe.png)

For more information, see [Install-and-configure-distribution-points](../../servers/deploy/configure/install-and-configure-distribution-points)

### Enable Bitlocker through ProvisionTS

In Configuration Manager current branch version 2309, Escrowing recovery key to Config Manager Database is now supported using ProvisionTS. **ProvisionTS** is the task sequence that is executed at the time of provisioning. As a result device can escrow the key to Config Manager Database instantly.

For more information, see [Preprovision-bitlocker-in-windows-pe](../../../osd/deploy-use/preprovision-bitlocker-in-windows-pe)

### Windows 11 Edition Upgrade using CM Policy settings

Starting in Configuration Manager current branch version 2309,administrator can now create a policy using edition upgrade in Configuration Manager to update the **Windows 11 edition**.

![A screenshot of the windows 11 edition upgrade wizard.](media/17668419-edition-upgrade-windows11.png)

For more information, see [Upgrade Windows devices to a new edition](../../../compliance/deploy-use/upgrade-windows-version)

### Windows 11 Upgrade Readiness Dashboard

Starting in Configuration Manager current branch version 2309, administrators can use this dashboard to devise their windows 11 upgrade strategy and discover the devices in the organization, which are ready for **Windows 11 Upgrade**. This Dashboard also provides a count by installed Feature update version and a view of all Windows devices inside the organization. Administrators can create a collection of Windows 11 ready for upgrading devices and roll out feature updates to them.

[![A screenshot of UX of windows 11 readiness dashboard.](media/17668425-windows11-dashboard.png)](media/17668425-windows11-dashboard.png#lightbox)

For more information, see [Manage Windows 11 readiness dashboard](../../../osd/deploy-use/manage-windows-11-readiness-dashboard)

## Cloud-attached management

### New Cloud Management Gateway (CMG) creation via Console

Starting in Configuration Manager current branch version 2309, we have enhanced security of **web (server) app** for the creation of CMG. For new CMG creation, users can select tenant and the app name using the Azure AD tenant name. After selecting tenant and app name the sign-in button appears, follow rest of the process as per the setup CMG.

![A screenshot of the cmg app creation via console.](media/cmg-console-creation.png)

Note

Pre-existing CMG customers must update their web server app by navigating to Azure Active Directory Tenants node --&gt; select the tenant --&gt; select the server app --&gt; click on "update application settings".

For more information, see [Configure Azure Active Directory for CMG](../../clients/manage/cmg/configure-azure-ad)

### New Cloud Management Gateway (CMG) creation via PowerShell

You can now create CMG **web (server) app** via PowerShell cmdlet, you need to specify TenantID in the argument:

PowerShell Commandlet: `Set-UpdateServerApplication – 'TenantID'`

If you try to create the CMG before updating RedirectUrl, you get an error "Your server Application needs to be updated".

PowerShell command: `Set-UpdateServerApplication` to update your App, and then try again to create CMG.

Note

For new customers, before creating CMG, create Azure AD web server app and execute the new PowerShell commandlet script.

For more information, see [New-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/new-cmcloudmanagementgateway)

## Deprecated features

Learn about support changes before they're implemented in [removed and deprecated items](deprecated/removed-and-deprecated).

- Configured resource access policies will block Configuration Manager 2403 upgrade, remove existing policies and move the slider to Intune. Please action before January 2024, read the [FAQ](../../../protect/plan-design/resource-access-deprecation-faq).

For more information, see [Removed and deprecated features for Configuration Manager](deprecated/removed-and-deprecated-cmfeatures).

## Other updates

For more information on changes to the Windows PowerShell cmdlets for Configuration Manager, see [version 2309 release notes](/en-us/powershell/sccm/2309-release-notes).