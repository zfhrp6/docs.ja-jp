---
title: "データベースに対するクエリの実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5204ceaf99d280ae1d26a896e5a66bfbf4de96dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="querying-the-database"></a><span data-ttu-id="0bbf9-102">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="0bbf9-102">Querying the Database</span></span>
<span data-ttu-id="0bbf9-103">ここでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトにおけるクエリの開発と実行の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0bbf9-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0bbf9-104">In This Section</span></span>  
 [<span data-ttu-id="0bbf9-105">方法 : クエリで情報を取得する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-105">How to: Query for Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-query-for-information.md)  
 <span data-ttu-id="0bbf9-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のクエリが、基本的には [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] のクエリとほとんど同じであることを簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="0bbf9-107">方法 : 情報を読み取り専用として取得する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-107">How to: Retrieve Information As Read-Only</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="0bbf9-108">データを変更する必要がない場合に、クエリのパフォーマンスを向上させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="0bbf9-109">方法 : 取得する関連データの量を制御する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-109">How to: Control How Much Related Data Is Retrieved</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="0bbf9-110">メイン ターゲットと一緒にどの関連データを取得するかを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="0bbf9-111">方法 : 関連データをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-111">How to: Filter Related Data</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-related-data.md)  
 <span data-ttu-id="0bbf9-112">サブクエリを使用して関連データを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="0bbf9-113">方法 : 遅延読み込みをオフにする</span><span class="sxs-lookup"><span data-stu-id="0bbf9-113">How to: Turn Off Deferred Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="0bbf9-114">遅延読み込みをオフにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="0bbf9-115">方法 : SQL クエリを直接実行する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-115">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="0bbf9-116">SQL 言語を使用してクエリを発行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="0bbf9-117">方法 : クエリを格納および再利用する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-117">How to: Store and Reuse Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="0bbf9-118">クエリを 1 回だけコンパイルし、異なるパラメーターで複数回使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="0bbf9-119">方法 : クエリで複合キーを処理する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-119">How to: Handle Composite Keys in Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="0bbf9-120">演算子が 1 つの引数しか受け取らない場合に、複数の列を 1 つのクエリに含める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="0bbf9-121">方法 : 多くのオブジェクトを一度に取得する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-121">How to: Retrieve Many Objects At Once</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="0bbf9-122"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="0bbf9-123">方法 : DataContext レベルでフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="0bbf9-123">How to: Filter at the DataContext Level</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="0bbf9-124"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> のもう 1 つの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="0bbf9-125">クエリの例</span><span class="sxs-lookup"><span data-stu-id="0bbf9-125">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="0bbf9-126">クエリの例を多数示します。</span><span class="sxs-lookup"><span data-stu-id="0bbf9-126">Provides many examples of queries.</span></span>
