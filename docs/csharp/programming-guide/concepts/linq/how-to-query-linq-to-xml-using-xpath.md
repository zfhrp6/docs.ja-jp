---
title: "方法: XPath を使用して LINQ to XML にクエリを実行する (C#)"
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
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86d02a119423fe33731f0049ca232dde7509936d
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>方法: XPath を使用して LINQ to XML にクエリを実行する (C#)
このトピックでは、XPath を使用して XML ツリーに対してクエリを実行できる拡張メソッドについて説明します。 これらの拡張メソッドについて詳しくは、<xref:System.Xml.XPath.Extensions?displayProperty=fullName> を参照してください。  
  
 古いコードの広範な利用など、XPath を使用してクエリを実行する特別な理由がない限りは、XPath を LINQ to XML と共に使用することはお勧めできません。 XPath クエリは、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリよりもパフォーマンスが低くなります。  
  
## <a name="example"></a>例  
 次の例では、小さな XML ツリーを作成し、<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> を使用して、一連の要素を選択しています。  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>関連項目  
 [高度なクエリ手法 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
