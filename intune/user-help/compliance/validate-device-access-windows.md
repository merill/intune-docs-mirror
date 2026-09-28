---
layout: Conceptual
title: Check device access in Company Portal for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/validate-device-access-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Check device access to find out if your device meets requirements, and is able to access work or school resources.
ms.date: 2025-09-03T00:00:00.0000000Z
ms.reviewer: madakeva
locale: en-us
document_id: 54d04931-3620-5b0b-e1af-2eff57d46c46
document_version_independent_id: 54d04931-3620-5b0b-e1af-2eff57d46c46
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/validate-device-access-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/validate-device-access-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/validate-device-access-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: b5b720b0-5b8c-b875-20f2-2f4df5943e5a
---

# Check device access in Company Portal for Windows - Microsoft Intune | Microsoft Learn

Verify that your device has access to work or school resources. The *check access* action in Company Portal evaluates your device's settings and its access status.

Organizations enforce requirements, such as encryption and password limits, to make sure only secure, trusted devices access their internal resources. Your device must meet and maintain these requirements to gain access. Complete the steps in this article to check access from the Company Portal app for Windows.

Note

If you don't have the Company Portal app installed, you can still [use the Company Portal website to check access](validate-status-company-portal-website).

## Check access

1. Open the Company Portal app for Windows and go to **Devices**.

![Screenshot of the Company Portal app for Windows highlighting the &quot;Devices&quot; option.](media/validate-device-access-windows/company-portal-windows-devices.png)
2. Select a device.
3. Under **Device status**, select **Check access**.

![Image of the Company Portal app Devices page highlighting the &quot;Check access&quot; button ](media/validate-device-access-windows/company-portal-windows-check-access.png)

    The app syncs your device with your organization's current requirements and checks to make sure your device matches them. This check can take a few minutes.
4. Look at the status update.

    - **Can access company resources**: No other action needed.
    - **Cannot access company resources**: Take the required remediation actions to regain access to company resources. After you update flagged settings, select **Check access** to recheck access.
    - **Can access company resources, but action required**: Take the required remediation actions by the specified date or lose access to company resources. After you update flagged settings, select **Check access** to recheck access.
5. When applicable, the status message shows Microsoft Learn help links and remediation actions. To start troubleshooting right away, select one or more of the options. The *resolve*, *check access*, and *contact* actions in the following list are only visible when you're using Company Portal on the affected device.

    - **How to resolve this** opens a relevant help article, if available.
    - **Resolve** redirects you to the setting on your device.
    - **Check access** evaluates your device again to make sure it matches your organization's requirements.
    - **Contact IT** redirects you to your IT team's contact information.

Need more help? Find your company support's contact information on the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).