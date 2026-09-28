---
layout: Conceptual
title: Technical preview 2106 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2106
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2106.
ms.date: 2021-06-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 769dc0c8-1b9e-7076-7505-86d292cce9e0
document_version_independent_id: 291dde75-1841-1df2-a417-cc3f26c8bb2d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2021/technical-preview-2106.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2021/technical-preview-2106
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2021/technical-preview-2106.md
platformId: b328b54c-d743-2930-33e0-23bf861486d1
---

# Technical preview 2106 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2106. Install this version to update and add new features to your technical preview site. When you install a new technical preview site, this release is also available as a baseline version.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Intune role-based access control for tenant attach

You can use Intune role-based access control (RBAC) when displaying the **Client details** page for [tenant attached devices](../../../tenant-attach/device-sync-actions) in the Microsoft Intune admin center. When using Intune as the RBAC authority, a user with the [Help Desk Operator role](../../../../fundamentals/role-based-access-control/overview#built-in-roles) doesn't need an assigned security role or additional permissions from Configuration Manager. Currently, the Help Desk Operator role can display only the **Client details** page without additional Configuration Manager permissions.

![Screenshot of the CoMgmtSettingsProd properties showing the Configure upload tab](media/8126836-intune-rbac.png)

To use Intune role-based access control for tenant attach, use the instructions below:

1. From the Configuration Manager console, go to, **Administration** &gt; **Cloud Services** &gt; **Cloud Attach**.
2. If you already have tenant attach enabled, open the properties for **CoMgmtSettingsProd**. If you don't have tenant attach enabled, select **Configure Cloud Attach** to open the **Cloud Attach Configuration wizard**.
3. On the **Configure upload** tab (or page in the wizard), enable the following option under the **Role-based Access Control** heading:

    **Use Intune role-based access control (RBAC) when you view Configuration Manager devices and take action in Microsoft Intune admin center**
4. Choose **OK** to save the change to the **CoMgmtSettingsProd** properties, or continue on with the wizard to finish enabling tenant attach.

Open the **Admin Center Preview** to verify the the Help Desk Operator can see **Client details**:

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace and select the **Devices** node.
2. Right-click on a device that's been uploaded to Microsoft Intune.
3. In the right-click menu, select **Start** &gt; **Admin Center Preview**to open the preview in your browser.
    - This launch is a preview experience. The final location will be in Microsoft Intune admin center.
4. Sign in to the Microsoft Intune admin center as a user that has the Help Desk Operator role.
5. Display the **Client details** page.

### Known issues

For this technical preview, an Intune RBAC check always occurs for the Help Desk Operator for all tenant attach actions, not just for **Client details**. If the Intune RBAC option isn't enabled and the Help Desk Operator doesn't have permissions from Configuration Manager, the incoming request from the Intune console will be rejected.

A Help Desk Operator without permissions in Configuration Manager will only see the **Client details** page. When the Help Desk Operator has permissions in Configuration Manager, they can access other tenant attach actions, such as CMPivot and Timeline.

## Convert a CMG to virtual machine scale set

Starting in current branch version 2010, you could deploy the cloud management gateway (CMG) with a virtual machine scale set in Azure. This support was primarily to unblock customers with a Cloud Solution Provider (CSP) subscription.

In this release, any customer with a CMG that uses the classic cloud service deployment can convert to a virtual machine scale set.

Tip

This process reuses the underlying storage account.

When you convert a CMG, you can't change all settings:

| Setting | Changeable |
| --- | --- |
| Azure environment | ![](media/red-x.png) |
| Subscription | ![](media/red-x.png) |
| Microsoft Entra app | ![](media/red-x.png) |
| Region | ![](media/red-x.png) |
| Resource group | ![](media/red-x.png) |
| VM size ^Note^ | ![](media/green-check.png) |
| VM instances | ![](media/green-check.png) |
| Verify CRL | ![](media/green-check.png) |
| Require TLS | ![](media/green-check.png) |
| Serve content | ![](media/green-check.png) |

To make changes that the conversion process doesn't support, you need to [Redeploy the service](../../clients/manage/cmg/modify-cloud-management-gateway).

Note

Starting in technical preview branch version 2105, you could [select the VM size for a CMG](technical-preview-2105#bkmk_cmgsize). In this release, the **Large** option is now the **A4\_V2** VM size. This change is based on performance testing and VM cost consideration.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Cloud Management Gateway** node.
2. Select a CMG instance whose **Status** is *Ready*. In the ribbon, select **Convert**. This action opens the Convert CMG wizard.
3. On the General page, select **Next**. You can't change any of these settings.
4. On the Settings page, note the new *Deployment name* with the suffix for the virtual machine scale set.
5. Make other configuration changes as needed. Then select **Next** and complete the wizard.

Monitor the conversion process the same as a new deployment. For example, view the state in the console, and review **cloudmgr.log**. For more information, see [Monitor CMG](../../clients/manage/cmg/monitor-clients-cloud-management-gateway#monitor-logs).

### Update or create a DNS CNAME

Since the deployment name changed, you need to update or create a DNS canonical name record (CNAME). This alias maps the service name to the deployment name. For more information, see [Create a DNS CNAME alias](../../clients/manage/cmg/server-auth-cert#create-a-dns-cname-alias).

For example,

- The CMG's *service name* is either `GraniteFalls.contoso.com` or `GraniteFalls.cloudapp.net`, which typically depends upon the [certificate type](../../clients/manage/cmg/server-auth-cert#summary-comparison-of-certificate-types).
- For the *deployment name*,
    - Classic: `GraniteFalls.cloudapp.net`
    - Virtual machine scale set: `GraniteFalls.EastUS.CloudApp.Azure.Com`

## Implicit uninstall of applications

Many customers have lots of collections because for every application they need at least two collections: one for install and another for uninstall. This practice adds overhead of managing more collections, and can reduce site performance for collection evaluation.

Starting in this release, you can enable an application deployment to support implicit uninstall. If a device is in a collection, the application installs. Then when you remove the device from the collection, the application uninstalls.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. [Add a device to a collection](../../clients/manage/manage-clients#add-selected-items). This action typically involves creating a direct membership rule for the device.
2. [Deploy an application](../../../apps/deploy-use/deploy-applications) to that device collection.
3. On the Deployment Settings page of the Deploy Software Wizard, configure the following options:

    - **Action**: Install
    - **Purpose**: Required
    - Enable **Uninstall this application if the targeted object falls out of the collection**
4. Complete the Deploy Software Wizard.
5. [Download computer policy](../../clients/manage/manage-clients#start-policy-retrieval) on the device. Because it's a required deployment, the client installs the app. You can use Software Center to view the installation status. For more information, see the [Software Center user guide](../../understand/software-center#applications).
6. Remove the device from the collection. This action typically involves removing the direct membership rule for the device from the [collection properties](../../clients/manage/collections/manage-collections#collection-properties).

After you remove the device from the collection, the following process happens:

- A background worker process runs on the site server every 10 minutes. This task keeps track of apps for which you've enabled this option. It then detects devices that you removed from the target collection. To help you troubleshoot this process, view the **SMS\_ImplicitUninstall.log** file on the site server.
- The client needs to download computer policy. By default, the [client policy polling interval](../../clients/deploy/about-client-settings#client-policy) client setting is 60 minutes. To accelerate this step, manually [Download computer policy](../../clients/manage/manage-clients#start-policy-retrieval).
- 15 minutes after the client receives the updated policy, it uninstalls the app.

Depending upon the timing of those steps, the longest time period for the client to uninstall the app is 85 minutes. If the first step happens immediately, and you manually download computer policy on the device, the overall process is 15 minutes.

## Microsoft .NET requirements

Configuration Manager now requires Microsoft .NET Framework version 4.6.2 for site servers, specific site systems, clients, and the console. Before you run setup to install or update the site, first update .NET and restart the system. If possible in your environment, install the latest version of .NET version 4.8.

Note

.NET Framework version 4.6.2 is preinstalled with Windows Server 2016 and Windows 10 version 1607. Later versions of Windows are preinstalled with a later version of the .NET Framework.

.NET Framework version 4.8 isn't supported on some OS versions, such as Windows 10 2015 LTSB.

For more information, see [.NET Framework system requirements](/en-us/dotnet/framework/get-started/system-requirements).

### Site server

If the site server doesn't have any collocated roles that require .NET, it still requires .NET, but setup doesn't automatically install it. Make sure the site server itself has at least .NET version 4.6.2, but install .NET 4.8 if possible.

### Site systems

During Configuration Manager setup, if site systems have a version earlier than 4.6.2, you'll see a prerequisite check warning. This check is a warning instead of an error, because setup will install version 4.6.2. When .NET updates, it usually requires Windows to restart. Site systems will send status message 4979 when a restart is required. Configuration Manager suppresses the restart; the system doesn't restart automatically.

The behavior will differ for different types of site roles that require .NET:

- The following site system roles support in-place upgrade of .NET. After upgrading .NET, if a restart is required, it sends status message 4979. The role keeps running with the earlier .NET version. After Windows restarts, the role starts using the new .NET version.

    - Asset Intelligence synchronization point
    - Management point
    - Service connection point
    - Data warehouse service point
- The following site systems roles uninstall and reinstall when .NET is upgraded. During site update, site component manager removes the role, and then updates .NET. If a restart is required, it sends status message 4979. After restart, site component manager reinstalls the role with the new .NET version. The role could be unavailable while it waits for you to restart the server.

    - SMS Provider for the administration service
    - Certificate registration point
    - Enrollment point
    - Enrollment proxy point
    - Reporting services point
    - Software update point

Note

Currently, you still need to enable the Windows feature for .NET Framework 3.5 on [site systems that require it](../../plan-design/configs/site-and-site-system-prerequisites).

If site systems have at least version 4.6.2 but earlier than version 4.8, you'll also see a prerequisite check warning. We recommend that you install the latest version of .NET version 4.8 to get the latest performance and security improvements. Configuration Manager setup doesn't automatically install .NET version 4.8. A later version of Configuration Manager will require .NET version 4.8.

There's also a new [management insight](../../servers/manage/management-insights) to recommend site systems that don't yet have .NET version 4.8 or later.

### Configuration Manager clients

When you install or update the Configuration Manager client, if the device doesn't have at least .NET version 4.6.2, CCMSetup installs it. CCMSetup suppresses a restart if necessary, and the user will see a Windows notification to restart. .NET version 4.8 is recommended on clients also.

### Configuration Manager console

The Configuration Manager console also requires .NET version 4.6.2, but version 4.8 is recommended. If you install the console on other devices, make sure to update .NET. If the device isn't compliant, the console setup doesn't install this prerequisite.

Note

The ConfigurationManager PowerShell module that installs with the console requires .NET version 4.7.2 or later.

## Audit mode for potentially unwanted applications

An **Audit** option for [potentially unwanted applications (PUA)](/en-us/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) was added in the **Antimalware policy** settings. Use PUA protection in audit mode to detect potentially unwanted applications without blocking them. PUA protection in audit mode is useful if your company is conducting an internal software security compliance check and you'd like to avoid any false positives.

To use the **Audit** option for potentially unwanted applications:

1. Go to **Assets and Compliance** &gt; **Endpoint Protection** &gt; **Antimalware policy**.
2. Choose the set of antimalware policies you want to change, or create a new custom antimalware policy.
3. Select the [**Real-time protection**](../../../protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) settings page.
4. Set the **Configure detection for potentially unwanted applications** setting to **Audit**.

## External notifications

In a complex IT environment, you may have an automation system like [Azure Logic Apps](/en-us/azure/logic-apps/logic-apps-overview). Customers use these systems to define and control automated workflows to integrate multiple systems. You could integrate Configuration Manager into a separate automation system through the product's SDK APIs. But this process can be complex and challenging for IT professionals without a software development background.

Starting in this release, you can enable the site to send notifications to an external system or application. This feature simplifies the process by using a web service-based method. You configure [subscriptions](../../servers/manage/configure-alerts) to send these notifications. These notifications are in response to specific, defined events as they occur. For example, [status message filter rules](../../servers/manage/use-status-system#manage-status-filter-rules).

Note

The external system or application defines and provides the methods that this feature calls.

When you set up this feature, the site opens a communication channel with the external system. That system can then start a complex workflow or action that doesn't exist in Configuration Manager.

These notifications use the following standardized schema:

```json
{
    "properties": {
        "EventID": {
            "type": "integer"
        },
        "EventName": {
            "type": "string"
        },
        "EventPayload": {
            "type": "string"
        },
        "MessageID": {
            "type": "string"
        },
        "ServerName": {
            "type": "string"
        },
        "SiteCode": {
            "type": "string"
        },
        "Source": {
            "type": "string"
        }
    },
    "type": "object"
}
```

### Prerequisites for external notifications

- The site's service connection point needs to be in online mode. For more information, see [About the service connection point](../../servers/deploy/configure/about-the-service-connection-point).
- Currently, this feature only supports Azure Logic Apps as the external system. An active Azure subscription with rights to create a logic app is required.
- The **Full administrator** security role with **All** security scope in Configuration Manager.
- In this release, to create the objects in Configuration Manager, you need to use the PowerShell script **SetupExternalServiceNotifications.ps1**. Use the following script sample to properly get the PowerShell script to use for this feature:

    ```powershell
    $FileName = ".\SetupExternalServiceNotifications.ps1"
    Invoke-WebRequest https://aka.ms/cmextnotificationscript -OutFile $FileName
    (Get-Content $FileName -Raw).Replace("`n","`r`n") | Set-Content $FileName -Force
    (Get-Content $FileName -Raw).TrimEnd("`r`n") | Set-Content $FileName -Force
    ```

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

#### Create an Azure logic app and workflow

Create an app in Azure Logic Apps to receive the notification from Configuration Manager.

1. Sign in to the [Azure portal](https://portal.azure.com).
2. In the Azure search box, enter `logic apps`, and select **Logic Apps**.
3. Select **Add** and choose **Consumption**. This action creates a new logic app.
4. On the **Basics** tab, specify the project details as necessary for your environment: subscription name, resource group, logic app name, and region.
5. Select **Review + create**. On the validation page, confirm the details that you provided, and select **Create**.
6. Under **Next steps**, select **Go to resource**.
7. Under the section to **Start with a common trigger**, select **When a HTTP request is received**.
8. At the bottom of the trigger editor, select **Use sample payload to generate schema**.
9. Paste the following sample schema:

    ```json
    {
        "EventID":0,
        "EventName":"",
        "SiteCode":"",
        "ServerName":"",
        "MessageID":0,
        "Source":"",
        "EventPayload":""
    }
    ```
10. Select **Done** and then select **Save**.
11. Copy the generated URL for the logic app. You'll use this URL later.
12. To add a new step in the designer, select **+ New Step**. Choose an appropriate action when it receives a notification from Configuration Manager. For example:

    - To send an email, use the [Office 365 Outlook connector](/en-us/azure/connectors/connectors-create-api-office365-outlook).
    - To post a message to Teams, use the [Microsoft Teams connector](/en-us/connectors/teams/).

    Sign in if necessary and complete the required information for the action. For more information, see the [Create logic apps](/en-us/azure/logic-apps/quickstart-create-first-logic-app-workflow#add-an-action) quickstart in the Azure Logic Apps documentation.

#### Subscribe to events and create a sample event in Configuration Manager

There are two types of events that are currently supported:

- The site raises a status message that matches conditions specified in a status filter rule.
- A user requests approval for an application in Software Center.

##### Status message

1. On the site server, run **SetupExternalServiceNotifications.ps1**. Since you're running it on the site server, enter `y` to continue.
2. Select option `2` to create a new status filter rule.
3. Specify a name for the new status filter rule.
4. Select message-matching criteria for the rule, and specify values to match. Specify `0` to not use a criterion. For this example, select `0` for all criteria except **Component**. Select the number for the **SMS\_REST\_PROVIDER** component, which varies per site.

    The following criteria are available:

    - **Source**: Client, SMS Provider, Site Server
    - **Site code**
    - **System**
    - **Component**
    - **Message type**: Milestone, Detail, Audit
    - **Severity**: Informational, Warning, Error
    - **Message ID**
    - **Property**
    - **Property value**

    Tip

    For more information about criteria for status message rules, see [Use the status system](../../servers/manage/use-status-system).
5. Rerun the PowerShell script. Select option `3` to create a new subscription.
6. Specify a name and description for the subscription. Then specify the logic app URL that you previously copied from the Azure portal.
7. Select the new status filter rule.
8. Select `0` to exit the script.
9. Trigger an event for the site component you chose for the status filter rule. For example, use the [Configuration Manager Service Manager](../../servers/deploy/configure/site-components#configuration-manager-service-manager) to restart the **SMS\_REST\_PROVIDER** component. You can also wait for the component to send a regular health status message.

##### App approval

Note

This event type requires a application that requires approval and is deployed to a user collection. For more information, see [Deploy applications](../../../apps/deploy-use/deploy-applications) and [Approve applications](../../../apps/deploy-use/app-approval).

1. On the site server, run **SetupExternalServiceNotifications.ps1**. Since you're running it on the site server, enter `y` to continue.
2. Select option `3` to create a new subscription.
3. Specify a name and description for the subscription. Then specify the logic app URL that you previously copied from the Azure portal.
4. Select the appropriate event for an application request.
5. Select `0` to exit the script.
6. On a managed device, submit an app approval request from Software Center. For more information, see [Software Center user guide](../../understand/software-center#install-an-application).

#### Monitor the workflow

Within five minutes, the event triggers the logic app workflow. Check the status of the workflow in the Azure portal. Navigate to the **Runs history** page of the logic app.

For more information, see [Monitor run status, review trigger history, and set up alerts for Azure Logic Apps](/en-us/azure/logic-apps/monitor-logic-apps).

#### Troubleshooting logs

Use the following Configuration Manager log files on the site server to help troubleshoot this process:

- **ExternalNotificationsWorker.log**: Check if the queue has been processed and notifications are sent to external system.
- **statmgr.log**: Check if the status filter rules have been processed without errors

### Known issue with external notifications

If you create a status filter rule, you'll see it in the site's list of **Status filter rules** in the Configuration Manager console. If you make a change on the **Actions** tab of the rule properties, the external notification won't work.

### Script usage

When you run **SetupExternalServiceNotifications.ps1**, it detects whether it's running on a site server:

- `Y`: Continue on the current server
- `N`: Specify the FQDN of a site server to use

If the script doesn't detect a site server, it prompts for an FQDN.

The following actions are then available:

- `0`: Skip/continue
- `1`: List available subscriptions
- `2`: Create a status filter rule to expose status messages
- `3`: Create a subscription. This option is only available for the top-level site.

Note

This script is only supported for sites running version 2106 or later.

## List additional third-party updates catalogs

To help you find custom catalogs that you can import for third-party software updates, there's now a documentation page with links to catalog providers. Choose **More Catalogs** from the ribbon in the **Third-party software update catalogs** node. Right-clicking on **Third-Party Software Update Catalogs** node also displays a **More Catalogs** menu item. Selecting **More Catalogs** opens a link to a documentation page containing a [list of additional third-party software update catalog providers](../../../sum/deploy-use/third-party-software-update-catalogs).

![Screenshot of the Third-Party Software Update Catalogs node with the More Catalogs icon in the ribbon](media/9989251-more-catalogs.png)

## Management insights rule for TLS/SSL software update points

[Management insights](../../servers/manage/management-insights) has a new rule to detect if your software update points are [configured to use TLS/SSL](../../../sum/get-started/software-update-point-ssl). To review the **Configure software update points to use TLS/SSL** rule, go to **Administration** &gt; **Management Insights** &gt; **All Insights** &gt; **Software Updates**.

## Renamed Co-management node to Cloud Attach

To better reflect the other cloud services Configuration Manager offers, the **Co-management** node has been renamed to the **Cloud Attach** node. Other changes you may notice include the ribbon button being renamed from **Configure Co-management** to **Configure Cloud Attach** and the **Co-management Configuration Wizard** was renamed to **Cloud Attach Configuration Wizard**.

![Screenshot showing the Cloud Attach node, the Configure Cloud attach ribbon button, and the Cloud Attach Configuration Wizard.](media/10158821-cloud-attach-node.png)

## Improvements for managing automatic deployment rules

The following items were added to help you better manage your automatic deployment rules:

### Updated Product parameter for New-CMSoftwareUpdateAutoDeploymentRule cmdlet

The `-Product` parameter for `New-CMSoftwareUpdateAutoDeploymentRule` was updated. When there are multiple products with the same name, `-Product` now selects all of them.

### Script to apply deployment package settings for automatic deployment rule

If you create an ADR with the **No deployment package** option, you're' unable to go back and add one later. To help you resolve this issue, we've uploaded the following script into [Community hub](../../servers/manage/community-hub):

Tip

For more information, see [Direct links to Community hub items](../../servers/manage/community-hub).

```powershell
<# Apply-ADRDeploymentPackageSettings #>

#=============================================
# START SCRIPT
#=============================================
param
(
[parameter(Mandatory = $true)]
[ValidateNotNullOrEmpty()]
[string]$sourceADRName,

[parameter(Mandatory = $true)]
[ValidateNotNullOrEmpty()]
[string]$targetADRName
)

Try {
       # Source ADR that already has the needed deployment package. You may need to create one if it doesn’t exist.
       $sourceADR = Get-CMSoftwareUpdateAutoDeploymentRule -Name $sourceADRName

       # Target ADR that will be updated to use the source ADR’s deployment package. Typically, this is the ADR that used the “No deployment package” option. 
       $targetADR = Get-CMSoftwareUpdateAutoDeploymentRule -Name $targetADRName

       # Apply the deployment package settings
       $targetADR.ContentTemplate = $sourceADR.ContentTemplate

       # Update the wmi object
       $targetADR.Put()
}
Catch{
       $exceptionDetails = "Exception: " + $_.Exception.Message + "HResult: " + $_.Exception.HResult
       Write-Error "Failed to apply ADR deployment package settings: $exceptionDetails"
}

#=============================================
```

## New prerequisite check for SQL Server 2012

When you install or update the site, it now warns for the presence of SQL Server 2012. The [support lifecycle](/en-us/lifecycle/products/microsoft-sql-server-2012) for SQL Server 2012 ends on July 12, 2022. Plan to upgrade database servers in your environment, including SQL Server Express at secondary sites.

## Console improvements

In this technical preview we've made the following improvements to the Configuration Manager console:

### Status message shortcuts

Shortcuts to [status messages](../../servers/manage/use-status-system) were added to the **Administrative Users** node and the **Accounts** node. Select an account, then select **Show Status Messages**.

![Screenshot of Administrative Users node with the Show Status Messages option in the ribbon.](media/8942963-show-status-messages.png)

### Navigate to collection

You can now navigate to a collection from the **Collections** tab in the **Devices** node. Select **View Collection** from either the ribbon or the right-click menu in the tab.

![Screenshot of the Collections tab in the Devices node.](media/9502958-collection.png)

### Added maintenance window column

A **Maintenance window** column was added to the **Collections** tab in the **Devices** node.

![Screenshot of the Maintenance window column for the Collections tab in the Devices node.](media/9708594-maintenance-window.png)

### Display assigned users

If a collection deletion fails due to scope assignment, the assigned users are displayed.

![Screenshot of assigned user list when collection fails to delete due to scope assignment.](media/9709014-assigned-users.png)

## Client encryption uses AES-256

Starting in this release, when you enable the site to **Use encryption**, the client uses the **AES-256** algorithm. This setting requires clients to encrypt inventory data and state messages before it sends to the management point. For more information, see [Plan for security - signing and encryption](../../plan-design/security/plan-for-security#signing-and-encryption).

Important

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

If you don't update the client to the latest version, it continues to use the 3DES algorithm.

Note

To encrypt the data, the client uses the public key of the management point's encryption certificate. Only the management point has the corresponding private key, so only it can decrypt the data.

The client bootstraps this certificate with the management point's signing certificate, which it bootstraps with the site's trusted root key. Make sure to securely provision the trusted root key on clients. For more information, see [Plan for security - the trusted root key](../../plan-design/security/plan-for-security#the-trusted-root-key).

## General known issues

### Unable to create Compliance Settings Configuration Items in the wizard

The wizard will fail when creating compliance settings configuration items through the console. As a workaround, you can use the [New-CMConfigurationItem](/en-us/powershell/module/configurationmanager/new-cmconfigurationitem) PowerShell cmdlet.

### Using Cloud Attach Configuration Wizard during upgrade fails

Don't use the **Cloud Attach Configuration Wizard** during the upgrade to 2106 technical preview. The wizard will fail to complete. Run the wizard after upgrade to 2106 technical preview is finished.

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in technical preview version 2106.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### Deprecated cmdlets

The following cmdlets are no longer available because the underlying features are no longer supported:

- Add-CMApplicationCatalogWebServicePoint
- Add-CMApplicationCatalogWebsitePoint
- Get-CMApplicationCatalogWebServicePoint
- Get-CMApplicationCatalogWebsitePoint
- Remove-CMApplicationCatalogWebServicePoint
- Remove-CMApplicationCatalogWebsitePoint
- Set-CMApplicationCatalogWebsitePoint
- Get-CMVhd
- New-CMVhd
- Remove-CMVhd
- Set-CMVhd

### Modified cmdlets

#### Add-CMTaskSequenceStep

For more information, see [Add-CMTaskSequenceStep](/en-us/powershell/module/configurationmanager/Add-CMTaskSequenceStep).

**Non-breaking changes**

Removed unnecessary parameter **StepName**.

#### Disconnect-CMTrackedObject

For more information, see [Disconnect-CMTrackedObject](/en-us/powershell/module/configurationmanager/Disconnect-CMTrackedObject).

**Non-breaking changes**

Added alias **Disconnect-CMObject** for this cmdlet.

#### New-CMSoftwareUpdateAutoDeploymentRule

For more information, see [New-CMSoftwareUpdateAutoDeploymentRule](/en-us/powershell/module/configurationmanager/New-CMSoftwareUpdateAutoDeploymentRule).

**Bugs that were fixed**

Fixed an issue to avoid duplicate product. For more information, see Improvements for managing automatic deployment rules.

#### New-CMTaskSequence

For more information, see [New-CMTaskSequence](/en-us/powershell/module/configurationmanager/New-CMTaskSequence).

**Non-breaking changes**

- Removed the **NewInstallOSImageVhd** parameter set
- Removed the **InstallOperatingSystemImageVhd** parameter

#### Set-CMDeploymentType

For more information, see [Set-CMDeploymentType](/en-us/powershell/module/configurationmanager/Set-CMDeploymentType).

**Bugs that were fixed**

Fixed an issue with the **AddRequirement** parameter to add new rules.

#### Update-CMDistributionPoint

For more information, see [Update-CMDistributionPoint](/en-us/powershell/module/configurationmanager/Update-CMDistributionPoint).

**Bugs that were fixed**

Fixed an issue to update content from both install and uninstall folders when they're different.