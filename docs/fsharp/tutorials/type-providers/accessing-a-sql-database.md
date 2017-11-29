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
ms.openlocfilehash: c99afc1121b4f0d6d05ef82681a32437ede06e42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a>チュートリアル : 型プロバイダーを使用した SQL データベースへのアクセス

> [!NOTE]
このガイドでは、f# 3.0 用に作成された、更新されます。  最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](http://fsharp.github.io/FSharp.Data/) を参照してください。

> [!NOTE]
API リファレンス リンクで msdn を実行します。  docs.microsoft.com API リファレンスは完全ではありません。

このチュートリアルでは、データベースへのライブ接続がある場合は、SQL データベースでデータの型を生成する f# 3.0 で提供される SqlDataConnection (LINQ to SQL) 型プロバイダーを使用する方法について説明します。 場合は、データベースへのライブ接続することはありませんが、LINQ to SQL スキーマ ファイル (DBML ファイル) を参照してください。[チュートリアル: DBML ファイルから生成する f# 型](generating-fsharp-types-from-dbml.md)です。

このチュートリアルでは、次のタスクについて説明します。 これらのタスクは、チュートリアルでは成功するには、この順序で実行する必要があります。


- テスト データベースを準備します。

- プロジェクトの作成

- 型プロバイダーを設定します。

- データの照会

- Null 許容フィールドの操作

- ストアド プロシージャの呼び出し

- データベースの更新

- TRANSACT-SQL コードを実行します。

- 完全なデータ コンテキストを使用してください。

- データの削除

- 必要に応じて、テスト データベースを作成します。

