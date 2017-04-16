---
title: "文字列の .NET Framework データ型への変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 文字列の .NET Framework データ型への変換
文字列を .NET Framework データ型に変換するには、アプリケーションの要件に適合する **XmlConvert** メソッドを使用します。  **XmlConvert** クラスで利用可能なすべての変換メソッドの一覧については、「[XmlConvert メンバー](frlrfSystemXmlXmlConvertMembersTopic)」を参照してください。  
  
 **ToString** メソッドから返される文字列は、渡したデータを文字列に変換したものです。  変換に **XmlConvert** クラスを使用する .NET Framework 型の中には、**System.Convert** クラスのメソッドを使用しないものがいくつかあります。  **XmlConvert** クラスは XML Schema \(XSD\) のデータ型に準拠しており、**XmlConvert** によって変換できるデータ型は決まっています。  
  
 次の表は、.NET Framework データ型の一覧と、XML スキーマ \(XSD\) のデータ型マップを使用した場合に返される文字列を示しています。  これらの .NET Framework 型は、**System.Convert** で処理することはできません。  
  
|.NET Framework 型|返される文字列|  
|----------------------|-------------|  
|Boolean|"true"、"false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"\-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"\-INF"|  
|DateTime|形式は、yyyy\-MM\-ddTHH:mm:sszzzzzz およびそのサブセットです。|  
|Timespan|PnYnMnTnHnMnS の形式。つまり、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。|  
  
> [!NOTE]
>  表中の .NET Framework 型を **ToString** メソッドを使用して文字列に変換したときに返される文字列は基本型ではなく、XML スキーマ \(XSD\) 文字列型です。  
  
 **DateTime** 値型と **Timespan** 値型の違いは、**DateTime** が瞬間を表すのに対して、**TimeSpan** が時間間隔を表すことです。  **DateTime** および **Timespan** の形式は、XML スキーマ \(XSD\) のデータ型仕様で指定されています。  次に例を示します。  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 **出力**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 整数を文字列に変換するコードを次に示します。  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 **出力**  
  
 `<Number>200</Number>`  
  
 ただし、文字列を **Boolean**、**Single**、または **Double** に変換する場合、返される .NET Framework 型は、**System.Convert** クラスを使用したときに返される型とは異なります。  
  
## String から Boolean  
 **ToBoolean** メソッドを使用して文字列を **Boolean** に変換するときの入力文字列と生成される型の対応を次の表に示します。  
  
|有効な文字列入力パラメーター|出力される .NET Framework 型|  
|--------------------|----------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 たとえば、次のような XML があるとします。  
  
 **入力**  
  
```  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 いずれも次のコードによって解釈することができ、**bvalue** は **System.Boolean.True** になります。  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## String から Single  
 **ToSingle** メソッドを使用して文字列を **Single** に変換するときの入力文字列と生成される型の対応を次の表に示します。  
  
|有効な文字列入力パラメーター|出力される .NET Framework 型|  
|--------------------|----------------------------|  
|"INF"|Single.PositiveInfinity|  
|"\-INF"|Single.NegativeInfinity|  
  
## String から Double  
 **ToDouble** メソッドを使用して文字列を **Double** に変換するときの入力文字列と生成される型の対応を次の表に示します。  
  
|有効な文字列入力パラメーター|出力される .NET Framework 型|  
|--------------------|----------------------------|  
|"INF"|Double.PositiveInfinity|  
|"\-INF"|Double.NegativeInfinity|  
  
 次のコードは、`<Infinity>INF</Infinity>` を書き込みます。  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## 参照  
 [XML データ型の変換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)   
 [.NET Framework 型の文字列への変換](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)