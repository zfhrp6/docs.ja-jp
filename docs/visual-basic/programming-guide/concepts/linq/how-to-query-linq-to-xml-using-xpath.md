---
title: "方法: LINQ to XML が XPath (Visual Basic) を使用してクエリを実行 |Microsoft ドキュメント"
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
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 586182367ea26539384ea630dde301fe447915b8
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="4df71-102">方法: LINQ to XML が XPath (Visual Basic) を使用してクエリを実行</span><span class="sxs-lookup"><span data-stu-id="4df71-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="4df71-103">このトピックでは、XPath を使用して XML ツリーに対してクエリを実行できる拡張メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4df71-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="4df71-104">詳細については、これらの拡張メソッドを使用して、 <xref:System.Xml.XPath.Extensions?displayProperty=fullName>。</xref:System.Xml.XPath.Extensions?displayProperty=fullName>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4df71-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="4df71-105">古いコードの広範な利用など、XPath を使用してクエリを実行する特別な理由がない限りは、XPath を LINQ to XML と共に使用することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="4df71-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="4df71-106">XPath クエリは実行されませんだけでなく[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="4df71-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df71-107">例</span><span class="sxs-lookup"><span data-stu-id="4df71-107">Example</span></span>  
 <span data-ttu-id="4df71-108">次の例は、小さな XML ツリーを作成し、使用して<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>要素のセットを選択します</xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>。</span><span class="sxs-lookup"><span data-stu-id="4df71-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="4df71-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4df71-109">This example produces the following output:</span></span>  
  
```  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4df71-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4df71-110">See Also</span></span>  
 [<span data-ttu-id="4df71-111">詳細クエリ手法 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4df71-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

