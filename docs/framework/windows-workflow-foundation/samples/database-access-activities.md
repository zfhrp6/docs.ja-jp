---
title: "データベース アクセス アクティビティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 10066c1d5e6bd0d03d91337a2fed987c881b23b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="database-access-activities"></a><span data-ttu-id="34950-102">データベース アクセス アクティビティ</span><span class="sxs-lookup"><span data-stu-id="34950-102">Database Access Activities</span></span>
<span data-ttu-id="34950-103">データベース アクセス アクティビティを使用すると、ワークフロー内でデータベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="34950-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="34950-104">これらのアクティビティを取得または情報を変更し、使用するデータベースへのアクセスを許可する[ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081)データベースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="34950-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34950-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="34950-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34950-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="34950-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="34950-107">このディレクトリが存在しない場合は、ダウンロード ページに移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="34950-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34950-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="34950-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`  
  
## <a name="database-activities"></a><span data-ttu-id="34950-109">データベース アクティビティ</span><span class="sxs-lookup"><span data-stu-id="34950-109">Database Activities</span></span>  
 <span data-ttu-id="34950-110">以降では、このサンプルに含まれている一連のアクティビティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="34950-110">The following sections detail the list of activities included in this sample.</span></span>  
  
## <a name="dbupdate"></a><span data-ttu-id="34950-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="34950-111">DbUpdate</span></span>  
 <span data-ttu-id="34950-112">データベースを変更する SQL クエリを実行します (挿入、更新、削除、およびその他の変更)。</span><span class="sxs-lookup"><span data-stu-id="34950-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>  
  
 <span data-ttu-id="34950-113">このクラスは作業を非同期に実行します (<xref:System.Activities.AsyncCodeActivity> から派生し、その非同期機能を使用します)。</span><span class="sxs-lookup"><span data-stu-id="34950-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>  
  
 <span data-ttu-id="34950-114">接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="34950-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="34950-115">実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。</span><span class="sxs-lookup"><span data-stu-id="34950-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="34950-116">`DbUpdate` の実行が完了すると、影響を受けたレコードの数が `AffectedRecords` プロパティで返されます。</span><span class="sxs-lookup"><span data-stu-id="34950-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
|<span data-ttu-id="34950-117">引数</span><span class="sxs-lookup"><span data-stu-id="34950-117">Argument</span></span>|<span data-ttu-id="34950-118">説明</span><span class="sxs-lookup"><span data-stu-id="34950-118">Description</span></span>|  
|-|-|  
|<span data-ttu-id="34950-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="34950-119">ProviderName</span></span>|<span data-ttu-id="34950-120">ADO.NET プロバイダーの不変名。</span><span class="sxs-lookup"><span data-stu-id="34950-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="34950-121">この引数を設定する場合は、`ConnectionString` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34950-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="34950-122">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="34950-122">ConnectionString</span></span>|<span data-ttu-id="34950-123">データベースに接続するための接続文字列。</span><span class="sxs-lookup"><span data-stu-id="34950-123">Connection string to connect to the database.</span></span> <span data-ttu-id="34950-124">この引数を設定する場合は、`ProviderName` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34950-124">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="34950-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="34950-125">ConfigName</span></span>|<span data-ttu-id="34950-126">接続情報が格納されている構成ファイル セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="34950-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="34950-127">この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="34950-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="34950-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="34950-128">CommandType</span></span>|<span data-ttu-id="34950-129">実行する <xref:System.Data.Common.DbCommand> の種類。</span><span class="sxs-lookup"><span data-stu-id="34950-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="34950-130">Sql</span><span class="sxs-lookup"><span data-stu-id="34950-130">Sql</span></span>|<span data-ttu-id="34950-131">実行する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="34950-131">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="34950-132">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34950-132">Parameters</span></span>|<span data-ttu-id="34950-133">SQL クエリのパラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="34950-133">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="34950-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="34950-134">AffectedRecords</span></span>|<span data-ttu-id="34950-135">最後の操作の影響を受けたレコードの数。</span><span class="sxs-lookup"><span data-stu-id="34950-135">Number of records affected by the last operation.</span></span>|  
  
## <a name="dbqueryscalar"></a><span data-ttu-id="34950-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="34950-136">DbQueryScalar</span></span>  
 <span data-ttu-id="34950-137">データベースから 1 つの値を取得するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="34950-137">Executes a query that retrieves a single value from the database.</span></span>  
  
 <span data-ttu-id="34950-138">このクラスは作業を非同期に実行します (<xref:System.Activities.AsyncCodeActivity%601> から派生し、その非同期機能を使用します)。</span><span class="sxs-lookup"><span data-stu-id="34950-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>  
  
 <span data-ttu-id="34950-139">接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="34950-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="34950-140">実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。</span><span class="sxs-lookup"><span data-stu-id="34950-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="34950-141">後に`DbQueryScalar`が実行すると、スカラーで返される、`Result``out`引数 (型の`TResult`、つまり、基本クラスで定義されている<xref:System.Activities.AsyncCodeActivity%601>)。</span><span class="sxs-lookup"><span data-stu-id="34950-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>  
  
```  
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|<span data-ttu-id="34950-142">引数</span><span class="sxs-lookup"><span data-stu-id="34950-142">Argument</span></span>|<span data-ttu-id="34950-143">説明</span><span class="sxs-lookup"><span data-stu-id="34950-143">Description</span></span>|  
|-|-|  
|<span data-ttu-id="34950-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="34950-144">ProviderName</span></span>|<span data-ttu-id="34950-145">ADO.NET プロバイダーの不変名。</span><span class="sxs-lookup"><span data-stu-id="34950-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="34950-146">この引数を設定する場合は、`ConnectionString` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34950-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="34950-147">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="34950-147">ConnectionString</span></span>|<span data-ttu-id="34950-148">データベースに接続するための接続文字列。</span><span class="sxs-lookup"><span data-stu-id="34950-148">Connection string to connect to the database.</span></span> <span data-ttu-id="34950-149">この引数を設定する場合は、`ProviderName` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34950-149">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="34950-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="34950-150">ConfigName</span></span>|<span data-ttu-id="34950-151">接続情報が格納されている構成ファイル セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="34950-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="34950-152">この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="34950-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="34950-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="34950-153">CommandType</span></span>|<span data-ttu-id="34950-154">実行する <xref:System.Data.Common.DbCommand> の種類。</span><span class="sxs-lookup"><span data-stu-id="34950-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="34950-155">Sql</span><span class="sxs-lookup"><span data-stu-id="34950-155">Sql</span></span>|<span data-ttu-id="34950-156">実行する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="34950-156">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="34950-157">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34950-157">Parameters</span></span>|<span data-ttu-id="34950-158">SQL クエリのパラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="34950-158">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="34950-159">結果</span><span class="sxs-lookup"><span data-stu-id="34950-159">Result</span></span>|<span data-ttu-id="34950-160">クエリの実行後に取得されたスカラー。</span><span class="sxs-lookup"><span data-stu-id="34950-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="34950-161">この引数は `TResult` 型です。</span><span class="sxs-lookup"><span data-stu-id="34950-161">This argument is of type `TResult`.</span></span>|  
  
