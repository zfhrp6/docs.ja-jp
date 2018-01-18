---
title: "Oracle データ型 Mappings1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: adb0fc332e00e766a62d0af1c110c5a7ce2d42c3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-data-type-mappings"></a>Oracle データ型のマッピング
次の表に、Oracle データ型およびその <xref:System.Data.OracleClient.OracleDataReader> へのマップを示します。  
  
|Oracle データ型|OracleDataReader.GetValue によって返される .NET Framework データ型|OracleDataReader.GetOracleValue によって返される OracleClient データ型|コメント|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型のエイリアスでは、**数**データ型とは、できるように、<xref:System.Data.OracleClient.OracleDataReader>を返します、 **System.Decimal**または<xref:System.Data.OracleClient.OracleNumber>浮動小数点値の代わりにします。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型のエイリアスでは、 **NUMBER(38)**データ型とは、できるように、<xref:System.Data.OracleClient.OracleDataReader>を返します、 **System.Decimal**または<xref:System.Data.OracleClient.OracleNumber>整数値の代わりにします。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO 秒**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|.NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR**では、データ型はサポートされていない、<xref:System.Data.OracleClient.OracleDataReader>オブジェクト。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ローカルのタイム ゾーンのタイムスタンプ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**タイム ゾーンのタイムスタンプ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**符号なし整数**|**数値**|<xref:System.Data.OracleClient.OracleNumber>|このデータ型のエイリアスでは、 **NUMBER(38)**データ型とは、できるように、<xref:System.Data.OracleClient.OracleDataReader>を返します、 **System.Decimal**または<xref:System.Data.OracleClient.OracleNumber>符号なし整数値の代わりにします。 .NET Framework データ型を使用することで、オーバーフローが発生する場合があります。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 次の表は、Oracle データ型および .NET Framework のデータ型 (**System.Data.DbType**と<xref:System.Data.OracleClient.OracleType>) パラメーターとしてバインドするときに使用します。  
  
|Oracle データ型|パラメーターとしてバインドする DbType 列挙型|パラメーターとしてバインドする OracleType 列挙型|コメント|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle では、バインドのみが許可、 **BFILE**として、 **BFILE**パラメーター。 .NET Data Provider for Oracle は自動的に作成できませんいずれかの以外にバインドしようとする場合**BFILE**などの値**byte[]**または<xref:System.Data.OracleClient.OracleBinary>です。|  
|**BLOB**||**Blob**|Oracle では、バインドのみが許可、 **BLOB**として、 **BLOB**パラメーター。 .NET Data Provider for Oracle は自動的に作成できませんいずれかの以外にバインドしようとする場合**BLOB**などの値**byte[]**または<xref:System.Data.OracleClient.OracleBinary>です。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle では、バインドのみが許可、 **CLOB**として、 **CLOB**パラメーター。 .NET Data Provider for Oracle は自動的に作成できませんいずれかの以外にバインドしようとする場合**CLOB**などの値**System.String**または<xref:System.Data.OracleClient.OracleString>です。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定、 **System.Data.DBType**と<xref:System.Data.OracleClient.OracleType>です。|  
|**INTEGER**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number します。**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定、 **System.Data.DBType**と<xref:System.Data.OracleClient.OracleType>です。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**INTERVAL DAY TO 秒**|**オブジェクト**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle では、バインドのみが許可、 **NCLOB**として、 **NCLOB**パラメーター。 .NET Data Provider for Oracle は自動的に作成できませんいずれかの以外にバインドしようとする場合**NCLOB**などの値**System.String**または<xref:System.Data.OracleClient.OracleString>です。|  
|**NUMBER**|**VarNumeric**|**数値**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**Binary**|**Raw**||  
|**REF CURSOR**||**カーソル**|詳細については、次を参照してください。 [Oracle REF Cursor](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)です。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**タイムスタンプ**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**ローカルのタイム ゾーンのタイムスタンプ**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**タイム ゾーンのタイムスタンプ**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> は、Oracle 9i クライアントとサーバー ソフトウェアの両方を使用している場合のみ使用できます。|  
|**符号なし整数**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>決定、 **System.Data.DBType**と<xref:System.Data.OracleClient.OracleType>です。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **InputOutput**、**出力**、および**ReturnValue** **ParameterDirection**によって使用される値、 <xref:System.Data.OracleClient.OracleParameter.Value%2A> のプロパティ<xref:System.Data.OracleClient.OracleParameter>入力値が、Oracle データ型でない限り、オブジェクトは .NET Framework データ型 (たとえば、<xref:System.Data.OracleClient.OracleNumber>または<xref:System.Data.OracleClient.OracleString>)。 これには適用されません**REF CURSOR**、 **BFILE**、または**LOB**データ型。  
  
## <a name="see-also"></a>参照  
 [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
