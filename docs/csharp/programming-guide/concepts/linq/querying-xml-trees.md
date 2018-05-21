---
title: XML ツリーのクエリ (C#)
ms.date: 07/20/2015
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
ms.openlocfilehash: 5d2e40da26f30a0ece570acf2fd25684d1cba40f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="16fde-102">XML ツリーのクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="16fde-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="16fde-103">ここでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="16fde-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="16fde-104">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリの詳細については、[C# の LINQ の概要](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16fde-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="16fde-105">XML ツリーをインスタンス化してからクエリを記述することが、ツリーからデータを抽出する最も効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="16fde-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="16fde-106">また、関数型構築と組み合わせてクエリを実行すると、元のドキュメントとは異なる形式の新しい XML ドキュメントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="16fde-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16fde-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="16fde-107">In This Section</span></span>  
  
|<span data-ttu-id="16fde-108">トピック</span><span class="sxs-lookup"><span data-stu-id="16fde-108">Topic</span></span>|<span data-ttu-id="16fde-109">説明</span><span class="sxs-lookup"><span data-stu-id="16fde-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="16fde-110">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="16fde-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="16fde-111">XML ツリーのクエリの一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="16fde-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="16fde-112">プロジェクションと変換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="16fde-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="16fde-113">XML ツリーからの射影と XML ツリーの変換の一般的な例について説明します。</span><span class="sxs-lookup"><span data-stu-id="16fde-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="16fde-114">高度なクエリ手法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="16fde-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="16fde-115">より高度なシナリオで役立つクエリ手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="16fde-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="16fde-116">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="16fde-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="16fde-117">多くの XPath 式と対応する [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の式について説明します。</span><span class="sxs-lookup"><span data-stu-id="16fde-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="16fde-118">XML の純粋関数型変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="16fde-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="16fde-119">関数型のプログラミング形式でクエリを記述する簡単なチュートリアルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="16fde-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16fde-120">参照</span><span class="sxs-lookup"><span data-stu-id="16fde-120">See Also</span></span>  
 [<span data-ttu-id="16fde-121">プログラミング ガイド (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="16fde-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="16fde-122">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="16fde-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
