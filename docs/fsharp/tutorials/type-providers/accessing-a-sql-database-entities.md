---
title: 'チュートリアル : 型プロバイダーおよびエンティティを使用した SQL データベースへのアクセス (F#)'
description: F# 3.0 では、ADO.NET Entity Data Model に基づいて SQL データベースの型指定されたデータにアクセスする方法を説明します。
keywords: visual f#, f#, 関数型プログラミング
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 153050f27ade0152741bdc2d77ab85eefa8418e9
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a><span data-ttu-id="801e2-104">チュートリアル : 型プロバイダーおよびエンティティを使用した SQL データベースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="801e2-104">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>

> [!NOTE]
<span data-ttu-id="801e2-105">このガイドでは、f# 3.0 用に作成された、更新されます。</span><span class="sxs-lookup"><span data-stu-id="801e2-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="801e2-106">最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](https://fsharp.github.io/FSharp.Data/) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="801e2-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="801e2-107">API リファレンス リンクで msdn を実行します。</span><span class="sxs-lookup"><span data-stu-id="801e2-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="801e2-108">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="801e2-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="801e2-109">F# 3.0 のこのチュートリアルでは、ADO.NET エンティティ データ モデルに基づいて SQL データベースの型指定されたデータにアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="801e2-109">This walkthrough for F# 3.0 shows you how to access typed data for a SQL database based on the ADO.NET Entity Data Model.</span></span> <span data-ttu-id="801e2-110">このチュートリアルでは、SQL データベースで使用するために F# `SqlEntityConnection` 型プロバイダーを設定する方法、データに対してクエリを作成する方法、データベースでストアド プロシージャを呼び出す方法、いくつかの ADO.NET Entity Framework 型とメソッドを使用してデータベースを更新する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="801e2-110">This walkthrough shows you how to set up the F# `SqlEntityConnection` type provider for use with a SQL database, how to write queries against the data, how to call stored procedures on the database, as well as how to use some of the ADO.NET Entity Framework types and methods to update the database.</span></span>

<span data-ttu-id="801e2-111">このチュートリアルでは以下のタスクについて説明します。このチュートリアルを正しく行うには、これらのタスクを順に行ってください。</span><span class="sxs-lookup"><span data-stu-id="801e2-111">This walkthrough illustrates the following tasks, which you should perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="801e2-112">School データベースの作成</span><span class="sxs-lookup"><span data-stu-id="801e2-112">Create the School database</span></span>
<br />

- <span data-ttu-id="801e2-113">F# プロジェクトの作成と構成</span><span class="sxs-lookup"><span data-stu-id="801e2-113">Create and configure an F# project</span></span>
<br />

- <span data-ttu-id="801e2-114">型プロバイダーを構成し、エンティティ データ モデルへの接続</span><span class="sxs-lookup"><span data-stu-id="801e2-114">Configure the type provider and connect to the Entity Data Model</span></span>
<br />

- <span data-ttu-id="801e2-115">データベースのクエリ</span><span class="sxs-lookup"><span data-stu-id="801e2-115">Query the database</span></span>
<br />

- <span data-ttu-id="801e2-116">データベースの更新</span><span class="sxs-lookup"><span data-stu-id="801e2-116">Updating the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="801e2-117">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="801e2-117">Prerequisites</span></span>
<span data-ttu-id="801e2-118">これらの手順を完了するには、データベースを作成できる、SQL Server を実行中のサーバーにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="801e2-118">You must have access to a server that's running SQL Server where you can create a database to complete these steps.</span></span>

## <a name="create-the-school-database"></a><span data-ttu-id="801e2-119">School データベースの作成</span><span class="sxs-lookup"><span data-stu-id="801e2-119">Create the School database</span></span>
<span data-ttu-id="801e2-120">SQL Server を実行している、管理者アクセス権を持つ任意のサーバー上に School データベースを作成することも、LocalDB を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="801e2-120">You can create the School database on any server that's running SQL Server to which you have administrative access, or you can use LocalDB.</span></span>


