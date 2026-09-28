---
layout: Conceptual
title: Import a Windows Driver Described by an INF File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-import-a-windows-driver-described-by-an-inf-file
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
description: You can import a Windows driver that is described by an information (.inf) file, in Configuration Manager, by using the CreateFromINF Method in Class SMS_Driver.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3914cb44-e439-3621-3853-c84821179cfb
document_version_independent_id: b772ecc3-ccd5-b13a-1327-87f25df69def
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-import-a-windows-driver-described-by-an-inf-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-import-a-windows-driver-described-by-an-inf-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-import-a-windows-driver-described-by-an-inf-file.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 28955c20-d69e-d1e7-bdd9-9b93cedf165f
---

# Import a Windows Driver Described by an INF File - Configuration Manager | Microsoft Learn

You can import a Windows driver that is described by an information (.inf) file, in Configuration Manager, by using the [CreateFromINF Method in Class SMS_Driver](../reference/osd/createfrominf-method-in-class-sms_driver).

### To import a Windows driver

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Call the [CreateFromINF Method in Class SMS_Driver](../reference/osd/createfrominf-method-in-class-sms_driver) to get the initial [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) management base object.
3. Create an instance of [SMS_Driver](../reference/osd/sms_driver-server-wmi-class) by using the management base object.
4. Populate the `SMS_Driver` object.
5. Commit the `SMS_Driver` object.

## Example

The following example method creates an `SMS_Driver` object for a Windows driver by using the supplied path and file name. The example also enables the driver by setting the value of the `IsEnabled` property to `true`. The helper function `GetDriverName` is used to get the name of the driver from the driver package XML.

Note

The `path` parameter must be supplied as a Universal Naming Convention (UNC) network path, for example, \\localhost\Drivers\ATIVideo\.

In the example, the `LocaleID` property is hard-coded to English (U.S.). If you need the locale for non-U.S. installations, you can get it from the [SMS_Identification Server WMI Class](../reference/core/servers/configure/sms_identification-server-wmi-class)`LocaleID` property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub ImportINFDriver(connection, path, name)

    Dim driverClass
    Dim inParams
    Dim outParams

    On Error Resume Next

    ' Obtain an instance of the class
    ' using a key property value.

    Set driverClass = connection.Get("SMS_Driver")

    ' Obtain an InParameters object specific
    ' to the method.
    Set inParams = driverClass.Methods_("CreateFromINF"). _
        inParameters.SpawnInstance_()

    ' Add the input parameters.
    inParams.Properties_.Item("DriverPath") =  path
    inParams.Properties_.Item("INFFile") =  name

    ' Call the method.
    ' The OutParameters object in outParams
    ' is created by the provider.
    Set outParams = connection.ExecMethod("SMS_Driver", "CreateFromINF", inParams)

   If Err <> 0 Then
        Wscript.Echo "Failed to add to the driver catalog: " + path + "\" + name
        Exit Sub
    End If

    outParams.Driver.IsEnabled =  True

    Dim LocalizedSettings(0)
    Set LocalizedSettings(0) = connection.Get("SMS_CI_LocalizedProperties").SpawnInstance_()
    LocalizedSettings(0).Properties_.item("LocaleID") =  1033
    LocalizedSettings(0).Properties_.item("DisplayName") = _
            GetDriverName(outParams.Driver.SDMPackageXML, "//DisplayName", "Text")

    LocalizedSettings(0).Properties_.item("Description") = ""
    outParams.Driver.LocalizedInformation = LocalizedSettings

    ' Save the driver.
    outParams.Driver.Put_

End Sub

Function GetDriverName(xmlContent, nodeName, attributeName)
    ' Load the XML Document
    Dim attrValue
    Dim XMLDoc
    Dim objNode
    Dim displayNameNode

    attrValue = ""
    Set XMLDoc = CreateObject("Microsoft.XMLDOM")
    XMLDoc.async = False
    XMLDoc.loadXML(xmlContent)

    'Check for a successful load of the XML Document.
    If xmlDoc.parseError.errorCode <> 0 Then
        WScript.Echo vbcrlf & "Error loading XML Document. Error Code : 0x" & hex(xmldoc.parseerror.errorcode)
        WScript.Echo "Reason: " & xmldoc.parseerror.reason
        WScript.Echo "Parse Error line " & xmldoc.parseError.line & ", character " & _
                      xmldoc.parseError.linePos & vbCrLf & xmldoc.parseError.srcText

        GetXMLAttributeValue = ""
    Else
        ' Select the node
        Set objNode = xmlDoc.SelectSingleNode(nodeName)

        If Not objNode Is Nothing Then
            ' Found the element, now just pick up the Text attribute value
            Set displayNameNode = objNode.attributes.getNamedItem(attributeName)
            If Not displayNameNode Is Nothing Then
               attrValue = displayNameNode.value
            Else
               WScript.Echo "Attribute not found"
            End If
        Else
            WScript.Echo "Failed to locate " & nodeName & " element."
        End If
    End If

    ' Save the results
    GetDriverName = attrValue
End Function
```

```c
public void ImportInfDriver(
    WqlConnectionManager connection,
    string path,
    string name)
{
    try
    {
        Dictionary<string, object> inParams = new Dictionary<string, object>();

        // Set up parameters for the path and file name.
        inParams.Add("DriverPath", path);
        inParams.Add("INFFile", name);

        // Import the INF file.
        IResultObject result = connection.ExecuteMethod("SMS_Driver", "CreateFromINF", inParams);

        // Create the SMS_Driver driver instance from the management base object returned in result["Driver"].
        IResultObject driver = connection.CreateInstance(result["Driver"].ObjectValue);

        // Enable the driver.
        driver["IsEnabled"].BooleanValue = true;

        List<IResultObject> driverInformationList = driver.GetArrayItems("LocalizedInformation");

        // Set up the display name and other information.
        IResultObject driverInfo = connection.CreateEmbeddedObjectInstance("SMS_CI_LocalizedProperties");
        driverInfo["DisplayName"].StringValue = GetDriverName(driver);
        driverInfo["LocaleID"].IntegerValue = 1033;
        driverInfo["Description"].StringValue = "";

        driverInformationList.Add(driverInfo);

        driver.SetArrayItems("LocalizedInformation", driverInformationList);

        // Commit the SMS_Driver object.
        driver.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to import driver: " + e.Message);
        throw;
    }
}

public string GetDriverName(IResultObject driver)
{
    // Extract
    XmlDocument sdmpackage = new XmlDocument();

    sdmpackage.LoadXml(driver.Properties["SDMPackageXML"].StringValue);

    // Iterate over all the <DisplayName/> tags.
    foreach (XmlNode displayName in sdmpackage.GetElementsByTagName("DisplayName"))
    {
    // Grab the first one with a Text attribute not equal to null.
        if (displayName != null && displayName.Attributes["Text"] != null
            && !string.IsNullOrEmpty(displayName.Attributes["Text"].Value))
        {
                // Return the DisplayName text.
                return displayName.Attributes["Text"].Value;
        }
    }
    // Default the driverName to the UniqueID.
    return driver["CI_UniqueID"].StringValue;
 }

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `path` | - Managed: `String`- VBScript: `String` | A valid UNC network path to the folder that contains the driver contents. For example, \\Servers\Driver\VideoDriver. |
| `name` | - Managed: `String`- VBScript: `String` | The name of the .inf file. For example, ATI.inf. |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).