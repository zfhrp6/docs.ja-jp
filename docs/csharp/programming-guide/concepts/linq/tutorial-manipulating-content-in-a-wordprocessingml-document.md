---
title: "チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dca728cf48c6af6437beb43bcb6a8c8b7283d639
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2018
---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a><span data-ttu-id="bc508-102">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-102">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>
<span data-ttu-id="bc508-103">このチュートリアルでは、関数型変換の方法と LINQ to XML を適用して XML ドキュメントを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc508-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="bc508-104">C# の例では、Microsoft Word で保存された Office Open XML WordprocessingML ドキュメント内の情報をクエリして操作します。</span><span class="sxs-lookup"><span data-stu-id="bc508-104">The C# examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="bc508-105">詳細については、[WordprocessingML の概要](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc508-105">For more information, see [Introduction to WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc508-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bc508-106">In This Section</span></span>  
  
|<span data-ttu-id="bc508-107">トピック</span><span class="sxs-lookup"><span data-stu-id="bc508-107">Topic</span></span>|<span data-ttu-id="bc508-108">説明</span><span class="sxs-lookup"><span data-stu-id="bc508-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="bc508-109">WordprocessingML ドキュメントの構造 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-109">Shape of WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="bc508-110">WordprocessingML ドキュメントの詳細について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="bc508-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="bc508-111">ソースとなる Office Open XML ドキュメントの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-111">Creating the Source Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="bc508-112">このチュートリアルのクエリのソース ドキュメントを作成するための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc508-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="bc508-113">既定の段落スタイルの検索 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-113">Finding the Default Paragraph Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="bc508-114">ドキュメントの既定のスタイルの名前を検索するクエリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bc508-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="bc508-115">段落とそのスタイルの取得 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-115">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="bc508-116">ドキュメントの段落のコレクションを取得するクエリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bc508-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="bc508-117">段落のテキストの取得 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-117">Retrieving the Text of the Paragraphs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="bc508-118">前のクエリを拡張して各段落のテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="bc508-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="bc508-119">拡張メソッドを使用したリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-119">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="bc508-120">拡張メソッドを使用してリファクタリングすることにより、コードを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="bc508-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="bc508-121">純粋関数によるリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-121">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="bc508-122">純粋関数を使用してリファクタリングすることにより、コードをさらに簡略化します。</span><span class="sxs-lookup"><span data-stu-id="bc508-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="bc508-123">異なる構造の XML の射影 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-123">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="bc508-124">元のドキュメントとは異なる構造の XML を射影することにより、XML 変換を完了します。</span><span class="sxs-lookup"><span data-stu-id="bc508-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="bc508-125">Word 文書内のテキストの検索 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-125">Finding Text in Word Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="bc508-126">前のクエリを使用してドキュメント内の指定された文字列を検索します。</span><span class="sxs-lookup"><span data-stu-id="bc508-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="bc508-127">Office Open XML WordprocessingML ドキュメントの詳細 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-127">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="bc508-128">Office Open XML WordprocessingML ドキュメントの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc508-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc508-129">参照</span><span class="sxs-lookup"><span data-stu-id="bc508-129">See Also</span></span>  
 [<span data-ttu-id="bc508-130">XML の純粋関数型変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-130">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)  
 [<span data-ttu-id="bc508-131">純粋関数型変換の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc508-131">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
