---
title: "オプティミスティック同時実行の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91684f1971692e83664fe41a0385a6d68b327237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="optimistic-concurrency-overview"></a><span data-ttu-id="31c3d-102">オプティミスティック同時実行の概要</span><span class="sxs-lookup"><span data-stu-id="31c3d-102">Optimistic Concurrency: Overview</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="31c3d-103"> はオプティミスティック同時実行制御をサポートします。</span><span class="sxs-lookup"><span data-stu-id="31c3d-103"> supports optimistic concurrency control.</span></span> <span data-ttu-id="31c3d-104">次の表でオプティミスティック同時実行制御を適用する条件[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="31c3d-104">The following table describes terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation:</span></span>  
  
|<span data-ttu-id="31c3d-105">用語</span><span class="sxs-lookup"><span data-stu-id="31c3d-105">Terms</span></span>|<span data-ttu-id="31c3d-106">説明</span><span class="sxs-lookup"><span data-stu-id="31c3d-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="31c3d-107">同時実行</span><span class="sxs-lookup"><span data-stu-id="31c3d-107">concurrency</span></span>|<span data-ttu-id="31c3d-108">2 人以上のユーザーがデータベースの同じ行を同時に更新しようとした状況のことです。</span><span class="sxs-lookup"><span data-stu-id="31c3d-108">The situation in which two or more users at the same time try to update the same database row.</span></span>|  
|<span data-ttu-id="31c3d-109">同時実行の競合</span><span class="sxs-lookup"><span data-stu-id="31c3d-109">concurrency conflict</span></span>|<span data-ttu-id="31c3d-110">2 人以上のユーザーが、行の中の 1 つまたは複数の列に対し、互いに競合する値を送信しようとした状況のことです。</span><span class="sxs-lookup"><span data-stu-id="31c3d-110">The situation in which two or more users at the same time try to submit conflicting values to one or more columns of a row.</span></span>|  
|<span data-ttu-id="31c3d-111">同時実行制御</span><span class="sxs-lookup"><span data-stu-id="31c3d-111">concurrency control</span></span>|<span data-ttu-id="31c3d-112">同時実行の競合を解決するために使用する手法のことです。</span><span class="sxs-lookup"><span data-stu-id="31c3d-112">The technique used to resolve concurrency conflicts.</span></span>|  
|<span data-ttu-id="31c3d-113">オプティミスティック同時実行制御</span><span class="sxs-lookup"><span data-stu-id="31c3d-113">optimistic concurrency control</span></span>|<span data-ttu-id="31c3d-114">他のトランザクションが行の値に変更を加えていないかどうかをまず調べたうえで変更の送信を許可する手法のことです。</span><span class="sxs-lookup"><span data-stu-id="31c3d-114">The technique that first investigates whether other transactions have changed values in a row before permitting changes to be submitted.</span></span><br /><br /> <span data-ttu-id="31c3d-115">比較して*ペシミスティック同時実行制御*、同時実行の競合を回避するレコードをロックします。</span><span class="sxs-lookup"><span data-stu-id="31c3d-115">Contrast with *pessimistic concurrency control*, which locks the record to avoid concurrency conflicts.</span></span><br /><br /> <span data-ttu-id="31c3d-116">*オプティミスティック*干渉別の可能性がありますいないを 1 つのトランザクションになる可能性と見なされるために、コントロールはこれと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="31c3d-116">*Optimistic* control is so termed because it considers the chances of one transaction interfering with another to be unlikely.</span></span>|  
|<span data-ttu-id="31c3d-117">競合の解決</span><span class="sxs-lookup"><span data-stu-id="31c3d-117">conflict resolution</span></span>|<span data-ttu-id="31c3d-118">データベースを再度クエリしてから相違点を調整することによって競合する項目を更新する処理のことです。</span><span class="sxs-lookup"><span data-stu-id="31c3d-118">The process of refreshing a conflicting item by querying the database again and then reconciling differences.</span></span><br /><br /> <span data-ttu-id="31c3d-119">オブジェクトを更新するときには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の変更トラッカーによって、以下のデータが記録されます。</span><span class="sxs-lookup"><span data-stu-id="31c3d-119">When an object is refreshed, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] change tracker holds the following data:</span></span><br /><br /> <span data-ttu-id="31c3d-120">最初に、データベースから取得および更新プログラムの使用-の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-120">-   The values originally taken from the database and used for the update check.</span></span><br /><span data-ttu-id="31c3d-121">-データベースから新しい値後続のクエリ。</span><span class="sxs-lookup"><span data-stu-id="31c3d-121">-   The new database values from the subsequent query.</span></span><br /><br /> <span data-ttu-id="31c3d-122">次に [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクトが競合しているかどうか (つまり 1 つまたは複数のメンバー値が変更されているかどうか) を判断します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-122">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] then determines whether the object is in conflict (that is, whether one or more of its member values has changed).</span></span> <span data-ttu-id="31c3d-123">オブジェクトが競合している場合[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]次に競合がどのメンバーを決定します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-123">If the object is in conflict, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] next determines which of its members are in conflict.</span></span><br /><br /> <span data-ttu-id="31c3d-124">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が見つけたメンバーの競合は、競合の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="31c3d-124">Any member conflict that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] discovers is added to a conflict list.</span></span>|  
  
 <span data-ttu-id="31c3d-125">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデル、*オプティミスティック同時実行の競合*の両方の次の条件に当てはまるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-125">In the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model, an *optimistic concurrency conflict* occurs when both of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="31c3d-126">クライアントがデータベースに変更を送信しようとした。</span><span class="sxs-lookup"><span data-stu-id="31c3d-126">The client tries to submit changes to the database.</span></span>  
  
