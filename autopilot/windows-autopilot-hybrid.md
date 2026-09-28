---
layout: Conceptual
title: Enrollment for Microsoft Entra hybrid joined devices - Windows Autopilot | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/windows-autopilot-hybrid
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
description: Use Windows Autopilot to enroll Microsoft Entra hybrid joined devices in Microsoft Intune.
ms.date: 2025-05-29T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-identity-device-management
locale: en-us
document_id: 9a62cb17-4d43-66ac-229c-a663937c1953
document_version_independent_id: 9a62cb17-4d43-66ac-229c-a663937c1953
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/windows-autopilot-hybrid.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: windows-autopilot-hybrid
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/windows-autopilot-hybrid.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f9597af6-b6ea-8a1d-5c5f-5d2a4054c906
---

# Enrollment for Microsoft Entra hybrid joined devices - Windows Autopilot | Microsoft Learn

Important

Microsoft recommends deploying new devices as cloud-native using Microsoft Entra join. Deploying new devices as Microsoft Entra hybrid join devices isn't recommended, including through Windows Autopilot. For more information, see [Microsoft Entra joined vs. Microsoft Entra hybrid joined in cloud-native endpoints: Which option is right for your organization](/en-us/intune/solutions/cloud-native-endpoints/azure-ad-joined-hybrid-azure-ad-joined#which-option-is-right-for-your-organization).

Intune and Windows Autopilot can be used to set up Microsoft Entra hybrid joined devices. To do so, follow the steps in this article. For more information about Microsoft Entra hybrid join, see [Understanding Microsoft Entra hybrid join and co-management](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201).

## Requirements

The list of requirements for performing Microsoft Entra hybrid join during Windows Autopilot is organized into three different categories:

- **General** - general requirements.
- **Device enrollment** - device enrollment requirements.
- **Intune connector** - Intune Connector for Active Directory requirements.

Select the appropriate tab to see the relevant requirements:

