---
title: "Refresh command (TMSL) | Microsoft Docs"
ms.date: 11/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
---
# Refresh command (TMSL)

  Processes objects in the current database.   
**Refresh** always runs in parallel unless you throttle it with [Sequence command &#40;TMSL&#41;](sequence-command-tmsl.md).  
  
 You can override some properties of some objects during a data refresh operation:  
  
- Change the **QueryDefinition** property of a **Partition** object to import data using an on-the-fly filter expression.  
  
- Provide data source credentials as part of a **Refresh** command,  in the **ConnectionString** property of a **DataSource**  object. This  approach could be considered more secure, as credentials are provided and used temporarily for the duration of the operation, rather than stored.  
  
 See the examples in this topic for an illustration of these property overrides.  
  
> [!NOTE]  
>  Unlike multidimensional processing, there is no special handling of processing errors for tabular processing.  

  
## Request  

 **Refresh** takes a type parameter and object definition.  
  
```json   
    {  
        "refresh": {  
            "description": "Parameters of Refresh command of Analysis Services JSON API",  
            "properties": {  
            "type": {  
                "enum": [  
                "full",  
                "clearValues",  
                "calculate",  
                "dataOnly",  
                "automatic",  
                "add",  
                "defragment"  
                ]  
            },  
            "objects": [  
. . .   
```  
  
 The **type** parameter  sets a scope on the processing operation.  
  
||||  
|-|-|-|  
|**Refresh type**|**Applies to**|**Description**|  
|full|Database,<br />Table,<br />Partition|For all partitions in the specified partition, table, or database, refresh data and recalculate all dependents. For a calculation partition, recalculate the partition and all its dependents.|  
|clearValues|Database,<br />Table,<br />Partition|Clear values in this object and all its dependents.|  
|calculate|Database,<br />Table,<br />Partition|Recalculate this object and all its dependents, but only if needed. This value does not force recalculation, except for volatile formulas.|  
|dataOnly|Database,<br />Table,<br />Partition|Refresh data in this object and clear all dependents.|  
|automatic|Database,<br />Table,<br />Partition|If the object needs to be refreshed and recalculated, refresh and recalculate the object and all its dependents. Applies if the partition is in a state other than Ready.|  
|add|Partition|Append data to this partition and recalculate all dependents. This command is valid only for regular partitions and not for calculation partitions.|  
|defragment|Database,<br />Table|Defragment the data in the specified table. As data is added to or removed from a table, the dictionaries of each column can become polluted with values that no longer exist in the actual column values. The defragment option will clean up the values in the dictionaries that are no longer used.|  
  
 You can refresh the following objects:  
  
 [Database object &#40;TMSL&#41;](database-object-tmsl.md) Process a database.  
  
```json   
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200"  
      }  
    ]  
  }  
}  
```  
  
 [Tables object &#40;TMSL&#41;](tables-object-tmsl.md) Process a single table.  
  
```json   
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "Date"  
      }  
    ]  
  }  
}  
```  
  
 [Partitions object &#40;TMSL&#41;](partitions-object-tmsl.md) Process a single partition within a table.  
  
```json   
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "FactSalesQuota",  
        "partition": "FactSalesQuota"  
      },  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "FactSalesQuota",  
        "partition": "FactSalesQuota - 2011"  
      }  
    ]  
  }  
}  
```  
  
## Response  

 Returns an empty result when the command succeeds. Otherwise, an XMLA exception is returned.  
  
## Examples  

 Override both the **ConnectionString** and **QueryDefinition** of a partition.  
  
```json   
{
  "refresh": {
    "type": "dataOnly",
    "objects": [
      {
        "database": "AdventureWorksDW2017",
        "table": "DimCustomer"
      }
    ],
    "overrides": [
      {
        "dataSources": [ // Bindings for DataSources​
          {
            "originalObject": {
              "database": "AdventureWorksDW2017",
              "dataSource": "SqlServer localhost"
            },
            "connectionString": "Provider=SQLNCLI11.1;Data Source=.;Persist Security Info=True;User ID=YourSQLLogin;Password=YourPassword;Initial Catalog=AdventureWorksDW2017"
          }
        ],
        "partitions": [ // Bindings for Partitions​
          {
            "originalObject": {
              "database": "AdventureWorksDW2017",
              "table": "DimCustomer",
              "partition": "DimCustomer"
            },
            "source": {
              "query": "SELECT * FROM [dbo].[DimCustomer]"
            }
          }
        ]
      }
    ]
  }
}
```  
  
 Scope particular overrides by setting the type parameter to a **dataOnly** refresh, metadata stays intact.  
  
```json   
{
  "refresh": {
    "type": "dataOnly",
    "objects": [
      {
        "database": "TMTestDB",
        "table": "Customer"
      },
      {
        "database": "TMTestDB",
        "table": "Sales"
      }
    ],
    "overrides": [
      {
        "scope": {
          "database": "TMTestDB",
          "table": "Sales"
        },
        "dataSources": [
          {
            "originalObject": {
              "dataSource": "SqlServer sqlcldb2 AS_foodmart_2000"
            },
            "connectionString": "Provider=SQLNCLI11;Data Source=sqlcldb2;Initial Catalog=AS_foodmart_2000;Integrated Security=SSPI;Persist Security Info=false"
          }
        ]
      }
    ]
  }
}
```  
  
## Usage (endpoints)  

 This command element is used in a statement of the Execute Method (XMLA) call over an XMLA endpoint, exposed in the following ways:  
  
- As an XMLA window in SQL Server Management Studio (SSMS)  
  
- As an input file to the **invoke-ascmd** PowerShell cmdlet  
  
- As an input to an SSIS task or SQL Server Agent job  
  
 You can generate a ready-made script  for this command from SSMS. For example, you can click the **Script** in a Processing dialog box.
