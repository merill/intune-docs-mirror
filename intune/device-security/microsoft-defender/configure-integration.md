---
layout: Conceptual
title: Configure Microsoft Defender for Endpoint with Intune and onboard devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/configure-integration
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.reviewer: laarrizz
ms.subservice: protect
description: Connect Microsoft Defender for Endpoint to Intune, onboard devices by platform, and configure compliance and Conditional Access policies that use device risk levels to control access to corporate resources.
ms.date: 2026-05-26T00:00:00.0000000Z
ms.topic: how-to
ai.usage: ai-assisted
locale: en-us
document_id: e1039679-f537-dea6-04a3-3927eb84d158
document_version_independent_id: e1039679-f537-dea6-04a3-3927eb84d158
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/microsoft-defender/configure-integration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/microsoft-defender/configure-integration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/microsoft-defender/configure-integration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 9fe4f6c2-e80c-d97c-1833-ac9b3734dd75
---

# Configure Microsoft Defender for Endpoint with Intune and onboard devices - Microsoft Intune | Microsoft Learn

This article provides step-by-step instructions to connect Microsoft Defender for Endpoint to Microsoft Intune, onboard devices to Defender for Endpoint by platform, and configure compliance and Conditional Access policies that use device risk levels to control access to corporate resources.

Task-specific requirements are listed throughout this article. Also review [general integration prerequisites](overview#prerequisites).

## What you'll accomplish

After completing this guide, you'll have completed the following integration workflows:

✅ **Service-to-service connection** between Intune and Microsoft Defender for Endpoint ✅ **Devices onboarded** to Microsoft Defender for Endpoint (Windows, macOS, Android, iOS/iPadOS) ✅ **Compliance policies** configured to automatically mark risky devices as noncompliant ✅ **Conditional Access policies** that block noncompliant devices from corporate resources

## Quick navigation

- Connect services
- Configure integration settings
- Onboard devices
- Configure compliance policies
- Configure app protection policies
- Set up Conditional Access

**For mobile environments:** This guide also covers [app protection policies](../mobile-threat-defense/create-app-protection-policy) for Android and iOS/iPadOS devices. These policies set device risk levels and work with both enrolled and unenrolled devices, providing additional protection for mobile apps based on Microsoft Defender for Endpoint threat assessments.

**Additional capabilities:** Beyond enrolled devices, you can also manage Defender for Endpoint security configurations on devices that aren't enrolled with Intune (including Linux devices). This scenario is called *Security Management for Microsoft Defender for Endpoint*. To enable this, set the *Allow Microsoft Defender for Endpoint to enforce Endpoint Security Configurations* toggle to *On*. For details, see [Microsoft Defender for Endpoint Security Configuration Management](security-settings-management).

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Connect Defender for Endpoint to Intune

Complete this one-time setup per tenant to create the service-to-service connection that enables integration features.

**Prerequisites:**

- Admin access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the **Endpoint Security Manager** role or equivalent permissions for *Mobile Threat Defense* settings. Custom roles require *Read* and *Modify* rights for the *Mobile Threat Defense* permission. For more information, see [Create a custom role](../../fundamentals/role-based-access-control/create-custom-role).
- Admin access to the [Microsoft Defender portal](https://security.microsoft.com) with the [Security Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) role in Microsoft Entra ID, or **Manage security settings in Windows Security Center** permission in Defender for Endpoint.

### Enable Intune and Defender for Endpoint integration

1. **Check connection status first:** Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select **Endpoint security** &gt; **Defender for Endpoint**.

    - If **Connection status** shows **Enabled**, the services are already connected. Skip to Onboard devices.
    - If **Connection status** shows **Unavailable**, continue with the next step.
2. **Open the Microsoft Defender portal:** From the Intune admin center, scroll to the bottom of the *Defender for Endpoint* page and select **Open the Defender Security Center** (or navigate directly to https://security.microsoft.com).

    Tip

    If already connected, the link reads: **Open the Defender for Endpoint admin console**.

    ![Screen shot that shows the patch to open the Microsoft Defender Security Center.](media/configure-integration/open-microsoft-defender.png)
3. **Enable the connection in Defender portal:** In the [Microsoft Defender portal](https://security.microsoft.com), go to **System** &gt; **Settings** &gt; **Endpoints** &gt; **General** &gt; **Advanced features**.

    ![Screen shot of the Defender console showing the path to Settings and then Endpoints.](media/configure-integration/defender-console-settings-endpoints.png)

    Locate **Intune connection**, toggle it to **On**, and then select **Save preferences**.

    ![Screen shot of the Microsoft Intune connection setting.](media/configure-integration/intune-connection-toggle.png)

    For more information about this setting, see [Microsoft Intune connection](/en-us/defender-endpoint/advanced-features#microsoft-intune-connection) in the Defender for Endpoint documentation.
4. **Validation:** Return to the Intune admin center. The **Connection status** should now show **Enabled** (it can take up to 15 minutes to update). You can review and adjust monitoring settings under **Endpoint security** &gt; **Defender for Endpoint** if needed.

The service-to-service connection is now established. Continue to configure which platforms and features use this integration.

## Configure integration settings

After you create the service connection, configure which platforms connect to Defender for Endpoint for compliance and app protection policy evaluation.

**Prerequisites:** Admin access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the **Endpoint Security Manager** role or equivalent permissions for *Mobile Threat Defense* settings. Custom roles require *Read* and *Modify* rights for the *Mobile Threat Defense* permission. For more information, see [Create a custom role](../../fundamentals/role-based-access-control/create-custom-role).

### Configure compliance and app protection settings

1. **Go to integration settings:** In the Intune admin center, go to **Endpoint security** &gt; Defender for Endpoint. The Connection status should now show **Enabled**.
2. **Configure compliance policy evaluation:** Enable these options under **Compliance policy evaluation** for your supported platforms:

    - **Connect Android devices to Defender for Endpoint**: **On**
    - **Connect iOS/iPadOS devices to Defender for Endpoint**: **On**
    - **Connect Windows devices to Defender for Endpoint**: **On**

    Note

    When you enable these settings, all applicable devices you currently manage with Intune, plus future enrollments, connect to Defender for Endpoint for compliance evaluation.

    Tip

    **Additional iOS settings:** For iOS devices, Defender for Endpoint also supports settings that help provide Vulnerability Assessment of apps. You can enable **App Sync for iOS Devices** to allow metadata sharing for threat analysis (requires MDM enrollment), and configure **Send full application inventory data on personally owned iOS/iPadOS Devices** to control what app data is shared with Defender for Endpoint. For details, see [Configure vulnerability assessment of apps](/en-us/defender-endpoint/ios-configure-features#configure-vulnerability-assessment-of-apps).

    For more information, see [Mobile Threat Defense toggle options](../mobile-threat-defense/enable-connector#mobile-threat-defense-toggle-options).
3. **Configure app protection policy evaluation:** Enable these options under **App protection policy evaluation** for mobile platforms:

    - **Connect Android devices to Defender for Endpoint**: **On**
    - **Connect iOS/iPadOS devices to Defender for Endpoint**: **On**

    Tip

    App protection policies work with both enrolled and unenrolled devices. For details, see [Mobile Threat Defense toggle options](../mobile-threat-defense/enable-connector#mobile-threat-defense-toggle-options).
4. **Configure Mobile Threat Defense role (Android):** Under **Mobile Threat Defense role**, you can optionally grant Defender for Endpoint enhanced security permissions on enrolled Android Enterprise corporate-owned fully managed and corporate-owned work profile devices. You can also enable automatic launch of Defender for Endpoint during device setup on these devices. For details about these toggles and the permissions they grant, see [Mobile Threat Defense role](../mobile-threat-defense/enable-connector#mobile-threat-defense-role).
5. **Save your configuration:** Select **Save** to apply all settings.

The platforms you enabled connect devices to Defender for Endpoint for threat assessment and compliance evaluation.

Important

**Classic Conditional Access cleanup:** As of August 2023, Intune no longer creates classic Conditional Access policies for Defender for Endpoint. If your tenant has legacy policies from previous integrations, you can safely delete them. To check: **Azure portal** &gt; **Entra ID** &gt; **Conditional Access** &gt; **Classic policies**.

## Onboard devices

Device onboarding configures your managed devices to communicate with Defender for Endpoint, enabling threat detection and risk assessment.

**Prerequisites:** Admin access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with **Endpoint Security Manager** role or equivalent permissions for *Endpoint detection and response* policies (custom roles require *Assign*, *Create*, *Delete*, *Read*, *Update*, and *View Reports* rights for the *Endpoint Detection and Response* permission).

Tip

**Version requirement:** Always use the latest Defender for Endpoint version for each platform to ensure optimal protection and compatibility.

**Platform-specific onboarding:**

- **Windows**: Automatic onboarding package (recommended)
- **macOS, Android, iOS/iPadOS**: Manual configuration required

### Onboard Windows devices

When you establish the service connection, Intune automatically receives an onboarding configuration package from Microsoft Defender for Endpoint. This package enables:

- Communication with [Microsoft Defender for Endpoint services](/en-us/defender-endpoint/microsoft-defender-endpoint)
- File scanning and threat detection
- Risk level reporting for compliance policies

Note

Device onboarding is a one-time action per device.

**Choose your deployment approach:**

- **Quick setup**: Preconfigured policy (deploys to all devices)
- **Custom setup**: Manual policy creation (granular control)

#### Option 1: Quick setup (preconfigured policy)

Use this option for fast, broad deployment to all Windows devices with no extra configuration.

**What's included:**

- Automatic onboarding package configuration
- Default scope tag
- Assignment to *All Devices* group
- No extra configuration required

##### Quick setup steps

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Endpoint security** &gt; **Endpoint detection and response** &gt; **EDR Onboarding Status** tab.
2. Select **Deploy preconfigured policy**.

    ![Screen shot that displays the path to the preconfigured policy option.](media/configure-integration/select-preconfigured-policy.jpg)
3. Configure the policy:

    - **Platform**: Select **Windows** (for Intune-managed) or **Windows (ConfigMgr)** (for Tenant Attach)
    - **Profile**: Select **Endpoint detection and response**
    - **Name**: Enter a descriptive name (for example, "MDE EDR Onboarding - All Windows Devices")
4. **Review and create**: Verify settings and select **Save**. The policy immediately starts deploying to all Windows devices.

    Note

    You can edit policy details later, but you can't change initial deployment settings during creation.

#### Option 2: Custom setup (manual policy creation)

Use this option for granular control, specific device groups, or custom scope tags.

##### Custom setup steps

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Endpoint security** &gt; **Endpoint detection and response** &gt; **Summary** tab &gt; **Create Policy**.
2. **Platform and profile:**

    - **Platform**: **Windows**
    - **Profile**: **Endpoint detection and response**
    - Select **Create**
3. **Basics:** Enter a descriptive name and optional description, and then select **Next**.
4. **Configuration settings:** Configure these options based on your requirements:

    - **Defender for Endpoint client configuration package type**:

        - **Auto from connector** (recommended): Uses the automatic onboarding package from Microsoft Defender for Endpoint.
        - **Onboard**: For disconnected environments - paste the WindowsDefenderATP.onboarding blob content.
    - **Sample Sharing**: Configure whether devices share suspicious file samples with Microsoft for analysis.

        - **All**: Enables automatic sample sharing for enhanced threat detection
        - **None**: Disables sample sharing (can reduce detection capabilities)

    Note

    **Telemetry Reporting Frequency** is deprecated and doesn't affect new devices. The setting remains visible for older policy compatibility.

    ![Screen shot of the configuration options for Endpoint Detection and Response.](media/configure-integration/automatic-package-configuration.png)

    Note

    The preceding screen capture shows your configuration options after a connection between Intune and Defender for Endpoint is set up. When connected, the details for the onboarding and offboarding blobs are automatically generated and transfer to Intune.

    If this connection isn't successfully configured, the setting *Defender for Endpoint client configuration package type* only includes options to specify onboard and offboard blobs.
5. **Scope tags** (optional): Add scope tags if needed, then select **Next**.
6. **Assignments**: Select device groups that receive this profile.

    Important

    - **Device groups**: Recommended for immediate deployment.
    - **User groups**: Requires user sign-in before policy applies.

    For assignment guidance, see [Assign user and device profiles](../../device-configuration/assign-device-profile).
7. **Review + create**: Verify all settings and select **Create**.

##### Validation steps

1. **Check policy deployment**: Navigate to **Endpoint security** &gt; **Endpoint detection and response** &gt; Select your policy &gt; **Device status**.
2. **Verify device onboarding**: After 15-30 minutes, devices should appear in the [Microsoft Defender portal](https://security.microsoft.com) under **Endpoints** &gt; **Device inventory**.

Tip

**Avoid policy conflicts:** Multiple policies managing the same settings can cause conflicts. See [Manage policy conflicts](../../device-configuration/endpoint-security/manage-policies#manage-policy-conflicts) for resolution guidance.

### Onboard macOS devices

Unlike Windows devices, macOS requires manual configuration since Intune doesn't provide automatic onboarding packages for macOS.

#### macOS onboarding quick start

1. **Deploy the app**: Follow the [Microsoft Defender for Endpoint for macOS](../../app-management/deployment/add-defender-macos) deployment guide.
2. **Configure settings**: Use Intune app configuration policies.
3. **Verify onboarding**: Check device appears in the Defender portal.

**Additional resources:**

- [Microsoft Defender for Endpoint for Mac](/en-us/defender-endpoint/microsoft-defender-endpoint-mac) - Complete feature documentation and release notes.

### Onboard Android devices

#### Android onboarding quick start

1. **Deploy the app**: Follow the [Deploy and configure Microsoft Defender for Endpoint on Android](deploy-android) deployment guide.
2. **Configure web protection**: Use [Microsoft Defender for Endpoint web protection](configure-web-protection-android) policies for additional security.
3. **Verify onboarding**: Confirm device registration in the Defender portal.

**Available configurations:**

- Web protection settings
- VPN-based scanning
- Privacy controls
- Threat detection preferences

### Onboard iOS/iPadOS devices

#### iOS onboarding quick start

1. **Deploy the app**: Follow [Microsoft Defender for Endpoint for iOS](/en-us/defender-endpoint/microsoft-defender-endpoint-ios) prerequisites and onboarding instructions.
2. **Configure supervision detection**: Set up supervised mode detection for enhanced features.
3. **Verify onboarding**: Check device registration in the Defender portal.

**Supervised mode configuration:** For supervised iOS/iPadOS devices, configure supervision detection to enable advanced management features. See [Complete deployment for supervised devices](/en-us/defender-endpoint/ios-install#complete-deployment-for-supervised-devices).

#### Configuration steps for supervised devices

1. **Create app configuration policy:** In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Apps** &gt; **App configuration policies** &gt; **Add** &gt; **Managed devices**.
2. **Configure basics:**

    - **Name**: Enter a descriptive name, such as "MDE Supervision Detection - iOS".
    - **Platform**: **iOS/iPadOS**
    - **Targeted app**: **Microsoft Defender for Endpoint**
3. **Configuration settings:**

    - **Configuration key**: `issupervised`
    - **Value type**: **String**
    - **Configuration value**: `{{issupervised}}`
4. **Assignment**: Target **All Devices** or specific supervised device groups.
5. **Review + create**: Complete policy creation.

### Monitor device onboarding status

Use the following steps to monitor which devices successfully onboard to Defender for Endpoint.

**To view onboarding status:**

1. In the Intune admin center, go to **Endpoint security** &gt; **Endpoint detection and response** &gt; **EDR Onboarding Status** tab.
2. Review the onboarding status for all platforms.

**Required permission:** Your account needs *Read* permission for *Microsoft Defender Advanced Threat Protection* in Intune RBAC.

**Success indicators:**

- Devices appear in the Defender portal under **Endpoints** &gt; **Device inventory**.
- EDR Onboarding Status shows "Successfully onboarded".
- Risk levels appear in device compliance reports.

## Create and assign compliance policy to set device risk level

Devices that exceed the configured risk threshold are automatically marked as noncompliant, which enables Conditional Access policies to block them from corporate resources.

**Supported platforms:** Android, iOS/iPadOS, and Windows devices.

**Prerequisites:**

- Admin access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with **Endpoint Security Manager** role or equivalent permissions for *Device compliance policies* (custom roles require *Assign*, *Create*, *Delete*, *Read*, and *Update* rights for the *Device compliance policies* permission).

Tip

New to compliance policies? See the [Create a policy](../compliance/create-policy#create-the-policy) guide for general instructions. The following steps focus specifically on Defender for Endpoint integration.

### Steps to create the policy

1. **Go to compliance policies:** In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; expand *Manage devices* and select **Compliance** &gt; **Policies** tab &gt; **Create policy**.
2. **Select platform:** Choose your target platform:

    - **Android device administrator** (limited support)
    - **Android Enterprise** (recommended for Android)
    - **iOS/iPadOS**
    - **Windows 10 and later**

    Important

    On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

    If necessary, select a Profile type, like *Windows 10/11 compliance policy* for the Windows platform.
3. **Configure basics:**

    - **Name**: Enter a descriptive name (for example, "MDE Risk Level - Windows Devices")
    - **Description**: Optional details about the policy purpose
4. **Set risk threshold:** On the **Compliance settings** tab, expand **Microsoft Defender for Endpoint** and configure **Require the device to be at or under the machine risk score**:

    **Risk level options** (determined by Microsoft Defender for Endpoint):

    - **Clear (Most Secure)**:

        - **Allows**: No threats
        - **Blocks**: Any detected threats
        - **Use when**: Maximum security required
    - **Low**:

        - **Allows**: Low-level threats only
        - **Blocks**: Medium and high threats
        - **Use when**: Balanced security and productivity
    - **Medium**:

        - **Allows**: Low and medium threats
        - **Blocks**: High-level threats only
        - **Use when**: Moderate security requirements
    - **High (Least Secure)**

        - **Allows**: All threat levels
        - **Blocks**: None (reporting only)
        - **Use when**: Maximum productivity, minimal blocking

    Important

    **Recommended setting**: **Low** provides the best balance of security and user productivity for most organizations.
5. **Complete configuration:**

    - **Actions for noncompliance**: Configure notifications and grace periods
    - **Assignments**: Select device or user groups to receive this policy
    - **Review + create**: Verify settings and create the policy
6. **Validation:**

    - Devices exceeding the risk threshold show as "Not compliant" in **Devices** &gt; **Compliance** &gt; **Device compliance**
    - Check **Reports** &gt; **Device compliance** for compliance trends

## Create and assign app protection policy to set device risk level

App protection policies work independently of device enrollment, providing an extra layer of security for mobile applications.

**Platforms:** iOS/iPadOS and Android only

**Prerequisites:**

- Admin access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with **Endpoint Security Manager** role or equivalent permissions for security-related *Mobile apps* policies. Custom roles require *Assign*, *Create*, *Delete*, *Read*, *Update*, and *Wipe* rights for the *Managed apps* permission.

Follow the [application protection policy creation guide](../../app-management/protection/create-policy#app-protection-policies-for-iosipados-and-android-apps) and configure these Defender for Endpoint-specific settings:

- **Apps**: Select apps to protect by threat-based policies
- **Conditional launch**: Configure threat level and response actions:

    - **Max allowed device threat level**:
        - **Secured**: No threats allowed (most secure)
        - **Low**: Only low-level threats permitted
        - **Medium**: Low and medium threats permitted
        - **High**: All threat levels permitted (reporting only)
    - **Actions**when threshold exceeded:
        - **Block access**: Prevent app access
        - **Wipe data**: Remove corporate data from the app
- **Assignments**: Assign to groups of users. The policy evaluates their devices for app-level protection.

Important

App protection policies evaluate all protected apps. Conditional launch blocks or wipes devices that exceed the threshold, regardless of enrollment status.

## Create a Conditional Access policy

A Conditional Access policy blocks devices marked as noncompliant from accessing corporate resources like SharePoint and Exchange Online.

Note

Conditional Access is a Microsoft Entra technologies. The Intune admin center provides direct access to the same Conditional Access configuration available in the Azure portal.

**Prerequisites:**

- Admin access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- Permissions equal to the [Conditional Access Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator) role in Entra ID for managing Conditional Access policies.

Important

A policy that requires device compliance for all cloud apps affects every user in scope immediately when enabled. Before turning the policy on, create it in **Report-only** mode first. Report-only mode logs what the policy *would* have done without blocking anyone, letting you confirm scope and catch misconfigurations before enforcement. See [Report-only mode](/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results).

### Steps to create the policy

1. **Go to Conditional Access:** In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Endpoint security** &gt; **Conditional Access** &gt; **Create new policy**.
2. **Basic configuration:**

    - **Name**: Enter a descriptive name, such as "Block Noncompliant Devices - MDE Integration".
3. **User assignment:**

    - **Include**: Select user groups that should be subject to this policy.
    - **Exclude**: Exclude your organization's [emergency break-glass admin accounts](/en-us/entra/identity/role-based-access-control/security-emergency-access) to prevent lockout. If you use Microsoft Entra Connect or Microsoft Entra Connect Cloud Sync, also exclude the **Directory Synchronization Accounts** directory role.
4. **Resource protection:**

    - **Target resources**: Select **Cloud apps**.
    - **Include**: Choose **Select apps**and add:
        - Office 365 SharePoint Online
        - Office 365 Exchange Online
        - Other corporate applications as needed
5. **Client app conditions:**

    - **Conditions** &gt; **Client apps** &gt; **Configure**: **Yes**
    - Select: **Browser** and **Mobile apps and desktop clients**
    - Select **Done**
6. **Access controls:**

    - **Grant** &gt; **Grant access**
    - Select: **Require device to be marked as compliant**
    - **For multiple controls**: **Require all the selected controls**
    - Select **Select**
7. **Enable policy:** Set **Enable policy** to **Report-only**, and then select **Create**. The policy is saved but doesn't block access yet.
8. **Review report-only results:** Wait 24 hours for sign-in data to accumulate, and then review the results:

    - In the [Microsoft Entra admin center](https://entra.microsoft.com), go to **Identity** &gt; **Monitoring & health** &gt; **Sign-in logs**.
    - Filter by your policy name and review the **Report-only** column. Confirm that only expected devices and users show as noncompliant.
    - If the scope looks correct, return to **Conditional Access** &gt; **Policies**, select your policy, and change **Enable policy** to **On**.
9. **Validation:** Test with a noncompliant device to confirm access is properly blocked. Check **Microsoft Entra ID** &gt; **Sign-ins** for policy enforcement logs.