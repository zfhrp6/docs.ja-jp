---
title: 'チュートリアル : DBML ファイルからの F# 型の生成 (F#)'
description: .Dbml ファイルにエンコード スキーマ情報がある場合、f# 3.0 でのデータベースからデータの f# 型を作成する方法を説明します。
keywords: visual f#, f#, 関数型プログラミング
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 3cd8df9becac0d1a8842eb22e2f772eee6307acf
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a><span data-ttu-id="d3d5f-104">チュートリアル : DBML ファイルからの F# 型の生成</span><span class="sxs-lookup"><span data-stu-id="d3d5f-104">Walkthrough: Generating F# Types from a DBML File</span></span>

> [!NOTE]
<span data-ttu-id="d3d5f-105">このガイドでは、f# 3.0 用に作成された、更新されます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="d3d5f-106">最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](https://fsharp.github.io/FSharp.Data/) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="d3d5f-107">API リファレンス リンクで msdn を実行します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="d3d5f-108">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="d3d5f-109">F# 3.0 に関するこのチュートリアルでは、スキーマ情報を格納する .dbml ファイルにエンコードがある場合、データベースからデータの型を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-109">This walkthrough for F# 3.0 describes how to create types for data from a database when you have schema information encoded in a .dbml file.</span></span> <span data-ttu-id="d3d5f-110">LINQ to SQL では、このファイル形式を使用して、データベース スキーマを表します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-110">LINQ to SQL uses this file format to represent database schema.</span></span> <span data-ttu-id="d3d5f-111">オブジェクト リレーショナル (O/R) のデザイナーを使用して Visual Studio での LINQ to SQL スキーマ ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-111">You can generate a LINQ to SQL schema file in Visual Studio by using the Object Relational (O/R) Designer.</span></span> <span data-ttu-id="d3d5f-112">詳細については、次を参照してください。 [O/r デザイナーの概要](https://msdn.microsoft.com/library/bb384511.aspx)と[LINQ to SQL でのコード生成](../../../../docs/framework/data/adonet/sql/linq/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-112">For more information, see [O/R Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) and [Code Generation in LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>

