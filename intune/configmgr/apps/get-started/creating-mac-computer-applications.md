---
layout: Conceptual
title: Create Mac computer applications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/get-started/creating-mac-computer-applications
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
description: See which considerations you must take into account when you create and deploy applications for Mac computers.
ms.date: 2022-01-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d758b4ef-397f-593c-f674-43482f45f988
document_version_independent_id: a46a0de1-f99e-912f-45f4-28847d760ef1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/get-started/creating-mac-computer-applications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/get-started/creating-mac-computer-applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/get-started/creating-mac-computer-applications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d5b3b7cf-472e-ca85-d0a4-d3ee36483548
---

# Create Mac computer applications - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in January 2022, this feature of Configuration Manager is deprecated. For more information, see [Mac computers](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices#mac-computers).

Keep the following considerations in mind when you create and deploy applications for Mac computers.

Important

The procedures in this topic cover information about deploying applications to Mac computers on which you installed the Configuration Manager client. Mac computers that you enrolled with Microsoft Intune do not support application deployment.

## General considerations

You can use Configuration Manager to deploy applications to Mac computers that run the Configuration Manager Mac client. The steps to deploy software to Mac computers are similar to the steps to deploy software to Windows computers. However, before you create and deploy applications for Mac computers that are managed by Configuration Manager, consider the following:

- Before you can deploy Mac application packages to Mac computers, you must use the **CMAppUtil** tool on a Mac computer to convert these applications into a format that can be read by Configuration Manager.
- Configuration Manager does not support the deployment of Mac applications to users. Instead, these deployments must be made to a device. Similarly, for Mac application deployments, Configuration Manager does not support the **Pre-deploy software to the user's primary device** option on the **Deployment Settings** page of the **Deploy Software Wizard**.
- Mac applications support simulated deployments.
- You cannot deploy applications to Mac computers that have a purpose of **Available**.
- The option to send wake-up packets when you deploy software is not supported for Mac computers.
- Mac computers do not support Background Intelligent Transfer Service (BITS) for downloading application content. If an application download fails, it is restarted from the beginning.
- Configuration Manager does not support global conditions when you create deployment types for Mac computers.

## Steps to create and deploy an application

The following table provides the steps, details, and information for creating and deploying applications for Mac computers.

| Step | Details |
| --- | --- |
| **Step 1**: Prepare Mac applications for Configuration Manager | Before you can create Configuration Manager applications from Mac software packages, you must use the **CMAppUtil** tool on a Mac computer to convert the Mac software into a Configuration Manager**.cmmac** file. |
| **Step 2**: Create a Configuration Manager application that contains the Mac software | Use the **Create Application Wizard** to create an application for the Mac software. |
| **Step 3**: Create a deployment type for the Mac application | This step is required only if you did not automatically import this information from the application. |
| **Step 4**: Deploy the Mac application | Use the **Deploy Software Wizard** to deploy the application to Mac computers. |
| **Step 5**: Monitor the deployment of the Mac application | Monitor the success of application deployments to Mac computers. |

## Supplemental procedures to create and deploy applications for Mac computers

Use the following procedures to create and deploy applications for Mac computers that are managed by Configuration Manager.

### Step 1: Prepare Mac applications for Configuration Manager

The process for creating and deploying Configuration Manager applications to Mac computers is similar to the deployment process for Windows computers. However, before you create Configuration Manager applications that contain Mac deployment types, you must prepare the applications by using the **CMAppUtil** tool. This tool is downloaded with the Mac client installation files. The **CMAppUtil** tool can gather information about the application, which includes detection data from the following Mac packages:

- Apple disk image (.dmg)
- Meta package file (.mpkg)
- macOS X installer package (.pkg)
- macOS X application (.app)

After it gathers application information, the **CMAppUtil** then creates a file with the extension **.cmmac**. This file contains the installation files for the Mac software and information about detection methods that can be used to evaluate whether the application is already installed. **CMAppUtil** can also process **.dmg** files that contain multiple Mac applications and create different deployment types for each application.

1. Copy the Mac software installation package to the folder on the Mac computer where you extracted the contents of the **macclient.dmg** file that you downloaded from the Microsoft Download Center.
2. On the same Mac computer, open a terminal window and navigate to the folder where you extracted the contents of the **macclient.dmg** file.
3. Navigate to the **Tools** folder and type the following command-line command:

    **./CMAppUtil***&lt;properties&gt;*

    For example, say you want to convert the contents of an Apple disk image file named **MySoftware.dmg** that's stored in the user's desktop folder into a **cmmac** file in the same folder. You also want to create **cmmac** files for all applications that are found in the disk image file. To do this, use the following command line:

    **./CMApputil –c /Users/***&lt;User Name&gt;***/Desktop/MySoftware.dmg -o /Users/***&lt;User Name&gt;***/Desktop -a**

    Note

    The application name can't be more than 128 characters.

    To configure options for **CMAppUtil**, use the command-line properties in the following table:

    | Property | More information |
    | --- | --- |
    | **-h** | Displays the available command-line properties. |
    | **-r** | Outputs the **detection.xml** of the provided **.cmmac** file to **stdout**. The output contains the detection parameters and the version of **CMAppUtil** that was used to create the **.cmmac** file. |
    | **-c** | Specifies the source file to be converted. |
    | **-o** | Specifies the output path in conjunction with the –c property. |
    | **-a** | Automatically creates .cmmac files in conjunction with the –c property for all applications and packages in the disk image file. |
    | **-s** | Skips generating the **detection.xml** if no detection parameters are found and forces the creation of the **.cmmac** file without the **detection.xml** file. |
    | **-v** | Displays more detailed output from the **CMAppUtil** tool together with diagnostic information. |
