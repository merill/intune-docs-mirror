---
layout: Conceptual
title: Configuration Manager Site Control File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file
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
description: Site control in Configuration Manager defines the settings for a specific site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: ed4f2bb8-28c3-1bce-b444-897cbc6a9e80
document_version_independent_id: b65bef23-3de3-a08b-4b24-30d80b207ab3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/about-the-configuration-manager-site-control-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 20abe8eb-80f1-f513-fb94-ab49cb2ebb7b
---

# Configuration Manager Site Control File - Configuration Manager | Microsoft Learn

Site control in Configuration Manager defines the settings for a specific site. The settings for each site are contained in the database and are accessed through Windows Management Instrumentation (WMI) when working with scripting languages, and through the managed SMS Provider library when working with a managed language.

Note

Previous releases of Configuration Manager had a physical file that was processed for site settings referred to as the site control file. Configuration Manager stores site settings directly in the site database; however, very little has changed when programmatically configuring a site.

The site control file in Configuration Manager is an ASCII text file (Sitectrl.ct0) that contains the configuration of each site. There are two types of site control files:

- Actual site control file - A working copy of the site control file that is stored in the Configuration Manager site database and in the inbox in the site control manager.
- Delta site control file - Contains the proposed site control file changes that are to be processed.

The site control file is stored on each site server in the site control manager inbox.

On the primary site, there is a copy of the site control file for the current site in the database. The primary site also has a copy of the site control file for all lower level sites in the hierarchy, including secondary sites.

Each child site passes a copy of its site control file to its parent site. Each parent site passes a copy of the site control file for itself and for each of its child sites up the hierarchy. Therefore, the central site's database contains copies of the site control files of every Configuration Manager site in the hierarchy.

## Site Control File Format

The site control file is a collection of resource definitions that contain embedded properties, embedded property lists and multi-string lists.

The following example shows a section of site control file that defines client component information. The resource is declared by the BEGIN\_CLIENT\_COMPONENT. The embedded properties are denoted by PROPERTY and have a name and value. The property lists are denoted by the BEGIN\_PROPERTY\_LIST section and list a property list name and several property names and associated values. The multi-string lists are denoted by the BEGIN\_CLIENT\_REG\_MULTI\_STRING\_LIST and provide a list of string values.

```
BEGIN_CLIENT_COMPONENT
    <SMS Client Base Components>
    <65537>
    SITE_KEY_FLAGS <1>
    PROPERTY <Component Verify Interval><REG_SZ><00011700001000F0><0>
    PROPERTY <Component Maintenance Interval (minutes)><REG_DWORD><><1500>
    BEGIN_PROPERTY_LIST
        <Copy Queue>
        <(REG_DWORD)Item Lifetime=11520>
        <(REG_DWORD)Wakeup cycle=1380>
    END_PROPERTY_LIST
    BEGIN_CLIENT_REG_MULTI_STRING_LIST
        <Retry Sequence><Copy Queue>
        SITE_KEY_FLAGS <1>
        <15>
        <30>
        <60>
        <360>
    END_CLIENT_REG_MULTI_STRING_LIST
END_CLIENT_COMPONENT
```

The provider has several Windows Management Instrumentation (WMI) classes that represent resources in the site control file. For example, [SMS_SCI_Component Server WMI Class](../../reference/core/servers/configure/sms_sci_component-server-wmi-class) holds information on the server components stored on a Configuration Manager site server. These classes derive from [SMS_SiteControlItem Server WMI Class](../../reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

For more information, see [Configuration Manager Site Configuration Server WMI Classes \[reference\]](../../reference/core/servers/configure/site-configuration-server-wmi-classes).

The following example is the declaration for [SMS_SCI_ClientConfig Server WMI Class](../../reference/core/servers/configure/sms_sci_clientconfig-server-wmi-class).

```mof
Class SMS_SCI_ClientConfig : SMS_SiteControlItem
{
     String ClientConfigName;
     UInt32 FileType;
     UInt32 Flags;
     String ItemName;
     String ItemType;
     String Platforms[];
     SMS_EmbeddedPropertyList PropLists[];
     SMS_EmbeddedProperty Props[];
     SMS_Client_Reg_MultiString_List RegMultiStringLists[];
     String SiteCode;
};
```

The declaration includes declarations for the embedded property, property list, and multi string list declarations.

You access the embedded properties, property lists, and multi-string lists by using the following classes:

| Type | WMI Class |
| --- | --- |
| Embedded property | [SMS_EmbeddedProperty Server WMI Class](../../reference/core/servers/configure/sms_embeddedproperty-server-wmi-class) |
| Embedded property list | [SMS_EmbeddedPropertyList Server WMI Class](../../reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class) (array) |
| Multi-string list | [SMS_Client_Reg_MultiString_List Server WMI Class](../../reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class) (array) |

This documentation has the following topic that describes the embedded properties:

[How to Read a Configuration Manager Site Control File Embedded Property List](how-to-read-a-configuration-manager-site-control-file-embedded-property-list)

## Using the Site Control File

How you access the site control file differs depending on whether you are using WMI or the managed provider.

### WMI

When you are using WMI, you use the `SMS_SiteControlFile` class methods to manage changes to the site control file. Writing to the site control file is managed by using session contextual information that you supply. This is used to enable concurrent writing to the site control file for multiple applications.

For more information, see [How to Read and Write to the Configuration Manager Site Control File by Using WMI](how-to-read-and-write-to-the-site-control-file-by-using-wmi)

If you are only reading from the site control file you can query it without setting up a session.

### Managed Provider

In almost all cases, your code does not have to lock or commit changes to the Configuration Manager site control file because the managed Configuration Manager library takes care of this for you.

As a result, programming the Configuration Manager site control file is fundamentally the same as programming Configuration Manager objects. This is different from accessing the Configuration Manager site control file through WMI where you explicitly have to get a session handle and commit any changes you make.

For more information, see, [How to Read and Write to the Configuration Manager Site Control File by Using Managed Code](how-to-read-and-write-to-the-site-control-file-by-using-managed-code).