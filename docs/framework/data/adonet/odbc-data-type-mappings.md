---
title: "ODBC データ型のマッピング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ODBC データ型のマッピング
.NET Framework Data Provider for ODBC \(<xref:System.Data.Odbc>\) のデータ型から推論される [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の型を次の表に示します。  <xref:System.Data.Odbc.OdbcDataReader> の型指定されたアクセサー メソッドも示します。  
  
|ODBC 型|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の型指定されたアクセサー|  
|------------|-------------------------------------------------------------------|------------------------------------------------------------------------------|  
|SQL\_BIGINT|Int64|GetInt64\(\)|  
|SQL\_BINARY|Byte\[\]|GetBytes\(\)|  
|SQL\_BIT|Boolean|GetBoolean\(\)|  
|SQL\_CHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
|SQL\_DECIMAL|Decimal \(10 進数型\)|GetDecimal\(\)|  
|SQL\_DOUBLE|Double \(倍精度浮動小数点型\)|GetDouble\(\)|  
|SQL\_GUID|Guid|GetGuid\(\)|  
|SQL\_INTEGER|Int32|GetInt32\(\)|  
|SQL\_LONG\_VARCHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
|SQL\_LONGVARBINARY|Byte\[\]|GetBytes\(\)|  
|SQL\_NUMERIC|Decimal \(10 進数型\)|GetDecimal\(\)|  
|SQL\_REAL|Single|GetFloat\(\)|  
|SQL\_SMALLINT|Int16|GetInt16\(\)|  
|SQL\_TINYINT|Byte|GetByte\(\)|  
|SQL\_TYPE\_TIMES|DateTime|GetDateTime\(\)|  
|SQL\_TYPE\_TIMESTAMP|DateTime|GetDateTime\(\)|  
|SQL\_VARBINARY|Byte\[\]|GetBytes\(\)|  
|SQL\_WCHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
|SQL\_WLONGVARCHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
|SQL\_WVARCHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|  
  
## 参照  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)