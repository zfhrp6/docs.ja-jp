---
title: "dotnet-test コマンド - .NET Core CLI | Microsoft Docs"
description: "`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。"
keywords: "dotnet-test, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/25/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
ms.translationtype: Human Translation
ms.sourcegitcommit: ae036cfcad341ffc859336a7ab2a49feec145715
ms.openlocfilehash: 734cf337fdd0d33f6c2b6d929b795b2307135550
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>名前

`dotnet-test` - 単体テストを実行するために使用される .NET テスト ドライバー。

## <a name="synopsis"></a>構文

`dotnet test [<PROJECT>] [-s|--settings] [-t|--list-tests] [--filter] [-a|--test-adapter-path] [-l|--logger] [-c|--configuration] [-f|--framework] [-o|--output] [-d|--diag] [--no-build] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>説明

`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。 単体テストは、単体テスト フレームワーク (MSTest、NUnit、xUnit など) および単体テスト フレームワークの dotnet テスト ランナーに対する依存関係があるコンソール アプリケーションです。 これらは NuGet パッケージとしてパッケージ化され、プロジェクトの通常の依存関係として復元されます。

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

指定された式を使用して、現在のプロジェクト内のテストを除外します。 詳細については、「[フィルター オプションの詳細](#filter-option-details)」セクションをご覧ください。 選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。

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

## <a name="filter-option-details"></a>フィルター オプションの詳細

`--filter <EXPRESSION>`

`<Expression>` の形式は `<property><operator><value>[|&<Expression>]` です。

`<property>` は `Test Case` の属性です。 よく利用される単体テスト フレームワークでサポートされるプロパティは以下の通りです。

| テスト フレームワーク | サポートされるプロパティ                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>名前</li><li>ClassName</li><li>優先度</li><li>TestCategory</li></ul> |
| Xunit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Traits</li></ul>                                   |

`<operator>` は、プロパティと値の関係を示します。

| 演算子 | 関数        |
| :------: | --------------- |
| `=`      | 完全一致     |
| `!=`     | 完全一致ではない |
| `~`      | 内容        |

`<value>` は文字列です。 すべての参照で大文字と小文字が区別されます。

`<operator>` を含まない式は、自動的に `FullyQualifiedName` プロパティの `contains` とみなされます (たとえば、`dotnet test --filter xyz` は `dotnet test --filter FullyQualifiedName~xyz` と同じです)。

式は条件演算子を使用して結合できます。

| 演算子 | 関数 |
| :------: | :------: |
| `|`      | OR       |
| `&`      | AND      |

条件演算子を使用する場合は、式をかっこで囲みます (例: `(Name~TestMethod1) | (Name~TestMethod2)`)。

選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[フレームワークとターゲット](../../standard/frameworks.md)   
[.NET Core のランタイム識別子 (RID) のカタログ](../rid-catalog.md)

