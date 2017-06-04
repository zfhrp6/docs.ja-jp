---
title: "XML データ型の変換 | Microsoft Docs"
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
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# XML データ型の変換
**XmlConvert** クラスのメソッドのほとんどは、文字列と厳密に型指定された形式との間のデータ変換に使われます。  これらのメソッドはロケールに依存しません。  つまり、変換の実行時にはロケールの設定は考慮されません。  
  
## 文字列を型として読み込む  
 文字列を読み込んで **DateTime** 型に変換するサンプルを次に示します。  
  
 入力として次の XML を使用します。  
  
 **入力**  
  
```  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 次のコードは、文字列を **DateTime** 形式に変換します。  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## 文字列を型として書き込む  
 **Int32** を読み込んで文字列に変換するサンプルを次に示します。  
  
 入力として次の XML を使用します。  
  
 **入力**  
  
```  
<TestInt32>-2147483648</TestInt32>  
```  
  
 次のコードは、**Int32** を **String** に変換します。  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## 参照  
 [文字列の .NET Framework データ型への変換](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)   
 [.NET Framework 型の文字列への変換](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)