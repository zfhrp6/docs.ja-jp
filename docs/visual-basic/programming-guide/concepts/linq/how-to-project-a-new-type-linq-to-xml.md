---
title: "方法: プロジェクトの新しい種類 (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b0e3149ca2fb5e36ebc759421e9489cbfe3dde5f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="98349-102">方法: プロジェクトの新しい種類 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98349-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="98349-103">このセクションの他の例として結果を返すクエリによる<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601>の`string`、および<xref:System.Collections.Generic.IEnumerable%601>の`int`</xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="98349-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="98349-104">これらは一般的な戻り値の型ですが、すべてのシナリオに適切であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="98349-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="98349-105">多くの場合、クエリを返す必要が、<xref:System.Collections.Generic.IEnumerable%601>の他の種類</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="98349-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98349-106">例</span><span class="sxs-lookup"><span data-stu-id="98349-106">Example</span></span>  
 <span data-ttu-id="98349-107">この例では、`Select` 句でオブジェクトをインスタンス化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="98349-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="98349-108">コードでは、まずコンストラクターを使用して新しいクラスを定義し、次に、式が新しいクラスの新しいインスタンスになるように `Select` ステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="98349-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="98349-109">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="98349-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="98349-110">この例では、`M:System.Xml.Linq.XElement.Element`メソッドのトピックで導入された[方法: 単一の子要素 (LINQ to XML) を取得 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="98349-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="98349-111">また、キャストを使用して、`M:System.Xml.Linq.XElement.Element` メソッドによって返された要素の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="98349-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="98349-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="98349-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="98349-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="98349-113">See Also</span></span>  
 [<span data-ttu-id="98349-114">射影と変換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98349-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
