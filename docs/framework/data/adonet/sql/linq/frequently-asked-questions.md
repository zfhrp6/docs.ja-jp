---
title: よく寄せられる質問
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 5f556c46823bd867709e8c53b59f7ac53201d242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365489"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="b82b9-102">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="b82b9-102">Frequently Asked Questions</span></span>
<span data-ttu-id="b82b9-103">ここでは、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] を実装するときに発生する可能性のある一般的な問題の対処法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-103">The following sections answer some common issues that you might encounter when you implement [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="b82b9-104">その他の問題はで対処する[トラブルシューティング](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-104">Additional issues are addressed in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="cannot-connect"></a><span data-ttu-id="b82b9-105">接続できない</span><span class="sxs-lookup"><span data-stu-id="b82b9-105">Cannot Connect</span></span>  
 <span data-ttu-id="b82b9-106">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-106">Q.</span></span> <span data-ttu-id="b82b9-107">データベースに接続できません。</span><span class="sxs-lookup"><span data-stu-id="b82b9-107">I cannot connect to my database.</span></span>  
  
 <span data-ttu-id="b82b9-108">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-108">A.</span></span> <span data-ttu-id="b82b9-109">接続文字列が正しいと、SQL Server インスタンスが実行されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-109">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="b82b9-110">また、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、名前付きパイプ プロトコルを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-110">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="b82b9-111">詳細については、次を参照してください。[チュートリアルによる学習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-111">For more information, see [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
## <a name="changes-to-database-lost"></a><span data-ttu-id="b82b9-112">データベースの変更内容が失われる</span><span class="sxs-lookup"><span data-stu-id="b82b9-112">Changes to Database Lost</span></span>  
 <span data-ttu-id="b82b9-113">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-113">Q.</span></span> <span data-ttu-id="b82b9-114">データベース内のデータを変更しましたが、アプリケーションを再実行すると、変更が元に戻っています。</span><span class="sxs-lookup"><span data-stu-id="b82b9-114">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>  
  
 <span data-ttu-id="b82b9-115">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-115">A.</span></span> <span data-ttu-id="b82b9-116">変更結果をデータベースに保存するために、必ず <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-116">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>  
  
## <a name="database-connection-open-how-long"></a><span data-ttu-id="b82b9-117">データベース接続: どれほどの時間開いているか</span><span class="sxs-lookup"><span data-stu-id="b82b9-117">Database Connection: Open How Long?</span></span>  
 <span data-ttu-id="b82b9-118">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-118">Q.</span></span> <span data-ttu-id="b82b9-119">データベース接続が開いている時間は、どれほどですか。</span><span class="sxs-lookup"><span data-stu-id="b82b9-119">How long does my database connection remain open?</span></span>  
  
 <span data-ttu-id="b82b9-120">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-120">A.</span></span> <span data-ttu-id="b82b9-121">通常、接続は、クエリ結果を処理するまでは開いた状態を保ちます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-121">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="b82b9-122">すべての結果を処理するのに時間がかかる可能性がある場合、結果をキャッシュに入れることが可能であれば、クエリに対して <xref:System.Linq.Enumerable.ToList%2A> を適用してください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-122">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="b82b9-123">通常のシナリオでは、各オブジェクトが一度だけ処理されるため、`DataReader` と [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のどちらの場合もストリーミング モデルがより優れています。</span><span class="sxs-lookup"><span data-stu-id="b82b9-123">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="b82b9-124">接続が厳密にどのように使用されるかは、以下に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-124">The exact details of connection usage depend on the following:</span></span>  
  
-   <span data-ttu-id="b82b9-125">接続オブジェクトを使って <xref:System.Data.Linq.DataContext> が作成されている場合は、接続状態。</span><span class="sxs-lookup"><span data-stu-id="b82b9-125">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>  
  
-   <span data-ttu-id="b82b9-126">接続文字列の設定 (たとえば、複数のアクティブな結果セット (MARS) の有効化)。</span><span class="sxs-lookup"><span data-stu-id="b82b9-126">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="b82b9-127">詳細については、「 [複数のアクティブな結果セット (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-127">For more information, see [Multiple Active Result Sets (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).</span></span>  
  
## <a name="updating-without-querying"></a><span data-ttu-id="b82b9-128">クエリを使用しない更新</span><span class="sxs-lookup"><span data-stu-id="b82b9-128">Updating Without Querying</span></span>  
 <span data-ttu-id="b82b9-129">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-129">Q.</span></span> <span data-ttu-id="b82b9-130">データベースに対してあらかじめクエリを実行せずに、テーブル データを更新できますか?</span><span class="sxs-lookup"><span data-stu-id="b82b9-130">Can I update table data without first querying the database?</span></span>  
  
 <span data-ttu-id="b82b9-131">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-131">A.</span></span> <span data-ttu-id="b82b9-132">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] にはセットベースの更新コマンドはありませんが、次のいずれかの技法を使用すると、あらかじめクエリを実行せずに更新できます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-132">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>  
  
-   <span data-ttu-id="b82b9-133"><xref:System.Data.Linq.DataContext.ExecuteCommand%2A> を使って SQL コードを送信する。</span><span class="sxs-lookup"><span data-stu-id="b82b9-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>  
  
-   <span data-ttu-id="b82b9-134">オブジェクトの新しいインスタンスを作成し、更新に関連したすべての現在値 (フィールド) を初期化する。</span><span class="sxs-lookup"><span data-stu-id="b82b9-134">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="b82b9-135">その後、<xref:System.Data.Linq.DataContext> を使ってオブジェクトを <xref:System.Data.Linq.Table%601.Attach%2A> に関連付け、更新対象のフィールドを変更します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-135">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>  
  
## <a name="unexpected-query-results"></a><span data-ttu-id="b82b9-136">予期しないクエリ結果</span><span class="sxs-lookup"><span data-stu-id="b82b9-136">Unexpected Query Results</span></span>  
 <span data-ttu-id="b82b9-137">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-137">Q.</span></span> <span data-ttu-id="b82b9-138">予期しない結果がクエリから返されます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-138">My query is returning unexpected results.</span></span> <span data-ttu-id="b82b9-139">どうなっているのか調べる方法はありますか。</span><span class="sxs-lookup"><span data-stu-id="b82b9-139">How can I inspect what is occurring?</span></span>  
  
 <span data-ttu-id="b82b9-140">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-140">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b82b9-141"> には、生成された SQL コードを調べるためのツールがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="b82b9-141"> provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="b82b9-142">このうち、最も重要なものは <xref:System.Data.Linq.DataContext.Log%2A> です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-142">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="b82b9-143">詳細については、次を参照してください。[デバッグのサポート](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-143">For more information, see [Debugging Support](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).</span></span>  
  
## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="b82b9-144">予期しないストアド プロシージャ結果</span><span class="sxs-lookup"><span data-stu-id="b82b9-144">Unexpected Stored Procedure Results</span></span>  
 <span data-ttu-id="b82b9-145">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-145">Q.</span></span> <span data-ttu-id="b82b9-146">戻り値が `MAX()` によって計算されるストアド プロシージャがあります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-146">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="b82b9-147">このストアド プロシージャを [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] サーフェイスにドラッグすると、戻り値が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="b82b9-147">When I drag the stored procedure to the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] surface, the return value is not correct.</span></span>  
  
 <span data-ttu-id="b82b9-148">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-148">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b82b9-149"> には、ストアド プロシージャを介して、データベースによって生成される値を返す方法が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-149"> provides two ways to return database-generated values by way of stored procedures:</span></span>  
  
-   <span data-ttu-id="b82b9-150">出力結果に名前を付ける。</span><span class="sxs-lookup"><span data-stu-id="b82b9-150">By naming the output result.</span></span>  
  
-   <span data-ttu-id="b82b9-151">出力パラメーターを明示的に指定する。</span><span class="sxs-lookup"><span data-stu-id="b82b9-151">By explicitly specifying an output parameter.</span></span>  
  
 <span data-ttu-id="b82b9-152">間違っている出力例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-152">The following is an example of incorrect output.</span></span> <span data-ttu-id="b82b9-153">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は結果をマップできないため、常に 0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-153">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 <span data-ttu-id="b82b9-154">出力パラメーターを使用して正しい出力をする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-154">The following is an example of correct output by using an output parameter:</span></span>  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 <span data-ttu-id="b82b9-155">出力結果に名前を付けて正しい出力をする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-155">The following is an example of correct output by naming the output result:</span></span>  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 <span data-ttu-id="b82b9-156">詳細については、次を参照してください。[のカスタマイズの操作によってストアド プロシージャの使用](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-156">For more information, see [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).</span></span>  
  
## <a name="serialization-errors"></a><span data-ttu-id="b82b9-157">シリアル化のエラー</span><span class="sxs-lookup"><span data-stu-id="b82b9-157">Serialization Errors</span></span>  
 <span data-ttu-id="b82b9-158">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-158">Q.</span></span> <span data-ttu-id="b82b9-159">シリアル化しようとすると、次のエラーを取得:"入力 'system.data.linq.changetracker+standardchangetracker' シリアル化可能としてマークされていません"。</span><span class="sxs-lookup"><span data-stu-id="b82b9-159">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>  
  
 <span data-ttu-id="b82b9-160">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-160">A.</span></span> <span data-ttu-id="b82b9-161">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のコード生成では、<xref:System.Runtime.Serialization.DataContractSerializer> のシリアル化がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-161">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="b82b9-162"><xref:System.Xml.Serialization.XmlSerializer> および <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="b82b9-162">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="b82b9-163">詳細については、「[Serialization](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)」 (シリアル化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-163">For more information, see [Serialization](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>  
  
## <a name="multiple-dbml-files"></a><span data-ttu-id="b82b9-164">複数の DBML ファイル</span><span class="sxs-lookup"><span data-stu-id="b82b9-164">Multiple DBML Files</span></span>  
 <span data-ttu-id="b82b9-165">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-165">Q.</span></span> <span data-ttu-id="b82b9-166">いくつかのテーブルを共有する複数の DBML ファイルが存在する場合は、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-166">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>  
  
 <span data-ttu-id="b82b9-167">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-167">A.</span></span> <span data-ttu-id="b82b9-168">設定、**コンテキスト Namespace**と**Entity Namespace**プロパティから、 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] DBML ファイルごとに個別の値にします。</span><span class="sxs-lookup"><span data-stu-id="b82b9-168">Set the **Context Namespace** and **Entity Namespace** properties from the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to a distinct value for each DBML file.</span></span> <span data-ttu-id="b82b9-169">この手法により、名前および名前空間の競合を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-169">This approach eliminates the name/namespace collision.</span></span>  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="b82b9-170">挿入または更新で、データベース生成値を明示的に設定しなくても良いようにする</span><span class="sxs-lookup"><span data-stu-id="b82b9-170">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>  
 <span data-ttu-id="b82b9-171">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-171">Q.</span></span> <span data-ttu-id="b82b9-172">あるデータベース テーブルに `DateCreated` という列があり、その既定値は SQL `Getdate()` です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-172">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="b82b9-173">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して新しいレコードを挿入しようとすると、値が `NULL` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-173">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="b82b9-174">データベースの既定値が設定されるようにするには、どうしたらいいですか。</span><span class="sxs-lookup"><span data-stu-id="b82b9-174">I would expect it to be set to the database default.</span></span>  
  
 <span data-ttu-id="b82b9-175">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-175">A.</span></span> <span data-ttu-id="b82b9-176">ID 列 (自動インクリメント)、rowguidcol 列 (データベースが生成した GUID)、およびタイムスタンプ列の場合は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が、このような状況に自動的に対処します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-176">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="b82b9-177">それ以外の場合に手動で設定する<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true`と<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b82b9-177">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>  
  
## <a name="multiple-dataloadoptions"></a><span data-ttu-id="b82b9-178">複数の DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="b82b9-178">Multiple DataLoadOptions</span></span>  
 <span data-ttu-id="b82b9-179">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-179">Q.</span></span> <span data-ttu-id="b82b9-180">最初の読み込みオプションを上書きせずに、追加の読み込みオプションを指定できますか?</span><span class="sxs-lookup"><span data-stu-id="b82b9-180">Can I specify additional load options without overwriting the first?</span></span>  
  
 <span data-ttu-id="b82b9-181">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-181">A.</span></span> <span data-ttu-id="b82b9-182">はい。</span><span class="sxs-lookup"><span data-stu-id="b82b9-182">Yes.</span></span> <span data-ttu-id="b82b9-183">次の例のように、最初のオプションは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="b82b9-183">The first is not overwritten, as in the following example:</span></span>  
  
```vb  
Dim dlo As New DataLoadOptions()  
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)  
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)  
```  
  
```csharp  
DataLoadOptions dlo = new DataLoadOptions();  
dlo.LoadWith<Order>(o => o.Customer);  
dlo.LoadWith<Order>(o => o.OrderDetails);  
```  
  
## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="b82b9-184">SQL Compact 3.5 の使用に関するエラー</span><span class="sxs-lookup"><span data-stu-id="b82b9-184">Errors Using SQL Compact 3.5</span></span>  
 <span data-ttu-id="b82b9-185">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-185">Q.</span></span> <span data-ttu-id="b82b9-186">テーブルを [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] データベースからドラッグすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-186">I get an error when I drag tables out of a [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] database.</span></span>  
  
 <span data-ttu-id="b82b9-187">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-187">A.</span></span> <span data-ttu-id="b82b9-188">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] は [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] ランタイムではサポートされますが、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="b82b9-188">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)], although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="b82b9-189">この場合、独自のエンティティ クラスを作成して適切な属性を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-189">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>  
  
## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="b82b9-190">継承関係でのエラー</span><span class="sxs-lookup"><span data-stu-id="b82b9-190">Errors in Inheritance Relationships</span></span>  
 <span data-ttu-id="b82b9-191">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-191">Q.</span></span> <span data-ttu-id="b82b9-192">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]でツールボックスの継承図形を使って、2 つのエンティティを接続すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-192">I used the toolbox inheritance shape in the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to connect two entities, but I get errors.</span></span>  
  
 <span data-ttu-id="b82b9-193">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-193">A.</span></span> <span data-ttu-id="b82b9-194">関係を作成するだけでは不十分です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-194">Creating the relationship is not enough.</span></span> <span data-ttu-id="b82b9-195">識別子の列、基本クラスの識別子の値、派生クラスの識別子の値などの情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-195">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>  
  
## <a name="provider-model"></a><span data-ttu-id="b82b9-196">プロバイダー モデル</span><span class="sxs-lookup"><span data-stu-id="b82b9-196">Provider Model</span></span>  
 <span data-ttu-id="b82b9-197">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-197">Q.</span></span> <span data-ttu-id="b82b9-198">パブリック プロバイダー モデルを利用できますか?</span><span class="sxs-lookup"><span data-stu-id="b82b9-198">Is a public provider model available?</span></span>  
  
 <span data-ttu-id="b82b9-199">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-199">A.</span></span> <span data-ttu-id="b82b9-200">いいえ。使用可能なパブリック プロバイダー モデルはありません。</span><span class="sxs-lookup"><span data-stu-id="b82b9-200">No public provider model is available.</span></span> <span data-ttu-id="b82b9-201">この時点で[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL Server のサポートと[!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)]のみです。</span><span class="sxs-lookup"><span data-stu-id="b82b9-201">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] only.</span></span>  
  
## <a name="sql-injection-attacks"></a><span data-ttu-id="b82b9-202">SQL 注入攻撃</span><span class="sxs-lookup"><span data-stu-id="b82b9-202">SQL-Injection Attacks</span></span>  
 <span data-ttu-id="b82b9-203">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-203">Q.</span></span> <span data-ttu-id="b82b9-204">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、SQL 注入攻撃からどのように保護されますか?</span><span class="sxs-lookup"><span data-stu-id="b82b9-204">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>  
  
 <span data-ttu-id="b82b9-205">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-205">A.</span></span> <span data-ttu-id="b82b9-206">ユーザー入力の連結により形成される従来の SQL クエリでは、SQL 注入が大きなリスクでした。</span><span class="sxs-lookup"><span data-stu-id="b82b9-206">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b82b9-207"> では、クエリで <xref:System.Data.SqlClient.SqlParameter> を使用することにより、そのような注入を防止します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-207"> avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="b82b9-208">ユーザー入力はパラメーター値に変換されます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-208">User input is turned into parameter values.</span></span> <span data-ttu-id="b82b9-209">この手法は、顧客の入力で悪意のあるコマンドが使用されることを防止します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-209">This approach prevents malicious commands from being used from customer input.</span></span>  
  
## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="b82b9-210">DBML ファイル内の読み取り専用フラグの変更</span><span class="sxs-lookup"><span data-stu-id="b82b9-210">Changing Read-only Flag in DBML Files</span></span>  
 <span data-ttu-id="b82b9-211">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-211">Q.</span></span> <span data-ttu-id="b82b9-212">DBML ファイルからオブジェクト モデルを作成するときに、どうすれば、特定のプロパティから setter を取り除くことができますか?</span><span class="sxs-lookup"><span data-stu-id="b82b9-212">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>  
  
 <span data-ttu-id="b82b9-213">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-213">A.</span></span> <span data-ttu-id="b82b9-214">これは高度なシナリオですが、以下の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-214">Take the following steps for this advanced scenario:</span></span>  
  
1.  <span data-ttu-id="b82b9-215">.dbml ファイル内で、<xref:System.Data.Linq.ITable.IsReadOnly%2A> フラグを `True` に変更することにより、プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-215">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>  
  
2.  <span data-ttu-id="b82b9-216">部分クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-216">Add a partial class.</span></span> <span data-ttu-id="b82b9-217">読み取り専用メンバー用のパラメーターを使ってコンストラクターを作成します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-217">Create a constructor with parameters for the read-only members.</span></span>  
  
3.  <span data-ttu-id="b82b9-218">既定の <xref:System.Data.Linq.Mapping.UpdateCheck> 値 (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) がアプリケーションにとって適切な値かどうかを検討します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-218">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="b82b9-219">使用している場合、 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Visual Studio で、変更を上書きする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-219">If you are using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] in Visual Studio, your changes might be overwritten.</span></span>  
  
## <a name="aptca"></a><span data-ttu-id="b82b9-220">APTCA</span><span class="sxs-lookup"><span data-stu-id="b82b9-220">APTCA</span></span>  
 <span data-ttu-id="b82b9-221">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-221">Q.</span></span> <span data-ttu-id="b82b9-222">System.Data.Linq は、部分的に信頼されているコードが使用できるようにマークされていますか?</span><span class="sxs-lookup"><span data-stu-id="b82b9-222">Is System.Data.Linq marked for use by partially trusted code?</span></span>  
  
 <span data-ttu-id="b82b9-223">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-223">A.</span></span> <span data-ttu-id="b82b9-224">はい。System.Data.Linq.dll アセンブリは、[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 属性でマークされている <xref:System.Security.AllowPartiallyTrustedCallersAttribute> アセンブリの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="b82b9-224">Yes, the System.Data.Linq.dll assembly is among those [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="b82b9-225">このマークがないと、[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] のアセンブリは完全に信頼されたコードによってのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-225">Without this marking, assemblies in the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] are intended for use only by fully trusted code.</span></span>  
  
 <span data-ttu-id="b82b9-226">プリンシパルのシナリオでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]部分的に許可するには、呼び出し元が有効にするのには信頼されているため、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Web アプリケーションからアクセスするアセンブリを*信頼*構成は、[中] です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-226">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>  
  
## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="b82b9-227">複数のテーブルからのデータのマッピング</span><span class="sxs-lookup"><span data-stu-id="b82b9-227">Mapping Data from Multiple Tables</span></span>  
 <span data-ttu-id="b82b9-228">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-228">Q.</span></span> <span data-ttu-id="b82b9-229">エンティティに、複数のテーブルから取得されたデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b82b9-229">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="b82b9-230">どのようにマップできますか?</span><span class="sxs-lookup"><span data-stu-id="b82b9-230">How do I map it?</span></span>  
  
 <span data-ttu-id="b82b9-231">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-231">A.</span></span> <span data-ttu-id="b82b9-232">データベース内にビューを作成して、エンティティをそのビューにマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-232">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b82b9-233"> は、テーブル用と同じ SQL をビュー用に生成します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-233"> generates the same SQL for views as it does for tables.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b82b9-234">このシナリオでのビューの使用には、制限があります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-234">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="b82b9-235">この手法は、<xref:System.Data.Linq.Table%601> に対して実行される操作が、基になるビューでサポートされるような場合に、最も安全に機能します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-235">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="b82b9-236">どのような操作が意図されるかは、開発者だけが知っています。</span><span class="sxs-lookup"><span data-stu-id="b82b9-236">Only you know which operations are intended.</span></span> <span data-ttu-id="b82b9-237">たとえば、ほとんどのアプリケーションは読み取り専用、および他の多くを実行`Create` / `Update` / `Delete`操作のみを使用してビューに対してストアド プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="b82b9-237">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="b82b9-238">接続プール</span><span class="sxs-lookup"><span data-stu-id="b82b9-238">Connection Pooling</span></span>  
 <span data-ttu-id="b82b9-239">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-239">Q.</span></span> <span data-ttu-id="b82b9-240"><xref:System.Data.Linq.DataContext> プールに役立つコンストラクトはありますか?</span><span class="sxs-lookup"><span data-stu-id="b82b9-240">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>  
  
 <span data-ttu-id="b82b9-241">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-241">A.</span></span> <span data-ttu-id="b82b9-242"><xref:System.Data.Linq.DataContext> のインスタンスは再使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-242">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="b82b9-243"><xref:System.Data.Linq.DataContext> はそれぞれ、特定の 1 つの編集/クエリ セッション用の状態 (ID キャッシュを含む) を保持します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-243">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="b82b9-244">データベースの現在の状態に基づく新しいインスタンスを得るには、新しい <xref:System.Data.Linq.DataContext> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-244">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="b82b9-245">それでも、基になる [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] 接続プールは使用できます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-245">You can still use underlying [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] connection pooling.</span></span> <span data-ttu-id="b82b9-246">詳しくは、「[SQL Server の接続プール (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b82b9-246">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="b82b9-247">2 番目の DataContext が更新されない</span><span class="sxs-lookup"><span data-stu-id="b82b9-247">Second DataContext Is Not Updated</span></span>  
 <span data-ttu-id="b82b9-248">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-248">Q.</span></span> <span data-ttu-id="b82b9-249">データベース内の値を格納するために、<xref:System.Data.Linq.DataContext> の 1 つのインスタンスを使用しました。</span><span class="sxs-lookup"><span data-stu-id="b82b9-249">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="b82b9-250">しかし、同じデータベースに対する 2 番目の <xref:System.Data.Linq.DataContext> では、更新された値が反映されません。</span><span class="sxs-lookup"><span data-stu-id="b82b9-250">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="b82b9-251">2 番目の <xref:System.Data.Linq.DataContext> インスタンスは、キャッシュされた値を返すようです。</span><span class="sxs-lookup"><span data-stu-id="b82b9-251">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>  
  
 <span data-ttu-id="b82b9-252">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-252">A.</span></span> <span data-ttu-id="b82b9-253">この動作は意図されたものです。</span><span class="sxs-lookup"><span data-stu-id="b82b9-253">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b82b9-254"> は、最初のインスタンスと同じインスタンス/値を返し続けます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-254"> continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="b82b9-255">更新の際には、オプティミスティック同時実行が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-255">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="b82b9-256">元のデータを使ってデータベースの現在の状態を検査し、実際に未変更であることをアサートします。</span><span class="sxs-lookup"><span data-stu-id="b82b9-256">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="b82b9-257">変更されている場合は競合が発生するため、アプリケーションでそれを解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-257">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="b82b9-258">1 つのオプションとして、アプリケーションは、元の状態をデータベースの現在の状態にリセットして、更新を再試行できます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-258">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="b82b9-259">詳細については、次を参照してください。[する方法: 変更の競合を管理](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-259">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="b82b9-260">また、<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> を false に設定することもできます。この場合、キャッシュと変更追跡が無効になります。</span><span class="sxs-lookup"><span data-stu-id="b82b9-260">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="b82b9-261">その後は、クエリを実行するたびに最新の値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="b82b9-261">You can then retrieve the latest values every time that you query.</span></span>  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="b82b9-262">読み取り専用モードで SubmitChanges を呼び出すことができない</span><span class="sxs-lookup"><span data-stu-id="b82b9-262">Cannot Call SubmitChanges in Read-only Mode</span></span>  
 <span data-ttu-id="b82b9-263">Q.</span><span class="sxs-lookup"><span data-stu-id="b82b9-263">Q.</span></span> <span data-ttu-id="b82b9-264">読み取り専用モードで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出そうとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b82b9-264">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>  
  
 <span data-ttu-id="b82b9-265">A: </span><span class="sxs-lookup"><span data-stu-id="b82b9-265">A.</span></span> <span data-ttu-id="b82b9-266">読み取り専用モードでは、変更を追跡するコンテキスト機能は無効です。</span><span class="sxs-lookup"><span data-stu-id="b82b9-266">Read-only mode turns off the ability of the context to track changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b82b9-267">関連項目</span><span class="sxs-lookup"><span data-stu-id="b82b9-267">See Also</span></span>  
 [<span data-ttu-id="b82b9-268">参照</span><span class="sxs-lookup"><span data-stu-id="b82b9-268">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="b82b9-269">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b82b9-269">Troubleshooting</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)  
 [<span data-ttu-id="b82b9-270">LINQ to SQL におけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="b82b9-270">Security in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