-   <span data-ttu-id="31c3d-127">データベースで、そのクライアントによる最後の読み取り以降に、1 つまたは複数の更新チェック値が更新されている。</span><span class="sxs-lookup"><span data-stu-id="31c3d-127">One or more update-check values have been updated in the database since the client last read them.</span></span>  
  
 <span data-ttu-id="31c3d-128">この競合を解決するためには、オブジェクトのどのメンバーが競合しているかを判別し、どのように対処するかを決定することが必要です。</span><span class="sxs-lookup"><span data-stu-id="31c3d-128">Resolution of this conflict includes discovering which members of the object are in conflict, and then deciding what you want to do about it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31c3d-129">オプティミスティック同時実行のチェックに関与するのは、<xref:System.Data.Linq.Mapping.UpdateCheck.Always> または <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> として割り当てられているメンバーのみです。</span><span class="sxs-lookup"><span data-stu-id="31c3d-129">Only members mapped as <xref:System.Data.Linq.Mapping.UpdateCheck.Always> or <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> participate in optimistic concurrency checks.</span></span> <span data-ttu-id="31c3d-130"><xref:System.Data.Linq.Mapping.UpdateCheck.Never> と指定されているメンバーには、チェックは実行されません。</span><span class="sxs-lookup"><span data-stu-id="31c3d-130">No check is performed for members marked <xref:System.Data.Linq.Mapping.UpdateCheck.Never>.</span></span> <span data-ttu-id="31c3d-131">詳細については、「<xref:System.Data.Linq.Mapping.UpdateCheck>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31c3d-131">For more information, see <xref:System.Data.Linq.Mapping.UpdateCheck>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31c3d-132">例</span><span class="sxs-lookup"><span data-stu-id="31c3d-132">Example</span></span>  
 <span data-ttu-id="31c3d-133">次のシナリオは、ユーザー 1 が、更新の手始めとして、データベースの行をクエリした状況です。</span><span class="sxs-lookup"><span data-stu-id="31c3d-133">For example, in the following scenario, User1 starts to prepare an update by querying the database for a row.</span></span> <span data-ttu-id="31c3d-134">ユーザー 1 が取得した行には、Alfreds、Maria、および Sales という値が入っています。</span><span class="sxs-lookup"><span data-stu-id="31c3d-134">User1 receives a row with values of Alfreds, Maria, and Sales.</span></span>  
  
 <span data-ttu-id="31c3d-135">ユーザー 1 は、Manager 列の値を Alfred に、また Department 列の値を Marketing に、それぞれ変更しようと考えています。</span><span class="sxs-lookup"><span data-stu-id="31c3d-135">User1 wants to change the value of the Manager column to Alfred and the value of the Department column to Marketing.</span></span> <span data-ttu-id="31c3d-136">しかし、ユーザー 1 がその変更を発行する前に、ユーザー 2 がデータベースに変更を送信しました。</span><span class="sxs-lookup"><span data-stu-id="31c3d-136">Before User1 can submit those changes, User2 has submitted changes to the database.</span></span> <span data-ttu-id="31c3d-137">その結果、Assistant 列の値は Mary に、また Department 列の値は Service に、それぞれ変更されました。</span><span class="sxs-lookup"><span data-stu-id="31c3d-137">So now the value of the Assistant column has been changed to Mary and the value of the Department column to Service.</span></span>  
  
 <span data-ttu-id="31c3d-138">ここで、ユーザー 1 が変更を送信しようとすると、送信は失敗し、<xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="31c3d-138">When User1 now tries to submit changes, the submission fails and a <xref:System.Data.Linq.ChangeConflictException> exception is thrown.</span></span> <span data-ttu-id="31c3d-139">このような結果になるのは、データベースの Assistant 列と Department 列の値が、予期した値と異なるためです。</span><span class="sxs-lookup"><span data-stu-id="31c3d-139">This result occurs because the database values for the Assistant column and the Department column are not those that were expected.</span></span> <span data-ttu-id="31c3d-140">Assistant 列と Department 列を表すメンバーが競合しています。</span><span class="sxs-lookup"><span data-stu-id="31c3d-140">Members representing the Assistant and Department columns are in conflict.</span></span> <span data-ttu-id="31c3d-141">この状況をまとめると次の表のようになります。</span><span class="sxs-lookup"><span data-stu-id="31c3d-141">The following table summarizes the situation.</span></span>  
  
