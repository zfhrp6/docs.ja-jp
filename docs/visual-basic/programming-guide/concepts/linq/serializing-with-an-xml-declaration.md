---
title: "XML 宣言 (Visual Basic) でシリアル化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 373df9b28ae7434d33ae81eba701d289cf1aa4f7
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>XML 宣言 (Visual Basic) でシリアル化します。
このトピックでは、シリアル化を実行する際に XML 宣言を生成するかどうかを制御する方法について説明します。  
  
## <a name="xml-declaration-generation"></a>XML 宣言の生成  
 シリアル化、<xref:System.IO.File>または<xref:System.IO.TextWriter>を使用して、<xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>メソッドまたは<xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>メソッドは、XML 宣言を生成します</xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.IO.TextWriter></xref:System.IO.File>。 シリアル化すると、 <xref:System.Xml.XmlWriter>、ライターの設定 (で指定されている、<xref:System.Xml.XmlWriterSettings>オブジェクト)、XML 宣言を生成するかどうかどうかを決定します</xref:System.Xml.XmlWriterSettings></xref:System.Xml.XmlWriter>。  
  
 `ToString` メソッドを使用して文字列にシリアル化する場合、生成される XML には XML 宣言は含まれません。  
  
### <a name="serializing-with-an-xml-declaration"></a>XML 宣言付きのシリアル化  
 次の例を作成し、 <xref:System.Xml.Linq.XElement>、ファイルにドキュメントを保存し、ファイルをコンソールに出力します</xref:System.Xml.Linq.XElement>。  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>XML 宣言なしでのシリアル化  
 次の例<xref:System.Xml.Linq.XElement><xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter></xref:System.Xml.Linq.XElement>を保存する方法を示しています。  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ツリーをシリアル化する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
