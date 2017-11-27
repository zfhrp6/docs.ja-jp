---
title: "方法: Descendants メソッド (Visual Basic) を使用して単一の子孫を検索"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0647dee5ced1e986fcb3fac7915437dfb37b0796
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a><span data-ttu-id="9e052-102">方法: Descendants メソッド (Visual Basic) を使用して単一の子孫を検索</span><span class="sxs-lookup"><span data-stu-id="9e052-102">How to: Find a Single Descendant Using the Descendants Method (Visual Basic)</span></span>
<span data-ttu-id="9e052-103"><xref:System.Xml.Linq.XContainer.Descendants%2A> 軸メソッドを使用すると、一意の名前を持つ単一の要素を検索するコードを簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="9e052-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="9e052-104">この手法は、特定の名前を持つ特定の子孫を検索する必要がある場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9e052-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="9e052-105">目的の要素に移動するコードを記述することもできますが、多くの場合、<xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用してコードを記述する方がより迅速で簡単です。</span><span class="sxs-lookup"><span data-stu-id="9e052-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e052-106">例</span><span class="sxs-lookup"><span data-stu-id="9e052-106">Example</span></span>  
 <span data-ttu-id="9e052-107">この例では、<xref:System.Linq.Enumerable.First%2A> 標準クエリ演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e052-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 <span data-ttu-id="9e052-108">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9e052-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="9e052-109">例</span><span class="sxs-lookup"><span data-stu-id="9e052-109">Example</span></span>  
 <span data-ttu-id="9e052-110">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="9e052-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9e052-111">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の操作](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e052-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="9e052-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9e052-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e052-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e052-113">See Also</span></span>  
 [<span data-ttu-id="9e052-114">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e052-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
