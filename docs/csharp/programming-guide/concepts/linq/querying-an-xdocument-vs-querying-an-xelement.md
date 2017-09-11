---
title: "XDocument のクエリと XElement のクエリ (C#)"
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
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fa756d4adb1c361ef52e58bf6bdfd3bc2e31d13a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="3e5e8-102">XDocument のクエリと XElement のクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="3e5e8-102">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="3e5e8-103"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> によってドキュメントを読み込む場合、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> によって読み込む場合とは少し異なるクエリを記述する必要があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="3e5e8-104">XDocument.Load と XElement.Load の比較</span><span class="sxs-lookup"><span data-stu-id="3e5e8-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="3e5e8-105"><xref:System.Xml.Linq.XElement> によって XML ドキュメントを <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> に読み込む場合、XML ツリーのルートの <xref:System.Xml.Linq.XElement> には読み込んだドキュメントのルート要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="3e5e8-106">一方、<xref:System.Xml.Linq.XDocument> によって同じ XML ドキュメントを <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> に読み込む場合は、ツリーのルートは <xref:System.Xml.Linq.XDocument> ノードで、読み込んだドキュメントのルート要素は <xref:System.Xml.Linq.XElement> の許可されている 1 つの子 <xref:System.Xml.Linq.XDocument> ノードになります。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="3e5e8-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 軸は、ルート ノードを基準に動作します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="3e5e8-108">この最初の例では、<xref:System.Xml.Linq.XElement.Load%2A> を使用して XML ツリー読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="3e5e8-109">次に、ツリーのルートの子要素をクエリします。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="3e5e8-110">この例では、次の出力が生成されることが想定されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="3e5e8-111">次の例は上の例と同じですが、<xref:System.Xml.Linq.XDocument> ではなく <xref:System.Xml.Linq.XElement> に XML ツリーが読み込まれる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="3e5e8-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="3e5e8-113">この同じクエリでは、3 つの子ノードではなく 1 つの `Root` ノードが返されたことがわかります。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="3e5e8-114">これに対処する 1 つの方法は、次のように、軸メソッドにアクセスする前に <xref:System.Xml.Linq.XDocument.Root%2A> プロパティを使用することです。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="3e5e8-115">このクエリは、<xref:System.Xml.Linq.XElement> をルートとするツリーのクエリと同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="3e5e8-116">この例では次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e5e8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e5e8-117">See Also</span></span>  
 [<span data-ttu-id="3e5e8-118">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3e5e8-118">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

