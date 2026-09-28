---
layout: Conceptual
title: Add custom settings to Linux devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings-linux
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Add Bash scripts to create a custom Linux profile in Microsoft Intune. Use the script to create, use, and control custom settings and features on Linux devices. This custom profile can then be assigned or distributed to Linux devices in your organization to create a baseline or standard.
ms.date: 2025-01-09T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: arnab
locale: en-us
document_id: 913c3c0d-a01b-c4b9-7c98-2a8e03e8b2ce
document_version_independent_id: 913c3c0d-a01b-c4b9-7c98-2a8e03e8b2ce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-custom-settings-linux.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-custom-settings-linux
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-custom-settings-linux.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 1cd1ef3a-4c53-e7e7-bfaf-2c8c238b52f7
---

# Add custom settings to Linux devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

Custom configuration profiles shouldn't be used for sensitive information, such as WiFi connections or authenticating apps, sites, and more.

Using Microsoft Intune, you can add or create custom configuration settings for your Linux devices using custom Bash scripts. They're designed to add device settings and features that aren't built in to Intune.

In Intune, you import an existing Bash script, and then assign the script policy to your Linux users and devices. Once assigned, the settings are distributed. They also create a baseline or standard for Linux in your organization.

This article lists the steps to add an existing script and has a GitHub repo with some sample scripts.

## Prerequisites

- **Linux Ubuntu Desktop**, **RedHat Enterprise Linux 8**, or **RedHat Enterprise Linux 9**: For a list of the supported versions, go to [Supported operating systems and browsers in Intune](../../fundamentals/ref-supported-platforms).
- **Linux devices are enrolled in Intune**. For more information on Linux enrollment, go to [Enrollment guide: Enroll Linux desktop devices in Microsoft Intune](../../device-enrollment/guide-linux).

## Import the script

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Scripts and remediations** &gt; **Platform scripts** tab &gt; **Add** &gt; **Linux**:

    ![Screenshot that shows how to select devices, scripts, add, and select Linux from the drop-down list to add a custom Bash script in Microsoft Intune.](media/configure-custom-settings-linux/add-linux-script.png)
3. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later.
    - **Description**: Enter a description for the policy. This setting is optional, but recommended.
4. Select **Next**.
5. In **Configuration settings**, configure the following settings:

    - **Execution context**: Select the context the script is executed in. Your options:

        - **User** (default): When a user signs in to the device, the script runs. If a user never signs into the device, or there isn't any user affinity, then the script doesn't run.
        - **Root**: The script always runs (with or without users logged in) at the device level. The first time the script executes, the end user might have to consent. After they consent, it should continue to execute on its schedule.
    - **Execution frequency**: Select how frequently the script is executed. The default is **Every 15 minutes**.
    - **Execution retries**: If the script fails, enter how many times Intune should retry running the script. The default is **No retries**.
    - **Execution Script**: Select the file picker to upload an existing Bash script. Only add `.sh` files.

        Microsoft has some sample Bash scripts at https://github.com/microsoft/shell-intune-samples/tree/master/Linux.
    - **Bash Script**: After you add an existing Bash script, the script text is shown. You can edit this script.
6. Select **Next**.
7. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
8. In **Assignments**, select the users or groups that will receive your profile. For more information on assigning profiles, see [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
9. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.