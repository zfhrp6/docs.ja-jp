---
title: "チュートリアル : 型プロバイダーを使用した SQL データベースへのアクセス (F#)"
description: "F# 3.0 では、SqlDataConnection (LINQ to SQL) 型プロバイダーを使用して、ライブ データベース接続がある場合は、SQL データベースの型を生成する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: 7177eca33ded712308bbc6198040d833b7364d55
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a><span data-ttu-id="cd910-104">チュートリアル : 型プロバイダーを使用した SQL データベースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="cd910-104">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="cd910-105">このガイドでは、f# 3.0 用に作成された、更新されます。</span><span class="sxs-lookup"><span data-stu-id="cd910-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="cd910-106">最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](http://fsharp.github.io/FSharp.Data/) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd910-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="cd910-107">API リファレンス リンクで msdn を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd910-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="cd910-108">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="cd910-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="cd910-109">このチュートリアルでは、データベースへのライブ接続がある場合は、SQL データベースでデータの型を生成する f# 3.0 で提供される SqlDataConnection (LINQ to SQL) 型プロバイダーを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd910-109">This walkthrough explains how to use the SqlDataConnection (LINQ to SQL) type provider that is available in F# 3.0 to generate types for data in a SQL database when you have a live connection to a database.</span></span> <span data-ttu-id="cd910-110">場合は、データベースへのライブ接続することはありませんが、LINQ to SQL スキーマ ファイル (DBML ファイル) を参照してください。[チュートリアル: DBML ファイルから生成する f# 型](generating-fsharp-types-from-dbml.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd910-110">If you do not have a live connection to a database, but you do have a LINQ to SQL schema file (DBML file), see [Walkthrough: Generating F# Types from a DBML File](generating-fsharp-types-from-dbml.md).</span></span>

<span data-ttu-id="cd910-111">このチュートリアルでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cd910-111">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="cd910-112">これらのタスクは、チュートリアルでは成功するには、この順序で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd910-112">These tasks must be performed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="cd910-113">テスト データベースを準備します。</span><span class="sxs-lookup"><span data-stu-id="cd910-113">Preparing a test database</span></span>

- <span data-ttu-id="cd910-114">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="cd910-114">Creating the project</span></span>

- <span data-ttu-id="cd910-115">型プロバイダーを設定します。</span><span class="sxs-lookup"><span data-stu-id="cd910-115">Setting up a type provider</span></span>

- <span data-ttu-id="cd910-116">データの照会</span><span class="sxs-lookup"><span data-stu-id="cd910-116">Querying the data</span></span>

- <span data-ttu-id="cd910-117">Null 許容フィールドの操作</span><span class="sxs-lookup"><span data-stu-id="cd910-117">Working with nullable fields</span></span>

- <span data-ttu-id="cd910-118">ストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="cd910-118">Calling a stored procedure</span></span>

- <span data-ttu-id="cd910-119">データベースの更新</span><span class="sxs-lookup"><span data-stu-id="cd910-119">Updating the database</span></span>

- <span data-ttu-id="cd910-120">TRANSACT-SQL コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="cd910-120">Executing Transact-SQL code</span></span>

- <span data-ttu-id="cd910-121">完全なデータ コンテキストを使用してください。</span><span class="sxs-lookup"><span data-stu-id="cd910-121">Using the full data context</span></span>

- <span data-ttu-id="cd910-122">データの削除</span><span class="sxs-lookup"><span data-stu-id="cd910-122">Deleting data</span></span>

- <span data-ttu-id="cd910-123">必要に応じて、テスト データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd910-123">Create a test database (as needed)</span></span>

## <a name="preparing-a-test-database"></a><span data-ttu-id="cd910-124">テスト データベースを準備します。</span><span class="sxs-lookup"><span data-stu-id="cd910-124">Preparing a Test Database</span></span>
<span data-ttu-id="cd910-125">SQL Server を実行するサーバーでは、テスト目的でデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd910-125">On a server that's running SQL Server, create a database for testing purposes.</span></span> <span data-ttu-id="cd910-126">データベースを使用するセクションでは、このページの下部にあるスクリプトを作成する[テスト データベースを作成する](#creating-a-test-database)これを行う。</span><span class="sxs-lookup"><span data-stu-id="cd910-126">You can use the database create script at the bottom of this page in the section [Creating a test database](#creating-a-test-database) to do this.</span></span>


#### <a name="to-prepare-a-test-database"></a><span data-ttu-id="cd910-127">テスト データベースを準備するには</span><span class="sxs-lookup"><span data-stu-id="cd910-127">To prepare a test database</span></span>

