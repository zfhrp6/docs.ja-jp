---
title: "チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツを操作する |Microsoft ドキュメント"
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
ms.assetid: f8028ba8-2dd1-4425-930c-8cc23176ebbc
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 28ab2d19cba0344868061fbe1f59c546a569fbdc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-visual-basic"></a><span data-ttu-id="d609b-102">チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作</span><span class="sxs-lookup"><span data-stu-id="d609b-102">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>
<span data-ttu-id="d609b-103">このチュートリアルでは、関数型変換の方法と LINQ to XML を適用して XML ドキュメントを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d609b-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="d609b-104">Visual Basic の例では、クエリして、Microsoft Word で保存された Office Open XML WordprocessingML ドキュメント内の情報を操作します。</span><span class="sxs-lookup"><span data-stu-id="d609b-104">The Visual Basic examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="d609b-105">詳細については、次を参照してください。、 [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="d609b-105">For more information, see the [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) Web site.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d609b-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d609b-106">In This Section</span></span>  
  
|<span data-ttu-id="d609b-107">トピック</span><span class="sxs-lookup"><span data-stu-id="d609b-107">Topic</span></span>|<span data-ttu-id="d609b-108">説明</span><span class="sxs-lookup"><span data-stu-id="d609b-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d609b-109">WordprocessingML ドキュメント (Visual Basic) の構造</span><span class="sxs-lookup"><span data-stu-id="d609b-109">Shape of WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="d609b-110">WordprocessingML ドキュメントの詳細について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="d609b-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="d609b-111">ソース Office Open XML ドキュメント (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="d609b-111">Creating the Source Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="d609b-112">このチュートリアルのクエリのソース ドキュメントを作成するための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="d609b-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="d609b-113">既定の段落スタイル (Visual Basic) の検索</span><span class="sxs-lookup"><span data-stu-id="d609b-113">Finding the Default Paragraph Style (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="d609b-114">ドキュメントの既定のスタイルの名前を検索するクエリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d609b-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="d609b-115">段落とそのスタイル (Visual Basic) の取得</span><span class="sxs-lookup"><span data-stu-id="d609b-115">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="d609b-116">ドキュメントの段落のコレクションを取得するクエリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d609b-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="d609b-117">(Visual Basic) の段落のテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="d609b-117">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="d609b-118">前のクエリを拡張して各段落のテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="d609b-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="d609b-119">拡張メソッド (Visual Basic) を使用してリファクタリングします。</span><span class="sxs-lookup"><span data-stu-id="d609b-119">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="d609b-120">拡張メソッドを使用してリファクタリングすることにより、コードを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="d609b-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="d609b-121">純粋関数 (Visual Basic) を使用してリファクタリングします。</span><span class="sxs-lookup"><span data-stu-id="d609b-121">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="d609b-122">純粋関数を使用してリファクタリングすることにより、コードをさらに簡略化します。</span><span class="sxs-lookup"><span data-stu-id="d609b-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="d609b-123">異なる形式 (Visual Basic) に XML を射影すること</span><span class="sxs-lookup"><span data-stu-id="d609b-123">Projecting XML in a Different Shape (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="d609b-124">元のドキュメントとは異なる構造の XML を射影することにより、XML 変換を完了します。</span><span class="sxs-lookup"><span data-stu-id="d609b-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="d609b-125">(Visual Basic) の Word 文書でテキストの検索</span><span class="sxs-lookup"><span data-stu-id="d609b-125">Finding Text in Word Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="d609b-126">前のクエリを使用してドキュメント内の指定された文字列を検索します。</span><span class="sxs-lookup"><span data-stu-id="d609b-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="d609b-127">Office の詳細については Open XML WordprocessingML ドキュメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d609b-127">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="d609b-128">Office Open XML WordprocessingML ドキュメントの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="d609b-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d609b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="d609b-129">See Also</span></span>  
 <span data-ttu-id="d609b-130">[(Visual Basic) の XML の純粋関数型変換](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="d609b-130">[Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span></span>  
<span data-ttu-id="d609b-131"> [純粋関数型変換 (Visual Basic) の概要](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="d609b-131"> [Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)</span></span>
