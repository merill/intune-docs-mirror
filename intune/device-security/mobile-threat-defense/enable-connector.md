---
layout: Conceptual
title: Enable Mobile Threat Defense connector in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-connector
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-mtd-apps
ms.reviewer: ilwu
ms.subservice: protect
description: Enable the connector between your Mobile Threat Defense (MTD) partner and Microsoft Intune.
ms.date: 2026-09-04T00:00:00.0000000Z
ai-usage: ai-assisted
ms.topic: how-to
locale: en-us
document_id: 6cb6f0b1-9072-0922-9d7f-110795150646
document_version_independent_id: 6cb6f0b1-9072-0922-9d7f-110795150646
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/enable-connector.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/enable-connector
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/enable-connector.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 699b06f3-2d32-791c-9065-49065f053edd
---

# Enable Mobile Threat Defense connector in Microsoft Intune - Microsoft Intune | Microsoft Learn

Intune can integrate data from a Mobile Threat Defense (MTD) partner for use by device compliance policies and device Conditional Access rules. Use this information to help protect corporate resources like Exchange and SharePoint by blocking access from compromised mobile devices.

After you [set up your MTD Partner](overview#mobile-threat-defense-partners) and configure the Intune connector in the MTD partner console, you can enable the MTD connection for that MTD partner application from within the Intune admin center.

Applies to:

- All [Intune Mobile Threat Defense partners](overview#mobile-threat-defense-partners).

## Required role-based access control permissions

To successfully enable the Mobile Threat Defense connector, use an account that's assigned [Role-based access control](../../fundamentals/role-based-access-control/overview) (RBAC) permissions equivalent to the *Endpoint Security Manager* built-in admin role for Intune. If you use a custom role, ensure it includes the *Read* and *Modify* rights for the Intune *Mobile Threat Defense* permission.

## To enable the Mobile Threat Defense connector

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Connectors and tokens** &gt; **Mobile Threat Defense**.
3. On **Mobile Threat Defense**, select **Add**.
4. For **Mobile Threat Defense connector to setup**, select your MTD partner solution from the drop-down list.

    Note

    As of the August 2023 Intune service release (2308), Intune no longer creates classic Conditional Access (CA) policies for the **Microsoft Defender for Endpoint** connector. As of April 2024 Intune service release (2404), Intune no longer needs classic CA policies for third-party **Mobile Threat Defense** connectors either. If your tenant has a classic CA policy that you previously created for integration with Defender for Endpoint or third-party Mobile Threat Defense connectors, you can delete it.
5. Enable the toggle options according to your organization's requirements. The toggle options that are visible can vary depending on the MTD partner. For example, the following image shows the available options for Symantec Endpoint Protection:

    ![Screenshot of the Add Connector pane for Symantec Endpoint Protection, showing toggle options for compliance policy evaluation, app protection policy evaluation, Mobile Threat Defense role, and shared settings.](media/enable-connector/enable-mtd-connector-1.png)

## Mobile Threat Defense toggle options

Note

To see the full list of toggle options, ensure your tenant's MDM Authority is [set to Intune](../../fundamentals/setup-mdm-authority#set-mdm-authority-to-intune).

The available options for connectors are divided into four categories. When a partner doesn't support a category, that category isn't available:

- Compliance policy evaluation
- App protection policy evaluation
- Mobile Threat Defense role
- Shared settings

Turn on the toggles for the options your organization requires.

### Compliance policy evaluation

- **Connect Android devices version *&lt;supported versions&gt;* and later to *&lt;MTD partner name&gt;***: When you turn on this option, compliance policies that use the Device Threat Level rule for Android devices (on supported OS versions) include data from this connector when they evaluate devices.
- **Connect iOS/iPadOS devices version *&lt;supported versions&gt;* and later to *&lt;MTD partner name&gt;***: When you turn on this option, compliance policies that use the Device Threat Level rule for iOS/iPadOS devices (on supported OS versions) include data from this connector when they evaluate devices.
- **Enable App Sync for iOS devices**: Allows this Mobile Threat Defense partner to request metadata of iOS applications from Intune to use for threat analysis purposes. This iOS device must be MDM-enrolled device and provides updated app data during device check-in. You can find standard Intune policy check-in frequencies in the [Refresh cycle times](../../device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).

    Note

    App Sync data is sent to Mobile Threat Defense partners at an interval based on device check-in, and shouldn't be confused with the refresh interval for the [Discovered Apps report](../../app-management/discovered-apps#details-of-discovered-apps).
- **Send full application inventory data on personally-owned iOS/iPadOS devices​**: This setting controls the application inventory data that Intune shares with this Mobile Threat Defense partner. Intune shares data when the partner syncs app data and requests the app inventory list.

    Choose from the following options:

    - **On** - Allows this Mobile Threat Defense partner to request a list of iOS/iPadOS applications from Intune for personally-owned iOS/iPadOS devices. This list includes unmanaged apps (apps not deployed through Intune) and the apps that were deployed through Intune.
    - **Off** - The partner doesn't get data about unmanaged apps. Intune does share data for the apps that are deployed through Intune.

    This setting has no effect for corporate devices. For corporate devices, Intune sends data about both managed and unmanaged apps when requested by this MTD vendor.
- **Enable Certificate Sync for iOS/iPadOS devices**: This option is only available when supported by the Mobile Threat Defense partner. When enabled it allows the Mobile Threat Defense partner to request a list of installed certificates on iOS/iPadOS devices from Intune to use for threat analysis purposes. This iOS/iPadOS device must be MDM-enrolled and provides updated certificate data during device check-in.

    Note

    Certificate Sync data is sent to Mobile Threat Defense partners at an interval based on device check-in.
- **Send full certificate inventory data on personally-owned iOS/iPadOS devices**: This setting controls the certificate inventory data that Intune shares with this Mobile Threat Defense partner for personally-owned devices. Intune shares data when the partner syncs certificate data and requests the certificate inventory list.

    Choose from the following options:

    - **On** - Allows this Mobile Threat Defense partner to request a list of installed certificates from Intune for personally-owned iOS/iPadOS devices. This list includes unmanaged certificates (certificates not deployed through Intune) and certificates that were deployed through Intune.
    - **Off** - The partner doesn't get data about unmanaged certificates for personally-owned devices. No certificate data is sent for personally-owned devices.

    This setting has no effect for corporate devices. For corporate devices, Intune sends data about both managed and unmanaged certificates when requested by this MTD vendor.
- **Block unsupported OS versions**: Block if the device is running an operating system less than the minimum supported version. Details of the minimum supported version are shared within the docs for the Mobile Threat Defense vendor.

### App protection policy evaluation

- **Connect Android devices of version *&lt;supported versions&gt;* to *&lt;MTD partner name&gt;* for app protection policy evaluation**: When you turn on this option, app protection policies that use the "Max allowed threat level" rule evaluate devices by including data from this connector.
- **Connect iOS devices version *&lt;supported versions&gt;* to *&lt;MTD partner name&gt;* for app protection policy evaluation**: When you turn on this option, app protection policies that use the "Max allowed threat level" rule evaluate devices by including data from this connector.

For more information about using Mobile Threat Defense connectors for Intune App Protection Policy evaluation, see [Set up Mobile Threat Defense for unenrolled devices](enable-unenrolled-devices).

### Mobile Threat Defense role

- **Grant MTD role permissions to *&lt;MTD partner name&gt;* on enrolled Android COBO and COPE devices**: When you turn on this option, the selected Mobile Threat Defense partner receives enhanced permissions to help protect enrolled Android Enterprise corporate-owned fully managed (COBO) and Android Enterprise corporate-owned work profile (COPE) devices from mobile threats.

    On devices where you configure these permissions, the MTD app gets the following exemptions:

    - **Suspension** — The app can't be suspended.
    - **Hibernation** — The app can't enter hibernation.
    - **Power restrictions** — The app is exempt from power-related restrictions such as app standby. The app can start foreground services from the background, and the user can't stop foreground services run by the app.
    - **User controls** — User control over the app is disabled. Users can't clear app data or force-stop the app.

    Important

    Only one MTD partner can hold MTD role permissions per tenant. To use this toggle, first configure the MTD connector for this partner, and target the MTD app to devices through a user or device group.

    Note

    This toggle is available for every [MTD partner](overview#mobile-threat-defense-partners) that supports Android. The same toggle is available on the Defender for Endpoint connector page at **Endpoint security** &gt; **Defender for Endpoint**.

    Applies to:

    - Android Enterprise corporate-owned fully managed
    - Android Enterprise corporate-owned work profile

    The Mobile Threat Defense role requires devices enrolled through the [Android Management API](https://developers.google.com/android/management). Personally-owned work profiles aren't currently supported.
- **Automatically launch Defender for Endpoint during setup on Android COBO and COPE devices**: This toggle is available only for the Defender for Endpoint connector. When you turn on this option, the Defender for Endpoint app automatically launches during the device setup process on Android Enterprise COBO and COPE devices, allowing Defender for Endpoint to complete its initial configuration without requiring the user to manually open it.

    Note

    This toggle requires that the **Grant MTD role permissions** toggle is also turned on for Defender for Endpoint.

### Shared settings

- **Number of days until partner is unresponsive**: Number of days of inactivity before Intune considers the partner to be unresponsive because the connection is lost. Intune ignores compliance state for unresponsive MTD partners.

Important

When possible, add and assign the MTD apps *before* creating the device compliance and the Conditional Access policy rules. This approach helps ensure that the MTD app is ready and available for end users to install before they can get access to email or other company resources.

Tip

You can see the **Connection status** and the **Last synchronized** time between Intune and the MTD partner from the Mobile Threat Defense pane.