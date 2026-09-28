---
layout: Conceptual
title: Intune endpoint security Account protection (Preview) policy settings - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-account-protection-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Endpoint security Account protection policy settings in Microsoft Intune
ms.date: 2024-07-23T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: juidaewo
locale: en-us
document_id: c07d3105-a603-a053-e0c5-16a69815aa9d
document_version_independent_id: c07d3105-a603-a053-e0c5-16a69815aa9d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-account-protection-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-account-protection-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-account-protection-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c9f2fb28-8ae0-580c-7aff-5c35452aa050
---

# Intune endpoint security Account protection (Preview) policy settings - Microsoft Intune | Microsoft Learn

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Important

In July 2024, the following Intune profiles for identity protection and account protection were deprecated and replaced by a new consolidated profile named *Account protection*. This newer profile is found in the account protection policy node of endpoint security, and is the only profile template that remains available to create new policy instances for identity and account protection. The settings from this new profile are also available through the settings catalog.

Any instances of the following older profiles that you have created remain available to use and edit:

- **Identity protection** – previously available from *Devices* &gt; *Configuration* &gt; *Create* &gt; *New Policy* &gt; *Windows 10 and later* &gt; *Templates* &gt; *Identity Protection*
- **Account protection (Preview)** – previously available from *Endpoint Security* &gt; *Account protection* &gt; *Windows 10 and later* &gt; *Account protection ( Preview)*

This article describes settings that are available in profiles for *Account protection (preview)*, which is a profile type that was previously available through the *Account protection* policy for Intune [Endpoint security](manage-policies). Although you cannot create new instances of this profile, the information in this article applies to instances of the profile you might still have in use.

The settings in this article apply to:

- Windows

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Supported platforms and profiles:

- **Windows 10 and later**:
    - Profile: **Account protection (Preview)**

Tip

For *Local user group membership* profiles, see [Manage local groups on Windows devices](account-protection#manage-local-groups-on-windows-devices).

For *Local admin password solution (Windows LAPS)* profiles, see [Manage LAPS policy](../../device-security/laps/deploy-policy).

## Account protection profile (Preview)

*The following settings details apply only to the endpoint security profile template for Account protection (Preview), which was deprecated in July 2024.*

- **Block Windows Hello for Business**

    Windows Hello for Business is an alternative method for signing in to Windows by replacing passwords, Smart Cards, and Virtual Smart Cards.

    - **Not configured** (*default*) - Devices provision Windows Hello for Business.
    - **Disabled** - Devices provision Windows Hello for Business. With this configuration, more settings are available that support configurations for PIN, Trusted Platform Module (TPM), and more.
    - **Enabled** - Devices don't provision Windows Hello for Business for any user

Important

Due to how Intune determines the scope and applicability of Windows Hello for Business policy, the device may log **Event ID 454** as a result of applying policy. This can be safely ignored when policy is being successful applied (and enforced).

- **Enable to use security keys for sign-in**

    Enable Windows Hello security key as a sign-in credential for all PCs in the tenant.

    - **Not configured** (*default*)
    - **Yes**
- **Turn on Credential Guard**[CSP: DeviceGuard](https://go.microsoft.com/fwlink/?linkid=872424)

    Credential Guard uses Windows Hypervisor to provide protections. Credential Guard requires hardware support for Secure Boot and DMA protections. This setting is only successful on devices that meet the hardware requirements.

    - **Not configured** (*default*) - Disable the use of Credential Guard, which is the Windows default.
    - **Enable with UEFI lock** - Enable Credential Guard and block it from being turned off remotely, as the UEFI persisted configuration must be manually cleared.
    - **Enable without UEFI lock** - Enable Credential Guard and allow it to be turned off without physical access to the machine.