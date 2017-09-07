---
title: "dotnet-build コマンド - .NET Core CLI"
description: "dotnet-build コマンドは、プロジェクトとそのすべての依存関係をします。"
keywords: "dotnet-build, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2006b15978f384e53e43a0a2562e81d10582abd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-build"></a>dotnet-build

## <a name="name"></a>名前

`dotnet-build` - プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

`dotnet build [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-r|--runtime] [--version-suffix] [--no-incremental] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>説明

`dotnet build` コマンドは、プロジェクトとその依存関係をバイナリ セットにビルドします。 バイナリには、拡張子が *.dll* である中間言語 (IL) ファイルのプロジェクトのコードと、拡張子が *.pdb* でありデバッグに使われるシンボル ファイルが含まれます。 アプリケーションの依存関係を一覧表示する依存関係 JSON ファイル (*\*.deps.json*) が生成されます。 共有ランタイムと、そのアプリケーションのバージョンを指定する、*\*.runtimeconfig.json* ファイルが生成されます。

サードパーティ (NuGet のライブラリなど) との依存関係があるプロジェクトの場合、NuGet キャッシュから解決され、プロジェクトのビルドの出力では使うことができません。 この点を考慮すると、`dotnet build` の生成物は別のコンピューターに転送して実行することはできません。 これは .NET Framework の動作とは対照的です。.NET Framework の場合、実行可能なプロジェクト (アプリケーション) をビルドすると、.NET Framework がインストールされている任意のコンピューター上で実行できる出力が生成されます。 .NET Core でも同様の動作にするには、[dotnet publish](dotnet-publish.md) コマンドを使います。 詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。 

ビルドには *project.assets.json* ファイルが必要です。このファイルには、アプリケーションの依存関係が一覧表示されています。 このファイルは、プロジェクトをビルドする前に [`dotnet restore`](dotnet-restore.md) を実行すると作成されます。 アセット ファイルがないと、ツールは参照アセンブリを解決できないため、エラーになります。

`dotnet build` は MSBuild を使ってプロジェクトをビルドするので、並行ビルドとインクリメンタル ビルドの両方をサポートしています。 詳しくは、「[インクリメンタル ビルド](/visualstudio/msbuild/incremental-builds)」をご覧ください。 

このオプションに加え、`dotnet build` コマンドは、プロパティを設定する `/p` やロガーを定義する `/l` などの MSBuild オプションも受け入れます。 これらのオプションについて詳しくは、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」をご覧ください。 

プロジェクトを実行できるかどうかは、プロジェクト ファイルの `<OutputType>` プロパティで決まります。 次の例は、実行可能なコードを生成するプロジェクトを示しています。

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

ライブラリを生成するには、`<OutputType>` プロパティを省略してください。 ビルドされる出力の主な違いは、ライブラリの IL DLL にはエントリ ポイントが含まれず、実行できないことです。 

## <a name="arguments"></a>引数

`PROJECT`

ビルドするプロジェクト ファイル。 プロジェクト ファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* で終わるファイル名拡張子を検索し、そのファイルを使います。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-o|--output <OUTPUT_DIRECTORY>`

ビルド済みバイナリを配置するディレクトリ。 このオプションを指定する場合は、`--framework` を定義する必要もあります。

`-f|--framework <FRAMEWORK>`

特定の[フレームワーク](../../standard/frameworks.md)用にコンパイルします。 フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。

`-c|--configuration <CONFIGURATION>`

ビルド構成を定義します。 省略すると、ビルド構成は既定で `Debug` になります。 リリース構成をビルドするには `Release` を使います。

`-r|--runtime <RUNTIME_IDENTIFIER>`

ターゲットのランタイムを指定します。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。

`--version-suffix <VERSION_SUFFIX>`

プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) のバージョン サフィックスを定義します。 形式は NuGet のバージョン ガイドラインに従います。

`--no-incremental`

インクリメンタル ビルドとして安全でないビルドをマークします。 これにより、インクリメンタル コンパイルは無効になり、プロジェクトの依存関係グラフのクリーン再ビルドが強制的に行われます。

`--no-dependencies`

プロジェクト間 (P2P) 参照を無視し、ビルド対象として指定されたルート プロジェクトのみをビルドします。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>例

プロジェクトとその依存関係をビルドします。

`dotnet build`

リリース構成を使用して、プロジェクトとその依存関係をビルドします。

`dotnet build --configuration Release`

特定のランタイム (この例では、Ubuntu 16.04) 用にプロジェクトとその依存関係をビルドします。

`dotnet build --runtime ubuntu.16.04-x64`

