---
layout: Conceptual
title: Overview of Windows Autopilot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/overview
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Windows Autopilot is a collection of technologies used to set up and pre-configure new devices, getting them ready for productive use.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: overview
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
locale: en-us
document_id: 20b3bc80-6f76-d211-ed90-8934ff1e36a9
document_version_independent_id: 20b3bc80-6f76-d211-ed90-8934ff1e36a9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/overview.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 94722b14-4f9f-9df0-679e-19cea978ce3e
---

# Overview of Windows Autopilot | Microsoft Learn

Windows Autopilot is a collection of technologies used to set up and pre-configure new devices, getting them ready for productive use. Windows Autopilot can be used to deploy Windows PCs or HoloLens 2 devices. For more information about deploying HoloLens 2 with Windows Autopilot, see [Windows Autopilot for HoloLens 2](/en-us/hololens/hololens2-autopilot).

Windows Autopilot can also be used to reset, repurpose, and recover devices. This solution enables an IT department to achieve these goals with little to no infrastructure to manage, with a process that's easy and simple.

Windows Autopilot simplifies the Windows device lifecycle, for both IT and end users, from initial deployment to end of life. Using cloud-based services, Windows Autopilot:

- Reduces the time IT spends on deploying, managing, and retiring devices.
- Reduces the infrastructure required to maintain the devices.
- Maximizes ease of use for all types of end users.

See the following video:

Note

This article is for **Windows Autopilot**. For **Windows Autopilot device preparation**, see [Overview of Windows Autopilot device preparation](device-preparation/overview).

## Process overview

When new Windows devices are initially deployed, Windows Autopilot uses the OEM-optimized version of Windows client. This version is preinstalled on the device, so custom images and drivers for every device model don't have to be maintained. Instead of re-imaging the device, the existing Windows installation can be transformed into a "business-ready" state that can:

- Apply settings and policies.
- Install apps.
- Change the edition of Windows being used to support advanced features. For example, from Windows Pro to Windows Enterprise.

![Process overview.](images/image1.png)

Once deployed, Windows devices can be managed with:

- Microsoft Intune.
- Windows Update client policies.
- Microsoft Configuration Manager.
- Other similar tools from non-Microsoft parties.

## Requirements

A [supported version](/en-us/windows/release-information/) of Windows semi-annual channel is required to use Windows Autopilot. For more information, see [Windows Autopilot software](requirements?tabs=software), [networking](requirements?tabs=networking), [configuration](requirements?tabs=configuration), and [licensing](requirements?tabs=licensing) requirements.

## Summary

Traditionally, IT pros spend significant time building and customizing images that are later deployed to devices. Windows Autopilot introduces a new approach.

- From the user's perspective, it only takes a few simple operations to make their device ready to use.
- From the IT pro's perspective, the only interaction required from the end user is to connect to a network and to verify their credentials. Everything beyond that is automated.

Windows Autopilot enables the following functionality:

- Automatic joining of devices to Microsoft Entra ID or Active Directory (via Microsoft Entra hybrid join). For more information about the differences between these two join options, see [Introduction to device management in Microsoft Entra ID](/en-us/azure/active-directory/device-management-introduction).
- Auto-enrollment of devices into mobile device management (MDM) services, such as Microsoft Intune ([*Requires a Microsoft Entra ID P1 or P2 subscription for configuration*](/en-us/windows/client-management/mdm/azure-ad-and-microsoft-intune-automatic-mdm-enrollment-in-the-new-portal)).
- Creation and auto-assignment of devices to configuration groups based on a device's profile.
- Customization of the out-of-box experience (OOBE) content specific to the organization.

Existing device can also be quickly prepared for a new user with [Windows Autopilot Reset](windows-autopilot-reset). The Reset capability is also useful in break/fix scenarios to quickly bring a device back to a business-ready state.

## Tutorial

For a tutorial with detailed instructions on configuring Windows Autopilot, see [Windows Autopilot scenarios](tutorial/autopilot-scenarios).