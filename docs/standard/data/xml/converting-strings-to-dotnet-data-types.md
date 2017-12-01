---
title: "文字列の .NET Framework データ型への変換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce594234e601cd8feb4723bbc383db9e3ed40522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="converting-strings-to-net-framework-data-types"></a>文字列の .NET Framework データ型への変換
文字列を .NET Framework データ型に変換する場合は、使用、 **XmlConvert**アプリケーション要件に適合するメソッド。 使用できるすべての変換方法の一覧については、 **XmlConvert**クラスを参照してください<xref:System.Xml.XmlConvert>です。  
  
 返される文字列、 **ToString**メソッドは渡されたデータの文字列バージョンです。 さらに、変換を使用していくつかの .NET Framework の型は、 **XmlConvert**クラス内のメソッドを使用していない、 **System.Convert**クラスです。 **XmlConvert**クラスは、XML スキーマ (XSD) データ型仕様に準拠しており、データ型を**XmlConvert**にマップできます。  
  
 次の表は、.NET Framework データ型の一覧と、XML スキーマ (XSD) のデータ型マップを使用した場合に返される文字列を示しています。 これらの .NET Framework 型を使用して処理することはできません**System.Convert**です。  
  
|.NET Framework 型|返される文字列|  
|-------------------------|---------------------|  
|Boolean|"true"、"false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|形式は、yyyy-MM-ddTHH:mm:sszzzzzz およびそのサブセットです。|  
|Timespan|PnYnMnTnHnMnS の形式。つまり、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。|  
  
> [!NOTE]
>  文字列を使用して、表に示すいずれかの .NET Framework 型に変換する場合、 **ToString**メソッドで返される文字列は、基本型ですが、XML スキーマ (XSD) 文字列型ではありません。  
  
 **DateTime**と**Timespan**こととは異なる値型、 **DateTime**一方で、瞬間を表します、 **TimeSpan**時間間隔を表します。 **DateTime**と**Timespan**形式は、XML スキーマ (XSD) データ型仕様で指定されます。 例:  
  
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
  
 `<Date>2001-08-04T00:00:00</Date>`。  
  
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
  
 ただし、変更する場合は、文字列を**ブール**、**単一**、または**二重**、返される .NET Framework の型を使用する場合に返される型と同じではありません、**System.Convert**クラスです。  
  
## <a name="string-to-boolean"></a>String から Boolean  
 次の表は、どのような生成される型、入力文字列を文字列に変換するときに**ブール**を使用して、 **ToBoolean**メソッドです。  
  
|有効な文字列入力パラメーター|出力される .NET Framework 型|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 たとえば、次のような XML があるとします。  
  
 **入力**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 次のコードによって認識できる両方と**bvalue**は**System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>String から Single  
 次の表は、どのような生成される型、入力文字列を文字列に変換するときに、**単一**を使用して、 **ToSingle**メソッドです。  
  
|有効な文字列入力パラメーター|出力される .NET Framework 型|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>String から Double  
 次の表は、どのような生成される型、入力文字列を文字列に変換するときに、**単一**を使用して、 **ToDouble**メソッドです。  
  
|有効な文字列入力パラメーター|出力される .NET Framework 型|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 次のコードは、`<Infinity>INF</Infinity>` を書き込みます。  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>関連項目  
 [XML データ型の変換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [.NET Framework の型を文字列に変換します。](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
