---
title: "方法: 空のクエリの結果セットを (Visual Basic) デバッグ |Microsoft ドキュメント"
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
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 85a0d070c415924ef116367b0202c01bef6d8ace
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="346e6-102">方法: 空のクエリの結果セット (Visual Basic) のデバッグ</span><span class="sxs-lookup"><span data-stu-id="346e6-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>
<span data-ttu-id="346e6-103">XML ツリーのクエリにおける最も一般的な問題の&1; つは、XML ツリーに既定の名前空間がある場合に、XML が名前空間に含まれていないものとして開発者がクエリを記述してしまうことです。</span><span class="sxs-lookup"><span data-stu-id="346e6-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="346e6-104">このトピックの最初に示す一連の例では、既定の名前空間内の XML が読み込まれ、クエリが不適切に実行される典型的な例を示しています。</span><span class="sxs-lookup"><span data-stu-id="346e6-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="346e6-105">2 番目に示す一連の例では、名前空間内の XML に対してクエリを実行できるようにするために必要な修正を示しています。</span><span class="sxs-lookup"><span data-stu-id="346e6-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="346e6-106">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="346e6-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="346e6-107">例</span><span class="sxs-lookup"><span data-stu-id="346e6-107">Example</span></span>  
 <span data-ttu-id="346e6-108">この例では、名前空間内にある XML の作成、および空の結果セットを返すクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="346e6-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns='http://www.adventure-works.com'>  
        <Child>1</Child>  
        <Child>2</Child>  
        <Child>3</Child>  
        <AnotherChild>4</AnotherChild>  
        <AnotherChild>5</AnotherChild>  
        <AnotherChild>6</AnotherChild>  
    </Root>  
Dim c1 As IEnumerable(Of XElement) = _  
        From el In root.<Child> _  
        Select el  
Console.WriteLine("Result set follows:")  
For Each el As XElement In c1  
    Console.WriteLine(el.Value)  
Next  
Console.WriteLine("End of result set")  
```  
  
 <span data-ttu-id="346e6-109">この例を実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="346e6-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="346e6-110">例</span><span class="sxs-lookup"><span data-stu-id="346e6-110">Example</span></span>  
 <span data-ttu-id="346e6-111">この例では、名前空間内にある XML の作成と、適切に記述されたクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="346e6-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="346e6-112">ソリューションを宣言し、グローバルな既定の名前空間を初期化します。</span><span class="sxs-lookup"><span data-stu-id="346e6-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="346e6-113">これにより、すべての XML プロパティが既定の名前空間に配置されます。</span><span class="sxs-lookup"><span data-stu-id="346e6-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="346e6-114">この例を正しく動作させるために必要な変更はこれだけです。</span><span class="sxs-lookup"><span data-stu-id="346e6-114">No other modifications are required to the example to make it work properly.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="346e6-115">この例を実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="346e6-115">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="346e6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="346e6-116">See Also</span></span>  
 [<span data-ttu-id="346e6-117">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="346e6-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
