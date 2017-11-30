---
title: "XName オブジェクト (LINQ to XML) の事前アトミック化 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 967e41afc70290a4e4bdccabb8f3f4dd4ac4f6ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="9bb68-102">XName オブジェクト (LINQ to XML) の事前アトミック化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bb68-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9bb68-103">LINQ to XML でパフォーマンスを向上させる方法の 1 つは、<xref:System.Xml.Linq.XName> オブジェクトの事前アトミック化です。</span><span class="sxs-lookup"><span data-stu-id="9bb68-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="9bb68-104">事前アトミック化とは、<xref:System.Xml.Linq.XName> クラスと <xref:System.Xml.Linq.XElement> クラスのコンストラクターを使用して XML ツリーを作成する前に、文字列を <xref:System.Xml.Linq.XAttribute> オブジェクトに割り当てる操作です。</span><span class="sxs-lookup"><span data-stu-id="9bb68-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="9bb68-105">次に、(文字列から <xref:System.Xml.Linq.XName> への暗黙的な変換を使用する) コンストラクターに文字列を渡す代わりに、初期化された <xref:System.Xml.Linq.XName> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="9bb68-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="9bb68-106">これによって、特定の名前が繰り返される大きい XML ツリーを作成するときにパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="9bb68-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="9bb68-107">これを行うには、XML ツリーを構築する前に、<xref:System.Xml.Linq.XName> オブジェクトを宣言して初期化し、次に要素名と属性名に文字列を指定する代わりに <xref:System.Xml.Linq.XName> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb68-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="9bb68-108">この手法では、同じ名前の多数の要素や属性を作成する場合に、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="9bb68-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="9bb68-109">各自のシナリオで事前アトミック化をテストし、使用すべきかどうかを判断してください。</span><span class="sxs-lookup"><span data-stu-id="9bb68-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bb68-110">例</span><span class="sxs-lookup"><span data-stu-id="9bb68-110">Example</span></span>  
 <span data-ttu-id="9bb68-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9bb68-111">The following example demonstrates this.</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="9bb68-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9bb68-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="9bb68-113">次の例は同じ手法を示し、XML ドキュメントが名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="9bb68-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="9bb68-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9bb68-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="9bb68-115">次に示すのは、より実働環境に近い例です。</span><span class="sxs-lookup"><span data-stu-id="9bb68-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="9bb68-116">この例では、要素の内容がクエリによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="9bb68-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 <span data-ttu-id="9bb68-117">前の例では、名前が事前アトミック化されていない次の例に比べて良いパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="9bb68-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bb68-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bb68-118">See Also</span></span>  
 [<span data-ttu-id="9bb68-119">パフォーマンス (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bb68-119">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [<span data-ttu-id="9bb68-120">最小単位に分割 XName および XNamespace オブジェクト (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bb68-120">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
