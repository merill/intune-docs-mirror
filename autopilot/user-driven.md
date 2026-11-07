---
layout: Conceptual
title: Windows Autopilot User-Driven Mode | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/user-driven
author: iceorbital
ms.author: acabello
ms.reviewer: madakeva
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: With Windows Autopilot user-driven mode, devices can be configured to deploy to a ready-to-use state without requiring help from IT personnel.
ms.date: 2026-10-28T00:00:00.0000000Z
ms.collection: M365-modern-desktop
ms.topic: how-to
locale: en-us
document_id: 01620937-fd7d-5214-5a2b-5173f3183e88
document_version_independent_id: 01620937-fd7d-5214-5a2b-5173f3183e88
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/user-driven.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-driven
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/user-driven.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 2427bbe9-52ae-9d30-a92d-14e7ad133f80
---

# Windows Autopilot User-Driven Mode | Microsoft Learn

Windows Autopilot user-driven mode configures a new Windows device and transforms it from its factory state to a ready-to-use state. IT personnel don't need to touch the device.

The process is simple. Ship or distribute devices to the end user with the following instructions:

1. Unbox the device, plug it in, and turn it on.
2. If the device uses multiple languages, select a language, locale, and keyboard.
3. Connect the device to a wireless or wired network with internet access. If using wireless, first connect to the Wi-Fi network.
4. Specify an email address account and password for the organization.

The rest of the process is automated. The device completes the following steps:

1. Join the organization.
2. Enroll in Microsoft Intune or another mobile device management (MDM) service.
3. Get configured as defined by the organization.

You can suppress other prompts during the out-of-box experience (OOBE). For more information about the available options, see [Configure Windows Autopilot profiles](profiles).

Important

