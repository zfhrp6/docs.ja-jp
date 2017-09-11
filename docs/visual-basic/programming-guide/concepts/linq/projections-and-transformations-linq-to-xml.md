---
title: "射影と変換 (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 297de224-b625-44cf-8c00-186b6189aa0e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 723685400aadbf883d7ad939e6a1dd5bdeb7ba09
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="projections-and-transformations-linq-to-xml-visual-basic"></a><span data-ttu-id="a767f-102">射影と変換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a767f-102">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a767f-103">このセクションでは、例を示します[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]射影と変換されます。</span><span class="sxs-lookup"><span data-stu-id="a767f-103">This section provides examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a767f-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a767f-104">In This Section</span></span>  
  
|<span data-ttu-id="a767f-105">トピック</span><span class="sxs-lookup"><span data-stu-id="a767f-105">Topic</span></span>|<span data-ttu-id="a767f-106">説明</span><span class="sxs-lookup"><span data-stu-id="a767f-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a767f-107">方法: LINQ to XML (Visual Basic) を使用してディクショナリを使用</span><span class="sxs-lookup"><span data-stu-id="a767f-107">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="a767f-108">ディクショナリを XML に変換する方法、および XML をディクショナリに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a767f-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="a767f-109">方法: XML ツリー (Visual Basic) の構造を変換</span><span class="sxs-lookup"><span data-stu-id="a767f-109">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="a767f-110">XML ドキュメントの構造を変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a767f-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="a767f-111">方法: 射影 (Visual Basic) の型を制御します。</span><span class="sxs-lookup"><span data-stu-id="a767f-111">How to: Control the Type of a Projection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="a767f-112">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリの型を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a767f-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="a767f-113">方法: プロジェクトの新しい種類 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a767f-113">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="a767f-114">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリからユーザー定義型のコレクションを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a767f-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="a767f-115">方法: プロジェクトのオブジェクト グラフ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a767f-115">How to: Project an Object Graph (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="a767f-116">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリから複雑なオブジェクト グラフを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a767f-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="a767f-117">方法: プロジェクトの匿名型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a767f-117">How to: Project an Anonymous Type (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="a767f-118">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリから匿名オブジェクトのコレクションを射影する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a767f-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="a767f-119">方法: XML (Visual Basic の場合) からテキスト ファイルを生成</span><span class="sxs-lookup"><span data-stu-id="a767f-119">How to: Generate Text Files from XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="a767f-120">XML ファイルを XML 以外のテキスト ファイルに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a767f-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="a767f-121">方法: CSV ファイル (Visual Basic) から XML を生成</span><span class="sxs-lookup"><span data-stu-id="a767f-121">How to: Generate XML from CSV Files (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="a767f-122">[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] を使用して CSV ファイルを解析し、そのファイルから XML を生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a767f-122">Shows how to use [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a767f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a767f-123">See Also</span></span>  
 [<span data-ttu-id="a767f-124">XML ツリー (Visual Basic) のクエリ</span><span class="sxs-lookup"><span data-stu-id="a767f-124">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
