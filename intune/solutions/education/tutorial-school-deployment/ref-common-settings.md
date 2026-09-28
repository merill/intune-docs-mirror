---
layout: Conceptual
title: Common Education configuration overview - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-common-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: yegor-a
ms.author: egorabr
ms.subservice: education
description: Learn about common configuration used by Education organizations in Intune.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 4257aa4a-978b-575d-f390-9d235e7bbef8
document_version_independent_id: 4257aa4a-978b-575d-f390-9d235e7bbef8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/ref-common-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/ref-common-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/ref-common-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fc44c002-229d-fade-e886-bd6ba3e27b5c
---

# Common Education configuration overview - Microsoft Intune | Microsoft Learn

Intune is a powerful tool that can help Education organizations manage their devices and data efficiently. However, configuring the right settings can be a time-consuming task, especially for those new to the platform. To help accelerate the process, we have assembled common configurations based on customer engagements into this reference document. These settings can help ensure the security and compliance of your devices and data, while maximizing the user experience for your students and staff. Whether you're setting up a new tenant or need a quick reference guide, this document is a valuable resource for any Education organization looking to optimize their use of Intune.

## Guiding Principles and Methodology

The recommended settings in this document are built from real-world customer configurations, reflecting how Education organizations are currently using Microsoft Intune to manage their Windows and iPadOS devices. The goal is to provide policies that prevent unintentional use, maintain consistency across devices, and ensure that devices are used solely for educational purposes. At the same time, these settings optimize the overall device experience for students.

Key areas of focus include:

- **Disabling AI capabilities**: Keep students focused by preventing distractions and the inappropriate use of OS AI features.
- **Update experience**: Ensure that devices are secure and up to date, while minimizing disruptions during class time.
- **Disabling changes to settings**: Maintain consistent device configurations and prevent tampering by locking critical settings.
- **Browsing experience**: Protect student privacy and data by ensuring a safe browsing environment, free from distractions and potential security risks.

These policies are commonly used but not mandatory. Schools can tailor their configurations based on their specific needs, and optional policies are provided for more situational use cases.

Caution

Adding these settings to your existing Intune tenant and assigning them to devices could potentially cause conflicts with your existing Intune policies. For more information, see [Compliance and device configuration policies that conflict](../../../device-configuration/troubleshoot-device-profiles#conflicts) and [Avoiding policy conflicts](policy-conflicts).

## Intune policies for Windows in Education

### Configuration sections

- [Device restrictions](ref-device-restrictions-settings-windows)
- [Windows Update](ref-update-settings-windows)
- [Microsoft Edge](ref-edge-settings-windows)
- [Delivery Optimization](ref-delivery-optimization-settings-windows)

### Optional

- [Windows privacy](ref-privacy-settings-windows)
- [Start menu customization](ref-start-menu-settings-windows)
- [OneDrive Known Folder Move](ref-onedrive-knownfoldermove-settings-windows)

## Intune policies for iPads in Education

- [Device restrictions](ref-device-restrictions-settings-ipados)
- [Apple Intelligence](ref-ai-restrictions-settings-ipados)
- [iPads with no user affinity](ref-shared-device-settings-ipados)
- [Optional restrictions](ref-optional-restrictions-settings-ipados)