---
title: "最小単位に分割 XName および XNamespace オブジェクト (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b08f3116f5acb404cf2c33072ec31fbaada4e7cb
ms.lasthandoff: 03/13/2017


---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>最小単位に分割 XName および XNamespace オブジェクト (LINQ to XML) (Visual Basic)
<xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>オブジェクトは、*最小単位に分割*; は、同じ修飾名を含んでいる場合、オブジェクトを参照して、同じです</xref:System.Xml.Linq.XNamespace>。</xref:System.Xml.Linq.XName> これによってクエリのパフォーマンスが向上します。これは、2 つのアトミック化された名前の等価性を比べる場合に、基になる中間言語が、2 つの参照が同じオブジェクトを指しているかどうかを判別するだけで済むためです。 基になるコードは、時間のかかる文字列比較を行う必要がありません。  
  
## <a name="atomization-semantics"></a>アトミック化のセマンティクス  
 アトミック化という&2; つ<xref:System.Xml.Linq.XName>オブジェクトが同じローカル名を所有していて、同じ名前空間内にある、同じインスタンスを共有する</xref:System.Xml.Linq.XName>。 2 つの場合は、同じ方法で<xref:System.Xml.Linq.XNamespace>オブジェクトが同じ名前空間 URI を持つ、同じインスタンスを共有します</xref:System.Xml.Linq.XNamespace>。  
  
 アトミック化されたオブジェクトをクラスに対して有効にするには、クラスのコンストラクターがパブリックではなく、プライベートであることが必要です。 その理由は、コンストラクターがパブリックであれば、アトミック化されていないオブジェクトを作成できるからです。 <xref:System.Xml.Linq.XName>および<xref:System.Xml.Linq.XNamespace>クラスの実装に<xref:System.Xml.Linq.XName>または<xref:System.Xml.Linq.XNamespace>.</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName>文字列に変換する暗黙的な変換演算子</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName> この方法でこれらのオブジェクトのインスタンスを取得します。 コンストラクターにはアクセスできないため、コンストラクターを使用してインスタンスを取得することはできません。  
  
 <xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>実装等値演算子および非等値演算子の&2; つのオブジェクト比較対象となるが、同じインスタンスを参照するかどうかを判断することもできます</xref:System.Xml.Linq.XNamespace>。</xref:System.Xml.Linq.XName>  
  
## <a name="example"></a>例  
 次のコードを作成<xref:System.Xml.Linq.XElement>オブジェクトし、同じ名前が同じインスタンスを共有することを示しています</xref:System.Xml.Linq.XElement>。  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 前述のように、アトミック化されたオブジェクトの利点は、されるときに、軸メソッドのいずれかを使用する、<xref:System.Xml.Linq.XName>をパラメーターとして、軸メソッドのみが決定する&2; つの名前の参照を同じインスタンスを目的の要素を選択します</xref:System.Xml.Linq.XName>。  
  
 次の例では、<xref:System.Xml.Linq.XName>に、<xref:System.Xml.Linq.XContainer.Descendants%2A>ので、アトミック化パターンによってパフォーマンスの向上がメソッド呼び出し</xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XName>。  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
