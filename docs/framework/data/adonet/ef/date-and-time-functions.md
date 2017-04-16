---
title: "日付と時刻関数 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 日付と時刻関数
.NET Framework Data Provider for SQL Server \(SqlClient\) には、`System.DateTime` 型の入力値に対して操作を実行し、`string`、数値、または `System.DateTime` 値の結果を返す日付と時刻関数が用意されています。  これらの関数は、SqlClient の SqlServer 名前空間に存在します。  Entity Framework は、プロバイダーの名前空間プロパティを使用することにより、型や関数など、特定のコンストラクターに対してこのプロバイダーによってどのプレフィックスが使用されているかを特定できます。次の表に、SqlClient の日付と時刻関数を示します。  
  
|関数|説明|  
|--------|--------|  
|`DATEADD(` `datepart`, `number`, `date``)`|指定された日付に特定の期間を加えた新しい `DateTime` 型の値を返します。<br /><br /> **引数**<br /><br /> `datepart`: 新しい値を返す対象となる日付の要素を表す `String`。<br /><br /> `number`: `datepart` に加算する値 \(`Int32`、`Int64`、`Decimal`、`Double` のいずれか\)。<br /><br /> `date`: 有効桁数が 0 ～ 7 の `DateTime`、`DateTimeOffset`、`Time` のいずれかの値を返す式、または日付形式の文字列。<br /><br /> **戻り値**<br /><br /> 有効桁数が 0 ～ 7 の `DateTime`、`DateTimeOffset`、または `Time` の新しい値。<br /><br /> **例**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(` `datepart`, `startdate`, `enddate``)`|指定された 2 つの日付間の差を、日付および時刻の単位で返します。<br /><br /> **引数**<br /><br /> `datepart`: 差分を計算する日付の要素を表す `String`。<br /><br /> `startdate`: 計算の開始日として、有効桁数が 0 ～ 7 の `DateTime`、`DateTimeOffset`、`Time` のいずれかの値を返す式、または日付形式の文字列を指定します。<br /><br /> `enddate`: 計算の終了日として、有効桁数が 0 ～ 7 の `DateTime`、`DateTimeOffset`、`Time` のいずれかの値を返す式、または日付形式の文字列を指定します。<br /><br /> **戻り値**<br /><br /> `Int32`。<br /><br /> **例**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(` `datepart`, `date``)`|指定された日付の特定の日付構成要素を文字列で返します。<br /><br /> **引数**<br /><br /> `datepart`: 新しい値を返す対象となる日付の要素を表す `String`。<br /><br /> `date`: 有効桁数が 0 ～ 7 の `DateTime`、`DateTimeOffset`、`Time` のいずれかの値を返す式、または日付形式の文字列。<br /><br /> **戻り値**<br /><br /> 指定された日付について、特定の日付要素を表す文字列。<br /><br /> **例**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(` `datepart`, `date``)`|指定された日付について、特定の日付要素を整数で返します。<br /><br /> **引数**<br /><br /> `datepart`: 新しい値を返す対象となる日付の要素を表す `String`。<br /><br /> `date`: 有効桁数が 0 ～ 7 の `DateTime`、`DateTimeOffset`、`Time` のいずれかの値を返す式、または日付形式の文字列。<br /><br /> **戻り値**<br /><br /> 指定された日付の特定の日付要素を表す `Int32` 値。<br /><br /> **例**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(` `date` `)`|指定された日付の日を整数として返します。<br /><br /> **引数**<br /><br /> `date`:有効桁数が 0 ～ 7 の `DateTime` 型または `DateTimeOffset` 型の式。<br /><br /> **戻り値**<br /><br /> 指定された日付の日を表す `Int32` 値。<br /><br /> **例**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|datetime 値に使用する現在の日付と時刻を SQL Server の内部形式で生成します。<br /><br /> **戻り値**<br /><br /> 有効桁数が 3 の `DateTime` としての現在のシステム日時。<br /><br /> **例**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|UTC \(協定世界時またはグリニッジ標準時\) 形式の datetime 値を生成します。<br /><br /> **戻り値**<br /><br /> UTC 形式の有効桁数 3 の `DateTime` 値。<br /><br /> **例**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(` `date` `)`|指定された日付の月を整数として返します。<br /><br /> **引数**<br /><br /> `date`:有効桁数が 0 ～ 7 の `DateTime` 型または `DateTimeOffset` 型の式。<br /><br /> **戻り値**<br /><br /> 指定された日付の月を表す `Int32` 値。<br /><br /> **例**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(` `date` `)`|指定された日付の年を整数として返します。<br /><br /> **引数**<br /><br /> `date`:有効桁数が 0 ～ 7 の `DateTime` 型または `DateTimeOffset` 型の式。<br /><br /> **戻り値**<br /><br /> 指定された日付の年を表す `Int32` 値。<br /><br /> **例**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|有効桁数が 7 の `DateTime` 値を返します。<br /><br /> **戻り値**<br /><br /> 有効桁数が 7 の `DateTime` 値。<br /><br /> **例**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|UTC \(協定世界時またはグリニッジ標準時\) 形式の datetime 値を生成します。<br /><br /> **戻り値**<br /><br /> UTC 形式の有効桁数 7 の `DateTime` 値。<br /><br /> **例**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|有効桁数が 7 の `DateTimeOffset` 値を返します。<br /><br /> **戻り値**<br /><br /> UTC 形式の有効桁数 7 の `DateTimeOffset` 値。<br /><br /> **例**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 SqlClient でサポートされる日付と時刻の関数の詳細については、SqlClient プロバイダー マニフェストで指定した SQL Server のバージョンのドキュメントを参照してください。  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[日付と時間関数 \(Transact\-SQL\)](http://go.microsoft.com/fwlink/?LinkId=115908)|[日付と時間関数 \(Transact\-SQL\)](http://go.microsoft.com/fwlink/?LinkId=115909)|[日付と時間関数 \(Transact\-SQL\)](http://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## 参照  
 [Entity Framework 用 SqlClient 関数](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)