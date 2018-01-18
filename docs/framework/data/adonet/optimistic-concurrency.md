---
title: "オプティミスティック同時実行制御"
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
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4cc1ac0446f13bcc6bc1c8262eae5716302c3e2d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="d3357-102">オプティミスティック同時実行制御</span><span class="sxs-lookup"><span data-stu-id="d3357-102">Optimistic Concurrency</span></span>
<span data-ttu-id="d3357-103">マルチユーザー環境には、データベースのデータを更新するための 2 つのモデルがあります。オプティミスティック同時実行制御とペシミスティック同時実行制御です。</span><span class="sxs-lookup"><span data-stu-id="d3357-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="d3357-104"><xref:System.Data.DataSet> オブジェクトは、データをリモート処理するときや、データと対話するときのように長時間にわたる利用状況では、オプティミスティック同時実行制御の使用を奨励するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d3357-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="d3357-105">ペシミスティック同時実行制御では、他のユーザーが現在のユーザーに影響を与えるようなデータ変更を実行するのを防ぐために、データ ソースで行をロックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3357-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="d3357-106">ペシミスティック モデルでは、あるユーザーがロックの適用される操作を実行すると、他のユーザーは、ロックが解除されるまで、競合する操作を実行できません。</span><span class="sxs-lookup"><span data-stu-id="d3357-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="d3357-107">このモデルは、同時実行の競合が発生するときに、トランザクションをロールバックするよりもデータをロックで保護する方が低コストに抑えられるため、データの競合が多い環境で主に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3357-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="d3357-108">したがって、ペシミスティック同時実行制御モデルでは、行を更新するユーザーがロックを設定します。</span><span class="sxs-lookup"><span data-stu-id="d3357-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="d3357-109">更新を終了してロックを解除するまでは、他のユーザーはその行を変更できません。</span><span class="sxs-lookup"><span data-stu-id="d3357-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="d3357-110">そのため、ペシミスティック同時実行制御は、レコードをプログラムで処理する場合のようにロック時間が短いときの実装に適しています。</span><span class="sxs-lookup"><span data-stu-id="d3357-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="d3357-111">ペシミスティック同時実行制御は、ユーザーがデータと対話していてレコードが比較的長時間ロックされる場合には適していません。</span><span class="sxs-lookup"><span data-stu-id="d3357-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3357-112">同じ操作で複数の行を更新する必要がある場合は、ペシミスティック同時実行制御でロックするよりも、トランザクションを作成する方が有効です。</span><span class="sxs-lookup"><span data-stu-id="d3357-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="d3357-113">これに対して、オプティミスティック同時実行制御を使用するユーザーは、行を読み取るときに行をロックしません。</span><span class="sxs-lookup"><span data-stu-id="d3357-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="d3357-114">ユーザーが行を更新するときは、行の読み取り後に別のユーザーがその行を変更したかどうかをアプリケーションで確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3357-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="d3357-115">オプティミスティック同時実行制御は、一般に、データの競合が少ない環境で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3357-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="d3357-116">オプティミスティック同時実行制御を使用すると、レコードをロックする必要がないためパフォーマンスが向上します。レコードをロックするには、サーバー リソースを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3357-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="d3357-117">また、レコードのロックを管理するためにデータベース サーバーに永続的に接続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3357-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="d3357-118">オプティミスティック同時実行制御モデルでは、サーバーとの接続が固定していないため、より短い時間で多数のクライアントを扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="d3357-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="d3357-119">オプティミスティック同時実行制御モデルでは、ユーザーがデータベースから値を受け取った後、その値を変更する前に別のユーザーがその値を変更した場合に、違反が発生したと見なされます。</span><span class="sxs-lookup"><span data-stu-id="d3357-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="d3357-120">サーバーが同時実行制御違反を解決する方法がよくわかる例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d3357-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="d3357-121">オプティミスティック同時実行制御の例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d3357-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="d3357-122">午後 1 時に、User1 が、次の値を持つデータベースから行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d3357-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="d3357-123">**CustID     LastName     FirstName**</span><span class="sxs-lookup"><span data-stu-id="d3357-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="d3357-124">101          Smith             Bob</span><span class="sxs-lookup"><span data-stu-id="d3357-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="d3357-125">列名</span><span class="sxs-lookup"><span data-stu-id="d3357-125">Column name</span></span>|<span data-ttu-id="d3357-126">元の値</span><span class="sxs-lookup"><span data-stu-id="d3357-126">Original value</span></span>|<span data-ttu-id="d3357-127">現在の値</span><span class="sxs-lookup"><span data-stu-id="d3357-127">Current value</span></span>|<span data-ttu-id="d3357-128">データベース内の値</span><span class="sxs-lookup"><span data-stu-id="d3357-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d3357-129">CustID</span><span class="sxs-lookup"><span data-stu-id="d3357-129">CustID</span></span>|<span data-ttu-id="d3357-130">101</span><span class="sxs-lookup"><span data-stu-id="d3357-130">101</span></span>|<span data-ttu-id="d3357-131">101</span><span class="sxs-lookup"><span data-stu-id="d3357-131">101</span></span>|<span data-ttu-id="d3357-132">101</span><span class="sxs-lookup"><span data-stu-id="d3357-132">101</span></span>|  
|<span data-ttu-id="d3357-133">LastName</span><span class="sxs-lookup"><span data-stu-id="d3357-133">LastName</span></span>|<span data-ttu-id="d3357-134">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-134">Smith</span></span>|<span data-ttu-id="d3357-135">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-135">Smith</span></span>|<span data-ttu-id="d3357-136">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-136">Smith</span></span>|  
|<span data-ttu-id="d3357-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="d3357-137">FirstName</span></span>|<span data-ttu-id="d3357-138">Bob</span><span class="sxs-lookup"><span data-stu-id="d3357-138">Bob</span></span>|<span data-ttu-id="d3357-139">Bob</span><span class="sxs-lookup"><span data-stu-id="d3357-139">Bob</span></span>|<span data-ttu-id="d3357-140">Bob</span><span class="sxs-lookup"><span data-stu-id="d3357-140">Bob</span></span>|  
  
 <span data-ttu-id="d3357-141">午後 1 時 1 分に、User2 が同じ行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d3357-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="d3357-142">User2 が変更午後 1時 03分**FirstName** "Robert"に"Bob"から、データベースを更新します。</span><span class="sxs-lookup"><span data-stu-id="d3357-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="d3357-143">列名</span><span class="sxs-lookup"><span data-stu-id="d3357-143">Column name</span></span>|<span data-ttu-id="d3357-144">元の値</span><span class="sxs-lookup"><span data-stu-id="d3357-144">Original value</span></span>|<span data-ttu-id="d3357-145">現在の値</span><span class="sxs-lookup"><span data-stu-id="d3357-145">Current value</span></span>|<span data-ttu-id="d3357-146">データベース内の値</span><span class="sxs-lookup"><span data-stu-id="d3357-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d3357-147">CustID</span><span class="sxs-lookup"><span data-stu-id="d3357-147">CustID</span></span>|<span data-ttu-id="d3357-148">101</span><span class="sxs-lookup"><span data-stu-id="d3357-148">101</span></span>|<span data-ttu-id="d3357-149">101</span><span class="sxs-lookup"><span data-stu-id="d3357-149">101</span></span>|<span data-ttu-id="d3357-150">101</span><span class="sxs-lookup"><span data-stu-id="d3357-150">101</span></span>|  