## <a name="dbquery"></a><span data-ttu-id="34950-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="34950-162">DbQuery</span></span>  
 <span data-ttu-id="34950-163">オブジェクトのリストを取得するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="34950-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="34950-164">マッピング関数が実行されるクエリを実行した後 (ことができます<xref:System.Func%601> < `DbDataReader`、 `TResult`> または<xref:System.Activities.ActivityFunc%601> < `DbDataReader`、 `TResult`>)。</span><span class="sxs-lookup"><span data-stu-id="34950-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="34950-165">このマッピング関数は、`DbDataReader` 内のレコードを取得して、返されるオブジェクトにマップします。</span><span class="sxs-lookup"><span data-stu-id="34950-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>  
  
 <span data-ttu-id="34950-166">接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="34950-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="34950-167">実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。</span><span class="sxs-lookup"><span data-stu-id="34950-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="34950-168">SQL クエリの結果は、`DbDataReader` を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="34950-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="34950-169">`DbDataReader` が反復処理されて、`DbDataReader` の行が `TResult` のインスタンスにマップされます。</span><span class="sxs-lookup"><span data-stu-id="34950-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="34950-170">ユーザー`DbQuery`に渡すマッピング コードが、これは、2 つの方法で行うことができます: を使用して、 <xref:System.Func%601> < `DbDataReader`、 `TResult`> または<xref:System.Activities.ActivityFunc%601> < `DbDataReader`、 `TResult`>。</span><span class="sxs-lookup"><span data-stu-id="34950-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="34950-171">1 つ目の方法は、マッピングが 1 つのパルスで実行されるので</span><span class="sxs-lookup"><span data-stu-id="34950-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="34950-172">高速ですが、XAML にシリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="34950-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="34950-173">2 つ目の方法は、マッピングが複数のパルスで実行されるので</span><span class="sxs-lookup"><span data-stu-id="34950-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="34950-174">時間がかかることがありますが、XAML へのシリアル化や宣言による作成が可能です (既存のアクティビティをマッピングに参加させることができます)。</span><span class="sxs-lookup"><span data-stu-id="34950-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>  
  
