---
layout: Conceptual
title: Introduction to the tutorial for deploying and managing devices in a school - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Introduction to deployment and management of devices in education environments.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 347077f2-c4a2-f108-11f7-b03aaed965f0
document_version_independent_id: 347077f2-c4a2-f108-11f7-b03aaed965f0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 3114a8a5-4377-8017-e336-3bcc56ac8efb
---

# Introduction to the tutorial for deploying and managing devices in a school - Microsoft Intune | Microsoft Learn

This guide introduces the tools and services available from Microsoft to deploy, configure, and manage devices in an education environment.

## Audience and user requirements

This tutorial is intended for education professionals responsible for deploying and managing devices, including:

- School leaders
- IT administrators
- Teachers
- Microsoft partners

This content provides a comprehensive path for schools to deploy and manage new devices with Microsoft Intune. It includes step-by-step information how to manage devices throughout their lifecycle.

Note

Depending on your school setup scenario, you may not need to implement all steps.

## Device lifecycle management

School IT administrators and educators need an easy-to-use, flexible, and secure way to manage the lifecycle of the devices in their schools. Microsoft has developed integrated suites of products for streamlined, cost-effective device lifecycle management.

Microsoft 365 Education provides tools and services that enable simplified management of all devices through Microsoft Intune services. With Microsoft's solutions, IT administrators have the flexibility to support diverse scenarios, including school-owned devices and bring-your-own devices.

Microsoft Intune services include:

- [Microsoft Intune](../../../fundamentals/what-is-intune)
- [Microsoft Intune for Education](/en-us/intune-education/what-is-intune-for-education)
- [Windows Autopilot](/en-us/autopilot/windows-autopilot)
- [Microsoft Surface Management Portal](../../../device-management/tools/surface-management-portal)

These services are part of the Microsoft 365 stack to help secure access, protect data, and manage risk.

## Why Intune?

Devices can be managed with Intune, enabling simplified management of multiple devices from a single point.

From enrollment, through configuration and protection, to resetting, Intune helps school IT administrators manage and optimize the devices throughout their lifecycle:

![The device lifecycle for Intune-managed devices](media/index/device-lifecycle.png)

- **Enroll:** to enable remote device management, devices must be enrolled in Intune with an account in your Microsoft Entra tenant. Some enrollment methods require an IT administrator to initiate enrollment, while others require students to complete the initial device setup process. This document discusses the facets of various device enrollment methodologies
- **Configure:** once the devices are enrolled in Intune, applications and settings are applied.
- **Protect and manage:** in addition to its configuration capabilities, Intune helps protect devices from unauthorized access or malicious attacks. For example, managing Defender Antivirus and Bitlocker can make devices more secure. Policies are available that let you control settings for Windows Firewall, Endpoint Protection, and software updates
- **Retire:** when it's time to repurpose a device, Intune offers several options, including resetting the device, removing it from management, or wiping school data. In this document, we cover different device return and exchange scenarios

## Four pillars of modern device management

In the remainder of this tutorial, we discuss the key concepts and benefits of modern device management with Microsoft 365 solutions for education. The guidance is organized around the four main pillars of modern device management:

- **Identity management:** setting up and configuring the identity system, with Microsoft 365 Education and Microsoft Entra ID, as the foundation for user identity and authentication
- **Initial setup:** setting up the Intune environment for managing devices, including configuring settings, deploying applications, and defining updates cadence
- **Device enrollment:** Setting up devices for deployment and enrolling them in Intune
- **Device reset:** Resetting managed devices with Intune