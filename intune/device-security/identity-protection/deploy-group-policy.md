---
layout: Conceptual
title: Deploy policy for Windows Hello to groups of Windows devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/identity-protection/deploy-group-policy
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: protect
description: Use a Microsoft Intune profile for Identity protection configure Windows Hello for Business on Windows devices.
ms.date: 2024-07-23T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-identity-device-management
- identity-protection
- sub-secure-endpoints
locale: en-us
document_id: 6ca146b7-dcef-f85b-8d9d-63705dd828f2
document_version_independent_id: 6ca146b7-dcef-f85b-8d9d-63705dd828f2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/identity-protection/deploy-group-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/identity-protection/deploy-group-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/identity-protection/deploy-group-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/798bd9d1-9cc5-4fc7-b0e5-8699d1f6ce2a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b5dc5f65-34a8-4bfc-9917-97d1e20c88b2
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: cf7a16e7-4cc4-db18-94d4-057d0f9997b5
---

# Deploy policy for Windows Hello to groups of Windows devices - Microsoft Intune | Microsoft Learn

Important

In July 2024, the following Intune profiles for identity protection and account protection were deprecated and replaced by a new consolidated profile named *Account protection*. This newer profile is found in the account protection policy node of endpoint security, and is the only profile template that remains available to create new policy instances for identity and account protection. The settings from this new profile are also available through the settings catalog.

Any instances of the following older profiles that you have created remain available to use and edit:

- *Identity protection* – previously available from *Devices* &gt; *Configuration* &gt; *Create* &gt; *New Policy* &gt; *Windows 10 and later* &gt; *Templates* &gt; *Identity Protection*
- *Account protection (Preview)* – previously available from *Endpoint Security* &gt; *Account protection* &gt; *Windows 10 and later* &gt; *Account protection ( Preview)*

Microsoft Intune supports use of *Account protection* profiles to manage Windows Hello for Business on your managed Windows devices. [Windows Hello for Business](/en-us/windows/security/identity-protection/hello-for-business/hello-overview) is a method for signing in to Windows devices by replacing passwords, smart cards, and virtual smart cards.

Applies to:

- Windows

When you use Intune Account protection profiles to manage Windows Hello for Business settings, you can:

- Enable Windows Hello for Business for devices and users
- Set device PIN requirements, including a minimum or maximum PIN length
- Allow gestures, such as a fingerprint, that users can (or can't use) to sign in to devices

In addition to Account protection profiles, Intune supports the following options to manage settings for Windows Hello for Business:

- [During device enrollment](configure-tenant-wide-policy): Configure tenant-wide policy that applies Windows Hello settings to devices at the time the device enrolls with Intune.
- [Security baselines](../security-baselines/overview): Some settings for Windows Hello can be managed through Intune's security baselines, like the baselines for *Microsoft Defender for Endpoint security* or *Security Baseline for Windows 10 and later*.
- [Settings catalog](../../device-configuration/settings-catalog/): The settings from endpoint security Account protection profiles are available in the Intune settings catalog.

Note

For customers looking to configure Windows Holographic for Business, please use [DeviceLock CSP](/en-us/windows/client-management/mdm/policy-csp-devicelock)