```  
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [OverloadGroup("DirectMapping")]  
    [DefaultValue(null)]  
    public Func<DbDataReader, TResult> Mapper { get; set; }  
  
    [OverloadGroup("MultiplePulseMapping")]  
    [DefaultValue(null)]  
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }  
}  
```  
  
|<span data-ttu-id="34950-175">引数</span><span class="sxs-lookup"><span data-stu-id="34950-175">Argument</span></span>|<span data-ttu-id="34950-176">説明</span><span class="sxs-lookup"><span data-stu-id="34950-176">Description</span></span>|  
|-|-|  
|<span data-ttu-id="34950-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="34950-177">ProviderName</span></span>|<span data-ttu-id="34950-178">ADO.NET プロバイダーの不変名。</span><span class="sxs-lookup"><span data-stu-id="34950-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="34950-179">この引数を設定する場合は、`ConnectionString` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34950-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="34950-180">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="34950-180">ConnectionString</span></span>|<span data-ttu-id="34950-181">データベースに接続するための接続文字列。</span><span class="sxs-lookup"><span data-stu-id="34950-181">Connection string to connect to the database.</span></span> <span data-ttu-id="34950-182">この引数を設定する場合は、`ProviderName` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34950-182">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="34950-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="34950-183">ConfigName</span></span>|<span data-ttu-id="34950-184">接続情報が格納されている構成ファイル セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="34950-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="34950-185">この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="34950-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="34950-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="34950-186">CommandType</span></span>|<span data-ttu-id="34950-187">実行する <xref:System.Data.Common.DbCommand> の種類。</span><span class="sxs-lookup"><span data-stu-id="34950-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="34950-188">Sql</span><span class="sxs-lookup"><span data-stu-id="34950-188">Sql</span></span>|<span data-ttu-id="34950-189">実行する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="34950-189">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="34950-190">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34950-190">Parameters</span></span>|<span data-ttu-id="34950-191">SQL クエリのパラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="34950-191">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="34950-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="34950-192">Mapper</span></span>|<span data-ttu-id="34950-193">マッピング関数 (<xref:System.Func%601><`DbDataReader`、 `TResult`>) 内のレコードを取得する、`DataReader`クエリの実行結果として取得され、型のオブジェクトのインスタンスを返します`TResult`に追加します。`Result`コレクション。</span><span class="sxs-lookup"><span data-stu-id="34950-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="34950-194">この場合、マッピングは 1 つのパルスで実行されますが、デザイナーを使用して宣言で作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="34950-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|  
|<span data-ttu-id="34950-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="34950-195">MapperFunc</span></span>|<span data-ttu-id="34950-196">マッピング関数 (<xref:System.Activities.ActivityFunc%601><`DbDataReader`、 `TResult`>) 内のレコードを取得する、`DataReader`クエリの実行結果として取得され、型のオブジェクトのインスタンスを返します`TResult`に追加します。`Result`コレクション。</span><span class="sxs-lookup"><span data-stu-id="34950-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="34950-197">この場合、マッピングは複数のパルスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="34950-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="34950-198">この関数は、XAML へのシリアル化や宣言による作成が可能です (既存のアクティビティをマッピングに参加させることができます)。</span><span class="sxs-lookup"><span data-stu-id="34950-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|  
|<span data-ttu-id="34950-199">結果</span><span class="sxs-lookup"><span data-stu-id="34950-199">Result</span></span>|<span data-ttu-id="34950-200">クエリを実行し、`DataReader` の各レコードに対してマッピング関数を実行した結果として取得されたオブジェクトのリスト。</span><span class="sxs-lookup"><span data-stu-id="34950-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|  
  
