---
layout: Conceptual
title: Enroll a Linux device in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-linux
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Enroll a work provided Linux device in Microsoft Intune to get secure access to work or school resources in Microsoft Edge.
ms.date: 2026-03-31T00:00:00.0000000Z
ms.reviewer: arnab
locale: en-us
document_id: 2e800209-7218-1d67-90b6-3b2602caa6c5
document_version_independent_id: 2e800209-7218-1d67-90b6-3b2602caa6c5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/enrollment/enroll-linux.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/enrollment/enroll-linux
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/enrollment/enroll-linux.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
platformId: fc602d95-9116-5ebb-a5d4-0a77c4f91a31
---

# Enroll a Linux device in Intune - Microsoft Intune | Microsoft Learn

Enroll a Linux device in Microsoft Intune to get secure access to work or school resources in Microsoft Edge. This article describes how to enroll and register a work or school-provided device on your organization's network.

## System requirements

Enrollment is supported on the following versions of Linux:

- Ubuntu Desktop, version 24.04 LTS or 26.04 LTS (physical, Azure VM, or Hyper-V machine with x86/64 CPUs)
- RedHat Enterprise Linux 9
- RedHat Enterprise Linux 10

Devices must be configured with a GNOME graphical desktop environment, which is automatically included with Ubuntu Desktop, version 24.04 LTS and 26.04 LTS.

Linux devices enrolled with Microsoft Intune are considered corporate-owned devices. Device enrollment isn't supported with personal devices.

We recommend enabling encryption when you first install Ubuntu Desktop on your device. Your organization may require your device to be encrypted, and it's easiest to encrypt the device during OS installation. For help with setting up Ubuntu Desktop, see the following resources on the Ubuntu website:

- [Ubuntu desktop downloads](https://ubuntu.com/download/desktop)
- [How to install Ubuntu desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

## Prerequisites

Install these apps on your device prior to enrollment:

- [Microsoft Edge web browser, version 102.*X* or later](https://www.microsoft.com/edge): The Edge browser is used to access your organization's websites and other online resources.
- [Microsoft Intune app](../company-portal/intune-app-linux): The Linux version of the Microsoft Intune app is used for enrollment. The Intune app registers your device with your org and enrolls it in Intune.

Note

When a new update becomes available for the Microsoft Intune app, your device might briefly register again during the update. You don’t need to take any action when that happens.

## Enroll device

Follow these steps to register a Linux device on your organization's network.

1. Open the Microsoft Intune app.
2. Sign in with your work or school account.
3. Review the pre-enrollment screens. Then select **Next** to begin enrollment.
4. Wait a few minutes while the Intune app enrolls your device.
    1. If instructed to, update the settings on your device to meet your organization's security requirements.
    2. An on-screen confirmation appears when your device is enrolled and ready-to-use for work. You can begin using your device for work right away.
    3. Sign in to Microsoft Edge with your work or school account to access your org's internal websites.

Note

Ubuntu on WSL2 is not a supported scenario.