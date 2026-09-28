---
layout: Conceptual
title: Windows Autopilot requirements | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/requirements
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Software, Networking, Licensing, and Configuration requirements for Windows Autopilot.
ms.date: 2025-07-08T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: article
ms.custom:
- CI 116757
- CSSTroubleshooting
locale: en-us
document_id: bae99d36-424f-dda3-562e-cba08dc4af9f
document_version_independent_id: bae99d36-424f-dda3-562e-cba08dc4af9f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/requirements.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/requirements.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 202d0e31-a477-f3c8-8fca-df1e2c2c5069
---

# Windows Autopilot requirements | Microsoft Learn

Tip

RSS can be used to notify when requirements are added or updated to this page. For example, the following RSS link includes this article:

```url
https://learn.microsoft.com/api/search/rss?search=%22The+list+of+requirements+for+Windows+Autopilot+is+organized+into+four+different+categories%22&locale=en-us&%24filter=
```

This example includes the `&locale=en-us` variable. The `locale` variable is required, but it can be changed to another supported locale. For example, `&locale=es-es`.

For more information on using RSS for notifications, see [How to use the docs](/en-us/intune/use-docs#notifications) in the Intune documentation.

The list of requirements for Windows Autopilot is organized into four different categories:

- **Software** - OS requirements.
- **Networking** - networking requirements.
- **Licensing** - licensing requirements.
- **Configuration** - configurations required in Microsoft Entra ID and Microsoft Intune.

Select the appropriate tab to see the relevant requirements:

# [Software](#tab/software)
### Software requirements

Windows Autopilot depends on specific features available in Windows client, Microsoft Entra ID, and the mobile device management (MDM) service such as Microsoft Intune. To use Windows Autopilot and access these features, some software requirements must be met.

Note

For a list of OEMs that currently support Windows Autopilot, see the Participant device manufacturers section at [Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot).

#### Windows 11

A [supported version](/en-us/windows/release-health/windows11-release-information) of Windows 11 General Availability Channel is required.

The following editions of Windows 11 are supported:

- Windows 11 Pro.
- Windows 11 Pro Education.
- Windows 11 Pro for Workstations.
- Windows 11 Enterprise.
- Windows 11 Education.
- [Windows 11 Enterprise LTSC](/en-us/windows/whats-new/ltsc/overview).
- Windows 11 IoT Enterprise only when used in Microsoft Teams Rooms devices.

#### Windows 10

A [supported version](/en-us/windows/release-health/release-information) of Windows 10 is required.

The following editions of Windows 10 are supported:

- Windows 10 Pro.
- Windows 10 Pro Education.
- Windows 10 Pro for Workstations.
- Windows 10 Enterprise.
- Windows 10 Education.
- [Windows 10 Enterprise LTSC](/en-us/windows/whats-new/ltsc/overview).
- Windows 10 IoT Enterprise only when used in Microsoft Teams Rooms devices.

#### HoloLens

- Windows Autopilot for HoloLens 2 requires a currently supported version of Windows Holographic. For more information, see [Windows Autopilot for HoloLens 2](/en-us/hololens/hololens2-autopilot).

Note

Procedures for deploying Windows Autopilot might refer to specific products and versions. The inclusion of these products in this content doesn't imply an extension of support for a version that is beyond its support lifecycle. Windows Autopilot doesn't support products that are beyond their support lifecycle. For more information, see [Microsoft Lifecycle Policy](/en-us/lifecycle/).

# [Networking](#tab/networking)
### Networking requirements

Windows Autopilot depends on various internet-based services. Access to these services must be provided for Windows Autopilot to function properly. In the simplest case, enabling proper functionality can be achieved by ensuring the following conditions:

- Ensure Domain Name Services (DNS) name resolution for internet DNS names.
- Allow access to all hosts via port 80 (HTTP), 443 (HTTPS), and 123 (UDP/NTP).

Additional configuration might be required to grant access to required services in environments that:

- Have more restrictive internet access.
- Require authentication before internet access can be obtained.

Note

Smart card and certificate based authentication is supported during the out-of-box experience (OOBE) with [Entra Certificate-based authentication](/en-us/entra/identity/authentication/concept-certificate-based-authentication). For more information, see [Entra certificate-based authentication & OOBE](/en-us/entra/identity/authentication/concept-certificate-based-authentication-smartcard#windows-out-of-the-box-experience-oobe).

#### Service requirements

Windows Autopilot relies on several different type of services to function properly. In order for these services to function properly, certain network configurations need to be performed. These services and their required network configurations are as follows:

##### Windows Autopilot Deployment Service

After a network connection is in place, each Windows device will contact the Windows Autopilot Deployment Service. The following URLs are used:

- `https://ztd.dds.microsoft.com`
- `https://login.live.com`

##### Windows Activation

Windows Autopilot requires Windows Activation services. For more information about the URLs that need to be accessible for the activation services, see [Windows activation or validation fails with error code 0x8004FE33](https://support.microsoft.com/topic/windows-activation-or-validation-fails-with-error-code-0x8004fe33-a9afe65e-230b-c1ed-3414-39acd7fddf52).

##### Microsoft Entra ID

Microsoft Entra ID validates user credentials. Additionally, the device is joined or registered to Microsoft Entra ID during Windows Autopilot. For more information, see [Office 365 IP Address and URL Web service](/en-us/microsoft-365/enterprise/microsoft-365-ip-web-service).

##### Microsoft Intune

Once authenticated, Microsoft Entra ID triggers enrollment of the device into the Intune mobile device management (MDM) service. For more information about Intune's network communication requirements, see [Network endpoints for Microsoft Intune](/en-us/intune/fundamentals/endpoints).

##### Windows Autopilot automatic device diagnostics collection

For diagnostics to be able to upload successfully from the client, make sure that the URL `lgmsapeweu.blob.core.windows.net` isn't blocked on the network. Diagnostics are available for 28 days before they're removed.

For more information, see [Collect diagnostics from a Windows device](/en-us/intune/device-management/actions/collect-diagnostics).

##### Windows Update

During the out-of-box experience (OOBE) process and after the Windows OS configuration, the Windows Update service retrieves needed updates. If there are problems connecting to Windows Update, see [Windows Update issues troubleshooting](/en-us/troubleshoot/windows-client/installing-updates-features-roles/windows-update-issues-troubleshooting).

If Windows Update is inaccessible, the Windows Autopilot process still continues but critical updates aren't available.

##### Delivery Optimization

Windows Autopilot contacts the [Delivery Optimization](/en-us/windows/deployment/update/waas-delivery-optimization) service when downloading the applications and updates. This contact establishes peer-to-peer sharing of content so that only a few devices need to download it from the internet.

- Windows Updates.
- Microsoft Store applications and application updates.
- Office Updates.
- Intune Win32 Applications.

If the Delivery Optimization Service is inaccessible, the Windows Autopilot process still continues with Delivery Optimization downloads from the cloud without peer-to-peer.

##### Network Time Protocol (NTP) sync

When a Windows device starts up, it talks to a network time server to ensure that the time on the device is correct. Ensure that UDP port **123** to `time.windows.com` is accessible.

##### Domain Name Services (DNS)

To resolve internet names for all services, the device communicates with a DNS server, typically provided via DHCP. This DNS server must be able to resolve internet names.

##### Diagnostics data

Diagnostic data collection is enabled by default. For more information, see [Manage enterprise diagnostic data](/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization#manage-diagnostic-data-using-group-policy-and-mdm).

If the device can't send diagnostic data, the Windows Autopilot process still continues. However, services that depend on diagnostic data don't work.

##### Network Connection Status Indicator (NCSI)

Windows must be able to tell that the device can access the internet. For more information, see [Network Connection Status Indicator (NCSI)](/en-us/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services#14-network-connection-status-indicator).

`*.msftconnecttest.com` must be resolvable via DNS and accessible via HTTP.

##### Windows Notification Services (WNS)

This service is used to enable Windows to receive notifications from applications and services. For more information, see [Microsoft Store](/en-us/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services#26-microsoft-store).

If the WNS services aren't available, the Windows Autopilot process still continues without notifications.

##### Microsoft Store

Applications in the Microsoft Store can be pushed to the device by triggering them via Intune or other MDM service. App updates and additional applications might also be needed when the user first logs in. For more information, see [Update to Intune integration with the Microsoft Store on Windows](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/update-to-intune-integration-with-the-microsoft-store-on-windows/ba-p/3585077) and [FAQ: Supporting Microsoft Store experiences on managed devices](https://techcommunity.microsoft.com/t5/windows-management/faq-supporting-microsoft-store-experiences-on-managed-devices/m-p/3585286).

If the Microsoft Store isn't accessible, the Windows Autopilot process still continues without Microsoft Store apps.

##### Microsoft 365

As part of the Intune device configuration, installation of Microsoft 365 Applications for enterprise might be required. For a list that includes all Office services, DNS names, IP addresses, including Microsoft Entra ID and other services that might overlap with the previously listed services, see [Office 365 URLs and IP address ranges](/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges).

##### Certificate revocation lists (CRLs)

Some of these services also need to check certificate revocation lists (CRLs) for certificates used in the services. For a full list, see [Office 365 URLs and IP address ranges](/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges) and [Office 365 Certificate Chains](/en-us/microsoft-365/compliance/encryption-office-365-certificate-chains).

##### Microsoft Entra hybrid join

Important

Microsoft recommends deploying new devices as cloud-native using Microsoft Entra join. Deploying new devices as Microsoft Entra hybrid join devices isn't recommended, including through Windows Autopilot. For more information, see [Microsoft Entra joined vs. Microsoft Entra hybrid joined in cloud-native endpoints: Which option is right for your organization](/en-us/intune/solutions/cloud-native-endpoints/azure-ad-joined-hybrid-azure-ad-joined#which-option-is-right-for-your-organization).

The device can be Microsoft Entra hybrid joined. The computer should be on the internal network for Microsoft Entra hybrid join to work. For more information, see [Windows Autopilot user-driven mode](user-driven#user-driven-mode-for-microsoft-entra-hybrid-join).

##### Windows Autopilot self-deploying mode and Windows Autopilot pre-provisioning

The TPM attestation process requires access to a set of HTTPS URLs, which are unique for each TPM provider. Ensure access to this URL pattern: `*.microsoftaik.azure.net`.

Firmware TPM devices, which are only provided by Intel, AMD, or Qualcomm, don't include all needed certificates at boot time and must be able to retrieve them from the manufacturer on first use. Devices with discrete TPM chips come with these certificates preinstalled. These devices include ones from any other manufacturer. For more information, see [TPM recommendations](/en-us/windows/security/information-protection/tpm/tpm-recommendations).

For each firmware TPM provider, make sure that the appropriate URL is accessible so that certificates can be successfully requested. For example:

- Intel: `https://ekop.intel.com/ekcertservice`
- Qualcomm: `https://ekcert.spserv.microsoft.com/EKCertificate/GetEKCertificate/v1`
- AMD: `https://ftpm.amd.com/pki/aia`

##### Proxy settings

Deploying proxy settings for Windows Autopilot should be configured on the proxy server itself. Implementing proxy settings via Intune policy isn't fully supported as it might cause issues and unexpected behavior with privileged access deployments.

# [Licensing](#tab/licensing)
### Licensing requirements

Windows Autopilot depends on specific capabilities available in Windows client and Microsoft Entra ID. It also requires a mobile device management (MDM) service such as Microsoft Intune. These capabilities can be obtained through various editions and subscription programs.

To provide needed Microsoft Entra ID and MDM functionality, including automatic MDM enrollment and company branding features, one of the following subscriptions is required:

- [Microsoft 365 Business Premium subscription](https://www.microsoft.com/microsoft-365/business).
- [Microsoft 365 F1 or F3 subscription](https://www.microsoft.com/microsoft-365/enterprise/firstline).
- [Microsoft 365 Academic A1, A3, or A5 subscription](https://www.microsoft.com/education/products/microsoft-365).
- [Microsoft 365 Enterprise E3 or E5 subscription](https://www.microsoft.com/microsoft-365/enterprise), which include all Windows client, Microsoft 365, and EMS features (Microsoft Entra ID and Intune).
- [Enterprise Mobility + Security E3 or E5 subscription]([https://www.microsoft.com/cloud-platform/enterprise-mobility-security](https://www.microsoft.com/licensing/product-licensing/enterprise-mobility-security), which include all needed Microsoft Entra ID and Intune features.
- [Intune for Education subscription](/en-us/intune-education/what-is-intune-for-education), which include all needed Microsoft Entra ID and Intune features.
- [Microsoft Entra ID P1 or P2](https://azure.microsoft.com/services/active-directory/) and [Microsoft Intune subscription](https://www.microsoft.com/security/business/microsoft-intune-pricing) or an alternative MDM service.

Note

When a Microsoft 365 subscription is used, licenses still need to be assigned to users so they can enroll device in Intune. For more information, see [assign licenses to users so they can enroll devices in Intune](/en-us/intune/fundamentals/assign-licenses).

Additionally, the following are also recommended (but not required):

- [Microsoft 365 Apps for enterprise](https://www.microsoft.com/microsoft-365/enterprise/microsoft-365-apps-for-enterprise-product) - Microsoft 365 Applications for enterprise can be deployed easily via Intune or other MDM service.
- [Windows Subscription Activation](/en-us/windows/deployment/windows-subscription-activation) - automatically step up devices from Windows Pro to Windows Enterprise edition.

# [Configuration](#tab/configuration)
### Configuration requirements

Before Windows Autopilot can be used, some configuration tasks are required to support the common Windows Autopilot scenarios.

- **Configure Microsoft Entra automatic enrollment**. For details when using Microsoft Intune, see [Set up Windows automatic Intune enrollment](tutorial/user-driven/azure-ad-join-automatic-enrollment) or [Enable Windows automatic enrollment](/en-us/intune/intune-service/enrollment/windows-enroll#enable-windows-automatic-enrollment). If using a different MDM service, contact the vendor for the specific URLs or configuration needed for those services.
- **The first user that signs in needs to have Microsoft Entra join permissions for some deployment scenarios**. For details, see [Allow users to join devices to Microsoft Entra ID](tutorial/user-driven/azure-ad-join-allow-users-to-join). The exception to this requirement is Windows Autopilot self-deployment mode since this method works in a userless context.

The following configurations are optional but recommended. They aren't required:

- **Automatically step up from Windows Pro to Windows Enterprise**. For more information, see [Windows Subscription Activation](/en-us/windows/deployment/windows-subscription-activation).
- **Configure Microsoft Entra custom branding**. To display an organization-specific sign-on page, configure Microsoft Entra ID with the images and text that need to be displayed. For more information, see [Quickstart: Add company branding to your sign-in page in Microsoft Entra ID](/en-us/azure/active-directory/fundamentals/customize-branding). Key elements for Windows Autopilot include the **square logo**, **sign-in page text**, and Microsoft Entra tenant name. The tenant name is configured separately in the Microsoft Entra tenant properties.

Specific scenarios have additional requirements. Generally, there are two specific tasks:

- **Device registration**. Devices must be added to Windows Autopilot to support most Windows Autopilot scenarios. For more information, see [Register devices as Windows Autopilot devices](tutorial/user-driven/azure-ad-join-register-device) or [Manually register devices with Windows Autopilot](add-devices).
- **Profile configuration**. Once devices are added to Windows Autopilot, a profile of settings needs to be applied to each device. For details see [Configure Windows Autopilot profiles](profiles). Microsoft Intune can automate this profile assignment. For more information, see [Create device groups for Windows Autopilot](enrollment-autopilot) and [Assignment of Windows Autopilot deployment profiles to devices](profiles#assignment-of-windows-autopilot-deployment-profiles-to-devices).

For more information, see [Windows Autopilot Scenarios](windows-autopilot-scenarios).

For a walkthrough for some of these and related steps, see this video:

There are no additional hardware requirements to use Windows Autopilot, beyond the hardware requirements to run Windows. For more information, see:

- [Find Windows 11 specs, features, and computer requirements](https://www.microsoft.com/windows/windows-11-specifications).
- [How to Find Windows 10 Computer Specifications & Systems Requirements](https://www.microsoft.com/windows/windows-10-specifications).
- [Windows minimum hardware requirements](/en-us/windows-hardware/design/minimum/minimum-hardware-requirements-overview).
- [Windows 11 requirements](/en-us/windows/whats-new/windows-11-requirements).

---