#### <a name="to-create-the-school-database"></a><span data-ttu-id="801e2-121">School データベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="801e2-121">To create the School database</span></span>

1. <span data-ttu-id="801e2-122">**サーバー エクスプ ローラー**、ショートカット メニューを開き、**データ接続** ノードを選択し**接続の追加**です。</span><span class="sxs-lookup"><span data-stu-id="801e2-122">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and then choose **Add Connection**.</span></span>
<br />  <span data-ttu-id="801e2-123">**接続の追加** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="801e2-123">The **Add Connection** dialog box appears.</span></span>
<br />

2. <span data-ttu-id="801e2-124">**サーバー名**ボックスで、管理アクセス権のある SQL Server のインスタンスの名前を指定するか、サーバーへのアクセス権がない場合は (localdb\v11.0) を指定します。</span><span class="sxs-lookup"><span data-stu-id="801e2-124">In the **Server name** box, specify the name of an instance of SQL Server to which you have administrative access, or specify (localdb\v11.0) if you don't have access to a server.</span></span>
<br />  <span data-ttu-id="801e2-125">SQL Server Express LocalDB は、開発およびテスト用の軽量のデータベース サーバーをコンピューターに提供します。</span><span class="sxs-lookup"><span data-stu-id="801e2-125">SQL Server Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="801e2-126">LocalDB の詳細については、次を参照してください。[チュートリアル: Visual Studio でのローカル データベース ファイルの作成](https://msdn.microsoft.com/library/ms233763.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="801e2-126">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>
<br />  <span data-ttu-id="801e2-127">新しいノードが作成された**サーバー エクスプ ローラー** **データ接続**です。</span><span class="sxs-lookup"><span data-stu-id="801e2-127">A new node is created in **Server Explorer** under **Data Connections**.</span></span>
<br />

3. <span data-ttu-id="801e2-128">新しい接続ノードのショートカット メニューを開き、選択**新しいクエリ**です。</span><span class="sxs-lookup"><span data-stu-id="801e2-128">Open the shortcut menu for the new connection node, and then choose **New Query**.</span></span>
<br />

4. <span data-ttu-id="801e2-129">開いている[School サンプル データベースを作成する](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx)Microsoft web サイトをコピーして貼り付けにデータベース スクリプトを作成する、School データベースをエディター ウィンドウにします。</span><span class="sxs-lookup"><span data-stu-id="801e2-129">Open [Creating the School Sample Database](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) on the Microsoft website, and then copy and paste the database script that creates the School database into the editor window.</span></span>
<br />


## <span data-ttu-id="801e2-130"><a name="BKMK_CreateConfigFSProj"> </a></span><span class="sxs-lookup"><span data-stu-id="801e2-130"><a name="BKMK_CreateConfigFSProj"> </a></span></span>

## <a name="create-and-configure-an-f-project"></a><span data-ttu-id="801e2-131">F# プロジェクトの作成と構成</span><span class="sxs-lookup"><span data-stu-id="801e2-131">Create and configure an F# project</span></span>
<span data-ttu-id="801e2-132">この手順では、プロジェクトを作成し、型プロバイダーを使用するようにそのプロジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="801e2-132">In this step, you create a project and set it up to use a type provider.</span></span>


#### <a name="to-create-and-configure-an-f-project"></a><span data-ttu-id="801e2-133">F# プロジェクトを作成および構成するには</span><span class="sxs-lookup"><span data-stu-id="801e2-133">To create and configure an F# project</span></span>

1. <span data-ttu-id="801e2-134">前のプロジェクトを閉じ、別のプロジェクトを作成し、名前**SchoolEDM**です。</span><span class="sxs-lookup"><span data-stu-id="801e2-134">Close the previous project, create another project, and name it **SchoolEDM**.</span></span>
<br />

2. <span data-ttu-id="801e2-135">**ソリューション エクスプ ローラー**、ショートカット メニューを開き、**参照**を選択し**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="801e2-135">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="801e2-136">選択、 **Framework**ノード、、 **Framework**一覧で、選択**System.Data**、 **System.Data.Entity**、および**System.Data.Linq**です。</span><span class="sxs-lookup"><span data-stu-id="801e2-136">Choose the **Framework** node, and then, in the **Framework** list, choose **System.Data**, **System.Data.Entity**,  and **System.Data.Linq**.</span></span>
<br />

4. <span data-ttu-id="801e2-137">選択、**拡張機能**ノードへの参照を追加、 [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) 、アセンブリを選択し、 **[ok]**  ダイアログ ボックスを閉じるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="801e2-137">Choose the **Extensions** node, add a reference to the [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly, and then choose the **OK** button to dismiss the dialog box.</span></span>
<br />

5. <span data-ttu-id="801e2-138">次のコードを追加して、内部モジュールを定義し、適切な名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="801e2-138">Add the following code to define an internal module and open appropriate namespaces.</span></span> <span data-ttu-id="801e2-139">型プロバイダーは、プライベートまたは内部名前空間にのみ型を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="801e2-139">The type provider can inject types only into a private or internal namespace.</span></span>
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. <span data-ttu-id="801e2-140">コードを実行する、コンパイル済みプログラムの代わりにスクリプトとして対話形式では、このチュートリアルで、プロジェクト ノードのショートカット メニューを開き、選択**新しい項目の追加**f# スクリプト ファイルを追加、および各手順でコードをスクリプトに追加します。</span><span class="sxs-lookup"><span data-stu-id="801e2-140">To run the code in this walkthrough interactively as a script instead of as a compiled program, open the shortcut menu for the project node, choose **Add New Item**, add an F# script file, and then add the code in each step to the script.</span></span> <span data-ttu-id="801e2-141">アセンブリ参照を読み込むには、次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="801e2-141">To load the assembly references, add the following lines.</span></span>
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. <span data-ttu-id="801e2-142">コードの各ブロックを強調表示して追加し、Alt キーを押しながら Enter キーを押して F# Interactive で実行します。</span><span class="sxs-lookup"><span data-stu-id="801e2-142">Highlight each block of code as you add it, and choose the Alt + Enter keys to run it in F# Interactive.</span></span>
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="801e2-143">型プロバイダーの構成とエンティティ データ モデルへの接続</span><span class="sxs-lookup"><span data-stu-id="801e2-143">Configure the type provider, and connect to the Entity Data Model</span></span>
<span data-ttu-id="801e2-144">この手順では、データ接続を使用して型プロバイダーを設定し、データを処理できるデータ コンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="801e2-144">In this step, you set up a type provider with a data connection and obtain a data context that allows you to work with data.</span></span>


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="801e2-145">型プロバイダーを構成してエンティティ データ モデルに接続するには</span><span class="sxs-lookup"><span data-stu-id="801e2-145">To configure the type provider, and connect to the Entity Data Model</span></span>

1. <span data-ttu-id="801e2-146">前に作成したエンティティ データ モデルに基づいて F# の型を生成する `SqlEntityConnection` 型プロバイダーを構成する次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="801e2-146">Enter the following code to configure the `SqlEntityConnection` type provider that generates F# types based on the Entity Data Model that you created previously.</span></span> <span data-ttu-id="801e2-147">完全な EDMX 接続文字列の代わりに、SQL 接続文字列のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="801e2-147">Instead of the full EDMX connection string, use only the SQL connection string.</span></span>
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  <span data-ttu-id="801e2-148">この操作により、前に作成したデータベース接続を使用して型プロバイダーを設定します。</span><span class="sxs-lookup"><span data-stu-id="801e2-148">This action sets up a type provider with the database connection that you created earlier.</span></span> <span data-ttu-id="801e2-149">`MultipleActiveResultSets` プロパティは、ADO.NET Entity Framework を使用する際に必要です。これは、このプロパティにより、1 つの接続でデータベースに対して複数のコマンドを非同期で実行できるようになるためです。この状況は ADO.NET Entity Framework コードで頻繁に発生します。</span><span class="sxs-lookup"><span data-stu-id="801e2-149">The property `MultipleActiveResultSets` is needed when you use the ADO.NET Entity Framework because this property allows multiple commands to execute asynchronously on the database in one connection, which can occur frequently in ADO.NET Entity Framework code.</span></span> <span data-ttu-id="801e2-150">詳細については、「 [複数のアクティブな結果セット (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="801e2-150">For more information, see [Multiple Active Result Sets (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span></span>
<br />

2. <span data-ttu-id="801e2-151">データ コンテキストを取得します。これは、プロパティとしてデータベース テーブルを含み、メソッドとしてデータベース ストアド プロシージャと関数を含むオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="801e2-151">Get the data context, which is an object that contains the database tables as properties and the database stored procedures and functions as methods.</span></span>
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a><span data-ttu-id="801e2-152">データベースの照会</span><span class="sxs-lookup"><span data-stu-id="801e2-152">Querying the database</span></span>
<span data-ttu-id="801e2-153">この手順では、F# クエリ式を使用してデータベースに対してさまざまなクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="801e2-153">In this step, you use F# query expressions to execute various queries on the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="801e2-154">データを照会するには</span><span class="sxs-lookup"><span data-stu-id="801e2-154">To query the data</span></span>

- <span data-ttu-id="801e2-155">エンティティ データ モデルからデータを照会する次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="801e2-155">Enter the following code to query the data from the entity data model.</span></span> <span data-ttu-id="801e2-156">データベース テーブル Course を Courses に、Person を People に変更する Pluralize = true の効果に注目してください。</span><span class="sxs-lookup"><span data-stu-id="801e2-156">Note the effect of Pluralize = true, which changes the database table Course to Courses and Person to People.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a><span data-ttu-id="801e2-157">データベースの更新</span><span class="sxs-lookup"><span data-stu-id="801e2-157">Updating the database</span></span>
<span data-ttu-id="801e2-158">データベースを更新するには、Entity Framework のクラスとメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="801e2-158">To update the database, you use the Entity Framework classes and methods.</span></span> <span data-ttu-id="801e2-159">SQLEntityConnection 型プロバイダーでは 2 種類のデータ コンテキストを使用できます。</span><span class="sxs-lookup"><span data-stu-id="801e2-159">You can use two types of data context with the SQLEntityConnection type provider.</span></span> <span data-ttu-id="801e2-160">最初の `ServiceTypes.SimpleDataContextTypes.EntityContainer` はデータベース テーブルと列を表す指定されたプロパティのみを含む簡易データ コンテキストです。</span><span class="sxs-lookup"><span data-stu-id="801e2-160">First, `ServiceTypes.SimpleDataContextTypes.EntityContainer` is the simplified data context, which includes only the provided properties that represent database tables and columns.</span></span> <span data-ttu-id="801e2-161">2 番目の完全データ コンテキストは Entity Framework クラス `System.Data.Objects.ObjectContext` のインスタンスで、これはデータベースに行を追加するメソッド `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="801e2-161">Second, the full data context is an instance of the Entity Framework class `System.Data.Objects.ObjectContext`, which contains the method `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` to add rows to the database.</span></span> <span data-ttu-id="801e2-162">Entity Framework は、テーブルとそれらのリレーションシップを認識するため、データベースの一貫性が強化されます。</span><span class="sxs-lookup"><span data-stu-id="801e2-162">The Entity Framework recognizes the tables and the relationships between them, so it enforces database consistency.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="801e2-163">データベースを更新するには</span><span class="sxs-lookup"><span data-stu-id="801e2-163">To update the database</span></span>

1. <span data-ttu-id="801e2-164">プログラムに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="801e2-164">Add the following code to your program.</span></span> <span data-ttu-id="801e2-165">この例では、2 つのオブジェクトとそのリレーションシップを追加し、インストラクターとオフィス割り当てを追加します。</span><span class="sxs-lookup"><span data-stu-id="801e2-165">In this example, you add two objects with a relationship between them, and you add an instructor and an office assignment.</span></span> <span data-ttu-id="801e2-166">テーブル `OfficeAssignments` には `InstructorID` 列が含まれています。この列は `PersonID` テーブルの `Person` 列を参照します。</span><span class="sxs-lookup"><span data-stu-id="801e2-166">The table `OfficeAssignments` contains the `InstructorID` column, which references the `PersonID` column in the `Person` table.</span></span>
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

<span data-ttu-id="801e2-167">`System.Data.Objects.ObjectContext.SaveChanges` を呼び出すまで、データベースの変更は行われません。</span><span class="sxs-lookup"><span data-stu-id="801e2-167">Nothing is changed in the database until you call `System.Data.Objects.ObjectContext.SaveChanges`.</span></span>
<br />

2. <span data-ttu-id="801e2-168">ここで、追加したオブジェクトを削除して、データベースを以前の状態に復元します。</span><span class="sxs-lookup"><span data-stu-id="801e2-168">Now restore the database to its earlier state by deleting the objects that you added.</span></span>
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
<span data-ttu-id="801e2-169">クエリ式を使用する際は、クエリには遅延評価が適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="801e2-169">When you use a query expression, you must remember that the query is subject to lazy evaluation.</span></span> <span data-ttu-id="801e2-170">したがって、データベースは、各クエリ式の後にあるラムダ式ブロックなどのチェーン評価中は読み取り用に開いています。</span><span class="sxs-lookup"><span data-stu-id="801e2-170">Therefore, the database is still open for reading during any chained evaluations, such as in the lambda expression blocks after each query expression.</span></span> <span data-ttu-id="801e2-171">明示的または暗黙的にトランザクションを使用するデータベース操作は、読み取り操作の完了後に行われます。</span><span class="sxs-lookup"><span data-stu-id="801e2-171">Any database operation that explicitly or implicitly uses a transaction must occur after the read operations have completed.</span></span>


## <a name="next-steps"></a><span data-ttu-id="801e2-172">次の手順</span><span class="sxs-lookup"><span data-stu-id="801e2-172">Next Steps</span></span>
<span data-ttu-id="801e2-173">使用できるクエリ演算子を確認することでその他のクエリ オプションを探索[クエリ式](../../language-reference/query-expressions.md)も確認し、 [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)をどのような機能が使用するときに理解するにはこの型プロバイダーを使用するとします。</span><span class="sxs-lookup"><span data-stu-id="801e2-173">Explore other query options by reviewing the query operators available in [Query Expressions](../../language-reference/query-expressions.md), and also review the [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) to understand what functionality is available to you when you use this type provider.</span></span>


## <a name="see-also"></a><span data-ttu-id="801e2-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="801e2-174">See Also</span></span>
[<span data-ttu-id="801e2-175">型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="801e2-175">Type Providers</span></span>](index.md)  
[<span data-ttu-id="801e2-176">SqlEntityConnection 型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="801e2-176">SqlEntityConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[<span data-ttu-id="801e2-177">チュートリアル: EDMX スキーマ ファイルからの f# 型の生成</span><span class="sxs-lookup"><span data-stu-id="801e2-177">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>](generating-fsharp-types-from-edmx.md)  
[<span data-ttu-id="801e2-178">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="801e2-178">ADO.NET Entity Framework</span></span>](https://msdn.microsoft.com/library/bb399572)  
[<span data-ttu-id="801e2-179">.edmx ファイルの概要</span><span class="sxs-lookup"><span data-stu-id="801e2-179">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[<span data-ttu-id="801e2-180">EDM ジェネレーター &#40;EdmGen.exe&#41;</span><span class="sxs-lookup"><span data-stu-id="801e2-180">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)  
