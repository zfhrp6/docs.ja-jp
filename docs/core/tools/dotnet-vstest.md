---
title: dotnet vstest コマンド - .NET Core CLI
description: dotnet vstest コマンドは、プロジェクトとそのすべての依存関係をビルドします。
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: e11b193ff7a8c639078c5cf279b7fbbeab553c92
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet-vstest` - 指定されたファイルからテストを実行します。

## <a name="synopsis"></a>構文

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a>説明

`dotnet-vstest` コマンドでは、`VSTest.Console` コマンド ライン アプリケーションを実行し、自動化された単体とコード化された UI アプリケーション テストを実行します。

## <a name="arguments"></a>引数

`TEST_FILE_NAMES`

指定されたアセンブリからテストを実行します。 複数のテスト アセンブリ名を指定するときは、空白で区切ります。

## <a name="options"></a>オプション

`--Settings|/Settings:<Settings File>`

テストの実行時に使用される設定です。

`--Tests|/Tests:<Test Names>`

指定した値に一致する名前のテストを実行します。 複数の値を指定するときは、コンマで区切ります。

`--TestAdapterPath|/TestAdapterPath`

テストの実行では、指定されたパス (存在する場合) からカスタム テスト アダプターを使用します。

`--Platform|/Platform:<Platform type>`

テストの実行に使用する対象のプラットフォーム アーキテクチャです。 有効な値は `x86`、`x64`、`ARM` です。

`--Framework|/Framework:<Framework Version>`

テストの実行に使用する対象の .NET Framework バージョンです。 有効な値の例としては、`.NETFramework,Version=v4.6`、`.NETCoreApp,Version=v1.0` などがあります。サポートされるその他の値は、`Framework35`、`Framework40`、`Framework45`、および `FrameworkCore10` です。

`--Parallel|/Parallel`

テストを並列で実行します。 既定では、コンピューター上のすべての使用可能なコアを使用できます。 設定ファイルを使用して、明示的なコア数を設定します。

`--TestCaseFilter|/TestCaseFilter:<Expression>`

指定した式に一致するテストを実行します。 `<Expression>` の形式は `<property>Operator<value>[|&<Expression>]` です。この場合の演算子は `=`、`!=`、または `~` のいずれかになります。  演算子 `~` は 'contains' セマンティクスを持ち、`DisplayName` などの文字列プロパティに適用できます。 かっこ `()` はサブ式をグループ化するために使用します。

`-?|--Help|/?|/Help`

コマンドの短いヘルプを印刷します。

`--logger|/logger:<Logger Uri/FriendlyName>`

テスト結果のロガーを指定します。  

* Team Foundation Server にテスト結果を発行するには、次のように `TfsPublisher` ロガー プロバイダーを使用します。

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Visual Studio テスト結果ファイル (TRX) に結果のログを書き込むには、`trx` ロガー プロバイダーを使用します。 このように切り替えることで、テスト結果ディレクトリに指定のログ ファイル名でファイルが作成されます。 `LogFileName` が指定されていない場合は、テスト結果を保持するために一意のファイル名が作成されます。

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

指定されたテスト コンテナーから探索されたテストを一覧表示します。

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

現在のプロセスを起動する親プロセスのプロセス ID です。

`--Port|/Port:<Port>`

ソケット接続およびイベント メッセージの受信用のポートを指定します。

`--Diag|/Diag:<Path to log file>`

テスト プラットフォームの詳細ログを有効にします。 指定されたファイルにログが書き込まれます。

`args`

アダプターに渡す追加の引数を指定します。 引数は `<n>=<v>` 形式の名前と値のペアとして指定されます。この場合の `<n>` は引数名、`<v>` は引数値です。 複数の引数を指定する場合は、空白で区切ります。

## <a name="examples"></a>使用例

`mytestproject.dll` でテストを実行する:

`dotnet vstest mytestproject.dll`

`mytestproject.dll` でテストを実行し、カスタム名を持つカスタム フォルダーにエクスポートします。

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

`mytestproject.dll` と `myothertestproject.exe` でテストを実行する:

`dotnet vstest mytestproject.dll myothertestproject.exe`

`TestMethod1` テストを実行する:

`dotnet vstest /Tests:TestMethod1`

`TestMethod1` および `TestMethod2` テストを実行する:

`dotnet vstest /Tests:TestMethod1,TestMethod2`

