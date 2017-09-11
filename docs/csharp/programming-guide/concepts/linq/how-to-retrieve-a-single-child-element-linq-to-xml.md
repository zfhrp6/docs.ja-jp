---
title: "方法: 単一の子要素を取得する (LINQ to XML) (C#)"
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
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 11a53104f73325a905ef5144aabddf8c270fd024
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="f056d-102">方法: 単一の子要素を取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f056d-102">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f056d-103">このトピックでは、子要素名を指定して単一の子要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f056d-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="f056d-104">子要素の名前が既知であり、この名前を持つ要素が 1 つしか存在しない場合は、コレクションの代わりに 1 つの要素だけを取得する方が便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="f056d-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="f056d-105"><xref:System.Xml.Linq.XContainer.Element%2A> メソッドは、指定された <xref:System.Xml.Linq.XElement> を持つ最初の子 <xref:System.Xml.Linq.XName> を返します。</span><span class="sxs-lookup"><span data-stu-id="f056d-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="f056d-106">Visual Basic で単一の子要素を取得する場合の一般的な方法は、XML プロパティを使用し、配列インデクサー表記を使用して最初の要素を取得する方法です。</span><span class="sxs-lookup"><span data-stu-id="f056d-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f056d-107">例</span><span class="sxs-lookup"><span data-stu-id="f056d-107">Example</span></span>  
 <span data-ttu-id="f056d-108"><xref:System.Xml.Linq.XContainer.Element%2A> メソッドの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f056d-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="f056d-109">この例では、`po` という名前の XML ツリーを受け取り、`Comment` という名前の最初の要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="f056d-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="f056d-110">Visual Basic の例では、配列インデクサー表記を使用して単一の要素を取得しています。</span><span class="sxs-lookup"><span data-stu-id="f056d-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="f056d-111">この例では、「[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f056d-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f056d-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f056d-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="f056d-113">例</span><span class="sxs-lookup"><span data-stu-id="f056d-113">Example</span></span>  
 <span data-ttu-id="f056d-114">上記と同じコードを使用して、名前空間内の XML から要素を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f056d-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="f056d-115">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f056d-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="f056d-116">この例では、XML ドキュメントの「[サンプル XML ファイル : 名前空間内の一般的な購買発注書](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="f056d-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f056d-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f056d-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f056d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f056d-118">See Also</span></span>  
 [<span data-ttu-id="f056d-119">LINQ to XML 軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="f056d-119">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

