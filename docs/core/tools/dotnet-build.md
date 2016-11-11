---
title: "dotnet-build コマンド | .NET Core SDK"
description: "dotnet-build コマンドは、プロジェクトとそのすべての依存関係をします。"
keywords: "dotnet-build, CLI, CLI コマンド, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 70285a83-4103-4617-be8b-d0e1e9a4a91d
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: 344f8154c63bbb3c5ce6840bc7c7b1659950c223

---

#<a name="dotnetbuild"></a>dotnet-build

## <a name="name"></a>名前 
dotnet-build -- プロジェクトとそのすべての依存関係をビルドします。 

## <a name="synopsis"></a>構文

`dotnet build [--help] [--output]  
    [--build-base-path] [--framework]  
    [--configuration]  [--runtime] [--version-suffix]
    [--build-profile]  [--no-incremental] [--no-dependencies]
    [<project>]`

## <a name="description"></a>説明

`dotnet build` コマンドは、ソース プロジェクトとその依存関係から複数のソース ファイルをバイナリにビルドします。 既定では、結果のバイナリは中間言語 (IL) になり、拡張子は DLL になります。 
`dotnet build` は、ホストがアプリケーションを実行するために必要なものの概要を示す `\*.deps` ファイルのドロップも行います。  

ビルドにはロック ファイルが必要です。つまり、コードをビルドする前に [`dotnet restore`](dotnet-restore.md) を実行する必要があります。

すべてのコンパイルが始まる前に、`build` 動詞で安全性のインクリメンタル チェックのためにプロジェクトとその依存関係が分析されます。
すべてのチェックをパスした場合、ビルドはプロジェクトとその依存関係のインクリメンタル コンパイルに進みます。それ以外の場合は、非インクリメンタル コンパイルに戻ります。 プロファイル フラグを使用することで、ユーザーはビルド時間を向上させる方法に関する追加情報を受信するように選択できます。

コンパイル プロセスをインクリメンタルに行うには、コンパイルを必要とする依存関係グラフのすべてのプロジェクトが以下の安全性チェックをパスする必要があります。
- プリコンパイル/ポストコンパイル スクリプトを使用しない
- パスからコンパイル ツール (resgen、コンパイラなど) を読み込まない
- 既知のコンパイラ (csc、vbc、fsc) のみを使用する

ライブラリではなく、実行可能なアプリケーションをビルドするには、project.json ファイルに[特別な構成](project-json.md#emitentrypoint)セクションが必要です。

```json
{ 
    "buildOptions": {
      "emitEntryPoint": true
    }
}
```

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-o|--output <OUTPUT_DIRECTORY>`

ビルド済みバイナリを配置するディレクトリ。 このオプションを指定する場合は、`--framework` を定義する必要もあります。

`-b|--build-base-path <OUTPUT_DIRECTORY>`

一時出力を配置するディレクトリ。

`-f|--framework <FRAMEWORK>`

特定のフレームワーク用にコンパイルします。 フレームワークは [project.json](project-json.md#frameworks) ファイルに定義する必要があります。

`-c|--configuration [Debug|Release]`

ビルドに使用する構成を定義します。  省略した場合は、既定で `Debug` に設定されます。

`-r|--runtime [RUNTIME_IDENTIFIER]`

ビルドのターゲット ランタイムです。 使用できるランタイム ID (RID) については、[RID カタログ](../rid-catalog.md)に関するページを参照してください。 

`--version-suffix [VERSION_SUFFIX]`

[project.json](project-json.md#version) ファイルのバージョン フィールドで `*` を置き換える必要がある値を定義します。 形式は NuGet のバージョン ガイドラインに従います。 

`--build-profile`

インクリメンタル コンパイルを自動的に有効にするために、ユーザーが行う必要のある安全性のインクリメンタル チェックを印刷します。

`--no-incremental`

インクリメンタル ビルドとして安全でないビルドをマークします。 これにより、インクリメンタル コンパイルは無効になり、プロジェクトの依存関係グラフのクリーン再ビルドが強制的に行われます。

`--no-dependencies`

プロジェクト間参照を無視し、ビルド対象として指定されたルート プロジェクトのみをビルドします。

## <a name="examples"></a>例

プロジェクトとその依存関係をビルドします。

`dotnet build`

リリース構成を使用して、プロジェクトとその依存関係をビルドします。

`dotnet build --configuration Release`

特定のランタイム (この例では、Ubuntu 16.04) 用にプロジェクトとその依存関係をビルドします。

`dotnet build --runtime ubuntu.16.04-x64`


<!--HONumber=Nov16_HO1-->


