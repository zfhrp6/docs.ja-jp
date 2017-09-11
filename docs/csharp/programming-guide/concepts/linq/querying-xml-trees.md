---
title: "XML ツリーのクエリ (C#)"
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
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4bad11434ed2610492854d5ec4a7a84bceb189f3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="1b0a4-102">XML ツリーのクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="1b0a4-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="1b0a4-103">ここでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="1b0a4-104">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリの詳細については、[C# の LINQ の概要](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="1b0a4-105">XML ツリーをインスタンス化してからクエリを記述することが、ツリーからデータを抽出する最も効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="1b0a4-106">また、関数型構築と組み合わせてクエリを実行すると、元のドキュメントとは異なる形式の新しい XML ドキュメントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b0a4-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1b0a4-107">In This Section</span></span>  
  
|<span data-ttu-id="1b0a4-108">トピック</span><span class="sxs-lookup"><span data-stu-id="1b0a4-108">Topic</span></span>|<span data-ttu-id="1b0a4-109">説明</span><span class="sxs-lookup"><span data-stu-id="1b0a4-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1b0a4-110">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1b0a4-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="1b0a4-111">XML ツリーのクエリの一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="1b0a4-112">プロジェクションと変換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1b0a4-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="1b0a4-113">XML ツリーからの射影と XML ツリーの変換の一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="1b0a4-114">高度なクエリ手法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1b0a4-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="1b0a4-115">より高度なシナリオで役立つクエリ手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="1b0a4-116">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1b0a4-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="1b0a4-117">多くの XPath 式と対応する [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の式について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="1b0a4-118">XML の純粋関数型変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="1b0a4-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="1b0a4-119">関数型のプログラミング形式でクエリを記述する簡単なチュートリアルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1b0a4-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b0a4-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b0a4-120">See Also</span></span>  
 <span data-ttu-id="1b0a4-121">[プログラミング ガイド (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1b0a4-121">[Programming Guide (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span></span>  
 [<span data-ttu-id="1b0a4-122">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="1b0a4-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

