---
layout: Conceptual
title: Windows Autopilot user-driven Microsoft Entra hybrid join - Step 2 of 10 - Install the Intune Connector for Active Directory | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/user-driven/hybrid-azure-ad-join-intune-connector
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
description: How to - Windows Autopilot user-driven Microsoft Entra hybrid join - Step 2 of 10 - Install the Intune Connector for Active Directory.
ms.date: 2025-05-29T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: e96ba3fe-0f09-9cd5-77ff-d18daf124ce1
document_version_independent_id: e96ba3fe-0f09-9cd5-77ff-d18daf124ce1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/user-driven/hybrid-azure-ad-join-intune-connector.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/user-driven/hybrid-azure-ad-join-intune-connector
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/user-driven/hybrid-azure-ad-join-intune-connector.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: c6c91827-d58d-9ba1-c38c-ed9be5952ea7
---

# Windows Autopilot user-driven Microsoft Entra hybrid join - Step 2 of 10 - Install the Intune Connector for Active Directory | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)

- **Step 2: Install the Intune Connector for Active Directory**

- Step 3: [Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit)
- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Deploy the device](hybrid-azure-ad-join-deploy-device)

For an overview of the Windows Autopilot user-driven Microsoft Entra hybrid join workflow, see [Windows Autopilot user-driven Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

Note

If the Intune Connector for Active Directory is already installed and configured, skip this step and move on to [Step 3: Increase the computer account limit in the Organizational Unit (OU)](hybrid-azure-ad-join-computer-account-limit).

## Install the Intune Connector for Active Directory

The **Intune Connector for Active Directory**, also known as the Offline Domain Join (ODJ) Connector, joins computers to an on-premises domain during the Windows Autopilot process. The connector creates computer objects in a specified Organizational Unit (OU) in Active Directory during the domain join process.

Important

Intune Connector for Active Directory versions older than 6.2501.2000.5 are deprecated and can no longer process enrollment requests. For more information, see the [Intune Connector for Active Directory with low-privileged account for Windows Autopilot Hybrid Microsoft Entra join deployments](https://aka.ms/Intune-Connector-blog) blog post.

To update the connector, you must:

1. Manually uninstall the legacy connector. There isn't an automatic option.
2. Download and install the updated connector, as described in this article.

Tip

If you use multiple domains to enroll Autopilot devices:

- You need a separate connector instance for each domain. A connector can only process enrollment requests for the same domain as the server it was installed on.
- There can be at most one connector per server, whether virtual machine or physical. You can set up more servers per domain for redundancy, each with its own connector installed. In that setup, if one connector fails, the requests go to another connector on another server in the same domain.

Select the tab that corresponds to the version of the Intune Connector for Active Directory that you want to install:

# [Updated Connector](#tab/updated-connector)
#### Before you begin

- Before you install, ensure that you meet the [Intune connector for Active Directory server requirements](/en-us/autopilot/windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements).
- Microsoft recommends (but doesn't require) that the administrator who installs and configures the Intune Connector for Active Directory has the domain rights listed in [Intune Connector for Active Directory requirements](../../windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements). These rights allow the Intune Connector for Active Directory installer and configuration process to set permissions for the Managed Service Account (MSA) on the **Computer** container or OUs where computer objects are created.

    If the administrator lacks these permissions, another administrator with the appropriate rights must [Increase the computer account limit in the Organizational Unit (OU)](../../windows-autopilot-hybrid?tab=updated-connector#increase-the-computer-account-limit-in-the-organizational-unit).

#### Turn off Internet Explorer Enhanced Security Configuration

Starting with version **6.2504.2001.8**, the updated Intune Connector for Active Directory switched to using WebView2, built on Microsoft Edge, instead of WebBrowser, built on Microsoft Internet Explorer. This change means that you no longer need to turn off the Internet Explorer Enhanced Security Configuration setting in Windows Server. Make sure to install version **6.2504.2001.8** or later of the Intune Connector for Active Directory to avoid issues with the Internet Explorer Enhanced Security Configuration setting.

#### Download the Intune Connector for Active Directory

1. On the server where you're installing the Intune Connector for Active Directory, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. In the **Home** screen, in the left pane, select **Devices**.
3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Intune Connector for Active Directory**.
6. In the **Intune Connector for Active Directory** screen, select **Add**.
7. In the **Add connector** window, under **Configuring the Intune Connector for Active Directory**, select **Download the on-premises Intune Connector for Active Directory**. The link downloads a file called `ODJConnectorBootstrapper.exe`.

#### Install the Intune Connector for Active Directory on the server

Important

You need to install the Intune Connector for Active Directory with an account that has the following domain rights:

- **Required**: Create **msDs-ManagedServiceAccount** objects in the Managed Service Accounts container.
- **Optional**: Modify permissions in OUs in Active Directory. If the administrator who installs the updated Intune Connector for Active Directory doesn't have this right, an administrator who has these rights needs to perform additional configuration steps. For more information, see the section **Increase the computer account limit in the Organizational Unit**.

1. Sign in to the server where you're installing the Intune Connector for Active Directory with an account that has local administrator rights.
2. If the previous legacy Intune Connector for Active Directory is installed, uninstall it before you install the updated Intune Connector for Active Directory. For more information, see [Uninstall the Intune Connector for Active Directory](../../windows-autopilot-hybrid#uninstall-the-intune-connector-for-active-directory).

    Important

    When you uninstall the previous legacy Intune Connector for Active Directory, ensure you run the legacy **Intune Connector for Active Directory** installer as part of the uninstall process. If the legacy Intune Connector for Active Directory installer prompts to **Uninstall** it when it runs, select to uninstall it. This step ensures that the previous legacy Intune Connector for Active Directory is fully uninstalled. You can download the legacy Intune Connector for Active Directory installer from [Intune Connector for Active Directory](https://www.microsoft.com/download/details.aspx?id=105392&amp;msockid=3cb707200c316b2c119712450d8b6a5d).

    Tip

    In domains with only a single Intune Connector for Active Directory, Microsoft recommends first installing the updated Intune Connector for Active Directory on another server. You should install the updated Intune Connector for Active Directory on another server before you uninstall the legacy Intune Connector for Active Directory on the current server. By installing the Intune Connector for Active Directory on another server first, you avoid any downtime while the Intune Connector for Active Directory is updating on the current server.
3. Open the `ODJConnectorBootstrapper.exe` file that you downloaded to launch the **Intune Connector for Active Directory Setup** install.
4. Step through the **Intune Connector for Active Directory Setup** install.
5. At the end of the install, select **Launch Intune Connector for Active Directory**.

    Note

    If you accidentally close **Intune Connector for Active Directory Setup** install without selecting **Launch Intune Connector for Active Directory**, you can reopen the **Intune Connector for Active Directory** configuration by selecting **Intune Connector for Active Directory** &gt; **Intune Connector for Active Directory** from the **Start** menu.

#### Sign in to the Intune Connector for Active Directory

1. In **Intune Connector for Active Directory**, under the **Enrollment** tab, select **Sign In**.
2. In the **Sign In** tab, sign in with the Microsoft Entra ID credentials of an Intune administrator role. The user account must have an assigned Intune license. The sign in process might take a few minutes to complete.

    Note

    The account you use to enroll the Intune Connector for Active Directory is only a temporary requirement at the time of installation. The account isn't used going forward after the server is enrolled.
3. After the sign in process completes:

    1. **The Intune Connector for Active Directory successfully enrolled** confirmation window appears. Select **OK** to close the window.
    2. **A Managed Service Account with name "&lt;MSA\_name&gt;" was successfully set up** confirmation window appears. The name of the MSA is in the format `msaODJ#####`, where **#####** are five random characters. Note the name of the MSA that was created, and then select **OK** to close the window. You might need the name of the MSA later to configure the MSA to allow creating computer objects in OUs.

    The **Enrollment** tab shows **Intune Connector for Active Directory is enrolled**. The **Sign In** button is greyed out and **Configure Managed Service Account** is enabled.
4. Close the **Intune Connector for Active Directory** window.

#### Verify the Intune Connector for Active Directory is active

After you authenticate, the Intune Connector for Active Directory finishes installing. When the installation finishes, verify that it's active in Intune by following these steps:

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) if it's still open. If the **Add connector** window is still displayed, close it.

    If the **Microsoft Intune admin center** isn't still open:

    1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
    2. In the **Home** screen, in the left pane, select **Devices**.
    3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
    4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
    5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Intune Connector for Active Directory**.
2. In the **Intune Connector for Active Directory** page:

    - Confirm that the server is displayed under **Connector name** and shows as **Active** under **Status**.
    - For the updated Intune Connector for Active Directory, make sure the version is greater than or equal to **6.2501.2000.5**.

    If the server isn't displayed, select **Refresh** or navigate away from the page, and then go back to the **Intune Connector for Active Directory** page.

Note

- It can take several minutes for the newly enrolled server to appear in the **Intune Connector for Active Directory** page of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). The enrolled server only appears if it can successfully communicate with the Intune service.
- Inactive Intune Connectors for Active Directory still appear in the **Intune Connector for Active Directory** page and is automatically cleaned up after 30 days.

After you install the Intune Connector for Active Directory, it starts logging in the **Event Viewer** under the path **Applications and Services Logs** &gt; **Microsoft** &gt; **Intune** &gt; **ODJConnectorService**. Under this path, you can find **Admin** and **Operational** logs.

#### Configure the MSA to allow creating objects in OUs (optional)

By default, MSAs only have access to create computer objects in the **Computers** container. MSAs don't have access to create computer objects in Organizational Units (OUs). To allow the MSA to create objects in OUs, you need to add the OUs to the `ODJConnectorEnrollmentWizard.exe.config` XML file found in `ODJConnectorEnrollmentWizard` directory where you installed Intune Connector for Active Directory, normally `C:\Program Files\Microsoft Intune\ODJConnector\`.

To configure the MSA to allow creating objects in OUs, follow these steps:

1. On the server where the Intune Connector for Active Directory is installed, navigate to the `ODJConnectorEnrollmentWizard` directory where the Intune Connector for Active Directory is installed, normally `C:\Program Files\Microsoft Intune\ODJConnector\`.
2. In the `ODJConnectorEnrollmentWizard` directory, open the existing `ODJConnectorEnrollmentWizard.exe.config` XML file in a text editor, such as **Notepad**.
3. In the `add key` element of the `ODJConnectorEnrollmentWizard.exe.config` XML file:

    - Next to `value=`, add any desired OUs that the MSA should have access to create computer objects in.
    - The OU name needs to be in the [LDAP distinguished name](/en-us/previous-versions/windows/desktop/ldap/distinguished-names) format and if applicable, needs to be escaped.
    - Separate multiple OUs with a semicolon (;).
    - Retain the quotes (") next to `value=`. All of the OU values need to be in one pair of quotes.
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

    In the following example, replace the example red text next to `value=` with your organization's OUs in [LDAP distinguished name format](/en-us/previous-versions/windows/desktop/ldap/distinguished-names). As shown in the example, ensure all OU entries are within the quotes (") and that each OU is separated with a semicolon (;).
4. After you add all desired OUs, save the `ODJConnectorEnrollmentWizard.exe.config` XML file.
5. As an administrator with appropriate permissions to modify OU permissions, open the **Intune Connector for Active Directory** by going to **Intune Connector for Active Directory** &gt; **Intune Connector for Active Directory** from the **Start** menu.

    Important

    If the administrator installing and configuring the Intune Connector for Active Directory doesn't have permissions to modify OU permissions, an administrator who has permissions to modify OU permissions needs to follow the steps in **Increase the computer account limit in the Organizational Unit**.
6. In the **Enrollment** tab in the **Intune Connector for Active Directory** window, select **Configure Managed Service Account**.
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
- Service account needs to have local **Log On as a Service** permission which could be set directly or by group membership. For more information, see [Enable service logon](/en-us/system-center/scsm/enable-service-log-on-sm).
- Permission needs to be granted manually for service accounts to create computer objects for hybrid Autopilot flows. For more information, see [Increase the computer account limit in the Organizational Unit (OU)](/en-us/autopilot/tutorial/user-driven/hybrid-azure-ad-join-computer-account-limit?tabs=updated-connector).

##### How to set up

Update `ODJConnectorEnrollmentWizard.exe.config`. Its default location is `C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorEnrollmentWizard`.

1. In the **appSettings section** of the file, add the following line:

    `<add key="TenantConfiguredManagedServiceAccount" value="{accountname}" />`
2. Sign in to the connector.

##### Disable OU updates

If you use your own MSA, the connector doesn't make any OU updates, even if you configure `OrganizationalUnitsUsedForOfflineDomainJoin`. To prevent errors, disable OU updates by updating `ODJConnectorEnrollmentWizard.exe.config`. The default location is `C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorEnrollmentWizard`.

1. In the **appSettings section** of the file, add the following line:

    `<add key="DisableOUUpdates" value="true" />`
2. Sign in to the connector.

# [Legacy Connector](#tab/legacy-connector)
Important

The legacy Intune Connector for Active Directory is deprecated. These instructions assume that the legacy Intune Connector for Active Directory is already installed or downloaded. If you don't have the legacy Intune Connector for Active Directory installer, you can download it from [Intune Connector for Active Directory](https://www.microsoft.com/download/details.aspx?id=105392&amp;msockid=3cb707200c316b2c119712450d8b6a5d).

However, best practice is to download and install the updated Intune Connector for Active Directory. For more information, select **Updated Connector** instead.

Before you begin the installation, make sure that you meet all of the [Intune connector for Active Directory server requirements](/en-us/autopilot/windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements).

#### Disable Internet Explorer Enhanced Security Configuration

By default, Windows Server has Internet Explorer Enhanced Security Configuration turned on. Internet Explorer Enhanced Security Configuration might cause problems signing in to the Intune Connector for Active Directory. Because Internet Explorer is deprecated and in most instances, not even installed on Windows Server, Microsoft recommends turning off Internet Explorer Enhanced Security Configuration. To turn off Internet Explorer Enhanced Security Configuration:

1. Sign in to the server where you're installing the Intune Connector for Active Directory with an account that has local administrator rights and domain admin rights. You need domain admin rights so the Intune Connector for Active Directory installer can properly create an MSA.
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

    If you want to install in a location other than the default of **C:\Program Files\Microsoft Intune\ODJConnector**, select **Options** and specify the desired install location.
3. When the install finishes, select **Configure Now** in the **Intune Connector for Active Directory Setup** installer window.

    Note

    If you accidentally select **Close** or close the **Intune Connector for Active Directory Setup** installer window, you can access the **Intune Connector for Active Directory** configuration by selecting **Intune Connector for Active Directory** &gt; **Intune Connector for Active Directory** from the **Start** menu.

#### Sign in to the legacy Intune Connector

1. In the **Intune Connector for Active Directory** window, under **Enrollment**, select **Sign In**.
2. In the **Sign In** tab, sign in with the credentials of an Intune administrator role. The user account must have an assigned Intune license. The sign in process might take a few minutes to complete.

    Note

    The account used to enroll the Intune Connector for Active Directory is only a temporary requirement at the time of installation. The account isn't used going forward after the server is enrolled.
3. After you sign in, a **The Intune Connector for Active Directory successfully enrolled** confirmation window appears. Select **OK** to close the window.

    The **Enrollment** tab shows **Intune Connector for Active Directory is enrolled** and the **Sign In** button is greyed out.
4. Close the **Intune Connector for Active Directory** window.

#### Verify the legacy Intune Connector for Active Directory is active

After authenticating, the Intune Connector for Active Directory finishes installing. After it finishes installing, verify that it's active in Intune by following these steps:

1. Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) if it's still open. If the **Add connector** window is still displayed, close it.

    If the **Microsoft Intune admin center** isn't still open:

    1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
    2. In the **Home** screen, in the left pane, select **Devices**.
    3. In the **Devices | Overview** screen, under **By platform**, select **Windows**.
    4. In the **Windows | Windows devices** screen, under **Device onboarding**, select **Enrollment**.
    5. In the **Windows | Windows enrollment** screen, under **Windows Autopilot**, select **Intune Connector for Active Directory**.
2. In the **Intune Connector for Active Directory** page, confirm that the server is displayed under **Connector name** and shows as **Active** under **Status**. If the server isn't displayed, select **Refresh** or navigate away from the page, and then go back to the **Intune Connector for Active Directory** page.

Note

- It can take several minutes for the newly enrolled server to appear in the **Intune Connector for Active Directory** page of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). The enrolled server only appears if it can successfully communicate with the Intune service.
- Inactive Intune Connectors for Active Directory still appear in the **Intune Connector for Active Directory** page and are automatically cleaned up after 30 days.

After the Intune Connector for Active Directory is installed, it starts logging in the **Event Viewer** under the path **Applications and Services Logs** &gt; **Microsoft** &gt; **Intune** &gt; **ODJConnectorService**. Under this path, you can find **Admin** and **Operational** logs.

---

## Next step: Increase the computer account limit in the Organizational Unit (OU)