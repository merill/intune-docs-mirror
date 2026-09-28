---
layout: Conceptual
title: Recommendations for power management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/best-practices-for-power-management
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
description: Learn Microsoft recommendations for power management in Configuration Manager.
ms.date: 2019-09-10T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ea8e7580-1c6f-d78d-562b-6aa1c738d189
document_version_independent_id: 9f0b4b99-5c45-fec0-c3b3-fdb21d8675e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/power/best-practices-for-power-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/power/best-practices-for-power-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/power/best-practices-for-power-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 298bcbbc-566f-8857-578c-aa420414ea29
---

# Recommendations for power management - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the following recommendations for power management in Configuration Manager.

## Monitor at a representative time

The monitoring phase of power management provides you with the following information from computers in your organization:

- Power consumption
- Activity
- Power management capabilities
- Environmental impact

Choose a representative time to monitor the devices. For example, monitoring during a public holiday doesn't provide a realistic report on computer power usage.

## Create a control collection

Create two collections of computers to help you monitor the effects of applying power plans to computers. The first collection should contain the majority of the computers to which you want to apply power settings. The *control collection* should contain the remaining computers. Apply the required power management plan to the first collection. Then run reports to compare the impact between the two collections.

## Run reports before you apply a plan

Before you apply a power management plan to a collection of computers, run the **Power Settings** report. Use this report to help you understand the power management settings that are already configured on computers in the collection. If you apply new power management settings to computers without first examining the existing settings, it might increase their power consumption.

## Exclude servers

Power management for computers that run Windows Server isn't supported. Add servers to a collection and exclude it from power management.

Note

Although Configuration Manager doesn't support power management of Windows Server, it still collects power usage data for analysis and reporting.

## Exclude other computers

If you have computers that you don't want to manage with power management, add these computers to an exclusion collection.

You might want to exclude from power management the following types of computers:

- Computers that must remain turned on.
- Computers that users need to connect to remotely.
- Computers that can't use power management.
- Computers that have the distribution point site system role.
- Public computers such as kiosk computers, information displays, or monitoring consoles where the computer and the monitor must always be turned on.

For more information, see [Configuring power management](configuring-power-management).

## Apply power plans to a test collection

Always test the effect of applying a power management plan on a test collection of computers before you apply the power plan to a larger collection of computers.

When you exclude a computer from power management, all power settings revert to their original values. You can't revert individual power settings to their original values.

## Apply power plan settings individually

Monitor the effect of applying each power setting before you apply the next one. This process makes sure that each setting has the required effect. For more information about power plan settings, see [Available power management plan settings](create-and-apply-power-plans#BKMK_Plans).

## Regularly monitor computers for multiple power plans

Power management includes a report that displays computers that have more than one power plan applied: **Computers with Multiple Power Plans**.

If a computer is a member of multiple collections, each applying different power plans, then the following behaviors apply:

- **Power plan**: If you apply multiple values for power settings to a computer, it uses the least restrictive value.
- **Wakeup time**: If you apply multiple wakeup times to a desktop computer, it uses the time closest to midnight.

For more information, see [Computers with multiple power plans](monitor-and-plan-for-power-management#BKMK_Multiple).

## Save or export power management information

When you run reports during the monitoring and compliance phases, save or export the results. Keep the data for later comparison in case Configuration Manager later removes the data.

Configuration Manager keeps in the site database the following power management information:

- Power management information used by daily reports: 31 days
- Power management information used by monthly reports: 13 months