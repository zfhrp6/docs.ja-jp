---
title: "プログラミング ガイド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03d4febc7e61425d0057c48949b18281ca3dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="programming-guide"></a><span data-ttu-id="2bd38-102">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2bd38-102">Programming Guide</span></span>
<span data-ttu-id="2bd38-103">ここでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のオブジェクト モデルを作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="2bd38-104">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、同じタスクの多くを[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]でも実行できます。</span><span class="sxs-lookup"><span data-stu-id="2bd38-104">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="2bd38-105">特定の問題に関する Microsoft のドキュメントを検索することもでき、参加することができます、 [LINQ フォーラム](http://go.microsoft.com/fwlink/?LinkId=76488)、専門家の複雑なトピックについての詳細を説明することができます。</span><span class="sxs-lookup"><span data-stu-id="2bd38-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="2bd38-106">また、[「LINQ to SQL: リレーショナル データのための .NET 統合言語クエリ」](http://go.microsoft.com/fwlink/?LinkId=93205) ホワイト ペーパーには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] テクノロジの詳細と、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] および C# のコード例が記載されています。</span><span class="sxs-lookup"><span data-stu-id="2bd38-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bd38-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2bd38-107">In This Section</span></span>  
 [<span data-ttu-id="2bd38-108">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="2bd38-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="2bd38-109">オブジェクト モデルを生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="2bd38-110">データベースとの通信</span><span class="sxs-lookup"><span data-stu-id="2bd38-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="2bd38-111">データベースへのコンジットとして <xref:System.Data.Linq.DataContext> オブジェクトを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="2bd38-112">データベースの照会</span><span class="sxs-lookup"><span data-stu-id="2bd38-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="2bd38-113">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でクエリを実行する方法を説明し、多数の例を示します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="2bd38-114">作成方法とデータの変更の送信</span><span class="sxs-lookup"><span data-stu-id="2bd38-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="2bd38-115">データベース内のデータを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="2bd38-116">デバッグのサポート</span><span class="sxs-lookup"><span data-stu-id="2bd38-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="2bd38-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトのデバッグ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="2bd38-118">背景情報</span><span class="sxs-lookup"><span data-stu-id="2bd38-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="2bd38-119">同時実行の競合の解決、新しいデータベースの作成など、上級ユーザー向けの追加項目が記載されています。</span><span class="sxs-lookup"><span data-stu-id="2bd38-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2bd38-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bd38-120">Related Sections</span></span>  
 [<span data-ttu-id="2bd38-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2bd38-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="2bd38-122">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] テクノロジの説明および機能の解説が記載されているトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="2bd38-123">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2bd38-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="2bd38-124">ストアド プロシージャの使用手順のトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="2bd38-125">LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="2bd38-125">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 <span data-ttu-id="2bd38-126">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使い始めるときに役立つリソースを示します。</span><span class="sxs-lookup"><span data-stu-id="2bd38-126">Provides resources to help you begin to learn about [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
