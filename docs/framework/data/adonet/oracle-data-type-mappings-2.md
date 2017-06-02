---
title: "Oracle データ型のマッピング | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2521bcc-0051-4f35-8be3-e8723edeaf6f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Oracle データ型のマッピング
.NET Framework Data Provider for Oracle \([!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]\) のデータ型から推論される <xref:System.Data.OracleClient> の型を次の表に示します。<xref:System.Data.OracleClient.OracleDataReader> の型指定されたアクセサー メソッドも示します。  
  
|Oracle 型|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の型指定されたアクセサー|OracleType の型指定されたアクセサー|  
|--------------|-------------------------------------------------------------------|------------------------------------------------------------------------------|-----------------------------|  
|BFILE|Byte\[\]|GetBytes\(\)|GetOracleBFile\(\)|  
|BLOB|Byte\[\]|GetBytes\(\)|GetOracleLob\(\)|  
|CHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|CLOB|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleLob\(\)|  
|DATE|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|FLOAT|Decimal \(10 進数型\)|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|INTEGER|Decimal \(10 進数型\)|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|INTERVAL YEAR TO MONTH \*|Int32|GetInt32\(\)|GetOracleMonthSpan\(\)|  
|INTERVAL DAY TO SECOND \*|TimeSpan|GetTimeSpan\(\)|GetOracleTimeSpan\(\)|  
|LONG|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|LONG RAW|Byte\[\]|GetBytes\(\)|GetOracleBinary\(\)|  
|NCHAR|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|NCLOB|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleLob\(\)|  
|NUMBER|Decimal \(10 進数型\)|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|NVARCHAR2|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|RAW|Byte\[\]|GetBytes\(\)|GetOracleBinary\(\)|  
|REF CURSOR||||  
|ROWID|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
|TIMESTAMP \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|TIMESTAMP WITH LOCAL TIME ZONE \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|TIMESTAMP WITH TIME ZONE \*|DateTime|GetDateTime\(\)|GetOracleDateTime\(\)|  
|UNSIGNED INTEGER|Decimal \(10 進数型\)|GetDecimal\(\)|GetOracleNumber\(\) \*\*|  
|VARCHAR2|String<br /><br /> Char\[\]|GetString\(\)<br /><br /> GetChars\(\)|GetOracleString\(\)|  
  
 \* この Oracle 型は、クライアントとサーバーの両方に Oracle 9i ソフトウェアを使用している場合にだけ使用できます。  
  
 \*\* Oracle の NUMBER 型の有効桁数は 38 桁です。[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の `decimal` 型は 28 桁に制限されています。 Oracle の NUMBER 型を [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の `decimal` 型に読み込む場合、28 桁を超える NUMBER 型の値では `OverflowException` がスローされます。`OracleDataReader` から Oracle の NUMBER 型の値を読み込む場合は、`GetOracleNumber` の型指定されたアクセサー メソッドを呼び出し、`OracleNumber` として Oracle の NUMBER 型の値を返すことをお勧めします。`DataSet` にデータを読む込む場合は、`FillError` イベントを使用して、`OverflowException` が発生したかどうかを確認し、発生時に適切な対応をすることができます。`FillError` イベントについては、「[DataAdapter のイベント処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)」を参照してください。  
  
## 参照  
 [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)