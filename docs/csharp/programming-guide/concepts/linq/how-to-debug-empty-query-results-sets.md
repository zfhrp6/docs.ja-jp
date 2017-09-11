---
title: "方法: 空のクエリ結果セットをデバッグする (C#)"
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
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 78c6d612e11f50bedf8f1c2e9826775494faa465
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="b1fd4-102">方法: 空のクエリ結果セットをデバッグする (C#)</span><span class="sxs-lookup"><span data-stu-id="b1fd4-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="b1fd4-103">XML ツリーのクエリにおける最も一般的な問題の 1 つは、XML ツリーに既定の名前空間がある場合に、XML が名前空間に含まれていないものとして開発者がクエリを記述してしまうことです。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="b1fd4-104">このトピックの最初に示す一連の例では、既定の名前空間内の XML が読み込まれ、クエリが不適切に実行される典型的な例を示しています。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="b1fd4-105">2 番目に示す一連の例では、名前空間内の XML に対してクエリを実行できるようにするために必要な修正を示しています。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="b1fd4-106">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-106">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1fd4-107">例</span><span class="sxs-lookup"><span data-stu-id="b1fd4-107">Example</span></span>  
 <span data-ttu-id="b1fd4-108">この例では、名前空間内にある XML の作成、および空の結果セットを返すクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="b1fd4-109">この例を実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="b1fd4-110">例</span><span class="sxs-lookup"><span data-stu-id="b1fd4-110">Example</span></span>  
 <span data-ttu-id="b1fd4-111">この例では、名前空間内にある XML の作成と、適切に記述されたクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="b1fd4-112">解決方法は、<xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して初期化し、そのオブジェクトを <xref:System.Xml.Linq.XName> オブジェクトの指定時に使用することです。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="b1fd4-113">この場合、<xref:System.Xml.Linq.XElement.Elements%2A> メソッドの引数は <xref:System.Xml.Linq.XName> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-113">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="b1fd4-114">この例を実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="b1fd4-114">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1fd4-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1fd4-115">See Also</span></span>  
 [<span data-ttu-id="b1fd4-116">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b1fd4-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

