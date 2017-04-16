---
title: "OLE DB スキーマ コレクション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# OLE DB スキーマ コレクション
ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 OLE DB プロバイダーでのスキーマ コレクションのサポートについて説明します。  
  
## Microsoft SQL Server OLE DB Provider  
 Microsoft SQL Server OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。  
  
-   \[テーブル\]  
  
-   列  
  
-   手順  
  
-   ProcedureParameters  
  
-   Catalog  
  
-   Indexes  
  
### \[テーブル\]  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|TABLE\_TYPE|String|  
|TABLE\_GUID|Guid|  
|DESCRIPTION|String|  
|TABLE\_PROPID|Int64|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### 列  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_HASDEFAULT|Boolean|  
|COLUMN\_DEFAULT|String|  
|COLUMN\_FLAGS|Int64|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|TYPE\_GUID|Guid|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DATETIME\_PRECISION|Int64|  
|CHARACTER\_SET\_CATALOG|String|  
|CHARACTER\_SET\_SCHEMA|String|  
|CHARACTER\_SET\_NAME|String|  
|COLLATION\_CATALOG|String|  
|COLLATION\_SCHEMA|String|  
|COLLATION\_NAME|String|  
|DOMAIN\_CATALOG|String|  
|DOMAIN\_SCHEMA|String|  
|DOMAIN\_NAME|String|  
|DESCRIPTION|String|  
|COLUMN\_LCID|Int32|  
|COLUMN\_COMPFLAGS|Int32|  
|COLUMN\_SORTID|Int32|  
|COLUMN\_TDSCOLLATION|Byte\[\]|  
|IS\_COMPUTED|Boolean|  
  
### 手順  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CATALOG|String|  
|PROCEDURE\_SCHEMA|String|  
|PROCEDURE\_NAME|String|  
|PROCEDURE\_TYPE|Int16|  
|PROCEDURE\_DEFINITION|String|  
|DESCRIPTION|String|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CATALOG|String|  
|PROCEDURE\_SCHEMA|String|  
|PROCEDURE\_NAME|String|  
|PARAMETER\_NAME|String|  
|ORDINAL\_POSITION|Int32|  
|PARAMETER\_TYPE|Int32|  
|PARAMETER\_HASDEFAULT|Boolean|  
|PARAMETER\_DEFAULT|String|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DESCRIPTION|String|  
|TYPE\_NAME|String|  
|LOCAL\_TYPE\_NAME|String|  
  
### Catalog  
  
|ColumnName|DataType|  
|----------------|--------------|  
|CATALOG\_NAME|String|  
|DESCRIPTION|String|  
  
### Indexes  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|INDEX\_CATALOG|String|  
|INDEX\_SCHEMA|String|  
|INDEX\_NAME|String|  
|PRIMARY\_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYPE|Int32|  
|FILL\_FACTOR|Int32|  
|INITIAL\_SIZE|Int32|  
|NULLS|Int32|  
|SORT\_BOOKMARKS|Boolean|  
|AUTO\_UPDATE|Boolean|  
|NULL\_COLLATION|Int32|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_NAME|String|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|COLLATION|Int16|  
|CARDINALITY|Decimal \(10 進数型\)|  
|PAGES|Int32|  
|FILTER\_CONDITION|String|  
|INTEGRATED|Boolean|  
  
## Microsoft Oracle OLE DB Provider  
 Microsoft Oracle OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。  
  
-   \[テーブル\]  
  
-   列  
  
-   手順  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   ビュー  
  
-   Indexes  
  
### \[テーブル\]  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|TABLE\_TYPE|String|  
|TABLE\_GUID|Guid|  
|DESCRIPTION|String|  
|TABLE\_PROPID|Int64|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### 列  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_HASDEFAULT|Boolean|  
|COLUMN\_DEFAULT|String|  
|COLUMN\_FLAGS|Int64|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|TYPE\_GUID|Guid|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DATETIME\_PRECISION|Int64|  
|CHARACTER\_SET\_CATALOG|String|  
|CHARACTER\_SET\_SCHEMA|String|  
|CHARACTER\_SET\_NAME|String|  
|COLLATION\_CATALOG|String|  
|COLLATION\_SCHEMA|String|  
|COLLATION\_NAME|String|  
|DOMAIN\_CATALOG|String|  
|DOMAIN\_SCHEMA|String|  
|DOMAIN\_NAME|String|  
|DESCRIPTION|String|  
  
