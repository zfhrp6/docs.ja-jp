---
title: "チュートリアル : DBML ファイルからの F# 型の生成 (F#)"
description: ".Dbml ファイルにエンコード スキーマ情報がある場合、f# 3.0 でのデータベースからデータの f# 型を作成する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: a919c2acb2b5b8c2ce93124f2f541bd092d15c35
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a>チュートリアル : DBML ファイルからの F# 型の生成

> [!NOTE]
このガイドでは、f# 3.0 用に作成された、更新されます。  最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](http://fsharp.github.io/FSharp.Data/) を参照してください。

> [!NOTE]
API リファレンス リンクで msdn を実行します。  docs.microsoft.com API リファレンスは完全ではありません。

F# 3.0 に関するこのチュートリアルでは、スキーマ情報を格納する .dbml ファイルにエンコードがある場合、データベースからデータの型を作成する方法について説明します。 LINQ to SQL では、このファイル形式を使用して、データベース スキーマを表します。 オブジェクト リレーショナル (O/R) のデザイナーを使用して Visual Studio での LINQ to SQL スキーマ ファイルを生成できます。 詳細については、次を参照してください。 [O/r デザイナーの概要](https://msdn.microsoft.com/library/bb384511.aspx)と[LINQ to SQL でのコード生成](../../../../docs/framework/data/adonet/sql/linq/index.md)です。

データベース マークアップ言語 (DBML) 型プロバイダーでは、コンパイル時に静的な接続文字列を指定する必要がなく、データベース スキーマに基づいた型を使用するコードを記述することができます。 最終のアプリケーションが別のデータベース、別の資格情報、またはよりも、アプリケーションの開発に使用する 1 つの異なる接続文字列に使用することを許可する必要がある場合に便利にすることができます。 コンパイル時に使用できるデータベースに直接接続があり、これは、同じデータベースと資格情報を最終的にビルドされたアプリケーションで使用する場合も、SQLDataConnection 型プロバイダーを使用することができます。 詳細については、次を参照してください。[チュートリアル: 型プロバイダーを使用して SQL データベースへのアクセス](accessing-a-sql-database.md)です。

このチュートリアルでは、次のタスクについて説明します。 これらは、チュートリアルでは成功するには、この順序で完了する必要があります。


- .Dbml ファイルを作成します。
<br />

- 作成、f# プロジェクトの設定
<br />

- 型プロバイダーを構成して、型の生成
<br />

- データベースの照会
<br />


## <a name="prerequisites"></a>必須コンポーネント

## <a name="creating-a-dbml-file"></a>.Dbml ファイルを作成します。
場合は、データベースでテストする必要はありません、作成の下部にある指示に従って[チュートリアル: 型プロバイダーを使用して SQL データベースへのアクセス](accessing-a-sql-database.md)です。 これらの手順を実行する場合は、いくつかの単純なテーブルと、SQL Server 上のストアド プロシージャを含む MyDatabase をという名前のデータベースを作成します。

.Dbml ファイルがある場合、セクションにスキップできます**設定を f# プロジェクトの作成と**です。 それ以外の場合、既存の SQL データベースを指定して .dbml ファイルを作成し、コマンドラインを使用してツール SqlMetal.exe できます。


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a>SqlMetal.exe を使用して .dbml ファイルを作成するには

1. 開く、**開発者コマンド プロンプト**です。
<br />

2. 入力して SqlMetal.exe へのアクセスがあることを確認してください。`SqlMetal.exe /?`コマンド プロンプトでします。 SqlMetal.exe が通常インストールされている、 **Microsoft SDKs**フォルダー **Program Files**または**%program Files (x86)**です。
<br />

3. 次のコマンド ライン オプションには、SqlMetal.exe を実行します。 代わりに適切なパスを置き換える`c:\destpath`.dbml ファイルを作成し、データベース サーバーの適切な値を挿入、名、およびデータベース名をインスタンス化します。
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
SqlMetal.exe にアクセス許可の問題により、ファイルの作成の問題がある場合への書き込みアクセスのあるフォルダーに、現在のディレクトリを変更します。


4. 他の使用可能なコマンド ライン オプションを参照することもできます。 たとえば、ビューと、生成された型に含まれる SQL 関数したい場合に使用できるオプションがあります。 詳細については、次を参照してください。 [SqlMetal.exe &#40;です。コード生成ツール &#41;](https://msdn.microsoft.com/library/bb386987).
<br />


## <a name="creating-and-setting-up-an-f-project"></a>作成、f# プロジェクトの設定
このステップでは、プロジェクトを作成し、DBML 型プロバイダーを使用する適切な参照を追加します。


#### <a name="to-create-and-set-up-an-f-project"></a>F# プロジェクトを作成してセットアップするには

1. 新しい f# コンソール アプリケーション プロジェクトをソリューションに追加します。
<br />

2. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、**参照**を選択し**参照の追加**です。
<br />

3. **アセンブリ**領域で、選択、 **Framework**  ノードをクリックし、使用可能なアセンブリの一覧で、選択、 **System.Data**と**System.Data.Linq**アセンブリ。
<br />

4. **アセンブリ**領域で、選択**拡張**をクリックし、使用可能なアセンブリの一覧で、選択**FSharp.Data.TypeProviders**です。
<br />

5. 選択、 **OK**これらのアセンブリへの参照をプロジェクトに追加するボタンをクリックします。
<br />

6. (省略可能) 前の手順で作成した .dbml ファイルをコピーし、ファイル、プロジェクトのメイン フォルダーに貼り付けます。 このフォルダーには、プロジェクト ファイル (.fsproj) およびコード ファイルが含まれています。 メニュー バーで、次のように選択します。**プロジェクト**、**既存項目の追加**、し、プロジェクトに追加する .dbml ファイルを指定します。 これらの手順を実行する場合は、次の手順で ResolutionFolder static パラメーターを省略できます。
<br />

## <a name="configuring-the-type-provider"></a>型プロバイダーの構成
このセクションでは、型プロバイダーを作成し、.dbml ファイルに記載されているスキーマから型を生成します。


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a>型プロバイダーを構成して、型を生成するには

- 表示されたコードを追加、 **TypeProviders**名前空間を使用する .dbml ファイルの型プロバイダーをインスタンス化します。 プロジェクトに .dbml ファイルを追加する場合は、ResolutionFolder static パラメーターを省略できます。
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

DataContext 型が生成されたすべての型へのアクセスを提供しから継承`System.Data.Linq.DataContext`です。 DbmlFile 型プロバイダーが、さまざまな静的パラメーターを設定できます。 たとえばを指定して、DataContext 型の別の名前を使用することができます`DataContext=MyDataContext`です。 その場合は、コードでは、次の例ようになります。
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a>データベースの照会
このセクションでは、f# クエリ式を使用するデータベースを照会します。


#### <a name="to-query-the-data"></a>データを照会するには

- データベースを照会するコードを追加します。
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a>次の手順
その他のクエリ式を使用またはデータ コンテキストから、データベース接続を取得し、通常の ADO.NET データ操作を実行する続行することができます。 追加の手順を参照してください「のデータのクエリ」の後で[チュートリアル: 型プロバイダーを使用して SQL データベースへのアクセス](accessing-a-sql-database.md)です。


## <a name="see-also"></a>関連項目
[DbmlFile 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[型プロバイダー](index.md)

[チュートリアル : 型プロバイダーを使用した SQL データベースへのアクセス](accessing-a-sql-database.md)

[SqlMetal.exe &#40;です。コード生成ツール &#41;](https://msdn.microsoft.com/library/bb386987)

[クエリ式](../../language-reference/query-expressions.md)
