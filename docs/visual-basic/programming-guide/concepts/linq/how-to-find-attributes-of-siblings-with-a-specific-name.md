---
title: "方法: 特定の名前 (XPATH-LINQ to XML) を持つ兄弟の属性を検索 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 598376bcf821940982a23fc2855e50765fe6be21
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="acc8d-102">方法: 特定の名前 (XPATH-LINQ to XML) を持つ兄弟の属性を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acc8d-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="acc8d-103">このトピックでは、コンテキスト ノードの兄弟が持つすべての属性を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="acc8d-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="acc8d-104">コレクション内にある特定の名前の属性のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="acc8d-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="acc8d-105">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="acc8d-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="acc8d-106">例</span><span class="sxs-lookup"><span data-stu-id="acc8d-106">Example</span></span>  
 <span data-ttu-id="acc8d-107">この例では、最初に `Book` 要素を検索し、次に `Book` という名前の兄弟要素をすべて検索します。その後、`id` という名前の属性をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="acc8d-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="acc8d-108">結果は属性のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="acc8d-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="acc8d-109">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="acc8d-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="acc8d-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="acc8d-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="acc8d-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="acc8d-111">See Also</span></span>  
 [<span data-ttu-id="acc8d-112">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acc8d-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