|<span data-ttu-id="d3357-151">LastName</span><span class="sxs-lookup"><span data-stu-id="d3357-151">LastName</span></span>|<span data-ttu-id="d3357-152">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-152">Smith</span></span>|<span data-ttu-id="d3357-153">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-153">Smith</span></span>|<span data-ttu-id="d3357-154">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-154">Smith</span></span>|  
|<span data-ttu-id="d3357-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="d3357-155">FirstName</span></span>|<span data-ttu-id="d3357-156">Bob</span><span class="sxs-lookup"><span data-stu-id="d3357-156">Bob</span></span>|<span data-ttu-id="d3357-157">Robert</span><span class="sxs-lookup"><span data-stu-id="d3357-157">Robert</span></span>|<span data-ttu-id="d3357-158">Bob</span><span class="sxs-lookup"><span data-stu-id="d3357-158">Bob</span></span>|  
  
 <span data-ttu-id="d3357-159">更新時のデータベース内の値は User2 が持つ元の値と一致しているため、更新は成功します。</span><span class="sxs-lookup"><span data-stu-id="d3357-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="d3357-160">午後 1 時 5 分に、User1 が "Bob" の名を "James" に変更し、行の更新を試みます。</span><span class="sxs-lookup"><span data-stu-id="d3357-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="d3357-161">列名</span><span class="sxs-lookup"><span data-stu-id="d3357-161">Column name</span></span>|<span data-ttu-id="d3357-162">元の値</span><span class="sxs-lookup"><span data-stu-id="d3357-162">Original value</span></span>|<span data-ttu-id="d3357-163">現在の値</span><span class="sxs-lookup"><span data-stu-id="d3357-163">Current value</span></span>|<span data-ttu-id="d3357-164">データベース内の値</span><span class="sxs-lookup"><span data-stu-id="d3357-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d3357-165">CustID</span><span class="sxs-lookup"><span data-stu-id="d3357-165">CustID</span></span>|<span data-ttu-id="d3357-166">101</span><span class="sxs-lookup"><span data-stu-id="d3357-166">101</span></span>|<span data-ttu-id="d3357-167">101</span><span class="sxs-lookup"><span data-stu-id="d3357-167">101</span></span>|<span data-ttu-id="d3357-168">101</span><span class="sxs-lookup"><span data-stu-id="d3357-168">101</span></span>|  
