---
layout: Conceptual
title: Windows client prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn about the prerequisites for deploying the Configuration Manager client to Windows computers.
ms.date: 2024-03-28T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: a6282a3a-0ddd-6238-3705-955cc21dea00
document_version_independent_id: f2f05817-b035-8df3-aa6c-e490f4f0ddfe
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 021af542-af11-2edc-8c16-6690e5b7da51
---

# Windows client prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Deploying Configuration Manager clients in your environment has the following external dependencies and dependencies within the product. Additionally, each client deployment method has its own dependencies that must be met for client installations to be successful.

For more information on the minimum hardware and OS requirements for the Configuration Manager client, see [Supported configurations](../../plan-design/configs/supported-configurations).

Note

The software version numbers shown in this article only list the minimum version numbers required.

Use the following information to determine the prerequisites for when you install the Configuration Manager client on Windows devices.

## Dependencies external to Configuration Manager

### Windows components

Many of these components are services or features that Windows enables by default. Don't disable these components on Configuration Manager clients.

| Component | Description |
| --- | --- |
| Windows Installer | Required to support the use of Windows Installer files for applications and software updates. |
| Background Intelligent Transfer Service (BITS) | Required to allow throttled data transfers between the client computer and Configuration Manager site systems. |
| Task Scheduler | Required for client operations, such as regularly evaluating the health of the Configuration Manager client. |
| Remote Differential Compression (RDC) | Required to optimize data transmission over the network. |
| SHA-2 code signing support | Clients require support for the SHA-2 code signing algorithm. For more information, see SHA-2 code signing support. |

#### SHA-2 code signing support