||<span data-ttu-id="31c3d-142">Manager</span><span class="sxs-lookup"><span data-stu-id="31c3d-142">Manager</span></span>|<span data-ttu-id="31c3d-143">Assistant</span><span class="sxs-lookup"><span data-stu-id="31c3d-143">Assistant</span></span>|<span data-ttu-id="31c3d-144">Department</span><span class="sxs-lookup"><span data-stu-id="31c3d-144">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="31c3d-145">元の状態</span><span class="sxs-lookup"><span data-stu-id="31c3d-145">Original state</span></span>|<span data-ttu-id="31c3d-146">Alfreds</span><span class="sxs-lookup"><span data-stu-id="31c3d-146">Alfreds</span></span>|<span data-ttu-id="31c3d-147">Maria</span><span class="sxs-lookup"><span data-stu-id="31c3d-147">Maria</span></span>|<span data-ttu-id="31c3d-148">Sales</span><span class="sxs-lookup"><span data-stu-id="31c3d-148">Sales</span></span>|  
|<span data-ttu-id="31c3d-149">ユーザー 1</span><span class="sxs-lookup"><span data-stu-id="31c3d-149">User1</span></span>|<span data-ttu-id="31c3d-150">Alfred</span><span class="sxs-lookup"><span data-stu-id="31c3d-150">Alfred</span></span>||<span data-ttu-id="31c3d-151">Marketing</span><span class="sxs-lookup"><span data-stu-id="31c3d-151">Marketing</span></span>|  
|<span data-ttu-id="31c3d-152">ユーザー 2</span><span class="sxs-lookup"><span data-stu-id="31c3d-152">User2</span></span>||<span data-ttu-id="31c3d-153">Mary</span><span class="sxs-lookup"><span data-stu-id="31c3d-153">Mary</span></span>|<span data-ttu-id="31c3d-154">サービス</span><span class="sxs-lookup"><span data-stu-id="31c3d-154">Service</span></span>|  
  
 <span data-ttu-id="31c3d-155">このような競合は、いくつかの方法で解決できます。</span><span class="sxs-lookup"><span data-stu-id="31c3d-155">You can resolve conflicts such as this in different ways.</span></span> <span data-ttu-id="31c3d-156">詳細については、次を参照してください。[する方法: 変更の競合を管理](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)です。</span><span class="sxs-lookup"><span data-stu-id="31c3d-156">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="conflict-detection-and-resolution-checklist"></a><span data-ttu-id="31c3d-157">競合の検出と解決のチェック リスト</span><span class="sxs-lookup"><span data-stu-id="31c3d-157">Conflict Detection and Resolution Checklist</span></span>  
 <span data-ttu-id="31c3d-158">競合の検出と解決は、さまざまな詳細レベルで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="31c3d-158">You can detect and resolve conflicts at any level of detail.</span></span> <span data-ttu-id="31c3d-159">極端な方法としては、すべての競合を 3 つの方法 (<xref:System.Data.Linq.RefreshMode> を参照) のいずれかで 1 つで解決し、それ以外の考慮を一切加えないという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="31c3d-159">At one extreme, you can resolve all conflicts in one of three ways (see <xref:System.Data.Linq.RefreshMode>) without additional consideration.</span></span> <span data-ttu-id="31c3d-160">正反対の方法としては、競合している各メンバーについて、それぞれの競合の種類ごとに、特定の処理を指定するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="31c3d-160">At the other extreme, you can designate a specific action for each type of conflict on every member in conflict.</span></span>  
  