### 手順  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CATALOG|String|  
|PROCEDURE\_SCHEMA|String|  
|PROCEDURE\_NAME|String|  
|PROCEDURE\_TYPE|Int16|  
|PROCEDURE\_DEFINITION|String|  
|DESCRIPTION|String|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CATALOG|String|  
|PROCEDURE\_SCHEMA|String|  
|PROCEDURE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|ROWSET\_NUMBER|Int64|  
|ORDINAL\_POSITION|Int64|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|TYPE\_GUID|Guid|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DESCRIPTION|String|  
|OVERLOAD|Int16|  
  
### ビュー  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|VIEW\_DEFINITION|String|  
|CHECK\_OPTION|Boolean|  
|IS\_UPDATABLE|Boolean|  
|DESCRIPTION|String|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### Indexes  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|INDEX\_CATALOG|String|  
|INDEX\_SCHEMA|String|  
|INDEX\_NAME|String|  
|PRIMARY\_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYPE|Int32|  
|FILL\_FACTOR|Int32|  
|INITIAL\_SIZE|Int32|  
|NULLS|Int32|  
|SORT\_BOOKMARKS|Boolean|  
|AUTO\_UPDATE|Boolean|  
|NULL\_COLLATION|Int32|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_NAME|String|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|COLLATION|Int16|  
|CARDINALITY|Decimal \(10 進数型\)|  
|PAGES|Int32|  
|FILTER\_CONDITION|String|  
|INTEGRATED|Boolean|  
  
## Microsoft Jet OLE DB Provider  
 Microsoft Jet OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。  
  
-   \[テーブル\]  
  
-   列  
  
-   手順  
  
-   ビュー  
  
-   Indexes  
  
### \[テーブル\]  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|TABLE\_TYPE|String|  
|TABLE\_GUID|Guid|  
|DESCRIPTION|String|  
|TABLE\_PROPID|Int64|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### 列  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|COLUMN\_NAME|String|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_HASDEFAULT|Boolean|  
|COLUMN\_DEFAULT|String|  
|COLUMN\_FLAGS|Int64|  
|IS\_NULLABLE|Boolean|  
|DATA\_TYPE|Int32|  
|TYPE\_GUID|Guid|  
|CHARACTER\_MAXIMUM\_LENGTH|Int64|  
|CHARACTER\_OCTET\_LENGTH|Int64|  
|NUMERIC\_PRECISION|Int32|  
|NUMERIC\_SCALE|Int16|  
|DATETIME\_PRECISION|Int64|  
|CHARACTER\_SET\_CATALOG|String|  
|CHARACTER\_SET\_SCHEMA|String|  
|CHARACTER\_SET\_NAME|String|  
|COLLATION\_CATALOG|String|  
|COLLATION\_SCHEMA|String|  
|COLLATION\_NAME|String|  
|DOMAIN\_CATALOG|String|  
|DOMAIN\_SCHEMA|String|  
|DOMAIN\_NAME|String|  
|DESCRIPTION|String|  
  
### 手順  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE\_CATALOG|String|  
|PROCEDURE\_SCHEMA|String|  
|PROCEDURE\_NAME|String|  
|PROCEDURE\_TYPE|Int16|  
|PROCEDURE\_DEFINITION|String|  
|DESCRIPTION|String|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### ビュー  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|VIEW\_DEFINITION|String|  
|CHECK\_OPTION|Boolean|  
|IS\_UPDATABLE|Boolean|  
|DESCRIPTION|String|  
|DATE\_CREATED|DateTime|  
|DATE\_MODIFIED|DateTime|  
  
### Indexes  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE\_CATALOG|String|  
|TABLE\_SCHEMA|String|  
|TABLE\_NAME|String|  
|INDEX\_CATALOG|String|  
|INDEX\_SCHEMA|String|  
|INDEX\_NAME|String|  
|PRIMARY\_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYPE|Int32|  
|FILL\_FACTOR|Int32|  
|INITIAL\_SIZE|Int32|  
|NULLS|Int32|  
|SORT\_BOOKMARKS|Boolean|  
|AUTO\_UPDATE|Boolean|  
|NULL\_COLLATION|Int32|  
|ORDINAL\_POSITION|Int64|  
|COLUMN\_NAME|String|  
|COLUMN\_GUID|Guid|  
|COLUMN\_PROPID|Int64|  
|COLLATION|Int16|  
|CARDINALITY|Decimal \(10 進数型\)|  
|PAGES|Int32|  
|FILTER\_CONDITION|String|  
|INTEGRATED|Boolean|  
  
## 参照  
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)