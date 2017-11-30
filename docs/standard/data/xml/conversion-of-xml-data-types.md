---
title: "XML データ型の変換"
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
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a>XML データ型の変換
メソッドの大部分がで見つかった、 **XmlConvert**文字列と厳密に型指定された形式間でデータを変換するクラスを使用します。 これらのメソッドはロケールに依存しません。 つまり、変換の実行時にはロケールの設定は考慮されません。  
  
## <a name="reading-string-as-types"></a>文字列を型として読み込む  
 次の例は、文字列を読み取り、に変換する、 **DateTime**型です。  
  
 入力として次の XML を使用します。  
  
 **入力**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 このコードを変換する文字列、 **DateTime**形式。  
  
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
  
## <a name="writing-strings-as-types"></a>文字列を型として書き込む  
 次のサンプルの読み取り、 **Int32**文字列に変換します。  
  
 入力として次の XML を使用します。  
  
 **入力**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 このコードは、変換、 **Int32**に、**文字列**:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework データ型を文字列に変換します。](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [.NET Framework の型を文字列に変換します。](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
