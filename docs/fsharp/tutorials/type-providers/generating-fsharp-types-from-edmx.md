---
title: 'チュートリアル : EDMX スキーマ ファイルからの F# 型の生成 (F#)'
description: F# で f# 3.0 では、スキーマが .edmx ファイルで指定されている Entity Data Model (EDM) で表されるデータの種類を作成する方法を説明します。
keywords: visual f#, f#, 関数型プログラミング
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 901457dce358f768b4f4c980703e09f6c744918e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a><span data-ttu-id="dff6f-104">チュートリアル : EDMX スキーマ ファイルからの F# 型の生成</span><span class="sxs-lookup"><span data-stu-id="dff6f-104">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>

> [!NOTE]
<span data-ttu-id="dff6f-105">このガイドでは、f# 3.0 用に作成された、更新されます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="dff6f-106">最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](https://fsharp.github.io/FSharp.Data/) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dff6f-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="dff6f-107">API リファレンス リンクで msdn を実行します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="dff6f-108">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="dff6f-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="dff6f-109">F# 3.0 に関するこのチュートリアルでは、スキーマが .edmx ファイルで指定されている、エンティティ データ モデル (EDM) で表現されるデータの型を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-109">This walkthrough for F# 3.0 shows you how to create types for data that is represented by the Entity Data Model (EDM), the schema for which is specified in an .edmx file.</span></span> <span data-ttu-id="dff6f-110">また、EdmxFile 型プロバイダーを使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-110">This walkthrough also shows how to use the EdmxFile type provider.</span></span> <span data-ttu-id="dff6f-111">開始する前に、SqlEntityConnection 型プロバイダーの方がより適切な選択かどうかを検討します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-111">Before you begin, consider whether a SqlEntityConnection type provider is a more appropriate type provider option.</span></span> <span data-ttu-id="dff6f-112">SqlEntityConnection 型プロバイダーは、プロジェクトの開発フェーズで接続できるライブ データベースがあり、コンパイル時に接続文字列の指定について気にする必要がない場合に最適な選択です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-112">The SqlEntityConnection type provider works best for scenarios where you have a live database that you can connect to during the development phase of your project, and you do not mind specifying the connection string at compile time.</span></span> <span data-ttu-id="dff6f-113">ただし、この型プロバイダーは、EdmxFile 型プロバイダーと比べて公開するデータベース機能が少ないという制約があります。</span><span class="sxs-lookup"><span data-stu-id="dff6f-113">However, this type provider is also limited in that it doesn't expose as much database functionality as the EdmxFile type provider.</span></span> <span data-ttu-id="dff6f-114">また、エンティティ データ モデルを使用するデータベース プロジェクトのライブ データベース接続がない場合は、.edmx ファイルを使用してデータベースに対するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-114">Also, if you don't have a live database connection for a database project that uses the Entity Data Model, you can use the .edmx file to code against the database.</span></span> <span data-ttu-id="dff6f-115">EdmxFile 型プロバイダーを使用する場合、F# コンパイラが EdmGen.exe を実行して、指定する型を生成します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-115">When you use the EdmxFile type provider, the F# compiler runs EdmGen.exe to generate the types that it provides.</span></span>

<span data-ttu-id="dff6f-116">このチュートリアルでは以下のタスクについて説明します。このチュートリアルを正しく行うには、これらの作業を順に行ってください。</span><span class="sxs-lookup"><span data-stu-id="dff6f-116">This walkthrough illustrates the following tasks, which you must perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="dff6f-117">EDMX ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="dff6f-117">Creating an EDMX file</span></span>
<br />

- <span data-ttu-id="dff6f-118">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="dff6f-118">Creating the project</span></span>
<br />

- <span data-ttu-id="dff6f-119">エンティティ データ モデルの接続文字列の検索または作成</span><span class="sxs-lookup"><span data-stu-id="dff6f-119">Finding or creating the entity data model connection string</span></span>
<br />

- <span data-ttu-id="dff6f-120">型プロバイダーの構成</span><span class="sxs-lookup"><span data-stu-id="dff6f-120">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="dff6f-121">データの照会</span><span class="sxs-lookup"><span data-stu-id="dff6f-121">Querying the data</span></span>
<br />

- <span data-ttu-id="dff6f-122">ストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="dff6f-122">Calling a stored procedure</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="dff6f-123">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="dff6f-123">Prerequisites</span></span>

