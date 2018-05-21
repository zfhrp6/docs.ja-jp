---
title: C# での既定の名前空間のスコープ 1
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 37b10c43071d4f6a9fb2a25d68ab2c100c27dde9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="6d95d-102">C# での既定の名前空間のスコープ</span><span class="sxs-lookup"><span data-stu-id="6d95d-102">Scope of Default Namespaces in C#</span></span>
<span data-ttu-id="6d95d-103">XML ツリーで表される既定の名前空間は、クエリのスコープ内にありません。</span><span class="sxs-lookup"><span data-stu-id="6d95d-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="6d95d-104">既定の名前空間に含まれる XML が存在する場合は、<xref:System.Xml.Linq.XNamespace> 変数を宣言し、この変数をローカル名と組み合わせて作成した修飾名をクエリで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d95d-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="6d95d-105">XML ツリーのクエリにおける最も一般的な問題の 1 つは、XML ツリーに既定の名前空間がある場合に、XML が名前空間に含まれていないものとして開発者がクエリを記述してしまうことです。</span><span class="sxs-lookup"><span data-stu-id="6d95d-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="6d95d-106">このトピックの最初に示す一連の例では、既定の名前空間内の XML が読み込まれても、クエリが不適切に実行される典型的な例を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d95d-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="6d95d-107">2 番目に示す一連の例では、名前空間内の XML に対してクエリを実行できるようにするために必要な修正を示しています。</span><span class="sxs-lookup"><span data-stu-id="6d95d-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d95d-108">例</span><span class="sxs-lookup"><span data-stu-id="6d95d-108">Example</span></span>  
 <span data-ttu-id="6d95d-109">この例では、名前空間内にある XML の作成、および空の結果セットを返すクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="6d95d-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6d95d-110">コード</span><span class="sxs-lookup"><span data-stu-id="6d95d-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6d95d-111">コメント</span><span class="sxs-lookup"><span data-stu-id="6d95d-111">Comments</span></span>  
 <span data-ttu-id="6d95d-112">この例を実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="6d95d-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="6d95d-113">例</span><span class="sxs-lookup"><span data-stu-id="6d95d-113">Example</span></span>  
 <span data-ttu-id="6d95d-114">この例では、名前空間内にある XML の作成と、適切に記述されたクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="6d95d-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="6d95d-115">上記の不適切に記述された例に対して、C# を使用する場合は、<xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して初期化し、そのオブジェクトを <xref:System.Xml.Linq.XName> オブジェクトの指定時に使用するのが正しい方法です。</span><span class="sxs-lookup"><span data-stu-id="6d95d-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="6d95d-116">この場合、<xref:System.Xml.Linq.XElement.Elements%2A> メソッドの引数は <xref:System.Xml.Linq.XName> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="6d95d-116">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6d95d-117">コード</span><span class="sxs-lookup"><span data-stu-id="6d95d-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6d95d-118">コメント</span><span class="sxs-lookup"><span data-stu-id="6d95d-118">Comments</span></span>  
 <span data-ttu-id="6d95d-119">この例を実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="6d95d-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d95d-120">参照</span><span class="sxs-lookup"><span data-stu-id="6d95d-120">See Also</span></span>  
 [<span data-ttu-id="6d95d-121">XML 名前空間の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d95d-121">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
