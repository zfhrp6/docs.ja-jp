---
title: "XML ツリー (Visual Basic の場合) からの要素、属性、およびノードの削除 |Microsoft ドキュメント"
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
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eef13476733f7c883080923614683a41d7cb3b3a
ms.lasthandoff: 03/13/2017


---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>XML ツリー (Visual Basic の場合) からの要素、属性、およびノードの削除
要素、属性、およびその他の種類のノードを削除して、XML ツリーを変更できます。  
  
 1 つの要素または&1; つの属性は XML ドキュメントから簡単に削除できます。 一方、要素または属性のコレクションを削除する場合は、まずコレクションをリストに具体化し、そのリストから要素または属性を削除する必要があります。 最良のアプローチが使用するには、<xref:System.Xml.Linq.Extensions.Remove%2A>拡張メソッドは、これはするが実行されます</xref:System.Xml.Linq.Extensions.Remove%2A>。  
  
 このような方法でコレクションの削除を実行する主な理由は、XML ツリーから取得するコレクションのほとんどが遅延実行を使用して生成されるからです。 最初にコレクションをリストに具体化せず、拡張メソッドも使用しない場合、特定の種類のバグが発生する可能性があります。 詳細については、次を参照してください。[混在宣言型コードと命令型コードのバグ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)します。  
  
 ノードおよび属性を XML ツリーから削除するメソッドを次に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)|削除、<xref:System.Xml.Linq.XAttribute>を親から</xref:System.Xml.Linq.XAttribute>。|  
|[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)|<xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer>から子ノードを削除します。|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName>|<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>からコンテンツおよび属性を削除します。|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName>|<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>の属性を削除します。|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName>|`null` を値に受け取ると、属性を削除します。|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName>|`null` を値に受け取ると、子要素を削除します。|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName>|削除、<xref:System.Xml.Linq.XNode>を親から</xref:System.Xml.Linq.XNode>。|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName>|ソース コレクション内のすべての属性または要素をその親要素から削除します。|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 この例では、要素を削除する&3; つの方法を示します。 まず、1 つの要素を削除します。 次に、要素のコレクションの取得を具体化して、使用して、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>演算子、およびコレクションを削除します</xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>。 最後に、要素のコレクションを取得し、削除を使用して、<xref:System.Xml.Linq.Extensions.Remove%2A>拡張メソッド</xref:System.Xml.Linq.Extensions.Remove%2A>。  
  
 詳細については、<xref:System.Linq.Enumerable.ToList%2A>演算子を参照してください[データ型を変換する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)</xref:System.Linq.Enumerable.ToList%2A> 。  
  
### <a name="code"></a>コード  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
  
```  
  
### <a name="comments"></a>コメント  
 このコードを実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 最初の孫要素が `Child1` から削除されていることがわかります。 すべての孫要素が、`Child2` と `Child3` から削除されています。  
  
## <a name="see-also"></a>関連項目  
 [XML ツリー (LINQ to XML) の変更 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