## <a name="creating-an-edmx-file"></a><span data-ttu-id="dff6f-124">EDMX ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="dff6f-124">Creating an EDMX file</span></span>
<span data-ttu-id="dff6f-125">既に EDMX ファイルがある場合は、この手順を省略できます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-125">If you already have an EDMX file, you can skip this step.</span></span>


#### <a name="to-create-an-edmx-file"></a><span data-ttu-id="dff6f-126">EDMX ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="dff6f-126">To create an EDMX file</span></span>

- <span data-ttu-id="dff6f-127">EDMX ファイルがない場合、最後の手順では、このチュートリアルの手順を行うことができる[エンティティ データ モデルを構成する](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model)です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-127">If you don't already have an EDMX file, you can follow the instructions at the end of this walkthrough in the step [Configuring the Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span></span>
<br />

## <a name="creating-the-project"></a><span data-ttu-id="dff6f-128">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="dff6f-128">Creating the project</span></span>
<span data-ttu-id="dff6f-129">この手順では、プロジェクトを作成し、EDMX 型プロバイダーを使用するために適切な参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-129">In this step, you create a project and add appropriate references to it to use the EDMX type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="dff6f-130">F# プロジェクトを作成してセットアップするには</span><span class="sxs-lookup"><span data-stu-id="dff6f-130">To create and set up an F# project</span></span>

1. <span data-ttu-id="dff6f-131">前のプロジェクトを閉じ、別のプロジェクトを作成して「SchoolEDM」という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-131">Close the previous project, create another project, and name it SchoolEDM.</span></span>
<br />

2. <span data-ttu-id="dff6f-132">**ソリューション エクスプ ローラー**、ショートカット メニューを開き、**参照**を選択し**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-132">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="dff6f-133">**アセンブリ**領域で、選択、 **Framework**ノード。</span><span class="sxs-lookup"><span data-stu-id="dff6f-133">In the **Assemblies** area, choose the **Framework** node.</span></span>
<br />

4. <span data-ttu-id="dff6f-134">使用可能なアセンブリの一覧で選択、 **System.Data.Entity**と**System.Data.Linq** 、アセンブリを選択し、**追加**これらへの参照を追加するプロジェクトにアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="dff6f-134">In the list of available assemblies, choose the **System.Data.Entity** and **System.Data.Linq** assemblies, and then choose the **Add** button to add references to these assemblies to your project.</span></span>
<br />

5. <span data-ttu-id="dff6f-135">**アセンブリ**領域で、選択、**拡張**ノード。</span><span class="sxs-lookup"><span data-stu-id="dff6f-135">In the **Assemblies** area, select the **Extensions** node.</span></span>
<br />

6. <span data-ttu-id="dff6f-136">使用できる拡張機能の一覧で、FSharp.Data.TypeProviders アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-136">In the  list of available extensions, add a reference to the FSharp.Data.TypeProviders assembly.</span></span>
<br />

7. <span data-ttu-id="dff6f-137">次のコードを追加し、適切な名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-137">Add the following code to open the appropriate namespaces.</span></span>
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="dff6f-138">エンティティ データ モデルの接続文字列の検索または作成</span><span class="sxs-lookup"><span data-stu-id="dff6f-138">Finding or creating the connection string for the Entity Data Model</span></span>
<span data-ttu-id="dff6f-139">エンティティ データ モデルの接続文字列 (EDMX 接続文字列) には、データベース プロバイダーの接続文字列だけではなく追加情報も含まれます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-139">The connection string for the Entity Data Model (EDMX connection string) includes not only the connection string for the database provider but also additional information.</span></span> <span data-ttu-id="dff6f-140">たとえば、簡単な SQL Server データベースの EDMX 接続文字列は次のコードのようになります。</span><span class="sxs-lookup"><span data-stu-id="dff6f-140">For example, EDMX connection string for a simple SQL Server database resembles the following code.</span></span>

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

