---
layout: Conceptual
title: Company Portal device setting requirements for Mac - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/update-settings-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn more about Intune Company Portal device setting requirements for Macs.
ms.date: 2024-03-04T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: 7572d7b7-5b58-c4e3-ac0e-be3eeef64fd6
document_version_independent_id: 7572d7b7-5b58-c4e3-ac0e-be3eeef64fd6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/update-settings-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/update-settings-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/update-settings-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: f803b6af-03b2-320d-02ef-0d2893e729e9
---

# Company Portal device setting requirements for Mac - Microsoft Intune | Microsoft Learn

This article describes the macOS device setting requirements that the Intune Company Portal can enforce on behalf of your workplace or school. Company Portal enforces these requirements on behalf of your workplace or school to ensure your device is secure while accessing their network. Requirements are specific to each organization. You only need to update the device settings that Company Portal flags.

## Device limit reached

To prevent unauthorized access to internal data, your school or workplace might limit the number of devices you can register. If you reach the device limit, we recommend removing one of your devices or contacting your support person to increase the device limit. Your options:

- Remove a device in Company Portal.
- Contact your IT support person and ask if they can increase the number of devices allowed to register.

## Identify device

If Company Portal prompts you to identify your device during enrollment, then there is another enrolled device associated with your work account. In this case, the device was enrolled via a method other than the Company Portal app. To resolve this message, select your device from the list in Company Portal.

If your device isn't listed:

1. Select **new device**.
2. Select **Continue**.
3. Enter the last four characters of your device's serial number. For more information, see [Find the serial number of your Apple product](https://support.apple.com/en-us/102858) on Apple Support.

## Update operating system version

Keeping your device up-to-date lets you access the newest features, and it also ensures that your device has the most secure version of its operating system. While using the device for work or school, we recommend keeping both personal and corporate devices up-to-date with the newest versions. Before updating your device, back up all of the information on it. Keeping a backup can help you recover your data if something should interrupt any updates, or lets you transfer your information to a replacement device.

To check your Mac for available software updates, go to **App Store** &gt; **Updates**. Select the newest macOS update available, and then select **Update**.

## Operating system isn't supported

The operating system (OS) version running on your device isn't supported. It's possible that the latest version of macOS doesn't work with your organization's apps, tools, and other internal infrastructure. To resolve this issue, contact your IT support person and find out what the OS requirements are for your device.

## Unable to get macOS device managed

If you receive these messages while trying to get your macOS device managed, contact your IT support person for help.

**Message 1**: *We're having trouble getting your device managed. This problem could be caused if you're using a virtual machine, have a restricted serial number, or if this device is already assigned to someone else. Learn how to resolve these problems or contact your company support.*

**Message 2**: *It looks like you're using a virtual machine. Make sure you've fully configured your virtual machine, including serial number and hardware model. If this isn't a virtual machine, please contact support.*

Your device may be blocked from enrolling for one of the following reasons:

- A macOS virtual machine (VM) isn't configured correctly.
- Your organization requires that the device is corporate-owned or has a registered device serial number.
- The device is already enrolled, and is assigned to someone else in your organization.

Your IT support person or IT administrator can help you identify and resolve the problem that applies to your device. For contact information, check the Company Portal app or [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).