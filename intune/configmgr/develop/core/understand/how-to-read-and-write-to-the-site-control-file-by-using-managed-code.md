---
layout: Conceptual
title: Read and Write to the Site Control File by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code
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
description: To write to the Configuration Manager site control file by using the managed SMS Provider, get the site definition file by querying for the required resource or component.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a285ebb7-f507-fa82-767c-0c4f1d8e1e8b
document_version_independent_id: c7b9cec6-123b-8922-ea17-51cc26f70dc5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code.md
cmProducts: []
platformId: 1ae13d53-3c17-dbdb-f7f8-564a85819166
---

# Read and Write to the Site Control File by Using Managed Code - Configuration Manager | Microsoft Learn

To write to the Configuration Manager site control file by using the managed SMS Provider, you get the site definition file by querying for the required resource or component. You then update the embedded property, embedded property list, or multi-string list as required.

Note

You can also use connection manager [GetInstance](/en-us/previous-versions/system-center/developer/cc146190%28v=msdn.10%29) to get the required resource or component.

The managed Configuration Manager manages the connection session to the site control file automatically for you. Therefore you treat the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) objects returned from the query in the same way as you treat [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) objects retrieved from the SMS Provider.

### To read and write to the site control file

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](how-to-connect-to-an-sms-provider-by-using-managed-code).
2. Use the Connection Manager **QueryProcessor** object *ExecQuery* or *GetInstance* method to get the required site control file resource or component [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object.
3. Using the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) update the site control file.
4. Use the [IResultObject](/en-us/previous-versions/system-center/developer/cc147376%28v=msdn.10%29) object [Put](/en-us/previous-versions/system-center/developer/cc146500%28v=msdn.10%29) method to commit the changes.

## Example

The following C# example accesses the client agent component of the site control file and creates a dummy property, property list and multi-string list. It then removes the updates that were made. The example demonstrates how to query the site control file, make updates, and commit changes to the site control file.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```
public void ReadWriteSCF(WqlConnectionManager connection,string siteCode)
{
    try
    {

    // Query for the site's site control file client agent settings.
    IResultObject resources =
    connection.QueryProcessor.ExecuteQuery
    ("SELECT * FROM SMS_SCI_ClientComp WHERE ClientComponentName = 'Client Agent' AND SiteCode = '" +
    siteCode + "'");

    foreach (IResultObject resource in resources)
    {
            // Embedded Properties

            Console.WriteLine("Embedded property");
            Console.WriteLine("-----------------");

            int value = 0;
            string value1 = "";
            string value2 = "";

            // Write a dummy embedded property.
            this.WriteScfEmbeddedProperty(resource, "Test", 10, "Hello", "World");

            // Get the embedded property back and display the values.
            if (this.GetScfEmbeddedProperty(resource, "Test", ref value, ref value1, ref value2))
            {
                Console.WriteLine("Value: " + value);
                Console.WriteLine("Value1: " + value1);
                Console.WriteLine("Value2: " + value2);

                // Remove the dummy embedded property.
                Dictionary<string, IResultObject> EmbeddedProperties = resource.EmbeddedProperties;
                EmbeddedProperties.Remove("Test");
                resource.EmbeddedProperties = EmbeddedProperties;
                resource.Put();

                // See if the dummy embedded property is still there.
                if (this.GetScfEmbeddedProperty(resource, "Test", ref value, ref value1, ref value2))
                {
                    Console.WriteLine("Test exists");
                }
                else
                {
                    Console.WriteLine("Test does not exist");
                }
            }
            else
            {
                Console.WriteLine("Property not found");
            }

            Console.WriteLine();

            // Embedded property list.

            Console.WriteLine("Embedded property list");
            Console.WriteLine("----------------------");

            // values contains the embedded property list.
            ArrayList values = new ArrayList();

            values.Add("Elephant");
            values.Add("Giraffe");

            // Write to the resource.
            this.WriteScfEmbeddedPropertyList(resource, "Animals", values);

            ArrayList retrievedValues;

            // Get the embedded property list and display.
            if (this.GetScfEmbeddedPropertyList(resource, "Animals", out retrievedValues))
            {
                foreach (string retrievedValue in retrievedValues)
                {
                    Console.WriteLine(retrievedValue);
                }

                // Remove one of the entries.
                retrievedValues.Remove("Elephant");
                Console.WriteLine();

                // Update the list.
                this.WriteScfEmbeddedPropertyList(resource, "Animals", retrievedValues);

                // Display the list again.
                this.GetScfEmbeddedPropertyList(resource, "Animals", out retrievedValues);
                foreach (string retrievedValue in retrievedValues)
                {
                    Console.WriteLine(retrievedValue);
                }

            }
            else
            {
                Console.WriteLine("None");
            }

            Console.WriteLine();

            // RegMultiStringList.

            Console.WriteLine("RegMultiStringList");
            Console.WriteLine("------------------");

            // valuesStrings is the RegMultiString List.
            ArrayList valueStrings = new ArrayList();

            valueStrings.Add("Tom");
            valueStrings.Add("Harry");

            this.WriteScfRegMultiStringList(resource, "Names", valueStrings);

            ArrayList retrievedValuesStrings;

            if (this.GetScfRegMultiStringList(resource, "Names", out retrievedValuesStrings))
            {
                foreach (string retrievedValue in retrievedValuesStrings)
                {
                    Console.WriteLine(retrievedValue);
                }

                // Remove one of the entries.
                retrievedValuesStrings.Remove("Tom");
                Console.WriteLine();

                // Update the list.
                this.WriteScfRegMultiStringList(resource, "Names", retrievedValuesStrings);

                // Display the list again.
                this.GetScfRegMultiStringList(resource, "Names", out retrievedValuesStrings);
                foreach (string retrievedValue in retrievedValuesStrings)
                {
                    Console.WriteLine(retrievedValue);
                }
            }
            else
            {
                Console.WriteLine("None");
            }
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed: " + e.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `siteCode` | - `String` | The site code for the Configuration Manager site. |

## Compiling the Code

### Namespaces

System

System.Collections.Generic

System.Collections

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

The Configuration Manager exceptions that can be raised are [SmsConnectionException](/en-us/previous-versions/system-center/developer/cc147431%28v=msdn.10%29) and [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29). These can be caught together with [SmsException](/en-us/previous-versions/system-center/developer/cc147433%28v=msdn.10%29).