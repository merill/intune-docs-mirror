---
layout: Conceptual
title: How to Define the Resources - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-resources
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
description: To support the Installer, a custom XML schema should be included as part of the assembly and the schema XSD file must be included as a resource in the assembly.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 688fe01b-6254-993d-23c2-20ebc1b8cfc0
document_version_independent_id: 55194927-7e7f-9319-18f2-5b339e09c65b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-resources.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-resources
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-resources.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 953a1c47-68d3-6f59-477e-b3cd44798dea
---

# How to Define the Resources - Configuration Manager | Microsoft Learn

To support the Installer, a custom XML schema should be included as part of the assembly. The schema file (XSD) file must be included as a resource in the assembly.

Important

The custom XML schema name must use the following naming convention:

1. &lt;*InstallerClassName*&gt;\_XmlSchema.xsd

    In the case of the RDP sample, the Installer implementation is called RdpInstaller, therefore the XML schema file for that technology is called RdpInstaller\_XmlSchema.xsd.

As part of the resource documentation, a localizable title and description the technology should be created.

Important

The Title and Desciption should use the following naming conventions:

1. &lt;*DeploymentTechnologyClassName*&gt;\_Title 2. &lt;*DeploymentTechnologyClassName*&gt;\_Description

### To define a custom schema file

1. Create the custom schema file.

    The following example from the RDP sample project demonstrates how to define a custom schema file.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <xs:schema id="RdpInstaller" version="1" elementFormDefault="qualified" targetNamespace="https://schemas.microsoft.com/SystemsManagement/2009/ApplicationManagement" xmlns="http://schemas.microsoft.com/SystemsManagement/2009/ApplicationManagement" xmlns:xs="http://www.w3.org/2001/XMLSchema">
      <xs:complexType name="RdpInstaller">
        <xs:complexContent mixed="false">
          <xs:extension base="Installer">
            <xs:sequence>
              <xs:element name="InstallFolder" type="string256" />
              <xs:element name="Filename" type="string256" />
              <xs:element name="ConstructRdpOnClient" type="xs:byte" />
              <xs:element name="FullAddress" type="string256" minOccurs="0" />
              <xs:element name="RemoteApplication" type="string256" minOccurs="0" />
              <xs:element name="FullScreen" type="xs:byte" minOccurs="0" />
              <xs:element name="DesktopWidth" type="int" minOccurs="0" />
              <xs:element name="DesktopHeight" type="int" minOccurs="0" />
              <xs:element name="AudioMode" type="string64" minOccurs="0" />
              <xs:element name="RemoteServerName" type="string64" minOccurs="0" />
              <xs:element name="RemoteServerPort" type="string64" minOccurs="0" />
              <xs:element name="KeyboardMode" type="int" minOccurs="0" />
              <xs:element name="RedirectPrinters" type="xs:byte" minOccurs="0" />
              <xs:element name="RedirectSmartCards" type="xs:byte" minOccurs="0" />
              <xs:element name="Username" type="string64" minOccurs="0" />
              <xs:element name="ContentFilename" type="string256" minOccurs="0" />
            </xs:sequence>
          </xs:extension>
        </xs:complexContent>
      </xs:complexType>
    </xs:schema>
    ```

#### Namespaces

Microsoft.ConfigurationManagement.ApplicationManagement

Microsoft.ConfigurationManagement.ApplicationManagement.Serialization

#### Assemblies

Microsoft.ConfigurationManagement.ApplicationManagement.dll

## .NET Framework Security