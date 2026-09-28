---
layout: Conceptual
title: Approve applications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/app-approval
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
description: Learn about the settings and behaviors for application approval in Configuration Manager.
ms.date: 2022-08-12T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom:
- sfi-ga-nochange
- sfi-ropc-nochange
locale: en-us
document_id: 56ff5731-8104-6514-4372-d6a0f28badb1
document_version_independent_id: 13539fef-47e2-16ce-5f6b-e3e40c64fe7d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/app-approval.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/app-approval
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/app-approval.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 92808bc6-5160-1f17-dbb5-a3df3240f534
---

# Approve applications - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When [deploying an application](deploy-applications) in Configuration Manager, you can require approval before installation. Users request the application in Software Center, and then you review the request in the Configuration Manager console. You can approve or deny the request.

Note

Starting in version 2111, you can also use most approval behaviors with [application groups](create-app-groups#app-approval).

## Approval settings

The application approval behavior depends upon whether you enable the recommended optional app approval experience. One of the following approval settings appears on the **Deployment Settings** page of the application deployment:

### An administrator must approve a request for this application on the device

Note

Configuration Manager doesn't enable this feature by default. Before using it, enable the optional feature **Approve application requests for users per device**. For more information, see [Enable optional features from updates](../../core/servers/manage/optional-features).

If you don't enable this feature, you see the prior experience.

The administrator approves any user requests for the application before the user can install it on the requested device. If the administrator approves the request, the user is only able to install the application on that device. The user must submit another request to install the application on another device. This option is grayed out when the deployment purpose is **Required**, or when you deploy the application to a device collection. 

Note

To take advantage of new Configuration Manager features, first update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

View **Application Requests** under **Application Management** in the **Software Library** workspace of the Configuration Manager console. There's a **Device** column in the list for each request. When you take action on the request, the Application Request dialog also includes the device name from which the user submitted the request.

If a request isn't approved within 30 days, it's removed. Reinstalling the client might cancel any pending approval requests.

When you require approval on a deployment to a device collection, the app isn't displayed in Software Center. If you require approval on a deployment to a user collection, the app is displayed in Software Center. You can still hide it from users with the client setting, **Hide unapproved applications in Software Center**. For more information, see [Software Center client settings](../../core/clients/deploy/about-client-settings#software-center).

After you've approved an application for installation, you can **Deny** the request in the Configuration Manager console. If users haven't already installed the application, this action stops them from installing new copies of the application from Software Center. If an application was previously approved and installed, when you **Deny** the request for the application, the client uninstalls the application from the user's device.

If you approve an app request in the console, and then deny it, you can approve it again. The app is reinstalled on the client after you approve it.

Automate the approval process with the [Approve-CMApprovalRequest](/en-us/powershell/module/configurationmanager/approve-cmapprovalrequest) PowerShell cmdlet. This cmdlet includes the **InstallActionBehavior** parameter. Use this parameter to specify whether to install the application right away or during non-business hours.

You can see which deployments require approval. Select an app in the **Applications** node. In the details pane, switch to the **Deployments** tab. There's a column displayed by default, **Requires Approval**.

#### Retry the install of pre-approved applications

You can retry the installation of an app that you previously approved for a user or device. The approval option is only for available deployments. If the user uninstalls the app, or if the initial install process fails, Configuration Manager doesn't reevaluate its state and reinstall it. This feature allows a support technician to quickly retry the app install for a user that calls for help.

1. Open the Configuration Manager console as a user that has the **Approve** permission on the Application object. For example, the **Application Administrator** or **Application Author** built-in roles have this permission.
2. Deploy an app that requires approval, and approve it.

    Tip

    Alternatively, [install an application for a device](install-app-for-device). It creates an approved request for the app on the device.

If the application doesn't install successfully, or the user uninstalls the app, use the following process to retry:

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Application Requests** node.
2. Select the previously approved app. In the Approval Request group of the ribbon, select **Retry install**.

#### Other app approval resources

- [Application approval improvements in ConfigMgr 1810](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/Application-approval-improvements-in-ConfigMgr-1810/ba-p/303534)
- [Updates to the application approval process in Configuration Manager](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/Updates-to-the-application-approval-process-in-Configuration/ba-p/275048)

### Require administrator approval if users request this application

Note

This experience applies if you don't enable the recommended optional app approval experience.

The administrator approves any user requests for the application before the user can install it. This option is grayed out when the deployment purpose is **Required**, or when you deploy the application to a device collection.

Application approval requests are displayed in the **Application Requests** node, under **Application Management** in the **Software Library** workspace. If a request isn't approved within 30 days, it's removed. Reinstalling the client might cancel any pending approval requests.

After you've approved an application for installation, you can **Deny** the request in the Configuration Manager console. This action doesn't cause the client to uninstall the application from any devices. It stops users from installing new copies of the application from Software Center.

## Email notifications

You can configure email notifications for application approval requests. When a user requests an application, you receive an email. Click links in the email to approve or deny the request, without requiring the Configuration Manager console.

You can define the email addresses of the users who can approve or deny the request while creating a new deployment for the application. If you need to change the list of email addresses afterwards, go to the **Monitoring** workspace, expand **Alerts**, and select the **Subscriptions** node. Select **Properties** from one of the **Approve application via email** subscriptions that's related to your application deployment.

If there is more than one alert, you can determine which alert goes with which deployment. Open the alert properties, and view the list of **Selected alerts** on the General tab. The deployment is enabled as the alert for this subscription.

Users can add a comment to the request from Software Center. This comment shows on the application request in the Configuration Manager console. That comment also shows in the email. Including this comment in the email helps the approvers make a better decision to approve or deny the request.

### Prerequisites

#### To send email notifications and take action on internal network

With these prerequisites, recipients receive an email with notification of the request. If they are on the internal network, they can also approve or deny the request from the email.

- Enable the [optional feature](../../core/servers/manage/optional-features)**Approve application requests for users per device**.
- Configure [email notification for alerts](../../core/servers/manage/configure-alerts#configure-email-notification-for-alerts).

    Note

    The administrative user that deploys the application needs permission to create an alert and subscription. If this user doesn't have these permissions, they'll see an error at the end of the **Deploy Software Wizard**: "You do not have security rights to perform this operation."
- [Set up the administration service in Configuration Manager](../../develop/adminservice/set-up).

Note

If you have multiple child primary sites in a hierarchy, configure these prerequisites for each primary site where you want to enable this feature. The links in the email notification are for the administration service at the primary site.

#### To take action from internet

With these additional optional prerequisites, recipients can approve or deny the request from anywhere they have internet access.

- Enable the SMS Provider administration service through the cloud management gateway. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Servers and Site System Roles** node. Select the server with the SMS Provider role. In the details pane, select the **SMS Provider** role, and select **Properties** in the ribbon on the Site Role tab. Select the option to **Allow Configuration Manager cloud management gateway traffic for administration service**.
- Install a supported version of the .NET Framework. Starting in version 2107, the SMS Provider requires .NET version 4.6.2, and version 4.8 is recommended. In version 2103 and earlier, this role requires .NET 4.5 or later. For more information, [Site and site system prerequisites](../../core/plan-design/configs/site-and-site-system-prerequisites#net-version-requirements).
- Set up a [cloud management gateway](../../core/clients/manage/cmg/overview).

    Note

    This scenario doesn't support CMG deployments with a virtual machine scale set until Configuration Manager version 2207 or later is installed.
- Onboard the site to [Azure services](../../core/servers/deploy/configure/azure-services-wizard) for **Cloud Management**.
- Enable [Microsoft Entra user Discovery](../../core/servers/deploy/configure/configure-discovery-methods#azureaadisc).
- Manually configure settings in Microsoft Entra ID:

    1. Go to the [Azure portal](https://portal.azure.com) as a user with **Global Administrator** permissions. Go to **Microsoft Entra ID**, and select **App registrations**.

        Important

        The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../../core/understand/fundamentals-of-role-based-administration).
    2. Select the **Client** application created for Configuration Manager **Cloud Management** integration.
    3. In the **Manage** menu, select **Authentication**.

        1. Add a new **Single-page application** type if not already present.
        2. In the **Redirect URIs** section, paste in the following path: `https://<CMG FQDN>/CCM_Proxy_ServerAuth/ImplicitAuth`
        3. Replace `<CMG FQDN>` with the fully qualified domain name (FQDN) of your cloud management gateway (CMG) service. For example, GraniteFalls.Contoso.com.
        4. For Configuration Manager version 2111 and later, in the **Implicit grant and hybrid flows** section, select the following options:

            - **Access tokens (used for implicit flows)**
            - **ID tokens (used for implicit and hybrid flows)**
        5. Then select **Save**.

    Note

    If on an existing Client Registration Application the Redirect URI needs to be updated, it will need to be created as SPA and older Redirect URI being removed.

### Configure email approval

1. In the Configuration Manager console, [deploy an application](deploy-applications) as available to a user collection. On the **Deployment Settings** page, enable it for approval. Then enter one or more email addresses to receive notification. Separate email addresses with a semi-colon (`;`).

    Note

    Anyone in your Microsoft Entra organization who receives the email can approve the request. Don't forward the email to others unless you want them to take action.
2. As a user, request the application in Software Center.
3. You receive an email notification within five minutes. The content of the email is similar to the following example:

![Example email notification for application approval.](media/1321550-email.png)

Note

The link to approve or deny is for one-time use. For example, you configure a group alias to receive notifications. Meg approves the request. Now Bruce can't deny the request.

Review the **NotiCtrl.log** file on the site server for troubleshooting.

## Maintenance

Configuration Manager stores the information about the application approval request in the site database. For requests that are canceled or denied, the site deletes the request history after 30 days. You can configure this deletion behavior with the **Delete Aged Application Request Data**[site maintenance task](../../core/servers/manage/maintenance-tasks). The site never deletes any approved or pending application requests.