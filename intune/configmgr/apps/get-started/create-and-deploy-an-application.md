---
layout: Conceptual
title: Create and deploy an application - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/get-started/create-and-deploy-an-application
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
description: Create and deploy an application containing a line-of-business app and learn how to manage apps effectively.
ms.date: 2021-10-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 4f57f183-60ca-2072-b8ff-0613a1d6536b
document_version_independent_id: 11010107-d1ca-d332-4a95-cbcaea8b2d75
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/get-started/create-and-deploy-an-application.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/get-started/create-and-deploy-an-application
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/get-started/create-and-deploy-an-application.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: fe688184-cac1-1809-c9aa-1e5d9d48b99a
---

# Create and deploy an application - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

In this article, you'll learn how to create an application with Configuration Manager. In this example, you'll create and deploy the [CMPivot standalone](../../core/servers/manage/cmpivot#bkmk_standalone) installer. For the purposes of this exercise, you'll configure it to only install on devices that are running Windows 11. Along the way, you'll learn about many of the things you can do to manage applications effectively.

Tip

The CMPivot standalone source file is in the Configuration Manager installation media or on the site server in the CD.Latest folder. Find it in the following folder: `\SMSSETUP\TOOLS\CMPivot\CMPivot.msi`

This procedure is designed to give you an overview of how to create and deploy Configuration Manager applications. However, it doesn't cover all the configuration options, or how to create and deploy applications for other platforms.

For specific details that are relevant to each platform, see one of the following articles:

- [Create Windows applications](creating-windows-applications)
- [Create Windows Phone applications](../../mdm/deploy-use/management-tasks-applications#bkmk_winphone)
- [Create Mac computer applications](creating-mac-computer-applications)
- [Create Windows Embedded applications](creating-windows-embedded-applications)

If you're already familiar with Configuration Manager applications, you can skip this article. To learn about all the options that are available when you create and deploy applications, see [Create applications](../deploy-use/create-applications).

## Before you start

Make sure that you've reviewed the information in [Introduction to application management](/en-us/previous-versions/troubleshoot/configmgr/introduction-to-application-management). That article helps you prepare your site to install applications and understand the terminology that's used here.

Make sure that the installation files for the CMPivot standalone app are in an accessible location on your network. This example uses the following path: `\\cm01.contoso.com\SMS_XYZ\cd.latest\SMSSETUP\TOOLS\CMPivot\CMPivot.msi`

## Create the application

Use the following procedure to start the Create Application Wizard and create the application:

1. In the Configuration Manager console, choose **Software Library** &gt; **Application Management** &gt; **Applications**.
2. On the **Home** tab, in the **Create** group, choose **Create Application**.
3. On the **General** page of the **Create Application Wizard**, choose **Automatically detect information about this application from installation files**. This action pre-populates some of the information in the wizard with information that's extracted from the installation .msi file. Then specify the following information:

    - **Type**: Choose **Windows Installer (\*.msi file)**.
    - **Location**: Select **Browse** to choose the location of the installation file **CMPivot.msi**. Make sure the location is specified in the form `\\Server\Share\File.msi` for Configuration Manager to locate the installation files.

    You'll end up with something that looks like the following screenshot:

    ![General page of Create Application Wizard.](media/create-app-wizard-general.png)
4. Choose **Next**. On the **Import Information** page, you'll see some information about the app and any associated files that were imported to Configuration Manager. Once you're done, choose **Next** again.
5. On the **General Information** page, you can supply further information about the application to help you sort and locate it in the Configuration Manager console.

    The **Installation program** field lets you specify the full command line that will be used to install the application on PCs. You can edit this field to add your own properties. For example, `/q` for an unattended installation.

    Tip

    Some of the fields on this page of the wizard might have been filled in automatically when you imported the application installation files.

    You'll end up with a screen that looks similar to the following screenshot:

    ![General Information page of the Create Application Wizard.](media/create-app-wizard-general-information.png)
6. Choose **Next**. On the Summary page, you can confirm your application settings and then complete the wizard.

You've finished creating the app. To find it, in the **Software Library** workspace, expand **Application Management**, and then choose **Applications**. For this example, you'll see:

![CMPivot in the Applications node of the Configuration Manager console.](media/app-list-cmpivot.png)

## Examine the properties

Now that you've created an application, you can refine the application settings if you need to. To look at the application properties, select the app, and then, in the **Home** tab in the **Properties** group, choose **Properties**.

In the **CMPivot Properties** dialog box, you'll see many items that you can configure to refine the behavior of the application. For more information about all the settings you can configure, see [Create applications](../deploy-use/create-applications).

For the purposes of this example, you'll just be changing some properties of the application's deployment type. In the app properties window, switch to the **Deployment Types** tab. Select the **CMPivot - Windows Installer (\*.msi file)** deployment type, and then select **Edit**.

You'll see a dialog box like this one:

![CMPivot app and deployment type property pages.](media/cmpivot-app-deployment-type-properties.png)

## Add a requirement

Requirements specify conditions that must be met before an application is installed on a device. You can choose from built-in requirements or you can create your own. In this example, you add a requirement that the application will only get installed on devices that are running Windows 11.

1. On the deployment type properties page, switch to the **Requirements** tab.
2. Select **Add** to open the **Create Requirement** window. Specify the following information:

    - **Category**: **Device**
    - **Condition**: **Operating system**
    - **Rule type**: **Value**
    - **Operator**: **One of**
    - From the OS list, select **All Windows 11 (64-bit)**.

    You'll end up with a dialog box that looks like this:

    ![Create Requirement window.](media/create-requirement-windows-11.png)
3. Select **OK** to close each property page that you opened. Then return to the **Applications** list in the Configuration Manager console.

Tip

Requirements can help reduce the number of Configuration Manager collections you need. Because you just specified that the application can only get installed on devices that are running Windows 11, you can later deploy this to a collection that contains PCs that run many different operating systems. But the application will only get installed on Windows 11 devices.

## Distribute the application content

Next, to deploy the application to PCs, make sure that the application content is copied to a distribution point. PCs access the distribution point to install the application.

Tip

To find out more about distribution points and content management in Configuration Manager, see [Manage content and content infrastructure](../../core/servers/deploy/configure/manage-content-and-content-infrastructure).

1. In the Configuration Manager console, choose **Software Library**.
2. In the **Software Library** workspace, expand **Applications**. Then, in the list of applications, select the **CMPivot** that you created.
3. On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.
4. On the **General** page of the **Distribute Content Wizard**, check that the application name is correct, and then choose **Next**.
5. On the **Content** page, review the information that will be copied to the distribution point, and then choose **Next**.
6. On the **Content Destination** page, choose **Add** to select one or more distribution points, or distribution point groups on which to install the application content.
7. Complete the wizard.

You can check that the application content was copied successfully to the distribution point from the **Monitoring** workspace, under **Distribution Status** &gt; **Content Status**.

## Deploy the application

Next, deploy the application to a device collection in your hierarchy. In this example, you deploy the application to the **All Systems** device collection.

Tip

Remember that only Windows 11 computers will install the application because of the requirements that you selected earlier.

1. In the Configuration Manager console, choose **Software Library** &gt; **Application Management** &gt; **Applications**.
2. From the list of applications, select the application that you created earlier (**CMPivot**), and then, on the **Home** tab in the **Deployment** group, choose **Deploy**.
3. On the **General** page of the **Deploy Software Wizard**, choose **Browse** to select the **All Systems** device collection.
4. On the **Content** page, check that the distribution point from which you want PCs to install the application is selected.
5. On the **Deployment Settings** page, make sure that the deployment action is set to **Install**, and the deployment purpose is set to **Required**.

    Tip

    By setting the deployment purpose to **Required**, you make sure that the application is installed on PCs that meet the requirements that you set. If you set this value to **Available**, then users can install the application on demand from Software Center.
6. On the **Scheduling** page, you can configure when the application will be installed. For this example, select **As soon as possible after the available time**.
7. On the **User Experience** page, choose **Next** to accept the default values.
8. Complete the wizard.

Use the information in the following **Monitor the application** section to see the status of your application deployment.

## Monitor the application

In this section, you'll take a quick look at the deployment status of the application that you deployed.

1. In the Configuration Manager console, choose **Monitoring** &gt; **Deployments**.
2. From the list of deployments, select **CMPivot**.
3. On the **Home** tab, in the **Deployment** group, choose **View Status**.
4. Select one of the following tabs to see more status updates about the application deployment:

    - **Success**: The application installed successfully on the indicated PCs.
    - **In Progress**: The application is still installing.
    - **Error**: An error occurred installing the application on the indicated PCs. Further information about the error is also displayed.
    - **Requirements Not Met**: No installation attempt was made on the indicated devices because they didn't meet the requirements you configured. In this example, because they don't run on Windows 11.
    - **Unknown**: Configuration Manager was unable to report the status of the deployment. Check back again later.

Tip

There are a few ways you can monitor application deployments. For more information, see [Monitor applications](../deploy-use/monitor-applications-from-the-console).

## User experience

Users who have PCs that are managed by Configuration Manager and running Windows 11 see a message telling them that they must install the CMPivot application. Once they accept the deployment, the application gets installed.