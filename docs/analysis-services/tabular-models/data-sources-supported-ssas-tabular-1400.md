﻿---
title: "Data sources supported in SQL Server Analysis Services tabular 1400 and higher models | Microsoft Docs"
ms.date: 02/20/2020
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
monikerRange: "asallproducts-allversions || azure-analysis-services-current || >= sql-analysis-services-2017"
---
# Data sources supported in SQL Server Analysis Services tabular 1400 and higher models

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

This article describes the types of data sources that can be used with SQL Server Analysis Services (SSAS) tabular models at the 1400 and higher compatibility level. 

For SSAS tabular models at the 1200 and lower compatibility levels, see [Data sources supported in SQL Server Analysis Services tabular 1200  models](data-sources-supported-ssas-tabular.md).

For Azure Analysis Services, see [Data sources supported in Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## Cloud data sources

|Datasource  |In-memory  |DirectQuery  |
|---------|---------|---------|
|Azure SQL Database     |   Yes      |    Yes      |
|Azure Synapse Analytics (SQL Data Warehouse)     |   Yes      |   Yes       |
|Azure Blob Storage     |   Yes       |    No      |
|Azure Table Storage    |   Yes       |    No      |
|Azure Cosmos DB     |  Yes        |  No        |
|Azure Data Lake Store (Gen1)<sup>[1](#gen2)</sup>      |   Yes       |    No      |
|Azure HDInsight HDFS    |     Yes     |   No       |
|Azure HDInsight Spark <sup>[2](#databricks)</sup>     |   Yes       |   No       |
||||

<a name="gen2">1</a> - ADLS Gen2 is currently not supported.   
<a name="databricks">2</a> - Azure Databricks using the Spark connector is currently not supported.   



**Provider**   
In-memory and DirectQuery models connecting to Azure data sources use .NET Framework Data Provider for SQL Server.

## On-premises data sources

### Supported by in-memory and DirectQuery models

|Datasource | In-memory provider | DirectQuery provider |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0, Microsoft OLE DB Provider for SQL Server, .NET Framework Data Provider for SQL Server | .NET Framework Data Provider for SQL Server |
| SQL Server Data Warehouse |SQL Server Native Client 11.0, Microsoft OLE DB Provider for SQL Server, .NET Framework Data Provider for SQL Server | .NET Framework Data Provider for SQL Server |
| Oracle |Microsoft OLE DB Provider for Oracle, Oracle Data Provider for .NET |Oracle Data Provider for .NET | |
| Teradata |OLE DB Provider for Teradata, Teradata Data Provider for .NET |Teradata Data Provider for .NET | |
| | | |

> [!NOTE]
> For in-memory models, OLE DB providers can provide better performance for large-scale data. When choosing between different providers for the same data source, try the OLE DB provider first.  

### Supported by in-memory models only

|Database  |
|---------|---------|---------|
|Access Database     | 
|SQL Server Analysis Services     | 
|IBM Informix (beta) | 
|JSON document     | 
|Lines from binary     | 
|MySQL Database     | 
|PostgreSQL Database    | Yes | No
|SAP HANA   | Yes | No
|SAP Business Warehouse    | Yes | No
|Sybase Database     | Yes | No
|||

|File  |  
|---------|---------|
|Excel workbook     |
|Folder     | 
|JSON | 
|Text/CSV    | 
|XML table    | 
|||

|Online services  |  
|---------|---------|
|Dynamics 365      |
|Exhange Online     |
|Saleforce Objects    | 
|Salesforce Reports     |
|SharePoint Online List     |
|||

|Other  |  
|---------|---------|
|Active Directory      | 
|Exhange     |  
|OData Feed     | 
|ODBC query     | 
|OLE DB  | 
|SharePoint list | 
|||

## See also

[Data sources supported in SQL Server Analysis Services tabular 1200  models](data-sources-supported-ssas-tabular.md)

[Data sources supported in Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
