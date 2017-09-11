---
title: "Visual Basic での既定の名前空間のスコープ |Microsoft ドキュメント"
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
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 138115cb1a5ec2e2c513419a32a9ebaec9c90d61
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="397d3-102">Visual Basic での既定の名前空間のスコープ</span><span class="sxs-lookup"><span data-stu-id="397d3-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="397d3-103">XML ツリーで表される既定の名前空間は、クエリのスコープ内にありません。</span><span class="sxs-lookup"><span data-stu-id="397d3-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="397d3-104">かどうかは、既定の名前空間に含まれる XML がある、まだ宣言する必要あります、<xref:System.Xml.Linq.XNamespace>変数と組み合わせて作成クエリで使用される修飾名のローカル名</xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="397d3-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="397d3-105">XML ツリーのクエリにおける最も一般的な問題の&1; つは、XML ツリーに既定の名前空間がある場合に、XML が名前空間に含まれていないものとして開発者がクエリを記述してしまうことです。</span><span class="sxs-lookup"><span data-stu-id="397d3-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="397d3-106">このトピックの最初に示す一連の例では、既定の名前空間内の XML が読み込まれても、クエリが不適切に実行される典型的な例を示しています。</span><span class="sxs-lookup"><span data-stu-id="397d3-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="397d3-107">2 番目に示す一連の例では、名前空間内の XML に対してクエリを実行できるようにするために必要な修正を示しています。</span><span class="sxs-lookup"><span data-stu-id="397d3-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="397d3-108">例</span><span class="sxs-lookup"><span data-stu-id="397d3-108">Example</span></span>  
 <span data-ttu-id="397d3-109">この例では、名前空間内にある XML の作成、および空の結果セットを返すクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="397d3-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="397d3-110">コード</span><span class="sxs-lookup"><span data-stu-id="397d3-110">Code</span></span>  
  
```vb  
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
  
### <a name="comments"></a><span data-ttu-id="397d3-111">コメント</span><span class="sxs-lookup"><span data-stu-id="397d3-111">Comments</span></span>  
 <span data-ttu-id="397d3-112">この例を実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="397d3-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="397d3-113">例</span><span class="sxs-lookup"><span data-stu-id="397d3-113">Example</span></span>  
 <span data-ttu-id="397d3-114">この例では、名前空間内にある XML の作成と、適切に記述されたクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="397d3-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="397d3-115">上記の不適切に記述された例に対しては、Visual Basic を使用する場合は、正しいアプローチを宣言して既定のグローバル名前空間の初期化です。</span><span class="sxs-lookup"><span data-stu-id="397d3-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="397d3-116">これにより、すべての XML プロパティが既定の名前空間に配置されます。</span><span class="sxs-lookup"><span data-stu-id="397d3-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="397d3-117">この例を正しく動作させるために必要な変更はこれだけです。</span><span class="sxs-lookup"><span data-stu-id="397d3-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="397d3-118">コード</span><span class="sxs-lookup"><span data-stu-id="397d3-118">Code</span></span>  
  
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
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="397d3-119">コメント</span><span class="sxs-lookup"><span data-stu-id="397d3-119">Comments</span></span>  
 <span data-ttu-id="397d3-120">この例を実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="397d3-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="397d3-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="397d3-121">See Also</span></span>  
 [<span data-ttu-id="397d3-122">XML 名前空間 (Visual Basic) の使用</span><span class="sxs-lookup"><span data-stu-id="397d3-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
