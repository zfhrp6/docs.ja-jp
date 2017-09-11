---
title: "方法: 要素名 (LINQ to XML) をフィルター処理 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 07f7867b0fc5cf79ba5ce06f95b07b5c538e83d3
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a><span data-ttu-id="f57bb-102">方法: 要素名 (LINQ to XML) をフィルター処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f57bb-102">How to: Filter on Element Names (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="f57bb-103">返すメソッドのいずれかを呼び出すと<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>、要素名をフィルター処理できます</xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="f57bb-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f57bb-104">例</span><span class="sxs-lookup"><span data-stu-id="f57bb-104">Example</span></span>  
 <span data-ttu-id="f57bb-105">この例では、指定した名前を持つ子孫だけが含まれるようにフィルター処理された子孫のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="f57bb-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="f57bb-106">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="f57bb-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
<span data-ttu-id="f57bb-107"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="f57bb-107"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="f57bb-108">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f57bb-108">This code produces the following output:</span></span>  
  
<span data-ttu-id="f57bb-109"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="f57bb-109"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="f57bb-110">返すメソッド<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>コレクションが同じパターンに従います</xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="f57bb-110">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="f57bb-111">そのシグネチャ<xref:System.Xml.Linq.XContainer.Elements%2A>と<xref:System.Xml.Linq.XContainer.Descendants%2A>。</xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XContainer.Elements%2A>に似ています</span><span class="sxs-lookup"><span data-stu-id="f57bb-111">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="f57bb-112">類似するシグネチャを持つメソッドの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f57bb-112">The following is the complete list of methods that have similar method signatures:</span></span>  
  
-   <span data-ttu-id="f57bb-113"><xref:System.Xml.Linq.XNode.Ancestors%2A></xref:System.Xml.Linq.XNode.Ancestors%2A></span><span class="sxs-lookup"><span data-stu-id="f57bb-113"><xref:System.Xml.Linq.XNode.Ancestors%2A></span></span>  
  
-   <span data-ttu-id="f57bb-114"><xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="f57bb-114"><xref:System.Xml.Linq.XContainer.Descendants%2A></span></span>  
  
-   <span data-ttu-id="f57bb-115"><xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="f57bb-115"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>  
  
-   <span data-ttu-id="f57bb-116"><xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="f57bb-116"><xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></span></span>  
  
-   <span data-ttu-id="f57bb-117"><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="f57bb-117"><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></span></span>  
  
-   <span data-ttu-id="f57bb-118"><xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></span><span class="sxs-lookup"><span data-stu-id="f57bb-118"><xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></span></span>  
  
-   <span data-ttu-id="f57bb-119"><xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></span><span class="sxs-lookup"><span data-stu-id="f57bb-119"><xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></span></span>  
  
## <a name="example"></a><span data-ttu-id="f57bb-120">例</span><span class="sxs-lookup"><span data-stu-id="f57bb-120">Example</span></span>  
 <span data-ttu-id="f57bb-121">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="f57bb-121">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="f57bb-122">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="f57bb-122">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="f57bb-123">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 一般的な購買発注書、Namespace で](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="f57bb-123">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f57bb-124">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f57bb-124">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="f57bb-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="f57bb-125">See Also</span></span>  
 [<span data-ttu-id="f57bb-126">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f57bb-126">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
