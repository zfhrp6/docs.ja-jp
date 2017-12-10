---
title: "チュートリアル : EDMX スキーマ ファイルからの F# 型の生成 (F#)"
description: "F# で f# 3.0 では、スキーマが .edmx ファイルで指定されている Entity Data Model (EDM) で表されるデータの種類を作成する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 1df0344e8dab2b40d82d1b9c61ccd2f026906243
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a>チュートリアル : EDMX スキーマ ファイルからの F# 型の生成

> [!NOTE]
このガイドでは、f# 3.0 用に作成された、更新されます。  最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](http://fsharp.github.io/FSharp.Data/) を参照してください。

> [!NOTE]
API リファレンス リンクで msdn を実行します。  docs.microsoft.com API リファレンスは完全ではありません。

F# 3.0 に関するこのチュートリアルでは、スキーマが .edmx ファイルで指定されている、エンティティ データ モデル (EDM) で表現されるデータの型を作成する方法を示します。 また、EdmxFile 型プロバイダーを使用する方法も示します。 開始する前に、SqlEntityConnection 型プロバイダーの方がより適切な選択かどうかを検討します。 SqlEntityConnection 型プロバイダーは、プロジェクトの開発フェーズで接続できるライブ データベースがあり、コンパイル時に接続文字列の指定について気にする必要がない場合に最適な選択です。 ただし、この型プロバイダーは、EdmxFile 型プロバイダーと比べて公開するデータベース機能が少ないという制約があります。 また、エンティティ データ モデルを使用するデータベース プロジェクトのライブ データベース接続がない場合は、.edmx ファイルを使用してデータベースに対するコードを記述できます。 EdmxFile 型プロバイダーを使用する場合、F# コンパイラが EdmGen.exe を実行して、指定する型を生成します。

このチュートリアルでは以下のタスクについて説明します。このチュートリアルを正しく行うには、これらの作業を順に行ってください。


- EDMX ファイルの作成
<br />

- プロジェクトの作成
<br />

- エンティティ データ モデルの接続文字列の検索または作成
<br />

- 型プロバイダーの構成
<br />

- データの照会
<br />

- ストアド プロシージャの呼び出し
<br />


## <a name="prerequisites"></a>必須コンポーネント

## <a name="creating-an-edmx-file"></a>EDMX ファイルの作成
既に EDMX ファイルがある場合は、この手順を省略できます。


#### <a name="to-create-an-edmx-file"></a>EDMX ファイルを作成するには

- EDMX ファイルがない場合、最後の手順では、このチュートリアルの手順を行うことができる[エンティティ データ モデルを構成する](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model)です。
<br />

## <a name="creating-the-project"></a>プロジェクトの作成
この手順では、プロジェクトを作成し、EDMX 型プロバイダーを使用するために適切な参照を追加します。


#### <a name="to-create-and-set-up-an-f-project"></a>F# プロジェクトを作成してセットアップするには

1. 前のプロジェクトを閉じ、別のプロジェクトを作成して「SchoolEDM」という名前を付けます。
<br />

2. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**参照**を選択し**参照の追加**です。
<br />

3. **アセンブリ**領域で、選択、 **Framework**ノード。
<br />

4. 使用可能なアセンブリの一覧で選択、 **System.Data.Entity**と**System.Data.Linq** 、アセンブリを選択し、**追加**これらへの参照を追加するプロジェクトにアセンブリ。
<br />

5. **アセンブリ**領域で、選択、**拡張**ノード。
<br />

6. 使用できる拡張機能の一覧で、FSharp.Data.TypeProviders アセンブリへの参照を追加します。
<br />

7. 次のコードを追加し、適切な名前空間を開きます。
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a>エンティティ データ モデルの接続文字列の検索または作成
エンティティ データ モデルの接続文字列 (EDMX 接続文字列) には、データベース プロバイダーの接続文字列だけではなく追加情報も含まれます。 たとえば、簡単な SQL Server データベースの EDMX 接続文字列は次のコードのようになります。

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

EDMX 接続文字列の詳細については、次を参照してください。[接続文字列](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)です。


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a>エンティティ データ モデルの接続文字列を検索または作成するには

1. EDMX 接続文字列は、手動で生成することが困難な場合があります。そのため、プログラムにより生成することで時間を節約できます。 EDMX 接続文字列がわかっている場合は、この手順を省略し、次の手順でその接続文字列を使用できます。 そうでない場合は、次のコードを使用し、指定したデータベース接続文字列から EDMX 接続文字列を生成します。
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

## <a name="configuring-the-type-provider"></a>型プロバイダーの構成
この手順では、EDMX 接続文字列を使用して型プロバイダーを作成および構成し、.edmx ファイルで定義されたスキーマの型を生成します。


#### <a name="to-configure-the-type-provider-and-generate-types"></a>型プロバイダーを構成して型を生成するには

1. このチュートリアルの最初の手順で生成した .edmx ファイルを、プロジェクト フォルダーにコピーします。
<br />

2. F# のプロジェクトでプロジェクト ノードのショートカット メニューを開いて選択**既存項目の追加**、プロジェクトに追加する .edmx ファイルを選択します。
<br />

3. 次のコードを入力し、.edmx ファイルの型プロバイダーをアクティブにします。 置き換える*サーバー*\*インスタンス * は、SQL Server とは、インスタンスの名前を実行して、最初の手順から .edmx ファイルの名前を使用して、このチュートリアルでは、サーバーの名前に置き換えます。
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a>データの照会
この手順では、F# クエリ式を使用してデータベースを照会します。


