---
title: '方法: 2 つのロケーション パスの和集合を検索する (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: cd98c1da2f2f8653c5db36f89a63dfdc7a7ab691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="c5ec2-102">方法: 2 つのロケーション パスの和集合を検索する (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c5ec2-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="c5ec2-103">XPath を使用すると、2 つの XPath ロケーション パスの結果の和集合を検索できます。</span><span class="sxs-lookup"><span data-stu-id="c5ec2-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="c5ec2-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c5ec2-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="c5ec2-105"><xref:System.Linq.Enumerable.Concat%2A> 標準クエリ演算子を使用すると、同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="c5ec2-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5ec2-106">例</span><span class="sxs-lookup"><span data-stu-id="c5ec2-106">Example</span></span>  
 <span data-ttu-id="c5ec2-107">この例では、`Category` 要素と `Price` 要素をすべて検索し、それらを 1 つのコレクションに連結します。</span><span class="sxs-lookup"><span data-stu-id="c5ec2-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="c5ec2-108">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリで <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> を呼び出して、結果を並べ替えていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c5ec2-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="c5ec2-109">XPath 式の評価結果もドキュメント順になります。</span><span class="sxs-lookup"><span data-stu-id="c5ec2-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="c5ec2-110">この例では、「[サンプル XML ファイル: 数値データ (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)」の XML ドキュメントを使います。</span><span class="sxs-lookup"><span data-stu-id="c5ec2-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="c5ec2-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c5ec2-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5ec2-112">参照</span><span class="sxs-lookup"><span data-stu-id="c5ec2-112">See Also</span></span>  
 [<span data-ttu-id="c5ec2-113">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c5ec2-113">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
