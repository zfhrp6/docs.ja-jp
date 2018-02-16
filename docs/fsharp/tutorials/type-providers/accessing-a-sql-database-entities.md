---
title: "チュートリアル : 型プロバイダーおよびエンティティを使用した SQL データベースへのアクセス (F#)"
description: "F# 3.0 では、ADO.NET Entity Data Model に基づいて SQL データベースの型指定されたデータにアクセスする方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: e0e78e06fa1129ba5eeb73bc36c14343c93d6927
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a>チュートリアル : 型プロバイダーおよびエンティティを使用した SQL データベースへのアクセス

> [!NOTE]
このガイドでは、f# 3.0 用に作成された、更新されます。  最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](http://fsharp.github.io/FSharp.Data/) を参照してください。

> [!NOTE]
API リファレンス リンクで msdn を実行します。  docs.microsoft.com API リファレンスは完全ではありません。

F# 3.0 のこのチュートリアルでは、ADO.NET エンティティ データ モデルに基づいて SQL データベースの型指定されたデータにアクセスする方法を示します。 このチュートリアルでは、SQL データベースで使用するために F# `SqlEntityConnection` 型プロバイダーを設定する方法、データに対してクエリを作成する方法、データベースでストアド プロシージャを呼び出す方法、いくつかの ADO.NET Entity Framework 型とメソッドを使用してデータベースを更新する方法を説明します。

このチュートリアルでは以下のタスクについて説明します。このチュートリアルを正しく行うには、これらのタスクを順に行ってください。


- School データベースの作成
<br />

- F# プロジェクトの作成と構成
<br />

- 型プロバイダーを構成し、エンティティ データ モデルへの接続
<br />

- データベースのクエリ
<br />

- データベースの更新
<br />


## <a name="prerequisites"></a>必須コンポーネント
これらの手順を完了するには、データベースを作成できる、SQL Server を実行中のサーバーにアクセスできる必要があります。

## <a name="create-the-school-database"></a>School データベースの作成
SQL Server を実行している、管理者アクセス権を持つ任意のサーバー上に School データベースを作成することも、LocalDB を使用することもできます。


#### <a name="to-create-the-school-database"></a>School データベースを作成するには

1. **サーバー エクスプ ローラー**、ショートカット メニューを開き、**データ接続** ノードを選択し**接続の追加**です。
<br />  **接続の追加** ダイアログ ボックスが表示されます。
<br />