## <a name="dbquerydataset"></a><span data-ttu-id="34950-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="34950-201">DbQueryDataSet</span></span>  
 <span data-ttu-id="34950-202"><xref:System.Data.DataSet> を返すクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="34950-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="34950-203">このクラスは作業を非同期に実行します </span><span class="sxs-lookup"><span data-stu-id="34950-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="34950-204">派生して<xref:System.Activities.AsyncCodeActivity> < `TResult`> し、その非同期機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="34950-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>  
  
 <span data-ttu-id="34950-205">接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="34950-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>  
  
 <span data-ttu-id="34950-206">実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。</span><span class="sxs-lookup"><span data-stu-id="34950-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="34950-207">後に、`DbQueryDataSet`が実行される、`DataSet`で返される、`Result``out`引数 (型の`TResult`、つまり、基本クラスで定義されている<xref:System.Activities.AsyncCodeActivity%601>)。</span><span class="sxs-lookup"><span data-stu-id="34950-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result``out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>  
  
```  
public class DbQueryDataSet : AsyncCodeActivity<DataSet>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|<span data-ttu-id="34950-208">引数</span><span class="sxs-lookup"><span data-stu-id="34950-208">Argument</span></span>|<span data-ttu-id="34950-209">説明</span><span class="sxs-lookup"><span data-stu-id="34950-209">Description</span></span>|  
|-|-|  
|<span data-ttu-id="34950-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="34950-210">ProviderName</span></span>|<span data-ttu-id="34950-211">ADO.NET プロバイダーの不変名。</span><span class="sxs-lookup"><span data-stu-id="34950-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="34950-212">この引数を設定する場合は、`ConnectionString` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34950-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|  
|<span data-ttu-id="34950-213">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="34950-213">ConnectionString</span></span>|<span data-ttu-id="34950-214">データベースに接続するための接続文字列。</span><span class="sxs-lookup"><span data-stu-id="34950-214">Connection string to connect to the database.</span></span> <span data-ttu-id="34950-215">この引数を設定する場合は、`ProviderName` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34950-215">If this argument is set, then `ProviderName` must also be set.</span></span>|  
|<span data-ttu-id="34950-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="34950-216">ConfigName</span></span>|<span data-ttu-id="34950-217">接続情報が格納されている構成ファイル セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="34950-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="34950-218">この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="34950-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|  
|<span data-ttu-id="34950-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="34950-219">CommandType</span></span>|<span data-ttu-id="34950-220">実行する <xref:System.Data.Common.DbCommand> の種類。</span><span class="sxs-lookup"><span data-stu-id="34950-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|  
|<span data-ttu-id="34950-221">Sql</span><span class="sxs-lookup"><span data-stu-id="34950-221">Sql</span></span>|<span data-ttu-id="34950-222">実行する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="34950-222">The SQL command to be executed.</span></span>|  
|<span data-ttu-id="34950-223">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34950-223">Parameters</span></span>|<span data-ttu-id="34950-224">SQL クエリのパラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="34950-224">Collection of the parameters of the SQL query.</span></span>|  
|<span data-ttu-id="34950-225">結果</span><span class="sxs-lookup"><span data-stu-id="34950-225">Result</span></span>|<span data-ttu-id="34950-226">クエリの実行後に取得された <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="34950-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|  
  
## <a name="configuring-connection-information"></a><span data-ttu-id="34950-227">接続情報の構成</span><span class="sxs-lookup"><span data-stu-id="34950-227">Configuring Connection Information</span></span>  
 <span data-ttu-id="34950-228">すべての DbActivities は同じ構成パラメーターを共有します。</span><span class="sxs-lookup"><span data-stu-id="34950-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="34950-229">パラメーターを構成するには次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="34950-229">They can be configured in two ways:</span></span>  
  
-   <span data-ttu-id="34950-230">`ConnectionString + InvariantName`: ADO.NET プロバイダーの不変名と接続文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="34950-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<DateTime>()  
    {  
        ProviderName = "System.Data.SqlClient",  
        ConnectionString = @"Data Source=.\SQLExpress;  
                             Initial Catalog=DbActivitiesSample;  
                             Integrated Security=True",  
        Sql = "SELECT GetDate()"  
    };  
    ```  
  