-   <span data-ttu-id="31c3d-161">オブジェクト モデルの <xref:System.Data.Linq.Mapping.UpdateCheck> オプションを指定または変更します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-161">Specify or revise <xref:System.Data.Linq.Mapping.UpdateCheck> options in your object model.</span></span>  
  
     <span data-ttu-id="31c3d-162">詳細については、次を参照してください。[する方法: 同時実行の競合があるテストを指定するメンバー](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)です。</span><span class="sxs-lookup"><span data-stu-id="31c3d-162">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
-   <span data-ttu-id="31c3d-163"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> の呼び出しの try/catch ブロックで、例外がどの時点でスローされるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-163">In the try/catch block of your call to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, specify at what point you want exceptions to be thrown.</span></span>  
  
     <span data-ttu-id="31c3d-164">詳細については、次を参照してください。[する方法: 指定のときに同時実行例外がスローされた](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)です。</span><span class="sxs-lookup"><span data-stu-id="31c3d-164">For more information, see [How to: Specify When Concurrency Exceptions are Thrown](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
-   <span data-ttu-id="31c3d-165">取得する競合の詳細さを判断し、それに応じたコードを try/catch ブロックに記述します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-165">Determine how much conflict detail you want to retrieve, and include code in your try/catch block accordingly.</span></span>  
  
     <span data-ttu-id="31c3d-166">詳細については、次を参照してください。[する方法: エンティティの競合情報の取得](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)と[する方法: メンバーの競合情報の取得](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)です。</span><span class="sxs-lookup"><span data-stu-id="31c3d-166">For more information, see [How to: Retrieve Entity Conflict Information](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) and [How to: Retrieve Member Conflict Information](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).</span></span>  
  
-   <span data-ttu-id="31c3d-167">含める、 `try` / `catch`を探索するさまざまな競合を解決する方法のコードします。</span><span class="sxs-lookup"><span data-stu-id="31c3d-167">Include in your `try`/`catch` code how you want to resolve the various conflicts you discover.</span></span>  
  
     <span data-ttu-id="31c3d-168">詳細については、次を参照してください[する方法: データベースの値を保持して競合の解決](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)、[する方法: データベースの値を上書きして競合の解決](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)、および[する方法: マージ競合を解決するには。データベースの値を持つ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-168">For more information, see [How to: Resolve Conflicts by Retaining Database Values](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [How to: Resolve Conflicts by Overwriting Database Values](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), and [How to: Resolve Conflicts by Merging with Database Values](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).</span></span>  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a><span data-ttu-id="31c3d-169">競合の発見と解決をサポートする LINQ to SQL の型</span><span class="sxs-lookup"><span data-stu-id="31c3d-169">LINQ to SQL Types That Support Conflict Discovery and Resolution</span></span>  
 <span data-ttu-id="31c3d-170">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で、オプティミスティック同時実行の競合の解決をサポートするクラスと機能を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="31c3d-170">Classes and features to support the resolution of conflicts in optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] include the following:</span></span>  
  
-   <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="31c3d-171">参照</span><span class="sxs-lookup"><span data-stu-id="31c3d-171">See Also</span></span>  
 [<span data-ttu-id="31c3d-172">方法 : 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="31c3d-172">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