If you use Active Directory Federation Services (ADFS), a [known issue](known-issues#a-non-assigned-user-can-sign-in-when-using-user-driven-mode-with-active-directory-federation-services-adfs) can enable the end user to sign in with a different account than the one assigned to that device.

Windows Autopilot user-driven mode supports Microsoft Entra join and Microsoft Entra hybrid joined devices. For more information about these two join options, see the following articles:

- [What is a device identity?](/en-us/azure/active-directory/devices/overview)
- [Learn more about cloud-native endpoints](/en-us/intune/solutions/cloud-native-endpoints/cloud-native-endpoints-overview)
- [Microsoft Entra joined vs. Microsoft Entra hybrid joined in cloud-native endpoints](/en-us/intune/solutions/cloud-native-endpoints/azure-ad-joined-hybrid-azure-ad-joined)
- [Tutorial: Set up and configure a cloud-native Windows endpoint with Microsoft Intune](/en-us/intune/solutions/cloud-native-endpoints/cloud-native-windows-endpoints)
- [How to: Plan your Microsoft Entra join implementation](/en-us/azure/active-directory/devices/device-join-plan)
- [A framework for Windows endpoint management transformation](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/a-framework-for-windows-endpoint-management-transformation/ba-p/2460684)
- [Success with remote Windows Autopilot and Microsoft Entra hybrid join](https://techcommunity.microsoft.com/t5/intune-customer-success/success-with-remote-windows-autopilot-and-hybrid-azure-active/ba-p/2749353)

The steps of the user-driven process are as follows:

1. After the device connects to a network, it downloads a Windows Autopilot profile. The profile defines the settings used for the device. For example, it defines the prompts suppressed during OOBE.
2. Windows checks for critical OOBE updates. If updates are available, Windows installs them. If necessary, the device restarts.
3. The user is prompted for Microsoft Entra credentials. This customized user experience shows the Microsoft Entra tenant name, logo, and sign-in text.
4. The device joins Microsoft Entra ID or Active Directory, depending on the Windows Autopilot profile settings.
5. The device enrolls to Intune or another configured MDM service. Depending on the organizational needs, this enrollment occurs either:

    - During the Microsoft Entra join process, using MDM auto-enrollment.
    - Before the Active Directory-join process.
6. If configured, it displays the [enrollment status page](enrollment-status) (ESP).
7. After the device configuration tasks complete, the user is signed in to Windows by using the credentials they previously provided. If the device restarts during the device ESP process, the user must reenter their credentials. These details don't persist after restart.
8. After sign-in, the enrollment status page displays for user-targeted configuration tasks.

If any issues occur, see [Troubleshooting Windows Autopilot overview](troubleshooting-faq#troubleshooting-windows-autopilot-overview).

For more information about the available join options, see the following sections:

- Microsoft Entra join is available if devices don't need to join an on-premises Active Directory domain.
- Microsoft Entra hybrid join is available for devices that need to join both Microsoft Entra ID and the on-premises Active Directory domain.

## User-driven mode for Microsoft Entra join

To complete a user-driven deployment by using Windows Autopilot, follow these preparation steps:

1. Ensure that the users performing user-driven mode deployments can join devices to Microsoft Entra ID. For more information, see [Configure device settings](/en-us/azure/active-directory/devices/device-management-azure-portal#configure-device-settings) in the Microsoft Entra documentation.
2. Create a Windows Autopilot profile for user-driven mode with the desired settings.

    - In Intune, explicitly choose this mode when you create a profile.
    - In Microsoft Store for Business and Partner Center, user-driven mode is the default.
3. If you're using Intune, create a device group in Microsoft Entra ID, and assign the Windows Autopilot profile to that group.

For each device that you deploy by using user-driven deployment, follow these extra steps:

- Add the device to Windows Autopilot. You can complete this step in two ways:

    - Automatically by a hardware manufacturer or partner when you purchase the device.
    - Manually as described in [Manually register devices with Windows Autopilot](add-devices).
- Assign a Windows Autopilot profile to the device:

    - If you use Intune and Microsoft Entra dynamic device groups, this assignment can be done automatically.
    - If you use Intune and Microsoft Entra static device groups, manually add the device to the device group.
    - If you use other methods, like Microsoft Store for Business or Partner Center, manually assign a Windows Autopilot profile to the device.

Tip

If the intended end state of the device is co-management, configure device enrollment in Intune to enable co-management. This configuration happens during the Windows Autopilot process. This behavior directs the workload authority in an orchestrated manner between Configuration Manager and Intune. For more information, see [How to enroll with Windows Autopilot](/en-us/intune/configmgr/comanage/autopilot-enrollment).

## User-driven mode for Microsoft Entra hybrid join

Important

We recommend you deploy new devices as cloud-native using Microsoft Entra join. We don't recommend deploying new devices as Microsoft Entra hybrid join devices, including through Windows Autopilot. For more information, see [Microsoft Entra joined vs. Microsoft Entra hybrid joined in cloud-native endpoints: Which option is right for your organization](/en-us/intune/solutions/cloud-native-endpoints/azure-ad-joined-hybrid-azure-ad-joined#which-option-is-right-for-your-organization).

Windows Autopilot requires that devices be Microsoft Entra joined. For an on-premises Active Directory environment, devices can be joined to the on-premises domain. To join the devices, configure Windows Autopilot devices to be [hybrid-joined to Microsoft Entra ID](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan).

Tip

As we talk with customers who use Microsoft Intune and Microsoft Configuration Manager to deploy, manage, and secure their client devices, we often get questions regarding co-managing devices and Microsoft Entra hybrid joined devices. Many customers confuse these two topics. *Co-management* is a management option, while Microsoft Entra ID is an identity option. For more information, see [Understanding hybrid Microsoft Entra and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201). This blog post aims to clarify Microsoft Entra hybrid join and co-management, how they work together, but aren't the same thing.

You can't deploy the Configuration Manager client while provisioning a new computer in Windows Autopilot user-driven mode for Microsoft Entra hybrid join. This limitation is due to the identity change of the device during the Microsoft Entra join process. Deploy the Configuration Manager client after the Windows Autopilot process. See [Client installation methods in Configuration Manager](/en-us/intune/configmgr/core/clients/deploy/plan/client-installation-methods) for alternative options for installing the client.

### Requirements for user-driven mode with hybrid Microsoft Entra ID

- Create a Windows Autopilot profile for user-driven mode.

    In the Windows Autopilot profile, under **Join to Microsoft Entra ID as**, select **Microsoft Entra hybrid joined**.
- If you use Intune, create a device group in Microsoft Entra ID. Assign the Windows Autopilot profile to the group.
- If you use Intune, create and assign a Domain Join profile. A Domain Join configuration profile includes on-premises Active Directory domain information.
- The device needs internet access. For more information, see the [networking requirements](requirements?tabs=networking).
- Install the Intune Connector for Active Directory.

    Note

    The Intune Connector for Active Directory joins the device to the on-premises domain. Users don't need permissions to join devices to the on-premises domain. This behavior assumes that the connector is configured for this action on the user's behalf. For more information, see [Increase the computer account limit in the Organizational Unit (OU)](windows-autopilot-hybrid#increase-the-computer-account-limit-in-the-organizational-unit).
- If you use a proxy, enable and configure the Web Proxy Auto-Discovery Protocol (WPAD) Proxy settings option.

In addition to these core requirements for user-driven Microsoft Entra hybrid join, the following requirements apply to on-premises devices:

- The device has a currently supported version of Windows.
- The device is connected to the internal network and has access to an Active Directory domain controller.

    - It needs to resolve the DNS records for the domain and the domain controllers.
    - It needs to communicate with the domain controller to authenticate the user.

### User-driven mode for Microsoft Entra hybrid join with VPN support

Devices joined to Active Directory need connectivity to an Active Directory domain controller for many activities. These activities include validating the user's credentials when they sign in and applying group policy settings. The Windows Autopilot user-driven process for Microsoft Entra hybrid joined devices checks that the device can contact a domain controller by pinging that domain controller.

By adding VPN support for this scenario, you can configure the Microsoft Entra hybrid join process to skip the connectivity check. This change doesn't eliminate the need for communicating with a domain controller. Instead, Intune delivers the needed VPN configuration to allow connection to the organization's network before the user attempts to sign in to Windows.

#### Requirements for user-driven mode with hybrid Microsoft Entra ID and VPN

In addition to the core requirements for user-driven mode with Microsoft Entra hybrid join, the following extra requirements apply to a remote scenario with VPN support:

- A currently supported version of Windows.
- In the Microsoft Entra hybrid join profile for Windows Autopilot, enable the following option: **Skip domain connectivity check**.
- A VPN configuration with one of the following options:

    - Can be deployed with Intune, and lets the user manually establish a VPN connection from the Windows sign-in screen.
    - Automatically establishes a VPN connection as needed.

The specific VPN configuration you need depends on the VPN software and authentication you use. For non-Microsoft VPN solutions, this configuration typically involves deploying a Win32 app by using Intune Management Extensions. This app includes the VPN client software and any specific connection information, such as VPN endpoint host names. For configuration details specific to that provider, see the VPN provider's documentation.

Note

The VPN requirements aren't specific to Windows Autopilot. For example, if you implement a VPN configuration to enable remote password resets, you can use that same configuration with Windows Autopilot. This configuration allows a user to sign in to Windows with a new password when not on the organization's network. After the user signs in and their credentials are cached, subsequent sign-in attempts don't need connectivity since Windows uses the cached credentials.

If the VPN software requires certificate authentication, use Intune to also deploy the required device certificate. You can deploy this certificate by using Intune certificate enrollment capabilities and targeting the certificate profiles to the device.

Some configurations aren't supported because they don't apply until the user signs in to Windows:

- User certificates
- Non-Microsoft UWP VPN plug-ins from the Windows Store

#### Validation

Before you attempt a Microsoft Entra hybrid join by using VPN, confirm that the user-driven mode for Microsoft Entra hybrid join process works on the internal network. This test simplifies troubleshooting by ensuring the core process works before adding the VPN configuration.

Next, confirm you can use Intune to deploy the VPN configuration and its requirements. Test these components with an existing device that's already Microsoft Entra hybrid joined. For example, some VPN clients create a per-machine VPN connection as part of the installation process. Validate the configuration by using the following steps:

1. Verify that you create at least one per-machine VPN connection.

    ```powershell
    Get-VpnConnection -AllUserConnection
    ```
2. Attempt to manually start the VPN connection.

    ```cmd
    RASDIAL.EXE "ConnectionName"
    ```
3. Sign out of Windows. Verify that the **VPN connection** icon appears on the Windows sign-in page.
4. Move the device off the internal network and try to establish the connection by using the icon on the Windows sign-in page. Sign in to an account that doesn't have cached credentials.

For VPN configurations that automatically connect, the validation steps might be different.

Note

You can use an always-on VPN for this scenario. For more information, see [Deploy always-on VPN](/en-us/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy-deployment).