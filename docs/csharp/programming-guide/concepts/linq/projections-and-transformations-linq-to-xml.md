---
title: "プロジェクションと変換 (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb0457ab-1823-47e6-9d2d-c93c958cc913
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 81172ebb440bc2737bbe3f1de0f1dd3cf6e086c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="projections-and-transformations-linq-to-xml-c"></a><span data-ttu-id="f1f82-102">プロジェクションと変換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-102">Projections and Transformations (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f1f82-103">ここでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] のプロジェクションと変換の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1f82-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f1f82-104">In This Section</span></span>  
  
|<span data-ttu-id="f1f82-105">トピック</span><span class="sxs-lookup"><span data-stu-id="f1f82-105">Topic</span></span>|<span data-ttu-id="f1f82-106">説明</span><span class="sxs-lookup"><span data-stu-id="f1f82-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f1f82-107">方法: LINQ to XML を使用してディクショナリを操作する (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-107">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="f1f82-108">ディクショナリを XML に変換する方法、および XML をディクショナリに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="f1f82-109">方法: XML ツリーの構造を変換する (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-109">How to: Transform the Shape of an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="f1f82-110">XML ドキュメントの構造を変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="f1f82-111">方法: プロジェクションの型を制御する (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-111">How to: Control the Type of a Projection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="f1f82-112">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリの型を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="f1f82-113">方法: 新しい型を射影する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-113">How to: Project a New Type (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="f1f82-114">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリからユーザー定義型のコレクションを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="f1f82-115">方法: オブジェクト グラフを射影する (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-115">How to: Project an Object Graph (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="f1f82-116">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリから複雑なオブジェクト グラフを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="f1f82-117">方法: 匿名型を射影する (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-117">How to: Project an Anonymous Type (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="f1f82-118">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリから匿名オブジェクトのコレクションを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="f1f82-119">方法: XML からテキスト ファイルを生成する (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-119">How to: Generate Text Files from XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="f1f82-120">XML ファイルを XML 以外のテキスト ファイルに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="f1f82-121">方法: CSV ファイルから XML を生成する (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-121">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="f1f82-122">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] を使用して CSV ファイルを解析し、そのファイルから XML を生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1f82-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1f82-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1f82-123">See Also</span></span>  
 [<span data-ttu-id="f1f82-124">XML ツリーのクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="f1f82-124">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
