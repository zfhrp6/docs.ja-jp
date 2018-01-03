---
title: "方法 : データベース値を上書きすることで競合を解決する"
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
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f3155eca2344e32913aaacbd0e2671603824aaf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="7b3b1-102">方法 : データベース値を上書きすることで競合を解決する</span><span class="sxs-lookup"><span data-stu-id="7b3b1-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="7b3b1-103">変更を再送信する前に、データベース内の予期した値と実際の値の違いを調整するために、<xref:System.Data.Linq.RefreshMode.KeepCurrentValues> を使用してデータベース内の値を上書きできます。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="7b3b1-104">詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b3b1-105">どの場合も、データベースから最新のデータを取得することで、まずクライアントのレコードが更新されます。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="7b3b1-106">この処理によって、次の更新処理が同じ同時実行チェックで失敗することを防止できます。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b3b1-107">例</span><span class="sxs-lookup"><span data-stu-id="7b3b1-107">Example</span></span>  
 <span data-ttu-id="7b3b1-108">このシナリオでは、ユーザー 1 が変更を送信しようとしたときに <xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。これは、途中でユーザー 2 が Assistant 列と Department 列を変更していたためです。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="7b3b1-109">次の表は、この状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="7b3b1-110">Manager</span><span class="sxs-lookup"><span data-stu-id="7b3b1-110">Manager</span></span>|<span data-ttu-id="7b3b1-111">Assistant</span><span class="sxs-lookup"><span data-stu-id="7b3b1-111">Assistant</span></span>|<span data-ttu-id="7b3b1-112">Department</span><span class="sxs-lookup"><span data-stu-id="7b3b1-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="7b3b1-113">ユーザー 1 およびユーザー 2 が照会した最初のデータベース状態</span><span class="sxs-lookup"><span data-stu-id="7b3b1-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="7b3b1-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="7b3b1-114">Alfreds</span></span>|<span data-ttu-id="7b3b1-115">Maria</span><span class="sxs-lookup"><span data-stu-id="7b3b1-115">Maria</span></span>|<span data-ttu-id="7b3b1-116">Sales</span><span class="sxs-lookup"><span data-stu-id="7b3b1-116">Sales</span></span>|  
|<span data-ttu-id="7b3b1-117">ユーザー 1 が送信しようとした変更内容</span><span class="sxs-lookup"><span data-stu-id="7b3b1-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="7b3b1-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="7b3b1-118">Alfred</span></span>||<span data-ttu-id="7b3b1-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="7b3b1-119">Marketing</span></span>|  
|<span data-ttu-id="7b3b1-120">ユーザー 2 が既に送信した変更内容</span><span class="sxs-lookup"><span data-stu-id="7b3b1-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="7b3b1-121">Mary</span><span class="sxs-lookup"><span data-stu-id="7b3b1-121">Mary</span></span>|<span data-ttu-id="7b3b1-122">サービス</span><span class="sxs-lookup"><span data-stu-id="7b3b1-122">Service</span></span>|  
  
 <span data-ttu-id="7b3b1-123">ユーザー 1 は、この競合を解決するために、データベース値を現在のクライアント メンバー値で上書きすることに決めます。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="7b3b1-124">ユーザー 1 が <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> を使用して競合を解決すると、データベース内の結果は次の表のようになります。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="7b3b1-125">Manager</span><span class="sxs-lookup"><span data-stu-id="7b3b1-125">Manager</span></span>|<span data-ttu-id="7b3b1-126">Assistant</span><span class="sxs-lookup"><span data-stu-id="7b3b1-126">Assistant</span></span>|<span data-ttu-id="7b3b1-127">Department</span><span class="sxs-lookup"><span data-stu-id="7b3b1-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="7b3b1-128">競合解決後の新しい状態</span><span class="sxs-lookup"><span data-stu-id="7b3b1-128">New state after conflict resolution.</span></span>|<span data-ttu-id="7b3b1-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="7b3b1-129">Alfred</span></span><br /><br /> <span data-ttu-id="7b3b1-130">(ユーザー 1 の値)</span><span class="sxs-lookup"><span data-stu-id="7b3b1-130">(from User1)</span></span>|<span data-ttu-id="7b3b1-131">Maria</span><span class="sxs-lookup"><span data-stu-id="7b3b1-131">Maria</span></span><br /><br /> <span data-ttu-id="7b3b1-132">(元の値)</span><span class="sxs-lookup"><span data-stu-id="7b3b1-132">(original)</span></span>|<span data-ttu-id="7b3b1-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="7b3b1-133">Marketing</span></span><br /><br /> <span data-ttu-id="7b3b1-134">(ユーザー 1 の値)</span><span class="sxs-lookup"><span data-stu-id="7b3b1-134">(from User1)</span></span>|  
  
 <span data-ttu-id="7b3b1-135">次のコード例は、データベース値を現在のクライアント メンバー値で上書きする方法を示しています </span><span class="sxs-lookup"><span data-stu-id="7b3b1-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="7b3b1-136">(個々のメンバーの競合に対する検査やカスタム ハンドリングは行われません)。</span><span class="sxs-lookup"><span data-stu-id="7b3b1-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7b3b1-137">参照</span><span class="sxs-lookup"><span data-stu-id="7b3b1-137">See Also</span></span>  
 [<span data-ttu-id="7b3b1-138">方法 : 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="7b3b1-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
