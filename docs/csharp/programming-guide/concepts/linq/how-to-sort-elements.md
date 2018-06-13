---
title: '方法: 要素を並べ替える (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: a49b4fea8410075ca8b28f2ef7792738d063e256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319768"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="4dfaa-102">方法: 要素を並べ替える (C#)</span><span class="sxs-lookup"><span data-stu-id="4dfaa-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="4dfaa-103">この例では、結果を並べ替えるクエリの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4dfaa-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dfaa-104">例</span><span class="sxs-lookup"><span data-stu-id="4dfaa-104">Example</span></span>  
 <span data-ttu-id="4dfaa-105">この例では、「[サンプル XML ファイル: 数値データ (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)」の XML ドキュメントを使います。</span><span class="sxs-lookup"><span data-stu-id="4dfaa-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="4dfaa-106">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4dfaa-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="4dfaa-107">例</span><span class="sxs-lookup"><span data-stu-id="4dfaa-107">Example</span></span>  
 <span data-ttu-id="4dfaa-108">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="4dfaa-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4dfaa-109">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dfaa-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="4dfaa-110">この例では、「[サンプル XML ファイル: 名前空間内の数値データ](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4dfaa-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="4dfaa-111">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4dfaa-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dfaa-112">参照</span><span class="sxs-lookup"><span data-stu-id="4dfaa-112">See Also</span></span>  
 [<span data-ttu-id="4dfaa-113">データの並べ替え (C#)</span><span class="sxs-lookup"><span data-stu-id="4dfaa-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
 [<span data-ttu-id="4dfaa-114">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4dfaa-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
