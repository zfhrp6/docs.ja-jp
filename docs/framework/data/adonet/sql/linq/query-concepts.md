---
title: "クエリの概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a125749-ccb5-49d5-999d-d2db7171d74d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 907761184256b7cf51c7c0f20fa43ee603e0ab12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="query-concepts"></a><span data-ttu-id="9d1c4-102">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="9d1c4-102">Query Concepts</span></span>
<span data-ttu-id="9d1c4-103">このセクションでは、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリを設計するうえでの主要な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d1c4-103">This section describes key concepts for designing [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d1c4-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9d1c4-104">In This Section</span></span>  
 [<span data-ttu-id="9d1c4-105">LINQ to SQL クエリ</span><span class="sxs-lookup"><span data-stu-id="9d1c4-105">LINQ to SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-queries.md)  
 <span data-ttu-id="9d1c4-106">一般的な [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] トピックを参照し、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 固有のアイテムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9d1c4-106">Refers to general [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] topics, and explains items specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="9d1c4-107">リレーションシップを介したクエリの実行</span><span class="sxs-lookup"><span data-stu-id="9d1c4-107">Querying Across Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)  
 <span data-ttu-id="9d1c4-108">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] オブジェクト モデルで関連付けを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d1c4-108">Explains how to use associations in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="9d1c4-109">クエリのリモート実行とローカル実行</span><span class="sxs-lookup"><span data-stu-id="9d1c4-109">Remote vs. Local Execution</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)  
 <span data-ttu-id="9d1c4-110">クエリの実行場所を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d1c4-110">Explains how to specify where you want your query executed.</span></span>  
  
 [<span data-ttu-id="9d1c4-111">遅延読み込みと即時読み込み</span><span class="sxs-lookup"><span data-stu-id="9d1c4-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)  
 <span data-ttu-id="9d1c4-112">関連オブジェクトをいつ読み込むかを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d1c4-112">Describes how to specify when related objects are loaded.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9d1c4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d1c4-113">Related Sections</span></span>  
 [<span data-ttu-id="9d1c4-114">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9d1c4-114">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="9d1c4-115">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] テクノロジについて説明するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="9d1c4-115">Contains links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology.</span></span>  
  
 [<span data-ttu-id="9d1c4-116">オブジェクト ID</span><span class="sxs-lookup"><span data-stu-id="9d1c4-116">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 <span data-ttu-id="9d1c4-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のオブジェクト識別子の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d1c4-117">Explains the concept of object identity in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="9d1c4-118">LINQ クエリの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="9d1c4-118">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="9d1c4-119">[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] のクエリ操作の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d1c4-119">Provides an introduction to query operations in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>
