---
title: "方法: 要素を並べ替える (C#)"
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
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a5c17b13f6f637559e2f99426b71947e795e0516
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="409e0-102">方法: 要素を並べ替える (C#)</span><span class="sxs-lookup"><span data-stu-id="409e0-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="409e0-103">この例では、結果を並べ替えるクエリの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="409e0-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="409e0-104">例</span><span class="sxs-lookup"><span data-stu-id="409e0-104">Example</span></span>  
 <span data-ttu-id="409e0-105">この例では、「[サンプル XML ファイル: 数値データ (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)」の XML ドキュメントを使います。</span><span class="sxs-lookup"><span data-stu-id="409e0-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="409e0-106">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="409e0-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="409e0-107">例</span><span class="sxs-lookup"><span data-stu-id="409e0-107">Example</span></span>  
 <span data-ttu-id="409e0-108">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="409e0-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="409e0-109">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="409e0-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="409e0-110">この例では、「[サンプル XML ファイル: 名前空間内の数値データ](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="409e0-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="409e0-111">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="409e0-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="409e0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="409e0-112">See Also</span></span>  
 <span data-ttu-id="409e0-113">[データの並べ替え (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md) </span><span class="sxs-lookup"><span data-stu-id="409e0-113">[Sorting Data (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md) </span></span>  
 [<span data-ttu-id="409e0-114">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="409e0-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

