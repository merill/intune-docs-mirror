---
layout: Conceptual
title: Common Education Windows Delivery Optimization configuration - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/ref-delivery-optimization-settings-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: yegor-a
ms.author: egorabr
ms.subservice: education
description: Learn about common Windows Delivery Optimization configuration used by Education organizations in Intune.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
ms.collection:
- graph-interactive
locale: en-us
document_id: 3edeb364-3039-33f6-9956-d5b5c66b5cd5
document_version_independent_id: 3edeb364-3039-33f6-9956-d5b5c66b5cd5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/ref-delivery-optimization-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
interactive_type: msgraph
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/ref-delivery-optimization-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/ref-delivery-optimization-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6f113c3f-4825-2c24-fe8f-a00e5b255068
---

# Common Education Windows Delivery Optimization configuration - Microsoft Intune | Microsoft Learn

There are many configuration options you can set in Delivery Optimization to customize the content delivery experience specific to your environment needs. This article summarizes the configurations that are most commonly used for student and teacher devices.

Windows Delivery Optimization helps you get Windows updates and Microsoft Store apps more quickly and reliably. It works by letting you get Windows updates and Microsoft Store apps from sources in addition to Microsoft, like other PCs on your local network, or PCs on the internet that are downloading the same files. Delivery Optimization also sends updates and apps from your PC to other PCs on your local network or PCs on the internet, based on your settings. Sharing this data between PCs helps reduce the internet bandwidth that's needed to keep more than one device up to date or can make downloads more successful if you have a limited or unreliable internet connection. Delivery Optimization creates a local cache, and stores files that it has downloaded in that cache for a short period of time.

To learn more, see:

- [Use the settings catalog to configure settings on Windows, iOS/iPadOS, and macOS devices](../../../device-configuration/settings-catalog/)
- [Delivery Optimization reference](/en-us/windows/deployment/do/waas-delivery-optimization-reference)
- [YouTube: Delivery Optimization](https://www.youtube.com/playlist?list=PLMuDtq95SdKtN9lntgTcuhsYCsSQR4Dyl)

Tip

When creating a settings catalog profile in the Microsoft Intune admin center, you can copy a policy name from this article and paste it into the settings picker search field to find the desired policy.

# [Settings](#tab/settings)
| **Category** | **Name** | **Value** | **Notes** | **CSP** |
| --- | --- | --- | --- | --- |
| Delivery Optimization | **DO Delay Background Download From Http** | 3600 | 1 hour in seconds. After the max delay is reached, the download will resume using HTTP, either downloading the entire payload or complementing the bytes that couldn't be downloaded from Peers. | [DODelayBackgroundDownloadFromHttp](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dodelaybackgrounddownloadfromhttp) |
| Delivery Optimization | **DO Download Mode** | HTTP blended with peering behind the same NAT. | Delivery Optimization enables peer sharing on the same network between clients that connect to the Internet using the same public IP. | [DODownloadMode](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dodownloadmode) |
| Delivery Optimization | **DO Max Cache Age** | 1209600 | 14 days in seconds. Specifies the maximum time in seconds that each file is held in the Delivery Optimization cache after downloading successfully. | [DOMaxCacheAge](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domaxcacheage) |
| Delivery Optimization | **DO Min Disk Size Allowed To Peer** | 100 | Specifies the required minimum disk size (capacity in GB) for the device to use Peer Caching. Recommended values: 64 GB to 256 GB.Adjust as necessary according to your hardware. | [DOMinDiskSizeAllowedToPeer](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#domindisksizeallowedtopeer) |
| Delivery Optimization | **DO Min File Size To Cache** | 5 | Specifies the minimum content file size in MB enabled to use Peer Caching. | [DOMinFileSizeToCache](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dominfilesizetocache) |
| Delivery Optimization | **DO Min RAM Allowed To Peer** | 2 | Specifies the minimum RAM size in GB required to use Peer Caching. | [DOMinRAMAllowedToPeer](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dominramallowedtopeer) |
| Delivery Optimization | **DO Restrict Peer selection By** | Subnet mask | Set this policy to restrict peer selection | [DORestrictPeerSelectionBy](/en-us/windows/client-management/mdm/policy-csp-deliveryoptimization#dorestrictpeerselectionby) |

# [Create policy using Graph Explorer](#tab/graph)
Use Graph to create the settings catalog policy in your tenant without assignments or scope tags.

This will create a policy in your tenant with the name **\_MSLearn\_Example\_CommonEDU - Windows - Delivery Optimization**.

```msgraph
POST https://graph.microsoft.com/beta/deviceManagement/configurationPolicies
Content-Type: application/json

{"name":"_MSLearn_Example_CommonEDU - Windows - Delivery Optimization","description":"https://aka.ms/ManageEduDevices","platforms":"windows10","technologies":"mdm","roleScopeTagIds":["0"],"settings":[{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_deliveryoptimization_dodelaybackgrounddownloadfromhttp","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationIntegerSettingValue","value":3600}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_deliveryoptimization_dodownloadmode","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_deliveryoptimization_dodownloadmode_1","children":[]}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_deliveryoptimization_domaxcacheage","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationIntegerSettingValue","value":1209600}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_deliveryoptimization_domindisksizeallowedtopeer","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationIntegerSettingValue","value":100}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_deliveryoptimization_dominfilesizetocache","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationIntegerSettingValue","value":5}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSimpleSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_deliveryoptimization_dominramallowedtopeer","simpleSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationIntegerSettingValue","value":2}}},{"@odata.type":"#microsoft.graph.deviceManagementConfigurationSetting","settingInstance":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingInstance","settingDefinitionId":"device_vendor_msft_policy_config_deliveryoptimization_dorestrictpeerselectionby","choiceSettingValue":{"@odata.type":"#microsoft.graph.deviceManagementConfigurationChoiceSettingValue","value":"device_vendor_msft_policy_config_deliveryoptimization_dorestrictpeerselectionby_1","children":[]}}}]}
```

1. Click *Try it* to open Graph Explorer.
2. Once Graph Explorer is open, select the ![](../../../media/icons/16/person.svg) user icon in the top right to sign-in and sign in with your Intune administrator organizational account.
3. Click **Run query** to create the policy in your tenant.

    Tip

    If it's the first time using Graph Explorer, you may need to authorize the application to access your tenant or to modify the existing permissions. This graph call requires *DeviceManagementConfiguration.ReadWrite.All* permissions. You can grant the required permissions by selecting **modify permissions** and then selecting **Consent**.
4. The policy is created in your tenant and can be edited to meet your requirements before assigning to groups.

Note

As of July 31 2025, Microsoft Graph replaced use of the *DeviceManagementConfiguration.ReadWrite.All* permission with *DeviceManagementScripts.ReadWrite.All* for the following API calls:

- ~/deviceManagement/deviceShellScripts
- ~/deviceManagement/deviceHealthScripts
- ~/deviceManagement/deviceComplianceScripts
- ~/deviceManagement/deviceCustomAttributeShellScripts
- ~/deviceManagement/deviceManagementScripts

---