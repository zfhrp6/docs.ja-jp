---
title: "ODBC スキーマ コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45cfed80decc2336c5a2bacf24fd075c2b81c531
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-schema-collections"></a>ODBC スキーマ コレクション
ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 ODBC ドライバーでのスキーマ コレクションのサポートについて説明します。  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Microsoft SQL Server ODBC Driver  
 Microsoft SQL Server ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。  
  
-   [テーブル]  
  
-   Indexes  
  
-   列  
  
-   手順  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   ビュー  
  
### <a name="tables-and-views"></a>Tables と Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|REMARKS|String|  
  
### <a name="indexes"></a>Indexes  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|NON_UNIQUE|Int16|  
|INDEX_QUALIFIER|String|  
|INDEX_NAME|String|  
|TYPE|Int16|  
|ORDINAL_POSITION|Int16|  
|COLUMN_NAME|String|  
|ASC_OR_DESC|String|  
|CARDINATLITY|Int32|  
|PAGES|Int32|  
|FILTER_CONDITION|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="columns"></a>列  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedures"></a>手順  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int32|  
|NUM_OUTPUT_PARAMS|Int32|  
|NUM_RESULT_SETS|Int32|  
|REMARKS|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
## <a name="microsoft-oracle-odbc-driver"></a>Microsoft Oracle ODBC Driver  
 Microsoft SQL Server Oracle ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。  
  
-   [テーブル]  
  
-   列  
  
-   手順  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   ビュー  
  
-   Indexes  
  
### <a name="tables-and-views"></a>Tables と Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|REMARKS|String|  
  
### <a name="columns"></a>列  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>手順  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|REMARKS|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|OVERLOAD|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Microsoft Jet ODBC Driver  
 Microsoft Jet ODBC Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。  
  
-   [テーブル]  
  
-   Indexes  
  
-   列  
  
-   手順  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   ビュー  
  
### <a name="tables-and-views"></a>Tables と Views  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|REMARKS|String|  
  
### <a name="columns"></a>列  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>手順  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|REMARKS|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|PRECISION|Int32|  
|LENGTH|Int32|  
|SCALE|Int16|  
|RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|OVERLOAD|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|NULLABLE|Int16|  
|REMARKS|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
  
## <a name="see-also"></a>参照  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