2. **サーバー名**ボックスで、管理アクセス権のある SQL Server のインスタンスの名前を指定するか、サーバーへのアクセス権がない場合は (localdb\v11.0) を指定します。
<br />  SQL Server Express LocalDB は、開発およびテスト用の軽量のデータベース サーバーをコンピューターに提供します。 LocalDB の詳細については、次を参照してください。[チュートリアル: Visual Studio でのローカル データベース ファイルの作成](https://msdn.microsoft.com/library/ms233763.aspx)です。
<br />  新しいノードが作成された**サーバー エクスプ ローラー** **データ接続**です。
<br />

3. 新しい接続ノードのショートカット メニューを開き、選択**新しいクエリ**です。
<br />

4. 開いている[School サンプル データベースを作成する](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx)Microsoft web サイトをコピーして貼り付けにデータベース スクリプトを作成する、School データベースをエディター ウィンドウにします。
<br />


## <a name="BKMK_CreateConfigFSProj"> </a>

## <a name="create-and-configure-an-f-project"></a>F# プロジェクトの作成と構成
この手順では、プロジェクトを作成し、型プロバイダーを使用するようにそのプロジェクトを設定します。


#### <a name="to-create-and-configure-an-f-project"></a>F# プロジェクトを作成および構成するには

1. 前のプロジェクトを閉じ、別のプロジェクトを作成し、名前**SchoolEDM**です。
<br />

2. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**参照**を選択し**参照の追加**です。
<br />

3. 選択、 **Framework**ノード、、 **Framework**一覧で、選択**System.Data**、 **System.Data.Entity**、および**System.Data.Linq**です。
<br />

4. 選択、**拡張機能**ノードへの参照を追加、 [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) 、アセンブリを選択し、 **[ok]**  ダイアログ ボックスを閉じるボタンをクリックします。
<br />

5. 次のコードを追加して、内部モジュールを定義し、適切な名前空間を開きます。 型プロバイダーは、プライベートまたは内部名前空間にのみ型を挿入できます。
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. コードを実行する、コンパイル済みプログラムの代わりにスクリプトとして対話形式では、このチュートリアルで、プロジェクト ノードのショートカット メニューを開き、選択**新しい項目の追加**f# スクリプト ファイルを追加、および各手順でコードをスクリプトに追加します。 アセンブリ参照を読み込むには、次の行を追加します。
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. コードの各ブロックを強調表示して追加し、Alt キーを押しながら Enter キーを押して F# Interactive で実行します。
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a>型プロバイダーの構成とエンティティ データ モデルへの接続
この手順では、データ接続を使用して型プロバイダーを設定し、データを処理できるデータ コンテキストを取得します。


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a>型プロバイダーを構成してエンティティ データ モデルに接続するには

1. 前に作成したエンティティ データ モデルに基づいて F# の型を生成する `SqlEntityConnection` 型プロバイダーを構成する次のコードを入力します。 完全な EDMX 接続文字列の代わりに、SQL 接続文字列のみを使用します。
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  この操作により、前に作成したデータベース接続を使用して型プロバイダーを設定します。 `MultipleActiveResultSets` プロパティは、ADO.NET Entity Framework を使用する際に必要です。これは、このプロパティにより、1 つの接続でデータベースに対して複数のコマンドを非同期で実行できるようになるためです。この状況は ADO.NET Entity Framework コードで頻繁に発生します。 詳細については、「 [複数のアクティブな結果セット (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars)」を参照してください。
<br />

2. データ コンテキストを取得します。これは、プロパティとしてデータベース テーブルを含み、メソッドとしてデータベース ストアド プロシージャと関数を含むオブジェクトです。
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a>データベースの照会
この手順では、F# クエリ式を使用してデータベースに対してさまざまなクエリを実行します。


#### <a name="to-query-the-data"></a>データを照会するには

- エンティティ データ モデルからデータを照会する次のコードを入力します。 データベース テーブル Course を Courses に、Person を People に変更する Pluralize = true の効果に注目してください。
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

## <a name="updating-the-database"></a>データベースの更新
データベースを更新するには、Entity Framework のクラスとメソッドを使用します。 SQLEntityConnection 型プロバイダーでは 2 種類のデータ コンテキストを使用できます。 最初の `ServiceTypes.SimpleDataContextTypes.EntityContainer` はデータベース テーブルと列を表す指定されたプロパティのみを含む簡易データ コンテキストです。 2 番目の完全データ コンテキストは Entity Framework クラス `System.Data.Objects.ObjectContext` のインスタンスで、これはデータベースに行を追加するメソッド `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` を含んでいます。 Entity Framework は、テーブルとそれらのリレーションシップを認識するため、データベースの一貫性が強化されます。


#### <a name="to-update-the-database"></a>データベースを更新するには

1. プログラムに次のコードを追加します。 この例では、2 つのオブジェクトとそのリレーションシップを追加し、インストラクターとオフィス割り当てを追加します。 テーブル `OfficeAssignments` には `InstructorID` 列が含まれています。この列は `PersonID` テーブルの `Person` 列を参照します。
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

`System.Data.Objects.ObjectContext.SaveChanges` を呼び出すまで、データベースの変更は行われません。
<br />

2. ここで、追加したオブジェクトを削除して、データベースを以前の状態に復元します。
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
クエリ式を使用する際は、クエリには遅延評価が適用されることに注意してください。 したがって、データベースは、各クエリ式の後にあるラムダ式ブロックなどのチェーン評価中は読み取り用に開いています。 明示的または暗黙的にトランザクションを使用するデータベース操作は、読み取り操作の完了後に行われます。


## <a name="next-steps"></a>次の手順
使用できるクエリ演算子を確認することでその他のクエリ オプションを探索[クエリ式](../../language-reference/query-expressions.md)も確認し、 [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)をどのような機能が使用するときに理解するにはこの型プロバイダーを使用するとします。


## <a name="see-also"></a>参照
[型プロバイダー](index.md)  
[SqlEntityConnection 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[チュートリアル: EDMX スキーマ ファイルからの f# 型の生成](generating-fsharp-types-from-edmx.md)  
[ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)  
[.edmx ファイルの概要](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[EDM ジェネレーター &#40;です。EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)  
