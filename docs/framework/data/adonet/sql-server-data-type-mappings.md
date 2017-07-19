---
title: "SQL Server データ型のマッピング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fafdc31a-f435-4cd3-883f-1dfadd971277
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# SQL Server データ型のマッピング
SQL Server と .NET Framework は異なる型システムを使用しています。  たとえば、.NET Framework の <xref:System.Decimal> 構造体の最大小数点以下桁数は 28 ですが、SQL Server の decimal データ型と numeric データ型の最大小数点以下桁数は 38 です。  データを読み書きするときにデータの整合性を保つために、<xref:System.Data.SqlClient.SqlDataReader> では、.NET Framework の型を返すアクセサー メソッドと共に、<xref:System.Data.SqlTypes> のオブジェクトを返す SQL Server 固有の型指定されたアクセサー メソッドを公開しています。  SQL Server の型と .NET Framework の型は、両方とも <xref:System.Data.DbType> および <xref:System.Data.SqlDbType> クラスの列挙によって表されます。これらは <xref:System.Data.SqlClient.SqlParameter> データ型を指定するときに使用できます。  
  
 推論される [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型、<xref:System.Data.DbType> 列挙と <xref:System.Data.SqlDbType> 列挙、および <xref:System.Data.SqlClient.SqlDataReader> のアクセサー メソッドを次の表に示します。  
  
|SQL Server データベース エンジンの型|.NET Framework 型|SqlDbType 列挙|SqlDataReader SqlTypes の型指定されたアクセサー|DbType 列挙|SqlDataReader DbType の型指定されたアクセサー|  
|------------------------------|----------------------|------------------|-----------------------------------------|---------------|---------------------------------------|  
|bigint|Int64|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt64%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt64%2A>|  
|バイナリ|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|ビット|Boolean|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBoolean%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBoolean%2A>|  
|char|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>,<br /><br /> <xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|date<br /><br /> \(SQL Server 2008 以降\)|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime2<br /><br /> \(SQL Server 2008 以降\)|DateTime|<xref:System.Data.SqlDbType>|なし|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetimeoffset<br /><br /> \(SQL Server 2008 以降\)|DateTimeOffset|<xref:System.Data.SqlDbType>|none|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|  
|decimal|Decimal \(10 進数型\)|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|FILESTREAM 属性 \(varbinary\(max\)\)|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|float|Double \(倍精度浮動小数点型\)|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDouble%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDouble%2A>|  
|イメージ|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|int|Int32|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt32%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt32%2A>|  
|money|Decimal \(10 進数型\)|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nchar|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|ntext|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|数値|Decimal \(10 進数型\)|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nvarchar|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|実数|Single|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlSingle%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetFloat%2A>|  
|rowversion|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|smalldatetime|DateTime|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|smallint|Int16|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt16%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetInt16%2A>|  
|smallmoney|Decimal \(10 進数型\)|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|sql\_variant|Object\*|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A> \*|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A> \*|  
|テキスト|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|時間<br /><br /> \(SQL Server 2008 以降\)|TimeSpan|<xref:System.Data.SqlDbType>|none|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|タイムスタンプ|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|tinyint|Byte|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlByte%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetByte%2A>|  
|uniqueidentifier|Guid|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlGuid%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetGuid%2A>|  
|varbinary|Byte\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|varchar|String<br /><br /> Char\[\]|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType>, <xref:System.Data.DbType>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|xml|Xml|<xref:System.Data.SqlDbType>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A>|<xref:System.Data.DbType>|none|  
  
 \* `sql_variant` の基になる型がわかっている場合は、特定の型指定されたアクセサーを使用してください。  
  
## [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]オンライン ブックのリファレンス  
 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] データ型の詳細については、「[データ型 \(データベース エンジン\)](http://go.microsoft.com/fwlink/?LinkID=107468)」を参照してください。  
  
## 参照  
 [SQL Server データ型と ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)   
 [SQL Server のバイナリ データと大きな値のデータ](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)   
 [ADO.NET でのデータ型のマッピング](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [パラメーターおよびパラメーター データ型の構成](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)