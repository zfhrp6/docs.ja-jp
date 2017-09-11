---
title: "方法: 単一の子要素 (LINQ to XML) を取得 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 006a6afbb07ceea64b8fcc6cdab1d4fd31ae3c87
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="6665b-102">方法: 単一の子要素 (LINQ to XML) を取得 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6665b-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="6665b-103">このトピックでは、子要素名を指定して単一の子要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6665b-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="6665b-104">子要素の名前が既知であり、この名前を持つ要素が&1; つしか存在しない場合は、コレクションの代わりに&1; つの要素だけを取得する方が便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="6665b-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="6665b-105"><xref:System.Xml.Linq.XContainer.Element%2A>の最初子<xref:System.Xml.Linq.XElement>に指定された<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XElement>メソッドが返されます。</xref:System.Xml.Linq.XContainer.Element%2A></span><span class="sxs-lookup"><span data-stu-id="6665b-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="6665b-106">Visual Basic で単一の子要素を取得する場合の一般的な方法は、XML プロパティを使用し、配列インデクサー表記を使用して最初の要素を取得する方法です。</span><span class="sxs-lookup"><span data-stu-id="6665b-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6665b-107">例</span><span class="sxs-lookup"><span data-stu-id="6665b-107">Example</span></span>  
 <span data-ttu-id="6665b-108">次の例では、使用、<xref:System.Xml.Linq.XContainer.Element%2A>メソッド</xref:System.Xml.Linq.XContainer.Element%2A>。</span><span class="sxs-lookup"><span data-stu-id="6665b-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="6665b-109">この例では、`po` という名前の XML ツリーを受け取り、`Comment` という名前の最初の要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="6665b-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="6665b-110">Visual Basic の例では、配列インデクサー表記を使用して単一の要素を取得しています。</span><span class="sxs-lookup"><span data-stu-id="6665b-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="6665b-111">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="6665b-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="6665b-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6665b-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="6665b-113">例</span><span class="sxs-lookup"><span data-stu-id="6665b-113">Example</span></span>  
 <span data-ttu-id="6665b-114">上記と同じコードを使用して、名前空間内の XML から要素を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6665b-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="6665b-115">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="6665b-115">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="6665b-116">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 一般的な購買発注書、Namespace で](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="6665b-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6665b-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6665b-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6665b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6665b-118">See Also</span></span>  
 [<span data-ttu-id="6665b-119">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6665b-119">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)

