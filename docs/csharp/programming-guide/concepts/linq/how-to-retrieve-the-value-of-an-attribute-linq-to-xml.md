---
title: "方法: 属性の値を取得する (LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 687a9d6da80259d41f6ed541cee4c579cdff23d8
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>方法: 属性の値を取得する (LINQ to XML) (C#)
このトピックでは、属性の値を取得する方法について説明します。 主に 2 つの方法があります。1 つは、<xref:System.Xml.Linq.XAttribute> を目的の型にキャストする方法です。その後、明示的な変換演算子によって、要素または属性のコンテンツが指定した型に変換されます。 もう 1 つは、<xref:System.Xml.Linq.XAttribute.Value%2A> プロパティを使用する方法です。 ただし、通常はキャストがより適切な方法です。 属性を NULL 値が許容される型にキャストすると、存在が不明確な属性の値を取得する場合にコードをより簡単に記述できます。 この手法の例については、「[方法: 要素の値を取得する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)」を参照してください。  
  
## <a name="example"></a>例  
 属性の値を取得するには、<xref:System.Xml.Linq.XAttribute> オブジェクトを目的の型にキャストします。  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>例  
 属性が名前空間内にある場合にその属性の値を取得する方法を次の例に示します。 詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
abcde  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