4. Ensure that the **.cmmac** file has been created in the output folder that you specified.

### Create a Configuration Manager application that contains the Mac software

Use the following procedure to help you create an application for Mac computers that are managed by Configuration Manager.

1. In the Configuration Manager console, choose **Software Library** &gt; **Application Management** &gt; **Applications**.
2. On the **Home** tab, in the **Create** group, choose **Create Application**.
3. On the **General** page of the **Create Application Wizard**, select **Automatically detect information about this application from installation files**.

    Note

    If you want to specify information about the application yourself, select **Manually specify the application information**. For more information about how to manually specify the information, see [How to create applications with Configuration Manager](../deploy-use/create-applications).
4. In the **Type** drop-down list, select **Mac OS X**.
5. In the **Location** field, specify the UNC path in the form *\\&lt;server&gt;\&lt;share&gt;\&lt;filename&gt;* to the Mac application installation file (**.cmmac** file) that will detect application information. Alternatively, choose **Browse** to browse to and specify the installation file location.

    Note

    You must have access to the UNC path that contains the application.
6. Choose **Next**.
7. On the **Import Information** page of the **Create Application Wizard**, review the information that was imported. If necessary, you can choose **Previous** to go back and correct any errors. Choose **Next** to proceed.
8. On the **General Information** page of the **Create Application Wizard**, specify information about the application such as the application name, comments, version, and an optional reference to help you reference the application in the Configuration Manager console.

    Note

    Some of the application information might already be on this page if it was previously obtained from the application installation files.
9. Choose **Next**, review the application information on the **Summary** page, and then complete the **Create Application Wizard**.
10. The new application is displayed in the **Applications** node of the Configuration Manager console.

### Step 3: Create a deployment type for the Mac application

Use the following procedure to help you create a deployment type for Mac computers that are managed by Configuration Manager.

Note

If you automatically imported information about the application in the **Create Application Wizard**, a deployment type for the application might already have been created.

1. In the Configuration Manager console, choose **Software Library** &gt; **Application Management** &gt; **Applications**.
2. Select an application. Then, on the **Home** tab, in the **Application** group, choose **Create Deployment Type** to create a new deployment type for this application.

    Note

    You can also start the **Create Deployment Type Wizard** from the **Create Application Wizard** and from the **Deployment Types** tab of the *&lt;application name&gt;***Properties** dialog box.
3. On the **General** page of the **Create Deployment Type Wizard**, in the **Type** drop-down list, select **Mac OS X**.
4. In the **Location** field, specify the UNC path in the form \\&lt;server&gt;\&lt;share&gt;\&lt;filename&gt; to the application installation file (**.cmmac** file). Alternatively, choose **Browse** to browse to and specify the installation file location.

    Note

    You must have access to the UNC path that contains the application.
5. Choose **Next**.
6. On the **Import Information** page of the **Create Deployment Type Wizard**, review the information that was imported. If necessary, choose **Previous** to go back and correct any errors. Choose **Next** to continue.
7. On the **General Information** page of the **Create Deployment Type Wizard**, specify information about the application such as the application name, comments, and the languages in which the deployment type is available.

    Note

    Some of the deployment type information might already be on this page if it was previously obtained from the application installation files.
8. Choose **Next**.
9. On the **Requirements** page of the **Create Deployment Type Wizard**, you can specify the conditions that must be met before the deployment type can be installed on Mac computers.
10. Choose **Add** to open the **Create Requirement** dialog box and add a new requirement.

    Note

    You can also add new requirements on the **Requirements** tab of the *&lt;deployment type name&gt;***Properties** dialog box.
11. From the **Category** drop-down list, select that this requirement is for a device.
12. From the **Condition** drop-down list, select the condition that you want to use to assess whether the Mac computer meets the installation requirements. The contents of this list varies depending on the category that you select.
13. From the **Operator** drop-down list, choose the operator to use to compare the selected condition to the specified value to assess whether the user or device meets the installation requirements. The available operators vary depending on the selected condition.
14. In the **Value** field, specify the values to use with the selected condition and operator to assess whether the user or device meets in the installation requirement. The available values vary depending on the condition and operator that you select.
15. Choose **OK** to save the requirement rule and exit the **Create Requirement** dialog box.
16. On the **Requirements** page of the **Create Deployment Type Wizard**, choose **Next**.
17. On the **Summary** page of the **Create Deployment Type Wizard**, review the actions for the wizard to take. If necessary, choose **Previous** to go back and change deployment type settings. Choose **Next** to create the deployment type.
18. After the **Progress** page finishes, review the actions that have been taken, and then choose **Close** to complete the **Create Deployment Type Wizard**.
19. If you started this wizard from the **Create Application Wizard**, you will return to the **Deployment Types** page.

### Deploy the Mac application

The steps to deploy an application to Mac computers are the same as the steps to deploy an application to Windows computers, except for the following differences:

- The deployment of applications to users is not supported.
- Deployments that have a purpose of **Available** are not supported.
- The **Pre-deploy software to the user's primary device** option on the **Deployment Settings** page of the **Deploy Software Wizard** is not supported.
- Because Mac computers do not support Software Center, the setting **User notifications** on the **User Experience** page of the **Deploy Software Wizard** is ignored.
- The option to send wake-up packets when you deploy software is not supported for Mac computers.

Note

You can build a collection that contains only Mac computers. To do so, create a collection that uses a query rule and use the example WQL query in the [How to create queries](../../core/servers/manage/create-queries) topic.

For more information, see [Deploy applications](../deploy-use/deploy-applications).

### Step 5: Monitor the deployment of the Mac application

You can use the same process to monitor application deployments to Mac computers as you would to monitor application deployments to Windows computers.

For more information, see [Monitor applications](../deploy-use/monitor-applications-from-the-console).