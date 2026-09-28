---
layout: Conceptual
title: Package Conversion Manager - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/pcm/package-conversion-manager
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
description: Learn about Package Conversion Manager to convert packages to applications in Configuration Manager.
ms.date: 2020-11-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: b6c34700-7e59-7ba9-086a-13b1da2e9b8b
document_version_independent_id: 326cb379-ef74-1110-a7fa-bdeebb15d31d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/pcm/package-conversion-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/pcm/package-conversion-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/pcm/package-conversion-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: fd35d324-b520-4079-b18a-9e065a3f34a3
---

# Package Conversion Manager - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Package Conversion Manager helps you convert Configuration Manager legacy packages into applications. Applications have additional benefits such as dependencies, requirement rules, detection methods, and user device affinity.

A Configuration Manager application contains files and programs that you deploy to client devices. However, unlike legacy packages and programs, an application provides additional user-centric functionality. For example, an application might contain deployment types for a local installation of a software package, a virtual application package, or a version of the application for mobile devices.

For more information, see the following articles:

- [Introduction to application management](/en-us/previous-versions/troubleshoot/configmgr/introduction-to-application-management)
- [Packages and programs](../deploy-use/packages-and-programs)

Important

If you previously installed an older version of Package Conversion Manager, first uninstall it before upgrading your site. This integrated version doesn't require installation, but may conflict with existing versions.

This integrated version of Package Conversion Manager works on packages in the Configuration Manager current branch site. It's not a standalone tool. If you have packages and programs in an older version of Configuration Manager, first migrate the packages into your current branch site. For more information, see [Migrate data between hierarchies](../../core/migration/migrate-data-between-hierarchies).

## Planning

Before you start converting packages into applications, first develop a plan. The following process is an example plan:

- Define a detailed package conversion plan
- Select and prepare packages for conversion
- Select test packages
- Analyze, investigate, and convert packages
- Test and deploy the applications

### Define a detailed package conversion plan

This section describes two sample package conversion plans:

- A high-resource test environment: You have a test environment with the resources, permissions, and architecture to fully replicate your production environment.
- A limited-resource test environment: You don't have a test environment that fully replicates your production environment.

Adjust these plans as necessary for other issues specific to your environment.

#### Sample plan for a high-resource test environment

Your test environment has the resources, permissions, and architecture similar to your production environment. Use the test environment to efficiently analyze and convert all of your packages, and then test all of your Configuration Manager applications. After completing that work, transfer it to the production environment.

Your package conversion plan may be similar to the following steps:

1. Select the packages you want to convert.
2. Migrate the packages for conversion into your test environment.
3. Prepare the packages for conversion.
4. Select test packages.
5. Analyze, investigate, and convert the test packages.
6. Test the converted applications.
7. Analyze and convert the remaining (non-test) packages.
8. Export the applications from the test environment. Import them into your production environment.

#### Sample plan for a limited-resource test environment

Your test environment doesn't have the resources, permissions, and architecture similar to your production environment. You can't analyze, test, and convert all of your packages. In this scenario, only analyze, investigate, convert, and test your test packages. Then migrate the remaining packages to the production environment to analyze and convert.

Your package conversion plan may be similar to the following steps:

1. Select the packages you want to convert.
2. Select test packages.
3. Migrate the test packages into your test environment.
4. Prepare the test packages for conversion.
5. Analyze, investigate, and convert the test packages.
6. Test the converted applications.
7. Export the test applications from the test environment. Then import them into your production environment.
8. Migrate the remaining packages into the production environment and prepare them for conversion.
9. Analyze, investigate, and convert the remaining packages in the production environment.
10. Release the remaining applications to the production environment.

### Select and prepare packages for conversion

#### Select the packages that you want to convert

Not all packages are suitable to be converted into applications. Before you begin to convert packages, identify the packages that won't be converted.

The best types of package for conversion to applications are those that contain user-facing software, for example:

- Windows Installer files (.msi and .msu)
- Microsoft Application Virtualization (App-V) programs
- Windows executable files (.exe)

The types of package that are best kept as packages and not converted to applications include:

- System maintenance tools. For example, scripts or backup utilities.
- Packages for software that are out of support.

Tip

After identifying packages that aren't appropriate for conversion into applications, move them to a separate folder in the Configuration Manager console. To create a package folder in the Configuration Manager console:

- Right-click the **Packages** node.
- Select **Folders**, and then select **Create Folder**.
- Enter the folder name, for example `Not Converted`.
- Click **OK**.

#### Prepare the packages for conversion

For each package you want to convert, ensure that they conform to the following conditions:

- The source files location is a full UNC path, for example `\\Server\Share\File`.
- Windows Installer files use only one unique product code.

### Select test packages

If possible, your group of test packages should include packages that meet the following criteria:

- At least one test package with a readiness state of **Automatic**.
- At least one test package with a readiness state of **Manual**.

Ideally, your test packages should be core packages, for example:

- Packages that you know well.
- Packages that are the most important to your organization.
- Packages that you can most easily test.

Identify the packages that are appropriate for testing. Then move them to a separate folder in the Configuration Manager console.

### Analyze, investigate, and convert packages

#### Analyze packages

To analyze an individual package or a small group, use Package Conversion Manager integrated in the Configuration Manager console. For more information, see [How to analyze and convert packages](how-to-analyze-and-convert).

Note

See the **Package Conversion Status** node in the **Monitoring** workspace. It displays summary information about the analysis and conversion processes.

#### Investigate analysis results

After analyzing the test packages, investigate the packages with a readiness state of **Manual** or **Error**. Determine the reasons why they have that state. Some common reasons for a readiness state of **Manual** or **Error** include:

- The package doesn't contain the information required to create a detection method in an application deployment type.
- The package doesn't contain the information required to convert collections to global conditions and requirements.
- The package contains more than one program.
- The package is dependent on another package that you haven't converted to an application.

For more information, use the following resources:

- Review the error messages and fixes in [Technical reference for Package Conversion Manager error messages](error-messages)
- Review the log file **PCMTrace.log**
- [Troubleshoot Package Conversion Manager](troubleshoot-pcm)

#### Convert the packages

For more information about how to convert packages, see [How to analyze and convert packages](how-to-analyze-and-convert).

Note

See the **Package Conversion Status** node in the **Monitoring** workspace. It displays summary information about the analysis and conversion processes.

### Test and deploy the applications

Test the applications, either in your test environment or your production environment, according to your detailed package conversion plan.

## Recommendations

- Use the **Package Conversion Status** node in the **Monitoring** workspace. It displays summary information about the analysis and conversion processes.
- Investigate the programs in your packages known as wrappers. Use the Package Conversion Manager plug-in to convert their functions into the equivalent Configuration Manager functionality.
- Ensure that you thoroughly test each converted application before you deploy it in a production environment.