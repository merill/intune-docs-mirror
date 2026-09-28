---
layout: Conceptual
title: Add New Properties to an Existing Resource Type - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-add-new-properties-to-an-existing-resource-type
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
description: Learn how to add a property to the resource class when the Data Discovery Manager detects that your data discovery record contains a property that doesn't exist.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8e9bcf9c-9ac1-1f22-c857-8f791ef383b8
document_version_independent_id: 94f02a8a-d06b-d445-6061-bfc791bdcb7b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-add-new-properties-to-an-existing-resource-type.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-add-new-properties-to-an-existing-resource-type
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-add-new-properties-to-an-existing-resource-type.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 325ac11e-5076-7a4b-df6c-6099337c28b1
---

# Add New Properties to an Existing Resource Type - Configuration Manager | Microsoft Learn

In Configuration Manager, when the Data Discovery Manager (DDM) detects that your data discovery record (DDR) contains a property that does not exist in the resource class, the property is added to the resource class. Depending on the data type of the new property, previous instances of the resource will contain either a zero or an empty string ("") for the value of the new property. You should specify all the class properties when you update an existing resource class. However, do not include the seven properties that the DDM creates for you. When the DDM creates a new resource class, it adds these additional properties to the class:

- ResourceID
- AgentName
- AgentSite
- AgentTime
- Name
- ResourceType
- SMSAssignedSite

    For a description of these properties, see `SMS_R_System`. In addition to creating these properties, the DDM creates an instance of `SMS_ResourceMap` for the new ResourceType value.

### To add properties to an existing resource type

1. Get a specific instance of an existing resource.
2. Create a new instance of the `SMSResGen` class.
3. Create a new DDR using the `NewDDR` method.
4. Add properties to the DDR using the ADDPROP\_ methods.
5. Write the new DDR to a file using the `DDRWrite` method.

## Example

The following example creates a DDR that adds the `OrganizationalUnit` property to the `SMS_R_System` class. You can then use this property to create collections based on departments and distribute software accordingly. If your organization uses Active Directory, you can use the information it contains to populate the `OrganizationalUnit` property.

The following example shows the key, name, and GUID properties that you use to update the system resource class.

```vbs

Sub CreateDDRToAddNewPropertiesToAnExistingResourceType()

    ' Define variables.
    Dim resourceID
    Dim existingResource
    Dim newDDR
    Dim siteCode
    Dim organizationalUnit

    ' Set variables.
    resourceID = 5
    siteCode = "TQ1"
    organizationalUnit = "Test OU"

    ' Get a specific resource (client) object using the resourceID value.
    Set existingResource = GetObject("winmgmts:root/sms/site_" & siteCode & ":SMS_R_System.ResourceID=" & resourceID & "")

    ' Load an instance of the SMSResGen.dll.
    Set newDDR = CreateObject("SMSResGen.SMSResGen.1")

    ' Create a new DDR using the DDRNew method.
    newDDR.DDRNew "System", "Department Discovery", siteCode

    ' Add properties to the new DDR using the DDRAdd methods.
    newDDR.DDRAddInteger "Client", existingResource.Client, ADDPROP_NONE
    newDDR.DDRAddString "Client Version", existingResource.ClientVersion, 15, ADDPROP_NONE
    newDDR.DDRAddStringArray "IP Addresses", existingResource.IPAddresses, 64, ADDPROP_NONE
    newDDR.DDRAddStringArray "IP Subnets", existingResource.IPSubnets, 64, ADDPROP_NONE
    newDDR.DDRAddString "Last Logon User Domain", existingResource.LastLogonUserDomain, 64, ADDPROP_NONE
    newDDR.DDRAddString "Last Logon User Name", existingResource.LastLogonUserName, 255, ADDPROP_NONE
    newDDR.DDRAddStringArray "MAC Addresses", existingResource.MACAddresses, 64, ADDPROP_KEY
    newDDR.DDRAddString "NetBIOS Name", existingResource.NetbiosName, 64, ADDPROP_NAME
    newDDR.DDRAddString "Operating System Name and Version", existingResource.OperatingSystemNameandVersion, 64, ADDPROP_NONE
    newDDR.DDRAddString "Resource Domain OR Workgroup", existingResource.ResourceDomainORWorkgroup, 64, ADDPROP_NONE
    newDDR.DDRAddStringArray "Resource Names", existingResource.ResourceNames, 128, ADDPROP_NONE
    newDDR.DDRAddStringArray "SMS Installed Sites", existingResource.SMSInstalledSites, 3, ADDPROP_NONE
    newDDR.DDRAddString "SMS Unique Identifier", existingResource.SMSUniqueIdentifier, 64, ADDPROP_GUID OR ADDPROP_KEY
    newDDR.DDRAddStringArray "System Roles", existingResource.SystemRoles, 32, ADDPROP_NONE

    ' The new property that is being added.
    newDDR.DDRAddString "Organizational Unit", OrganizationalUnit, 64, ADDPROP_NONE

    ' Write new DDR to file.
    newDDR.DDRWrite "NewDDR_AddToExistingResource.DDR"
    wscript.echo "Created new DDR."

End Sub

```

