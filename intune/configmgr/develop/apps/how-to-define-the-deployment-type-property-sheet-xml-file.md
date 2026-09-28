---
layout: Conceptual
title: Define the Deployment Type Property Sheet XML File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-deployment-type-property-sheet-xml-file
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
description: Learn how to create and define the custom deployment type property page XML file for use within Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c54d00d7-cfcb-9b82-c2c2-335ff214ec96
document_version_independent_id: 93c4eb0b-6dec-8dd9-61de-2fbb0a7f5573
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-deployment-type-property-sheet-xml-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-deployment-type-property-sheet-xml-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-deployment-type-property-sheet-xml-file.md
cmProducts: []
platformId: 1c6e5d4c-2853-e460-82a4-d6f4e6649231
---

# Define the Deployment Type Property Sheet XML File - Configuration Manager | Microsoft Learn

To define the custom deployment type property page XML file, create an XML file based on the `https://schemas.microsoft.com/SystemsManagementServer/2005/03/ConsoleFramework` schema. The XML file for the deployment type property sheet should be named &lt;*TechnologyID*&gt;DeploymentTypePropertySheet.xml.

### To define the deployment type property page XML file

1. Create a deployment type property sheet XML file.

    The following example from the RPC sample project shows how to define the deployment type property sheet XML file.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <SmsFormData xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" FormatVersion="1" xmlns="https://schemas.microsoft.com/SystemsManagementServer/2005/03/ConsoleFramework">
      <Form Id="f1908d6f-1ef8-4304-a229-c521c8e33713" FormType="PropertySheet">
        <Resources>
          <Title Name="_AppTitle" />
          <Icon Name="_AppIcon" />
        </Resources>
        <Assembly Name="AdminUI.DeploymentType.Rdp.dll" Namespace="RdpTechnology.AdminConsole"/>
        <Pages>
          <Page VendorId="Partner Company Name" Id="{8A248387-62CB-4253-8255-47E9723BC40D}" Type="RdpDeploymentTechnologyPageControl" />
        </Pages>
      </Form>
    </SmsFormData>
    ```