---
title: "dotnet-publish コマンド - .NET Core CLI"
description: "dotnet-publish コマンドは、.NET Core プロジェクトをディレクトリに発行します。"
keywords: "dotnet-publish, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a8a37b1eacab13682d4f4a2bea2f9ea248cdd9eb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>名前

`dotnet-publish` - ホスティング システムへの展開のため、アプリケーションとその依存関係をフォルダーにパックします。

## <a name="synopsis"></a>構文

`dotnet publish [<PROJECT>] [-f|--framework] [-r|--runtime] [-o|--output] [-c|--configuration] [--version-suffix] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>説明

`dotnet publish` はアプリケーションをコンパイルし、プロジェクト ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。 出力の内容は次のとおりです。

* アセンブリの中間言語 (IL) コード (拡張子 `*.dll`)。
* *\*.deps.json* ファイル。プロジェクトのすべての依存関係が含まれます。
* *\*.runtime.config.json* ファイル。アプリケーションが想定する共有ランタイムと、ランタイムの他の構成オプション (ガベージ コレクションの種類など) を指定します。
* アプリケーションの依存関係。 これらは NuGet キャッシュから出力フォルダーにコピーされます。

`dotnet publish` コマンドの出力は、ホスティング システム (サーバー、PC、Mac、ラップトップなど) に展開して実行できる状態になっており、展開用にアプリケーションを準備するための正式にサポートされる唯一の方法です。 プロジェクトに指定されている展開の種類によっては、ホスティング システムに .NET Core 共有ランタイムがインストールされている場合とされていない場合があります。 詳しくは、「[.NET Core アプリケーション展開](../deploying/index.md)」をご覧ください。 発行されるアプリケーションのディレクトリ構造については、「[Directory structure](/aspnet/core/hosting/directory-structure)」 (ディレクトリ構造) をご覧ください。

## <a name="arguments"></a>引数

`PROJECT` 

発行するプロジェクトです。指定されていない場合は、既定で現在のディレクトリに設定されます。 

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-f|--framework <FRAMEWORK>`

指定した[ターゲット フレームワーク](../../standard/frameworks.md)のアプリケーションを発行します。 ターゲット フレームワークはプロジェクト ファイルで指定する必要があります。

`-r|--runtime <RUNTIME_IDENTIFIER>`

指定されたランタイムのアプリケーションを発行します。 これは、[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd) を作成するときに使われます。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。 既定では、[フレームワークに依存する展開 (FDD)](../deploying/index.md#framework-dependent-deployments-fdd) が発行されます。

`-o|--output <OUTPUT_DIRECTORY>`

出力ディレクトリのパスを指定します。 指定しないと、既定で、フレームワークに依存する展開の場合は *./bin/[configuration]/[framework]/* に、自己完結型の展開の場合は *./bin/[configuration]/[framework]/[runtime]* に設定されます。

`-c|--configuration <CONFIGURATION>`

プロジェクトのビルド時に使用する構成です。 既定値は `Debug` です。

`--version-suffix <VERSION_SUFFIX>`

プロジェクト ファイルのバージョン フィールドでアスタリスク (`*`) を置き換えるバージョン サフィックスを定義します。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>例

現在のディレクトリのプロジェクトを発行します。

`dotnet publish`

指定されたプロジェクト ファイルを使用して、アプリケーションを発行します。

`dotnet publish ~/projects/app1/app1.csproj`
    
`netcoreapp1.1` フレームワークを使って現在のディレクトリ内のプロジェクトを発行します。

`dotnet publish --framework netcoreapp1.1`
    
`netcoreapp1.1` フレームワークと `OS X 10.10` のランタイム (この RID はプロジェクト ファイルに列挙しておく必要があります) を使って、現在のアプリケーションを発行します。

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a>関連項目

* [ターゲット フレームワーク](../../standard/frameworks.md)
* [ランタイム識別子 (RID) のカタログ](../rid-catalog.md)

