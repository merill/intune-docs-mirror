---
layout: Conceptual
title: Windows Delivery Optimization settings for Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-delivery-optimization-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Delivery Optimization settings for Windows devices that you can deploy using Intune.
ms.date: 2025-04-22T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: davguy
locale: en-us
document_id: 3703d442-93e7-de37-2b6c-b50599654b0a
document_version_independent_id: 3703d442-93e7-de37-2b6c-b50599654b0a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-delivery-optimization-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-delivery-optimization-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-delivery-optimization-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 46114907-4b89-c685-4836-14eff6881752
---

# Windows Delivery Optimization settings for Intune - Microsoft Intune | Microsoft Learn

This feature applies to:

- Windows

Note

The information in this article applies to Intune profiles for Delivery Optimization created before April 24, 2025.

This article details the settings you can find in Windows device configuration templates for Delivery Optimization created before April 24, 2025. On April 24, 2025, the original Delivery Optimization template was deprecated and replaced by a new template that uses the newer settings format as found in the Settings Catalog.

For profiles that use the new settings format, Intune no longer maintains a list of each setting by name. Instead, the name of each setting, its configuration options, and its explanatory text that is available within in the Microsoft Intune admin center are taken directly from the settings authoritative content. You can access that content by viewing a settings *information text* and then selecting the **Learn more** link.

> 
> Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](../settings-catalog/).

This article lists some of the settings for Delivery Optimization that Intune supports for devices that run Windows.

Most options in the Microsoft Intune admin center directly map to Delivery Optimization settings that are covered in-depth in the Windows documentation. These options include links to relevant content. Settings or options that are specific to Intune don't contain links to additional content.

The following tables include:

- **Setting**: The setting as it appears in Intune. Settings that are links open the relevant entry in [Configure Delivery Optimization for Windows updates](/en-us/windows/deployment/update/waas-delivery-optimization) in the Windows documentation where you can learn more about the setting.
- **Windows version**: The minimum version of Windows that includes support for this setting.
- **Details**: A brief description of how Intune implements the setting, including the Intune default. When available, there are links to [Delivery Optimization Policy configuration service provider](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization) (CSP) entries.

To configure Intune to use these settings, see [Deliver updates](configure-delivery-optimization-windows).

## Before you begin

- [Create a Windows Delivery Optimization profile](configure-delivery-optimization-windows).

## Delivery Optimization

