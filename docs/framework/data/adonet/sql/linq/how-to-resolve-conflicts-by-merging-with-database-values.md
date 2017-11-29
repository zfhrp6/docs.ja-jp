---
title: "方法 : データベース値とマージすることで競合を解決する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8e5114052951950c5866d80c974555678b1d040a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="8d43a-102">方法 : データベース値とマージすることで競合を解決する</span><span class="sxs-lookup"><span data-stu-id="8d43a-102">How to: Resolve Conflicts by Merging with Database Values</span></span>
<span data-ttu-id="8d43a-103">変更内容を再送信する前に、データベース内の予期した値と実際の値の違いを調整するために、<xref:System.Data.Linq.RefreshMode.KeepChanges> を使用して、データベース内の値を現在のクライアント メンバー値とマージできます。</span><span class="sxs-lookup"><span data-stu-id="8d43a-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="8d43a-104">詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="8d43a-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d43a-105">どの場合も、データベースから最新のデータを取得することで、まずクライアントのレコードが更新されます。</span><span class="sxs-lookup"><span data-stu-id="8d43a-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="8d43a-106">この処理によって、次の更新処理が同じ同時実行チェックで失敗することを防止できます。</span><span class="sxs-lookup"><span data-stu-id="8d43a-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d43a-107">例</span><span class="sxs-lookup"><span data-stu-id="8d43a-107">Example</span></span>  
 <span data-ttu-id="8d43a-108">このシナリオでは、ユーザー 1 が変更内容を送信しようとしたときに <xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。途中でユーザー 2 が Assistant 列と Department  列を変更したためです。</span><span class="sxs-lookup"><span data-stu-id="8d43a-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="8d43a-109">次の表は、この状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d43a-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="8d43a-110">Manager</span><span class="sxs-lookup"><span data-stu-id="8d43a-110">Manager</span></span>|<span data-ttu-id="8d43a-111">Assistant</span><span class="sxs-lookup"><span data-stu-id="8d43a-111">Assistant</span></span>|<span data-ttu-id="8d43a-112">Department</span><span class="sxs-lookup"><span data-stu-id="8d43a-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="8d43a-113">ユーザー 1 およびユーザー 2 が照会した最初のデータベース状態</span><span class="sxs-lookup"><span data-stu-id="8d43a-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="8d43a-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="8d43a-114">Alfreds</span></span>|<span data-ttu-id="8d43a-115">Maria</span><span class="sxs-lookup"><span data-stu-id="8d43a-115">Maria</span></span>|<span data-ttu-id="8d43a-116">Sales</span><span class="sxs-lookup"><span data-stu-id="8d43a-116">Sales</span></span>|  
|<span data-ttu-id="8d43a-117">ユーザー 1 が送信しようとした変更内容</span><span class="sxs-lookup"><span data-stu-id="8d43a-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="8d43a-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="8d43a-118">Alfred</span></span>||<span data-ttu-id="8d43a-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="8d43a-119">Marketing</span></span>|  
|<span data-ttu-id="8d43a-120">ユーザー 2 が既に送信した変更内容</span><span class="sxs-lookup"><span data-stu-id="8d43a-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="8d43a-121">Mary</span><span class="sxs-lookup"><span data-stu-id="8d43a-121">Mary</span></span>|<span data-ttu-id="8d43a-122">サービス</span><span class="sxs-lookup"><span data-stu-id="8d43a-122">Service</span></span>|  
  
 <span data-ttu-id="8d43a-123">ユーザー 1 は、この競合を解決するために、データベース値を現在のクライアント メンバー値にマージすることに決めます。</span><span class="sxs-lookup"><span data-stu-id="8d43a-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="8d43a-124">その結果、現在の変更セットでも値が変更されているデータベース値のみが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="8d43a-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="8d43a-125">ユーザー 1 が <xref:System.Data.Linq.RefreshMode.KeepChanges> を使用して競合を解決すると、データベース内の結果は次の表のようになります。</span><span class="sxs-lookup"><span data-stu-id="8d43a-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="8d43a-126">Manager</span><span class="sxs-lookup"><span data-stu-id="8d43a-126">Manager</span></span>|<span data-ttu-id="8d43a-127">Assistant</span><span class="sxs-lookup"><span data-stu-id="8d43a-127">Assistant</span></span>|<span data-ttu-id="8d43a-128">Department</span><span class="sxs-lookup"><span data-stu-id="8d43a-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="8d43a-129">競合解決後の新しい状態</span><span class="sxs-lookup"><span data-stu-id="8d43a-129">New state after conflict resolution.</span></span>|<span data-ttu-id="8d43a-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="8d43a-130">Alfred</span></span><br /><br /> <span data-ttu-id="8d43a-131">(ユーザー 1 の値)</span><span class="sxs-lookup"><span data-stu-id="8d43a-131">(from User1)</span></span>|<span data-ttu-id="8d43a-132">Mary</span><span class="sxs-lookup"><span data-stu-id="8d43a-132">Mary</span></span><br /><br /> <span data-ttu-id="8d43a-133">(ユーザー 2 の値)</span><span class="sxs-lookup"><span data-stu-id="8d43a-133">(from User2)</span></span>|<span data-ttu-id="8d43a-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="8d43a-134">Marketing</span></span><br /><br /> <span data-ttu-id="8d43a-135">(ユーザー 1 の値)</span><span class="sxs-lookup"><span data-stu-id="8d43a-135">(from User1)</span></span>|  
  
 <span data-ttu-id="8d43a-136">次の例では、クライアントでも値が変更されている場合を除き、データベース値を現在のクライアント メンバー値にマージする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d43a-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="8d43a-137">個別のメンバーの競合に対する検査やカスタム ハンドリングは発生しません。</span><span class="sxs-lookup"><span data-stu-id="8d43a-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8d43a-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d43a-138">See Also</span></span>  
 [<span data-ttu-id="8d43a-139">方法: データベースの値を上書きすることによって競合を解決するには</span><span class="sxs-lookup"><span data-stu-id="8d43a-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [<span data-ttu-id="8d43a-140">方法: データベース値を保持して競合を解決するには</span><span class="sxs-lookup"><span data-stu-id="8d43a-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [<span data-ttu-id="8d43a-141">方法: 変更の競合の管理</span><span class="sxs-lookup"><span data-stu-id="8d43a-141">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
