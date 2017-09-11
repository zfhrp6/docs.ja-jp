---
title: "方法:&2; つの場所のパス (XPATH-LINQ to XML) の和集合を検索 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 63c3399a60f8c26e39ef9d575a569b85bd7c5f68
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="cf01b-102">方法:&2; つの場所のパス (XPATH-LINQ to XML) の和集合を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf01b-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="cf01b-103">XPath を使用すると、2 つの XPath ロケーション パスの結果の和集合を検索できます。</span><span class="sxs-lookup"><span data-stu-id="cf01b-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="cf01b-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cf01b-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="cf01b-105">使用して、同じ結果を得ることができます、<xref:System.Linq.Enumerable.Concat%2A>標準クエリ演算子です</xref:System.Linq.Enumerable.Concat%2A>。</span><span class="sxs-lookup"><span data-stu-id="cf01b-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf01b-106">例</span><span class="sxs-lookup"><span data-stu-id="cf01b-106">Example</span></span>  
 <span data-ttu-id="cf01b-107">この例では、`Category` 要素と `Price` 要素をすべて検索し、それらを&1; つのコレクションに連結します。</span><span class="sxs-lookup"><span data-stu-id="cf01b-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="cf01b-108">注意してください、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]呼び出しをクエリ<xref:System.Xml.Linq.Extensions.InDocumentOrder%2A>結果の順序</xref:System.Xml.Linq.Extensions.InDocumentOrder%2A>。</span><span class="sxs-lookup"><span data-stu-id="cf01b-108">Note that the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="cf01b-109">XPath 式の評価結果もドキュメント順になります。</span><span class="sxs-lookup"><span data-stu-id="cf01b-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="cf01b-110">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 数値データ (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="cf01b-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="cf01b-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cf01b-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf01b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf01b-112">See Also</span></span>  
 [<span data-ttu-id="cf01b-113">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf01b-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