## <a name="preparing-a-test-database"></a>テスト データベースを準備します。
SQL Server を実行するサーバーでは、テスト目的でデータベースを作成します。 データベースを使用するセクションでは、このページの下部にあるスクリプトを作成する[テスト データベースを作成する](#creating-a-test-database)これを行う。


#### <a name="to-prepare-a-test-database"></a>テスト データベースを準備するには

MyDatabase 作成スクリプトを実行するには、開く、**ビュー**  メニューを選択し**SQL Server オブジェクト エクスプ ローラー**かを選択して、ctrl キーを押しながら\,ctrl キーを押しながら S キー。 **SQL Server オブジェクト エクスプ ローラー**ウィンドウで、適切なインスタンスのショートカット メニューを開き、選択**新しいクエリ**、このページの下部にあるスクリプトをコピーし、エディターにスクリプトを貼り付けます。 SQL スクリプトを実行するには、三角形のシンボルでは、ツールバーのアイコンを選択するか、ctrl キーを押しながら Q キーを選択します。 詳細については**SQL Server オブジェクト エクスプ ローラー**を参照してください[接続されているデータベース開発](https://msdn.microsoft.com/library/hh272679(VS.103).aspx)です。


## <a name="creating-the-project"></a>プロジェクトの作成
次に、f# アプリケーション プロジェクトを作成します。


#### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには

1. 新しい f# アプリケーション プロジェクトを作成します。

2. 参照を追加[FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3)、だけでなく`System.Data`、および`System.Data.Linq`です。

3. F# コード ファイル Program.fs の先頭に次のコード行を追加することで、適切な名前空間を開きます。

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. ほとんど f# のプログラムと同様、コードを実行するには、コンパイル済みのプログラムとしては、このチュートリアルでまたはスクリプトとして対話形式で実行することができます。 スクリプトを使用する場合は、ショートカット メニューを開き、プロジェクト ノードを選択**新しい項目の追加**f# スクリプト ファイルを追加し、スクリプトに各手順でコードを追加します。 アセンブリの参照を読み込むファイルの上部にある次の行を追加する必要があります。

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  それを追加し、f# Interactive で実行するには、Alt + enter キーを押すと、各コード ブロックを選択できます。

## <a name="setting-up-a-type-provider"></a>型プロバイダーを設定します。
この手順では、データベース スキーマの型プロバイダーを作成します。


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a>データベースに直接接続から型プロバイダーを設定するには

型プロバイダーを使用して SQL データベースの照会に使用できる型を作成するために必要なコードの 2 つの重要な線があります。 最初に、型プロバイダーがインスタンス化します。 これを行うには、作成、型の省略形の外観、`SqlDataConnection`静的ジェネリック パラメーターを使用します。 `SqlDataConnection`SQL 型のプロバイダーと混同しないで`SqlConnection`となる型 ADO.NET プログラミングで使用します。 、に接続するデータベースが存在して接続文字列がある場合は、次のコードを使用して、型プロバイダーを呼び出します。 指定された文字列の例の独自の接続文字列を置き換えてください。 たとえば、MYSERVER とデータベース インスタンスはインスタンス、データベース名が MyDatabase であり、データベース、接続文字列にアクセスする Windows 認証を使用する場合は、サーバーとなる場合は、次のコード例で指定します。

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

これで、型を持つ`dbSchema`、データベース テーブルを表すすべての生成された型を含む親型です。 また、オブジェクトがある`db`を持つメンバーとして、データベース内のすべてのテーブルです。 テーブル名は、プロパティと、これらのプロパティの種類、f# コンパイラによって生成されます。 入れ子にされた型として型自体が表示される`dbSchema.ServiceTypes`です。 したがって、これらのテーブルの行の取得されたデータは、そのテーブルに対して生成された適切な型のインスタンスです。 型の名前は`ServiceTypes.Table1`します。

F# 言語が SQL クエリにクエリを解釈する方法を理解しておくための確認を設定する行、`Log`データ コンテキストのプロパティです。

型プロバイダーによって作成された型をさらに調査するには、するには、次のコードを追加します。

```fsharp
let table1 = db.Table1
```

ポインターを合わせる`table1`その型を表示します。 その型は`System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>`汎用引数の場合、各行の型が生成された型であることを示しますと`dbSchema.ServiceTypes.Table1`です。 コンパイラは、データベースのテーブルごとに、類似する型を作成します。

## <a name="querying-the-data"></a>データの照会
このステップでは、f# クエリ式を使用してクエリを記述します。


#### <a name="to-query-the-data"></a>データを照会するには

1. 今すぐデータベースにそのテーブルに対してクエリを作成します。 次のコードを追加します。

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  単語の外観`query`クエリ式では、一般的なデータベース クエリのような結果のコレクションを生成する計算式の型であることを示します。 クエリ上でマウス ポインターを移動する場合のインスタンスであることを確認は[Linq.QueryBuilder クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d)、クエリ コンピュテーション式を定義する型。 ポインターを合わせる場合`query1`のインスタンスであることがわかります`System.Linq.IQueryable`です。 名前からわかるように、 `System.Linq.IQueryable` 、照会するクエリの結果ではなくデータを表します。 クエリとは、クエリが評価されるときに、データベースは、のみことを意味の照会、レイジー評価される可能性があります。 最後の行を使用してクエリに渡します`Seq.iter`です。 クエリは、列挙可能なシーケンスのように繰り返し処理される場合があります。 詳細については、次を参照してください。[クエリ式](../../language-reference/query-expressions.md)です。

2. クエリにクエリ演算子を追加します。 複雑なクエリを構築するために使用できる利用できるクエリ演算子の数があります。 この例では、クエリ変数を排除し、代わりに、パイプライン演算子を使用することができますも示しています。

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. 2 つのテーブルの結合を使用した複雑なクエリを追加します。

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

4. 実際のコードでクエリ内のパラメーターは通常の値または変数、コンパイル時間ではなく定数です。 パラメーターを受け取るし、値 10 をその関数を呼び出している関数内のクエリをラップする次のコードを追加します。

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a>Null 許容フィールドの操作
データベースでは、フィールドは多くの場合、null 値を許可します。 .NET 型システムでは、使用可能な値として null をそれらの型を持たないため null 値を許容するデータの通常の数値データ型を使うことはできません。 これらの値がのインスタンスによって表されるため、`System.Nullable`型です。 このようなフィールドの値フィールドの名前で直接アクセスする、代わりに、追加の手順を追加する必要があります。 使用することができます、`System.Nullable.Value`プロパティを null 許容型の基になる値にアクセスします。 `System.Nullable.Value`プロパティは、オブジェクトが値ではなく null の場合に例外をスローします。 使用することができます、`System.Nullable.HasValue`値が存在するかどうかを使用するブール型のメソッド`System.Nullable.GetValueOrDefault()`を常に、実際の値があることを確認します。 使用する場合`System.Nullable.GetValueOrDefault()`し、データベースで null 値がある、置き換えられる文字列型の空の文字列などの値、整数型の場合は 0 またはフローティング 0.0 のポイントの種類。

Null 許容の値の等値テストや比較を実行する必要がある場合、`where`クエリ内の句については、null 許容の演算子を使用することができます、 [Linq.NullableOperators モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d)です。 これらは通常の比較演算子と同様、 `=`、 `>`、`<=`など、点を除いて、疑問符 (?) が表示される、演算子の右または左に、null 許容の値がします。 演算子など、`>?`が、大きい-より右側の null 許容の値を持つ演算子。 これらの演算子の動作方法は、式の両辺が null の場合に、式が評価`false`です。 `where`句、一般につまり null フィールドを含む行が選択されていない、クエリの結果では返されません。


#### <a name="to-work-with-nullable-fields"></a>Null 値許容フィールドを使用するには

次のコードは、null 許容の値の操作を示しています。あると想定**TestData1**整数フィールドであり、null 値を許容します。

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

## <a name="calling-a-stored-procedure"></a>ストアド プロシージャの呼び出し
データベースでストアド プロシージャは、f# から呼び出すことができます。 Static パラメーターを設定する必要があります`StoredProcedures`に`true`で型プロバイダーのインスタンス化します。 型プロバイダー`SqlDataConnection`生成される型の構成に使用できるいくつかの静的メソッドを格納します。 これらの詳細については、次を参照してください。 [SqlDataConnection 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)です。 データ コンテキスト型のメソッドでは、各ストアド プロシージャが生成されます。


#### <a name="to-call-a-stored-procedure"></a>ストアド プロシージャを呼び出すには

ストアド プロシージャが null 許容であるパラメーターを受け取る場合は、適切なを渡す必要があります。`System.Nullable`値。 スカラーまたはテーブルを返すストアド プロシージャ メソッドの戻り値は`System.Data.Linq.ISingleResult`、返されるデータにアクセスできるようにするプロパティが含まれています。 型引数を`System.Data.Linq.ISingleResult`特定のプロシージャに依存していても、型プロバイダーを生成する型のいずれかです。 という名前のストアド プロシージャの`Procedure1`、型が`Procedure1Result`です。 種類`Procedure1Result`名前を含む列、返されるテーブルにして、またはスカラー値を返すストアド プロシージャの戻り値を表します。

次のコードがあるものと、プロシージャ`Procedure1`パラメーターとして 2 つの null 許容型整数を受け取り、データベースをという名前の列を返すクエリが実行されて`TestData1`整数を返します。

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

## <a name="updating-the-database"></a>データベースの更新
LINQ DataContext 型には、生成された型と完全に型指定された方法でトランザクションのデータベースの更新を実行するが簡単にするメソッドが含まれています。


#### <a name="to-update-the-database"></a>データベースを更新するには

1. 次のコードでは、いくつかの行がデータベースに追加されます。 使用することができますのみ行を追加する場合`System.Data.Linq.Table.InsertOnSubmit()`を追加する新しい行を指定します。 複数の行を挿入する場合は、コレクションと呼び出しに配置するにする必要があります`System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`です。 これらのメソッドのいずれかを呼び出すときに、データベースはすぐに変更されません。 呼び出す必要があります`System.Data.Linq.DataContext.SubmitChanges`を実際には、変更をコミットします。 呼び出しをする前に行う操作は既定では、`System.Data.Linq.DataContext.SubmitChanges`同じトランザクションの一部では暗黙的にします。

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

2. 今すぐ削除操作を呼び出すことによって、行をクリーンアップします。

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

## <a name="executing-transact-sql-code"></a>TRANSACT-SQL コードを実行します。
TRANSACT-SQL を使用して直接指定することも、`System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])`メソッドを`DataContext`クラスです。


#### <a name="to-execute-custom-sql-commands"></a>カスタムの SQL コマンドを実行するには

次のコードでは、テーブルにレコードを挿入し、テーブルからレコードを削除する SQL コマンドを送信する方法を示します。

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

## <a name="using-the-full-data-context"></a>完全なデータ コンテキストを使用してください。
前の例で、`GetDataContext`と呼ばれるものを取得するメソッドが使用された、*簡易データ コンテキスト*データベース スキーマです。 簡易データ コンテキストは、できるだけ多くのメンバーがないために、クエリを構築するときに使用する簡単です。 そのため、IntelliSense でプロパティを参照するときは、テーブルおよびストアド プロシージャなど、データベースの構造に集中できます。 ただし、簡易データ コンテキストで行うことができますに制限があります。 その他のアクションを実行する機能を提供する完全なデータ コンテキスト。 使用可能なこの内にある、`ServiceTypes`の名前を持つ、 *DataContext* static パラメーター指定した場合。 指定しなかった場合、その他の入力に基づく SqlMetal.exe によって、データ コンテキスト型の名前が生成されます。 完全データ コンテキストが継承`System.Data.Linq.DataContext`など ADO.NET データ型への参照を含む、基底クラスのメンバーを公開し、`Connection`オブジェクトなどのメソッド`System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])`と`System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])`SQL では、クエリの作成に使用できます。明示的にトランザクションを処理することもできます。


#### <a name="to-use-the-full-data-context"></a>完全データ コンテキストを使用するには

次のコードは、完全データ コンテキスト オブジェクトを取得して、データベースに対して直接コマンドを実行する使用を示します。 この場合、2 つのコマンドは、同じトランザクションの一部として実行されます。

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

## <a name="deleting-data"></a>データの削除
この手順では、データ テーブルから行を削除する方法を示します。


#### <a name="to-delete-rows-from-the-database"></a>データベースから行を削除するには

これで、いずれかをクリーンアップするのインスタンスを指定したテーブルから行を削除する関数を記述して行を追加、`System.Data.Linq.Table`クラスです。 削除するすべての行を検索するクエリを記述しに、クエリの結果をパイプ、`deleteRows`関数。 このコードでは、関数の引数の部分的な適用を提供する機能を活用します。

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

## <a name="creating-a-test-database"></a>テスト データベースを作成します。
このセクションでは、このチュートリアルを使用して、テスト データベースを設定する方法を示します。

いくつかの方法でデータベースを変更する場合は、型プロバイダーをリセットする必要が注意してください。 型プロバイダーをリセットするには、再構築または型プロバイダーを含むプロジェクトをクリーンアップします。


#### <a name="to-create-the-test-database"></a>テスト データベースを作成するには

1. **サーバー エクスプ ローラー**、ショートカット メニューを開き、**データ接続** ノードを選択し、**接続の追加**です。 **接続の追加** ダイアログ ボックスが表示されます。

2. **サーバー名**ボックスでする管理アクセス権を持つ、SQL Server のインスタンスの名前を指定するか、サーバーへのアクセスがない (localdb\v11.0) を指定します。 SQL Express LocalDB は、コンピューターで開発およびテストの軽量のデータベース サーバーを提供します。 新しいノードが作成された**サーバー エクスプ ローラー** **データ接続**です。 LocalDB の詳細については、次を参照してください。[チュートリアル: Visual Studio でのローカル データベース ファイルの作成](https://msdn.microsoft.com/library/ms233763.aspx)です。

3. 新しい接続ノードのショートカット メニューを開き、選択**新しいクエリ**です。

4. 次の SQL スクリプトをコピー、クエリ エディターに貼り付けますおよびを選択し、 **Execute**ツールバーのボタンまたは Ctrl + shift キーを押しながら E キーを選択します。

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


## <a name="see-also"></a>関連項目
[型プロバイダー](index.md)

[SqlDataConnection 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[チュートリアル: DBML ファイルからの f# 型の生成](generating-fsharp-types-from-dbml.md)

[クエリ式](../../language-reference/query-expressions.md)

[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)

[SqlMetal.exe &#40;です。コード生成ツール &#41;](https://msdn.microsoft.com/library/bb386987)
