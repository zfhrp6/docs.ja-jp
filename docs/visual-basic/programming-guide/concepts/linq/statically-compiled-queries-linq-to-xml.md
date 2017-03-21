---
title: "静的にコンパイル済みクエリ (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ea8e71acf861b93a21296c74254b3ca4d977d0a
ms.lasthandoff: 03/13/2017


---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>静的にコンパイル済みクエリ (LINQ to XML) (Visual Basic)
代わりに LINQ を XML で最も重要なパフォーマンスのいずれかの利点<xref:System.Xml.XmlDocument>を LINQ to XML クエリでは静的にコンパイル、実行時に XPath クエリを解釈する必要があります</xref:System.Xml.XmlDocument>。 この機能は LINQ to XML に組み込まれているので、追加の手順を実行することなく利用できますが、その違いを理解しておくと、この&2; つの技術のどちらかを選ぶときに役立ちます。 このトピックでは、相違点について説明します。  
  
## <a name="statically-compiled-queries-vs-xpath"></a>静的にコンパイルされたクエリと XPath  
 次の例は、指定した名前と指定した値の属性がある子孫要素を取得する方法を示しています。  
  
 次に示すのは、これに相当する XPath 式です。  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
  
```  
  
 この例のクエリ式は、コンパイラによってメソッドベースのクエリ構文に書き換えられています。 メソッドベースのクエリ構文で書かれた次の例では、前の例と同じ結果が生成されます。  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <xref:System.Linq.Enumerable.Where%2A>メソッドは、拡張メソッド</xref:System.Linq.Enumerable.Where%2A>。 詳細については、次を参照してください。[拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)します。 <xref:System.Linq.Enumerable.Where%2A>拡張メソッドは、次のように記述されているかのように、上記のクエリがコンパイルされた:</xref:System.Linq.Enumerable.Where%2A>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 この例では、前の&2; つの例と同じ結果が生成されます。 これは、静的にリンクされたメソッド呼び出しにクエリが効果的にコンパイルされたことを示します。 これと反復子の遅延実行セマンティクスが組み合わさることで、パフォーマンスが向上します。 反復子の遅延実行セマンティクスの詳細については、次を参照してください。[遅延実行とレイジー評価 linq to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)します。  
  
> [!NOTE]
>  これらは、コンパイラが書き込むコードの例です。 実際の実装はこれらの例と若干異なる可能性がありますが、パフォーマンスは同じか類似したものになります。  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>XmlDocument を使用した XPath 式の実行  
 次の例では使用<xref:System.Xml.XmlDocument>前の例と同じ結果を得るため:</xref:System.Xml.XmlDocument>  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
  
```  
  
 このクエリには、LINQ to XML を使用する例と同じ出力が返されます。唯一の違いがありますが LINQ to XML が印刷された XML をインデント<xref:System.Xml.XmlDocument>しません</xref:System.Xml.XmlDocument>。  
  
 ただし、<xref:System.Xml.XmlDocument>アプローチ一般的にパフォーマンスが低く、LINQ to XML のため、<xref:System.Xml.XmlNode.SelectNodes%2A>メソッド必要があります、次の操作に、内部的に呼び出されるたびに:</xref:System.Xml.XmlNode.SelectNodes%2A> </xref:System.Xml.XmlDocument>  
  
-   XPath 式を含んでいる文字列を解析してトークンに分解します。  
  
-   トークンを検証して、XPath 式が有効であることを確認します。  
  
-   式を内部式ツリーに変換します。  
  
-   ノードを反復処理し、式の評価に基づいて結果セットのノードを適切に選択します。  
  
 この場合、対応する LINQ to XML のクエリよりも処理量がかなり多くなります。 特定のパフォーマンスの違いは、さまざまな種類のクエリはによって異なりますが一般に LINQ to XML クエリは処理量が少ないためよりも優れて<xref:System.Xml.XmlDocument>。</xref:System.Xml.XmlDocument>を使用して XPath 式を評価します。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
