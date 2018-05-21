---
title: LINQ の概要 (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: 3c32c20efec55568a668c5dba55baf8f3ebbee7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="9736a-102">LINQ の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="9736a-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="9736a-103">統合言語クエリ (LINQ) は、.NET Framework Version 3.5 で導入された、オブジェクトとデータの溝を埋める画期的な手法です。</span><span class="sxs-lookup"><span data-stu-id="9736a-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="9736a-104">これまでは、データに対するクエリは、コンパイル時の型チェックや IntelliSense のサポートなしに、単純な文字列として表現されてきました。</span><span class="sxs-lookup"><span data-stu-id="9736a-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="9736a-105">さらに、SQL データベース、XML ドキュメント、さまざまな Web サービスといったデータ ソースの種類ごとに、異なるクエリ言語を習得する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="9736a-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="9736a-106">LINQ により、"*クエリ*" は C# での高度な言語構成要素になります。</span><span class="sxs-lookup"><span data-stu-id="9736a-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="9736a-107">厳密に型指定されているオブジェクトのコレクションに対して、言語キーワードと使い慣れた演算子を用いてクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="9736a-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="9736a-108">C# を使って LINQ クエリを記述できます。対象は、<xref:System.Collections.IEnumerable> またはジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスをサポートする SQL Server データベース、XML ドキュメント、ADO.NET データセット、その他のオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="9736a-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="9736a-109">サード パーティからも、多くの Web サービスとその他のデータベース実装に対する LINQ のサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="9736a-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="9736a-110">新しいプロジェクトで LINQ クエリを使用できるほか、既存のプロジェクトで LINQ 以外のクエリを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9736a-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="9736a-111">唯一の要件は、プロジェクトが .NET Framework 3.5 以降をターゲットとしていることです。</span><span class="sxs-lookup"><span data-stu-id="9736a-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="9736a-112">次の Visual Studio の図は、SQL Server データベースに対して部分的に完了した LINQ クエリを示しています。このクエリは C# および Visual Basic の両方で記述されており、完全な型チェックと IntelliSense に対応しています。</span><span class="sxs-lookup"><span data-stu-id="9736a-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="9736a-113">![Intellisense を使用する LINQ クエリ](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="9736a-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9736a-114">次の手順</span><span class="sxs-lookup"><span data-stu-id="9736a-114">Next Steps</span></span>  
 <span data-ttu-id="9736a-115">LINQ の詳細については、最初に「[C# の LINQ の概要](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)」の概要に関するセクションで基本的な概念を理解し、次に関心のある LINQ テクノロジのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9736a-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="9736a-116">SQL Server データベース: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="9736a-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="9736a-117">XML ドキュメント: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="9736a-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="9736a-118">ADO.NET データセット: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="9736a-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="9736a-119">.NET のコレクション、ファイル、文字列など: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="9736a-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9736a-120">参照</span><span class="sxs-lookup"><span data-stu-id="9736a-120">See Also</span></span>  
 [<span data-ttu-id="9736a-121">統合言語クエリ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9736a-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
