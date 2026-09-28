---
layout: Conceptual
title: Use Microsoft Tunnel VPN with Android devices that don't enroll with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/mam-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-intune-suite
ms.reviewer: ochukwunyere
ms.subservice: suite
description: Add support for Mobile Application Management (MAM) for Android to the Microsoft Tunnel Gateway. Tunnel support for MAM expands access to your organizational resources for devices that can't or haven't enrolled with Microsoft Intune
ms.date: 2026-05-26T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: 05143e7f-26af-828f-c46b-c1944d88d506
document_version_independent_id: 05143e7f-26af-828f-c46b-c1944d88d506
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/microsoft-tunnel/mam-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/microsoft-tunnel/mam-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/microsoft-tunnel/mam-android.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://authoring-docs-microsoft.poolparty.biz/devrel/80beb97b-18aa-44f8-9420-8f2a4cd448eb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c09e0ef-0fde-4b6d-bf1b-b517e4db7f80
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c62ee2af-5398-27a7-4d15-fc763902edf2
---

# Use Microsoft Tunnel VPN with Android devices that don't enroll with Microsoft Intune - Microsoft Intune | Microsoft Learn

This feature requires Microsoft Intune Plan 2 or an additional subscription. For licensing options, see [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) and [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

When you add Microsoft Tunnel for Mobile Application Management (MAM) to your tenant, you can use Microsoft Tunnel VPN Gateway with unenrolled Android devices to support MAM scenarios. With support for MAM, your unenrolled devices can use Tunnel to securely connect to your organization allowing users and apps safe access to your organizational data.

Applies to:

- Android Enterprise

To extend your existing [Microsoft Tunnel configuration](install) to support [MAM](../../app-management/protection/mam-without-enrollment), create and deploy three profiles that configure this support on your unenrolled devices:

- App configuration policy for Microsoft Defender. This policy configures Microsoft Defender for Endpoint on a device as the VPN tunnel client app.
- App configuration policy for Microsoft Edge. This policy configures Microsoft Edge to support identity-switch, which automatically connects and disconnects the VPN tunnel when switching from a Microsoft "Work or school" account to a Microsoft "personal account" in Microsoft Edge.
- App protection policy to automatically start the connection to Microsoft Tunnel when the MAM enabled app on the device accesses corporate resources.

With these policies in place, your existing Site and Server configurations for Tunnel support access from devices that aren't enrolled in Intune. In addition, you can choose to deploy your configurations for MAM Tunnel to enrolled devices instead of using MDM Tunnel configurations. However, an enrolled device must use only the MDM Tunnel configurations or the MAM Tunnel configurations, but not both. For example, enrolled devices can't have an app like Microsoft Edge that uses MAM tunnel configurations while other apps use MDM Tunnel configurations.

**Try the interactive demo**: The [Microsoft Tunnel for Mobile Application Management for Android](/ https:/regale.cloud/Microsoft/viewer/1896/microsoft-tunnel-for-mobile-application-management-for-android/index.html#/0/0) interactive demo shows how Tunnel for MAM extends the Microsoft Tunnel VPN Gateway to support Android devices not enrolled with Intune.

## Prerequisites

**Infrastructure and tenant**:

Tunnel for MAM requires the same considerations and prerequisites as using Tunnel for enrolled devices. For more information, see [Tunnel prerequisites](prerequisites).

After [configuring Microsoft Tunnel](install), you'll be ready to add the two *App configuration policies* and the *App protection policy* that enables unenrolled devices to use Tunnel. Configuration of these policies is detailed in the following sections.

**Devices**:

Users of devices that aren't enrolled with Intune must install the following apps on their Android device before they can use the Tunnel for MAM scenario. These apps can all be manually installed from the Google Play store:

1. **Microsoft Defender** – Get it from [Microsoft Defender - Apps on Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx&amp;hl=en_US&amp;gl=US&amp;pli=1). Microsoft Defender includes the tunnel client app that the device uses to connect to Microsoft Tunnel. To support Tunnel for MAM, Microsoft Defender for Endpoint must be version **1.0.4722.0101** or higher.
2. **Microsoft Edge** – Get it from [Microsoft Edge: Web Browser - Apps on Google Play](https://play.google.com/store/apps/details?id=com.microsoft.emmx&amp;hl=en_US&amp;gl=US).
3. **Company Portal** – Get it at [Intune Company Portal - Apps on Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&amp;hl=en_US&amp;gl=US). Devices must install the Company Portal app, even though users won't need to sign in to the app or enroll their device with Intune.

**Line of Business apps**:

For your Line of Business (LOB) apps, integrate them with the MAM SDK. Later, you can add your LOB apps to your app protection policy and app configuration policies for MAM Tunnel. See [Getting started with MAM for Android](../../developer/app-sdk/android-phase-3).

Note

Make sure your Android LOB applications support direct proxy or Proxy Auto-Configuration (PAC) for both MDM and MAM.

**MAM SDK Version**:

To use the Android Trusted Roots Functionality for Microsoft Tunnel for MAM requires a MAM SDK version of 9.5.0 or later, go to [Release Version 9.5.0 · msintuneappsdk/ms-intune-app-sdk-android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android/releases/tag/9.5.0) on github.com.

## Government cloud support

Microsoft Tunnel for MAM on Android is supported with the following sovereign cloud environments:

- U.S. Government Community Cloud (GCC) High
- U.S. Department of Defense (DoD)

Microsoft Tunnel for MAM on Android isn't supported on Microsoft Azure operated by 21Vianet.

Microsoft Tunnel for MAM on Android doesn't support Federal Information Processing Standard (FIPS).

For more information, see [Microsoft Intune for US Government GCC service description](../../fundamentals/government-service).

## Configure policies to support Microsoft Tunnel for MAM

To support using Tunnel for MAM, create and deploy the three profiles detailed in the following sections. These policies can be created in any order:

- App configuration policy for Microsoft Edge
- App configuration policy for Microsoft Defender
- App protection policy for Microsoft Edge

When all three are configured and deployed to the same groups, the app protection policy automatically triggers Tunnel to connect to the VPN whenever Microsoft Edge is launched.

You can also configure a [Trusted certificate profile](../../device-configuration/certificates/trusted-root-profiles) for use with Microsoft Edge and with your line-of-business apps when they must connect to on-premises resources and are protected by an SSL/TLS certificate issued by an on-premises or private certificate authority (CA). By default, Microsoft Edge supports trusted root certificates. For LOB apps, you use the MAM SDK to add support for trusted root certificates.

### App configuration policy for Microsoft Defender

Create an App configuration policy to configure Microsoft Defender for Endpoint on the device for use as the tunnel client app.

Note

Ensure only a single Defender app configuration policy targets the unenrolled device. Targeting more than 1 app configuration policy with different tunnel settings for Defender for Endpoint will create tunnel connection issues on the device.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Apps** &gt; **Configuration** &gt; **Create** &gt; **Managed Apps**.
2. On the *Basics* tab:

    1. Enter a *Name* for this policy, and a *Description (optional)*.
    2. Click on **Select public apps**, select **Microsoft Defender Endpoint** for *Android*, and then click **Select**.

    When Microsoft Defender Endpoint is listed for *Public apps*, select **Next**.

    ![Screen shot of configuring an app configuration policy with Microsoft Defender Endpoint as a public app.](media/mam-android/public-apps-defender.png)
3. On the *Settings* tab, skip the *General configuration settings* category, which isn't used for this policy. For the *Microsoft Tunnel settings* category, make the following configurations:

    - Set *Use Microsoft Tunnel VPN* to **Yes**.
    - For *Connection name*, specify the connection name of your VPN.

    Next, click **Select a site**:

    - For *Site Name*, select an available site, and then click **OK**.
    - *Per-App VPN (Android only)* is an optional setting. Select public or custom apps, to restrict the use of use the Tunnel VPN connection to these specified apps.

        Important

        To ensure seamless identity switching and accurate Tunnel notifications within Microsoft Edge, it's essential to include Edge in your per-app VPN list.

        ![Screen shot of the per-app configuration configuration with Microsoft Edge added.](media/mam-android/edge_per_app.png)

        Important

        MAM Tunnel for Android doesn't support the use of *Always-on VPN*. When *Always-on VPN* is set to *Enable*, Tunnel does not connect successfully and sends connection failure notifications to the device user.

        To block network traffic when the MAM Tunnel connection is unavailable, configure Strict Tunnel Mode through the Microsoft Edge app configuration policy instead of Always-on VPN.
    - *Proxy* is an optional setting. Configure proxy settings to meet your on-premises network requirements.

        Note

        Proxy server configurations are not supported with versions of Android prior to version 10. For more information, see [VpnService.Builder](https://developer.android.com/reference/android/net/VpnService.Builder#setHttpProxy%28android.net.ProxyInfo%29) in that Android developer documentation.

    When ready, select **Next** to continue.

    ![Screen shot of the app configuration policies settings configuration.](media/mam-android/settings-configuration-defender.png)
4. On the *Assignments* tab, select **Add Groups**, and then select the same Microsoft Entra groups that you deployed the Microsoft Edge App configuration profile to, and then select **Next**.
5. On the *Review + Create* tab, select **Create** to complete creation of the policy and deploy the policy to the assigned groups.

The new policy appears in the list of App configuration policies.

### App configuration policy for Microsoft Edge

Create an App configuration policy for Microsoft Edge. This policy configures Microsoft Edge to support identity-switch, providing the ability to automatically connect the VPN Tunnel when signing-in or switching to a Microsoft "Work or school" account, and automatically disconnect the VPN tunnel when switching to a Microsoft personal account.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Apps** &gt; **Configuration** &gt; **Create** &gt; **Managed Apps**.
2. On the *Basics* tab:

    1. Enter a *Name* for the policy, and a *Description (optional)*.
    2. Click on **Select public apps**, select **Microsoft Edge** for *Android*, and then click **Select**.

    After Microsoft Edge is listed for *Public apps*, select **Next**.

    ![Screen shot of configuring an app configuration policy with Microsoft Edge as a public app.](media/mam-android/public-apps-edge.png)
3. On the *Settings* tab, configure the *Name* and *Value* pair in the *General configuration settings* category as follows:

    | Name | Description |
    | --- | --- |
    | `com.microsoft.intune.mam.managedbrowser.StrictTunnelMode`**Value**: `True` | When set to `True`, it provides **Strict Tunnel Mode** support to Edge. When users sign in to Edge with an organization account, if the VPN isn't connected, then **Strict Tunnel Mode** blocks internet traffic.  When the VPN reconnects, internet browsing is available again. |
    | `com.microsoft.intune.mam.managedbrowser.TunnelAvailable.IntuneMAMOnly`**Value**: `True` | When set to `True`, it provides **Identity switch** support to Edge.  When users sign in with **Work account or School account**, Edge automatically connects to the VPN. When users enable in-private browsing, Edge switches to a **Personal account** and disconnects the VPN. |

    Note

    The `StrictTunnelMode` app config key applies to MAM scenarios for unenrolled devices, where it blocks Edge internet traffic when the MAM Tunnel connection is unavailable. For enrolled devices, Strict Tunnel Mode is configured as a device-level setting in the [Microsoft Tunnel VPN profile](install#create-a-vpn-profile) and applies to all network traffic on the device, not just Edge.

    The following image shows the `Identity switch` setting in an app configuration policy for Microsoft Edge:

    ![Image that shows the Identity switch configuration key and value for MAM Tunnel on unmanaged Android devices in Microsoft Intune.](media/mam-android/name-value-pair-edge.png)

    Note

    Ensure there are no trailing spaces at the end of the General configuration setting.

    You can use this same policy to configure other Microsoft Edge configurations in the *Microsoft Edge configuration settings* category. After any additional configurations for Microsoft Edge are ready, select **Next**.
4. On the *Assignments* tab, select **Add Groups**, and then select one or more Microsoft Entra groups that will receive this policy. After configuring groups, select **Next**.
5. On the *Review + Create* tab, select **Create** to complete creation of the policy and deploy the policy to the assigned groups.

The new policy appears in the list of App configuration policies.

### App protection policy for Microsoft Edge

Create an app protection policy to automatically start the Microsoft Tunnel VPN connection when the app is launched.

Note

When the app is started, the Tunnel VPN connection will attempt to start, once started, the device will have access to the on-premises network routes available via the Microsoft Tunnel Gateway. If you wish to limit the tunnel network access to specific apps, then configure the "Per-App VPN (Android only) settings.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Apps** &gt; **Protection** &gt; **Create** &gt; **Android**.
2. On the *Basics* tab, enter a *Name* for this policy, and a *Description (optional)*, and then select **Next**.
3. On the *Apps* tab, click **Select public apps**, select **Microsoft Edge**, and then click **Select**.

    When Microsoft Edge is listed for *Public apps*, select **Next**.

    ![Screen shot of configuring an app protection policy with Microsoft Edge as a public app.](media/mam-android/app-protection-edge.png)
4. On the *Data protection* tab, scroll to the bottom and set *Start Microsoft Tunnel connection on app-launch* to **Yes**, and then select **Next**.

    ![Screen shot of configuring an app protection policy setting for using Tunnel on app-launch.](media/mam-android/app-protection-data-protection-tab.png)
5. Continue past the *Access requirements* and *Conditional launch* tabs.
6. On the *Assignments* tab, select **Add Groups**, and then select the same Microsoft Entra groups that you deployed the two app configuration profiles to, and then select **Next**.
7. On the *Review + Create* tab, select **Create** to complete creation of the policy and deploy the policy to the assigned groups.

The new policy appears in the list of app configuration policies.

## Configure Line of Business applications

If you've integrated your LOB apps with the MAM SDK, you can use them with Microsoft Tunnel by adding them as *custom apps* to the three MAM Tunnel policies you've previously created.

For more information about adding custom apps to policies, see the following articles for the two policy types:

- [App configuration policies for Intune App SDK managed apps](../../app-management/configuration/configure-managed-apps)
- [How to create and assign app protection policies](../../app-management/protection/create-policy)

To support LOB apps on your unenrolled devices, the apps must deploy as *available apps* from within Microsoft Intune admin center. You can't use Intune to deploy apps as required apps to unenrolled devices.

### Use a trusted certificate profile

LOB apps that use the MAM tunnel on Android are required to integrate with the Intune App SDK and must use the new Tunnel for MAM trust manager to utilize trusted root certificate support for their LOB apps. To support trusted root certificates, you must use the minimum SDK version (or later) as detailed in the Prerequisites section of this article.

**Trusted Root Certificates Management**:

If your application requires SSL/TLS certificates issued by an on-premises or private certificate authority to provide secure access to internal websites and applications, the Intune App SDK has added support for certificate trust management using the API classes [MAMTrustedRootCertsManager](https://github.com/microsoftconnect/ms-intune-app-sdk-android/blob/master/docs/com/microsoft/intune/mam/client/app/MAMTrustedRootCertsManager.html) and [MAMCertTrustWebViewClient](https://github.com/microsoftconnect/ms-intune-app-sdk-android/blob/master/docs/com/microsoft/intune/mam/client/app/MAMCertTrustWebViewClient.html).

**Requirements**:

- **Certificate formats** supported by Tunnel for MAM Android:

    - DER encoded binary X.509
    - PEM
- **MAMCertTrustWebViewClient** supports:

    - Android 11 or higher
- **MAMTrustedRootCertsManager** supports:

    - SSLContext
    - SSLSocketFactory
    - TrustManager
    - WebView

During configuration of the app configuration profile for an app that will use Tunnel for MAM, select the certificate profile that will be used:

1. On the *Settings* tab of your app configuration profile, expand *Microsoft Tunnel for Mobile Application Management settings*. [![View of the Tunnel settings in an app configuration policy.](media/mam-android/settings-certificates.png)](media/mam-android/settings-certificates.png#lightbox)
2. Configure the following options:

    1. Set *Use Microsoft Tunnel for MAM* to **Yes**.
    2. For *Connection name*, specify a user facing name for this connection, like *mam-tunnel-vpn*.
    3. Next, select **Select a Site**, and choose one of your Microsoft Tunnel Gateway sites. If you haven't configured a Tunnel Gateway site, see [Configure Microsoft Tunnel](install).
    4. If your app requires a trusted certificate, select **Root Certificate** to open the *Select Root Certificates* pane, and then select a trusted certificate profile to use.

    [![View of the root certificate selection pane.](media/mam-android/select-root-certificate.png)](media/mam-android/select-root-certificate.png#lightbox)

    For information about configuring root certificate profiles, see [Trusted root certificate profiles for Microsoft Intune](../../device-configuration/certificates/trusted-root-profiles).
3. After configuring the Tunnel MAM settings, Select **Next** to open the *Assignments* tab.

## Known Issues

The following are known issues or limitations for MAM Tunnel for Android.

### Tunnel for Mobile Application Management does not support Microsoft Defender in Personal Profile mode

For information about Microsoft Defender in Personal Profile Mode, see [Microsoft Defender in Personal Profile on Android Enterprise in BYOD mode](/en-us/microsoft-365/security/defender-endpoint/android-intune#set-up-microsoft-defender-in-personal-profile-on-android-enterprise-in-byod-mode).

**Workaround**: None.

### MAM Tunnel not supported when using the MDM Tunnel

You can choose to use MAM Tunnel with enrolled devices instead of using MDM Tunnel configurations. However, an enrolled device must use only the MDM Tunnel configurations or the MAM Tunnel configurations, but not both. For example, enrolled devices can't have an app like Microsoft Edge that uses MAM tunnel configurations while other apps use MDM Tunnel configurations.

**Workaround**: None.

### Line of business application using WebView and Intune SDK for Trusted root support, internal endpoints are unrenderable

**Workaround**: Manually deploy and install the trusted root certificate on unenrolled Android devices that use LOB Apps with WebView on Tunnel.

### Android fails to build the certificate chain when you use private certification authority

When using WebView with [MAMCertTrustWebViewClient](https://github.com/microsoftconnect/ms-intune-app-sdk-android/blob/master/docs/com/microsoft/intune/mam/client/app/MAMCertTrustWebViewClient.html) in MAM to validate certificates, MAM delegates to Android to build a certificate chain from certificates provided by the admins and the server. If a server that uses private certificates provides the full chain to the connecting WebView but the admin deploys only the root certificate, Android can fail to build the cert chain and fail when checking the server trust. This behavior occurs because Android requires intermediate certificates to build the chain to an acceptable level.

**Workaround**: To ensure proper certificate validation, admins must deploy the root certificate and all intermediate certificates in Intune. If the root certificate along with all intermediate certificates aren't deployed, Android can fail to build the certificate chain and fail to trust the server.

### Defender for Endpoint certificate error when using a TLS/SSL certificate from a private certificate authority

When Microsoft Tunnel Gateway server uses a TLS/SSL certificate issued by a private (on-premises) CA, Microsoft Defender for Endpoint generates a certificate error when attempting to connect.

**Work around**: Manually install the corresponding trusted root certificate of the private certificate authority on the Android device. A future update of the Defender for Endpoint app will provide support and remove the need to manually install the trusted root certificate.

### Microsoft Edge can't reach internal resources for a short time after being launched

Immediately after Microsoft Edge opens, the browser attempts to connect to internal resources before successfully connecting to Tunnel. This behavior results in the browser reporting that the resource or destination URL is unavailable.

**Workaround**: Refresh the browser connection on the device. The resource becomes available after the connection to Tunnel is established.

### The three apps required to support Tunnel for unenrolled devices aren't visible in the Company Portal app on a device

After Microsoft Edge, Microsoft Defender for Endpoint, and the Company Portal, are assigned to a device as *available with or without enrollment*, the targeted user can't find the apps in the Company Portal or at *portal.manage.microsoft.com*.

**Workaround**: Install all three apps manually from the Google Play store. You can find links to all three apps on Google Play in this articles Prerequisites section.

### Error: "MSTunnel VPN is failed to start, contact your IT administrator for help"

This error message can occur even though the tunnel is connected.

**Workaround**: This message can be ignored.

### Error: Invalid Licensing, please contact administrator

This error occurs when the version of Microsoft Defender for Endpoint doesn't support Tunnel.

**Workaround**: Install the supported version of Defender for Endpoint from [Microsoft Defender - Apps on Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx&amp;hl=en_US&amp;gl=US&amp;pli=1).

### Using multiple policies for Defender to configure different tunnel sites for different apps isn't supported

Using two or more app configuration policies for Microsoft Defender that specify different Tunnel Sites isn't supported and can result in a race condition that prevents successful use of Tunnel.

**Workaround**: Target each device with a single app configuration policy for Microsoft Defender, ensuring each unenrolled device is configured to use only one Site.

### Auto-Disconnect with Line of Business Apps

We do not support auto disconnect in Line-of-Business (LOB) scenarios.

If Edge is the only application listed in the per-app VPN configuration, the auto disconnect feature will function correctly. If there are other applications included in the per-app VPN configuration, the auto disconnect feature will not work. In this case, users must manually disconnect to ensure all connections are terminated.

**Workaround**: Users must manually disconnect connections in LOB scenarios.