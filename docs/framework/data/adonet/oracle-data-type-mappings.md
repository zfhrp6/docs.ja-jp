---
title: "Oracle データ型のマッピング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Oracle データ型のマッピング
次の表に、Oracle データ型およびその <xref:System.Data.OracleClient.OracleDataReader> へのマップを示します。  
  
|Oracle データ型|OracleDataReader.GetValue によって返される .NET Framework データ型|OracleDataReader.GetOracleValue によって返される OracleClient データ型|解説|  
|-----------------|------------------------------------------------------------|----------------------------------------------------------------|--------|  
|**BFILE**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal \(10 進数型\)**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型は **NUMBER** データ型のエイリアスであり、<xref:System.Data.OracleClient.OracleDataReader> が浮動小数点数値ではなく **System.Decimal** または <xref:System.Data.OracleClient.OracleNumber> を返すことを目的として用意されています。  .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**INTEGER**|**Decimal \(10 進数型\)**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型は **NUMBER\(38\)** データ型のエイリアスであり、<xref:System.Data.OracleClient.OracleDataReader> が整数値ではなく **System.Decimal** または <xref:System.Data.OracleClient.OracleNumber> を返すことを目的として用意されています。  .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO SECOND**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**Decimal \(10 進数型\)**|<xref:System.Data.OracleClient.OracleNumber>|.NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte\[\]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR** データ型は <xref:System.Data.OracleClient.OracleDataReader> オブジェクトではサポートされていません。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**UNSIGNED INTEGER**|**Number**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型は **NUMBER\(38\)** データ型のエイリアスであり、<xref:System.Data.OracleClient.OracleDataReader> が符号なし整数値ではなく **System.Decimal** または <xref:System.Data.OracleClient.OracleNumber> を返すことを目的として用意されています。  .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 次の表に、パラメーターとしてバインドする場合に使用する Oracle データ型および .NET Framework データ型 \(**System.Data.DbType** および <xref:System.Data.OracleClient.OracleType>\) を示します。  
  
|Oracle データ型|パラメーターとしてバインドする DbType 列挙型|パラメーターとしてバインドする OracleType 列挙型|解説|  
|-----------------|--------------------------------|------------------------------------|--------|  
|**BFILE**||**BFile**|Oracle では、**BFILE** パラメーターとしてのみ **BFILE** をバインドできます。  .NET Data Provider for Oracle では、**byte\[\]** や <xref:System.Data.OracleClient.OracleBinary> など、**BFILE** 以外の値をバインドしようとした場合に、自動的にこれを構築することはありません。|  
|**BLOB**||**Blob**|Oracle では、**BLOB** パラメーターとしてのみ **BLOB** をバインドできます。  .NET Data Provider for Oracle では、**byte\[\]** や <xref:System.Data.OracleClient.OracleBinary> など、**BLOB** 以外の値をバインドしようとした場合に、自動的にこれを構築することはありません。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle では、**CLOB** パラメーターとしてのみ **CLOB** をバインドできます。  .NET Data Provider for Oracle では、**System.String** や <xref:System.Data.OracleClient.OracleString> など、**CLOB** 以外の値をバインドしようとした場合に、自動的にこれを構築することはありません。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> により **System.Data.DBType** および <xref:System.Data.OracleClient.OracleType> が決定されます。|  
|**INTEGER**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> により **System.Data.DBType** および <xref:System.Data.OracleClient.OracleType> が決定されます。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**INTERVAL DAY TO SECOND**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**2 項**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle では、**NCLOB** パラメーターとしてのみ **NCLOB** をバインドできます。  .NET Data Provider for Oracle では、**System.String** や <xref:System.Data.OracleClient.OracleString> など、**NCLOB** 以外の値をバインドしようとした場合に、自動的にこれを構築することはありません。|  
|**NUMBER**|**VarNumeric**|**Number**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**2 項**|**Raw**||  
|**REF CURSOR**||**カーソル**|詳細については、「[Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)」を参照してください。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**Timestamp**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**UNSIGNED INTEGER**|**Byte、UInt16、UInt32、UInt64、Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> により **System.Data.DBType** および <xref:System.Data.OracleClient.OracleType> が決定されます。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 <xref:System.Data.OracleClient.OracleParameter> オブジェクトの <xref:System.Data.OracleClient.OracleParameter.Value%2A> プロパティで使用される **InputOutput** 値、**Output** 値、および **ReturnValue** **ParameterDirection** 値は、入力値が Oracle データ型 \(<xref:System.Data.OracleClient.OracleNumber> や <xref:System.Data.OracleClient.OracleString> など\) でない限り、.NET Framework データ型となります。  これは **REF CURSOR**、**BFILE**、または **LOB** データ型には適用されません。  
  
## 参照  
 [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)