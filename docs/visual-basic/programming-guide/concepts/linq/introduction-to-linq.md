---
title: "LINQ (Visual Basic) の概要 |Microsoft ドキュメント"
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
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d2c02daacc2674da31715e5fda027b97e6b7bc97
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="3b79e-102">LINQ (Visual Basic) の概要</span><span class="sxs-lookup"><span data-stu-id="3b79e-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="3b79e-103">統合言語クエリ (LINQ) は、革新で導入された .NET Framework version 3.5 そのブリッジのオブジェクトの世界とデータの世界の差です。</span><span class="sxs-lookup"><span data-stu-id="3b79e-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="3b79e-104">これまでは、データに対するクエリとして表現されるもの時間や IntelliSense のサポートをコンパイル時の型チェックなしの単純な文字列。</span><span class="sxs-lookup"><span data-stu-id="3b79e-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="3b79e-105">さらに、データ ソースの種類ごとに異なるクエリ言語を習得する必要がある: SQL データベース、XML ドキュメント、さまざまな Web サービス、およびなどです。</span><span class="sxs-lookup"><span data-stu-id="3b79e-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="3b79e-106">LINQ では、*クエリ*Visual Basic での第一級の言語構成要素。</span><span class="sxs-lookup"><span data-stu-id="3b79e-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="3b79e-107">言語のキーワードと使い慣れた演算子を使用してオブジェクトの厳密に型指定のコレクションに対するクエリを記述するとします。</span><span class="sxs-lookup"><span data-stu-id="3b79e-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="3b79e-108">Visual Basic で LINQ クエリを記述するには SQL Server データベース、XML ドキュメント、ADO.NET データセット、およびサポートするようなオブジェクトのコレクションの<xref:System.Collections.IEnumerable>または汎用<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="3b79e-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="3b79e-109">LINQ のサポートは、多くの Web サービスおよびその他のデータベースの実装のサード パーティによっても表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b79e-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="3b79e-110">新しいプロジェクト、または既存のプロジェクトでの LINQ 以外のクエリと並行 LINQ クエリを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3b79e-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="3b79e-111">唯一の要件は、プロジェクトが .NET Framework 3.5 以降を対象とします。</span><span class="sxs-lookup"><span data-stu-id="3b79e-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="3b79e-112">Visual Studio から次の図は、完全な型チェック、IntelliSense のサポートと、c# および Visual Basic の両方で、SQL Server データベースに対して LINQ クエリを部分的に完了を示します。</span><span class="sxs-lookup"><span data-stu-id="3b79e-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="3b79e-113">![Intellisense を使用する LINQ クエリ](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="3b79e-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3b79e-114">次の手順</span><span class="sxs-lookup"><span data-stu-id="3b79e-114">Next Steps</span></span>  
 <span data-ttu-id="3b79e-115">LINQ の詳細については、最初に Getting Started セクションで基本的な概念をよく理解[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)で関心のある LINQ テクノロジのドキュメントを読み取り。</span><span class="sxs-lookup"><span data-stu-id="3b79e-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="3b79e-116">SQL Server データベース: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span><span class="sxs-lookup"><span data-stu-id="3b79e-116">SQL Server databases: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span></span>  
  
-   <span data-ttu-id="3b79e-117">XML ドキュメント: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="3b79e-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="3b79e-118">ADO.NET データセット: [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)</span><span class="sxs-lookup"><span data-stu-id="3b79e-118">ADO.NET Datasets: [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)</span></span>  
  
-   <span data-ttu-id="3b79e-119">.NET コレクション、ファイル、文字列に: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="3b79e-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b79e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b79e-120">See Also</span></span>  
 [<span data-ttu-id="3b79e-121">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b79e-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
