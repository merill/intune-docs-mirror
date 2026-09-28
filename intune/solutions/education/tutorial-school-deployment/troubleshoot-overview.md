---
layout: Conceptual
title: Troubleshoot Windows devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/troubleshoot-overview
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn how to troubleshoot Windows devices from Intune and contact Microsoft Support for issues related to Intune and other services.
ms.date: 2024-05-02T00:00:00.0000000Z
zone_pivot_groups: platforms-windows-ios
ms.topic: tutorial
locale: en-us
document_id: 41f211be-11fe-254e-deff-9e9ccca0b6c9
document_version_independent_id: 41f211be-11fe-254e-deff-9e9ccca0b6c9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/troubleshoot-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/troubleshoot-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/troubleshoot-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4023ea41-afb5-0bb9-4769-47cf72bf9a9b
---

# Troubleshoot Windows devices - Microsoft Intune | Microsoft Learn

Microsoft Intune provides many tools that can help you troubleshoot devices.

- [Troubleshooting device enrollment in Intune](/en-us/troubleshoot/mem/intune/troubleshoot-device-enrollment-in-intune)
- [Troubleshooting policies and profiles in Microsoft Intune](/en-us/troubleshoot/mem/intune/troubleshoot-policies-in-microsoft-intune)
- [Troubleshooting device actions in Intune](/en-us/troubleshoot/mem/intune/troubleshoot-device-actions)

::: zone pivot="windows"

Here's a collection of resources to help you troubleshoot Windows devices managed by Intune:

- [Troubleshooting Windows Autopilot overview](/en-us/autopilot/troubleshooting-faq#troubleshooting-windows-autopilot-overview)
- [Troubleshoot Windows Wi-Fi profiles](/en-us/troubleshoot/mem/intune/troubleshoot-wi-fi-profiles#troubleshoot-windows-wi-fi-profiles)
- [Troubleshooting BitLocker with the Intune encryption report](/en-us/troubleshoot/mem/intune/troubleshoot-bitlocker-admin-center)
- [Troubleshooting custom settings](/en-us/troubleshoot/mem/intune/troubleshoot-csp-custom-settings)
- [Troubleshooting Win32 app installations with Intune](/en-us/troubleshoot/mem/intune/troubleshoot-win32-app-install)
- [**Collect diagnostics**](../../../device-management/actions/collect-diagnostics) is a remote action that lets you collect and download Windows device logs without interrupting the user [![Intune for Education dashboard](media/troubleshoot-overview/intune-diagnostics.png)](media/troubleshoot-overview/intune-diagnostics.png#lightbox)

::: zone-end

::: zone pivot="ios"

Here's a collection of resources to help you troubleshoot iOS devices managed by Intune:

- [iOS or iPadOS devices aren't checking in with the Intune service](/en-us/troubleshoot/mem/intune/device-enrollment/ios-devices-inactive)
- [Troubleshooting iOS/iPadOS device enrollment errors in Microsoft Intune](/en-us/troubleshoot/mem/intune/device-enrollment/troubleshoot-ios-enrollment-errors)
- [iOS or iPadOS device is stuck on an enrollment screen](/en-us/troubleshoot/mem/intune/device-enrollment/device-stuck-in-enrollment)
- [Troubleshooting profile installation failed error on iOS or iPadOS devices](/en-us/troubleshoot/mem/intune/device-enrollment/profile-installation-failed)
- [Intune enrollment process doesn't start on Apple Automated Device Enrollment devices](/en-us/troubleshoot/mem/intune/device-enrollment/apple-dep-device-fails-auto-enrollment)
- [ADE enrollment error 'XPC_TYPE_ERROR Connection invalid'](/en-us/troubleshoot/mem/intune/device-enrollment/dep-enrollment-xpc-type-error)
- [You can't access company resources on an Intune-enrolled ADE device](/en-us/troubleshoot/mem/intune/device-protection/cannot-access-company-resources-on-dep)

::: zone-end

## How to contact Microsoft Support

Microsoft provides global technical, pre sales, billing, and subscription support for cloud-based device management services. This support includes Microsoft Intune, Configuration Manager, Windows 365, and Microsoft Managed Desktop.

Follow these steps to obtain support in Microsoft Intune provides many tools that can help you troubleshoot Windows devices:

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- Select **Troubleshooting + support** &gt; **Help and support**. [![Screenshot that shows how to obtain support from Microsoft Intune.](media/troubleshoot-overview/advanced-support.png)](media/troubleshoot-overview/advanced-support.png#lightbox)
- Select the required support scenario: Configuration Manager, Intune, Co-management, or Windows 365.
- Above **How can we help?**, select one of three icons to open different panes: *Find solutions*, *Contact support*, or *Service requests*.
- In the **Find solutions**pane, use the text box to specify a few details about your issue. Depending on the presence of specific keywords, the console provides help like:
    - Run diagnostics: start automated tests and investigations of your tenant from the console to reveal known issues. When you run a diagnostic, you may receive mitigation steps to help with resolution.
    - View insights: find links to documentation that provides context and background specific to the product area or actions relating to your issue.
    - Recommended articles: browse suggested troubleshooting topics and other content related to your issue.
- If needed, use the *Contact support* pane to file an online support ticket. 
    Important

    When opening a case, be sure to include as many details as possible in the *Description* field. Such information includes: timestamp and date, device ID, device model, serial number, OS version, and any other details relevant to the issue.
- To review your case history, select the **Service requests** pane. Active cases are at the top of the list, with closed issues also available for review.

For more information, see [Microsoft Intune support page](/en-us/mem/get-support).