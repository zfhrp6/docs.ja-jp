---
title: "dateTimeInvalidLocalFormat MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "dates [.NET Framework], formatting"
  - "invalid date time local format"
  - "invalid local formats"
  - "MDAs (managed debugging assistants), invalid local formats"
  - "managed debugging assistants (MDAs), invalid local formats"
  - "dateTimeInvalidLocalFormat MDA"
  - "date formatting"
  - "time formatting"
  - "UTC formatting"
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# dateTimeInvalidLocalFormat MDA
`dateTimeInvalidLocalFormat` MDA は、世界協定時刻 \(UTC: Universal Coordinated Time\) として保存されている <xref:System.DateTime> インスタンスが、ローカル <xref:System.DateTime> インスタンス専用の形式で書式指定されたときにアクティブになります。  この MDA は、未指定または既定の <xref:System.DateTime> インスタンスに対してはアクティブになりません。  
  
## 症状  
 アプリケーションで、次のようなローカル形式を使用して UTC <xref:System.DateTime> インスタンスを手動でシリアル化しています。  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### 原因  
 <xref:System.DateTime.ToString%2A?displayProperty=fullName> メソッドの 'z' 形式には、ローカル タイム ゾーン オフセット \(たとえば、シドニー時間の場合は "\+10:00"\) が含まれます。  そのため、<xref:System.DateTime> の値がローカルの場合にのみ、有意な結果が生成されます。  値が UTC 時刻の場合、<xref:System.DateTime.ToString%2A?displayProperty=fullName> には、ローカル タイム ゾーン オフセットが含まれますが、タイム ゾーン指定子を表示したり、調整したりされません。  
  
### 解決策  
 UTC <xref:System.DateTime> インスタンスが UTC であることを示すように書式指定する必要があります。  UTC 時刻の形式としては、次のように 'Z' を使用して UTC 時刻を示すようにすることをお勧めします。  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 また、インスタンスがローカル、UTC、未指定のいずれの場合でも正しくシリアル化する <xref:System.DateTime.Kind%2A> プロパティを利用して <xref:System.DateTime> をシリアル化する "o" 形式もあります。  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## ランタイムへの影響  
 この MDA はランタイムに影響しません。  
  
## 出力  
 この MDA がアクティブになっても特別な出力は生成されませんが、呼び出し履歴を使用すると、この MDA をアクティブにした <xref:System.DateTime.ToString%2A> 呼び出しの位置を確認できます。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 次のように、<xref:System.Xml.XmlConvert> クラスや <xref:System.Data.DataSet> クラスを使用して UTC <xref:System.DateTime> 値を間接的にシリアル化するアプリケーションについて考えてみます。  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> と <xref:System.Data.DataSet> のシリアル化では、既定でシリアル化用のローカル形式を使用します。  UTC など、他の種類の <xref:System.DateTime> 値をシリアル化する場合は、追加のオプションが必要です。  
  
 この例では、`XmlConvert` での `ToString` 呼び出しに `XmlDateTimeSerializationMode.RoundtripKind` を渡します。  これで、データが UTC 時間としてシリアル化されます。  
  
 <xref:System.Data.DataSet> を使用する場合は、<xref:System.Data.DataColumn> オブジェクトの <xref:System.Data.DataColumn.DateTimeMode%2A> プロパティを <xref:System.Data.DataSetDateTime> に設定します。  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## 参照  
 <xref:System.Globalization.DateTimeFormatInfo>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)