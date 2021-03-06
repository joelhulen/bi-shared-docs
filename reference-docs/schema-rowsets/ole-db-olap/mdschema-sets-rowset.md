---
title: "MDSCHEMA_SETS Rowset | Microsoft Docs"
ms.date: 07/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
---
# MDSCHEMA_SETS Rowset

  Describes any sets that are currently defined in a database, including session-scoped sets.  
  
## Rowset Columns  
 The **MDSCHEMA_SETS** rowset contains the following columns.  
  
|Column name|Type indicator|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|The name of the database.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Not supported.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|The name of the cube.|  
|**SET_NAME**|**DBTYPE_WSTR**|The name of the set, as specified in the **CREATE SET** statement.|  
|**SCOPE**|**DBTYPE_I4**|The scope of the set:<br /><br /> **MDSET_SCOPE_GLOBAL** (**1**)<br /><br /> **MDSET_SCOPE_SESSION** (**2**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Not supported.|  
|**EXPRESSION**|**DBTYPE_WSTR**|The expression for the set.|  
|**DIMENSIONS**|**DBTYPE_WSTR**|A comma delimited list of hierarchies included in the set.|  
|**SET_CAPTION**|**DBTYPE_WSTR**|A label or caption associated with the set. The label or caption is used primarily for display purposes.|  
|**SET_DISPLAY_FOLDER**|**DBTYPE_WSTR**|A string that identifies the path of the display folder that the client application uses to show the set. The folder level separator is defined by the client application. For the tools and clients supplied by Analysis Services, the backslash (\\) is the level separator. To provide multiple display folders, use a semicolon (;) to separate the folders.|  
|**SET_EVALUATION_CONTEXT**|**DBTYPE_I4**|The context for the set. The set can be static or dynamic. This column can have one of the following values:<br /><br /> MDSET_RESOLUTION_STATIC=1<br /><br /> MDSET_RESOLUTION_DYNAMIC=2|  
  
 The rowset is sorted on **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**.  
  
## Restriction Columns  
 The **MDSCHEMA_SETS** rowset can be restricted on the columns listed in the following table.  
  
|Column name|Type indicator|Restriction State|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Optional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**SET_NAME**|**DBTYPE_WSTR**|Optional.|  
|**SCOPE**|**DBTYPE_I4**|Optional.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Optional.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|Optional.<br /><br /> Note: Only one hierarchy can be included, and only those named sets whose hierarchies exactly match the restriction are returned.|  
