---
title: "方法: 中間値 (Visual Basic) を計算 |Microsoft ドキュメント"
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
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 033f813bdfa84eda68ac0edd0b38da2bb72158ee
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="c8319-102">方法: 中間値 (Visual Basic) を計算</span><span class="sxs-lookup"><span data-stu-id="c8319-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="c8319-103">この例では、並べ替え、フィルタリング、および選択を実行する際に使用できる中間値を計算する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8319-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8319-104">例</span><span class="sxs-lookup"><span data-stu-id="c8319-104">Example</span></span>  
 <span data-ttu-id="c8319-105">次の例では、`Let` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8319-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="c8319-106">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 数値データ (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="c8319-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 <span data-ttu-id="c8319-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c8319-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="c8319-108">例</span><span class="sxs-lookup"><span data-stu-id="c8319-108">Example</span></span>  
 <span data-ttu-id="c8319-109">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="c8319-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c8319-110">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="c8319-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="c8319-111">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 数値データ、Namespace を](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="c8319-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c8319-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c8319-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8319-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8319-113">See Also</span></span>  
 [<span data-ttu-id="c8319-114">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8319-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

