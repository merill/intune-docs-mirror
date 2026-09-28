---
layout: Conceptual
title: Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 2 of 11 - Install the Intune Connector for Active Directory | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-intune-connector
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
description: How to - Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 2 of 11 - Install the Intune Connector for Active Directory.
ms.date: 2025-05-29T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 1096cfe0-031f-9251-0e8b-7a11880ed07f
document_version_independent_id: 1096cfe0-031f-9251-0e8b-7a11880ed07f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-intune-connector.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/pre-provisioning/hybrid-azure-ad-join-intune-connector
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/pre-provisioning/hybrid-azure-ad-join-intune-connector.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 2fe73af9-1780-197f-a97f-7d6d226aa442
---

# Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join - Step 2 of 11 - Install the Intune Connector for Active Directory | Microsoft Learn

Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)

- **Step 2: Install the Intune Connector for Active Directory**

- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Technician flow](hybrid-azure-ad-join-technician-flow)
- Step 11: [User flow](hybrid-azure-ad-join-user-flow)

For an overview of the Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join workflow, see [Windows Autopilot for pre-provisioned deployment Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

Note

If the Intune Connector for Active Directory is already installed and configured, skip this step and move on to [Step 3: Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit).

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
- Microsoft recommends (not required) that the administrator installing and configuring the Intune Connector for Active Directory has the domain rights listed in [Intune Connector for Active Directory requirements](../../windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements). These rights allow the Intune Connector for Active Directory installer and configuration process to set permissions for the Managed Service Account (MSA) on the **Computer** container or OUs where computer objects are created.

    If the administrator lacks these permissions, another administrator with the appropriate rights must [Increase the computer account limit in the Organizational Unit (OU)](../../windows-autopilot-hybrid?tab=updated-connector#increase-the-computer-account-limit-in-the-organizational-unit).

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
2. If the previous legacy Intune Connector for Active Directory is installed, uninstall it first before installing the updated Intune Connector for Active Directory. For more information, see [Uninstall the Intune Connector for Active Directory](../../windows-autopilot-hybrid#uninstall-the-intune-connector-for-active-directory).

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

## Next step: Increase the computer account limit in the Organizational Unit (OU)