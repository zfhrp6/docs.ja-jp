---
title: "方法: 特定の属性を持つ要素を検索する (XPath-LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a69d3503c7cb64cc825fadece8a4121e633366b7
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a>方法: 特定の属性を持つ要素を検索する (XPath-LINQ to XML) (C#)
特定の属性を持つすべての要素を検索しなければならない場合があります。 属性の内容は問わず、 属性の存在に基づいて選択を行うような場合です。  
  
 XPath 式を次に示します。  
  
 `./*[@Select]`  
  
## <a name="example"></a>例  
 次のコードは、`Select` 属性を持つ要素のみを選択します。  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a>関連項目  
 [XPath ユーザー向けの LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