<span data-ttu-id="cd910-128">MyDatabase 作成スクリプトを実行するには、開く、**ビュー**  メニューを選択し**SQL Server オブジェクト エクスプ ローラー**かを選択して、ctrl キーを押しながら\,ctrl キーを押しながら S キー。</span><span class="sxs-lookup"><span data-stu-id="cd910-128">To run the MyDatabase Create Script, open the **View** menu, and then choose **SQL Server Object Explorer** or choose the Ctrl+\, Ctrl+S keys.</span></span> <span data-ttu-id="cd910-129">**SQL Server オブジェクト エクスプ ローラー**ウィンドウで、適切なインスタンスのショートカット メニューを開き、選択**新しいクエリ**、このページの下部にあるスクリプトをコピーし、エディターにスクリプトを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="cd910-129">In **SQL Server Object Explorer** window, open the shortcut menu for the appropriate instance, choose **New Query**, copy the script at the bottom of this page, and then paste the script into the editor.</span></span> <span data-ttu-id="cd910-130">SQL スクリプトを実行するには、三角形のシンボルでは、ツールバーのアイコンを選択するか、ctrl キーを押しながら Q キーを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd910-130">To run the SQL script, choose the toolbar icon with the triangular symbol, or choose the Ctrl+Q keys.</span></span> <span data-ttu-id="cd910-131">詳細については**SQL Server オブジェクト エクスプ ローラー**を参照してください[接続されているデータベース開発](https://msdn.microsoft.com/library/hh272679(VS.103).aspx)です。</span><span class="sxs-lookup"><span data-stu-id="cd910-131">For more information about **SQL Server Object Explorer**, see [Connected Database Development](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span></span>


## <a name="creating-the-project"></a><span data-ttu-id="cd910-132">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="cd910-132">Creating the project</span></span>
<span data-ttu-id="cd910-133">次に、f# アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd910-133">Next, you create an F# application project.</span></span>


#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="cd910-134">プロジェクトを作成し、設定するには</span><span class="sxs-lookup"><span data-stu-id="cd910-134">To create and set up the project</span></span>

1. <span data-ttu-id="cd910-135">新しい f# アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd910-135">Create a new F# Application project.</span></span>

2. <span data-ttu-id="cd910-136">参照を追加[FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3)、だけでなく`System.Data`、および`System.Data.Linq`です。</span><span class="sxs-lookup"><span data-stu-id="cd910-136">Add references to [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), as well as `System.Data`, and `System.Data.Linq`.</span></span>

3. <span data-ttu-id="cd910-137">F# コード ファイル Program.fs の先頭に次のコード行を追加することで、適切な名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="cd910-137">Open the appropriate namespaces by adding the following lines of code to the top of your F# code file Program.fs.</span></span>

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. <span data-ttu-id="cd910-138">ほとんど f# のプログラムと同様、コードを実行するには、コンパイル済みのプログラムとしては、このチュートリアルでまたはスクリプトとして対話形式で実行することができます。</span><span class="sxs-lookup"><span data-stu-id="cd910-138">As with most F# programs, you can execute the code in this walkthrough as a compiled program, or you can run it interactively as a script.</span></span> <span data-ttu-id="cd910-139">スクリプトを使用する場合は、ショートカット メニューを開き、プロジェクト ノードを選択**新しい項目の追加**f# スクリプト ファイルを追加し、スクリプトに各手順でコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="cd910-139">If you prefer to use scripts, open the shortcut menu for the project node, select **Add New Item**, add an F# script file, and add the code in each step to the script.</span></span> <span data-ttu-id="cd910-140">アセンブリの参照を読み込むファイルの上部にある次の行を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd910-140">You will need to add the following lines at the top of the file to load the assembly references.</span></span>

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  <span data-ttu-id="cd910-141">それを追加し、f# Interactive で実行するには、Alt + enter キーを押すと、各コード ブロックを選択できます。</span><span class="sxs-lookup"><span data-stu-id="cd910-141">You can then select each block of code as you add it and press Alt+Enter to run it in F# Interactive.</span></span>

## <a name="setting-up-a-type-provider"></a><span data-ttu-id="cd910-142">型プロバイダーを設定します。</span><span class="sxs-lookup"><span data-stu-id="cd910-142">Setting up a type provider</span></span>
<span data-ttu-id="cd910-143">この手順では、データベース スキーマの型プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd910-143">In this step, you create a type provider for your database schema.</span></span>


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a><span data-ttu-id="cd910-144">データベースに直接接続から型プロバイダーを設定するには</span><span class="sxs-lookup"><span data-stu-id="cd910-144">To set up the type provider from a direct database connection</span></span>

