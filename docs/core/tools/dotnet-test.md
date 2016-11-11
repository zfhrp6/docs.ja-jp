---
title: "dotnet-test コマンド | .NET Core SDK"
description: "`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。"
keywords: "dotnet-test, CLI, CLI コマンド, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: b12861f0ce3c40bf4db51994ea5d4a92b8ef0162

---

#<a name="dotnettest"></a>dotnet-test

## <a name="name"></a>Name

`dotnet-test`- 構成済みのテスト ランナーを使用して、単体テストを実行します。

## <a name="synopsis"></a>構文

`dotnet test [project] [--help] 
    [--parentProcessId] [--port] [--configuration]   
    [--output] [--build-base-path] [--framework] [--runtime]
    [--no-build]`  

## <a name="description"></a>説明

`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。 単体テストは、単体テスト フレームワーク (NUnit や xUnit など) およびその単体テスト フレームワークの dotnet テスト ランナーに対する依存関係があるクラス ライブラリ プロジェクトです。 これらは NuGet パッケージとしてパッケージ化され、プロジェクトの通常の依存関係として復元されます。

テスト プロジェクトでは、"testRunner" ノードを使用して project.json にテスト ランナー プロパティを指定する必要もあります。 この値には、単体テスト フレームワークの名前を含める必要があります。

次のサンプルの project.json では必要なプロパティが示されています。

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {
    "System.Runtime.Serialization.Primitives": "4.1.1",
    "xunit": "2.1.0",
    "dotnet-test-xunit": "1.0.0-rc2-192208-24"
  },
  "testRunner": "xunit",
  "frameworks": {
    "netcoreapp1.0": {
      "dependencies": {
        "Microsoft.NETCore.App": {
          "type": "platform",
          "version": "1.0.0"
        }
      },
      "imports": [
        "dotnet5.4",
        "portable-net451+win8"
      ]
    }
  }
}
```

`dotnet test`では、以下の 2 つの実行モードがサポートされます。

1. コンソール: コンソール モードでは、`dotnet test` は単に渡されたコマンドを完全に実行し、結果を出力します。 --port を渡さずに `dotnet test` を呼び出すと、常にコンソール モードで実行されるため、ランナーはコンソール モードで実行されます。
2. デザイン時: エディターや統合開発環境 (IDE) などの他のツールのコンテキストで使用されます。 このモードの詳細については、[dotnet-test プロトコル](test-protocol.md) のドキュメントを参照してください。 

## <a name="options"></a>オプション

`[project]`
    
テスト プロジェクトへのパスを指定します。 省略すると、既定で現在のディレクトリに設定されます。

`-?|-h|--help`

コマンドの短いヘルプを印刷します。

`--parentProcessId`

IDE でプロセス ID を指定するために使用されます。 親プロセスが終了すると、テストは終了します。

`--port`

IDE で接続をリッスンするポートの番号を指定するために使用されます。

`-c|--configuration <Debug|Release>`

ビルドに使用する構成です。 既定値は `Release` です。 

`-o|--output [OUTPUT_DIRECTORY]`

実行するバイナリを検索するディレクトリです。

`-b|--build-base-path <OUTPUT_DIRECTORY>`

一時出力を配置するディレクトリ。

`-f|--framework [FRAMEWORK]`

特定のフレームワークのテスト バイナリを検索します。

`-r|--runtime [RUNTIME_IDENTIFIER]`

指定されたランタイムのテスト バイナリを検索します。

`--no-build` 

実行の前にテスト プロジェクトをビルドしません。 

## <a name="examples"></a>例

現在のディレクトリのプロジェクトでテストを実行します。

`dotnet test` 

test1 プロジェクトでテストを実行します。

`dotnet test /projects/test1/project.json` 

## <a name="see-also"></a>関連項目

[dotnet-test 通信プロトコル](test-protocol.md)

[フレームワーク](../../standard/frameworks.md)

[ランタイム識別子 (RID) のカタログ](../rid-catalog.md)


<!--HONumber=Nov16_HO1-->


