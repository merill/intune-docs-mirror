---
layout: Conceptual
title: Step 4. Create App Configuration Policies for Microsoft Edge for Business - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/edge-data-security/app-configuration-step-4
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- FocusArea_Apps_AppManagement
ms.reviewer: samarti
ms.subservice: apps
description: Step 4. Create app configuration policies for Microsoft Edge for Business across Windows, Android, and iOS platforms.
ms.date: 2026-01-23T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 
zone_pivot_groups: app-protection-platforms
locale: en-us
document_id: 1dd232d9-a6ae-1f59-3d2a-3786eac693bc
document_version_independent_id: 1dd232d9-a6ae-1f59-3d2a-3786eac693bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/edge-data-security/app-configuration-step-4.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/edge-data-security/app-configuration-step-4
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/edge-data-security/app-configuration-step-4.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d57e6130-6726-4cca-16b9-73c8b97b9c14
---

# Step 4. Create App Configuration Policies for Microsoft Edge for Business - Microsoft Intune | Microsoft Learn

App configuration policies (ACP) customize Microsoft Edge for Business behavior and features on each platform. In the Secure Enterprise Browser plan, ACPs work alongside App Protection Policies (Step 2) and Conditional Access (Step 1) to deliver a layered, Zero Trust browser experience on managed and BYOD devices.

This step defines three progressive ACP configurations per platform, Level 1 (Basic), Level 2 (Enhanced), and Level 3 (High), so you can standardize user experience, lock down risky surfaces, and align restrictions to data sensitivity and user risk. These policies complement data-protection controls (APP) rather than replace them.

Note

App configuration policies customize browser features and behavior. They complement app protection policies that focus on data protection.

## Policy Selection Based on Device Enrollment

App Configuration Policies (this step) are designed for non-enrolled devices using the Managed Apps configuration channel, while Settings Catalog policies (Step 5) are designed for enrolled devices with device-level controls.

Important

Choose the appropriate policy type based on device enrollment status to avoid policy conflicts.

## Security Level Selection

The three security levels (Level 1, 2, 3) are not cumulative - they represent progressively stricter configurations designed for different user roles and data sensitivity requirements.

### Implementation Guidance

- Evaluate your scenarios and user roles to determine which level is appropriate for each user group
- Deploy only one level per user/device, not all three levels simultaneously
- Align security level assignment with business role and data access requirements

### Example Assignments

- **Level 1 (Basic)**: General users, standard productivity workflows (~80% of users)
- **Level 2 (Enhanced)**: Finance, HR, IT staff handling sensitive data (~15% of users)
- **Level 3 (High)**: Executives, SecOps, Legal, users with access to highly confidential data (~5% of users)

::: zone pivot="windows"

## App configuration policies for Windows

Windows app configuration policies provide browser customization through managed app settings.

> 
> **Microsoft Documentation:**
> 
> - [Microsoft Edge Browser Policies](/en-us/deployedge/microsoft-edge-policies)
> - [Windows App Configuration Policies](../../app-management/configuration/overview)
> - [Managed App Configuration for Windows](../../app-management/configuration/configure-managed-apps)
> 

**Prerequisites:**

- Windows 11
- Microsoft Edge installed
- Intune enrollment or MAM managed
- User Entra ID account

### Level 1 - Basic browser configuration for Windows

Level 1 configuration provides foundational browser security controls while maintaining user productivity.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics**tab, enter:
    - **Name:** Edge Windows ACP Level 1 Basic
    - **Description:** Enhanced browser customization for Microsoft Edge Windows with comprehensive basic controls addressing ACP gap analysis
4. In **Target policy to**, select **Selected apps**.
    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge Windows**, then select **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| HomepageLocation | `https://portal.company.com` | [Configure the home page URL](/en-us/deployedge/microsoft-edge-browser-policies/homepagelocation) |
