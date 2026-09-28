---
layout: Conceptual
title: Apple School Manager - create enrollment policy - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-2
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: annovich
ms.subservice: enrollment
description: Learn how to create the enrollment policy in Intune for Apple School Manager enrollment.
ms.date: 2026-04-29T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: af614a4c-797f-5880-c486-2c349a39c0c1
document_version_independent_id: af614a4c-797f-5880-c486-2c349a39c0c1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/school-manager-step-2.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/school-manager-step-2
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/school-manager-step-2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: be3ecd6a-3178-2dd0-25e1-6e37f2280f8a
---

# Apple School Manager - create enrollment policy - Microsoft Intune | Microsoft Learn

After you get your Apple token, you can create an enrollment policy for school devices. An essential part of setup is creating enrollment policies. The policies contain the settings that apply to devices during device enrollment.

## Create a policy

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices**.
2. Expand **Device onboarding**, and then select **Enrollment**.
3. Select the **Apple mobile** tab.
4. Under **Bulk Enrollment Methods**, choose **Enrollment program tokens**.
5. Choose a token, and then select **Enrollment policies**.
6. Select **Create policy** and choose the platform you're configuring:

    - iOS/iPadOS
    - tvOS
    - visionOS
7. For **Basics**, give the policy a **Name** and **Description** for administrative purposes. Users don't see these details.

    You can use the name you enter here to create a dynamic group in Microsoft Entra ID. To assign devices with this enrollment policy to a group, for example, enter the name in the *enrollmentPolicyName* parameter in your dynamic group rules. For more information, see [Microsoft Entra dynamic groups](/en-us/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).
8. Select **Next**.
9. On the **Configuration settings** tab, configure **User Affinity**. Decide if devices with this policy must enroll with an assigned user or without an assigned user. User affinity isn't supported on tvOS and visionOS devices.

    - **Enroll with User Affinity** - Choose this option for devices that belong to users and that want to use the company portal for services like installing apps. This option also lets users authenticate their devices by using the company portal. If using Active Directory Federation Services (AD FS), user affinity requires [WS-Trust 1.3 Username/Mixed endpoint](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff608241%28v=ws.10%29). [Learn more](/en-us/powershell/module/adfs/get-adfsendpoint). Apple School Manager's Shared iPad mode requires user enroll without user affinity.
    - **Enroll without User Affinity** - Choose this option for devices unaffiliated with a single user, such as a shared device. Use this option for devices that perform tasks without accessing local user data. Apps like the Company Portal app don't work.
10. If you chose **Enroll with User Affinity**, select how users must authenticate: Company Portal, Setup Assistant (legacy), or Setup Assistant with modern authentication. For more information about authentication methods, see [Authentication methods for automated device enrollment in Intune](ref-automated-authentication-methods).

    Note

    If you want any of the following features, set **Authenticate with Company Portal instead of Apple Setup Assistant** to **Yes**.

    - Use multifactor authentication
    - Prompt users who need to change their password when they first sign in
    - Prompt users to reset their expired passwords during enrollment

    These features aren't supported when authenticating with Apple Setup Assistant.
11. Choose if you want locked enrollment for devices using this policy. **Locked enrollment** disables Apple settings that allow the management profile to be removed from the **Settings** menu. After device enrollment, you can't change this setting without wiping the device.
12. You can let multiple users sign on to enrolled iPads by using a managed Apple ID. To do so, choose **Yes** under **Shared iPad** (this option requires **Enroll without User Affinity** set to **Yes**.) Managed Apple IDs are created in the Apple School Manager portal. Learn more about [shared iPad](../../solutions/education/ref-classroom-settings-ios-shared) and [shared iPad requirements for Apple](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).
13. Choose if you want the devices using this policy to be able to **Sync with computers**. **Deny All** means that devices using this policy can't sync with any data on any computer.
14. If you chose **Allow Apple Configurator by certificate** in the previous step, choose an Apple Configurator Certificate to import.
15. You can specify a naming format for devices that is automatically applied when they enroll. To do so, select **Yes** under **Apply device name template**. Then, in the **Device Name Template** box, enter the template to use for the names using this policy. You can specify a template format that includes the device type and serial number.
16. Under **Setup Assistant**, select the Apple Setup Assistant screens you want to show and hide to users. The following table describes the available settings.

    | Setting | Description |
    | --- | --- |
    | **Department Name** | Appears when users tap **About Configuration** during activation. |
    | **Department Phone** | Appears when the user selects the **Need Help** button during activation. |
    | **Setup Assistant Options** | The following optional settings can be set up later in the iOS/iPadOS **Settings** menu. |
    | **Passcode** | Prompt for passcode during activation. Always require a passcode for unsecured devices unless access is controlled in some other manner (like kiosk mode that restricts the device to one app). |
    | **Location Services** | If enabled, Setup Assistant prompts for the service during activation. |
    | **Restore** | If enabled, Setup Assistant prompts for iCloud backup during activation. |
    | **iCloud and Apple ID** | If enabled, Setup Assistant prompts the user to sign in with an Apple ID, and the Apps & Data screen allows the device to be restored from iCloud backup. |
    | **Terms and Conditions** users can set up Touch ID or Face ID to unlock the device and sign in to apps. |  |
    | **Apple Pay** | If enabled, users can set up Apple Pay. |
    | **Zoom** | If enabled, users can choose between standard and zoomed display settings. |
    | **Siri** | If enabled, users can configure Siri. |
    | **Diagnostic Data** | If enabled, users can choose whether to send diagnostic app data to developers. |
17. Choose **OK**.
18. To save the policy, choose **Create**.