<span data-ttu-id="cd910-145">型プロバイダーを使用して SQL データベースの照会に使用できる型を作成するために必要なコードの 2 つの重要な線があります。</span><span class="sxs-lookup"><span data-stu-id="cd910-145">There are two critical lines of code that you need in order to create the types that you can use to query a SQL database using the type provider.</span></span> <span data-ttu-id="cd910-146">最初に、型プロバイダーがインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="cd910-146">First, you instantiate the type provider.</span></span> <span data-ttu-id="cd910-147">これを行うには、作成、型の省略形の外観、`SqlDataConnection`静的ジェネリック パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd910-147">To do this, create what looks like a type abbreviation for a `SqlDataConnection` with a static generic parameter.</span></span> <span data-ttu-id="cd910-148">`SqlDataConnection`SQL 型のプロバイダーと混同しないで`SqlConnection`となる型 ADO.NET プログラミングで使用します。</span><span class="sxs-lookup"><span data-stu-id="cd910-148">`SqlDataConnection` is a SQL type provider, and should not be confused with `SqlConnection` type that is used in ADO.NET programming.</span></span> <span data-ttu-id="cd910-149">、に接続するデータベースが存在して接続文字列がある場合は、次のコードを使用して、型プロバイダーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cd910-149">If you have a database that you want to connect to, and have a connection string, use the following code to invoke the type provider.</span></span> <span data-ttu-id="cd910-150">指定された文字列の例の独自の接続文字列を置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="cd910-150">Substitute your own connection string for the example string given.</span></span> <span data-ttu-id="cd910-151">たとえば、MYSERVER とデータベース インスタンスはインスタンス、データベース名が MyDatabase であり、データベース、接続文字列にアクセスする Windows 認証を使用する場合は、サーバーとなる場合は、次のコード例で指定します。</span><span class="sxs-lookup"><span data-stu-id="cd910-151">For example, if your server is MYSERVER and the database instance is INSTANCE, the database name is MyDatabase, and you want to use Windows Authentication to access the database, then the connection string would be as given in the following example code.</span></span>

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

<span data-ttu-id="cd910-152">これで、型を持つ`dbSchema`、データベース テーブルを表すすべての生成された型を含む親型です。</span><span class="sxs-lookup"><span data-stu-id="cd910-152">Now you have a type, `dbSchema`, which is a parent type that contains all the generated types that represent database tables.</span></span> <span data-ttu-id="cd910-153">また、オブジェクトがある`db`を持つメンバーとして、データベース内のすべてのテーブルです。</span><span class="sxs-lookup"><span data-stu-id="cd910-153">You also have an object, `db`, which has as its members all the tables in the database.</span></span> <span data-ttu-id="cd910-154">テーブル名は、プロパティと、これらのプロパティの種類、f# コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd910-154">The table names are properties, and the type of these properties is generated by the F# compiler.</span></span> <span data-ttu-id="cd910-155">入れ子にされた型として型自体が表示される`dbSchema.ServiceTypes`です。</span><span class="sxs-lookup"><span data-stu-id="cd910-155">The types themselves appear as nested types under `dbSchema.ServiceTypes`.</span></span> <span data-ttu-id="cd910-156">したがって、これらのテーブルの行の取得されたデータは、そのテーブルに対して生成された適切な型のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="cd910-156">Therefore, any data retrieved for rows of these tables is an instance of the appropriate type that was generated for that table.</span></span> <span data-ttu-id="cd910-157">型の名前は`ServiceTypes.Table1`します。</span><span class="sxs-lookup"><span data-stu-id="cd910-157">The name of the type is `ServiceTypes.Table1`.</span></span>

<span data-ttu-id="cd910-158">F# 言語が SQL クエリにクエリを解釈する方法を理解しておくための確認を設定する行、`Log`データ コンテキストのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="cd910-158">To familiarize yourself with how the F# language interprets queries into SQL queries, review the line that sets the `Log` property on the data context.</span></span>

<span data-ttu-id="cd910-159">型プロバイダーによって作成された型をさらに調査するには、するには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="cd910-159">To further explore the types created by the type provider, add the following code.</span></span>

```fsharp
let table1 = db.Table1
```

<span data-ttu-id="cd910-160">ポインターを合わせる`table1`その型を表示します。</span><span class="sxs-lookup"><span data-stu-id="cd910-160">Hover over `table1` to see its type.</span></span> <span data-ttu-id="cd910-161">その型は`System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>`汎用引数の場合、各行の型が生成された型であることを示しますと`dbSchema.ServiceTypes.Table1`です。</span><span class="sxs-lookup"><span data-stu-id="cd910-161">Its type is `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` and the generic argument implies that the type of each row is the generated type, `dbSchema.ServiceTypes.Table1`.</span></span> <span data-ttu-id="cd910-162">コンパイラは、データベースのテーブルごとに、類似する型を作成します。</span><span class="sxs-lookup"><span data-stu-id="cd910-162">The compiler creates a similar type for each table in the database.</span></span>

## <a name="querying-the-data"></a><span data-ttu-id="cd910-163">データの照会</span><span class="sxs-lookup"><span data-stu-id="cd910-163">Querying the data</span></span>
<span data-ttu-id="cd910-164">このステップでは、f# クエリ式を使用してクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="cd910-164">In this step, you write a query using F# query expressions.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="cd910-165">データを照会するには</span><span class="sxs-lookup"><span data-stu-id="cd910-165">To query the data</span></span>