<span data-ttu-id="d3d5f-113">データベース マークアップ言語 (DBML) 型プロバイダーでは、コンパイル時に静的な接続文字列を指定する必要がなく、データベース スキーマに基づいた型を使用するコードを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-113">The Database Markup Language (DBML) type provider allows you to write code that uses types based on a database schema without requiring you to specify a static connection string at compile time.</span></span> <span data-ttu-id="d3d5f-114">最終のアプリケーションが別のデータベース、別の資格情報、またはよりも、アプリケーションの開発に使用する 1 つの異なる接続文字列に使用することを許可する必要がある場合に便利にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-114">That can be useful if you need to allow for the possibility that the final application will use a different database, different credentials, or a different connection string than the one you use to develop the application.</span></span> <span data-ttu-id="d3d5f-115">コンパイル時に使用できるデータベースに直接接続があり、これは、同じデータベースと資格情報を最終的にビルドされたアプリケーションで使用する場合も、SQLDataConnection 型プロバイダーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-115">If you have a direct database connection that you can use at compile time and this is the same database and credentials that you will eventually use in your built application, you can also use the SQLDataConnection type provider.</span></span> <span data-ttu-id="d3d5f-116">詳細については、次を参照してください。[チュートリアル: 型プロバイダーを使用して SQL データベースへのアクセス](accessing-a-sql-database.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-116">For more information, see [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>

<span data-ttu-id="d3d5f-117">このチュートリアルでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-117">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="d3d5f-118">これらは、チュートリアルでは成功するには、この順序で完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-118">They should be completed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="d3d5f-119">.Dbml ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-119">Creating a .dbml file</span></span>
<br />

- <span data-ttu-id="d3d5f-120">作成、f# プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="d3d5f-120">Creating and setting up an F# project</span></span>
<br />

- <span data-ttu-id="d3d5f-121">型プロバイダーを構成して、型の生成</span><span class="sxs-lookup"><span data-stu-id="d3d5f-121">Configuring the type provider and generating the types</span></span>
<br />

- <span data-ttu-id="d3d5f-122">データベースの照会</span><span class="sxs-lookup"><span data-stu-id="d3d5f-122">Querying the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="d3d5f-123">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d3d5f-123">Prerequisites</span></span>

## <a name="creating-a-dbml-file"></a><span data-ttu-id="d3d5f-124">.Dbml ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-124">Creating a .dbml file</span></span>
<span data-ttu-id="d3d5f-125">場合は、データベースでテストする必要はありません、作成の下部にある指示に従って[チュートリアル: 型プロバイダーを使用して SQL データベースへのアクセス](accessing-a-sql-database.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-125">If you do not have a database to test on, create one by following the instructions at the bottom of [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span> <span data-ttu-id="d3d5f-126">これらの手順を実行する場合は、いくつかの単純なテーブルと、SQL Server 上のストアド プロシージャを含む MyDatabase をという名前のデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-126">If you follow these instructions, you will create a database called MyDatabase that contains a few simple tables and stored procedures on your SQL Server.</span></span>

<span data-ttu-id="d3d5f-127">.Dbml ファイルがある場合、セクションにスキップできます**設定を f# プロジェクトの作成と**です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-127">If you already have a .dbml file, you can skip to the section, **Create and Set Up an F# Project**.</span></span> <span data-ttu-id="d3d5f-128">それ以外の場合、既存の SQL データベースを指定して .dbml ファイルを作成し、コマンドラインを使用してツール SqlMetal.exe できます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-128">Otherwise, you can create a .dbml file given an existing SQL database and by using the command-line tool SqlMetal.exe.</span></span>


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a><span data-ttu-id="d3d5f-129">SqlMetal.exe を使用して .dbml ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="d3d5f-129">To create a .dbml file by using SqlMetal.exe</span></span>

1. <span data-ttu-id="d3d5f-130">開く、**開発者コマンド プロンプト**です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-130">Open a **Developer Command Prompt**.</span></span>
<br />

2. <span data-ttu-id="d3d5f-131">入力して SqlMetal.exe へのアクセスがあることを確認してください。`SqlMetal.exe /?`コマンド プロンプトでします。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-131">Ensure that you have access to SqlMetal.exe by entering `SqlMetal.exe /?` at the command prompt.</span></span> <span data-ttu-id="d3d5f-132">SqlMetal.exe が通常インストールされている、 **Microsoft SDKs**フォルダー **Program Files**または**%program Files (x86)**です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-132">SqlMetal.exe is typically installed under the **Microsoft SDKs** folder in **Program Files** or **Program Files (x86)**.</span></span>
<br />

3. <span data-ttu-id="d3d5f-133">次のコマンド ライン オプションには、SqlMetal.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-133">Run SqlMetal.exe with the following command-line options.</span></span> <span data-ttu-id="d3d5f-134">代わりに適切なパスを置き換える`c:\destpath`.dbml ファイルを作成し、データベース サーバーの適切な値を挿入、名、およびデータベース名をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-134">Substitute an appropriate path in place of `c:\destpath` to create the .dbml file, and insert appropriate values for the database server, instance name, and database name.</span></span>
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
<span data-ttu-id="d3d5f-135">SqlMetal.exe にアクセス許可の問題により、ファイルの作成の問題がある場合への書き込みアクセスのあるフォルダーに、現在のディレクトリを変更します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-135">If SqlMetal.exe has trouble creating the file due to permissions issues, change the current directory to a folder that you have write access to.</span></span>


4. <span data-ttu-id="d3d5f-136">他の使用可能なコマンド ライン オプションを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-136">You can also look at the other available command-line options.</span></span> <span data-ttu-id="d3d5f-137">たとえば、ビューと、生成された型に含まれる SQL 関数したい場合に使用できるオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-137">For example, there are options you can use if you want views and SQL functions included in the generated types.</span></span> <span data-ttu-id="d3d5f-138">詳細については、次を参照してください。 [SqlMetal.exe&#40;コード生成ツール&#41;](https://msdn.microsoft.com/library/bb386987)です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-138">For more information, see [SqlMetal.exe &#40;Code Generation Tool&#41;](https://msdn.microsoft.com/library/bb386987).</span></span>
<br />


## <a name="creating-and-setting-up-an-f-project"></a><span data-ttu-id="d3d5f-139">作成、f# プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="d3d5f-139">Creating and setting up an F# project</span></span>
<span data-ttu-id="d3d5f-140">このステップでは、プロジェクトを作成し、DBML 型プロバイダーを使用する適切な参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-140">In this step, you create a project and add appropriate references to use the DBML type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="d3d5f-141">F# プロジェクトを作成してセットアップするには</span><span class="sxs-lookup"><span data-stu-id="d3d5f-141">To create and set up an F# project</span></span>

1. <span data-ttu-id="d3d5f-142">新しい f# コンソール アプリケーション プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-142">Add a new F# Console Application project to your solution.</span></span>
<br />

2. <span data-ttu-id="d3d5f-143">**ソリューション エクスプ ローラー**、ショートカット メニューを開き、**参照**を選択し**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-143">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="d3d5f-144">**アセンブリ**領域で、選択、 **Framework**  ノードをクリックし、使用可能なアセンブリの一覧で、選択、 **System.Data**と**System.Data.Linq**アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-144">In the **Assemblies** area, choose the **Framework** node, and then, in the list of available assemblies, choose the **System.Data** and **System.Data.Linq** assemblies.</span></span>
<br />

4. <span data-ttu-id="d3d5f-145">**アセンブリ**領域で、選択**拡張**をクリックし、使用可能なアセンブリの一覧で、選択**FSharp.Data.TypeProviders**です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-145">In the **Assemblies** area, choose **Extensions**, and then, in the list of available assemblies, choose **FSharp.Data.TypeProviders**.</span></span>
<br />

5. <span data-ttu-id="d3d5f-146">選択、 **OK**これらのアセンブリへの参照をプロジェクトに追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-146">Choose the **OK** button to add references to these assemblies to your project.</span></span>
<br />

6. <span data-ttu-id="d3d5f-147">(省略可能)</span><span class="sxs-lookup"><span data-stu-id="d3d5f-147">(Optional).</span></span> <span data-ttu-id="d3d5f-148">前の手順で作成した .dbml ファイルをコピーし、ファイル、プロジェクトのメイン フォルダーに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-148">Copy the .dbml file that you created in the previous step, and paste the file in the main folder for your project.</span></span> <span data-ttu-id="d3d5f-149">このフォルダーには、プロジェクト ファイル (.fsproj) およびコード ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-149">This folder contains the project file (.fsproj) and code files.</span></span> <span data-ttu-id="d3d5f-150">メニュー バーで、次のように選択します。**プロジェクト**、**既存項目の追加**、し、プロジェクトに追加する .dbml ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-150">On the menu bar, choose **Project**, **Add Existing Item**, and then specify the .dbml file to add it to your project.</span></span> <span data-ttu-id="d3d5f-151">これらの手順を実行する場合は、次の手順で ResolutionFolder static パラメーターを省略できます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-151">If you complete these steps, you can omit the ResolutionFolder static parameter in the next step.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="d3d5f-152">型プロバイダーの構成</span><span class="sxs-lookup"><span data-stu-id="d3d5f-152">Configuring the type provider</span></span>
<span data-ttu-id="d3d5f-153">このセクションでは、型プロバイダーを作成し、.dbml ファイルに記載されているスキーマから型を生成します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-153">In this section, you create a type provider and generate types from the schema that’s described in the .dbml file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a><span data-ttu-id="d3d5f-154">型プロバイダーを構成して、型を生成するには</span><span class="sxs-lookup"><span data-stu-id="d3d5f-154">To configure the type provider and generate the types</span></span>

- <span data-ttu-id="d3d5f-155">表示されたコードを追加、 **TypeProviders**名前空間を使用する .dbml ファイルの型プロバイダーをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-155">Add code that opens the **TypeProviders** namespace and instantiates the type provider for the .dbml file that you want to use.</span></span> <span data-ttu-id="d3d5f-156">プロジェクトに .dbml ファイルを追加する場合は、ResolutionFolder static パラメーターを省略できます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-156">If you added the .dbml file to your project, you can omit the ResolutionFolder static parameter.</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

<span data-ttu-id="d3d5f-157">DataContext 型が生成されたすべての型へのアクセスを提供しから継承`System.Data.Linq.DataContext`です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-157">The DataContext type provides access to all the generated types and inherits from `System.Data.Linq.DataContext`.</span></span> <span data-ttu-id="d3d5f-158">DbmlFile 型プロバイダーが、さまざまな静的パラメーターを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-158">The DbmlFile type provider has various static parameters that you can set.</span></span> <span data-ttu-id="d3d5f-159">たとえばを指定して、DataContext 型の別の名前を使用することができます`DataContext=MyDataContext`です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-159">For example, you can use a different name for the DataContext type by specifying `DataContext=MyDataContext`.</span></span> <span data-ttu-id="d3d5f-160">その場合は、コードでは、次の例ようになります。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-160">In that case, your code resembles the following example:</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a><span data-ttu-id="d3d5f-161">データベースの照会</span><span class="sxs-lookup"><span data-stu-id="d3d5f-161">Querying the database</span></span>
<span data-ttu-id="d3d5f-162">このセクションでは、f# クエリ式を使用するデータベースを照会します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-162">In this section, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="d3d5f-163">データを照会するには</span><span class="sxs-lookup"><span data-stu-id="d3d5f-163">To query the data</span></span>

- <span data-ttu-id="d3d5f-164">データベースを照会するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-164">Add code to query the database.</span></span>
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a><span data-ttu-id="d3d5f-165">次の手順</span><span class="sxs-lookup"><span data-stu-id="d3d5f-165">Next Steps</span></span>
<span data-ttu-id="d3d5f-166">その他のクエリ式を使用またはデータ コンテキストから、データベース接続を取得し、通常の ADO.NET データ操作を実行する続行することができます。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-166">You can proceed to use other query expressions, or get a database connection from the data context and perform normal ADO.NET data operations.</span></span> <span data-ttu-id="d3d5f-167">追加の手順を参照してください「のデータのクエリ」の後で[チュートリアル: 型プロバイダーを使用して SQL データベースへのアクセス](accessing-a-sql-database.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3d5f-167">For additional steps, see the sections after "Query the Data" in [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="d3d5f-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3d5f-168">See Also</span></span>
[<span data-ttu-id="d3d5f-169">DbmlFile 型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d3d5f-169">DbmlFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="d3d5f-170">型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="d3d5f-170">Type Providers</span></span>](index.md)

[<span data-ttu-id="d3d5f-171">チュートリアル : 型プロバイダーを使用した SQL データベースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="d3d5f-171">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>](accessing-a-sql-database.md)

[<span data-ttu-id="d3d5f-172">SqlMetal.exe&#40;コード生成ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="d3d5f-172">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)

[<span data-ttu-id="d3d5f-173">クエリ式</span><span class="sxs-lookup"><span data-stu-id="d3d5f-173">Query Expressions</span></span>](../../language-reference/query-expressions.md)
