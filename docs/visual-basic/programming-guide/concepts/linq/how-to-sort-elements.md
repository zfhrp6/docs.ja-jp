---
title: "方法: 要素 (Visual Basic) の並べ替え |Microsoft ドキュメント"
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
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5b36e9717b3366d73ee4c72390c88dde52248496
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-sort-elements-visual-basic"></a><span data-ttu-id="9787b-102">方法: 要素 (Visual Basic) を並べ替える</span><span class="sxs-lookup"><span data-stu-id="9787b-102">How to: Sort Elements (Visual Basic)</span></span>
<span data-ttu-id="9787b-103">この例では、結果を並べ替えるクエリの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9787b-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9787b-104">例</span><span class="sxs-lookup"><span data-stu-id="9787b-104">Example</span></span>  
 <span data-ttu-id="9787b-105">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 数値データ (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="9787b-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="9787b-106">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9787b-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="9787b-107">例</span><span class="sxs-lookup"><span data-stu-id="9787b-107">Example</span></span>  
 <span data-ttu-id="9787b-108">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="9787b-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9787b-109">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="9787b-109">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="9787b-110">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 数値データ、Namespace を](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="9787b-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="9787b-111">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9787b-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="9787b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="9787b-112">See Also</span></span>  
 <span data-ttu-id="9787b-113">[データの並べ替え](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md) </span><span class="sxs-lookup"><span data-stu-id="9787b-113">[Sorting Data](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md) </span></span>  
<span data-ttu-id="9787b-114"> [基本的なクエリ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="9787b-114"> [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)</span></span>
