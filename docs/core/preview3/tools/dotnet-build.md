---
title: "dotnet-build コマンド | Microsoft Docs"
description: "dotnet-build コマンドは、プロジェクトとそのすべての依存関係をします。"
keywords: "dotnet-build, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: d2eeeccd6b3bdf82ba02fea6ce89785ef19d4116

---

#<a name="dotnet-build-tooling-preview-4"></a>dotnet-build (Tooling Preview 4)

> [!WARNING]
> このトピックは、Visual Studio 2017 RC - .NET Core Tools Preview 4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[dotnet-build](../../tools/dotnet-build.md)」トピックを参照してください。

## <a name="name"></a>名前 
dotnet-build -- プロジェクトとそのすべての依存関係をビルドします。 

## <a name="synopsis"></a>構文

`dotnet build [--help] [--output]  [--framework]  
    [--configuration]  [--runtime] [--version-suffix]
    [--build-profile]  [--no-incremental] [--no-dependencies]
    [<project>]`

## <a name="description"></a>説明

`dotnet build` コマンドは、ソース プロジェクトとその依存関係から複数のソース ファイルをバイナリにビルドします。 既定では、結果のバイナリは中間言語 (IL) になり、拡張子は DLL になります。 
`dotnet build` は、ホストがアプリケーションを実行するために必要なものの概要を示す `*.deps` ファイルのドロップも行います。  

ビルドには、アセット ファイル (アプリケーションのすべての依存関係を一覧するファイル) が存在している必要があります。つまり、コードをビルドする前に [`dotnet restore`](dotnet-restore.md) を実行する必要があるということです。

すべてのコンパイルが始まる前に、`build` 動詞で安全性のインクリメンタル チェックのためにプロジェクトとその依存関係が分析されます。
すべてのチェックをパスした場合、ビルドはプロジェクトとその依存関係のインクリメンタル コンパイルに進みます。それ以外の場合は、非インクリメンタル コンパイルに戻ります。 プロファイル フラグを使用することで、ユーザーはビルド時間を向上させる方法に関する追加情報を受信するように選択できます。

ライブラリではなく、実行可能アプリケーションをビルドするには、`<OutputType>` プロパティを設定する必要があります。

```xml
<PropertyGroup>
    <OutputType>Exe</OutputType>
</PropertyGroup>
```

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-o|--output <OUTPUT_DIRECTORY>`

ビルド済みバイナリを配置するディレクトリ。 このオプションを指定する場合は、`--framework` を定義する必要もあります。

`-f|--framework <FRAMEWORK>`

特定のフレームワーク用にコンパイルします。 フレームワークは、[project file](csproj.md) に定義する必要があります。

`-c|--configuration [Debug|Release]`

ビルドに使用する構成を定義します。  省略した場合は、既定で `Debug` に設定されます。

`-r|--runtime [RUNTIME_IDENTIFIER]`

ビルドのターゲット ランタイムです。 使用できるランタイム ID (RID) については、[RID カタログ](../../rid-catalog.md)に関するページを参照してください。 

`--version-suffix [VERSION_SUFFIX]`

プロジェクト ファイルのバージョン フィールドで `*` を置き換える必要がある値を定義します。 形式は NuGet のバージョン ガイドラインに従います。 

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



<!--HONumber=Jan17_HO3-->