| Setting | Windows version | Details |
| --- | --- | --- |
| [Download mode](/en-us/windows/deployment/update/waas-delivery-optimization-reference#download-mode) | 1511 | Specify the download method that Delivery Optimization uses to download content.<br>- **Not configured**: End users update their devices using their own methods, which might be to use the *Windows Updates or Delivery Optimization* settings available with the operating system.<br>- **HTTP only, no peering (0)**: Get updates only from the internet. Don't get updates from other computers on your network (peer-to-peer).<br>- **HTTP blended with peering behind the same NAT (1)**: Get updates from the internet and from other computers on your network that are behind the same Network Address Translation (NAT) IP addresses.<br>- **HTTP blended with peering across a private group (2)**: Peering occurs on devices with the same Group ID. When this option is selected, peering crosses your NAT IP addresses.<br>- **HTTP blended with Internet peering (3)**: Get updates from the internet and from other computers on your network.<br>- **Simple download mode with no peering (99)**: Gets updates from the internet, directly from the update owner, such as Microsoft. It doesn't contact the Delivery Optimization cloud services.<br>- **Bypass mode (100)**: Use Background Intelligent Transfer Service (BITS) to get updates. Don't use Delivery Optimization.<br><br>**Default**: Not configured  Policy CSP: [DODownloadMode](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dodownloadmode) |
| [Restrict Peer Selection](/en-us/windows/deployment/update/waas-delivery-optimization-reference#select-a-method-to-restrict-peer-selection) | 1803 | Requires **Download mode** be set to *HTTP blended with peering behind the same NAT (1)* or *HTTP blended with peering across a private group (2)*.Restricts peer selection to a specific group of devices.**Default**: Not configured  Policy CSP: [DORestrictPeerSelectionBy](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dorestrictpeerselectionby) |
| [Group ID source](/en-us/windows/deployment/update/waas-delivery-optimization-reference#select-the-source-of-group-ids) | 1803 | Requires **Download mode** be set to *HTTP blended with peering across a private group*.Restricts peer selection to a specific group of devices by source.If you select **Custom**, you then configure **Group ID (as GUID)**. Use a GUID as the Group ID if you need to create a single group for Local Network Peering for branches that are on different domains or aren't on the same LAN. **Default**: Not configured  Policy CSP: [DOGroupId](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dogroupid) |

## Bandwidth

Note

**DOMaxDownloadBandwidth** and **DOMaxUploadBandwidth** are [deprecated](/en-us/windows/deployment/deploy-whats-new#delivery-optimization). Instead, use **DO Max Foreground Download Bandwidth** and **DO Max Background Download Bandwidth** that can be configured through the Intune [settings catalog](../settings-catalog/).

| Setting | Windows version | Details |
| --- | --- | --- |
| Bandwidth optimization type | *See details* | Select how Intune determines the maximum bandwidth that Delivery Optimization can use across all concurrent download activities.  Options include: <br>- **Not configured**<br>- **Absolute** – Specify the [Maximum download bandwidth (in KB/s)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#maximum-download-bandwidth) and the [Maximum upload bandwidth (in KB/s)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#max-upload-bandwidth) that a device can use across all its concurrent Delivery Optimization downloads activities.&lt;br Policy CSP: [DOMaxDownloadBandwidth](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domaxdownloadbandwidth) (*deprecated*) and [DOMaxUploadBandwidth](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domaxuploadbandwidth) (*deprecated*)<br>- **Percent** – Specify the [Maximum foreground download bandwidth (in %)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth) and [Maximum background download bandwidth (in %)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#maximum-foreground-download-bandwidth) that a device can use across all its concurrent Delivery Optimization downloads activities.  Policy CSP: [DOPercentageMaxForegroundBandwidth](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dopercentagemaxforegroundbandwidth) and [DOPercentageMaxBackgroundBandwidth](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dopercentagemaxbackgroundbandwidth)<br>- **Percent with business hours** – For a maximum [foreground](/en-us/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-foreground-download-bandwidth) download bandwidth, and a maximum [background](/en-us/windows/deployment/update/waas-delivery-optimization-reference#set-business-hours-to-limit-background-download-bandwidth) download bandwidth, configure business hours start and end times, and then the percentage of bandwidth to use during and outside your business hours.  Policy CSP: [DOSetHoursToLimitBackgroundDownloadBandwidth](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dosethourstolimitbackgrounddownloadbandwidth) and [DOSetHoursToLimitForegroundDownloadBandwidth](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dosethourstolimitforegrounddownloadbandwidth) |
| [Delay background HTTP download (in seconds)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#delay-background-download-from-http-in-secs) | 1803 | Use this setting to configure a maximum time to delay a background download of content over HTTP. This configuration applies only to downloads that support a peer-to-peer download source. During this delay, the device searches for a peer with the content available. While devices wait for a peer source, the download appears to be stuck for the end user. **Default**: *No value is configured***Recommended**: 60 seconds Policy CSP: [DODelayBackgroundDownloadFromHttp](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dodelaybackgrounddownloadfromhttp) |
| [Delay foreground HTTP download (in seconds)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#delay-foreground-download-from-http-in-secs) | 1803 | Configure a maximum time to delay a foreground (interactive) download of content over HTTP. This configuration applies only to downloads that support a peer-to-peer download source. During this delay, the device searches for a peer with the content available. While devices wait for a peer source, the download appears to be stuck for the end user. **Default**: *No value is configured***Recommended**: 60 seconds Policy CSP: [DODelayForegroundDownloadFromHttp](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dodelayforegrounddownloadfromhttp) |

## Caching

| Setting | Windows version | Details |
| --- | --- | --- |
| [Minimum RAM required for peer caching (in GB)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#minimum-ram-inclusive-allowed-to-use-peer-caching) | 1709 | Specify the minimum RAM size in GBs that a device must have to use peer caching. **Default**: *No value is configured***Recommended**: 4 GB Policy CSP: [DOMinRAMAllowedToPeer](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dominramallowedtopeer) |
| [Minimum disk size required for peer caching (in GB)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#minimum-disk-size-allowed-to-use-peer-caching) | 1709 | Specify the minimum disk size in GBs that a device must have to use peer caching. **Default**: *No value is configured***Recommended**: 32 GB Policy CSP: [DOMinDiskSizeAllowedToPeer](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domindisksizeallowedtopeer) |
| [Minimum content file size for peer caching (in MB)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#minimum-peer-caching-content-file-size) | 1709 | Specify the minimum size in MB that a file must meet or exceeded to use peer caching. **Default**: *No value is configured***Recommended**: 10 MB  Policy CSP: [DOMinFileSizeToCache](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dominfilesizetocache) |
| [Minimum battery level required to upload (in %)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#allow-uploads-while-the-device-is-on-battery-while-under-set-battery-level) | 1709 | Specify as a percent, the minimum battery level that a device must have to upload data to peers. If the battery level drops to the specified value, any active uploads automatically pause. **Default**: *No value is configured***Recommended**: 40%  Policy CSP: [DOMinBatteryPercentageAllowedToUpload](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dominbatterypercentageallowedtoupload) |
| [Modify cache drive](/en-us/windows/deployment/update/waas-delivery-optimization-reference#modify-cache-drive) | 1607 | Specify the drive that Delivery Optimization uses for its cache. You can use an environment variable, drive letter, or a full path. **Default**: %SystemDrive%  Policy CSP: [DOModifyCacheDrive](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domodifycachedrive) |
| [Maximum cache age (in days)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#max-cache-age) | 1511 | Specify for how long after each file successfully downloads that the file is held in the Delivery Optimization cache on a device.  With Intune, you configure the cache age in days. The number of days you define is converted into the applicable number of seconds, which is how Windows defines this setting. For example, an Intune configuration of three days is converted on the device to 259200 seconds (three days). **Default**: *No value is configured***Recommended**: 7  Policy CSP: [DOMaxCacheAge](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domaxcacheage) |
| Maximum cache size type | *See details* | Select how to manage the amount of disk space on a device that is used by Delivery Optimization. When not configured, cache size defaults to 20% of the free disk space available. <br>- **Not configured** (Default)<br>- **Absolute** – Specify the [Absolute maximum cache size (in GB)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#absolute-max-cache-size) to configure the maximum amount of drive space a device can use for Delivery Optimization. When set to 0 (zero), the cache size is unlimited, although Delivery Optimization clears the cache when the device is low on disk space.  Policy CSP: [DOAbsoluteMaxCacheSize](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#doabsolutemaxcachesize)<br>- **Percentage** – Specify the [Maximum cache size (in %)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#max-cache-size) to configure the maximum amount of drive space a device can use for Delivery Optimization. The percentage is of the available drive space, and Delivery Optimization constantly assesses the available drive space and clears the cache to keep the maximum cache size under the set percentage.  Policy CSP: [DOMaxCacheSize](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domaxcachesize) |
| [VPN peer caching](/en-us/windows/deployment/update/waas-delivery-optimization-reference#enable-peer-caching-while-the-device-connects-via-vpn) | 1709 | Select **Enabled** to configure a device to participate in Peer Caching while connected by VPN to the domain network. Devices that are enabled can download from or upload to other domain network devices, either on VPN or on the corporate domain network. **Default**: Not configured  Policy CSP: [DOAllowVPNPeerCaching](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domaxcacheage) |

## Local Server Caching

| Setting | Details |
| --- | --- |
| Cache server host names | Specify the IP address or FQDN of Network Cache servers that will be used by your devices for Delivery Optimization, and then select **Add** to add that entry to the list. **Default**: Not configured  Policy CSP: [DOCacheHost](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#docachehost) |
| [Delay foreground download Cache Server fallback (in seconds)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#delay-foreground-download-cache-server-fallback-in-secs) | Specify a time in seconds (0-2592000) to delay the fallback from a Cache server to the HTTP source for a foreground content download. When the Bandwidth setting for *Delay background HTTP download (in seconds)* is configured, that setting applies first to allow downloads from peers. (0-2592000). **Default**: 0  Policy CSP [DODelayCacheServerFallbackForeground](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dodelaycacheserverfallbackforeground) |
| [Delay background download Cache Server fallback (in seconds)](/en-us/windows/deployment/update/waas-delivery-optimization-reference#delay-background-download-cache-server-fallback-in-secs) | Specify a time in seconds (0-2592000) to delay the fallback from a Cache server to the HTTP source for a background content download. When the Bandwidth setting for *Delay background HTTP download (in seconds)* is configured, that setting applies first to allow downloads from peers. (0-2592000) **Default**: 0  Policy CSP: [DODelayCacheServerFallbackBackground](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dodelaycacheserverfallbackbackground) |

Note

When you install a Microsoft Connected Cache on a Configuration Manager distribution point, cloud-managed devices can use the on-premises cache. As long as the device can communicate with the server, the cache is available to deliver content to these devices. For more information, see [Microsoft Connected Cache in Configuration Manager](../../configmgr/core/plan-design/hierarchy/microsoft-connected-cache).