| ShowHomeButton | Enabled | [Show Home button on toolbar](/en-us/deployedge/microsoft-edge-browser-policies/showhomebutton) |
| NewTabPageLocation | `https://portal.company.com` | [Configure the new tab page URL](/en-us/deployedge/microsoft-edge-browser-policies/newtabpagelocation) |
| RestoreOnStartup | Open the new tab page (5) | [Action to take on startup](/en-us/deployedge/microsoft-edge-browser-policies/restoreonstartup) |
| HTTPSOnlyMode | Enabled | [Configure Automatic HTTPS](/en-us/deployedge/microsoft-edge-browser-policies/httpsonlymode) |
| DefaultPopupsSetting | Do not allow popups (2) | [Default pop-up window setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultpopupssetting) |
| PasswordManagerEnabled | Disabled | [Enable saving passwords to the password manager](/en-us/deployedge/microsoft-edge-browser-policies/passwordmanagerenabled) |
| AutofillAddressEnabled | Disabled | [Enable AutoFill for addresses](/en-us/deployedge/microsoft-edge-browser-policies/autofilladdressenabled) |
| AutofillCreditCardEnabled | Disabled | [Enable Autofill for payment instructions](/en-us/deployedge/microsoft-edge-browser-policies/autofillcreditcardenabled) |
| TrackingPrevention | Balanced (2) | [Block tracking of users' web-browsing activity](/en-us/deployedge/microsoft-edge-browser-policies/trackingprevention) |
| DefaultSearchProviderEnabled | Enabled | [Enable the default search provider](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchproviderenabled) |
| DefaultSearchProviderName | Microsoft Bing | [Default search provider name](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://www.bing.com/search?q={searchTerms}` | [Default search provider search URL](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidersearchurl) |
| SearchSuggestEnabled | Disabled | [Enable search suggestions](/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
| NetworkPredictionOptions | Don't predict (2) | [Enable network prediction](/en-us/deployedge/microsoft-edge-browser-policies/networkpredictionoptions) |
| ImportAutofillFormData | Disabled | [Allow importing of autofill form data](/en-us/deployedge/microsoft-edge-browser-policies/importautofillformdata) |
| ImportSavedPasswords | Disabled | [Allow importing of saved passwords](/en-us/deployedge/microsoft-edge-browser-policies/importsavedpasswords) |
| ImportBrowsingHistory | Disabled | [Allow importing of browsing history](/en-us/deployedge/microsoft-edge-browser-policies/importhistory) |
| ImportCookies | Disabled | [Allow importing cookies](/en-us/deployedge/microsoft-edge-browser-policies/importcookies) |
| ImportExtensions | Disabled | [Allow importing of extension](/en-us/deployedge/microsoft-edge-browser-policies/importextensions) |
| ExtensionInstallBlocklist | `["external_component", "external_pref", "external_registry"]` | [Control which extensions cannot be installed](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallblocklist) |
| ExtensionAllowedTypes | `["extension", "theme"]` | [Configure allowed extension types](/en-us/deployedge/microsoft-edge-browser-policies/extensionallowedtypes) |
| ExtensionInstallSources | `[https://corp.contoso.com/*]` | [Configure extension and user script install sources](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallsources) |
| DefaultDownloadDirectory | `${user_home}/Downloads/Edge` | [Set download directory](/en-us/deployedge/microsoft-edge-browser-policies/downloaddirectory) |
| PromptForDownloadLocation | Enabled | [Ask where to save downloaded files](/en-us/deployedge/microsoft-edge-browser-policies/promptfordownloadlocation) |
| DownloadRestrictions | Block malicious downloads and dangerous file types | [Allow download restrictions](/en-us/deployedge/microsoft-edge-browser-policies/downloadrestrictions) |
| HubsSidebarEnabled | Disabled | [Show Hubs Sidebar](/en-us/deployedge/microsoft-edge-browser-policies/hubssidebarenabled) |
| ShowMicrosoftRewards | Disabled | [Show Microsoft Rewards experiences](/en-us/deployedge/microsoft-edge-browser-policies/showmicrosoftrewards) |
| EdgeShoppingAssistantEnabled | Disabled | [Shopping in Microsoft Edge Enabled](/en-us/deployedge/microsoft-edge-browser-policies/edgeshoppingassistantenabled) |
| EdgeWorkspacesEnabled | Enabled | [Edge Workspaces](/en-us/deployedge/microsoft-edge-browser-policies/edgeworkspacesenabled) |
| FavoritesBarEnabled | Enabled | [Show favorites bar](/en-us/deployedge/microsoft-edge-browser-policies/favoritesbarenabled) |
| AllowDeletingBrowserHistory | Enabled | [Enable deleting browser and download history](/en-us/deployedge/microsoft-edge-browser-policies/allowdeletingbrowserhistory) |

1. Select **Next**.
2. For **Assignments**, assign to **SEB-Level1-Users** group.
3. Select **Next** to review the settings. Then choose **Create**.

### Level 2 - Enhanced browser configuration for Windows

Level 2 configuration adds enhanced security controls and restrictions for sensitive environments.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics**tab, enter:
    - **Name:** Edge Windows ACP Level 2 Enhanced
    - **Description:** Advanced browser customization with enhanced security controls and comprehensive feature management
4. In **Target policy to**, select **Selected apps**.
    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge Windows**, then select **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| HomepageLocation | `https://portal.company.com` | [Configure the home page URL](/en-us/deployedge/microsoft-edge-browser-policies/homepagelocation) |
| ShowHomeButton | Enabled | [Show Home button on toolbar](/en-us/deployedge/microsoft-edge-browser-policies/showhomebutton) |
| NewTabPageLocation | `https://portal.company.com` | [Configure the new tab page URL](/en-us/deployedge/microsoft-edge-browser-policies/newtabpagelocation) |
| RestoreOnStartup | Open the new tab page (5) | [Action to take on startup](/en-us/deployedge/microsoft-edge-browser-policies/restoreonstartup) |
| HTTPSOnlyMode | Enabled | [Configure Automatic HTTPS](/en-us/deployedge/microsoft-edge-browser-policies/httpsonlymode) |
| DefaultPopupsSetting | Do not allow popups (2) | [Default pop-up window setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultpopupssetting) |
| PasswordManagerEnabled | Disabled | [Enable saving passwords to the password manager](/en-us/deployedge/microsoft-edge-browser-policies/passwordmanagerenabled) |
| AutofillAddressEnabled | Disabled | [Enable AutoFill for addresses](/en-us/deployedge/microsoft-edge-browser-policies/autofilladdressenabled) |
| AutofillCreditCardEnabled | Disabled | [Enable Autofill for payment instructions](/en-us/deployedge/microsoft-edge-browser-policies/autofillcreditcardenabled) |
| TrackingPrevention | Balanced (2) | [Block tracking of users' web-browsing activity](/en-us/deployedge/microsoft-edge-browser-policies/trackingprevention) |
| DefaultSearchProviderEnabled | Enabled | [Enable the default search provider](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchproviderenabled) |
| DefaultSearchProviderName | Microsoft Bing | [Default search provider name](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://www.bing.com/search?q={searchTerms}` | [Default search provider search URL](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidersearchurl) |
| SearchSuggestEnabled | Disabled | [Enable search suggestions](/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
| NetworkPredictionOptions | Don't predict (2) | [Enable network prediction](/en-us/deployedge/microsoft-edge-browser-policies/networkpredictionoptions) |
| ImportAutofillFormData | Disabled | [Allow importing of autofill form data](/en-us/deployedge/microsoft-edge-browser-policies/importautofillformdata) |
| ImportSavedPasswords | Disabled | [Allow importing of saved passwords](/en-us/deployedge/microsoft-edge-browser-policies/importsavedpasswords) |
| ImportBrowsingHistory | Disabled | [Allow importing of browsing history](/en-us/deployedge/microsoft-edge-browser-policies/importhistory) |
| ImportCookies | Disabled | [Allow importing cookies](/en-us/deployedge/microsoft-edge-browser-policies/importcookies) |
| ImportExtensions | Disabled | [Allow importing of extension](/en-us/deployedge/microsoft-edge-browser-policies/importextensions) |
| ExtensionInstallBlocklist | `["external_component", "external_pref", "external_registry"]` | [Control which extensions cannot be installed](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallblocklist) |
| ExtensionAllowedTypes | `["extension", "theme"]` | [Configure allowed extension types](/en-us/deployedge/microsoft-edge-browser-policies/extensionallowedtypes) |
| ExtensionInstallSources | `[https://corp.contoso.com/*]` | [Configure extension and user script install sources](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallsources) |
| DefaultDownloadDirectory | `${user_home}/Downloads/Edge` | [Set download directory](/en-us/deployedge/microsoft-edge-browser-policies/downloaddirectory) |
| PromptForDownloadLocation | Enabled | [Ask where to save downloaded files](/en-us/deployedge/microsoft-edge-browser-policies/promptfordownloadlocation) |
| DownloadRestrictions | Block malicious downloads and dangerous file types | [Allow download restrictions](/en-us/deployedge/microsoft-edge-browser-policies/downloadrestrictions) |
| HubsSidebarEnabled | Disabled | [Show Hubs Sidebar](/en-us/deployedge/microsoft-edge-browser-policies/hubssidebarenabled) |
| ShowMicrosoftRewards | Disabled | [Show Microsoft Rewards experiences](/en-us/deployedge/microsoft-edge-browser-policies/showmicrosoftrewards) |
| EdgeShoppingAssistantEnabled | Disabled | [Shopping in Microsoft Edge Enabled](/en-us/deployedge/microsoft-edge-browser-policies/edgeshoppingassistantenabled) |
| EdgeWorkspacesEnabled | Enabled | [Edge Workspaces](/en-us/deployedge/microsoft-edge-browser-policies/edgeworkspacesenabled) |
| FavoritesBarEnabled | Enabled | [Show favorites bar](/en-us/deployedge/microsoft-edge-browser-policies/favoritesbarenabled) |
| AllowDeletingBrowserHistory | Enabled | [Enable deleting browser and download history](/en-us/deployedge/microsoft-edge-browser-policies/allowdeletingbrowserhistory) |
| SmartScreenForTrustedDownloadsEnabled | Enabled | [Force Microsoft Defender SmartScreen checks on downloads from trusted sources](/en-us/deployedge/microsoft-edge-browser-policies/smartscreenfortrusteddownloadsenabled) |
| InsecureContentAllowedForUrls | `[]` | [Allow insecure content on specified sites](/en-us/deployedge/microsoft-edge-browser-policies/insecurecontentallowedforurls) |
| InsecureContentBlockedForUrls | `["*"]` | [Block insecure content on specified sites](/en-us/deployedge/microsoft-edge-browser-policies/insecurecontentblockedforurls) |
| ExtensionInstallAllowlist | `[]` | [Allow specific extensions to be installed](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallallowlist) |
| ExtensionInstallForcelist | `[]` | [Control which extensions are installed silently](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallforcelist) |
| ExtensionSettings | `{"*":{"installation_mode":"blocked"}}` | [Configure extension management settings](/en-us/deployedge/microsoft-edge-browser-policies/extensionsettings) |
| NativeMessagingAllowlist | `[]` | [Control which native messaging hosts users can use](/en-us/deployedge/microsoft-edge-browser-policies/nativemessagingallowlist) |
| NativeMessagingHostBlocklist | `["*"]` | [Configure native messaging block list](/en-us/deployedge/microsoft-edge-browser-policies/nativemessagingblocklist) |
| AutoSelectCertificateForUrls | `["*.company.com"]` | [Automatically select client certificates for these sites](/en-us/deployedge/microsoft-edge-browser-policies/autoselectcertificateforurls) |
| WebRtcUdpPortRange | 10000:11000 | [Restrict the range of local UDP ports used by WebRTC](/en-us/deployedge/microsoft-edge-browser-policies/webrtcudpportrange) |
| DefaultImagesSetting | Allow images (1) | [Default images setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultimagessetting) |
| DefaultJavaScriptSetting | Allow JavaScript (1) | [Default JavaScript setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultjavascriptsetting) |
| ClearBrowsingDataOnExit | Enabled | [Clear browsing data when Microsoft Edge closes](/en-us/deployedge/microsoft-edge-browser-policies/clearbrowsingdataonexit) |
| SyncDisabled | Enabled | [Disable synchronization of data using Microsoft sync services](/en-us/deployedge/microsoft-edge-browser-policies/syncdisabled) |
| PrintingEnabled | Enabled | [Enable printing](/en-us/deployedge/microsoft-edge-browser-policies/printingenabled) |
| InPrivateModeAvailability | InPrivate mode available (0) | [InPrivate mode availability](/en-us/deployedge/microsoft-edge-browser-policies/inprivatemodeavailability) |
| ForceSync | Disabled | [Force synchronization of browser data and do not show the sync consent prompt](/en-us/deployedge/microsoft-edge-browser-policies/forcesync) |
| SleepingTabsEnabled | Enabled | [Configure sleeping tabs](/en-us/deployedge/microsoft-edge-browser-policies/sleepingtabsenabled) |
| SearchSuggestEnabled | Disabled | [Enable search suggestions](/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
| LocalProvidersEnabled | Disabled | [Allow suggestions from local providers](/en-us/deployedge/microsoft-edge-browser-policies/localprovidersenabled) |
| VideoCaptureAllowed | Disabled | [Allow or block video capture](/en-us/deployedge/microsoft-edge-browser-policies/videocaptureallowed) |
| DefaultNotificationsSetting | Block (2) | [Default notification setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultnotificationssetting) |
| DefaultGeolocationSetting | Don't allow sites to track users' physical location (2) | [Default geolocation setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultgeolocationsetting) |
| WebUsbAllowDevicesForUrls | `[]` | [Allow WebUSB on specific sites](/en-us/deployedge/microsoft-edge-browser-policies/webusballowdevicesforurls) |
| WebUsbBlockedForUrls | `[{"urls": ["*"], "devices": [{"vendor_id": "*", "product_id": "*"}]}]` | [Block WebUSB on specific sites](/en-us/deployedge/microsoft-edge-browser-policies/webusbblockedforurls) |
| WebRtcLocalhostIpHandling | Disable non-proxied UDP (default\_public\_interface\_only) | [Restrict exposure of local IP address by WebRTC](/en-us/deployedge/microsoft-edge-browser-policies/webrtclocalhostiphandling) |

1. Select **Next**.
2. For **Assignments**, assign to **SEB-Level2-Users** group.
3. Select **Next** to review the settings. Then choose **Create**.

### Level 3 - High security configuration for Windows

Level 3 configuration enforces maximum security with zero-trust controls and comprehensive data-loss prevention.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics** tab, enter:

    - **Name:** Edge Windows ACP Level 3 High
    - **Description:** High browser customization with complete enterprise controls, zero-trust configuration, and comprehensive security isolation
4. In **Target policy to**, select **Selected apps**.

    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge Windows**, then select **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

    | Name | Value | Documentation |
    | --- | --- | --- |
    | HomepageLocation | `https://portal.company.com` | [Configure the home page URL](/en-us/deployedge/microsoft-edge-browser-policies/homepagelocation) |
    | ShowHomeButton | Enabled | [Show Home button on toolbar](/en-us/deployedge/microsoft-edge-browser-policies/showhomebutton) |
    | NewTabPageLocation | `https://portal.company.com` | [Configure the new tab page URL](/en-us/deployedge/microsoft-edge-browser-policies/newtabpagelocation) |
    | RestoreOnStartup | Open the new tab page (5) | [Action to take on startup](/en-us/deployedge/microsoft-edge-browser-policies/restoreonstartup) |
    | HTTPSOnlyMode | Enabled | [Configure Automatic HTTPS](/en-us/deployedge/microsoft-edge-browser-policies/httpsonlymode) |
    | DefaultPopupsSetting | Do not allow popups (2) | [Default pop-up window setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultpopupssetting) |
    | PasswordManagerEnabled | Disabled | [Enable saving passwords to the password manager](/en-us/deployedge/microsoft-edge-browser-policies/passwordmanagerenabled) |
    | AutofillAddressEnabled | Disabled | [Enable AutoFill for addresses](/en-us/deployedge/microsoft-edge-browser-policies/autofilladdressenabled) |
    | AutofillCreditCardEnabled | Disabled | [Enable Autofill for payment instructions](/en-us/deployedge/microsoft-edge-browser-policies/autofillcreditcardenabled) |
    | TrackingPrevention | Balanced (2) | [Block tracking of users' web-browsing activity](/en-us/deployedge/microsoft-edge-browser-policies/trackingprevention) |
    | DefaultSearchProviderEnabled | Enabled | [Enable the default search provider](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchproviderenabled) |
    | DefaultSearchProviderName | Microsoft Bing | [Default search provider name](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidername) |
    | DefaultSearchProviderSearchURL | `https://www.bing.com/search?q={searchTerms}` | [Default search provider search URL](/en-us/deployedge/microsoft-edge-browser-policies/defaultsearchprovidersearchurl) |
    | SearchSuggestEnabled | Disabled | [Enable search suggestions](/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
    | ImportAutofillFormData | Disabled | [Allow importing of autofill form data](/en-us/deployedge/microsoft-edge-browser-policies/importautofillformdata) |
    | ImportSavedPasswords | Disabled | [Allow importing of saved passwords](/en-us/deployedge/microsoft-edge-browser-policies/importsavedpasswords) |
    | ImportBrowsingHistory | Disabled | [Allow importing of browsing history](/en-us/deployedge/microsoft-edge-browser-policies/importhistory) |
    | ImportCookies | Disabled | [Allow importing cookies](/en-us/deployedge/microsoft-edge-browser-policies/importcookies) |
    | ImportExtensions | Disabled | [Allow importing of extension](/en-us/deployedge/microsoft-edge-browser-policies/importextensions) |
    | ExtensionInstallBlocklist | `["external_component", "external_pref", "external_registry"]` | [Control which extensions cannot be installed](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallblocklist) |
    | ExtensionAllowedTypes | `["extension", "theme"]` | [Configure allowed extension types](/en-us/deployedge/microsoft-edge-browser-policies/extensionallowedtypes) |
    | ExtensionInstallSources | `[https://corp.contoso.com/*]` | [Configure extension and user script install sources](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallsources) |
    | DefaultDownloadDirectory | `${user_home}/Downloads/Edge` | [Set download directory](/en-us/deployedge/microsoft-edge-browser-policies/downloaddirectory) |
    | PromptForDownloadLocation | Enabled | [Ask where to save downloaded files](/en-us/deployedge/microsoft-edge-browser-policies/promptfordownloadlocation) |
    | HubsSidebarEnabled | Disabled | [Show Hubs Sidebar](/en-us/deployedge/microsoft-edge-browser-policies/hubssidebarenabled) |
    | ShowMicrosoftRewards | Disabled | [Show Microsoft Rewards experiences](/en-us/deployedge/microsoft-edge-browser-policies/showmicrosoftrewards) |
    | EdgeShoppingAssistantEnabled | Disabled | [Shopping in Microsoft Edge Enabled](/en-us/deployedge/microsoft-edge-browser-policies/edgeshoppingassistantenabled) |
    | EdgeWorkspacesEnabled | Enabled | [Edge Workspaces](/en-us/deployedge/microsoft-edge-browser-policies/edgeworkspacesenabled) |
    | FavoritesBarEnabled | Enabled | [Show favorites bar](/en-us/deployedge/microsoft-edge-browser-policies/favoritesbarenabled) |
    | AllowDeletingBrowserHistory | Enabled | [Enable deleting browser and download history](/en-us/deployedge/microsoft-edge-browser-policies/allowdeletingbrowserhistory) |
    | SmartScreenForTrustedDownloadsEnabled | Enabled | [Force Microsoft Defender SmartScreen checks on downloads from trusted sources](/en-us/deployedge/microsoft-edge-browser-policies/smartscreenfortrusteddownloadsenabled) |
    | InsecureContentAllowedForUrls | [] | [Allow insecure content on specified sites](/en-us/deployedge/microsoft-edge-browser-policies/insecurecontentallowedforurls) |
    | InsecureContentBlockedForUrls | ["\*"] | [Block insecure content on specified sites](/en-us/deployedge/microsoft-edge-browser-policies/insecurecontentblockedforurls) |
    | ExtensionInstallAllowlist | [] | [Allow specific extensions to be installed](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallallowlist) |
    | ExtensionInstallForcelist | [] | [Control which extensions are installed silently](/en-us/deployedge/microsoft-edge-browser-policies/extensioninstallforcelist) |
    | ExtensionSettings | {"\*":{"installation\_mode":"blocked"}} | [Configure extension management settings](/en-us/deployedge/microsoft-edge-browser-policies/extensionsettings) |
    | NativeMessagingAllowlist | [] | [Control which native messaging hosts users can use](/en-us/deployedge/microsoft-edge-browser-policies/nativemessagingallowlist) |
    | NativeMessagingBlocklist | ["\*"] | [Configure native messaging block list](/en-us/deployedge/microsoft-edge-browser-policies/nativemessagingblocklist) |
    | AutoSelectCertificateForUrls | ["\*.company.com"] | [Automatically select client certificates for these sites](/en-us/deployedge/microsoft-edge-browser-policies/autoselectcertificateforurls) |
    | WebRtcUdpPortRange | 10000:11000 | [Restrict the range of local UDP ports used by WebRTC](/en-us/deployedge/microsoft-edge-browser-policies/webrtcudpportrange) |
    | DefaultImagesSetting | Allow images (1) | [Default images setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultimagessetting) |
    | DefaultJavaScriptSetting | Allow JavaScript (1) | [Default JavaScript setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultjavascriptsetting) |
    | SyncDisabled | Enabled | [Disable synchronization of data using Microsoft sync services](/en-us/deployedge/microsoft-edge-browser-policies/syncdisabled) |
    | ForceSync | Disabled | [Force synchronization of browser data and do not show the sync consent prompt](/en-us/deployedge/microsoft-edge-browser-policies/forcesync) |
    | SleepingTabsEnabled | Enabled | [Configure sleeping tabs](/en-us/deployedge/microsoft-edge-browser-policies/sleepingtabsenabled) |
    | SearchSuggestEnabled | Disabled | [Enable search suggestions](/en-us/deployedge/microsoft-edge-browser-policies/searchsuggestenabled) |
    | LocalProvidersEnabled | Disabled | [Allow suggestions from local providers](/en-us/deployedge/microsoft-edge-browser-policies/localprovidersenabled) |
    | DefaultNotificationsSetting | Block (2) | [Default notification setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultnotificationssetting) |
    | DefaultGeolocationSetting | Don't allow sites to track users' physical location (2) | [Default geolocation setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultgeolocationsetting) |
    | WebUsbBlockedForUrls | [] | [Allow WebUSB on specific sites](/en-us/deployedge/microsoft-edge-browser-policies/webusballowdevicesforurls) |
    | WebUsbBlockDevicesForUrls | [{"urls":["*"],"devices":[{"vendor\_id":"*","product\_id":"\*"}]}] | [Block WebUSB on specific sites](/en-us/deployedge/microsoft-edge-browser-policies/webusbblockedforurls) |
    | WebRtcLocalhostIpHandling | Disable non-proxied UDP (default\_public\_interface\_only) | [Restrict exposure of local IP address by WebRTC](/en-us/deployedge/microsoft-edge-browser-policies/webrtclocalhostiphandling) |
    | URLAllowlist | ["*.company.com", "*.microsoft.com", "\*.office.com"] | [Define a list of allowed URLs](/en-us/deployedge/microsoft-edge-browser-policies/urlallowlist) |
    | URLBlocklist | ["\*"] | [Block access to a list of URLs](/en-us/deployedge/microsoft-edge-browser-policies/urlblocklist) |
    | CookiesAllowedForUrls | ["\*.company.com"] | [Allow cookies on specific sites](/en-us/deployedge/microsoft-edge-browser-policies/cookiesallowedforurls) |
    | CookiesBlockedForUrls | ["\*"] | [Block cookies on specific sites](/en-us/deployedge/microsoft-edge-browser-policies/cookiesblockedforurls) |
    | CookiesSessionOnlyForUrls | ["\*"] | [Limit cookies from specific websites to current session](/en-us/deployedge/microsoft-edge-browser-policies/cookiessessiononlyforurls) |
    | DownloadRestrictions | Block all downloads (4) | [Download restrictions](/en-us/deployedge/microsoft-edge-browser-policies/downloadrestrictions) |
    | ScreenCaptureAllowed | Disabled | [Allow or deny screen capture](/en-us/deployedge/microsoft-edge-browser-policies/screencaptureallowed) |
    | PrintingEnabled | Disabled | [Enable printing](/en-us/deployedge/microsoft-edge-browser-policies/printingenabled) |
    | DefaultClipboardSetting | Block clipboard (2) | [Default clipboard site permission](/en-us/deployedge/microsoft-edge-browser-policies/defaultclipboardsetting) |
    | VideoCaptureAllowed | Disabled | [Allow or block video capture](/en-us/deployedge/microsoft-edge-browser-policies/videocaptureallowed) |
    | InPrivateModeAvailability | InPrivate mode forced (2) | [Configure InPrivate mode availability](/en-us/deployedge/microsoft-edge-browser-policies/inprivatemodeavailability) |
    | ClearBrowsingDataOnExit | Enabled | [Clear browsing data when Microsoft Edge closes](/en-us/deployedge/microsoft-edge-browser-policies/clearbrowsingdataonexit) |
    | SavingBrowserHistoryDisabled | Enabled | [Disable saving browser history](/en-us/deployedge/microsoft-edge-browser-policies/savingbrowserhistorydisabled) |
    | DeveloperToolsAvailability | Disallowed (2) | [Control where developer tools can be used](/en-us/deployedge/microsoft-edge-browser-policies/developertoolsavailability) |
    | NetworkPredictionOptions | Don't predict (2) | [Enable network prediction](/en-us/deployedge/microsoft-edge-browser-policies/networkpredictionoptions) |
    | EdgeCollectionsEnabled | Disabled | [Enable the Collections feature](/en-us/deployedge/microsoft-edge-browser-policies/edgecollectionsenabled) |
8. Select **Next**.
9. For **Assignments**, assign to **SEB-Level3-Users** group.
10. Select **Next** to review the settings. Then choose **Create**.

### Validation (All Windows Levels)

#### Policy Application

- In the Intune admin center, verify the Settings Catalog, Security Baseline, APP, and ACP policy deployment status for the targeted Windows devices.

#### Endpoint Verification

- On the client device, open Microsoft Edge and navigate to `edge://policy`.
- Confirm that all configured policy keys appear with expected values and don't show an **Error** state.

#### URL and Feature Enforcement

- **Level 1:** Confirm core security controls are active, including SmartScreen, tracking prevention, and basic restriction settings.
- **Level 2:** Validate enhanced restrictions such as extension blocking, data sync restrictions, and clear-on-exit behaviors.
- **Level 3:** Attempt to browse to nonallowlisted URLs and verify they're blocked or isolated (for example, Application Guard).

#### Update Policies

- In `edge://policy`, search for **Update** to ensure the configured update behavior (for example, daily checks, suppressed hours, version pinning) matches the assigned security level.

#### Isolation Controls (Level 3 Only)

- Verify that high-risk or unapproved URLs trigger the expected isolation behavior, such as forced application isolation or a secure browsing container.

::: zone-end

::: zone pivot="android"

## App Configuration Policies for Android

Android app configuration policies customize Microsoft Edge for Business behavior on mobile devices. These policies define browser defaults, restrict risky features, and enforce privacy protections in alignment with enterprise security frameworks.

> 
> **Microsoft Documentation:**
> 
> - [Microsoft Edge Mobile Policies](/en-us/deployedge/microsoft-edge-mobile-policies)
> - [Android App Configuration Policies](../../app-management/configuration/overview)
> - [Managed App Configuration for Android](../../app-management/configuration/configure-managed-apps)
> 

**Prerequisites:**

- Android 10.0+ (8.0+ for userless devices)
- Microsoft Edge for Android installed
- Company Portal or Intune app installed
- Microsoft Intune license assigned to the user
- Device MAM-enabled or MDM-enrolled through Intune
- User signed in with Microsoft Entra ID account

### Level 1 – Basic Mobile Browser Configuration for Android

Level 1 configuration provides foundational browser security controls while maintaining user productivity.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics**tab, enter:
    - **Name:** Edge Android ACP Level 1 Basic
    - **Description:** Basic browser configuration for Microsoft Edge Android with essential security settings and fundamental mobile controls
4. In **Target policy to**, select **Selected apps**.
    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge (Android)**, then select **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | true | [Microsoft Entra password single sign-on](../../app-management/configuration/configure-edge-ios-android#microsoft-entra-password-single-sign-on) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [Microsoft Defender SmartScreen](../../app-management/configuration/configure-edge-ios-android#microsoft-defender-smartscreen) |
| EdgeMyApps | true | [Enable EdgeMyApps](/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Enforce default HTTPS](/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | false | [Disable password import](/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeNewTabPageLayout | 0 | [Configure new tab page layout](/en-us/deployedge/microsoft-edge-mobile-policies#edgenewtabpagelayout) |
| EdgeEnableKioskMode | false | [Enable kiosk mode](/en-us/deployedge/microsoft-edge-mobile-policies#edgeenablekioskmode) |
| EdgeShowAddressBarInKioskMode | true | [Show address bar in kiosk mode](/en-us/deployedge/microsoft-edge-mobile-policies#edgeshowaddressbarinkioskmode) |
| SmartScreenEnabled | true | [Enable SmartScreen](/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Enable search suggestions](/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | true | [Enable translate](/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | true | [Allow SSL error override](/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| DefaultBrowserSettingEnabled | true | [Enable as default browser](/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | true | [Enable Edge Copilot](/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| EdgeSharedDeviceSupportEnabled | true | [Enable shared device support](/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| ExperimentationAndConfigurationServiceControl | 1 | [Experimentation and configuration service control](/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| DefaultPopupsSetting | 2 | [Default pop-ups setting](/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| DefaultCookiesSetting | 1 | [Default cookies setting](/en-us/deployedge/microsoft-edge-mobile-policies#defaultcookiessetting) |
| BiometricAuthenticationBeforeFilling | false | [Biometric authentication before filling](/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Enable password manager](/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| EdgeBrandLogo | true | [Enable Edge brand logo](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Set Edge brand color](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Enable default search provider](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | "Preferred Company Search" | [Default search provider name](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | "https://search.company.com?q={searchTerms}" | [Default search provider search URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | "https://search.company.com/suggest?q={searchTerms}" | [Default search provider suggest URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | "company" | [Default search provider keyword](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| ProxySettings | {"ProxyServer": "IP:Port", "ProxyBypassList": "\*.company.com", "ProxyMode": "direct"} | [Configure proxy settings](/en-us/deployedge/microsoft-edge-browser-policies/proxysettings) |

1. Under Microsoft Tunnel for Mobile Application Management settings:

| Name | Value |
| --- | --- |
| Tunnel enabled | Not configured |
| Connection name | Not configured |
| Microsoft Tunnel site | Not configured |
| Per-App VPN (Android only) | No Per-App VPN |
| Automatic configuration script | Not configured |
| Address | Not configured |
| Port Number | Not configured |
| Root Certificate | Not configured |

1. Expand **Edge configuration settings** and configure:

| Name | Value |
| --- | --- |
| Application proxy redirection | Disable |
| Homepage shortcut URL | `https://www.company.com` |
| Managed bookmarks | Company Portal | `https://portal.company.com` |
| Allowed URLs | Leave empty (Level 3 uses Allowed URLs) |
| Blocked URLs | Leave empty (Level 2 uses Blocked URLs) |
| Redirect restricted sites to personal context | Disable |

1. Select **Next**
2. In **Assignments**, assign to **SEB-Level1-Users** group.
3. Select **Next** to review the settings. Then choose **Create**.

### Level 2 – Enhanced Mobile Browser Configuration for Android

Level 2 configuration adds enhanced security controls and restrictions for sensitive environments.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics**tab, enter:
    - **Name:** Edge Android ACP Level 2 Enhanced
    - **Description:** Enhanced browser configuration for Microsoft Edge Android with more security controls and data protection features
4. In **Target policy to**, select **Selected apps**.
    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge (Android)**, then select **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | true | [Microsoft Entra password single sign-on](../../app-management/configuration/configure-edge-ios-android#microsoft-entra-password-single-sign-on) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [Microsoft Defender SmartScreen](../../app-management/configuration/configure-edge-ios-android#microsoft-defender-smartscreen) |
| EdgeMyApps | true | [Enable EdgeMyApps](/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Enforce default HTTPS](/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | true | [Disable password import](/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeNewTabPageLayout | 1 | [Configure new tab page layout](/en-us/deployedge/microsoft-edge-mobile-policies#edgenewtabpagelayout) |
| EdgeEnableKioskMode | false | [Enable kiosk mode](/en-us/deployedge/microsoft-edge-mobile-policies#edgeenablekioskmode) |
| EdgeShowAddressBarInKioskMode | true | [Show address bar in kiosk mode](/en-us/deployedge/microsoft-edge-mobile-policies#edgeshowaddressbarinkioskmode) |
| SmartScreenEnabled | true | [Enable SmartScreen](/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Enable search suggestions](/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | true | [Enable translate](/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | false | [Allow SSL error override](/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| DefaultBrowserSettingEnabled | false | [Set as default browser](/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | false | [Enable Edge Copilot](/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| EdgeSharedDeviceSupportEnabled | true | [Enable shared device support](/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| ExperimentationAndConfigurationServiceControl | 0 | [Experimentation and configuration service control](/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| EdgeSyncDisabled | true | [Disable browser sync](/en-us/deployedge/microsoft-edge-mobile-policies#edgesyncdisabled) |
| SavingBrowserHistoryDisabled | false | [Disable browser history saving](/en-us/deployedge/microsoft-edge-mobile-policies#savingbrowserhistorydisabled) |
| DefaultPopupsSetting | 2 | [Default pop-ups setting](/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| DefaultCookiesSetting | 2 | [Default cookies setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultcookiessetting) |
| BiometricAuthenticationBeforeFilling | true | [Biometric authentication before filling](/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Enable password manager](/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| EdgeBrandLogo | true | [Enable Edge brand logo](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Set Edge brand color](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Enable default search provider](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | "Preferred Company Search" | [Default search provider name](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | "https://search.company.com?q={searchTerms}" | [Default search provider search URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | "https://search.company.com/suggest?q={searchTerms}" | [Default search provider suggest URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | "company" | [Default search provider keyword](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| ProxySettings | {"ProxyServer": "IP:Port", "ProxyBypassList": "\*.company.com", "ProxyMode": "direct"} | [Configure proxy settings](/en-us/deployedge/microsoft-edge-browser-policies/proxysettings) |
| EdgeDisabledFeatures | password|autofill|copilot|collections|readaloud | [Disable features](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisabledfeatures) |

1. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Allowed URLs | Leave empty (Level 2 uses blocked URLs instead – when blocked URLs are configured, allowed URLs field becomes unavailable) |
| Blocked URLs | \*.facebook.com, \*.twitter.com, \*.instagram.com, \*.tiktok.com |
| Redirect restricted sites to personal context | Enable |

1. Select **Next**
2. In **Assignments**, assign to **SEB-Level2-Users** group.
3. Select **Next** to review the settings. Then choose **Create**.

### Level 3 – High Security Mobile Configuration for Android

Level 3 configuration enforces maximum security with zero-trust controls and comprehensive data-loss prevention.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics**tab, enter:
    - **Name:** Edge Android ACP Level 3 High
    - **Description:** High security browser configuration for Microsoft Edge Android with maximum restrictions, strict isolation, and comprehensive privacy controls
4. In **Target policy to**, select **Selected apps**.
    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge (Android)**, then select **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | false | [Microsoft Entra password single sign-on](/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [SmartScreen enabled](../../app-management/configuration/configure-edge-ios-android#microsoft-defender-smartscreen) |
| EdgeMyApps | false | [Enable EdgeMyApps](/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Enforce default HTTPS](/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | true | [Disable importing passwords](/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeNewTabPageLayout | 2 | [Configure new tab page layout](/en-us/deployedge/microsoft-edge-mobile-policies#edgenewtabpagelayout) |
| EdgeEnableKioskMode | true | [Enable kiosk mode](/en-us/deployedge/microsoft-edge-mobile-policies#edgeenablekioskmode) |
| EdgeShowAddressBarInKioskMode | false | [Show address bar in kiosk mode](/en-us/deployedge/microsoft-edge-mobile-policies#edgeshowaddressbarinkioskmode) |
| SmartScreenEnabled | true | [SmartScreen enabled](/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Disable search suggestions](/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| EdgeSyncDisabled | true | [Disable browser sync](/en-us/deployedge/microsoft-edge-mobile-policies#edgesyncdisabled) |
| InPrivateModeAvailability | 1 | [Disable InPrivate mode](/en-us/deployedge/microsoft-edge-mobile-policies#inprivatemodeavailability) |
| SavingBrowserHistoryDisabled | true | [Disable browser history saving](/en-us/deployedge/microsoft-edge-mobile-policies#savingbrowserhistorydisabled) |
| DefaultPopupsSetting | 2 | [Default pop-ups setting](/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| TranslateEnabled | false | [Disable translate](/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | false | [SSL error override allowed](/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| EdgeSharedDeviceSupportEnabled | false | [Disable shared device support](/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| AutofillCreditCardEnabled | false | [Disable autofill for payment instructions](/en-us/deployedge/microsoft-edge-browser-policies/autofillcreditcardenabled) |
| DownloadRestrictions | 2 | [Download restrictions](/en-us/deployedge/microsoft-edge-browser-policies/downloadrestrictions) |
| ExperimentationAndConfigurationServiceControl | 0 | [Experimentation and configuration service control](/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| DefaultBrowserSettingEnabled | false | [Set as default browser](/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | false | [Enable Edge Copilot](/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| DefaultCookiesSetting | 4 | [Default cookies setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultcookiessetting) |
| DefaultJavaScriptSetting | 2 | [Default JavaScript setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultjavascriptsetting) |
| DefaultGeolocationSetting | 2 | [Default geolocation setting](/en-us/deployedge/microsoft-edge-browser-policies/defaultgeolocationsetting) |
| BiometricAuthenticationBeforeFilling | true | [Biometric authentication before filling](/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Enable password manager](/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| EdgeDisabledFeatures | inprivate|autofill|password|translator|readaloud|drop|coupons|extensions|copilot|collections|myapps | [Disable features](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisabledfeatures) |
| EdgeBrandLogo | true | [Enable Edge brand logo](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Set Edge brand color](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Enable default search provider](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | "Preferred Company Search" | [Default search provider name](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | "https://search.company.com?q={searchTerms}" | [Default search provider search URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | "https://search.company.com/suggest?q={searchTerms}" | [Default search provider suggest URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | "company" | [Default search provider keyword](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| ProxySettings | {"ProxyServer": "IP:Port", "ProxyBypassList": "\*.company.com", "ProxyMode": "fixed\_servers"} | [Configure proxy settings](/en-us/deployedge/microsoft-edge-browser-policies/proxysettings) |
| EdgeBlockSignInEnabled | true | [Block sign-in enabled](/en-us/deployedge/microsoft-edge-browser-policies/edgeblocksigninenabled) |

1. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Allowed URLs | \*.company.com, \*.microsoft.com, login.microsoftonline.com |
| Blocked URLs | Leave empty (Level 3 uses allowed URLs – when allowed URLs are configured, blocked URLs field becomes unavailable) |

1. Select **Next**
2. In **Assignments**, assign to **SEB-Level3-Users** group.
3. Select **Next** to review the settings. Then choose **Create**.

### Validation (All Android Levels)

#### Policy Application

- In the Intune admin center, verify the ACP deployment status for assigned Android devices.

#### Browser Configuration

- On an Android device, open Microsoft Edge and go to `edge://policy` to confirm the expected configuration values are present and not marked as errors.

#### URL Filtering

- **Level 1:** Confirm allowed URLs operate as expected.
- **Level 2:** Confirm blocked URLs (such as social media domains) are restricted.
- **Level 3:** Confirm only allowlisted corporate URLs are accessible.

#### Feature Restrictions

- Validate restricted features based on the assigned security level, such as InPrivate mode, autofill, password import, extensions, and Copilot visibility.

#### Homepage and Bookmarks

- Confirm the managed homepage and managed bookmarks appear correctly in Microsoft Edge.

#### Security Settings

- Verify that SmartScreen, HTTPS enforcement, and data-sharing restrictions operate according to the applied policy.

#### VPN Integration (If Configured)

- For deployments using Microsoft Tunnel, ensure per-app VPN settings connect and route traffic as defined in the ACP.

::: zone-end

::: zone pivot="ios-ipados"

## App Configuration Policies for iOS/iPadOS

iOS app configuration policies define and enforce browser behavior for Microsoft Edge for Business on iPhone and iPad devices. These policies provide progressive control over privacy, security, and data protection while aligning with Zero Trust principles.

> 
> **Microsoft Documentation:**
> 
> - [Microsoft Edge Mobile Policies](/en-us/deployedge/microsoft-edge-mobile-policies)
> - [iOS App Configuration Policies](../../app-management/configuration/overview)
> - [Managed App Configuration for iOS](../../app-management/configuration/configure-managed-apps)
> 

**Prerequisites:**

- iOS/iPadOS 17+
- Microsoft Edge for iOS installed
- Company Portal or Intune app installed
- Microsoft Intune license assigned to the user
- Device MAM-enabled or MDM-enrolled through Intune
- User signed in with Microsoft Entra ID account

Important

In iOS App Configuration Policies, **Allowed URLs** and **Blocked URLs** are mutually exclusive. When you configure one, the other becomes unavailable.

### Level 1 – Basic mobile browser configuration for iOS

Level 1 configuration provides foundational browser security controls while maintaining user productivity.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics**tab, enter:
    - **Name:** Edge iOS ACP Level 1 Basic
    - **Description:** Basic browser configuration for Microsoft Edge iOS with essential security settings and fundamental mobile controls
4. In **Target policy to**, select **Selected apps**.
    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge**.
    - Choose **Microsoft Edge (iOS/iPadOS)**, then **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | true | [Password single sign-on](/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [SmartScreen enabled](/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| EdgeMyApps | true | [Enable EdgeMyApps](/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Default HTTPS enforced](/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | false | [Disable password import](/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeProxyPacUrl |  | [Proxy PAC URL](/en-us/deployedge/microsoft-edge-mobile-policies#edgeproxypacurl) |
| BiometricAuthenticationBeforeFilling | false | [Biometric authentication before filling](/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Disable password manager](/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| SmartScreenEnabled | true | [SmartScreen enabled](/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Disable search suggestions](/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | true | [Translate enabled](/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | true | [SSL error override allowed](/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| DefaultBrowserSettingEnabled | true | [Default browser setting enabled](/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| ExperimentationAndConfigurationServiceControl | 1 | [Experimentation and configuration service control](/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| DefaultPopupsSetting | 2 | [Disable pop-ups](/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| EdgeBrandLogo | true | [Organizational branding – logo](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Organizational branding – color](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Default search provider enabled](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | Preferred Company Search | [Default search provider name](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://search.company.com?q={searchTerms}` | [Default search provider search URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | `https://search.company.com/suggest?q={searchTerms}` | [Default search provider suggest URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | company | [Default search provider keyword](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| EdgeNetworkStackPref | 0 | [Edge network stack preference](/en-us/deployedge/microsoft-edge-mobile-policies#edgenetworkstackpref) |

1. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Application proxy redirection | Disable |
| Homepage shortcut URL | `https://www.company.com` |
| Managed bookmarks | Company Portal | `https://portal.company.com` |
| Allowed URLs | Leave empty (Level 3 uses Allowed URLs) |
| Blocked URLs | Leave empty (Level 2 uses Blocked URLs) |
| Redirect restricted sites to personal context | Disable |

1. Select **Next**.
2. In **Assignments**, assign to **SEB-Level1-Users** group.
3. Select **Next** to review the settings. Then choose **Create** when you're done.

### Level 2 – Enhanced mobile browser configuration for iOS

Level 2 configuration adds enhanced security controls and restrictions for sensitive environments.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics**tab, enter:
    - **Name:** Edge iOS ACP Level 2 Enhanced
    - **Description:** Enhanced browser configuration for Microsoft Edge iOS with more security controls and data protection features
4. In **Target policy to**, select **Selected apps**.
    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge**.
    - Choose **Microsoft Edge (iOS/iPadOS)**, then **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | true | [Password single sign-on](/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [SmartScreen enabled](/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| EdgeMyApps | true | [Enable EdgeMyApps](/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Default HTTPS enforced](/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | true | [Disable password import](/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeProxyPacUrl |  | [Proxy PAC URL](/en-us/deployedge/microsoft-edge-mobile-policies#edgeproxypacurl) |
| BiometricAuthenticationBeforeFilling | true | [Biometric authentication before filling](/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Disable password manager](/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| SmartScreenEnabled | true | [SmartScreen enabled](/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Disable search suggestions](/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | true | [Translate enabled](/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | false | [SSL error override allowed](/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| EdgeNetworkStackPref | 0 | [Network stack preference](/en-us/deployedge/microsoft-edge-mobile-policies#edgenetworkstackpref) |
| DefaultBrowserSettingEnabled | false | [Default browser setting enabled](/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | false | [Disable Edge Copilot](/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| EdgeSharedDeviceSupportEnabled | true | [Enable shared device support](/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| ExperimentationAndConfigurationServiceControl | 0 | [Experimentation and configuration service control](/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| EdgeSyncDisabled | true | [Disable browser sync](/en-us/deployedge/microsoft-edge-mobile-policies#edgesyncdisabled) |
| SavingBrowserHistoryDisabled | false | [Disable browser history saving](/en-us/deployedge/microsoft-edge-mobile-policies#savingbrowserhistorydisabled) |
| DefaultPopupsSetting | 2 | [Disable pop-ups](/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| EdgeBrandLogo | true | [Organizational branding – logo](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Organizational branding – color](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Default search provider enabled](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | Preferred Company Search | [Default search provider name](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://search.company.com?q={searchTerms}` | [Default search provider search URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | `https://search.company.com/suggest?q={searchTerms}` | [Default search provider suggest URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | company | [Default search provider keyword](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| EdgeDisabledFeatures | password|autofill|copilot|collections|readaloud | [Disable features](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisabledfeatures) |
| EdgeBlockSignInEnabled | false | [Block sign-in enabled](/en-us/deployedge/microsoft-edge-mobile-policies#edgeblocksigninenabled) |

1. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Allowed URLs | Leave empty (Level 2 uses blocked URLs instead – when blocked URLs are configured, allowed URLs field becomes unavailable) |
| Blocked URLs | \*.facebook.com, \*.twitter.com, \*.instagram.com, \*.tiktok.com |
| Redirect restricted sites to personal context | Enable |

1. Select **Next**.
2. In **Assignments**, assign to **SEB-Level2-Users** group.
3. Select **Next** to review the settings. Then choose **Create** when you're done.

### Level 3 – High security mobile configuration for iOS

Level 3 configuration enforces maximum security with zero-trust controls and comprehensive data-loss prevention.

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Manage apps** &gt; **Configuration** &gt; **Create** &gt; **Managed apps**.
3. On the **Basics**tab, enter:
    - **Name:** Edge iOS ACP Level 3 High
    - **Description:** High security browser configuration for Microsoft Edge iOS with maximum restrictions, strict isolation, and comprehensive privacy controls
4. In **Target policy to**, select **Selected apps**.
    - Choose **+ Select public apps**.
    - In the **Select apps to target** panel, search for and select **Microsoft Edge (iOS/iPadOS)**, then select **Select**.
5. Select **Next**.
6. On the **Settings** step, expand **General configuration settings**.
7. Configure each setting using the **Name** and **Value** specified:

| Name | Value | Documentation |
| --- | --- | --- |
| com.microsoft.intune.mam.managedbrowser.PasswordSSO | false | [Password single sign-on](/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| com.microsoft.intune.mam.managedbrowser.SmartScreenEnabled | true | [SmartScreen enabled](/en-us/microsoft-365/solutions/apps-config-step-4#general-app-configuration-settings) |
| EdgeMyApps | false | [Enable EdgeMyApps](/en-us/deployedge/microsoft-edge-mobile-policies#edgemyapps) |
| EdgeDefaultHTTPS | true | [Default HTTPS enforced](/en-us/deployedge/microsoft-edge-mobile-policies#edgedefaulthttps) |
| EdgeDisableShareUsageData | true | [Disable sharing usage data](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisableshareusagedata) |
| EdgeImportPasswordsDisabled | true | [Disable password import](/en-us/deployedge/microsoft-edge-mobile-policies#edgeimportpasswordsdisabled) |
| EdgeProxyPacUrl |  | [Proxy PAC URL](/en-us/deployedge/microsoft-edge-mobile-policies#edgeproxypacurl) |
| BiometricAuthenticationBeforeFilling | true | [Biometric authentication before filling](/en-us/deployedge/microsoft-edge-browser-policies/biometricauthenticationbeforefilling) |
| PasswordManagerEnabled | false | [Disable password manager](/en-us/deployedge/microsoft-edge-mobile-policies#passwordmanagerenabled) |
| SmartScreenEnabled | true | [SmartScreen enabled](/en-us/deployedge/microsoft-edge-mobile-policies#smartscreenenabled) |
| SearchSuggestEnabled | false | [Disable search suggestions](/en-us/deployedge/microsoft-edge-mobile-policies#searchsuggestenabled) |
| TranslateEnabled | false | [Translate enabled](/en-us/deployedge/microsoft-edge-mobile-policies#translateenabled) |
| HideFirstRunExperience | true | [Hide first run experience](/en-us/deployedge/microsoft-edge-mobile-policies#hidefirstrunexperience) |
| SSLErrorOverrideAllowed | false | [SSL error override allowed](/en-us/deployedge/microsoft-edge-mobile-policies#sslerroroverrideallowed) |
| EdgeNetworkStackPref | 0 | [Network stack preference](/en-us/deployedge/microsoft-edge-mobile-policies#edgenetworkstackpref) |
| DefaultBrowserSettingEnabled | false | [Default browser setting enabled](/en-us/deployedge/microsoft-edge-mobile-policies#defaultbrowsersettingenabled) |
| EdgeCopilotEnabled | false | [Disable Edge Copilot](/en-us/deployedge/microsoft-edge-mobile-policies#edgecopilotenabled) |
| EdgeSharedDeviceSupportEnabled | false | [Disable shared device support](/en-us/deployedge/microsoft-edge-mobile-policies#edgeshareddevicesupportenabled) |
| ExperimentationAndConfigurationServiceControl | 0 | [Experimentation and configuration service control](/en-us/deployedge/microsoft-edge-mobile-policies#experimentationandconfigurationservicecontrol) |
| EdgeSyncDisabled | true | [Disable browser sync](/en-us/deployedge/microsoft-edge-mobile-policies#edgesyncdisabled) |
| SavingBrowserHistoryDisabled | true | [Disable browser history saving](/en-us/deployedge/microsoft-edge-mobile-policies#savingbrowserhistorydisabled) |
| DefaultPopupsSetting | 2 | [Disable pop-ups](/en-us/deployedge/microsoft-edge-mobile-policies#defaultpopupssetting) |
| EdgeBrandLogo | true | [Organizational branding – logo](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandlogo) |
| EdgeBrandColor | `#0078d4` | [Organizational branding – color](/en-us/deployedge/microsoft-edge-mobile-policies#edgebrandcolor) |
| DefaultSearchProviderEnabled | true | [Default search provider enabled](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderenabled) |
| DefaultSearchProviderName | Preferred Company Search | [Default search provider name](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidername) |
| DefaultSearchProviderSearchURL | `https://search.company.com?q={searchTerms}` | [Default search provider search URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersearchurl) |
| DefaultSearchProviderSuggestURL | `https://search.company.com/suggest?q={searchTerms}` | [Default search provider suggest URL](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchprovidersuggesturl) |
| DefaultSearchProviderKeyword | company | [Default search provider keyword](/en-us/deployedge/microsoft-edge-mobile-policies#defaultsearchproviderkeyword) |
| EdgeDisabledFeatures | inprivate|autofill|password|translator|readaloud|drop|coupons|extensions|copilot|collections|myapps|share | [Disable features](/en-us/deployedge/microsoft-edge-mobile-policies#edgedisabledfeatures) |
| EdgeBlockSignInEnabled | true | [Block sign-in enabled](/en-us/deployedge/microsoft-edge-browser-policies/edgeblocksigninenabled) |

1. Expand **Edge configuration settings** and configure:

| Setting | Value |
| --- | --- |
| Allowed URLs | \*.company.com, \*.microsoft.com, login.microsoftonline.com |
| Blocked URLs | Leave empty (Level 3 uses allowed URLs – when allowed URLs are configured, blocked URLs field becomes unavailable) |

1. Per-App VPN (optional): Integrate with Microsoft Tunnel if necessary for isolated secure traffic routing
2. Select **Next**.
3. In **Assignments**, assign to **SEB-Level3-Users** group.
4. Select **Next** to review the settings. Then choose **Create** when you're done.

### Validation (All iOS Levels)

#### Policy Application

- In the Intune admin center, verify the assigned App Protection and App Configuration policies have successfully deployed to the targeted iOS devices.

#### App Configuration Verification

- On the device, open Microsoft Edge and navigate to **Settings**.
- Confirm that managed configuration values—such as homepage, search provider, password manager, and disabled features—match the applied ACP settings.

#### URL Filtering

- **Level 1:** Confirm that allowed URLs operate as expected.
- **Level 2:** Verify that blocked URL categories (for example, social media domains) can't be accessed.
- **Level 3:** Confirm that only the configured corporate allowlisted URLs are accessible.

#### Feature Restrictions

- Validate restricted features based on the assigned level, including:
    - **Level 1:** SmartScreen, pop-up blocking, and basic security controls.
    - **Level 2:** Sync disabled, password import blocked, biometric authentication for filling enabled, InPrivate browsing controlled.
    - **Level 3:** InPrivate disabled, history saving disabled, shared device mode disabled, and advanced restrictions (such as Collections, Extensions, Drop, Copilot) enforced.

#### Homepage and Bookmarks

- Confirm that the managed homepage and any configured managed bookmarks appear correctly in Microsoft Edge.

#### Policy Dependency Check

- Ensure the user is signed in to Edge using their work or school (Entra ID) account, as App Configuration settings only apply within the managed work profile context.

::: zone-end