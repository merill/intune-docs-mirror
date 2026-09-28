---
layout: Conceptual
title: Get the Microsoft Intune app for Linux - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/company-portal/intune-app-linux
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Describes how to install, update, and remove the Microsoft Intune app for Linux.
ms.date: 2026-03-31T00:00:00.0000000Z
ms.reviewer: arnab
locale: en-us
document_id: cd289f04-c40c-8c36-0d8c-03dddedc53b4
document_version_independent_id: cd289f04-c40c-8c36-0d8c-03dddedc53b4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/company-portal/intune-app-linux.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/company-portal/intune-app-linux
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/company-portal/intune-app-linux.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7bed8ad5-7a9f-289b-7ba5-3393c43b1590
---

# Get the Microsoft Intune app for Linux - Microsoft Intune | Microsoft Learn

This article describes how to install, update, and remove the Microsoft Intune app for Linux on a personal device.

The Microsoft Intune app package is available at https://packages.microsoft.com/. For more information about how to use, install, and configure Linux software packages for Microsoft products, see [Linux Software Repository for Microsoft Products](/en-us/windows-server/administration/linux-package-repository-for-microsoft-software).

## Requirements

The Microsoft Intune app is supported with the following operating systems:

- Ubuntu Desktop, version 24.04 LTS or 26.04 LTS (physical or Hyper-V machine with x86/64 CPUs)
- RedHat Enterprise Linux 9
- RedHat Enterprise Linux 10

## Install Microsoft Intune app for Ubuntu Desktop

A sample script to install the Microsoft Intune app and its dependencies on your device is available on [GitHub](https://go.microsoft.com/fwlink/?linkid=2358529). Review the instructions carefully before installing.

### Uninstall app for Ubuntu Desktop

Run the following commands to uninstall the Microsoft Intune app and remove local registration data from devices running Ubuntu Desktop.

1. Remove the Intune app from your system.

    ```bash
    sudo apt remove intune-portal
    ```
2. Remove the local registration data. This command removes the local configuration data that contains your device registration.

    ```bash
    sudo apt purge intune-portal
    ```

## Install Microsoft Intune app for RedHat Enterprise Linux

A sample script to install the Microsoft Intune app and its dependencies on your device is available on [GitHub](https://go.microsoft.com/fwlink/?linkid=2358529). Review the instructions carefully before installing.

### Uninstall app for RedHat Enterprise Linux

Run the following commands to uninstall the Microsoft Intune app and remove local registration data on devices running RedHat Enterprise Linux.

1. Remove the Intune portal package.

    ```bash
    sudo dnf remove intune-portal
    ```
2. Remove local registration data.

    ```bash
    sudo rm -rf /var/opt/microsoft/mdatp
    sudo rm -rf /etc/opt/microsoft/mdatp
    sudo rm -rf /opt/microsoft/mdatp
    ```