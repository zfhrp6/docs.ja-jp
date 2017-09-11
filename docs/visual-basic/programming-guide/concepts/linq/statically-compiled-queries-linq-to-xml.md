---
title: "静的にコンパイル済みクエリ (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 83d6e37a00477cedc4a5a4c520ad79ff764d5ff7
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="82923-102">静的にコンパイル済みクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82923-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="82923-103">代わりに LINQ を XML で最も重要なパフォーマンスのいずれかの利点<xref:System.Xml.XmlDocument>を LINQ to XML クエリでは静的にコンパイル、実行時に XPath クエリを解釈する必要があります</xref:System.Xml.XmlDocument>。</span><span class="sxs-lookup"><span data-stu-id="82923-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="82923-104">この機能は LINQ to XML に組み込まれているので、追加の手順を実行することなく利用できますが、その違いを理解しておくと、この&2; つの技術のどちらかを選ぶときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="82923-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="82923-105">このトピックでは、相違点について説明します。</span><span class="sxs-lookup"><span data-stu-id="82923-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="82923-106">静的にコンパイルされたクエリと XPath</span><span class="sxs-lookup"><span data-stu-id="82923-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="82923-107">次の例は、指定した名前と指定した値の属性がある子孫要素を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="82923-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="82923-108">次に示すのは、これに相当する XPath 式です。</span><span class="sxs-lookup"><span data-stu-id="82923-108">The following is the equivalent XPath expression:</span></span>  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="82923-109">この例のクエリ式は、コンパイラによってメソッドベースのクエリ構文に書き換えられています。</span><span class="sxs-lookup"><span data-stu-id="82923-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="82923-110">メソッドベースのクエリ構文で書かれた次の例では、前の例と同じ結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="82923-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <span data-ttu-id="82923-111"><xref:System.Linq.Enumerable.Where%2A>メソッドは、拡張メソッド</xref:System.Linq.Enumerable.Where%2A>。</span><span class="sxs-lookup"><span data-stu-id="82923-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="82923-112">詳細については、次を参照してください。[拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)します。</span><span class="sxs-lookup"><span data-stu-id="82923-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="82923-113"><xref:System.Linq.Enumerable.Where%2A>拡張メソッドは、次のように記述されているかのように、上記のクエリがコンパイルされた:</xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="82923-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="82923-114">この例では、前の&2; つの例と同じ結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="82923-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="82923-115">これは、静的にリンクされたメソッド呼び出しにクエリが効果的にコンパイルされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="82923-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="82923-116">これと反復子の遅延実行セマンティクスが組み合わさることで、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="82923-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="82923-117">反復子の遅延実行セマンティクスの詳細については、次を参照してください。[遅延実行とレイジー評価 linq to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="82923-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82923-118">これらは、コンパイラが書き込むコードの例です。</span><span class="sxs-lookup"><span data-stu-id="82923-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="82923-119">実際の実装はこれらの例と若干異なる可能性がありますが、パフォーマンスは同じか類似したものになります。</span><span class="sxs-lookup"><span data-stu-id="82923-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="82923-120">XmlDocument を使用した XPath 式の実行</span><span class="sxs-lookup"><span data-stu-id="82923-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="82923-121">次の例では使用<xref:System.Xml.XmlDocument>前の例と同じ結果を得るため:</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="82923-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 <span data-ttu-id="82923-122">このクエリには、LINQ to XML を使用する例と同じ出力が返されます。唯一の違いがありますが LINQ to XML が印刷された XML をインデント<xref:System.Xml.XmlDocument>しません</xref:System.Xml.XmlDocument>。</span><span class="sxs-lookup"><span data-stu-id="82923-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="82923-123">ただし、<xref:System.Xml.XmlDocument>アプローチ一般的にパフォーマンスが低く、LINQ to XML のため、<xref:System.Xml.XmlNode.SelectNodes%2A>メソッド必要があります、次の操作に、内部的に呼び出されるたびに:</xref:System.Xml.XmlNode.SelectNodes%2A> </xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="82923-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="82923-124">XPath 式を含んでいる文字列を解析してトークンに分解します。</span><span class="sxs-lookup"><span data-stu-id="82923-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="82923-125">トークンを検証して、XPath 式が有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="82923-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="82923-126">式を内部式ツリーに変換します。</span><span class="sxs-lookup"><span data-stu-id="82923-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="82923-127">ノードを反復処理し、式の評価に基づいて結果セットのノードを適切に選択します。</span><span class="sxs-lookup"><span data-stu-id="82923-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="82923-128">この場合、対応する LINQ to XML のクエリよりも処理量がかなり多くなります。</span><span class="sxs-lookup"><span data-stu-id="82923-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="82923-129">特定のパフォーマンスの違いは、さまざまな種類のクエリはによって異なりますが一般に LINQ to XML クエリは処理量が少ないためよりも優れて<xref:System.Xml.XmlDocument>。</xref:System.Xml.XmlDocument>を使用して XPath 式を評価します。</span><span class="sxs-lookup"><span data-stu-id="82923-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82923-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="82923-130">See Also</span></span>  
 [<span data-ttu-id="82923-131">パフォーマンス (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82923-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

