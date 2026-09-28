---
layout: Conceptual
title: Education device erollment with standard out-of-box experience (OOBE) and Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/enroll-entra-join
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn how to join devices to Microsoft Entra ID from OOBE and automatically get them enrolled in Intune.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: d14af554-26e0-0c92-5ea8-82c9547ada2d
document_version_independent_id: d14af554-26e0-0c92-5ea8-82c9547ada2d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/enroll-entra-join.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/enroll-entra-join
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/enroll-entra-join.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: b1a74348-8274-fd40-3388-769ce1e3494b
---

# Education device erollment with standard out-of-box experience (OOBE) and Intune - Microsoft Intune | Microsoft Learn

If you're setting up a Windows device individually, you can use the out-of-box experience to join it to your school's Microsoft Entra tenant, and automatically enroll it in Intune. With this process, no advance preparation is needed:

1. Follow the on-screen prompts for region selection, keyboard selection, and network connection.
2. Wait for updates. If any updates are available, they are installed at this time. ![Windows 11 OOBE - updates page](media/enroll-entra-join/win11-oobe-updates.png)
3. When prompted, select **Set up for work or school** and authenticate using your school's Microsoft Entra account. ![Windows 11 OOBE - authentication page](media/enroll-entra-join/win11-oobe-auth.png)
4. The device joins Microsoft Entra ID and automatically enroll in Intune. All settings defined in Intune are applied to the device.

Important

If you configured enrollment restrictions in Intune blocking personal Windows devices, this process will not complete. You will need to use a different enrollment method, or ensure that the devices are registered in Windows Autopilot.

![Windows 11 login screen](media/shared/win11-login-screen.png)