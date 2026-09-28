---
layout: Conceptual
title: Management functionalities for Surface devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/manage-surface
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn about the management capabilities offered to Surface devices, including firmware management and the Surface Management Portal.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 8e40f79e-02ee-43a6-7249-9ea4a39a3201
document_version_independent_id: 8e40f79e-02ee-43a6-7249-9ea4a39a3201
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/manage-surface.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/manage-surface
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/manage-surface.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
platformId: 876bdbe7-39b5-f605-b2b3-28396fb4943a
---

# Management functionalities for Surface devices - Microsoft Intune | Microsoft Learn

Microsoft Surface devices offer advanced management functionalities, including the possibility to manage firmware settings and a web portal designed for them.

## Manage device firmware for Surface devices

Surface devices use a Unified Extensible Firmware Interface (UEFI) setting that allows you to enable or disable built-in hardware components, protect UEFI settings from being changed, and adjust device boot configuration. With [Device Firmware Configuration Interface profiles built into Intune](../../../device-configuration/templates/ref-dfci-settings-windows), Surface UEFI management extends the modern management capabilities to the hardware level. Windows can pass management commands from Intune to UEFI for Windows Autopilot-deployed devices.

DFCI supports zero-touch provisioning, eliminates BIOS passwords, and provides control of security settings for boot options, cameras and microphones, built-in peripherals, and more. For more information, see [Manage DFCI on Surface devices](/en-us/surface/surface-manage-dfci-guide) and [Manage DFCI with Windows Autopilot](/en-us/autopilot/dfci-management), which includes a list of requirements to use DFCI.

[![Creation of a DFCI profile from Microsoft Intune](media/manage-surface/dfci-profile.png)](media/manage-surface/dfci-profile.png#lightbox)

## Microsoft Surface Management Portal

Located in the Microsoft Intune admin center, the Microsoft Surface Management Portal enables you to self-serve, manage, and monitor your school's Intune-managed Surface devices at scale. Get insights into device compliance, support activity, warranty coverage, and more.

When Surface devices are enrolled in cloud management and users sign in for the first time, information automatically flows into the Surface Management Portal, giving you a single pane of glass for Surface-specific administration activities.

To access and use the Surface Management Portal:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Partner Portals** &gt; **Surface Management Portal**. [![Surface Management Portal within Microsoft Intune](media/manage-surface/surface-management-portal.png)](media/manage-surface/surface-management-portal.png#lightbox)
3. See an **Overview**of your Surface devices.
    - Devices that are out of compliance or not registered, have critically low storage, require updates, or are currently inactive, are listed here.
4. To obtain details on each insights category, select **Insights**.
    - This dashboard displays diagnostic information that you can customize and export.
5. To obtain the device's warranty information, select **Insights**.
6. To review a list of support requests and their status, select **Support**.