|<span data-ttu-id="d3357-169">LastName</span><span class="sxs-lookup"><span data-stu-id="d3357-169">LastName</span></span>|<span data-ttu-id="d3357-170">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-170">Smith</span></span>|<span data-ttu-id="d3357-171">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-171">Smith</span></span>|<span data-ttu-id="d3357-172">Smith</span><span class="sxs-lookup"><span data-stu-id="d3357-172">Smith</span></span>|  
|<span data-ttu-id="d3357-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="d3357-173">FirstName</span></span>|<span data-ttu-id="d3357-174">Bob</span><span class="sxs-lookup"><span data-stu-id="d3357-174">Bob</span></span>|<span data-ttu-id="d3357-175">James</span><span class="sxs-lookup"><span data-stu-id="d3357-175">James</span></span>|<span data-ttu-id="d3357-176">Robert</span><span class="sxs-lookup"><span data-stu-id="d3357-176">Robert</span></span>|  
  
 <span data-ttu-id="d3357-177">この時点で、データベース内の値 ("Robert") は User1 が期待していた元の値 ("Bob") と一致していないため、User1 による更新はオプティミスティック同時実行制御違反となります。</span><span class="sxs-lookup"><span data-stu-id="d3357-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="d3357-178">同時実行制御違反は、更新が失敗したことを通知するだけです。</span><span class="sxs-lookup"><span data-stu-id="d3357-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="d3357-179">ここで、User2 による変更を User1 による変更で上書きするか、または User1 による変更をキャンセルするかの決定が必要になります。</span><span class="sxs-lookup"><span data-stu-id="d3357-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="d3357-180">オプティミスティック同時実行制御違反テスト</span><span class="sxs-lookup"><span data-stu-id="d3357-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="d3357-181">オプティミスティック同時実行制御違反をテストするには、いくつか方法があります。</span><span class="sxs-lookup"><span data-stu-id="d3357-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="d3357-182">1 つは、テーブルにタイムスタンプ列を含める方法です。</span><span class="sxs-lookup"><span data-stu-id="d3357-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="d3357-183">一般に、データベースには、レコードを最後に更新した日付と時刻を識別するために使用するタイムスタンプ機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d3357-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="d3357-184">この機能を使用すると、timestamp 列がテーブル定義に組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d3357-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="d3357-185">レコードが更新されると、タイムスタンプが更新されて現在の日付と時刻が反映されます。</span><span class="sxs-lookup"><span data-stu-id="d3357-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="d3357-186">オプティミスティック同時実行制御違反テストでは、テーブル内容についてのクエリによって timestamp 列が返されます。</span><span class="sxs-lookup"><span data-stu-id="d3357-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="d3357-187">更新しようとすると、データベースのタイムスタンプ値と、変更行に格納されている元のタイムスタンプ値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="d3357-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="d3357-188">一致した場合、更新が実行され、timestamp 列が現在の時刻に更新されてその更新が反映されます。</span><span class="sxs-lookup"><span data-stu-id="d3357-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="d3357-189">一致しなかった場合は、オプティミスティック同時実行制御違反が発生します。</span><span class="sxs-lookup"><span data-stu-id="d3357-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="d3357-190">オプティミスティック同時実行制御違反をテストするためのもう 1 つの方法は、行のすべての列の元の値が、データベース内の値とまだ一致しているかどうかを検証することです。</span><span class="sxs-lookup"><span data-stu-id="d3357-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="d3357-191">たとえば、次のクエリを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="d3357-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="d3357-192">内の行を更新するときに、オプティミスティック同時実行制御違反をテストする**Table1**、次の UPDATE ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d3357-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="d3357-193">元の値がデータベース内の値と一致する間は、更新が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d3357-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="d3357-194">値が変更された場合は、WHERE 句の条件と一致する行を見つけることができないため更新できません。</span><span class="sxs-lookup"><span data-stu-id="d3357-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="d3357-195">クエリで、常に一意の主キー値を返すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d3357-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="d3357-196">一意の主キーを返さないと、UPDATE ステートメントによって複数の行が更新されることがあり、意図に反した結果となります。</span><span class="sxs-lookup"><span data-stu-id="d3357-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="d3357-197">データ ソースの列で null が使用できる場合は、ローカル テーブルおよびデータ ソースで一致する null 参照がないかどうかをチェックするように WHERE 句を拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3357-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="d3357-198">たとえば、次の UPDATE ステートメントは、ローカル行の null 参照がデータ ソースの null 参照とまだ一致しているかどうか、つまり、ローカル行の値がデータ ソースの値とまだ一致しているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="d3357-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="d3357-199">オプティミスティック同時実行制御モデルを使用するときは、より制限の少ない抽出条件を適用するように選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3357-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="d3357-200">たとえば、WHERE 句で主キー列だけを使用すると、前回のクエリ実行後に主キー以外の列が更新されたかどうかに関係なく、データが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="d3357-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="d3357-201">WHERE 句を特定の列だけに適用することもできます。特定の列だけに WHERE 句を適用した場合は、特定のフィールドが前回のクエリ実行後に更新されていない限りデータが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="d3357-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="d3357-202">DataAdapter.RowUpdated イベント</span><span class="sxs-lookup"><span data-stu-id="d3357-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="d3357-203">**RowUpdated**のイベント、<xref:System.Data.Common.DataAdapter>オブジェクトは、オプティミスティック同時実行制御違反のアプリケーションに通知を提供する前に説明した手法と組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3357-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="d3357-204">**RowUpdated**を更新するには、各再試行の後に発生する**Modified**から行、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="d3357-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="d3357-205">これにより、例外発生時の処理、カスタム エラー情報の追加、再試行ロジックの追加などの特別の処理コードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d3357-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="d3357-206"><xref:System.Data.Common.RowUpdatedEventArgs>オブジェクトを返します、 **RecordsAffected**テーブルで変更された各行の特定の更新コマンドによって影響を受ける行の数を表すプロパティ。</span><span class="sxs-lookup"><span data-stu-id="d3357-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="d3357-207">オプティミスティック同時実行性をテストする update コマンドを設定して、 **RecordsAffected**プロパティは、その結果の値を返す 0、オプティミスティック同時実行制御違反が発生したときにレコードが更新されないためです。</span><span class="sxs-lookup"><span data-stu-id="d3357-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="d3357-208">この場合、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d3357-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="d3357-209">**RowUpdated**イベントを使用すると、このアイテムのみを処理し、適切な設定では、例外を回避**RowUpdatedEventArgs.Status**などの値**UpdateStatus.SkipCurrentRow**です。</span><span class="sxs-lookup"><span data-stu-id="d3357-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="d3357-210">詳細については、 **RowUpdated**イベントを参照してください[DataAdapter イベントの処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3357-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="d3357-211">必要に応じて、設定することができます**DataAdapter.ContinueUpdateOnError**に**true**、呼び出す前に**更新**、および、に格納されているエラー情報への応答**RowError**行の場合に、特定のプロパティ、**更新**が完了します。</span><span class="sxs-lookup"><span data-stu-id="d3357-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="d3357-212">詳細については、次を参照してください。[行エラー情報](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3357-212">For more information, see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="d3357-213">オプティミスティック同時実行制御の例</span><span class="sxs-lookup"><span data-stu-id="d3357-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="d3357-214">設定する単純な例を次に示します、 **UpdateCommand**の**DataAdapter**オプティミスティック同時実行性をテストするしを使用して、 **RowUpdated**テストするためのイベントオプティミスティック同時実行制御違反。</span><span class="sxs-lookup"><span data-stu-id="d3357-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="d3357-215">アプリケーションは、設定、オプティミスティック同時実行制御違反が発生したときに、 **RowError**オプティミスティック同時実行制御違反を反映するように、更新が実行される行のです。</span><span class="sxs-lookup"><span data-stu-id="d3357-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="d3357-216">更新コマンドの WHERE 句に渡されるパラメーター値にマップされる注、**元**それぞれの列の値。</span><span class="sxs-lookup"><span data-stu-id="d3357-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then   
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName, connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)   
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3357-217">参照</span><span class="sxs-lookup"><span data-stu-id="d3357-217">See Also</span></span>  
 [<span data-ttu-id="d3357-218">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="d3357-218">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="d3357-219">DataAdapter によるデータ ソースの更新</span><span class="sxs-lookup"><span data-stu-id="d3357-219">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="d3357-220">行エラー情報</span><span class="sxs-lookup"><span data-stu-id="d3357-220">Row Error Information</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [<span data-ttu-id="d3357-221">トランザクションと同時実行</span><span class="sxs-lookup"><span data-stu-id="d3357-221">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="d3357-222">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="d3357-222">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
