---
title: "XML ツリー (Visual Basic) の作成 |Microsoft ドキュメント"
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
ms.assetid: e86ba12b-17de-4579-81bb-66322b84cfbe
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c60746a3da6255e4c245febf55151b41186a75b7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="creating-xml-trees-visual-basic"></a><span data-ttu-id="7f357-102">XML ツリー (Visual Basic) の作成</span><span class="sxs-lookup"><span data-stu-id="7f357-102">Creating XML Trees (Visual Basic)</span></span>
<span data-ttu-id="7f357-103">最も一般的な XML タスクの&1; つは、XML ツリーの構築です。</span><span class="sxs-lookup"><span data-stu-id="7f357-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="7f357-104">ここでは、XML ツリーを作成するいくつかの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f357-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f357-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7f357-105">In This Section</span></span>  
  
|<span data-ttu-id="7f357-106">トピック</span><span class="sxs-lookup"><span data-stu-id="7f357-106">Topic</span></span>|<span data-ttu-id="7f357-107">説明</span><span class="sxs-lookup"><span data-stu-id="7f357-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7f357-108">関数型構築 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f357-108">Functional Construction (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="7f357-109">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の関数型構築の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="7f357-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span> <span data-ttu-id="7f357-110">関数型構築は、単一のステートメントで XML ツリーの全体または一部を作成するための機能です。</span><span class="sxs-lookup"><span data-stu-id="7f357-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="7f357-111">このトピックでは、XML ツリーを構築する際にクエリを組み込む方法も示します。</span><span class="sxs-lookup"><span data-stu-id="7f357-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="7f357-112">Visual Basic で XML リテラルの概要</span><span class="sxs-lookup"><span data-stu-id="7f357-112">Introduction to XML Literals in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md)|<span data-ttu-id="7f357-113">内のツリーを作成する簡単な概要については、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] XML リテラルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="7f357-113">Provides a quick introduction to creating trees in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] by using XML literals.</span></span> <span data-ttu-id="7f357-114">このトピックには、XML リテラルの [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ドキュメントへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f357-114">This topic includes links to the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] documentation of XML literals.</span></span>|  
|[<span data-ttu-id="7f357-115">複製とアタッチ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f357-115">Cloning vs. Attaching (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="7f357-116">既存の XML ツリーからノードを追加する場合 (ノードは複製されてから追加されます) と親のないノードを追加する場合 (ノードは単に追加されます) の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7f357-116">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="7f357-117">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="7f357-117">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="7f357-118">さまざまなソースの XML を解析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f357-118">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="7f357-119">上位に階層化<xref:System.Xml.XmlReader>を使用して、XML の解析</xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="7f357-119"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="7f357-120">方法: XmlWriter (LINQ to XML) を使用して XML ツリーを作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f357-120">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="7f357-121"><xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter>を使用して XML ツリーを設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7f357-121">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="7f357-122">方法: XSD (LINQ to XML) を使用して検証 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f357-122">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="7f357-123">XSD を使用して XML ツリーを検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f357-123">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="7f357-124">XElement オブジェクトと XDocument オブジェクトの有効なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="7f357-124">Valid Content of XElement and XDocument Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects.md)|<span data-ttu-id="7f357-125">コンストラクターやメソッドに渡すことができる有効な引数について説明します。これらのコンストラクターやメソッドは、コンテンツを要素やドキュメントに追加するためのものです。</span><span class="sxs-lookup"><span data-stu-id="7f357-125">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f357-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f357-126">See Also</span></span>  
 [<span data-ttu-id="7f357-127">プログラミング ガイド (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f357-127">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
