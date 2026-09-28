---
layout: Conceptual
title: Device enrollment overview - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/enroll-overview
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn about the different options to enroll Windows devices in Microsoft Intune.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
zone_pivot_groups: platforms-windows-ios
locale: en-us
document_id: 82ec25d0-1998-bebb-6e8a-b2c50a700817
document_version_independent_id: 82ec25d0-1998-bebb-6e8a-b2c50a700817
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/enroll-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/enroll-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/enroll-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a4378bb1-4ead-0005-81a1-03852a687747
---

# Device enrollment overview - Microsoft Intune | Microsoft Learn

![The device lifecycle for Intune-managed devices - enrollment](media/shared/enroll.png)

In this section you will:

- Enroll your devices into Intune

Select one of the following options to learn the next steps about the enrollment method you chose:

::: zone pivot="windows"

- [Automatic Intune enrollment via Microsoft Entra join](enroll-entra-join)
- [Automatic Intune enrollment with provisioning packages](enroll-package)
- [Automatic Intune enrollment with Windows Autopilot](enroll-autopilot)

::: zone-end

::: zone pivot="ios"

- [Enroll with Company Portal](enroll-ios-company-portal)
- [Enroll devices with Automated Device Enrollment](enroll-ios-ade)
- [Enroll devices with Apple Configurator](enroll-ios-apple-configurator)

::: zone-end

Tip

See [Plan enrollment](enrollment-planning) for a comparison between the enrollment methods which describes the ideal scenarios for using either option. It's recommended to review the table when planning your enrollment and deployment strategies.