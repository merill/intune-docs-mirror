---
layout: Conceptual
title: Windows Autopilot with co-management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-autopilot
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
description: Use Windows Autopilot with co-management in Configuration Manager to simplify the set up of new Windows devices.
ms.date: 2021-11-08T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 6e969102-a98f-fcda-4bf3-7645f52a7896
document_version_independent_id: 92586124-bfff-4cde-3f07-cad9a61955f7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/quickstart-autopilot.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/quickstart-autopilot
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/quickstart-autopilot.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 15f554d9-d084-c275-a1fc-8409b91f7eb8
---

# Windows Autopilot with co-management - Configuration Manager | Microsoft Learn

Receiving a new Windows device is exciting. However, it can take time to configure all your settings and apps so that you can be productive. Co-management solves this device provisioning problem with Windows Autopilot.

Windows Autopilot provides a simplified experience for both you and your users in the following situations:

- Set up and pre-configure new Windows 10 or later devices
- Reset, recycle, and recover existing devices

Windows Autopilot reduces the time, resources, and complexity associated with deploying, managing, and retiring devices. At the same time, the experience for your users is streamlined and easy from first boot.

Windows Autopilot supports several scenarios, all of which are maximized with co-management:

- Users can drive their own deployments of new devices into Microsoft Entra ID
- You can set up self-deploying new device deployments into Microsoft Entra ID for shared devices and kiosks
- With Windows Autopilot for existing devices, use Configuration Manager to migrate an existing device from earlier versions of Windows and Active Directory to later versions of Windows and Microsoft Entra ID

In the following video, senior program manager Danny Guillory and principal program manager Andrew McMurray discuss and demo Windows Autopilot with co-management:

Note

[Introducing Windows Autopilot into co-management](autopilot-enrollment). When you use [Windows Autopilot](/en-us/autopilot/overview) to provision a device, it first enrolls to Microsoft Entra ID and Microsoft Intune. If the intended end-state of the device is co-management, previously this experience was difficult because of installation of Configuration Manager client as Win32 app which introduces component timing and policy delays.

## Benefits

When you use co-management and Windows Autopilot together, you make sure that new devices entering your network end up in the same state of management. In this setup, devices are enrolled in Intune and have a Configuration Manager client. It allows you to use the new Windows provisioning model, and helps you eliminate the need to create, maintain, and update custom OS images.

In all of these scenarios, you can automatically [enable co-management](how-to-prepare-win10) by Intune. This automation assists with the provisioning process, and for ongoing management of the device.

With Windows Autopilot, you don't need to worry about images and drivers. Focus on provisioning devices by this automated process using Intune and Configuration Manager via co-management.

Here's how using co-management and Windows Autopilot together can help you right now:

### Reduce time, costs, and complexity

Windows Autopilot uses the OEM-optimized version of Windows that's preinstalled on the device. This configuration saves organizations the effort of having to maintain custom images and drivers for every model of device in use. Instead of reimaging the device, transform the existing Windows installation into a "business-ready" state. It applies settings and policies, installs apps, and changes the edition of Windows. For example, upgrading from Windows 10 Pro to Windows 10 Enterprise so that you can support advanced features.

### Improve the user experience

The best user experience causes the least disruption and helps them get back to focusing on their work. Windows Autopilot offers a simple approach to help your users get set up quickly with a few simple clicks and their Microsoft Entra credentials. For many organizations with a large field of remote employees, use Windows Autopilot to ship new devices straight from the manufacturer.

### Use Windows Autopilot and Configuration Manager to migrate existing Windows devices to Windows 10 or later

With Windows Autopilot for existing devices, you create a configuration file and deploy it with a Configuration Manager task sequence. This process easily migrates existing devices from earlier versions of Windows to Windows 10 or later. You use a signature Windows 10 image in Configuration Manager, and then apply it to the existing Windows device with the Windows Autopilot configuration. When the user starts the device, they use the Windows Autopilot user-driven onboarding process.

Here are the steps for Windows Autopilot for existing devices:

![Process overview for Windows Autopilot for existing devices](media/autopilot-for-existing-devices.png)

1. Deploy group policy to redirect known folders to OneDrive
2. Generate Windows Autopilot configuration file
3. Deploy task sequence to upgrade to Windows 10 or later
4. The Windows machine goes through Windows Autopilot on first boot

### Modernizing device provisioning for all types of workers

With Windows Autopilot, you can now provide a hands-free OS deployment to unmanned devices or shared devices using the self-deploying mode. This setup meets the needs of all your different types of workers. Also, the Windows Autopilot Reset function makes sure that re-provisioning of a device to a new user is simple and easy. This process simplifies what has traditionally been a difficult task when you have seasonal or contract workers.

## Case study

The German logistics and rail freight company DB Schenker uses Windows Autopilot to increase employee productivity and free its IT teams from working on day-to-day support tasks. DB Schenker has moved away from traditional imaging and replaced it with provisioning via the cloud. They now use Microsoft Entra join and Intune to get new devices up and running quickly.

Rather than have their remote workers waste time traveling to a location with IT services, DB Schenker now uses Windows Autopilot. They ship their workers hardware directly from the manufacturer to their local field office. The worker connects the new device to the internet, and they sign in with their Microsoft Entra credentials. The device then connects to the applications and services that DB Schenker's IT department assigns to the user's individual profile.

## Value proposition

Create satisfaction in your organization by creating a better user experience for your users. Use Windows Autopilot to drive down costs. Free up your time to focus on other projects to drive more value and impact for your organization.

## Configure

For more information, see the following articles:

- [Windows Autopilot into co-management](autopilot-enrollment)
- [Create device groups](/en-us/autopilot/enrollment-autopilot)
- [Windows Autopilot for existing devices](/en-us/autopilot/existing-devices)