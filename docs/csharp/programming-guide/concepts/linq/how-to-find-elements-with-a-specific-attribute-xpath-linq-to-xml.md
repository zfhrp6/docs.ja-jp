---
title: "方法: 特定の属性を持つ要素を検索する (XPath-LINQ to XML) (C#)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fec0b9a4dc5cee0f10f1675f1b8b281c40be7f21
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="0c8ef-102">方法: 特定の属性を持つ要素を検索する (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0c8ef-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="0c8ef-103">特定の属性を持つすべての要素を検索しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0c8ef-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="0c8ef-104">属性の内容は問わず、</span><span class="sxs-lookup"><span data-stu-id="0c8ef-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="0c8ef-105">属性の存在に基づいて選択を行うような場合です。</span><span class="sxs-lookup"><span data-stu-id="0c8ef-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="0c8ef-106">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0c8ef-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="0c8ef-107">例</span><span class="sxs-lookup"><span data-stu-id="0c8ef-107">Example</span></span>  
 <span data-ttu-id="0c8ef-108">次のコードは、`Select` 属性を持つ要素のみを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c8ef-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
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
  
 <span data-ttu-id="0c8ef-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0c8ef-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c8ef-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c8ef-110">See Also</span></span>  
 [<span data-ttu-id="0c8ef-111">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0c8ef-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