<span data-ttu-id="dff6f-141">EDMX 接続文字列の詳細については、次を参照してください。[接続文字列](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-141">For more information about EDMX connection strings, see [Connection Strings](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="dff6f-142">エンティティ データ モデルの接続文字列を検索または作成するには</span><span class="sxs-lookup"><span data-stu-id="dff6f-142">To find or create the connection string for the Entity Data Model</span></span>

1. <span data-ttu-id="dff6f-143">EDMX 接続文字列は、手動で生成することが困難な場合があります。そのため、プログラムにより生成することで時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-143">EDMX connection strings can be difficult to generate by hand, so you can save time by generating it programmatically.</span></span> <span data-ttu-id="dff6f-144">EDMX 接続文字列がわかっている場合は、この手順を省略し、次の手順でその接続文字列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-144">If you know your EDMX connection string, you can bypass this step and simply use that string in the next step.</span></span> <span data-ttu-id="dff6f-145">そうでない場合は、次のコードを使用し、指定したデータベース接続文字列から EDMX 接続文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-145">If not, use the following code to generate the EDMX connection string from a database connection string that you provide.</span></span>
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a><span data-ttu-id="dff6f-146">型プロバイダーの構成</span><span class="sxs-lookup"><span data-stu-id="dff6f-146">Configuring the type provider</span></span>
<span data-ttu-id="dff6f-147">この手順では、EDMX 接続文字列を使用して型プロバイダーを作成および構成し、.edmx ファイルで定義されたスキーマの型を生成します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-147">In this step, you create and configure the type provider with the EDMX connection string, and you generate types for the schema that's defined in the .edmx file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="dff6f-148">型プロバイダーを構成して型を生成するには</span><span class="sxs-lookup"><span data-stu-id="dff6f-148">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="dff6f-149">このチュートリアルの最初の手順で生成した .edmx ファイルを、プロジェクト フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="dff6f-149">Copy the .edmx file that you generated in the first step of this walkthrough to your project folder.</span></span>
<br />

2. <span data-ttu-id="dff6f-150">F# のプロジェクトでプロジェクト ノードのショートカット メニューを開いて選択**既存項目の追加**、プロジェクトに追加する .edmx ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-150">Open the shortcut menu for the project node in your F# project, choose **Add Existing Item**, and then choose the .edmx file to add it to your project.</span></span>
<br />

3. <span data-ttu-id="dff6f-151">次のコードを入力し、.edmx ファイルの型プロバイダーをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="dff6f-151">Enter the following code to activate the type provider for your .edmx file.</span></span> <span data-ttu-id="dff6f-152">置き換える*サーバー*\*インスタンス * は、SQL Server とは、インスタンスの名前を実行して、最初の手順から .edmx ファイルの名前を使用して、このチュートリアルでは、サーバーの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-152">Replace *Server*\*Instance* with the name of your server that's running SQL Server and the name of your instance, and use the name of your .edmx file from the first step in this walkthrough.</span></span>
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a><span data-ttu-id="dff6f-153">データの照会</span><span class="sxs-lookup"><span data-stu-id="dff6f-153">Querying the data</span></span>
<span data-ttu-id="dff6f-154">この手順では、F# クエリ式を使用してデータベースを照会します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-154">In this step, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="dff6f-155">データを照会するには</span><span class="sxs-lookup"><span data-stu-id="dff6f-155">To query the data</span></span>

- <span data-ttu-id="dff6f-156">エンティティ データ モデルのデータを照会する次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-156">Enter the following code to query the data in the entity data model.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="dff6f-157">ストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="dff6f-157">Calling a stored procedure</span></span>
<span data-ttu-id="dff6f-158">EDMX 型プロバイダーを使用してストアド プロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-158">You can call stored procedures by using the EDMX type provider.</span></span> <span data-ttu-id="dff6f-159">School データベースには次の手順では、ストアド プロシージャが含まれています**UpdatePerson**レコード、指定された新しい列の値を更新します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-159">In the following procedure, the School database contains a stored procedure, **UpdatePerson**, which updates a record, given new values for the columns.</span></span> <span data-ttu-id="dff6f-160">このストアド プロシージャは DataContext 型のメソッドとして公開されるため、使用できます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-160">You can use this stored procedure because it's exposed as a method on the DataContext type.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="dff6f-161">ストアド プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="dff6f-161">To call a stored procedure</span></span>

- <span data-ttu-id="dff6f-162">次のコードを追加してレコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-162">Add the following code to update records.</span></span>
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

<span data-ttu-id="dff6f-163">正常に終了した場合、結果は 1 です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-163">The result is 1 if you succeed.</span></span> <span data-ttu-id="dff6f-164">注意して**exactlyOne**クエリ式内で 1 つの結果のみを返します。 それ以外の場合、例外がスローされることを確認するために使用します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-164">Notice that **exactlyOne** is used in the query expression to ensure that only one result is returned; otherwise, an exception is thrown.</span></span> <span data-ttu-id="dff6f-165">また、null 許容値をより簡単に使用するを使用する、単純な**null 許容**通常の値から null 許容値を作成するには、このコードで定義されている関数です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-165">Also, to work with nullable values more easily, you can use the simple **nullable** function that's defined in this code to create a nullable value out of an ordinary value.</span></span>

<br />

## <a name="configuring-the-entity-data-model"></a><span data-ttu-id="dff6f-166">エンティティ データ モデルの構成</span><span class="sxs-lookup"><span data-stu-id="dff6f-166">Configuring the Entity Data Model</span></span>
<span data-ttu-id="dff6f-167">この手順は、データベースから完全なエンティティ データ モデルを生成する方法を確認する際に、テストに使用するデータベースがない場合にのみ、完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dff6f-167">You should complete this procedure only if you want to know how to generate a full Entity Data Model from a database and you don't have a database with which to test.</span></span>


#### <a name="to-configure-the-entity-data-model"></a><span data-ttu-id="dff6f-168">エンティティ データ モデルを構成するには</span><span class="sxs-lookup"><span data-stu-id="dff6f-168">To configure the Entity Data Model</span></span>

1. <span data-ttu-id="dff6f-169">メニュー バーで、次のように選択します。 **SQL**、 **TRANSACT-SQL エディター**、**新しいクエリ**データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-169">On the menu bar, choose **SQL**, **Transact-SQL Editor**, **New Query** to create a database.</span></span> <span data-ttu-id="dff6f-170">プロンプトが表示されたら、データベース サーバーおよびインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-170">If prompted, specify your database server and instance.</span></span>
<br />

2. <span data-ttu-id="dff6f-171">コピーして」の説明に従って、受講者用データベースを作成するデータベースのスクリプトの内容を貼り付ける、 [Entity Framework ドキュメント](https://msdn.microsoft.com/data/JJ614587.aspx)データ デベロッパー センターにします。</span><span class="sxs-lookup"><span data-stu-id="dff6f-171">Copy and paste the contents of the database script that creates the Student database, as described in the [Entity Framework documentation](https://msdn.microsoft.com/data/JJ614587.aspx) in the Data Developer Center.</span></span>
<br />

3. <span data-ttu-id="dff6f-172">SQL スクリプトを実行するには、三角形で、ツール バー ボタンを選択するか、ctrl キーを押しながら Q キーを選択します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-172">Run the SQL script by choosing the toolbar button with the triangle symbol or choosing the Ctrl+Q keys.</span></span>
<br />

4. <span data-ttu-id="dff6f-173">**サーバー エクスプ ローラー**、ショートカット メニューを開き、**データ接続**、選択**接続の追加**、インスタンスの名前のデータベース サーバーの名前を入力、および School データベース。</span><span class="sxs-lookup"><span data-stu-id="dff6f-173">In **Server Explorer**, open the shortcut menu for **Data Connections**, choose **Add Connection**, and then enter the name of the database server, the name of the instance name, and the School database.</span></span>
<br />

5. <span data-ttu-id="dff6f-174">C# または Visual Basic コンソール アプリケーション プロジェクトを作成で、ショートカット メニューを開き、**新しい項目の追加**を選択し**ADO.NET エンティティ データ モデル**です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-174">Create a C# or Visual Basic Console Application project, open its shortcut menu, choose **Add New Item**, and then choose **ADO.NET Entity Data Model**.</span></span>
<br />  <span data-ttu-id="dff6f-175">Entity Data Model ウィザードが開きます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-175">The Entity Data Model Wizard opens.</span></span> <span data-ttu-id="dff6f-176">このウィザードを使用すると、エンティティ データ モデルを作成する方法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-176">By using this wizard, you can choose how you want to create the Entity Data Model.</span></span>
<br />

6. <span data-ttu-id="dff6f-177">**モデルのコンテンツ**を選択、**データベースから生成**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="dff6f-177">Under **Choose Model Contents**, select the **Generate from database** check box.</span></span>
<br />

7. <span data-ttu-id="dff6f-178">次のページで、新しく作成された School データベースをデータ接続として選択します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-178">On the next page, choose your newly created School database as the data connection.</span></span>
<br />  <span data-ttu-id="dff6f-179">この接続のようになります **&lt;servername&gt;.&lt;instancename&gt;です。School.dbo**です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-179">This connection should resemble **&lt;servername&gt;.&lt;instancename&gt;.School.dbo**.</span></span>
<br />

8. <span data-ttu-id="dff6f-180">エンティティ接続文字列は、後で重要となる場合があるため、クリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="dff6f-180">Copy your entity connection string to the Clipboard because that string might be important later.</span></span>
<br />

9. <span data-ttu-id="dff6f-181">エンティティ接続文字列を保存する チェック ボックスを確認してください、 **App.Config**ファイルが選択され、テキスト ボックスで、必要な場合に役立つ、後で接続文字列を検索する必要がありますの文字列値を書き留めます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-181">Make sure the check box to save the entity connection string to the **App.Config** file is selected, and make note of the string value in the text box, which should help you locate the connection string later, if needed.</span></span>
<br />

10. <span data-ttu-id="dff6f-182">次のページで選択**テーブル**と**ストアド プロシージャおよび関数**です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-182">On the next page, choose **Tables** and **Stored Procedures and Functions**.</span></span>
<br />  <span data-ttu-id="dff6f-183">これらの最上位ノードを選択すると、すべてのテーブル、ストアド プロシージャ、および関数が選択されます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-183">By choosing these top-level nodes, you choose all tables, stored procedures, and functions.</span></span> <span data-ttu-id="dff6f-184">また、必要に応じて、これらを個別に選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-184">You can also choose these individually, if you want.</span></span>
<br />

11. <span data-ttu-id="dff6f-185">他の設定のチェック ボックスがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-185">Make sure that the check boxes for the other settings are selected.</span></span>
<br />  <span data-ttu-id="dff6f-186">最初の**複数化または単数生成されたオブジェクト名** チェック ボックスは単数形をデータベース テーブルを表すオブジェクトを名前付け規則に一致するように複数形に変更するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-186">The first **Pluralize or singularize generated object names** check box indicates whether to change singular forms to plural to match conventions in naming objects that represent database tables.</span></span> <span data-ttu-id="dff6f-187">**モデルに外部キー列を含める**チェック ボックスは、データベース スキーマについて生成されるオブジェクトの種類の他のフィールドを結合する目的は、対象のフィールドを含めるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-187">The **Include foreign key columns in the model** check box determines whether to include fields for which the purpose is to join to other fields in the object types that are generated for the database schema.</span></span> <span data-ttu-id="dff6f-188">3 番目のチェック ボックスは、モデルにストアド プロシージャおよび関数を含めるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dff6f-188">The third check box indicates whether to include stored procedures and functions in the model.</span></span>
<br />

12. <span data-ttu-id="dff6f-189">選択、**完了**School データベースに基づいているエンティティ データ モデルを含む .edmx ファイルを生成するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dff6f-189">Select the **Finish** button to generate an .edmx file that contains an Entity Data Model that's based on the School database.</span></span>
<br />  <span data-ttu-id="dff6f-190">ファイル、 **Model1.edmx**は、プロジェクトに追加され、データベース ダイアグラムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dff6f-190">A file, **Model1.edmx**, is added to your project, and a database diagram appears.</span></span>
<br />

13. <span data-ttu-id="dff6f-191">メニュー バーで、次のように選択します**ビュー**、**その他のウィンドウ**、 **Entity Data Model ブラウザー**モデルのすべての詳細を表示または**エンティティ データ モデル マッピングの詳細。**を開くには、生成されたオブジェクト モデルをデータベース テーブルと列にマップする方法を示すウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="dff6f-191">On the menu bar, choose **View**, **Other Windows**, **Entity Data Model Browser** to view all the details of the model or **Entity Data Model Mapping Details** to open a window that shows how the generated object model maps onto database tables and columns.</span></span>
<br />


## <a name="next-steps"></a><span data-ttu-id="dff6f-192">次の手順</span><span class="sxs-lookup"><span data-stu-id="dff6f-192">Next Steps</span></span>
<span data-ttu-id="dff6f-193">記載されている、使用可能なクエリ演算子を調べることで他のクエリを調査[クエリ式](../../language-reference/query-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="dff6f-193">Explore other queries by looking at the available query operators as listed in [Query Expressions](../../language-reference/query-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="dff6f-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="dff6f-194">See Also</span></span>
[<span data-ttu-id="dff6f-195">型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="dff6f-195">Type Providers</span></span>](index.md)

[<span data-ttu-id="dff6f-196">EdmxFile 型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="dff6f-196">EdmxFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="dff6f-197">チュートリアル : 型プロバイダーおよびエンティティを使用した SQL データベースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="dff6f-197">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>](accessing-a-sql-database-entities.md)

[<span data-ttu-id="dff6f-198">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="dff6f-198">Entity Framework</span></span>](https://msdn.microsoft.com/data/ef)

[<span data-ttu-id="dff6f-199">.edmx ファイルの概要</span><span class="sxs-lookup"><span data-stu-id="dff6f-199">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="dff6f-200">EDM ジェネレーター &#40;EdmGen.exe&#41;</span><span class="sxs-lookup"><span data-stu-id="dff6f-200">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)

