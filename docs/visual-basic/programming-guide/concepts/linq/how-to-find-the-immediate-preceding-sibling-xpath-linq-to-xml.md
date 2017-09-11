---
title: "方法: 前の兄弟を検索 (XPATH-LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 3e5c0100ea2a5d4ad3e5f503f2680f946e08e6fd
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="308a8-102">方法: 前の兄弟を検索 (XPATH-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="308a8-102">How to: Find the Immediate Preceding Sibling (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="308a8-103">ノードの直前の兄弟を検索することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="308a8-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="308a8-104">
          [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] とは対照的に、XPath では先行する兄弟軸の位置述語にはセマンティクス上の違いがあります。この  と XPath の相違点は、注目すべき特徴といえます。</span><span class="sxs-lookup"><span data-stu-id="308a8-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="308a8-105">例</span><span class="sxs-lookup"><span data-stu-id="308a8-105">Example</span></span>  
 <span data-ttu-id="308a8-106">この例では、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クエリ<xref:System.Linq.Enumerable.Last%2A><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>によって返されるコレクションの最後のノードを検索する演算子</xref:System.Linq.Enumerable.Last%2A>を使用して</span><span class="sxs-lookup"><span data-stu-id="308a8-106">In this example, the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="308a8-107">一方、XPath 式は、値が 1 の述語を使用して直前の要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="308a8-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="308a8-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="308a8-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a><span data-ttu-id="308a8-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="308a8-109">See Also</span></span>  
 [<span data-ttu-id="308a8-110">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="308a8-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

