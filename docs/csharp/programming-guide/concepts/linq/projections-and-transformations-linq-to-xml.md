---
title: "プロジェクションと変換 (LINQ to XML) (C#)"
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
ms.assetid: bb0457ab-1823-47e6-9d2d-c93c958cc913
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9dc3f97281f2cd13a44e52c441b537e9e2c640a6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="projections-and-transformations-linq-to-xml-c"></a><span data-ttu-id="8e572-102">プロジェクションと変換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-102">Projections and Transformations (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8e572-103">ここでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] のプロジェクションと変換の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e572-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8e572-104">In This Section</span></span>  
  
|<span data-ttu-id="8e572-105">トピック</span><span class="sxs-lookup"><span data-stu-id="8e572-105">Topic</span></span>|<span data-ttu-id="8e572-106">説明</span><span class="sxs-lookup"><span data-stu-id="8e572-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8e572-107">方法: LINQ to XML を使用してディクショナリを操作する (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-107">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="8e572-108">ディクショナリを XML に変換する方法、および XML をディクショナリに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="8e572-109">方法: XML ツリーの構造を変換する (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-109">How to: Transform the Shape of an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="8e572-110">XML ドキュメントの構造を変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="8e572-111">方法: プロジェクションの型を制御する (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-111">How to: Control the Type of a Projection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="8e572-112">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリの型を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="8e572-113">方法: 新しい型を射影する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-113">How to: Project a New Type (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="8e572-114">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリからユーザー定義型のコレクションを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="8e572-115">方法: オブジェクト グラフを射影する (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-115">How to: Project an Object Graph (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="8e572-116">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリから複雑なオブジェクト グラフを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="8e572-117">方法: 匿名型を射影する (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-117">How to: Project an Anonymous Type (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="8e572-118">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリから匿名オブジェクトのコレクションを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="8e572-119">方法: XML からテキスト ファイルを生成する (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-119">How to: Generate Text Files from XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="8e572-120">XML ファイルを XML 以外のテキスト ファイルに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="8e572-121">方法: CSV ファイルから XML を生成する (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-121">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="8e572-122">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] を使用して CSV ファイルを解析し、そのファイルから XML を生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e572-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e572-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e572-123">See Also</span></span>  
 [<span data-ttu-id="8e572-124">XML ツリーのクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="8e572-124">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)