Because of weaknesses in the SHA-1 algorithm and to align to industry standards, Microsoft now only signs Configuration Manager binaries using the more secure SHA-2 algorithm. Legacy Windows OS versions require an update for SHA-2 code signing support. For more information, see [2019 SHA-2 code signing support requirement for Windows and WSUS](https://support.microsoft.com/topic/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus-64d1c82d-31ee-c273-3930-69a4cde8e64f).

If you don't update these OS versions, you can't install a supported version of the Configuration Manager current branch client. This behavior applies to either a new client install or updating it from a previous version.

If you need to manage a client on a version of Windows that's not updated, or older than the versions listed above, use the Configuration Manager extended interoperability client (EIC) version 1902. For more information, see [Extended interoperability client](../../understand/interoperability-client).

Tip

If you don't use [automatic client update](../manage/upgrade/upgrade-clients-for-windows-computers#bkmk_autoupdate), and update clients with another mechanism, make sure to update the version of ccmsetup. An older version of ccmsetup may not properly validate the new SHA-2 code signing certificate on client binaries. For example, if you copy ccmsetup.exe to a file share, or use ccmsetup.msi with group policy.

The following client update mechanisms aren't affected:

- Client push installation: It uses the client package from the site.
- Software update-based installation: The site update republishes to WSUS.
- Intune MDM-managed Windows devices: The supported version for this mechanism already supports SHA-2 code signing, but it's still important to use the latest ccmsetup.msi.

### Components automatically downloaded during installation

The Configuration Manager client has external dependencies. These dependencies depend on the OS version and the installed software on the client computer. If the client requires these dependencies to complete the installation, it automatically installs them.

| Component | Description |
| --- | --- |
| Microsoft Visual C++ 2015-2019 Redistributable version 14.28.29914.0 (`vcredist_x*.exe`) | (*Version 2107 and later*) Required to support client operations. When you install this update on client computers, it might require a restart to complete the installation. |
| Microsoft Visual C++ 2013 Redistributable version 12.0.40660.0 (`vcredist_x*.exe`) | (*Version 2103 and earlier*) Required to support client operations. When you install this update on client computers, it might require a restart to complete the installation. |
| Windows Imaging APIs 6.0.6001.18000 or later (`wimgapi.msi`) | Required to allow Configuration Manager to manage Windows image (.wim) files. |
| Microsoft Policy Platform 1.2.3514.0 or later (`MicrosoftPolicyPlatformSetup.msi`) | Required to allow clients to evaluate compliance settings. |
| Microsoft .NET Framework version 4.6.2 or later (`NDP462-KB3151800-x86-x64-AllOS-ENU.exe`) | *Version 2107 and later*: Required to support client operations. Automatically installed on the computer if it doesn't have this version installed. For more information, see More details about Microsoft .NET. |
| Microsoft .NET Framework version 4.5.2 or later (`NDP452-KB2901907-x86-x64-AllOS-ENU.exe`) | *Version 2103 and earlier*: Required to support client operations. Automatically installed on the computer if it doesn't have this version installed. For more information, see More details about Microsoft .NET. |
| Microsoft .NET Framework version 3.5 (`dotNetFx35setup.exe`) | *Version 2309 and later*: Required to support arm64 software update deployment. Install on the computer if it doesn't have this version installed. For more information, see More details about Microsoft .NET. |
| Microsoft Monitoring Agent version 10.20.18053.0 (`MMASetup-*.exe`) | Installed as needed by devices that you onboard to Microsoft Defender for Endpoint. |
| Windows Firewall configuration (`WindowsFirewallConfigurationProvider.msi`) | Required for certain endpoint protection policies. |
| Microsoft WebView2 (`Microsoft.WebView2.FixedVersionRuntime.x86.cab`) | Installed as needed when you use Software Center custom tabs. |

Note

Starting in version 2107, the Configuration Manager client no longer has an external dependency on Microsoft SQL Server Compact Edition (CE) 4.0 SP1. It now uses a built-in version of this component to store information related to client operations.

#### More details about Microsoft .NET

When you install or update the Configuration Manager client, if the device doesn't have at least the required version of the .NET Framework, CCMSetup installs it. Starting in version 2107, the minimum required version is 4.6.2.

Microsoft recommends that you install the latest version of .NET version 4.8 to get the latest performance and security improvements. CCMSetup doesn't automatically install .NET version 4.8. A later version of Configuration Manager will require .NET version 4.8.

Note

.NET Framework version 4.6.2 is preinstalled with Windows Server 2016 and Windows 10 version 1607. Later versions of Windows are preinstalled with a later version of the .NET Framework.

.NET Framework version 4.8 isn't supported on some OS versions, such as Windows 10 2015 LTSB.

.Net Framework version 3.5 isn't installed on arm64 versions.

For more information, see [.NET Framework system requirements](/en-us/dotnet/framework/get-started/system-requirements).

Whether you update .NET before updating the Configuration Manager client, or CCMSetup updates it, .NET may require a restart to complete its installation. CCMSetup suppresses a restart if necessary. The user sees a **Restart required** notice in the Windows notification area.

Important

When the Configuration Manager client updates to version 2111 or later, client notifications are dependent upon .NET 4.6.2 or later. Until you update .NET to version 4.6.2 or later, and restart the device, users won't see notifications from Configuration Manager. Other client-side functionality may be affected until the device is updated and restarted.

The following scenarios are common reasons why .NET requires the computer to restart:

- .NET applications or services are running on the computer.
- One or more software updates required for .NET installation are missing.
- The computer is pending a restart from prior installation of .NET framework software updates.

After .NET Framework is installed, it may require other updates. These updates may also require the computer to restart.

If you need to manage the device restarts before you update the Configuration Manager client, use the following recommended process:

1. Install the latest baseline .NET version. For example, starting in version 2107, install .NET version 4.8.
2. Restart the device.
3. Scan for software updates and install the latest .NET cumulative update.
4. Restart the device.
5. Install the latest Configuration Manager client version.

##### Known issue with .NET version 4.6.2 on Windows Server 2008 SP2

The release of .NET version 4.6.2 that Configuration Manager redistributes doesn't install on Windows Server 2008 SP2. This version of the OS is covered under the [Extended Security Updates](../../plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_ESU) (ESU) program. While products under this program are no longer supported for use with Configuration Manager, you can use the *latest released version of Configuration Manager current branch* to deploy and install Windows security updates released under the ESU program.

Microsoft recommends updating the OS to a later version that's fully supported. If your business requirements necessitate use of this OS version, download the latest release of .NET version 4.6.2 published on 6/23/2021 or later. For more information, see [The .NET Framework 4.6.2 offline installer for Windows](https://support.microsoft.com/topic/the-net-framework-4-6-2-offline-installer-for-windows-9dce3874-a9e5-9b11-289d-5594824aafe0). This .NET release does install on Server 2008 SP2. Manually update .NET on devices with this OS version before you update the Configuration Manager client to version 2107.

## Configuration Manager dependencies

For more information, see [Determine the site system roles for clients](plan/determine-the-site-system-roles-for-clients).

| Component | Description |
| --- | --- |
| Management point | To deploy the Configuration Manager client, you don't require a management point. Clients require a management point to transfer information with the site. Without a management point, you can't manage client computers. |
| Distribution point | The distribution point is an optional, but recommended site system role for client deployment and management. All distribution points host the client source files. Clients find the nearest distribution point from which to download the source files during client deployment or update. If the site doesn't have a distribution point, computers download the client source files from their management point. |
| Fallback status point | The fallback status point is an optional, but recommended site system role for client deployment. The fallback status point tracks client deployment and enables computers in the Configuration Manager site to send state messages when they can't communicate with a management point. |
| Reporting services point | The reporting services point is an optional, but recommended site system role. It displays reports related to client deployment and management. For more information, see [Introduction to reporting](../../servers/manage/introduction-to-reporting). |

## Installation method dependencies

The following prerequisites are specific to the various [methods of client installation](plan/client-installation-methods).

### Client push installation

- The site uses client push installation accounts to connect to computers to install the client. Specify these accounts on the **Accounts** tab of the Client Push Installation Properties. The account must be a member of the local Administrators group on the destination computer.

    If you don't specify a client push installation account, the site server uses its computer account.
- The site needs to discover the computer on which you're installing the client. At least one Configuration Manager discovery method is needed.
- The computer has an ADMIN$ share.
- To automatically push the Configuration Manager client to discovered resources, select the option to **Enable client push installation to assigned resources** in the Client Push Installation Properties.
- The client computer needs to communicate with a distribution point or a management point to download the source files.
- When you require Kerberos mutual authentication, clients must be in a trusted Active Directory forest. Kerberos in Windows relies upon Active Directory for mutual authentication.

To use client push, you need the following security permissions:

- To configure the client push installation account: **Modify** and **Read** permission for the **Site** object.
- To use client push to install the client to collections, devices and queries: **Modify Resource** and **Read** permission for the **Collection** object.

The **Infrastructure Administrator** default security role includes the required permissions to manage client push installations.

### Software update point-based installation

- If you haven't extended the Active Directory schema, or you're installing clients from another forest, use group policy to provision installation parameters for CCMSetup.exe. For more information, see [How to provision client installation properties](deploy-clients-to-windows-computers#BKMK_Provision).
- Publish the Configuration Manager client to the software update point.
- To download the source files, the client computer needs to communicate with a distribution point or a management point.

For the security permissions required to manage Configuration Manager software updates, see [Prerequisites for software updates](../../../sum/plan-design/prerequisites-for-software-updates).

### Group policy-based installation

- If you haven't extended the Active Directory schema, or you're installing clients from another forest, use group policy to provision installation parameters for CCMSetup.exe. For more information, see [How to provision client installation properties](deploy-clients-to-windows-computers#BKMK_Provision).
- To download the source files, the client computer needs to communicate with a distribution point or a management point.

### Logon script-based installation

To download the source files, the client computer needs to communicate with a distribution point or a management point. Unless you specified CCMSetup.exe with the following command-line parameter: `ccmsetup /source`

### Manual installation

To download the source files, the client computer needs to communicate with a distribution point or a management point. Unless you specified CCMSetup.exe with the following command-line parameter: `ccmsetup /source`

### Microsoft Intune MDM installation

- Requires a Microsoft Intune subscription and appropriate licenses.
- Requires the device has internet access, even if it isn't internet-based.
- Depending upon the use case, you may also require one or both of the following technologies:

    - Microsoft Entra ID
    - Cloud management gateway

### Workgroup computer installation

To access resources in the Configuration Manager site server's domain, configure a network access account for the site.

For more information about how to configure the network access account, see the [Fundamental concepts for content management](../../plan-design/hierarchy/fundamental-concepts-for-content-management).

### Software distribution-based installation (for upgrades only)

- If you haven't extended the Active Directory schema, or you're installing clients from another forest, use group policy to provision installation parameters for CCMSetup.exe. For more information, see [How to provision client installation properties](deploy-clients-to-windows-computers#BKMK_Provision).
- To download the source files, the client computer needs to communicate with a distribution point or a management point.

For the security permissions required to upgrade the Configuration Manager client using application management, see [Security and privacy for application management](../../../apps/plan-design/security-and-privacy-for-application-management).

### Automatic client upgrades

You must be a member of the **Full Administrator** security role to configure automatic client upgrades.

## Firewall requirements

If there's a firewall between the site system servers and the computers onto which you want to install the Configuration Manager client, see [Windows Firewall and port settings for clients](windows-firewall-and-port-settings-for-clients).