---
title: "方法: XPath を使用して LINQ to XML にクエリを実行する (C#)"
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
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6d7acf7519e6ab3384f2f34b8435fe96307921f0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="7c521-102">方法: XPath を使用して LINQ to XML にクエリを実行する (C#)</span><span class="sxs-lookup"><span data-stu-id="7c521-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="7c521-103">このトピックでは、XPath を使用して XML ツリーに対してクエリを実行できる拡張メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7c521-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="7c521-104">これらの拡張メソッドの使用に関する詳細については、<xref:System.Xml.XPath.Extensions?displayProperty=fullName> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c521-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="7c521-105">古いコードの広範な利用など、XPath を使用してクエリを実行する特別な理由がない限りは、XPath を LINQ to XML と共に使用することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="7c521-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="7c521-106">XPath クエリは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリよりもパフォーマンスが低くなります。</span><span class="sxs-lookup"><span data-stu-id="7c521-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c521-107">例</span><span class="sxs-lookup"><span data-stu-id="7c521-107">Example</span></span>  
 <span data-ttu-id="7c521-108">次の例では、小さな XML ツリーを作成し、<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> を使用して要素のセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="7c521-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="7c521-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7c521-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c521-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c521-110">See Also</span></span>  
 [<span data-ttu-id="7c521-111">高度なクエリ手法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c521-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

