---
title: LINQ to SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 62f7a3b0fcefa9eb6f5b56d96217a9988a193104
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="linq-to-sql"></a><span data-ttu-id="b9dd2-102">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b9dd2-102">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b9dd2-103"> は [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] Version 3.5 のコンポーネントであり、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-103"> is a component of [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9dd2-104">リレーショナル データは 2 次元テーブル (*リレーション*または*フラット ファイル*) のコレクションで表され、共通の列がテーブルを相互に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-104">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="b9dd2-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を効果的に使用するには、リレーショナル データベースの基本原則を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-105">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="b9dd2-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="b9dd2-107">アプリケーションが実行されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-107">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="b9dd2-108">データベースから結果が返されると、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はそれをプログラミング言語で操作できるオブジェクトに変換し直します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-108">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="b9dd2-109">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用する開発者は、通常、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用します。これには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の機能の多くを実装するためのユーザー インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-109">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="b9dd2-110">このリリースの [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に含まれているドキュメントでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを構築するのに必要な基本的なビルド ブロック、プロセス、および手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-110">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="b9dd2-111">特定の問題に関する Microsoft のドキュメントを検索することもでき、参加することができます、 [LINQ フォーラム](http://go.microsoft.com/fwlink/?LinkId=76488)、専門家の複雑なトピックについての詳細を説明することができます。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-111">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="b9dd2-112">また、[「LINQ to SQL: リレーショナル データのための .NET 統合言語クエリ」](http://go.microsoft.com/fwlink/?LinkId=93205) ホワイト ペーパーには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] テクノロジの詳細と、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] および C# のコード例が記載されています。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-112">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9dd2-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b9dd2-113">In This Section</span></span>  
 [<span data-ttu-id="b9dd2-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="b9dd2-114">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 <span data-ttu-id="b9dd2-115">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の簡単な概要と、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して作業を始める方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-115">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="b9dd2-116">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b9dd2-116">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="b9dd2-117">マップ、クエリ、更新、デバッグ、および同様のタスクを行う手順を示します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-117">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="b9dd2-118">参照</span><span class="sxs-lookup"><span data-stu-id="b9dd2-118">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 <span data-ttu-id="b9dd2-119">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のさまざまな側面に関するリファレンス情報を示します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-119">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="b9dd2-120">SQL-CLR 型マッピング、標準クエリ演算子変換などのトピックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-120">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="b9dd2-121">サンプル</span><span class="sxs-lookup"><span data-stu-id="b9dd2-121">Samples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 <span data-ttu-id="b9dd2-122">[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] および C# のサンプルへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-122">Provides links to [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9dd2-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9dd2-123">Related Sections</span></span>  
 [<span data-ttu-id="b9dd2-124">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b9dd2-124">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 <span data-ttu-id="b9dd2-125">[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] テクノロジの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-125">Provides an overview of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies.</span></span>  
  
 [<span data-ttu-id="b9dd2-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="b9dd2-126">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="b9dd2-127">[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] ユーザーを対象に [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] テクノロジについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-127">Describes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies for [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] users.</span></span>  
  
 [<span data-ttu-id="b9dd2-128">LINQ to ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b9dd2-128">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/library/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 <span data-ttu-id="b9dd2-129">[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] ポータルにリンクします。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-129">Links to the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portal.</span></span>  
  
 [<span data-ttu-id="b9dd2-130">LINQ to SQL チュートリアル</span><span class="sxs-lookup"><span data-stu-id="b9dd2-130">LINQ to SQL Walkthroughs</span></span>](http://msdn.microsoft.com/library/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 <span data-ttu-id="b9dd2-131">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のチュートリアルを一覧します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-131">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="b9dd2-132">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="b9dd2-132">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 <span data-ttu-id="b9dd2-133">ドキュメントで使用されるサンプル データベースをダウンロードする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-133">Describes how to download sample databases used in the documentation.</span></span>  
  
 [<span data-ttu-id="b9dd2-134">LinqDataSource テクノロジの概要</span><span class="sxs-lookup"><span data-stu-id="b9dd2-134">LinqDataSource Technology Overview</span></span>](http://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136)  
 <span data-ttu-id="b9dd2-135"><xref:System.Web.UI.WebControls.LinqDataSource> コントロールが [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] データソース コントロールのアーキテクチャを通じて[!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] を Web 開発者に公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9dd2-135">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] to Web developers through the [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] data-source control architecture.</span></span>
