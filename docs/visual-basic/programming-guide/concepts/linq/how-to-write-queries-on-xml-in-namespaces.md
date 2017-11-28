---
title: "方法: 名前空間 (Visual Basic) 内の XML に対するクエリの作成"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5708a2a162132262722f390842f59c9c6a6838e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="35a16-102">方法: 名前空間 (Visual Basic) 内の XML に対するクエリの作成</span><span class="sxs-lookup"><span data-stu-id="35a16-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="35a16-103">名前空間内の XML に対するクエリを記述するには、正しい名前空間を持つ <xref:System.Xml.Linq.XName> オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35a16-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="35a16-104">Visual Basic での最も一般的な方法は、グローバル名前空間を定義し、その名前空間を使用する XML リテラルおよび XML プロパティを使用することです。</span><span class="sxs-lookup"><span data-stu-id="35a16-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="35a16-105">既定のグローバル名前空間を定義できます。その場合、XML リテラルの要素は既定でこの名前空間に含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="35a16-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="35a16-106">または、プレフィックスを持つグローバル名前空間を定義し、そのプレフィックスを必要に応じて XML リテラルや XML プロパティで使用できます。</span><span class="sxs-lookup"><span data-stu-id="35a16-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="35a16-107">XML のその他の形式と同様に、属性は既定でどの名前空間にも含まれません。</span><span class="sxs-lookup"><span data-stu-id="35a16-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="35a16-108">このトピックの最初に示す一連の例では、既定の名前空間内に XML ツリーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35a16-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="35a16-109">2 つ目の例では、プレフィックスを持つ名前空間で XML ツリーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35a16-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35a16-110">例</span><span class="sxs-lookup"><span data-stu-id="35a16-110">Example</span></span>  
 <span data-ttu-id="35a16-111">次の例では、既定の名前空間に含まれる XML ツリーを作成しています。</span><span class="sxs-lookup"><span data-stu-id="35a16-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="35a16-112">さらに、要素のコレクションを取得しています。</span><span class="sxs-lookup"><span data-stu-id="35a16-112">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
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
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="35a16-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="35a16-113">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="35a16-114">例</span><span class="sxs-lookup"><span data-stu-id="35a16-114">Example</span></span>  
 <span data-ttu-id="35a16-115">一方、Visual Basic では、プレフィックスを持つ名前空間を使用する XML ツリーでクエリを記述する場合と、既定の名前空間内の XML ツリーに対してクエリを実行する場合とで、大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="35a16-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="35a16-116">通常は、`Imports` ステートメントを使用してプレフィックスを持つ名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="35a16-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="35a16-117">この場合、XML ツリーを作成するときに要素および属性の名前でプレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="35a16-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="35a16-118">また、XML プロパティを使用して XML ツリーに対してクエリを実行するときにもプレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="35a16-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="35a16-119">次の例では、プレフィックスを持つ名前空間に含まれる XML ツリーを作成しています。</span><span class="sxs-lookup"><span data-stu-id="35a16-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="35a16-120">さらに、要素のコレクションを取得しています。</span><span class="sxs-lookup"><span data-stu-id="35a16-120">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="35a16-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="35a16-121">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="35a16-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="35a16-122">See Also</span></span>  
 [<span data-ttu-id="35a16-123">XML 名前空間 (Visual Basic) の使用</span><span class="sxs-lookup"><span data-stu-id="35a16-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
