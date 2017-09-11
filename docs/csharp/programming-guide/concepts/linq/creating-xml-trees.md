---
title: "XML ツリーの作成 (C#)"
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
ms.assetid: bccc3e0a-c08c-468e-9d30-e075670fdace
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 99b197b86096b803b9732ab2546b23ff59e3e2fe
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-xml-trees-c"></a><span data-ttu-id="d1887-102">XML ツリーの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="d1887-102">Creating XML Trees (C#)</span></span>
<span data-ttu-id="d1887-103">最も一般的な XML タスクの 1 つは、XML ツリーの構築です。</span><span class="sxs-lookup"><span data-stu-id="d1887-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="d1887-104">ここでは、XML ツリーを作成するいくつかの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1887-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1887-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d1887-105">In This Section</span></span>  
  
|<span data-ttu-id="d1887-106">トピック</span><span class="sxs-lookup"><span data-stu-id="d1887-106">Topic</span></span>|<span data-ttu-id="d1887-107">説明</span><span class="sxs-lookup"><span data-stu-id="d1887-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d1887-108">関数型構築 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1887-108">Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="d1887-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の関数型構築の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="d1887-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="d1887-110">関数型構築は、単一のステートメントで XML ツリーの全体または一部を作成するための機能です。</span><span class="sxs-lookup"><span data-stu-id="d1887-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="d1887-111">このトピックでは、XML ツリーを構築する際にクエリを組み込む方法も示します。</span><span class="sxs-lookup"><span data-stu-id="d1887-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="d1887-112">C# での XML ツリーの作成 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d1887-112">Creating XML Trees in C# (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md)|<span data-ttu-id="d1887-113">C# でツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1887-113">Shows how to create trees in C#.</span></span>|  
|[<span data-ttu-id="d1887-114">複製とアタッチ (C#)</span><span class="sxs-lookup"><span data-stu-id="d1887-114">Cloning vs. Attaching (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="d1887-115">既存の XML ツリーからノードを追加する場合 (ノードは複製されてから追加されます) と親のないノードを追加する場合 (ノードは単に追加されます) の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d1887-115">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="d1887-116">XML の解析 (C#)</span><span class="sxs-lookup"><span data-stu-id="d1887-116">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="d1887-117">さまざまなソースの XML を解析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1887-117">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d1887-118"> は、XML の解析に使用する <xref:System.Xml.XmlReader> の上位に階層化されます。</span><span class="sxs-lookup"><span data-stu-id="d1887-118"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="d1887-119">方法: XmlWriter を使用して XML ツリーを設定する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1887-119">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="d1887-120"><xref:System.Xml.XmlWriter> を使用して XML ツリーを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1887-120">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="d1887-121">方法: XSD を使用して検証する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1887-121">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="d1887-122">XSD を使用して XML ツリーを検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1887-122">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="d1887-123">XElement オブジェクトと XDocument オブジェクトの有効なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="d1887-123">Valid Content of XElement and XDocument Objects</span></span>](../../../../csharp/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects3.md)|<span data-ttu-id="d1887-124">コンストラクターやメソッドに渡すことができる有効な引数について説明します。これらのコンストラクターやメソッドは、コンテンツを要素やドキュメントに追加するためのものです。</span><span class="sxs-lookup"><span data-stu-id="d1887-124">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1887-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1887-125">See Also</span></span>  
 [<span data-ttu-id="d1887-126">プログラミング ガイド (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1887-126">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

