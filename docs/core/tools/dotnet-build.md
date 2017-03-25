---
title: "dotnet-build コマンド | Microsoft Docs"
description: "dotnet-build コマンドは、プロジェクトとそのすべての依存関係をします。"
keywords: "dotnet-build, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 17c2db54f871795c370a6475c21e36736a6b46c3
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-build"></a>dotnet-build

## <a name="name"></a>名前

`dotnet-build` - プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

```
dotnet build [project] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity]
dotnet build [--help]
```

## <a name="description"></a>説明
`dotnet build` コマンドは、プロジェクトとその依存関係をバイナリ セットにビルドします。 バイナリは、デバッグに使用するシンボル ファイル (拡張子が `*.pdb`) と中間言語 (IL) のプロジェクトのコード (拡張子が `*.dll`) です。 また、アプリケーションの依存関係を列挙する JSON ファイル (拡張子が `*.deps.json`) が生成されます。 最後に、`runtime.config.json` ファイルも生成されます。 このファイルで、ビルドされるコードを実行する共有ランタイムとバージョンを指定します。 

サードパーティ (NuGet のライブラリなど) との依存関係があるプロジェクトの場合、NuGet キャッシュから解決され、プロジェクトのビルドの出力では使用できません。 この点を考慮すると、`dotnet build` の生成物は別のコンピューターに転送して実行することはできません。 これは .NET Framework の動作とは対照的です。.NET Framework の場合、実行可能なプロジェクト (アプリケーション) をビルドすると、.NET Framework がインストールされている任意のコンピューター上で実行できる出力が生成されます。 .NET Core でも同様の動作にするには、[dotnet publish](dotnet-publish.md) コマンドを使用する必要があります。 詳細については、「[.NET Core アプリケーション展開](../deploying/index.md)」を参照してください。 

ビルドには、*assets.json* ファイル (アプリケーションのすべての依存関係を一覧するファイル) が存在している必要があります。つまり、プロジェクトをビルドする前に [`dotnet restore`](dotnet-restore.md) を実行する必要があるということです。 ツールのエラーによりアセット ファイル マニフェストがないと、参照アセンブリを解決できないため、エラーになります。 

`dotnet build` は MSBuild を使用してプロジェクトをビルドするので、並行ビルドとインクリメンタル ビルドの両方をサポートしています。 これらのトピックの詳細については、[MSBuild のドキュメント](https://docs.microsoft.com/visualstudio/msbuild/msbuild)を参照してください。 

このオプションに加え、`dotnet build` コマンドは、プロパティを設定する `/p` やロガーを定義する `/l` などの MSBuild オプションも受け入れます。 これらのオプションを使用する場合の詳細については、[`dotnet msbuild`](dotnet-msbuild.md) コマンドのドキュメントを参照してください。 参照してください 

プロジェクトを実行できるかどうかは、プロジェクト ファイルの `<OutputType>` プロパティで決まります。 次の例は、実行可能なコードを生成するプロジェクトを示しています。 


```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

ライブラリを生成するには、このプロパティを省略してください。 出力の主な違いは、ライブラリの IL DLL には、エントリ ポイントが含まれず、実行できないということです。 

## <a name="arguments"></a>引数

`project`

ビルドするプロジェクト ファイル。
プロジェクト ファイルを指定しない場合、MSBuild は、現在の作業ディレクトリからファイル名拡張子 `proj` を検索し、そのファイルを使用します。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-o|--output <OUTPUT_DIRECTORY>`

ビルド済みバイナリを配置するディレクトリ。 このオプションを指定する場合は、`--framework` を定義する必要もあります。

`-f|--framework <FRAMEWORK>`

特定のフレームワーク用にコンパイルします。 フレームワークは、[project file](csproj.md) に定義する必要があります。

`-c|--configuration [Debug|Release]`

ビルドに使用する構成を定義します。 省略した場合は、既定で `Debug` に設定されます。

`-r|--runtime [RUNTIME_IDENTIFIER]`

ビルドのターゲット ランタイムです。 使用できるランタイム ID (RID) については、[RID カタログ](../rid-catalog.md)に関するページを参照してください。

`--version-suffix [VERSION_SUFFIX]`

プロジェクト ファイルのバージョン フィールドで `*` を置き換える必要がある値を定義します。 形式は NuGet のバージョン ガイドラインに従います。

`--no-incremental`

インクリメンタル ビルドとして安全でないビルドをマークします。 これにより、インクリメンタル コンパイルは無効になり、プロジェクトの依存関係グラフのクリーン再ビルドが強制的に行われます。

`--no-dependencies`

プロジェクト間参照を無視し、ビルド対象として指定されたルート プロジェクトのみをビルドします。

`-v|--verbosity`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>例

プロジェクトとその依存関係をビルドします。

`dotnet build`

リリース構成を使用して、プロジェクトとその依存関係をビルドします。

`dotnet build --configuration Release`

特定のランタイム (この例では、Ubuntu 16.04) 用にプロジェクトとその依存関係をビルドします。

`dotnet build --runtime ubuntu.16.04-x64`
