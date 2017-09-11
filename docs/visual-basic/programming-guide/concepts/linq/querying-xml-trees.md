---
title: "XML ツリー (Visual Basic) のクエリ |Microsoft ドキュメント"
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
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9b2aa1e4852657590449be3e297302bf41ba3e5d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="31349-102">XML ツリーのクエリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31349-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="31349-103">ここでは、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="31349-103">This section provides examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>  
  
 <span data-ttu-id="31349-104">書き込みの詳細については[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリを実行、表示[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)します。</span><span class="sxs-lookup"><span data-stu-id="31349-104">For more information about writing [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="31349-105">XML ツリーをインスタンス化してからクエリを記述することが、ツリーからデータを抽出する最も効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="31349-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="31349-106">また、関数型構築と組み合わせてクエリを実行すると、元のドキュメントとは異なる形式の新しい XML ドキュメントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="31349-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31349-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="31349-107">In This Section</span></span>  
  
|<span data-ttu-id="31349-108">トピック</span><span class="sxs-lookup"><span data-stu-id="31349-108">Topic</span></span>|<span data-ttu-id="31349-109">説明</span><span class="sxs-lookup"><span data-stu-id="31349-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="31349-110">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31349-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="31349-111">XML ツリーのクエリの一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="31349-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="31349-112">射影と変換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31349-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="31349-113">XML ツリーからの射影と XML ツリーの変換の一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="31349-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="31349-114">詳細クエリ手法 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31349-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="31349-115">より高度なシナリオで役立つクエリ手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="31349-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="31349-116">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31349-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="31349-117">XPath 式の数を表示し、その[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]対応します。</span><span class="sxs-lookup"><span data-stu-id="31349-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="31349-118">(Visual Basic) の XML の純粋関数型変換</span><span class="sxs-lookup"><span data-stu-id="31349-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="31349-119">関数型のプログラミング形式でクエリを記述する簡単なチュートリアルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="31349-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31349-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="31349-120">See Also</span></span>  
 <span data-ttu-id="31349-121">[プログラミング ガイド (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="31349-121">[Programming Guide (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span></span>  
<span data-ttu-id="31349-122"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="31349-122"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)</span></span>