-   <span data-ttu-id="34950-231">`ConfigName`: 接続情報を含む構成セクションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="34950-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>  
  
    ```xml  
    <connectionStrings>      
        <add name="DbActivitiesSample"  
             providerName="System.Data.SqlClient"  
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>  
      </connectionStrings>  
    ```  
  
-   <span data-ttu-id="34950-232">アクティビティで次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="34950-232">In the activity:</span></span>  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<int>()  
    {                  
        ConfigName = "DbActivitiesSample",  
        Sql = "SELECT COUNT(*) FROM Roles"  
    };  
    ```  
  
## <a name="running-this-sample"></a><span data-ttu-id="34950-233">このサンプルの実行</span><span class="sxs-lookup"><span data-stu-id="34950-233">Running this sample</span></span>  
  
### <a name="setup-instructions"></a><span data-ttu-id="34950-234">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="34950-234">Setup instructions</span></span>  
 <span data-ttu-id="34950-235">このサンプルはデータベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="34950-235">This sample uses a database.</span></span> <span data-ttu-id="34950-236">設定と読み込みのためのスクリプト (Setup.cmd) がサンプルに付属しているので、</span><span class="sxs-lookup"><span data-stu-id="34950-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="34950-237">そのファイルを、コマンド プロンプトを使用して実行してください。</span><span class="sxs-lookup"><span data-stu-id="34950-237">You must execute that file using the command prompt.</span></span>  
  
 <span data-ttu-id="34950-238">Setup.cmd スクリプトは、CreateDb.sql スクリプト ファイルを呼び出します。このスクリプト ファイルには、次の操作を実行する SQL コマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="34950-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>  
  
-   <span data-ttu-id="34950-239">DbActivitiesSample という名前のデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="34950-239">Creates a database called DbActivitiesSample.</span></span>  
  
-   <span data-ttu-id="34950-240">Roles テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="34950-240">Creates the Roles table.</span></span>  
  
-   <span data-ttu-id="34950-241">Employees テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="34950-241">Creates Employees table.</span></span>  
  
-   <span data-ttu-id="34950-242">3 個のレコードを Roles テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="34950-242">Inserts three records into the Roles table.</span></span>  
  
-   <span data-ttu-id="34950-243">12 個のレコードを Employees テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="34950-243">Inserts twelve records into the Employees table.</span></span>  
  
##### <a name="to-run-setupcmd"></a><span data-ttu-id="34950-244">Setup.cmd を実行するには</span><span class="sxs-lookup"><span data-stu-id="34950-244">To run Setup.cmd</span></span>  
  
1.  <span data-ttu-id="34950-245">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="34950-245">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="34950-246">DbActivities サンプル フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="34950-246">Go to the DbActivities sample folder.</span></span>  
  
3.  <span data-ttu-id="34950-247">「Setup.cmd」を入力し、、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="34950-247">Type "setup.cmd" and press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34950-248">Setup.cmd は、ローカル コンピューターの SqlExpress インスタンスにサンプルをインストールしようとします。</span><span class="sxs-lookup"><span data-stu-id="34950-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="34950-249">他の SQL Server インスタンスにインストールする場合は、その新しいインスタンス名を使用して Setup.cmd を編集します。</span><span class="sxs-lookup"><span data-stu-id="34950-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>  
  
##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="34950-250">サンプル データベースをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="34950-250">To uninstall the sample database</span></span>  
  
1.  <span data-ttu-id="34950-251">コマンド プロンプトで、サンプル フォルダーから Cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="34950-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>  
  
##### <a name="to-run-the-sample"></a><span data-ttu-id="34950-252">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="34950-252">To run the sample</span></span>  
  
1.  <span data-ttu-id="34950-253">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="34950-253">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]</span></span>  
  
2.  <span data-ttu-id="34950-254">ソリューションをコンパイルするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="34950-254">To compile the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="34950-255">Ctrl キーを押しながら F5 キーを押して、サンプルをデバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="34950-255">To run the sample without debugging, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="34950-256">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="34950-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34950-257">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="34950-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="34950-258">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="34950-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34950-259">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="34950-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
