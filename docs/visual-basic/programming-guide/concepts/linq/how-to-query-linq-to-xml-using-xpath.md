---
title: '方法: LINQ to XML を XPath (Visual Basic) を使用してクエリを実行'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d8f23bd8417c3f59377e5e677b08e403ecc1122d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639338"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="1ebe7-102">方法: LINQ to XML を XPath (Visual Basic) を使用してクエリを実行</span><span class="sxs-lookup"><span data-stu-id="1ebe7-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="1ebe7-103">このトピックでは、XPath を使用して XML ツリーに対してクエリを実行できる拡張メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1ebe7-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="1ebe7-104">これらの拡張メソッドの使用に関する詳細については、<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ebe7-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="1ebe7-105">古いコードの広範な利用など、XPath を使用してクエリを実行する特別な理由がない限りは、XPath を LINQ to XML と共に使用することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="1ebe7-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="1ebe7-106">XPath クエリは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリよりもパフォーマンスが低くなります。</span><span class="sxs-lookup"><span data-stu-id="1ebe7-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ebe7-107">例</span><span class="sxs-lookup"><span data-stu-id="1ebe7-107">Example</span></span>  
 <span data-ttu-id="1ebe7-108">次の例では、小さな XML ツリーを作成し、<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> を使用して要素のセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="1ebe7-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="1ebe7-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1ebe7-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ebe7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ebe7-110">See Also</span></span>  
 [<span data-ttu-id="1ebe7-111">詳細クエリ手法 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ebe7-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