# [General](#tab/general-requirements)
- Successfully configured the [Microsoft Entra hybrid joined devices](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan). Be sure to [verify the device registration](/en-us/azure/active-directory/devices/howto-hybrid-join-verify) by using the [Get-MgDevice](/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdevice) cmdlet.
- If [Domain and OU-based filtering](/en-us/azure/active-directory/hybrid/how-to-connect-install-custom#domain-and-ou-filtering) is configured as part of Microsoft Entra Connect, ensure that the default organizational unit (OU) or container intended for the Windows Autopilot devices is included in the sync scope.

# [Device enrollment](#tab/device-enrollemnt-requirements)
The device to be enrolled must follow these requirements:

- Use a currently supported version of Windows.
- Have access to the internet [following Windows Autopilot network requirements](requirements?tabs=networking).
- Have access to an Active Directory domain controller.
- Successfully ping the domain controller of the domain being joined.
- If using Proxy, Web Proxy Auto-Discovery Protocol (WPAD) Proxy settings option must be enabled and configured.
- Undergo the out-of-box experience (OOBE).
- Use an authorization type that Microsoft Entra ID supports in OOBE.

Although not required, configuring Microsoft Entra hybrid join for Active Directory Federated Services (ADFS) enables a faster Windows Autopilot Microsoft Entra registration process during deployments. Federated customers that aren't supporting the use of passwords and using ADFS need to follow the steps in the article [Active Directory Federation Services prompt=login parameter support](/en-us/windows-server/identity/ad-fs/operations/ad-fs-prompt-login) to properly configure the authentication experience.

# [Intune connector](#tab/intune-connector-requirements)
- The Intune Connector for Active Directory, also known as the Offline Domain Join (ODJ) connector, must be installed on a computer that's running Windows Server 2016 or later with .NET Framework version 4.7.2 or later.
- The server hosting the Intune Connector for Active Directory must have access to the Internet and Active Directory.

    Note

    The Intune Connector for Active Directory server requires standard domain client access to domain controllers, which includes the RPC port requirements it needs to communicate with Active Directory. For more information, see the following articles:

    - [Service overview and network port requirements for Windows](/en-us/troubleshoot/windows-server/networking/service-overview-and-network-port-requirements)
    - [How to configure a firewall for Active Directory domains and trusts](/en-us/troubleshoot/windows-server/identity/config-firewall-for-ad-domains-and-trusts)
    - [Hybrid Identity Required Ports and Protocols](/en-us/azure/active-directory/hybrid/reference-connect-ports)
- To increase scale and availability, multiple connectors can be installed in a domain. Each connector must be able to create computer objects in the domain that it supports.
- The administrator installing the Intune Connector for Active Directory must be a local administrator on the server where the Intune Connector for Active Directory is being installed.
- For the updated Intune Connector for Active Directory, installation needs to be done with an account that has the following domain rights:

    - **Required** - Create **msDs-ManagedServiceAccount** objects in the Managed Service Accounts container
    - **Optional** - Modify permissions in OUs in Active Directory - if the administrator installing the updated Intune Connector for Active Directory doesn't have this right, additional configuration steps are required by an administrator who has these rights. For more information, see the section Increase the computer account limit in the Organizational Unit (OU) in this article.

        These rights allow the Intune Connector for Active Directory install to properly create Managed Service Accounts (MSAs) and set permissions correctly for the OUs that the MSA is adding computers to.

- The Intune Connector for Active Directory requires the [same endpoints as Intune](/en-us/intune/fundamentals/endpoints).

---

## Set up Windows automatic MDM enrollment

1. Sign in to the [Azure portal](https://portal.azure.com/) and select **Microsoft Entra ID**.
2. In the left hand pane, select **Manage** | **Mobility (MDM and WIP)** &gt; **Microsoft Intune**.
3. Make sure users who deploy Microsoft Entra joined devices by using Intune and Windows are members of a group included in **MDM User scope**.
4. Use the default values in the **MDM Terms of use URL**, **MDM Discovery URL**, and **MDM Compliance URL** boxes, and then select **Save**.

## Install the Intune Connector for Active Directory

The **Intune Connector for Active Directory**, also known as the Offline Domain Join (ODJ) Connector, joins computers to an on-premises domain during the Windows Autopilot process. The connector creates computer objects in a specified Organizational Unit (OU) in Active Directory during the domain join process.

Important

The Intune Connector for Active Directory versions older than 6.2501.2000.5 are deprecated and can no longer process enrollment requests. For more information, see the [Intune Connector for Active Directory with low-privileged account for Windows Autopilot Hybrid Microsoft Entra join deployments](https://aka.ms/Intune-Connector-blog) blog post.

To update the connector, you must:

1. Manually uninstall the legacy connector. There isn't an automatic option.
2. Download and install the updated connector (described in this article).

Tip

If using multiple domains to enroll Autopilot devices:

- You'd need a separate connector instance for each domain. A connector can only process enrollment requests for the same domain as the server it was installed on.
- There can be at most 1 connector per server (VM or physical). Additional servers per domain can be set up for redundancy, each with its own connector installed. In that setup, if one connector fails, the requests will go to another connector on another server within the same domain.

Select the tab that corresponds to the version of the Intune Connector for Active Directory that is being installed:

# [Updated Connector](#tab/updated-connector)
#### Before you begin

- Before you install, make sure that all of the [Intune connector for Active Directory server requirements](/en-us/autopilot/windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements) are met.
- Microsoft recommends (not required) that the administrator installing and configuring the Intune Connector for Active Directory has the domain rights listed in [Intune Connector for Active Directory requirements](windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements). These rights allow the Intune Connector for Active Directory installer and configuration process to set permissions for the Managed Service Account (MSA) on the **Computer** container or OUs where computer objects are created.

    If the administrator lacks these permissions, another administrator with the appropriate rights must [Increase the computer account limit in the Organizational Unit (OU)](windows-autopilot-hybrid?tab=updated-connector#increase-the-computer-account-limit-in-the-organizational-unit).

#### Turn off Internet Explorer Enhanced Security Configuration

Starting with version **6.2504.2001.8**, the updated Intune Connector for Active Directory switched to using WebView2, built on Microsoft Edge, instead of WebBrowser, built on Microsoft Internet Explorer. This change means that the Internet Explorer Enhanced Security Configuration setting in Windows Server no longer needs to be turned off. Make sure to install version **6.2504.2001.8** or later of the Intune Connector for Active Directory to avoid issues with the Internet Explorer Enhanced Security Configuration setting.

#### Download the Intune Connector for Active Directory

1. On the server where the Intune Connector for Active Directory is being installed, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Intune Connector for Active Directory**.
6. In the **Intune Connector for Active Directory** screen, select **Add**.
7. In the **Add connector** window that opens, under **Configuring the Intune Connector for Active Directory**, select **Download the on-premises Intune Connector for Active Directory**. The link downloads a file called `ODJConnectorBootstrapper.exe`.

#### Install the Intune Connector for Active Directory on the server

Important

The Intune Connector for Active Directory installation needs to be done with an account that has the following domain rights:

- **Required** - Create **msDs-ManagedServiceAccount** objects in the Managed Service Accounts container.
- **Optional** - Modify permissions in OUs in Active Directory - if the administrator installing the updated Intune Connector for Active Directory doesn't have this right, additional configuration steps are required by an administrator who has these rights. For more information, see the step/section **Increase the computer account limit in the Organizational Unit**.

1. Sign in to the server where the Intune Connector for Active Directory is being installed with an account that has local administrator rights.
2. If the previous legacy Intune Connector for Active Directory is installed, uninstall it first before installing the updated Intune Connector for Active Directory. For more information, see [Uninstall the Intune Connector for Active Directory](windows-autopilot-hybrid#uninstall-the-intune-connector-for-active-directory).

    Important

    When uninstalling the previous legacy Intune Connector for Active Directory, make sure to run the legacy **Intune Connector for Active Directory** installer as part of the uninstall process. If the legacy Intune Connector for Active Directory installer prompts to **Uninstall** it when it's run, select to uninstall it. This step ensures that the previous legacy Intune Connector for Active Directory is fully uninstalled. The legacy Intune Connector for Active Directory installer can be downloaded from [Intune Connector for Active Directory](https://www.microsoft.com/download/details.aspx?id=105392&amp;msockid=3cb707200c316b2c119712450d8b6a5d).

    Tip

    In domains with only a single Intune Connector for Active Directory, Microsoft recommends first installing the updated Intune Connector for Active Directory on another server. Installing the updated Intune Connector for Active Directory on another server should be done before uninstalling the legacy Intune Connector for Active Directory on the current server. Installing the Intune Connector for Active Directory on another first avoids any downtime while the Intune Connector for Active Directory is being updated on the current server.
3. Open the `ODJConnectorBootstrapper.exe` file that downloaded to launch the **Intune Connector for Active Directory Setup** install.
4. Step through the **Intune Connector for Active Directory Setup** install.
5. At the end of the install, select the checkbox **Launch Intune Connector for Active Directory**.

    Note

    If **Intune Connector for Active Directory Setup** install is accidentally closed without selecting the checkbox **Launch Intune Connector for Active Directory**, the **Intune Connector for Active Directory** configuration can be reopened by selecting **Intune Connector for Active Directory** &gt; **Intune Connector for Active Directory** from the **Start** menu.

#### Sign in to the Intune Connector for Active Directory

1. In the **Intune Connector for Active Directory** window, under the **Enrollment** tab, select **Sign In**.
2. Under the **Sign In** tab, sign in with the Microsoft Entra ID credentials of an Intune administrator role. The user account must have an assigned Intune license. The sign in process might take a few minutes to complete.

    Note

    The account used to enroll the Intune Connector for Active Directory is only a temporary requirement at the time of installation. The account isn't used going forward after the server is enrolled.
3. Once the sign in process completes:

    1. **The Intune Connector for Active Directory successfully enrolled** confirmation window appears. Select **OK** to close the window.
    2. **A Managed Service Account with name "&lt;MSA\_name&gt;" was successfully set up** confirmation window appears. The name of the MSA is in the format `msaODJ#####` where **#####** are five random characters. Notate the name of the MSA that was created, and then select **OK** to close the window. The name of the MSA might be needed later to configure the MSA to allow creating computer objects in OUs.
4. The **Enrollment** tab shows **Intune Connector for Active Directory is enrolled**. The **Sign In** button is greyed out and **Configure Managed Service Account** is enabled.
5. Close the **Intune Connector for Active Directory** window.

#### Verify the Intune Connector for Active Directory is active

After authenticating, the Intune Connector for Active Directory finishes installing. Once it finishes installing, verify that it's active in Intune by following these steps:

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) if it's still open. If the **Add connector** window is still displayed, close it.

    If the **Microsoft Intune admin center** isn't still open:

    1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
    2. In the **Home** screen, select **Devices** in the left hand pane.
    3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
    4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
    5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Intune Connector for Active Directory**.
2. In the **Intune Connector for Active Directory** page:

    - Confirm that the server is displayed under **Connector name** and shows as **Active** under **Status**
    - For the updated Intune Connector for Active Directory, make sure the version is greater than or equal to **6.2501.2000.5**.

    If the server isn't displayed, select **Refresh** or navigate away from the page, and then navigate back to the **Intune Connector for Active Directory** page.

Note

- It can take several minutes for the newly enrolled server to appear in the **Intune Connector for Active Directory** page of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). The enrolled server only appears if it can successfully communicate with the Intune service.
- Inactive Intune Connectors for Active Directory still appear in the **Intune Connector for Active Directory** page and will automatically be cleaned up after 30 days.

After the Intune Connector for Active Directory is installed, it will start logging in the **Event Viewer** under the path **Applications and Services Logs** &gt; **Microsoft** &gt; **Intune** &gt; **ODJConnectorService**. Under this path, **Admin** and **Operational** logs can be found.

#### Configure the MSA to allow creating objects in OUs (optional)

By default, MSAs only have access to create computer objects in the **Computers** container. MSAs don't have access to create computer objects in Organizational Units (OUs). To allow the MSA to create objects in OUs, the OUs need to be added to the `ODJConnectorEnrollmentWizard.exe.config` XML file found in `ODJConnectorEnrollmentWizard` directory where the Intune Connector for Active Directory was installed, normally `C:\Program Files\Microsoft Intune\ODJConnector\`.

To configure the MSA to allow creating objects in OUs, follow these steps:

1. On the server where the Intune Connector for Active Directory is installed, navigate to `ODJConnectorEnrollmentWizard` directory where the Intune Connector for Active Directory was installed, normally `C:\Program Files\Microsoft Intune\ODJConnector\`.
2. In the `ODJConnectorEnrollmentWizard` directory, open the existing `ODJConnectorEnrollmentWizard.exe.config` XML file in a text editor, for example, **Notepad**.
3. In the `add key` element of the `ODJConnectorEnrollmentWizard.exe.config` XML file:

    - Next to `value=`, add in any desired OUs that the MSA should have access to create computer objects in.
    - The OU name needs to be in the [LDAP distinguished name](/en-us/previous-versions/windows/desktop/ldap/distinguished-names) format and if applicable, needs to be escaped.
    - Multiple OUs are supported by separating each OU with a semicolon (;).
    - Make sure to retain the quotes (") next to `value=`. All of the OU values need to be within one pair of quotes.
    - Don't change the name of the key element `OrganizationalUnitsUsedForOfflineDomainJoin`.

    The following example is an example XML entry with multiple OUs in LDAP distinguished name format:

    ```xml
      <appSettings>
    
        <!-- Semicolon separated list of OUs that will be used for Hybrid Autopilot, using LDAP distinguished name format.
            The ODJ Connector will only have permission to create computer objects in these OUs.
            The value here should be the same as the value in the Hybrid Autopilot configuration profile in the Azure portal - https://learn.microsoft.com/en-us/mem/intune/configuration/domain-join-configure
    
            Usage example (NOTE: PLEASE ENSURE THAT THE DISTINGUISHED NAME IS ESCAPED PROPERLY):
            Domain contains the following OUs:
              - OU=HybridDevices,DC=contoso,DC=com
              - OU=HybridDevices2,OU=IntermediateOU,OU=TopLevelOU,DC=contoso,DC=com
    
            Value: "OU=HybridDevices,DC=contoso,DC=com;OU=HybridDevices2,OU=IntermediateOU,OU=TopLevelOU,DC=contoso,DC=com" -->
    
        <add key="OrganizationalUnitsUsedForOfflineDomainJoin" value="OU=SubOU,OU=TopLevelOU,DC=contoso,DC=com;OU=Mine,DC=contoso,DC=com" />
      </appSettings>
    ```

    Tip

    In the example, replace the example red text next to `value=` with the organization's OUs in [LDAP distinguished name format](/en-us/previous-versions/windows/desktop/ldap/distinguished-names). As shown in the example, make sure all OU entries are within the quotes (") and that each OU is separated with a semicolon (;) .
4. Once all desired OUs are added, save the `ODJConnectorEnrollmentWizard.exe.config` XML file.
5. As an administrator that has appropriate permissions to modify OU permissions, open the **Intune Connector for Active Directory** by navigating to **Intune Connector for Active Directory** &gt; **Intune Connector for Active Directory** from the **Start** menu.

    Important

    If the administrator installing and configuring the Intune Connector for Active Directory doesn't have permissions to modify OU permissions, then the section/steps **Increase the computer account limit in the Organizational Unit** need to be followed instead by an administrator that does have permissions to modify OU permissions.
6. Under the **Enrollment** tab in the **Intune Connector for Active Directory** window, select **Configure Managed Service Account**.
7. An **A Managed Service Account with name "&lt;MSA\_name&gt;" was successfully set up** confirmation window appears. Select **OK** to close the window.

#### Use a custom Managed Service Account (optional)

Optionally, you can configure the connector to use your own Managed Service Account, as opposed to the MSA automatically set up by the connector.

##### MSA requirements

This section describes the MSA requirements.

- Provided account must be a service account with either of the following object categories in Active Directory:

    - `CN=ms-DS-Group-Managed-Service-Account,CN=Schema,CN=Configuration,DC=contoso,DC=com`
    - `CN=ms-DS-Managed-Service-Account,CN=Schema,CN=Configuration,DC=contoso,DC=com`
- The configuration value for the service account needs to be in the following format: `<msaAccountName@domain>`
- Service account needs to exist in the same domain as the ODJ Connector’s server.
- Service account needs to be installed on the server hosting the ODJ Connector. For more information, see [Install-ADServiceAccount](/en-us/powershell/module/activedirectory/install-adserviceaccount).

    - If using sMSA, the account can only be linked to a single machine.
    - If using a gMSA, the server you’re installing the gMSA on needs to have access to the password.
- Service account needs to have local **Log On as a Service** permission which could be set directly or via group membership. For more information, see [Enable service logon](/en-us/system-center/scsm/enable-service-log-on-sm).
- Permission needs to be granted manually for service accounts to create computer objects for hybrid Autopilot flows. For more information, see [Increase the computer account limit in the Organizational Unit (OU)](/en-us/autopilot/tutorial/user-driven/hybrid-azure-ad-join-computer-account-limit?tabs=updated-connector).

##### How to set up

Update `ODJConnectorEnrollmentWizard.exe.config`. Its default location is `C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorEnrollmentWizard`.

1. In the **appSettings section** of the file, add the following line:

    `<add key="TenantConfiguredManagedServiceAccount" value="{accountname}" />`
2. Sign in to the connector.

##### Disable OU updates

Using your own MSA will disable the connector from making any OU updates, regardless of any configured in OrganizationalUnitsUsedForOfflineDomainJoin. To prevent errors, disable OU updates by updating `ODJConnectorEnrollmentWizard.exe.config`. Its default location is `C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorEnrollmentWizard`.

1. In the **appSettings section** of the file, add the following line:

    `<add key="DisableOUUpdates" value="true" />`
2. Sign in to the connector.

# [Legacy Connector](#tab/legacy-connector)
Important

The legacy Intune Connector for Active Directory is deprecated. These instructions assume that the legacy Intune Connector for Active Directory is already installed or is already downloaded. If the legacy Intune Connector for Active Directory installer isn't already downloaded, it can be downloaded from [Intune Connector for Active Directory](https://www.microsoft.com/download/details.aspx?id=105392&amp;msockid=3cb707200c316b2c119712450d8b6a5d).

However, best practice is to download and install the updated Intune Connector for Active Directory. For more information, select the **Updated Connector** tab instead.

Before beginning the installation, make sure that all of the [Intune connector for Active Directory server requirements](/en-us/autopilot/windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements) are met.

#### Disable Internet Explorer Enhanced Security Configuration

By default Windows Server has Internet Explorer Enhanced Security Configuration turned on. Internet Explorer Enhanced Security Configuration might cause problems signing in to the Intune Connector for Active Directory. Since Internet Explorer is deprecated and in most instances, not even installed on Windows Server, Microsoft recommends turning off Internet Explorer Enhanced Security Configuration. To turn off Internet Explorer Enhanced Security Configuration:

1. Sign in to the server where the Intune Connector for Active Directory is being installed with an account that has local administrator rights and domain admin rights. Domain admin rights are required so that the Intune Connector for Active Directory installer can properly create an MSA.
2. Open **Server Manager**.
3. In the left pane of Server Manager, select **Local Server**.
4. In the right **PROPERTIES** pane of Server Manager, select the **On** or **Off** link next to **IE Enhanced Security Configuration**.
5. In the **Internet Explorer Enhanced Security Configuration** window, select **Off** under **Administrators:**, and then select **OK**.

#### Install the legacy Intune Connector for Active Directory on the server

1. Open the previously downloaded `ODJConnectorBootstrapper.exe` file to launch the **Intune Connector for Active Directory Setup** install.

    Note

    If the legacy Intune Connector for Active Directory is already installed, go to the **Start** menu &gt; **Intune Connector for Active Directory** &gt; **Intune Connector for Active Directory**, and then proceed to Sign in to the legacy Intune Connector for Active Directory.
2. In the **Intune Connector for Active Directory Setup** installer window, select **I agree to the license terms and conditions**, and then select **Install**.

    Note

    If an install location other than the default of **C:\Program Files\Microsoft Intune\ODJConnector** is desired, select **Options** and specify the desired install location.
3. When the install completes, select **Configure Now** in the **Intune Connector for Active Directory Setup** installer window.

    Note

    If **Close** is accidentally selected or the **Intune Connector for Active Directory Setup** installer window is accidentally closed, the **Intune Connector for Active Directory** configuration can be accessed by selecting **Intune Connector for Active Directory** &gt; **Intune Connector for Active Directory** from the **Start** menu.

#### Sign in to the legacy Intune Connector

1. In the **Intune Connector for Active Directory** window, under the **Enrollment** tab, select **Sign In**.
2. Under the **Sign In** tab, sign in with the credentials of an Intune administrator role. The user account must have an assigned Intune license. The sign in process might take a few minutes to complete.

    Note

    The account used to enroll the Intune Connector for Active Directory is only a temporary requirement at the time of installation. The account isn't used going forward after the server is enrolled.
3. Once the sign in process is complete, a **The Intune Connector for Active Directory successfully enrolled** confirmation window appears. Select **OK** to close the window.
4. The **Enrollment** tab shows **Intune Connector for Active Directory is enrolled** and the **Sign In** button is greyed out.
5. Close the **Intune Connector for Active Directory** window.

#### Verify the legacy Intune Connector for Active Directory is active

After authenticating, the Intune Connector for Active Directory finishes installing. Once it finishes installing, verify that it's active in Intune by following these steps:

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) if it's still open. If the **Add connector** window is still displayed, close it.

    If the **Microsoft Intune admin center** isn't still open:

    1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
    2. In the **Home** screen, select **Devices** in the left hand pane.
    3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
    4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
    5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Intune Connector for Active Directory**.
2. In the **Intune Connector for Active Directory** page, confirm that the server is displayed under **Connector name** and shows as **Active** under **Status**. If the server isn't displayed, select **Refresh** or navigate away from the page, and then navigate back to the **Intune Connector for Active Directory** page.

Note

- It can take several minutes for the newly enrolled server to appear in the **Intune Connector for Active Directory** page of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). The enrolled server only appears if it can successfully communicate with the Intune service.
- Inactive Intune Connectors for Active Directory still appear in the **Intune Connector for Active Directory** page and will automatically be cleaned up after 30 days.

After the Intune Connector for Active Directory is installed, it will start logging in the **Event Viewer** under the path **Applications and Services Logs** &gt; **Microsoft** &gt; **Intune** &gt; **ODJConnectorService**. Under this path, **Admin** and **Operational** logs can be found.

---

### Configure web proxy settings

If there's a web proxy in the networking environment, ensure that the Intune Connector for Active Directory works properly by referring to [Configure proxy settings for the Intune Connector for Active Directory](autopilot-hybrid-connector-proxy).

## Increase the computer account limit in the Organizational Unit

# [Updated Connector](#tab/updated-connector)
Important

This step is only needed under one of the following conditions:

- The administrator that installed and configured the Intune Connector for Active Directory didn't have appropriate rights as outlined in [Intune Connector for Active Directory Requirements](windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements).
- The administrator that installed and configured the Intune Connector had appropriate rights as outlined above, but the [Managed Service Account (MSA)](/en-us/windows-server/identity/ad-ds/manage/understand-service-accounts#standalone-managed-service-accounts) could not be granted permission to create computer objects in the organizational unit(s) specified during the Intune Connector installation. For more information, see [Configure the new Microsoft Intune connector for Active Directory with the least privilege principle](https://techcommunity.microsoft.com/blog/intunecustomersuccess/configure-the-new-microsoft-intune-connector-for-active-directory-with-the-least/4432478).
- The `ODJConnectorEnrollmentWizard.exe.config` XML file wasn't modified to add OUs that the MSA should have permissions for.

The purpose of Intune Connector for Active Directory is to join computers to a domain and add them to an OU. For this reason, the Managed Service Account being used for the Intune Connector for Active Directory needs to have permissions to create computer accounts in the OU where the computers are joined to the on-premises domain.

With default permissions in Active Directory, domain joins by the Intune Connector for Active Directory might initially work without any permission modifications to the OU in Active Directory. However after MSA attempts to join more than 10 computers to the on-premises domain, it would stop working because by default, Active Directory only allows any single account to join up to 10 computers to the on-premises domain.

The following users aren't restricted by the 10 computer domain join limitation:

- Users in the Administrators or Domain Administrators groups: In order to comply with the least privilege principles model, Microsoft doesn't recommend making the MSA an administrator or domain administrator.
- Users with delegated permissions on Organizational Unit (OUs) and containers in Active Directory to create computer accounts: This method is recommended since it follows the least privilege principles model.

To fix this limitation, the MSA needs the **Create computer accounts** permission in the Organizational Unit (OU) where the computers are joined to in the on-premises domain. The Intune Connector for Active Directory sets the permissions for the MSAs to the OUs as long as one of the following conditions is met:

- The administrator installing the Intune Connector for Active Directory has the necessary permissions to set permissions on the OUs.
- The administrator configuring the Intune Connector for Active Directory has the necessary permissions to set permissions on the OUs.

If the administrator installing or configuring the Intune Connector for Active Directory doesn't have the necessary permissions to set permissions on the OUs, then the following steps need to be followed:

1. Sign in to a computer that has access to the **Active Directory Users and Computers** console with an account that as the necessary permissions to set permissions on OUs.
2. Open the **Active Directory Users and Computers** console by running **DSA.msc**.
3. Expand the desired domain and navigate to the organizational unit (OU) that computers are joining to during Windows Autopilot.

    Note

    The OU that computers join during the Windows Autopilot deployment is specified later during the **Configure and assign domain join profile** step.
4. Right-click on the OU and select **Properties**.

    Note

    If computers are joining the default **Computers** container instead of an OU, right-click on the **Computers** container and select **Delegate Control**.
5. In the OU **Properties** windows that opens, select the **Security** tab.
6. In the **Security** tab, select **Advanced**.
7. In the **Advanced Security Settings** window, select **Add**.
8. In the **Permission Entry** windows, next to **Principal**, select the **Select a principal** link.
9. In the **Select User, Computer, Service Account, or Group** window, select the **Object Types...** button.
10. In the **Object Types** window, select the **Service Accounts** check box, and then select **OK**.
11. In the **Select User, Computer, Service Account, or Group** window, under **Enter the object name to select**, enter the name of the MSA being used for the Intune Connector for Active Directory.

    Tip

    The MSA was created during the **Install the Intune Connector for Active Directory** step/section and has the name format of `msaODJ#####` where **#####** are five random characters. If the MSA name isn't known, follow these steps to find the MSA name:

    1. On the server running the Intune Connector for Active Directory, right-click on the **Start** menu and then select **Computer Management**.
    2. In the **Computer Management** window, expand **Services and Applications** and then select **Services**.
    3. In the results pane, locate the service with the name **Intune ODJConnector for Active Service**. The name of the MSA is listed in the **Log On As** column.
12. Select **Check Names** to validate the MSA name entry. Once the entry is validated, select **OK**.
13. In the **Permission Entry** windows, select the **Applies to:** drop-down menu and then select **This object only**.
14. Under **Permissions**, unselect all items, and then only select the **Create Computer objects** check box.
15. Select **OK** to close the **Permission Entry** window.
16. In the **Advanced Security Settings** window, select either **Apply** or **OK** to apply the changes.

# [Legacy Connector](#tab/legacy-connector)
The purpose of Intune Connector for Active Directory is to join computers to a domain and add them to an OU. For this reason, the server running the Intune Connector for Active Directory needs to have permissions to create computer accounts in the OU where the computers are joined to the on-premises domain.

With default permissions in Active Directory, domain joins by the Intune Connector for Active Directory might initially work without any permission modifications to the OU in Active Directory. However after the server running the Intune Connector for Active Directory attempts to join more than 10 computers to the on-premises domain, it would stop working because by default, Active Directory only allows any single account to join up to 10 computers to the on-premises domain.

The following users aren't restricted by the 10 computer domain join limitation:

- Users in the Administrators or Domain Administrators groups - in order to comply with the least privilege principles model, Microsoft doesn't recommend making the computer account running the Intune Connector for Active Directory an administrator or domain administrator.
- Users with delegated permissions on Organizational Unit (OUs) and containers in Active Directory to create computer accounts - this method is recommended since it follows the least privilege principles model.

To fix this limitation, the server running the Intune Connector for Active Directory needs the **Create computer accounts** permission in the Organizational Unit (OU) where the computers are joined to in the on-premises domain:

To increase the computer account limit in the Organizational Unit (OU) that computers are joining to during Windows Autopilot, follow these steps on a computer that has access to the **Active Directory Users and Computers** console:

1. Open the **Active Directory Users and Computers** console by running **DSA.msc**.
2. Expand the desired domain and navigate to the organizational unit (OU) that computers are joining to during Windows Autopilot.

    Note

    The OU that computers join during the Windows Autopilot deployment is specified later during the **Configure and assign domain join profile** step.
3. Right-click on the OU and select **Delegate Control**.

    Note

    If computers are joining the default **Computers** container instead of an OU, right-click on the **Computers** container and select **Delegate Control**.
4. In the **Welcome to the Delegation of Control Wizard** window of the **Delegation of Control Wizard**, select **Next**.
5. In the **Users or Groups** window, under **Selected users and groups**, select **Add**.
6. Next to **Select this object type:** in the **Select Users, Computers, or Groups** window, select **Object Types**.
7. In the **Object Types** window, select the **Computers** check box, and then select **OK**. The other items in this window can be left at their default.
8. In the **Select Users, Computers, or Groups** window, under the **Enter the object names to select** box, enter the name of the computer where the Intune Connector for Active Directory was installed during the **Install the Intune Connector for Active Directory** step.
9. Select **Check Names** to validate the entry. Once the entry is validated, select **OK**.
10. In the **Users or Groups** window, verify that the correct computer is shown under **Selected users and groups:**, and then select **Next**.
11. In the **Tasks to Delegate** window, select **Create a custom task to delegate**, and then select **Next**.
12. In the **Active Directory Object Type** window:

    1. Select **Only the following objects in the folder**.
    2. Under **Only the following objects in the folder**, select **Computer objects**.
    3. Select the **Create selected objects in this folder** checkbox.
    4. Select **Next**.
13. In the **Permissions** window, under **Permissions:**, select the **Full Control** check box, and then select **Next**.

    Note

    After selecting the **Full Control** check box, all other options under **Permissions:** are automatically selected. The automatic selection of the checkboxes is normal and expected. Don't unselect any of the check boxes after they're automatically selected.
14. In the **Completing the Delegation of Control Wizard** window, select **Finish**.

---

## Create a device group

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** &gt; **New group**.
2. In the **Group** pane, select the following options:

    1. For **Group type**, select **Security**.
    2. Enter a **Group name** and **Group description**.
    3. Select a **Membership type**.
3. If **Dynamic Devices** is selected for the membership type, in the **Group** pane, select **Dynamic device members**.
4. Select **Edit** in the **Rule syntax** box and enter one of the following code lines:

    - To create a group that includes all Windows Autopilot devices, enter:

        `(device.devicePhysicalIDs -any _ -startsWith "[ZTDId]")`
    - Intune's Group Tag field maps to the OrderID attribute on Microsoft Entra devices. To create a group that includes all of Windows Autopilot devices with a specific Group Tag (OrderID), enter:

        `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - To create a group that includes all Windows Autopilot devices with a specific Purchase Order ID, enter:

        `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
5. Select **Save** &gt; **Create**.

## Register Windows Autopilot devices

Select one of the following ways to enroll Windows Autopilot devices.

### Register Windows Autopilot devices that are already enrolled

1. Create a Windows Autopilot deployment profile with the setting **Convert all targeted devices to Autopilot** set to **Yes**.
2. Assign the profile to a group that contains the members that need to be automatically registered with Windows Autopilot.

For more information, see [Configure Windows Autopilot profiles](profiles).

### Register Windows Autopilot devices that aren't enrolled

Devices that aren't yet enrolled into Windows Autopilot can be manually registered. For more information, see [Manual registration](manual-registration).

### Register devices from an OEM

If purchasing new devices, some OEMs can register the devices on behalf of the organization. For more information, see [OEM registration](oem-registration).

### Display registered Windows Autopilot device

Before devices enroll in Intune, *registered* Windows Autopilot devices are displayed in three places (with names set to their serial numbers):

- The **Windows Autopilot Devices** pane in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Select **Devices** &gt; **By platform | Windows** &gt; **Device onboarding | Enrollment**. Under **Windows Autopilot**, select **Devices**.
- The **Devices | All devices** pane in the [Azure portal](https://portal.azure.com). Select **Devices** &gt; **All Devices**.
- The **Autopilot** pane in [Microsoft 365 admin center](https://admin.microsoft.com/). Select **Devices** &gt; **Autopilot**.

After the Windows Autopilot devices are *enrolled*, the devices are displayed in four places:

- The **Devices | All Devices** pane in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Select **Devices** &gt; **All devices**.
- The **Windows | Windows devices** pane in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Select **Devices** &gt; **By platform | Windows**.
- The **Devices | All devices** pane in the [Azure portal](https://portal.azure.com). Select **Devices** &gt; **All Devices**.
- The **Active devices** pane in [Microsoft 365 admin center](https://admin.microsoft.com/). Select **Devices** &gt; **Active devices**.

Note

After devices are enrolled, the devices are still displayed in the **Windows Autopilot Devices** pane in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and in the **Autopilot** pane in [Microsoft 365 admin center](https://admin.microsoft.com/), but those objects are the Windows Autopilot registered objects.

A device object is pre-created in Microsoft Entra ID once a device is registered in Windows Autopilot. When a device goes through a hybrid Microsoft Entra deployment, by design, another device object is created resulting in duplicate entries.

## VPNs

The following VPN clients are tested and validated:

- In-box Windows VPN client
- Cisco AnyConnect (Win32 client)
- Pulse Secure (Win32 client)
- GlobalProtect (Win32 client)
- Checkpoint (Win32 client)
- Citrix NetScaler (Win32 client)
- SonicWall (Win32 client)
- FortiClient VPN (Win32 client)

When using VPNs, select **Yes** for the **Skip AD connectivity check** option in the Windows Autopilot deployment profile. Always-On VPNs shouldn't require this option since it connects automatically.

Note

This list of VPN clients isn't a comprehensive list of all VPN clients that work with Windows Autopilot. Contact the respective VPN vendor regarding compatibility and supportability with Windows Autopilot or regarding any issues with using a VPN solution with Windows Autopilot.

### Unsupported VPN clients

The following VPN solutions are **known** not to work with Windows Autopilot and therefore aren't supported for use with Windows Autopilot:

- UWP-based VPN plug-ins
- Anything that requires a user cert
- DirectAccess

In addition, any bring-your-own (BYO) VPN configurations are not supported for use during Windows Autopilot in pre-provisioning mode.

Note

Omission of a specific VPN client from this list doesn't automatically mean it's supported or that it works with Windows Autopilot. This list only lists the VPN clients that are **known** not to work with Windows Autopilot.

## Create and assign a Windows Autopilot deployment profile

Windows Autopilot deployment profiles are used to configure the Windows Autopilot devices.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Deployment Profiles**.
6. In the **Windows Autopilot deployment profiles** screen, select the **Create Profile** drop down menu and then select **Windows PC**.
7. In the **Create profile** screen, on the **Basics** page, enter a **Name** and optional **Description**.
8. If all devices in the assigned groups should automatically register to Windows Autopilot, set **Convert all targeted devices to Autopilot** to **Yes**. All corporate owned, non-Windows Autopilot devices in assigned groups register with the Windows Autopilot deployment service. Personally owned devices aren't registered to Windows Autopilot. Allow 48 hours for the registration to be processed. When the device is unenrolled and reset, Windows Autopilot enrolls it again. After a device is registered in this way, disabling this setting or removing the profile assignment won't remove the device from the Windows Autopilot deployment service. Instead the devices need to be directly deleted. For more information, see [Delete Windows Autopilot devices](add-devices#delete-windows-autopilot-devices).
9. Select **Next**.
10. On the **Out-of-box experience (OOBE)** page, for **Deployment mode**, select **User-driven**.
11. In the **Join to Microsoft Entra ID as** box, select **Microsoft Entra hybrid joined**.
12. If deploying devices off of the organization's network using VPN support, set the **Skip Domain Connectivity Check** option to **Yes**. For more information, see [User-driven mode for Microsoft Entra hybrid join with VPN support](user-driven#user-driven-mode-for-microsoft-entra-hybrid-join-with-vpn-support).
13. Configure the remaining options on the **Out-of-box experience (OOBE)** page as needed.
14. Select **Next**.
15. On the **Scope tags** page, select [scope tags](/en-us/intune/fundamentals/role-based-access-control/scope-tags) for this profile.
16. Select **Next**.
17. On the **Assignments** page, select **Select groups to include** &gt; search for and select the device group &gt; **Select**.
18. Select **Next** &gt; **Create**.

Note

Intune periodically checks for new devices in the assigned groups, and then begin the process of assigning profiles to those devices. Due to several different factors involved in the process of Windows Autopilot profile assignment, an estimated time for the assignment can vary from scenario to scenario. These factors can include Microsoft Entra groups, membership rules, hash of a device, Intune and Windows Autopilot service, and internet connection. The assignment time varies depending on all the factors and variables involved in a specific scenario.

## (Optional) Turn on the enrollment status page

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, select **Devices** in the left hand pane.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Enrollment Status Page**.
6. In the **Enrollment Status Page** pane, select **Default** &gt; **Settings**.
7. In the **Show app and profile installation progress** box, select **Yes**.
8. Configure the other options as needed.
9. Select **Save**.

## Create and assign a Domain Join profile

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Manage devices | Configuration** &gt; **Policies** &gt;**Create** &gt; **New Policy**.
2. In the **create a profile** window that opens, enter the following properties:

    - **Name**: Enter a descriptive name for the new profile.
    - **Description**: Enter a description for the profile.
    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates**, select the template name **Domain Join**, and select **Create**.
3. Enter the **Name** and **Description** and select **Next**.
4. Provide a **Computer name prefix** and **Domain name**.
5. (Optional) Provide an **Organizational unit** (OU) in [DN format](/en-us/windows/desktop/ad/object-names-and-identities#distinguished-name). The options include:

    - Provide an OU in which control is delegated to the Windows device that is running the Intune Connector for Active Directory.
    - Provide an OU in which control is delegated to the root computers in organization's on-premises Active Directory.
    - If this field is left blank, the computer object is created in the Active Directory default container. The default container is normally the `CN=Computers` container. For more information, see [Redirect the users and computers containers in Active Directory domains](/en-us/troubleshoot/windows-server/identity/redirect-users-computers-containers).

    Valid examples:

    - `OU=SubOU,OU=TopLevelOU,DC=contoso,DC=com`
    - `OU=Mine,DC=contoso,DC=com`

    Invalid examples:

    - `CN=Computers,DC=contoso,DC=com` - a container can't be specified. Instead, leave the value blank to use the default for the domain.
    - `OU=Mine` - the domain must be specified via the `DC=` attributes.

    Make sure not to use quotation marks around the value in **Organizational unit**.
6. Select **OK** &gt; **Create**. The profile is created and displayed in the list.
7. [Assign a device profile](/en-us/intune/device-configuration/assign-device-profile#assign-a-policy-to-users-or-groups) to the same group used at the step [Create a device group](windows-autopilot-hybrid#create-a-device-group). Different groups can be used if there's a need to join devices to different domains or OUs.

Note

The naming capability for Windows Autopilot for Microsoft Entra hybrid join doesn't support variables such as **%SERIAL%**. It only supports prefixes for the computer name.

## Uninstall the Intune Connector for Active Directory

The Intune Connector for Active Directory is installed locally on a computer via an executable file. If the Intune Connector for Active Directory needs to be uninstalled from a computer, it needs to also be done locally on the computer. The Intune Connector for Active Directory can't be removed through the Intune portal or through a graph API call.

To uninstall the Intune Connector for Active Directory from the server, select the appropriate tab for the version of the Windows Server OS and then follow the steps:

# [Windows Server 2025](#tab/windows-server-2025)
1. Sign in to the computer hosting the Intune Connector for Active Directory.
2. Right-click on the **Start** menu and then select **Settings** &gt; **Apps** &gt; **Installed apps**.

    Or

    Select the following **Apps &gt; Installed apps** shortcut:
3. In the **Apps &gt; Installed apps** window, find **Intune Connector for Active Directory**.
4. Next to **Intune Connector for Active Directory**, select **...** &gt; **Uninstall**, and then select the **Uninstall** button.
5. The Intune Connector for Active Directory proceeds to uninstall.
6. In some cases, the Intune Connector for Active Directory might not fully uninstall until the original Intune Connector for Active Directory installer `ODJConnectorBootstrapper.exe` is run again. To verify that the Intune Connector for Active Directory is fully uninstalled, run the `ODJConnectorBootstrapper.exe` installer again. If it prompts to **Uninstall**, select to uninstall it. Otherwise, close the `ODJConnectorBootstrapper.exe` installer.

    Note

    The legacy **Intune Connector for Active Directory** installer can be downloaded from the [Intune Connector for Active Directory](https://www.microsoft.com/download/details.aspx?id=105392&amp;msockid=3cb707200c316b2c119712450d8b6a5d) and should only be used for uninstalls. For new installs, use the [updated Intune Connector for Active Directory](windows-autopilot-hybrid?tabs=updated-connector#install-the-intune-connector-for-active-directory-on-the-server).

# [Windows Server 2019/2022](#tab/windows-server-2019-2022)
1. Sign in to the computer hosting the Intune Connector for Active Directory.
2. Right-click the **Start** menu and then select **Settings** &gt; **Apps**.

    Or

    Select the following **Apps** shortcut:
3. Under **Apps & features**, find and select **Intune Connector for Active Directory**.
4. Under **Intune Connector for Active Directory**, select the **Uninstall** button, and then select the **Uninstall** button again.
5. The Intune Connector for Active Directory proceeds to uninstall.
6. In some cases, the Intune Connector for Active Directory might not fully uninstall until the original Intune Connector for Active Directory installer `ODJConnectorBootstrapper.exe` is run again. To verify that the Intune Connector for Active Directory is fully uninstalled, run the `ODJConnectorBootstrapper.exe` installer again. If it prompts to **Uninstall**, select to uninstall it. Otherwise, close the `ODJConnectorBootstrapper.exe` installer.

    Note

    The legacy **Intune Connector for Active Directory** installer can be downloaded from the [Intune Connector for Active Directory](https://www.microsoft.com/download/details.aspx?id=105392&amp;msockid=3cb707200c316b2c119712450d8b6a5d) and should only be used for uninstalls. For new installs, use the [updated Intune Connector for Active Directory](windows-autopilot-hybrid?tabs=updated-connector#install-the-intune-connector-for-active-directory-on-the-server).

# [Windows Server 2016](#tab/windows-server-2016)
1. Sign in to the computer hosting the Intune Connector for Active Directory.
2. Right-click the **Start** menu and then select **Settings** &gt; **System** &gt; **Apps & features**.

    Or

    Select the following **Apps** shortcut:
3. Under **Apps & features**, find and select **Intune Connector for Active Directory**.
4. Under **Intune Connector for Active Directory**, select the **Uninstall** button, and then select the **Uninstall** button again.
5. The Intune Connector for Active Directory proceeds to uninstall.
6. In some cases, the Intune Connector for Active Directory might not fully uninstall until the original Intune Connector for Active Directory installer `ODJConnectorBootstrapper.exe` is run again. To verify that the Intune Connector for Active Directory is fully uninstalled, run the `ODJConnectorBootstrapper.exe` installer again. If it prompts to **Uninstall**, select to uninstall it. Otherwise, close the `ODJConnectorBootstrapper.exe` installer.

    Note

    The legacy **Intune Connector for Active Directory** installer can be downloaded from the [Intune Connector for Active Directory](https://www.microsoft.com/download/details.aspx?id=105392&amp;msockid=3cb707200c316b2c119712450d8b6a5d) and should only be used for uninstalls. For new installs, use the [updated Intune Connector for Active Directory](windows-autopilot-hybrid?tabs=updated-connector#install-the-intune-connector-for-active-directory-on-the-server).

---