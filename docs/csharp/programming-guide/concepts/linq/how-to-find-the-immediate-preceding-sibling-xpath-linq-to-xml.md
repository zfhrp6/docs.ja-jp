---
title: '方法: 直前の兄弟を検索する (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 82c0ee6e7340ada18fb2077c0b8b04fb6a41671a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318556"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="d823b-102">方法: 直前の兄弟を検索する (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d823b-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d823b-103">ノードの直前の兄弟を検索することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d823b-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="d823b-104">
          [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] とは対照的に、XPath では先行する兄弟軸の位置述語にはセマンティクス上の違いがあります。この  と XPath の相違点は、注目すべき特徴といえます。</span><span class="sxs-lookup"><span data-stu-id="d823b-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d823b-105">例</span><span class="sxs-lookup"><span data-stu-id="d823b-105">Example</span></span>  
 <span data-ttu-id="d823b-106">この例では、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリは、<xref:System.Linq.Enumerable.Last%2A> 演算子を使用して、<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> から返されるコレクション内の最後のノードを検索します。</span><span class="sxs-lookup"><span data-stu-id="d823b-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="d823b-107">一方、XPath 式は、値が 1 の述語を使用して直前の要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="d823b-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="d823b-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d823b-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="d823b-109">参照</span><span class="sxs-lookup"><span data-stu-id="d823b-109">See Also</span></span>  
 [<span data-ttu-id="d823b-110">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d823b-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
