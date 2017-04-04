---
title: "dotnet-test コマンド - .NET Core CLI | Microsoft Docs"
description: "`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。"
keywords: "dotnet-test, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 26b5834135db8041995a137f5008d00cdf14d820
ms.lasthandoff: 03/22/2017

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>名前

`dotnet-test` - 単体テストを実行するために使用される .NET テスト ドライバー。

## <a name="synopsis"></a>構文

`dotnet test [<PROJECT>] [-s|--settings] [-t|--list-tests] [--filter] [-a|--test-adapter-path] [-l|--logger] [-c|--configuration] [-f|--framework] [-o|--output] [-d|--diag] [--no-build] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>説明

`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。 単体テストは、単体テスト フレームワーク (MSText、NUnit、xUnit など) および単体テスト フレームワークの dotnet テスト ランナーに対する依存関係があるクラス ライブラリ プロジェクトです。 これらは NuGet パッケージとしてパッケージ化され、プロジェクトの通常の依存関係として復元されます。

テスト プロジェクトでは、テスト ランナーを指定する必要もあります。 これは、通常の `<PackageReference>` 要素を使用して指定されます。次のサンプル プロジェクト ファイルのようになります。

[!code-xml[XUnit 基本テンプレート](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="options"></a>オプション

`PROJECT`
    
テスト プロジェクトへのパスを指定します。 省略すると、既定で現在のディレクトリに設定されます。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-s|--settings <SETTINGS_FILE>`

テストの実行時に使用される設定です。 

`-t|--list-tests`

現在のプロジェクトで検出されたすべてのテストを一覧表示します。 

`--filter <EXPRESSION>`

指定された式を使用して、現在のプロジェクト内のテストを除外します。 フィルタリングの詳細については、「[Running selective unit tests in Visual Studio using TestCaseFilter](https://aka.ms/vstest-filtering)」 (TestCaseFilter を利用し、Visual Studio で選択的単体テストを実行する) を参照してください。

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

テスト実行で指定されたパスからカスタムのテスト アダプターを使用します。 

`-l|--logger <LoggerUri/FriendlyName>`

テスト結果のロガーを指定します。 

`-c|--configuration <CONFIGURATION>`

ビルドに使用する構成です。 既定値は `Debug` ですが、プロジェクトの構成がこの既定の SDK 設定に優先する可能性があります。

`-f|--framework <FRAMEWORK>`

特定の[フレームワーク](../../standard/frameworks.md)のテスト バイナリを検索します。

`-o|--output <OUTPUT_DIRECTORY>`

実行するバイナリを検索するディレクトリです。

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

テスト プラットフォームの診断モードを有効にし、指定したファイルに診断メッセージを出力します。 

`--no-build` 

実行の前にテスト プロジェクトをビルドしません。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>例

現在のディレクトリのプロジェクトでテストを実行します。

`dotnet test` 

`test1` プロジェクトでテストを実行します。

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>関連項目

* [ターゲット フレームワーク](../../standard/frameworks.md)
* [ランタイム識別子 (RID) のカタログ](../rid-catalog.md)