#### <a name="to-query-the-data"></a>データを照会するには

- エンティティ データ モデルのデータを照会する次のコードを入力します。
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

## <a name="calling-a-stored-procedure"></a>ストアド プロシージャの呼び出し
EDMX 型プロバイダーを使用してストアド プロシージャを呼び出すことができます。 School データベースには次の手順では、ストアド プロシージャが含まれています**UpdatePerson**レコード、指定された新しい列の値を更新します。 このストアド プロシージャは DataContext 型のメソッドとして公開されるため、使用できます。


#### <a name="to-call-a-stored-procedure"></a>ストアド プロシージャを呼び出すには

- 次のコードを追加してレコードを更新します。
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

正常に終了した場合、結果は 1 です。 注意して**exactlyOne**クエリ式内で 1 つの結果のみを返します。 それ以外の場合、例外がスローされることを確認するために使用します。 また、null 許容値をより簡単に使用するを使用する、単純な**null 許容**通常の値から null 許容値を作成するには、このコードで定義されている関数です。

<br />

## <a name="configuring-the-entity-data-model"></a>エンティティ データ モデルの構成
この手順は、データベースから完全なエンティティ データ モデルを生成する方法を確認する際に、テストに使用するデータベースがない場合にのみ、完了する必要があります。


#### <a name="to-configure-the-entity-data-model"></a>エンティティ データ モデルを構成するには

1. メニュー バーで、次のように選択します。 **SQL**、 **TRANSACT-SQL エディター**、**新しいクエリ**データベースを作成します。 プロンプトが表示されたら、データベース サーバーおよびインスタンスを指定します。
<br />

2. コピーして」の説明に従って、受講者用データベースを作成するデータベースのスクリプトの内容を貼り付ける、 [Entity Framework ドキュメント](http://msdn.microsoft.com/data/JJ614587.aspx)データ デベロッパー センターにします。
<br />

3. SQL スクリプトを実行するには、三角形で、ツール バー ボタンを選択するか、ctrl キーを押しながら Q キーを選択します。
<br />

4. **サーバー エクスプ ローラー**、ショートカット メニューを開き、**データ接続**、選択**接続の追加**、インスタンスの名前のデータベース サーバーの名前を入力、および School データベース。
<br />

5. C# または Visual Basic コンソール アプリケーション プロジェクトを作成で、ショートカット メニューを開き、**新しい項目の追加**を選択し**ADO.NET エンティティ データ モデル**です。
<br />  Entity Data Model ウィザードが開きます。 このウィザードを使用すると、エンティティ データ モデルを作成する方法を選択できます。
<br />

6. **モデルのコンテンツ**を選択、**データベースから生成**チェック ボックスをオンします。
<br />

7. 次のページで、新しく作成された School データベースをデータ接続として選択します。
<br />  この接続のようになります **&lt;servername&gt;.&lt;instancename&gt;です。School.dbo**です。
<br />

8. エンティティ接続文字列は、後で重要となる場合があるため、クリップボードにコピーします。
<br />

9. エンティティ接続文字列を保存する チェック ボックスを確認してください、 **App.Config**ファイルが選択され、テキスト ボックスで、必要な場合に役立つ、後で接続文字列を検索する必要がありますの文字列値を書き留めます。
<br />

10. 次のページで選択**テーブル**と**ストアド プロシージャおよび関数**です。
<br />  これらの最上位ノードを選択すると、すべてのテーブル、ストアド プロシージャ、および関数が選択されます。 また、必要に応じて、これらを個別に選択することもできます。
<br />

11. 他の設定のチェック ボックスがオンになっていることを確認します。
<br />  最初の**複数化または単数生成されたオブジェクト名** チェック ボックスは単数形をデータベース テーブルを表すオブジェクトを名前付け規則に一致するように複数形に変更するかどうかを示します。 **モデルに外部キー列を含める**チェック ボックスは、データベース スキーマについて生成されるオブジェクトの種類の他のフィールドを結合する目的は、対象のフィールドを含めるかどうかを決定します。 3 番目のチェック ボックスは、モデルにストアド プロシージャおよび関数を含めるかどうかを示します。
<br />

12. 選択、**完了**School データベースに基づいているエンティティ データ モデルを含む .edmx ファイルを生成するボタンをクリックします。
<br />  ファイル、 **Model1.edmx**は、プロジェクトに追加され、データベース ダイアグラムが表示されます。
<br />

13. メニュー バーで、次のように選択します**ビュー**、**その他のウィンドウ**、 **Entity Data Model ブラウザー**モデルのすべての詳細を表示または**エンティティ データ モデル マッピングの詳細。**を開くには、生成されたオブジェクト モデルをデータベース テーブルと列にマップする方法を示すウィンドウです。
<br />


## <a name="next-steps"></a>次の手順
記載されている、使用可能なクエリ演算子を調べることで他のクエリを調査[クエリ式](../../language-reference/query-expressions.md)です。


## <a name="see-also"></a>関連項目
[型プロバイダー](index.md)

[EdmxFile 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[チュートリアル : 型プロバイダーおよびエンティティを使用した SQL データベースへのアクセス](accessing-a-sql-database-entities.md)

[Entity Framework](http://msdn.microsoft.com/data/ef)

[.edmx ファイルの概要](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[EDM ジェネレーター &#40;です。EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)

