---
title: "チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)"
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
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 293e8de848f83517211e3f3ed640102a2c534764
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a><span data-ttu-id="ba98e-102">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-102">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>
<span data-ttu-id="ba98e-103">このチュートリアルでは、関数型変換の方法と LINQ to XML を適用して XML ドキュメントを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="ba98e-104">C# の例では、Microsoft Word で保存された Office Open XML WordprocessingML ドキュメント内の情報をクエリして操作します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-104">The C# examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="ba98e-105">詳細については、[OpenXML 開発者](http://go.microsoft.com/fwlink/?LinkID=95573)の Web サイトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba98e-105">For more information, see the [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) Web site.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba98e-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ba98e-106">In This Section</span></span>  
  
|<span data-ttu-id="ba98e-107">トピック</span><span class="sxs-lookup"><span data-stu-id="ba98e-107">Topic</span></span>|<span data-ttu-id="ba98e-108">説明</span><span class="sxs-lookup"><span data-stu-id="ba98e-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ba98e-109">WordprocessingML ドキュメントの構造 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-109">Shape of WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="ba98e-110">WordprocessingML ドキュメントの詳細について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="ba98e-111">ソースとなる Office Open XML ドキュメントの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-111">Creating the Source Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="ba98e-112">このチュートリアルのクエリのソース ドキュメントを作成するための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="ba98e-113">既定の段落スタイルの検索 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-113">Finding the Default Paragraph Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="ba98e-114">ドキュメントの既定のスタイルの名前を検索するクエリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="ba98e-115">段落とそのスタイルの取得 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-115">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="ba98e-116">ドキュメントの段落のコレクションを取得するクエリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="ba98e-117">段落のテキストの取得 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-117">Retrieving the Text of the Paragraphs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="ba98e-118">前のクエリを拡張して各段落のテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="ba98e-119">拡張メソッドを使用したリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-119">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="ba98e-120">拡張メソッドを使用してリファクタリングすることにより、コードを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="ba98e-121">純粋関数によるリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-121">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="ba98e-122">純粋関数を使用してリファクタリングすることにより、コードをさらに簡略化します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="ba98e-123">異なる構造の XML の射影 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-123">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="ba98e-124">元のドキュメントとは異なる構造の XML を射影することにより、XML 変換を完了します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="ba98e-125">Word 文書内のテキストの検索 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-125">Finding Text in Word Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="ba98e-126">前のクエリを使用してドキュメント内の指定された文字列を検索します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="ba98e-127">Office Open XML WordprocessingML ドキュメントの詳細 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-127">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="ba98e-128">Office Open XML WordprocessingML ドキュメントの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba98e-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba98e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba98e-129">See Also</span></span>  
 <span data-ttu-id="ba98e-130">[XML の純粋関数型変換 (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="ba98e-130">[Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span></span>  
 [<span data-ttu-id="ba98e-131">純粋関数型変換の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba98e-131">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)