1. <span data-ttu-id="cd910-166">今すぐデータベースにそのテーブルに対してクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd910-166">Now create a query for that table in the database.</span></span> <span data-ttu-id="cd910-167">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="cd910-167">Add the following code.</span></span>

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  <span data-ttu-id="cd910-168">単語の外観`query`クエリ式では、一般的なデータベース クエリのような結果のコレクションを生成する計算式の型であることを示します。</span><span class="sxs-lookup"><span data-stu-id="cd910-168">The appearance of the word `query` indicates that this is a query expression, a type of computation expression that generates a collection of results similar of a typical database query.</span></span> <span data-ttu-id="cd910-169">クエリ上でマウス ポインターを移動する場合のインスタンスであることを確認は[Linq.QueryBuilder クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d)、クエリ コンピュテーション式を定義する型。</span><span class="sxs-lookup"><span data-stu-id="cd910-169">If you hover over query, you will see that it is an instance of [Linq.QueryBuilder Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), a type that defines the query computation expression.</span></span> <span data-ttu-id="cd910-170">ポインターを合わせる場合`query1`のインスタンスであることがわかります`System.Linq.IQueryable`です。</span><span class="sxs-lookup"><span data-stu-id="cd910-170">If you hover over `query1`, you will see that it is an instance of `System.Linq.IQueryable`.</span></span> <span data-ttu-id="cd910-171">名前からわかるように、 `System.Linq.IQueryable` 、照会するクエリの結果ではなくデータを表します。</span><span class="sxs-lookup"><span data-stu-id="cd910-171">As the name suggests, `System.Linq.IQueryable` represents data that may be queried, not the result of a query.</span></span> <span data-ttu-id="cd910-172">クエリとは、クエリが評価されるときに、データベースは、のみことを意味の照会、レイジー評価される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cd910-172">A query is subject to lazy evaluation, which means that the database is only queried when the query is evaluated.</span></span> <span data-ttu-id="cd910-173">最後の行を使用してクエリに渡します`Seq.iter`です。</span><span class="sxs-lookup"><span data-stu-id="cd910-173">The final line passes the query through `Seq.iter`.</span></span> <span data-ttu-id="cd910-174">クエリは、列挙可能なシーケンスのように繰り返し処理される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cd910-174">Queries are enumerable and may be iterated like sequences.</span></span> <span data-ttu-id="cd910-175">詳細については、次を参照してください。[クエリ式](../../language-reference/query-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd910-175">For more information, see [Query Expressions](../../language-reference/query-expressions.md).</span></span>

2. <span data-ttu-id="cd910-176">クエリにクエリ演算子を追加します。</span><span class="sxs-lookup"><span data-stu-id="cd910-176">Now add a query operator to the query.</span></span> <span data-ttu-id="cd910-177">複雑なクエリを構築するために使用できる利用できるクエリ演算子の数があります。</span><span class="sxs-lookup"><span data-stu-id="cd910-177">There are a number of query operators available that you can use to construct more complex queries.</span></span> <span data-ttu-id="cd910-178">この例では、クエリ変数を排除し、代わりに、パイプライン演算子を使用することができますも示しています。</span><span class="sxs-lookup"><span data-stu-id="cd910-178">This example also shows that you can eliminate the query variable and use a pipeline operator instead.</span></span>

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. <span data-ttu-id="cd910-179">2 つのテーブルの結合を使用した複雑なクエリを追加します。</span><span class="sxs-lookup"><span data-stu-id="cd910-179">Add a more complex query with a join of two tables.</span></span>

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. <span data-ttu-id="cd910-180">実際のコードでクエリ内のパラメーターは通常の値または変数、コンパイル時間ではなく定数です。</span><span class="sxs-lookup"><span data-stu-id="cd910-180">In real-world code, the parameters in your query are usually values or variables, not compile-time constants.</span></span> <span data-ttu-id="cd910-181">パラメーターを受け取るし、値 10 をその関数を呼び出している関数内のクエリをラップする次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="cd910-181">Add the following code that wraps a query in a function that takes a parameter, and then calls that function with the value 10.</span></span>

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a><span data-ttu-id="cd910-182">Null 許容フィールドの操作</span><span class="sxs-lookup"><span data-stu-id="cd910-182">Working with nullable fields</span></span>
<span data-ttu-id="cd910-183">データベースでは、フィールドは多くの場合、null 値を許可します。</span><span class="sxs-lookup"><span data-stu-id="cd910-183">In databases, fields often allow null values.</span></span> <span data-ttu-id="cd910-184">.NET 型システムでは、使用可能な値として null をそれらの型を持たないため null 値を許容するデータの通常の数値データ型を使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="cd910-184">In the .NET type system, you cannot use the ordinary numerical data types for data that allows nulls because those types do not have null as a possible value.</span></span> <span data-ttu-id="cd910-185">これらの値がのインスタンスによって表されるため、`System.Nullable`型です。</span><span class="sxs-lookup"><span data-stu-id="cd910-185">Therefore, these values are represented by instances of `System.Nullable` type.</span></span> <span data-ttu-id="cd910-186">このようなフィールドの値フィールドの名前で直接アクセスする、代わりに、追加の手順を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd910-186">Instead of accessing the value of such fields directly with the name of the field, you need to add some extra steps.</span></span> <span data-ttu-id="cd910-187">使用することができます、`System.Nullable.Value`プロパティを null 許容型の基になる値にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cd910-187">You can use the `System.Nullable.Value` property to access the underlying value of a nullable type.</span></span> <span data-ttu-id="cd910-188">`System.Nullable.Value`プロパティは、オブジェクトが値ではなく null の場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="cd910-188">The `System.Nullable.Value` property throws an exception if the object is null rather than having a value.</span></span> <span data-ttu-id="cd910-189">使用することができます、`System.Nullable.HasValue`値が存在するかどうかを使用するブール型のメソッド`System.Nullable.GetValueOrDefault()`を常に、実際の値があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cd910-189">You can use the `System.Nullable.HasValue` Boolean method to determine if a value exists, or use `System.Nullable.GetValueOrDefault()` to ensure that you have an actual value in all cases.</span></span> <span data-ttu-id="cd910-190">使用する場合`System.Nullable.GetValueOrDefault()`し、データベースで null 値がある、置き換えられる文字列型の空の文字列などの値、整数型の場合は 0 またはフローティング 0.0 のポイントの種類。</span><span class="sxs-lookup"><span data-stu-id="cd910-190">If you use `System.Nullable.GetValueOrDefault()` and there is a null in the database, then it is replaced with a value such as an empty string for string types, 0 for integral types or 0.0 for floating point types.</span></span>

<span data-ttu-id="cd910-191">Null 許容の値の等値テストや比較を実行する必要がある場合、`where`クエリ内の句については、null 許容の演算子を使用することができます、 [Linq.NullableOperators モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="cd910-191">When you need to perform equality tests or comparisons on nullable values in a `where` clause in a query, you can use the nullable operators found in the [Linq.NullableOperators Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span></span> <span data-ttu-id="cd910-192">これらは通常の比較演算子と同様、 `=`、 `>`、`<=`など、点を除いて、疑問符 (?) が表示される、演算子の右または左に、null 許容の値がします。</span><span class="sxs-lookup"><span data-stu-id="cd910-192">These are like the regular comparison operators `=`, `>`, `<=`, and so on, except that a question mark appears on the left or right of the operator where the nullable values are.</span></span> <span data-ttu-id="cd910-193">演算子など、`>?`が、大きい-より右側の null 許容の値を持つ演算子。</span><span class="sxs-lookup"><span data-stu-id="cd910-193">For example, the operator `>?` is a greater-than operator with a nullable value on the right.</span></span> <span data-ttu-id="cd910-194">これらの演算子の動作方法は、式の両辺が null の場合に、式が評価`false`です。</span><span class="sxs-lookup"><span data-stu-id="cd910-194">The way these operators work is that if either side of the expression is null, the expression evaluates to `false`.</span></span> <span data-ttu-id="cd910-195">`where`句、一般につまり null フィールドを含む行が選択されていない、クエリの結果では返されません。</span><span class="sxs-lookup"><span data-stu-id="cd910-195">In a `where` clause, this generally means that the rows that contain null fields are not selected and not returned in the query results.</span></span>


#### <a name="to-work-with-nullable-fields"></a><span data-ttu-id="cd910-196">Null 値許容フィールドを使用するには</span><span class="sxs-lookup"><span data-stu-id="cd910-196">To work with nullable fields</span></span>

<span data-ttu-id="cd910-197">次のコードは、null 許容の値の操作を示しています。あると想定**TestData1**整数フィールドであり、null 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="cd910-197">The following code shows working with nullable values; assume that **TestData1** is an integer field that allows nulls.</span></span>

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="cd910-198">ストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="cd910-198">Calling a stored procedure</span></span>
<span data-ttu-id="cd910-199">データベースでストアド プロシージャは、f# から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="cd910-199">Any stored procedures on the database can be called from F#.</span></span> <span data-ttu-id="cd910-200">Static パラメーターを設定する必要があります`StoredProcedures`に`true`で型プロバイダーのインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="cd910-200">You must set the static parameter `StoredProcedures` to `true` in the type provider instantiation.</span></span> <span data-ttu-id="cd910-201">型プロバイダー`SqlDataConnection`生成される型の構成に使用できるいくつかの静的メソッドを格納します。</span><span class="sxs-lookup"><span data-stu-id="cd910-201">The type provider `SqlDataConnection` contains several static methods that you can use to configure the types that are generated.</span></span> <span data-ttu-id="cd910-202">これらの詳細については、次を参照してください。 [SqlDataConnection 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="cd910-202">For a complete description of these, see [SqlDataConnection Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span></span> <span data-ttu-id="cd910-203">データ コンテキスト型のメソッドでは、各ストアド プロシージャが生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd910-203">A method on the data context type is generated for each stored procedure.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="cd910-204">ストアド プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="cd910-204">To call a stored procedure</span></span>

<span data-ttu-id="cd910-205">ストアド プロシージャが null 許容であるパラメーターを受け取る場合は、適切なを渡す必要があります。`System.Nullable`値。</span><span class="sxs-lookup"><span data-stu-id="cd910-205">If the stored procedures takes parameters that are nullable, you need to pass an appropriate `System.Nullable` value.</span></span> <span data-ttu-id="cd910-206">スカラーまたはテーブルを返すストアド プロシージャ メソッドの戻り値は`System.Data.Linq.ISingleResult`、返されるデータにアクセスできるようにするプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cd910-206">The return value of a stored procedure method that returns a scalar or a table is `System.Data.Linq.ISingleResult`, which contains properties that enable you to access the returned data.</span></span> <span data-ttu-id="cd910-207">型引数を`System.Data.Linq.ISingleResult`特定のプロシージャに依存していても、型プロバイダーを生成する型のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="cd910-207">The type argument for `System.Data.Linq.ISingleResult` depends on the specific procedure and is also one of the types that the type provider generates.</span></span> <span data-ttu-id="cd910-208">という名前のストアド プロシージャの`Procedure1`、型が`Procedure1Result`です。</span><span class="sxs-lookup"><span data-stu-id="cd910-208">For a stored procedure named `Procedure1`, the type is `Procedure1Result`.</span></span> <span data-ttu-id="cd910-209">種類`Procedure1Result`名前を含む列、返されるテーブルにして、またはスカラー値を返すストアド プロシージャの戻り値を表します。</span><span class="sxs-lookup"><span data-stu-id="cd910-209">The type `Procedure1Result` contains the names of the columns in a returned table, or, for a stored procedure that returns a scalar value, it represents the return value.</span></span>

<span data-ttu-id="cd910-210">次のコードがあるものと、プロシージャ`Procedure1`パラメーターとして 2 つの null 許容型整数を受け取り、データベースをという名前の列を返すクエリが実行されて`TestData1`整数を返します。</span><span class="sxs-lookup"><span data-stu-id="cd910-210">The following code assumes that there is a procedure `Procedure1` on the database that takes two nullable integers as parameters, runs a query that returns a column named `TestData1`, and returns an integer.</span></span>

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a><span data-ttu-id="cd910-211">データベースの更新</span><span class="sxs-lookup"><span data-stu-id="cd910-211">Updating the database</span></span>
<span data-ttu-id="cd910-212">LINQ DataContext 型には、生成された型と完全に型指定された方法でトランザクションのデータベースの更新を実行するが簡単にするメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cd910-212">The LINQ DataContext type contains methods that make it easier to perform transacted database updates in a fully typed fashion with the generated types.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="cd910-213">データベースを更新するには</span><span class="sxs-lookup"><span data-stu-id="cd910-213">To update the database</span></span>

1. <span data-ttu-id="cd910-214">次のコードでは、いくつかの行がデータベースに追加されます。</span><span class="sxs-lookup"><span data-stu-id="cd910-214">In the following code, several rows are added to the database.</span></span> <span data-ttu-id="cd910-215">使用することができますのみ行を追加する場合`System.Data.Linq.Table.InsertOnSubmit()`を追加する新しい行を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd910-215">If you are only adding a row, you can use `System.Data.Linq.Table.InsertOnSubmit()` to specify the new row to add.</span></span> <span data-ttu-id="cd910-216">複数の行を挿入する場合は、コレクションと呼び出しに配置するにする必要があります`System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`です。</span><span class="sxs-lookup"><span data-stu-id="cd910-216">If you are inserting multiple rows, you should put them into a collection and call `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span></span> <span data-ttu-id="cd910-217">これらのメソッドのいずれかを呼び出すときに、データベースはすぐに変更されません。</span><span class="sxs-lookup"><span data-stu-id="cd910-217">When you call either of these methods, the database is not immediately changed.</span></span> <span data-ttu-id="cd910-218">呼び出す必要があります`System.Data.Linq.DataContext.SubmitChanges`を実際には、変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="cd910-218">You must call `System.Data.Linq.DataContext.SubmitChanges` to actually commit the changes.</span></span> <span data-ttu-id="cd910-219">呼び出しをする前に行う操作は既定では、`System.Data.Linq.DataContext.SubmitChanges`同じトランザクションの一部では暗黙的にします。</span><span class="sxs-lookup"><span data-stu-id="cd910-219">By default, everything that you do before you call `System.Data.Linq.DataContext.SubmitChanges` is implicitly part of the same transaction.</span></span>

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. <span data-ttu-id="cd910-220">今すぐ削除操作を呼び出すことによって、行をクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="cd910-220">Now clean up the rows by calling a delete operation.</span></span>

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a><span data-ttu-id="cd910-221">TRANSACT-SQL コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="cd910-221">Executing Transact-SQL code</span></span>
<span data-ttu-id="cd910-222">TRANSACT-SQL を使用して直接指定することも、`System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])`メソッドを`DataContext`クラスです。</span><span class="sxs-lookup"><span data-stu-id="cd910-222">You can also specify Transact-SQL directly by using the `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` method on the `DataContext` class.</span></span>


#### <a name="to-execute-custom-sql-commands"></a><span data-ttu-id="cd910-223">カスタムの SQL コマンドを実行するには</span><span class="sxs-lookup"><span data-stu-id="cd910-223">To execute custom SQL commands</span></span>

<span data-ttu-id="cd910-224">次のコードでは、テーブルにレコードを挿入し、テーブルからレコードを削除する SQL コマンドを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cd910-224">The following code shows how to send SQL commands to insert a record into a table and also to delete a record from a table.</span></span>

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a><span data-ttu-id="cd910-225">完全なデータ コンテキストを使用してください。</span><span class="sxs-lookup"><span data-stu-id="cd910-225">Using the full data context</span></span>
<span data-ttu-id="cd910-226">前の例で、`GetDataContext`と呼ばれるものを取得するメソッドが使用された、*簡易データ コンテキスト*データベース スキーマです。</span><span class="sxs-lookup"><span data-stu-id="cd910-226">In the previous examples, the `GetDataContext` method was used to get what is called the *simplified data context* for the database schema.</span></span> <span data-ttu-id="cd910-227">簡易データ コンテキストは、できるだけ多くのメンバーがないために、クエリを構築するときに使用する簡単です。</span><span class="sxs-lookup"><span data-stu-id="cd910-227">The simplified data context is easier to use when you are constructing queries because there are not as many members available.</span></span> <span data-ttu-id="cd910-228">そのため、IntelliSense でプロパティを参照するときは、テーブルおよびストアド プロシージャなど、データベースの構造に集中できます。</span><span class="sxs-lookup"><span data-stu-id="cd910-228">Therefore, when you browse the properties in IntelliSense, you can focus on the database structure, such as the tables and stored procedures.</span></span> <span data-ttu-id="cd910-229">ただし、簡易データ コンテキストで行うことができますに制限があります。</span><span class="sxs-lookup"><span data-stu-id="cd910-229">However, there is a limit to what you can do with the simplified data context.</span></span> <span data-ttu-id="cd910-230">その他のアクションを実行する機能を提供する完全なデータ コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="cd910-230">A full data context that provides the ability to perform other actions.</span></span> <span data-ttu-id="cd910-231">使用可能なこの内にある、`ServiceTypes`の名前を持つ、 *DataContext* static パラメーター指定した場合。</span><span class="sxs-lookup"><span data-stu-id="cd910-231">is also available This is located in the `ServiceTypes` and has the name of the *DataContext* static parameter if you provided it.</span></span> <span data-ttu-id="cd910-232">指定しなかった場合、その他の入力に基づく SqlMetal.exe によって、データ コンテキスト型の名前が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd910-232">If you did not provide it, the name of the data context type is generated for you by SqlMetal.exe based on the other input.</span></span> <span data-ttu-id="cd910-233">完全データ コンテキストが継承`System.Data.Linq.DataContext`など ADO.NET データ型への参照を含む、基底クラスのメンバーを公開し、`Connection`オブジェクトなどのメソッド`System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])`と`System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])`SQL では、クエリの作成に使用できます。明示的にトランザクションを処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="cd910-233">The full data context inherits from `System.Data.Linq.DataContext` and exposes the members of its base class, including references to ADO.NET data types such as the `Connection` object, methods such as `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` and `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` that you can use to write queries in SQL, and also a means to work with transactions explicitly.</span></span>


#### <a name="to-use-the-full-data-context"></a><span data-ttu-id="cd910-234">完全データ コンテキストを使用するには</span><span class="sxs-lookup"><span data-stu-id="cd910-234">To use the full data context</span></span>

<span data-ttu-id="cd910-235">次のコードは、完全データ コンテキスト オブジェクトを取得して、データベースに対して直接コマンドを実行する使用を示します。</span><span class="sxs-lookup"><span data-stu-id="cd910-235">The following code demonstrates getting a full data context object and using it to execute commands directly against the database.</span></span> <span data-ttu-id="cd910-236">この場合、2 つのコマンドは、同じトランザクションの一部として実行されます。</span><span class="sxs-lookup"><span data-stu-id="cd910-236">In this case, two commands are executed as part of the same transaction.</span></span>

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a><span data-ttu-id="cd910-237">データの削除</span><span class="sxs-lookup"><span data-stu-id="cd910-237">Deleting data</span></span>
<span data-ttu-id="cd910-238">この手順では、データ テーブルから行を削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cd910-238">This step shows you how to delete rows from a data table.</span></span>


#### <a name="to-delete-rows-from-the-database"></a><span data-ttu-id="cd910-239">データベースから行を削除するには</span><span class="sxs-lookup"><span data-stu-id="cd910-239">To delete rows from the database</span></span>

<span data-ttu-id="cd910-240">これで、いずれかをクリーンアップするのインスタンスを指定したテーブルから行を削除する関数を記述して行を追加、`System.Data.Linq.Table`クラスです。</span><span class="sxs-lookup"><span data-stu-id="cd910-240">Now, clean up any added rows by writing a function that deletes rows from a specified table, an instance of the `System.Data.Linq.Table` class.</span></span> <span data-ttu-id="cd910-241">削除するすべての行を検索するクエリを記述しに、クエリの結果をパイプ、`deleteRows`関数。</span><span class="sxs-lookup"><span data-stu-id="cd910-241">Then write a query to find all the rows that you want to delete, and pipe the results of the query into the `deleteRows` function.</span></span> <span data-ttu-id="cd910-242">このコードでは、関数の引数の部分的な適用を提供する機能を活用します。</span><span class="sxs-lookup"><span data-stu-id="cd910-242">This code takes advantage of the ability to provide partial application of function arguments.</span></span>

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a><span data-ttu-id="cd910-243">テスト データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd910-243">Creating a test database</span></span>
<span data-ttu-id="cd910-244">このセクションでは、このチュートリアルを使用して、テスト データベースを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cd910-244">This section shows you how to set up the test database to use in this walkthrough.</span></span>

<span data-ttu-id="cd910-245">いくつかの方法でデータベースを変更する場合は、型プロバイダーをリセットする必要が注意してください。</span><span class="sxs-lookup"><span data-stu-id="cd910-245">Note that if you alter the database in some way, you will have to reset the type provider.</span></span> <span data-ttu-id="cd910-246">型プロバイダーをリセットするには、再構築または型プロバイダーを含むプロジェクトをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="cd910-246">To reset the type provider, rebuild or clean the project that contains the type provider.</span></span>


#### <a name="to-create-the-test-database"></a><span data-ttu-id="cd910-247">テスト データベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="cd910-247">To create the test database</span></span>

1. <span data-ttu-id="cd910-248">**サーバー エクスプ ローラー**、ショートカット メニューを開き、**データ接続** ノードを選択し、**接続の追加**です。</span><span class="sxs-lookup"><span data-stu-id="cd910-248">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and choose **Add Connection**.</span></span> <span data-ttu-id="cd910-249">**接続の追加** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd910-249">The **Add Connection** dialog box appears.</span></span>

2. <span data-ttu-id="cd910-250">**サーバー名**ボックスでする管理アクセス権を持つ、SQL Server のインスタンスの名前を指定するか、サーバーへのアクセスがない (localdb\v11.0) を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd910-250">In the **Server name** box, specify the name of an instance of SQL Server that you have administrative access to, or if you do not have access to a server, specify (localdb\v11.0).</span></span> <span data-ttu-id="cd910-251">SQL Express LocalDB は、コンピューターで開発およびテストの軽量のデータベース サーバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="cd910-251">SQL Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="cd910-252">新しいノードが作成された**サーバー エクスプ ローラー** **データ接続**です。</span><span class="sxs-lookup"><span data-stu-id="cd910-252">A new node is created in **Server Explorer** under **Data Connections**.</span></span> <span data-ttu-id="cd910-253">LocalDB の詳細については、次を参照してください。[チュートリアル: Visual Studio でのローカル データベース ファイルの作成](https://msdn.microsoft.com/library/ms233763.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="cd910-253">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>

3. <span data-ttu-id="cd910-254">新しい接続ノードのショートカット メニューを開き、選択**新しいクエリ**です。</span><span class="sxs-lookup"><span data-stu-id="cd910-254">Open the shortcut menu for the new connection node, and select **New Query**.</span></span>

4. <span data-ttu-id="cd910-255">次の SQL スクリプトをコピー、クエリ エディターに貼り付けますおよびを選択し、 **Execute**ツールバーのボタンまたは Ctrl + shift キーを押しながら E キーを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd910-255">Copy the following SQL script, paste it into the query editor, and then choose the **Execute** button on the toolbar or choose the Ctrl+Shift+E keys.</span></span>

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a><span data-ttu-id="cd910-256">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd910-256">See Also</span></span>
[<span data-ttu-id="cd910-257">型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="cd910-257">Type Providers</span></span>](index.md)

[<span data-ttu-id="cd910-258">SqlDataConnection 型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="cd910-258">SqlDataConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="cd910-259">チュートリアル: DBML ファイルからの f# 型の生成</span><span class="sxs-lookup"><span data-stu-id="cd910-259">Walkthrough: Generating F# Types from a DBML File</span></span>](generating-fsharp-types-from-dbml.md)

[<span data-ttu-id="cd910-260">クエリ式</span><span class="sxs-lookup"><span data-stu-id="cd910-260">Query Expressions</span></span>](../../language-reference/query-expressions.md)

[<span data-ttu-id="cd910-261">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cd910-261">LINQ to SQL</span></span>](../../../../docs/framework/data/adonet/sql/linq/index.md)

[<span data-ttu-id="cd910-262">SqlMetal.exe &#40;です。コード生成ツール &#41;</span><span class="sxs-lookup"><span data-stu-id="cd910-262">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)