```c

public void CreateDDRToAddNewPropertiesToAnExistingResourceType(WqlConnectionManager connection)
{
    try
    {
        // Define and set the required variables.
        int resourceID = 5;
        string siteCode = "TQ1";
        string organizationalUnit = "Test OU";

        // Get a specific resource (client) object using the resourceID value.
        IResultObject existingResource = connection.GetInstance(@"SMS_R_SYSTEM.ResourceID='" + resourceID + "'");

        // Create the SMSResGenClass instance.
        SMSRSGENCTLLib.SMSResGen newDDR = new SMSRSGENCTLLib.SMSResGen();

        // Create a new DDR using the DDRNew method.
        newDDR.DDRNew("System", "Department Discovery", siteCode);

        // Add properties to the new DDR using the DDRAddInteger, DDRAddString and DDRAddStringArray methods.
        newDDR.DDRAddInteger("Client", existingResource["Client"].IntegerValue, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddString("Client Version",existingResource["ClientVersion"].StringValue, 15, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddStringArray("IP Addresses",existingResource["IPAddresses"].StringArrayValue, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddStringArray("IP Subnets", existingResource["IPSubnets"].StringArrayValue, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddString("Last Logon User Domain",existingResource["LastLogonUserDomain"].StringValue, 255, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddString("Last Logon User Name",existingResource["LastLogonUserName"].StringValue, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_KEY);
        newDDR.DDRAddStringArray("MAC Addresses",existingResource["MACAddresses"].StringArrayValue, 32, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NAME);
        newDDR.DDRAddString("NetBIOS Name",existingResource["NetbiosName"].StringValue, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddString("Operating System Name and Version",existingResource["OperatingSystemNameandVersion"].StringValue, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddStringArray("Resource Names",existingResource["ResourceNames"].StringArrayValue, 128, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddStringArray("SMS Installed Sites",existingResource["SMSInstalledSites"].StringArrayValue, 3, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);
        newDDR.DDRAddString("SMS Unique Identifier",existingResource["SMSUniqueIdentifier"].StringValue, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_GUID | SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_KEY);
        newDDR.DDRAddStringArray("System Roles",existingResource["SystemRoles"].StringArrayValue, 32, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);

        // The new property that is being added.
        newDDR.DDRAddString("Organizational Unit", organizationalUnit, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_ARRAY | SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);

        // Write new DDR to file.
        newDDR.DDRWrite("NewDDR_AddToExistingResource.DDR");
        Console.WriteLine("Created new DDR.");
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create DDR. Error: " + ex.Message);
        throw;
    }
}

```

The example method has no parameters.

## Compiling the Code

Important

This VBScript and C# examples require **smsrsgen.dll** and **smsrsgenctl.dll**, respectively. Both files are included as a part of the downloadable Configuration Manager SDK (in the "Redistributables" folder).

The file **smsrsgenctl.dll** is a 32-bit dll and must be registered on the system that will run the application. In addition, the application using **smsrsgenctl.dll** should be compiled as an x86 application.

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](role-based-administration).