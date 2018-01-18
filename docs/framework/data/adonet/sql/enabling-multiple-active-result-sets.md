---
title: "複数のアクティブな結果セットの有効化"
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
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b2b1e3ccfe162b6d4903aaf162673ba476296d8b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="fdcc3-102">複数のアクティブな結果セットの有効化</span><span class="sxs-lookup"><span data-stu-id="fdcc3-102">Enabling Multiple Active Result Sets</span></span>
<span data-ttu-id="fdcc3-103">複数のアクティブな結果セット (MARS : Multiple Active Result Set) は、SQL Server で動作する機能であり、複数のバッチを単一の接続で実行することができます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-103">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="fdcc3-104">SQL Server で使用できるように MARS が有効になっているときは、使用中の各コマンド オブジェクトは接続にセッションを追加します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-104">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdcc3-105">単一の MARS セッションは、MARS 用に 1 つの論理接続を開いた後、アクティブな各コマンドにつき 1 つの論理接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-105">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="fdcc3-106">接続文字列で MARS を有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="fdcc3-106">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdcc3-107">次の接続文字列が、サンプルを使用して**AdventureWorks** SQL Server に付属のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-107">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="fdcc3-108">指定されている接続文字列は、データベースが MSSQL1 という名前のサーバーにインストールされていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-108">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="fdcc3-109">必要に応じて、お使いの環境に合わせて接続文字列を変更してください。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-109">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="fdcc3-110">既定では、MARS 機能は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-110">The MARS feature is disabled by default.</span></span> <span data-ttu-id="fdcc3-111">この機能を有効にするには、キーワード ペア "MultipleActiveResultSet=True" を接続文字列に追加します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-111">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="fdcc3-112">"True" は、MARS を有効にするための唯一の有効な値です。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-112">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="fdcc3-113">次の例では、SQL Server のインスタンスに接続し、MARS が有効になるよう指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-113">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="fdcc3-114">MARS を無効にするには、キーワード ペア "MultipleActiveResultSet=False" を接続文字列に追加します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-114">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="fdcc3-115">"False" は、MARS を無効にするための唯一の有効な値です。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-115">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="fdcc3-116">次の接続文字列では、MARS を無効にしています。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-116">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="fdcc3-117">MARS の使用に関する特記事項</span><span class="sxs-lookup"><span data-stu-id="fdcc3-117">Special Considerations When Using MARS</span></span>  
 <span data-ttu-id="fdcc3-118">一般に、MARS の有効な接続を使用するために、既存のアプリケーションを修正する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-118">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="fdcc3-119">ただし、MARS 機能をご自分のアプリケーションで使用する場合、次の特記事項について理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-119">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="fdcc3-120">ステートメント インタリーブ</span><span class="sxs-lookup"><span data-stu-id="fdcc3-120">Statement Interleaving</span></span>  
 <span data-ttu-id="fdcc3-121">MARS 操作は、サーバー上で同期して実行されます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-121">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="fdcc3-122">SELECT ステートメントと BULK INSERT ステートメントをインタリーブすることができます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-122">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="fdcc3-123">ただし、DML (データ操作言語) と DDL (データ定義言語) のステートメントはアトミック実行されます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-123">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="fdcc3-124">バッチのアトミック実行中にステートメントを実行しようとすると、いずれもブロックされます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-124">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="fdcc3-125">サーバーでの並列実行は MARS の機能ではありません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-125">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="fdcc3-126">MARS 接続において、SELECT ステートメントを含むバッチと DML ステートメントを含むバッチの 2 つが送信されると、SELECT ステートメントの実行中に DML の実行が開始されます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-126">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="fdcc3-127">ただし、DML ステートメントは SELECT ステートメントが進行する前に実行を完了しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-127">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="fdcc3-128">両方のステートメントが同じトランザクションで実行されている場合、SELECT ステートメントの実行を開始した後に行われた DML ステートメントによる変更は、読み取り操作では表示されません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-128">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="fdcc3-129">SELECT ステートメント内の WAITFOR ステートメントは、待機中、つまり最初の行が作成されるまではトランザクションを生成しません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-129">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="fdcc3-130">これは、WAITFOR ステートメントが待機している間は、同一の接続内では他のいかなるバッチも実行されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-130">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="fdcc3-131">MARS セッションのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="fdcc3-131">MARS Session Cache</span></span>  
 <span data-ttu-id="fdcc3-132">MARS を有効にして接続が開かれている場合、論理セッションが作成されます。このセッションによってオーバーヘッドが増加します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-132">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="fdcc3-133">オーバーヘッドを最小限に抑えるおよびパフォーマンスの向上に**SqlClient**接続内で、MARS セッションをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-133">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="fdcc3-134">キャッシュには、最大 10 個の MARS セッションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-134">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="fdcc3-135">ユーザーがこの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-135">This value is not user adjustable.</span></span> <span data-ttu-id="fdcc3-136">セッションが限度に達すると新しいセッションが作成され、エラーは生成されません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-136">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="fdcc3-137">キャッシュとそのキャッシュに含まれるセッションは、接続ごとに作成されます。接続をまたいで共有されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-137">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="fdcc3-138">セッションが解放されると、プールの上限に達している場合を除き、セッションはプールに返されます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-138">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="fdcc3-139">キャッシュ プールがいっぱいになっている場合、セッションは閉じられます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-139">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="fdcc3-140">MARS セッションの有効期限は終了しません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-140">MARS sessions do not expire.</span></span> <span data-ttu-id="fdcc3-141">クリーンアップされるのは、接続オブジェクトが破棄されるときだけです。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-141">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="fdcc3-142">MARS セッションのキャッシュはプリロードされません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-142">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="fdcc3-143">アプリケーションがさらに多くのセッションを要求したときに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-143">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="fdcc3-144">スレッド セーフ</span><span class="sxs-lookup"><span data-stu-id="fdcc3-144">Thread Safety</span></span>  
 <span data-ttu-id="fdcc3-145">MARS 操作は、スレッド セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-145">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="fdcc3-146">接続プール</span><span class="sxs-lookup"><span data-stu-id="fdcc3-146">Connection Pooling</span></span>  
 <span data-ttu-id="fdcc3-147">MARS の有効な接続は、その他の接続と同じようにプールされます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-147">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="fdcc3-148">アプリケーションが 2 つの接続を開き、その一方は MARS が有効で他方は MARS が無効になっている場合、それら 2 つの接続は別々のプールに入れられます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-148">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="fdcc3-149">詳細については、次を参照してください。 [SQL サーバー接続プール (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)です。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-149">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="fdcc3-150">SQL Server のバッチ実行環境</span><span class="sxs-lookup"><span data-stu-id="fdcc3-150">SQL Server Batch Execution Environment</span></span>  
 <span data-ttu-id="fdcc3-151">接続を開くとき、既定の環境が定義されます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-151">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="fdcc3-152">この環境は、MARS の論理セッションにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-152">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="fdcc3-153">バッチ実行環境には、次のコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-153">The batch execution environment includes the following components:</span></span>  
  
-   <span data-ttu-id="fdcc3-154">SET オプション (ANSI_NULLS、DATE_FORMAT、LANGUAGE、TEXTSIZE など)</span><span class="sxs-lookup"><span data-stu-id="fdcc3-154">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
-   <span data-ttu-id="fdcc3-155">セキュリティ コンテキスト (ユーザーまたはアプリケーションのロール)</span><span class="sxs-lookup"><span data-stu-id="fdcc3-155">Security context (user/application role)</span></span>  
  
-   <span data-ttu-id="fdcc3-156">データベース コンテキスト (現在のデータベース)</span><span class="sxs-lookup"><span data-stu-id="fdcc3-156">Database context (current database)</span></span>  
  
-   <span data-ttu-id="fdcc3-157">実行状態を変数 (たとえば、@@ERROR、@@ROWCOUNT、@@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="fdcc3-157">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
-   <span data-ttu-id="fdcc3-158">最上位の一時テーブル</span><span class="sxs-lookup"><span data-stu-id="fdcc3-158">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="fdcc3-159">MARS を使用すると、既定の実行環境が接続に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-159">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="fdcc3-160">所定の接続で実行を開始する新しいバッチは、いずれも既定の環境のコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-160">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="fdcc3-161">コードが所定のバッチで実行されるときは、その環境に対して行われるすべての変更は、常に特定のバッチにスコープ設定されます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-161">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="fdcc3-162">実行が完了すると、実行の設定は既定の環境にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-162">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="fdcc3-163">単一のバッチが複数のコマンドを発行し、それらが同じトランザクションで連続して実行される場合、そのセマンティクスは、以前のクライアントやサーバーを含む接続で公開されているときのセマンティクスと同じです。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-163">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="fdcc3-164">並列実行</span><span class="sxs-lookup"><span data-stu-id="fdcc3-164">Parallel Execution</span></span>  
 <span data-ttu-id="fdcc3-165">MARS は、アプリケーション内で複数の接続に対するすべての要件を削除するようには設計されていません。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-165">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="fdcc3-166">アプリケーションがサーバーに対するコマンドの完全な並列実行を必要とする場合、複数の接続を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-166">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="fdcc3-167">たとえば、次のようなシナリオがあるとします。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-167">For example, consider the following scenario.</span></span> <span data-ttu-id="fdcc3-168">2 つのコマンド オブジェクトが作成され、一方は結果セットを処理し、もう一方はデータを更新するとします。それらは MARS を介して共通の接続を共有します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-168">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="fdcc3-169">このシナリオでは、`Transaction`です。`Commit`</span><span class="sxs-lookup"><span data-stu-id="fdcc3-169">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="fdcc3-170">次の例外を生成する最初のコマンド オブジェクトのすべての結果を読み取られるまでの更新に失敗します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-170">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="fdcc3-171">メッセージ: トランザクション コンテキストを他のセッションが使用中です。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-171">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="fdcc3-172">ソース: .Net SqlClient Data Provider</span><span class="sxs-lookup"><span data-stu-id="fdcc3-172">Source: .Net SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="fdcc3-173">期待される出力: (null)</span><span class="sxs-lookup"><span data-stu-id="fdcc3-173">Expected: (null)</span></span>  
  
 <span data-ttu-id="fdcc3-174">受信: System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="fdcc3-174">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="fdcc3-175">このシナリオに対応するには、次の 3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-175">There are three options for handling this scenario:</span></span>  
  
1.  <span data-ttu-id="fdcc3-176">リーダーが作成されてからトランザクションを開始し、リーダーがトランザクションの一部にならないようにします。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-176">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="fdcc3-177">すべての更新は、それ自身のトランザクションになります。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-177">Every update then becomes its own transaction.</span></span>  
  
2.  <span data-ttu-id="fdcc3-178">リーダーが閉じてからすべての操作をコミットします。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-178">Commit all work after the reader is closed.</span></span> <span data-ttu-id="fdcc3-179">この場合、後続の更新バッチが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-179">This has the potential for a substantial batch of updates.</span></span>  
  
3.  <span data-ttu-id="fdcc3-180">MARS を使用せず、代わりに MARS が導入される以前に行っていたように、コマンド オブジェクトごとに別々の接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-180">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="fdcc3-181">MARS サポートの検出</span><span class="sxs-lookup"><span data-stu-id="fdcc3-181">Detecting MARS Support</span></span>  
 <span data-ttu-id="fdcc3-182">アプリケーションは、`SqlConnection.ServerVersion` の値を読み取って MARS サポートを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-182">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="fdcc3-183">SQL Server 2005 のメジャー番号は 9、SQL Server 2008 のメジャー番号は 10 です。</span><span class="sxs-lookup"><span data-stu-id="fdcc3-183">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdcc3-184">参照</span><span class="sxs-lookup"><span data-stu-id="fdcc3-184">See Also</span></span>  
 [<span data-ttu-id="fdcc3-185">複数のアクティブな結果セット (MARS)</span><span class="sxs-lookup"><span data-stu-id="fdcc3-185">Multiple Active Result Sets (MARS)</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [<span data-ttu-id="fdcc3-186">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="fdcc3-186">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
