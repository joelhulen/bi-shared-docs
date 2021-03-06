---
title: "OLE DB Schema Rowsets | Microsoft Docs"
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
# OLE DB Schema Rowsets

  The following OLE DB schema rowsets are supported by the Microsoft XML for Analysis (XMLA) provider. Use the **DISCOVER_ENUMERATORS** rowset with the [Discover](../../xmla/xml-elements-methods-discover.md) method to check whether a particular data source provider supports a rowset.  
  
 You can also find detailed information about these rowsets by searching for the topic "Schema Rowsets" in the OLE DB Programmer's Reference portion of the MSDN® Library at the Microsoft Web site.  
  
 The following table describes this schema rowset.  
  
|Rowset|Description|  
|------------|-----------------|  
|**DBSCHEMA_ASSERTIONS**|Identifies the assertions that are defined in the catalog and owned by a given user.|  
|[DBSCHEMA_CATALOGS Rowset](dbschema-catalogs-rowset.md) <sup>1</sup>|Identifies the physical attributes associated with catalogs that are accessible from the database management system (DBMS). For some systems, such as Microsoft Access, there may be only one catalog. For SQL Server, this rowset enumerates all catalogs (databases) defined in the system database.|  
|**DBSCHEMA_CHARACTER_SETS**|Identifies the character sets that are defined in the catalog and accessible to a given user.|  
|**DBSCHEMA_CHECK_CONSTRAINTS**|Identifies the check constraints that are defined in the catalog and owned by a given user.|  
|**DBSCHEMA_CHECK_CONSTRAINTS_BY_TABLE**|Identifies the check constraints for a given table, defined in a catalog owned by a given user.|  
|**DBSCHEMA_COLLATIONS**|Identifies the character collations that are defined in the catalog and accessible to a given user.|  
|**DBSCHEMA_COLUMN_DOMAIN_USAGE**|Identifies the columns defined in the catalog that are dependent on a domain defined in the catalog and owned by a given user.|  
|**DBSCHEMA_COLUMN_PRIVILEGES**|Identifies the privileges on columns of tables that are defined in the catalog and are available to or granted by a given user.|  
|[DBSCHEMA_COLUMNS Rowset](dbschema-columns-rowset.md) <sup>1</sup>|Provides column information for all columns meeting the provided restriction criteria.|  
|**DBSCHEMA_CONSTRAINT_COLUMN_USAGE**|Identifies the columns used by referential constraints, unique constraints, check constraints, and assertions and that are defined in the catalog and owned by a given user.|  
|**DBSCHEMA_CONSTRAINT_TABLE_USAGE**|Identifies the tables that are used by referential constraints, unique constraints, check constraints, and assertions and that are defined in the catalog and owned by a given user.|  
|**DBSCHEMA_FOREIGN_KEYS**|Identifies the foreign key columns defined in the catalog by a given user. This schema rowset is built upon several ISO schema views as a convenience to the non-SQL programmer. If supported, this schema rowset must be synchronized with the related ISO views (**REFERENTIAL_CONSTRAINTS** and **CONSTRAINT_COLUMN_USAGE**).|  
|**DBSCHEMA_INDEXES**|Identifies the indexes that are defined in the catalog and owned by a given user.|  
|**DBSCHEMA_KEY_COLUMN_USAGE**|Identifies the columns that are defined in the catalog and are constrained as keys by a given user.|  
|**DBSCHEMA_PRIMARY_KEYS**|Identifies the primary key columns defined in the catalog by a given user. This schema rowset is built upon an ISO schema view as a convenience to the non-SQL programmer. If supported, this schema rowset must be synchronized with the related ISO view (**CONSTRAINT_COLUMN_USAGE**).|  
|**DBSCHEMA_PROCEDURE_COLUMNS**|Returns information about the columns of rowsets returned by procedures.|  
|**DBSCHEMA_PROCEDURE_PARAMETERS**|Returns information about the parameters and return codes of procedures.|  
|**DBSCHEMA_PROCEDURES**|Identifies the procedures that are defined in the catalog and owned by a given user. This is an OLE DB extension.|  
|[DBSCHEMA_PROVIDER_TYPES Rowset](dbschema-provider-types-rowset.md) <sup>1</sup>|Identifies the (base) data types supported by the data provider.|  
|**DBSCHEMA_REFERENTIAL_CONSTRAINTS**|Identifies the referential constraints that are defined in the catalog and owned by a given user.|  
|**DBSCHEMA_SCHEMATA**|Identifies the schemas that are owned by a given user.|  
|**DBSCHEMA_SQL_LANGUAGES**|Identifies the conformance levels, options, and dialects supported by the SQL implementation processing data defined in the catalog.|  
|**DBSCHEMA_STATISTICS**|Identifies the statistics that are defined in the catalog and owned by a given user.<br /><br /> This table is not related to the **TABLE_STATISTICS** rowset.|  
|**DBSCHEMA_TABLE_CONSTRAINTS**|Identifies the table constraints that are defined in the catalog and owned by a given user.|  
|**DBSCHEMA_TABLE_PRIVILEGES**|Identifies the privileges on tables that are defined in the catalog and available to or granted by a given user.|  
|**DBSCHEMA_TABLE_STATISTICS**|Describes the available set of statistics on tables in the provider.<br /><br /> This rowset is not related to the **STATISTICS** rowset.|  
|[DBSCHEMA_TABLES Rowset](dbschema-tables-rowset.md) <sup>1</sup>|Identifies the measure groups and dimensions exposed as tables within SQL Server Analysis Services.|  
|**DBSCHEMA_TABLES_INFO** <sup>1</sup>|Identifies the tables (including views) that are defined in the catalog and accessible to a given user.|  
|**DBSCHEMA_TRANSLATIONS**|Identifies the character translations that are defined in the catalog and accessible to a given user.|  
|**DBSCHEMA_TRUSTEE**|Enumerates the trustees for a data source.|  
|**DBSCHEMA_USAGE_PRIVILEGES**|Identifies the **USAGE** privileges on objects that are defined in the catalog and are available to or granted by a given user.|  
|**DBSCHEMA_VIEW_COLUMN_USAGE**|Identifies the views that are defined in the catalog and accessible to a given user.|  
|**DBSCHEMA_VIEW_TABLE_USAGE**|Identifies the tables on which viewed tables, defined in the catalog and owned by a given user, are dependent.|  
|**DBSCHEMA_VIEWS**|Identifies the views that are defined in the catalog and accessible to a given user.|  
  
 <sup>1</sup> Indicates schema rowsets supported by the MSOLAP data source provider for the XMLA provider.  

  
  
