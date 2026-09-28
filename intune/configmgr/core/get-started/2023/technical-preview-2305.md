---
layout: Conceptual
title: Technical preview 2305 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2023/technical-preview-2305
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2305.
ms.date: 2023-05-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: eff6d0fd-c5ec-11b3-c910-0e3c2e6de48a
document_version_independent_id: eff6d0fd-c5ec-11b3-c910-0e3c2e6de48a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2023/technical-preview-2305.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2023/technical-preview-2305
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2023/technical-preview-2305.md
platformId: 8fd5237a-7ff6-b17b-bbb8-a36c2a644734
---

# Technical preview 2305 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2305. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## OSD preferred MP option for PXE boot scenario

Preferred Management Point (MP) option will now allow PXE clients to communicate to an initial lookup MP and receive the list of MP(s) to be used for further communication. When the option is enabled, it allows an MP to redirect the PXE client to another MP, based on the client location in the site boundaries.

![Screenshot of how to enable OSD preferred MP option for PXE boot scenario.](media/2839966-osd-mp-pxe.png) !

## New Site Maintenance task “Delete Aged Task Execution Status Messages” is now available on primary servers to clean up data older than 30 days or configured number of days

You can enable this feature by utilizing the Site Maintenance Window or using PowerShell Commandlet. By default, it's set to run on Saturday and delete the data older than 30 days. It does so by cleaning up [dbo].TaskExecutionStatus Table

Example: Set-CMSiteMaintenanceTask -Sitecode "XXX" -MaintenanceTaskName "Delete Aged Task Execution Status Messages" -DaysOfWeek Friday

![Screenshot of Site Maintenance task “Delete Aged Task Execution Status Messages”.](media/6167745-console-task-scheduler.png)

## CMG creation using third PartyApp via Console

The use of first party app is deprecated for the creation of CMG. Now, CMG uses a third party server app to get bearer tokens. For CMG creation, users can select tenant and the app name using the Microsoft Entra tenant name. Once you select the tenant and app name, the sign-in button appears. Existing Customers, must update their server app as current version, doesn't have the Redirect to- "http://localhost"

To update the server app, you can navigate to Microsoft Entra tenants node --&gt; select the tenant --&gt; select the server app --&gt; select "update application settings".

## CMG creation using third Party ServerApp via PowerShell

To create CMG using third party Server app via PowerShell cmdlet, you need to specify TenantID in the argument:

PowerShell Commandlet: `Set-UpdateServerApplication – TenantID`

If you're utilizing the existing Microsoft Entra server app, when existing (nonupdated) Microsoft Entra server app is used, ensure that the server app has RedirectUrl="http://localhost” added in Azure portal and in TableAAD\_Application\_EX in Database.

If you try to create the CMG before updating RedirectUrl, you get an error "Your server Application needs to be updated".

Run this PowerShell command: `Set-UpdateServerApplication` to update your App, and then try again to create CMG.

Note

For new customers, before creating CMG, create Microsoft Entra server app that contains the RedirectUrl="http://localhost” in your App. Once redirect URL and database settings are complete, you can execute the new PowerShell commandlet script.

## Attack Surface Reduction (ASR) capability now marks Server SKU as compliant only after enforcement

Prior to the Attack Surface Reduction capability in Windows Server, rules were marked compliant by default. As this rule setting becomes available to Server SKU, the rule setting is enforced through Config Manager. Now the Server SKU will be marked as compliant for an Attack Surface Reduction rule, only after enforcement of the rule.

## Enhancing security for External service notifications URL

This feature avoids the risk of directing the subscription logic to an untrusted URL, resulting in information leakage. The upgrade prevents information from being sent to an HTTPS URL with an untrusted certificate. This method ensures that the data is protected by a trusted SSL certificate. For a secure connection, we recommend using SSL certificates from trusted Certification Authorities. This security feature only allows connections to URLs that have trusted certificates for enhanced security.

## Enable BitLocker through ProvisionTS

ProvisionTS is the task sequence that is executed at the time of provisioning the device. Escrowing recovery key to Config Manager Database is now supported using ProvisionTS. As a result, a device can escrow the key to Config Manager Database instantly.

## Client certificate state in console (self-signed) to match state in control panel (PKI)

For clients that have a PKI certificate, the Configuration Manager console displays the Client certificate property as self-signed. The client control panel Client certificate property shows PKI. After this release, Configuration Manager console and client control panel Client certificate will be in sync and shows same state.

![Screenshot of PKI cert for the client certificate state.](media/10278780-console-pki-cert.png)