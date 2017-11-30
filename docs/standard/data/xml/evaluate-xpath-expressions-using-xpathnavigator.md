---
title: "XPathNavigator による Xpath 式の評価"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d513f48155a582a5158cccdd682f5b8485caefd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="14252-102">XPathNavigator による Xpath 式の評価</span><span class="sxs-lookup"><span data-stu-id="14252-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="14252-103"><xref:System.Xml.XPath.XPathNavigator> クラスは、XPath 式を評価する <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="14252-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="14252-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドは XPath 式を受け取って評価し、XPath 式の結果に基づいて W3C XPath 型のブール値、数字、文字列、またはノード セットを返します。</span><span class="sxs-lookup"><span data-stu-id="14252-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="14252-105">Evaluate メソッド</span><span class="sxs-lookup"><span data-stu-id="14252-105">The Evaluate Method</span></span>  
 <span data-ttu-id="14252-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドは XPath 式を受け取って評価し、XPath 式の結果に基づいて W3C XPath 型のブール値 (<xref:System.Boolean>)、数字 (<xref:System.Double>)、文字列 (<xref:System.String>)、またはノード セット (<xref:System.Xml.XPath.XPathNodeIterator>) を返します。</span><span class="sxs-lookup"><span data-stu-id="14252-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="14252-107">たとえば、<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドは数値演算メソッドで使用できます。</span><span class="sxs-lookup"><span data-stu-id="14252-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="14252-108">次のサンプル コードは、`books.xml` ファイル内の本すべての総額を計算します。</span><span class="sxs-lookup"><span data-stu-id="14252-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="14252-109">この例は、`books.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="14252-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="14252-110">position 関数と last 関数</span><span class="sxs-lookup"><span data-stu-id="14252-110">position and last Functions</span></span>  
 <span data-ttu-id="14252-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドはオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="14252-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="14252-112"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドの 1 つは、パラメーターとして <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="14252-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="14252-113">この特定の <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドは、現在の評価対象コンテキストを指定するノード セット引数を許可することを除き、パラメーターとして <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> オブジェクトだけを受け取る <xref:System.Xml.XPath.XPathExpression> メソッドと同じです。</span><span class="sxs-lookup"><span data-stu-id="14252-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="14252-114">XPath の `position()` 関数および `last()` 関数は現在のコンテキスト ノードに相対的であるため、これらの関数ではコンテキストが必須です。</span><span class="sxs-lookup"><span data-stu-id="14252-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="14252-115">ロケーション ステップで述語として使用される場合を除き、XPath の `position()` 関数および `last()` 関数では、ノード セットへの参照が評価のために必須です。ノード セットへの参照がない場合、`position` 関数および `last` 関数は `0` を返します。</span><span class="sxs-lookup"><span data-stu-id="14252-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14252-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="14252-116">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="14252-117">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="14252-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="14252-118">XPathNavigator による XML データを選択します。</span><span class="sxs-lookup"><span data-stu-id="14252-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="14252-119">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="14252-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="14252-120">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="14252-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="14252-121">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="14252-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="14252-122">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="14252-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
