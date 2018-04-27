---
title: LINQ to ADO.NET (ポータル ページ)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a266b23856c05c7b5ea07c9020d29b2797c0036
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-adonet-portal-page"></a><span data-ttu-id="85d32-102">LINQ to ADO.NET (ポータル ページ)</span><span class="sxs-lookup"><span data-stu-id="85d32-102">LINQ to ADO.NET (Portal Page)</span></span>
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)]<span data-ttu-id="85d32-103"> では、[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] プログラミング モデルを使用して [!INCLUDE[vstecado](~/includes/vstecado-md.md)] 内の列挙可能なオブジェクトに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="85d32-103"> enables you to query over any enumerable object in [!INCLUDE[vstecado](~/includes/vstecado-md.md)] by using the [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programming model.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85d32-104">[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] のドキュメントについては、.NET Framework SDK の「[LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)」の ADO.NET のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="85d32-104">The [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] documentation is located in the ADO.NET section of the .NET Framework SDK: [LINQ and ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).</span></span>  
  
 <span data-ttu-id="85d32-105">ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] には、[!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、および [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] の 3 つのテクノロジがあります。</span><span class="sxs-lookup"><span data-stu-id="85d32-105">There are three separate ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] technologies: [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], and [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)].</span></span> [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]<span data-ttu-id="85d32-106"> に対する豊富な最適化されたクエリを提供、 <xref:System.Data.DataSet>、 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server データベース スキーマを直接クエリすることができ、[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]クエリを実行することができます、[!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="85d32-106"> provides richer, optimized querying over the <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] enables you to directly query SQL Server database schemas, and [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] allows you to query an [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)].</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="85d32-107">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="85d32-107">LINQ to DataSet</span></span>  
 <span data-ttu-id="85d32-108"><xref:System.Data.DataSet> は、[!INCLUDE[vstecado](~/includes/vstecado-md.md)] で最も幅広く使用されているコンポーネントの 1 つであり、[!INCLUDE[vstecado](~/includes/vstecado-md.md)] の基礎である非接続型プログラミングの重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="85d32-108">The <xref:System.Data.DataSet> is one of the most widely used components in [!INCLUDE[vstecado](~/includes/vstecado-md.md)], and is a key element of the disconnected programming model that [!INCLUDE[vstecado](~/includes/vstecado-md.md)] is built on.</span></span> <span data-ttu-id="85d32-109">こうした突出した特長がある反面、<xref:System.Data.DataSet> のクエリ機能には制限もあります。</span><span class="sxs-lookup"><span data-stu-id="85d32-109">Despite this prominence, however, the <xref:System.Data.DataSet> has limited query capabilities.</span></span>  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]<span data-ttu-id="85d32-110"> では、他の多くのデータ ソースで使用できるのと同じクエリ機能を使用することで、豊富なクエリ機能を <xref:System.Data.DataSet> に組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="85d32-110"> enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for many other data sources.</span></span>  
  
 <span data-ttu-id="85d32-111">詳細については、「[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85d32-111">For more information, see [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="85d32-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="85d32-112">LINQ to SQL</span></span>  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]<span data-ttu-id="85d32-113"> には、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャが用意されています。</span><span class="sxs-lookup"><span data-stu-id="85d32-113"> provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="85d32-114">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="85d32-114">In [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="85d32-115">アプリケーションを実行すると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。</span><span class="sxs-lookup"><span data-stu-id="85d32-115">When you execute the application, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="85d32-116">データベースから結果が返されると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] で元の操作できるオブジェクトに変換されます。</span><span class="sxs-lookup"><span data-stu-id="85d32-116">When the database returns the results, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates them back into objects that you can manipulate.</span></span>  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]<span data-ttu-id="85d32-117"> には、データベースのストアド プロシージャ、ユーザー定義関数、オブジェクト モデルの継承のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="85d32-117"> includes support for stored procedures and user-defined functions in the database, and for inheritance in the object model.</span></span>  
  
 <span data-ttu-id="85d32-118">詳細については、「[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85d32-118">For more information, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="85d32-119">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="85d32-119">LINQ to Entities</span></span>  
 <span data-ttu-id="85d32-120">[!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)]を介して、リレーショナル データは .NET 環境でオブジェクトとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="85d32-120">Through the [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)], relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="85d32-121">これにより、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="85d32-121">This makes the object layer an ideal target for [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="85d32-122">この機能は、[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="85d32-122">This capability is known as [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)].</span></span> <span data-ttu-id="85d32-123">LINQ の詳細については、「[LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85d32-123">See [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d32-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="85d32-124">See Also</span></span>  
 [<span data-ttu-id="85d32-125">LINQ と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="85d32-125">LINQ and ADO.NET</span></span>](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)  
 [<span data-ttu-id="85d32-126">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85d32-126">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
