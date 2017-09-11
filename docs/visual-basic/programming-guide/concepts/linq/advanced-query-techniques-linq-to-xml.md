---
title: "詳細クエリ手法 (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 79be877c-fadc-4dfb-9f03-426082b13656
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6983fa5b9637210bb3c56e8f693eb4f956dab0a8
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="advanced-query-techniques-linq-to-xml-visual-basic"></a><span data-ttu-id="13afc-102">詳細クエリ手法 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13afc-102">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="13afc-103">ここでは、高度な [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリ手法の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13afc-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="13afc-104">In This Section</span></span>  
  
|<span data-ttu-id="13afc-105">トピック</span><span class="sxs-lookup"><span data-stu-id="13afc-105">Topic</span></span>|<span data-ttu-id="13afc-106">説明</span><span class="sxs-lookup"><span data-stu-id="13afc-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="13afc-107">方法:&2; つのコレクション (LINQ to XML) を結合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13afc-107">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="13afc-108">`Join` 句を使用して XML データでリレーションシップを利用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="13afc-109">方法: グループ化 (Visual Basic) を使用して階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="13afc-109">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="13afc-110">データをグループ化する方法と、グループ化に基づいて XML を生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="13afc-111">方法: LINQ to XML が XPath (Visual Basic) を使用してクエリを実行</span><span class="sxs-lookup"><span data-stu-id="13afc-111">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="13afc-112">XPath クエリに基づいてコレクションを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="13afc-113">方法: LINQ to XML 軸メソッド (Visual Basic) を記述</span><span class="sxs-lookup"><span data-stu-id="13afc-113">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="13afc-114">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 軸メソッドを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-114">Shows how to write a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axis method.</span></span>|  
|[<span data-ttu-id="13afc-115">方法: ツリー (Visual Basic) ですべてのノードを一覧表示</span><span class="sxs-lookup"><span data-stu-id="13afc-115">How to: List All Nodes in a Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="13afc-116">XML ツリー内のすべてのノードを一覧表示するユーティリティ メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-116">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="13afc-117">これは、XML ツリーを変更するコードをデバッグする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="13afc-117">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="13afc-118">方法: Office Open XML ドキュメント (Visual Basic の場合) から段落を取得</span><span class="sxs-lookup"><span data-stu-id="13afc-118">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="13afc-119">Office Open XML ドキュメントを開き、XElement オブジェクトのコレクション内の段落、段落のテキスト、および段落のスタイルを取得するコードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-119">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="13afc-120">方法: Office Open XML ドキュメント (Visual Basic) の変更</span><span class="sxs-lookup"><span data-stu-id="13afc-120">How to: Modify an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="13afc-121">Office Open XML ドキュメントを開き、変更し、保存するコードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-121">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="13afc-122">方法: ファイル システム (Visual Basic の場合) から XML ツリーを設定</span><span class="sxs-lookup"><span data-stu-id="13afc-122">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="13afc-123">ファイル システムから XML ツリーを作成するコードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="13afc-123">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13afc-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="13afc-124">See Also</span></span>  
 [<span data-ttu-id="13afc-125">XML ツリー (Visual Basic) のクエリ</span><span class="sxs-lookup"><span data-stu-id="13afc-125">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
