---
title: "XML ツリーへの要素、属性、およびノードの追加 (C#) | Microsoft Docs"
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
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 858d5b2c5ed680a0e52e374b8ec98762d7fde043
ms.lasthandoff: 03/13/2017


---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>XML ツリーへの要素、属性、およびノードの追加
コンテンツ (要素、属性、コメント、処理命令、テキスト、および CDATA) を既存の XML ツリーに追加できます。  
  
## <a name="methods-for-adding-content"></a>コンテンツを追加するためのメソッド  
 次のメソッドは <xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> に子コンテンツを追加します。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<xref:System.Xml.Linq.XContainer> の子コンテンツの末尾にコンテンツを追加します。|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<xref:System.Xml.Linq.XContainer> の子コンテンツの冒頭にコンテンツを追加します。|  
  
 次のメソッドは、<xref:System.Xml.Linq.XNode> の兄弟ノードとしてコンテンツを追加します。 兄弟コンテンツを追加する最も一般的なノードは <xref:System.Xml.Linq.XElement> です。ただし、<xref:System.Xml.Linq.XText> や <xref:System.Xml.Linq.XComment> など、他の種類のノードに有効な兄弟コンテンツを追加することもできます。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<xref:System.Xml.Linq.XNode> の後にコンテンツを追加します。|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<xref:System.Xml.Linq.XNode> の前にコンテンツを追加します。|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、2 つの XML ツリーを作成し、その 1 つを変更します。  
  
### <a name="code"></a>コード  
  
```csharp  
XElement srcTree = new XElement("Root",   
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a>コメント  
 このコードを実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ツリーの変更 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
