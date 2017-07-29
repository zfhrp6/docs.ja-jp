---
title: "XML 宣言付きのシリアル化 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 36ffb8ddd584785c660896ca77707d504638852f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="serializing-with-an-xml-declaration-c"></a>XML 宣言付きのシリアル化 (C#)
このトピックでは、シリアル化を実行する際に XML 宣言を生成するかどうかを制御する方法について説明します。  
  
## <a name="xml-declaration-generation"></a>XML 宣言の生成  
 <xref:System.IO.File> メソッドまたは <xref:System.IO.TextWriter> メソッドを使用して <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> または <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> にシリアル化すると、XML 宣言が生成されます。 <xref:System.Xml.XmlWriter> にシリアル化する場合は、<xref:System.Xml.XmlWriterSettings> オブジェクトで指定したライター設定により、XML 宣言が生成されるかどうかが決定されます。  
  
 `ToString` メソッドを使用して文字列にシリアル化する場合、生成される XML には XML 宣言は含まれません。  
  
### <a name="serializing-with-an-xml-declaration"></a>XML 宣言付きのシリアル化  
 次の例では、<xref:System.Xml.Linq.XElement> を作成し、ドキュメントをファイルに保存して、そのファイルをコンソールに出力します。  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>XML 宣言なしでのシリアル化  
 <xref:System.Xml.Linq.XElement> を <xref:System.Xml.XmlWriter> に保存する方法を次の例に示します。  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ツリーのシリアル化 (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

