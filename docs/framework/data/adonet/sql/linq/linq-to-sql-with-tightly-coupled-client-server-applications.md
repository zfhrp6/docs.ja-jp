---
title: "密結合クライアント サーバー アプリケーションと LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3879d8eeec498f2855ee2b540f77570ee91109f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a><span data-ttu-id="95bff-102">密結合クライアント サーバー アプリケーションと LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="95bff-102">LINQ to SQL with Tightly-Coupled Client-Server Applications</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="95bff-103">プレゼンテーション層の密結合のスマート クライアントと中間層で使用できます。</span><span class="sxs-lookup"><span data-stu-id="95bff-103"> can be used on the middle tier with tightly-coupled Smart Clients on the presentation layer.</span></span> <span data-ttu-id="95bff-104">読み取り専用データ アクセス、オプティミスティック同時実行チェックなし、またはタイムスタンプを使用したオプティミスティック同時実行のシナリオの場合、非リモートのシナリオに比べて複雑さはほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="95bff-104">In scenarios that involve read-only data access, no optimistic concurrency checks, or optimistic concurrency with timestamps, there is not much more complexity than with non-remote scenarios.</span></span> <span data-ttu-id="95bff-105">しかし、元の値を使用したオプティミスティック同時実行チェックをデータベースで行う必要がある場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は DataSet のようなレベルのデータ ラウンド トリップをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="95bff-105">However, when a database requires optimistic concurrency checks with original values, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not provide the level of support for round-tripping of data that you find in DataSets.</span></span> <span data-ttu-id="95bff-106">ただし、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中間層は任意のプラットフォーム上のクライアントとの間でデータをやり取りできます。</span><span class="sxs-lookup"><span data-stu-id="95bff-106">However, a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] middle tier can exchange data with clients on any platform.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="95bff-107">[!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)]クライアントにシリアル化された後に、エンティティの状態を追跡するためのインフラストラクチャを提供されません。</span><span class="sxs-lookup"><span data-stu-id="95bff-107"> in [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] provides no infrastructure for tracking entity state after they have been serialized to a client.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="95bff-108">ここで、データ層とプレゼンテーション層の間のやり取りは、小さな比較的アトミックなサービス指向アーキテクチャのできますが、元の値の任意のラウンド トリップは行われません。</span><span class="sxs-lookup"><span data-stu-id="95bff-108"> enables service-oriented architectures where interactions between the data and presentation layers are small and relatively atomic, but does not perform any round-tripping of original values.</span></span> <span data-ttu-id="95bff-109">このため、密結合のスマート クライアントを [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] と共に使用し、元の値を使ったオプティミスティック同時実行制御をデータベースで行う場合には、プレゼンテーション層と中間層の間で変更内容を通信するための独自の機構を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95bff-109">Therefore, if you want to use a tightly-coupled Smart Client with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and a database uses optimistic concurrency with original values, you will have to implement your own mechanism for communicating changes between the presentation tier and middle tier.</span></span> <span data-ttu-id="95bff-110">中間層で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用することの利点を考慮に入れて、この余分の作業を行うかどうかは、システム設計者の判断に任せられます。</span><span class="sxs-lookup"><span data-stu-id="95bff-110">It is up to the system designer to decide whether it makes sense to do this bit of extra work in exchange for the benefits that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides on the middle tier.</span></span> <span data-ttu-id="95bff-111">一方、データベースでタイムスタンプを使用する場合には、変更追跡用のカスタム ロジックは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="95bff-111">On the other hand, if the database has timestamps, then there is no need for custom change-tracking logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95bff-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="95bff-112">See Also</span></span>  
 [<span data-ttu-id="95bff-113">N 層でおよびリモート アプリケーション LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="95bff-113">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [<span data-ttu-id="95bff-114">LINQ to SQL N 層 Web サービスと</span><span class="sxs-lookup"><span data-stu-id="95bff-114">LINQ to SQL N-Tier with Web Services</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [<span data-ttu-id="95bff-115">n 層アプリケーションでのデータセットの操作</span><span class="sxs-lookup"><span data-stu-id="95bff-115">Work with datasets in n-tier applications</span></span>](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
