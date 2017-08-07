---
title: "dotnet-clean コマンド - .NET Core CLI"
description: "dotnet-clean コマンドは現在のディレクトリを消去します。"
keywords: "dotnet-clean, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 10222781d5bff596d1b7883bc73097758e878235
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-clean"></a>dotnet-clean

## <a name="name"></a>名前

`dotnet-clean` - プロジェクトの出力を消去します。 

## <a name="synopsis"></a>構文

`dotnet clean [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>説明

`dotnet clean` コマンドは、以前のビルドの出力を消去します。 [MSBuild ターゲット](/visualstudio/msbuild/msbuild-targets)として実装されます。そのため、コマンドの実行時にプロジェクトが評価されます。 ビルド中に作成された出力のみが消去されます。 中間 (*obj*) と最終出力 (*bin*) フォルダーの両方が消去されます。

## <a name="arguments"></a>引数

`PROJECT`

消去する MSBuild プロジェクトです。 プロジェクト ファイルを指定しない場合、MSBuild は、現在の作業ディレクトリから *proj* で終わるファイル名拡張子を検索し、そのファイルを使います。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-o|--output <OUTPUT_DIRECTORY>`

ビルド出力が配置されたディレクトリです。 プロジェクトのビルド時にフレームワークを指定した場合、出力ディレクトリ スイッチと共に `-f|--framework <FRAMEWORK>` スイッチを指定します。

`-f|--framework <FRAMEWORK>`

ビルド時に指定された[フレームワーク](../../standard/frameworks.md)です。 フレームワークは、[プロジェクト ファイル](csproj.md)で定義する必要があります。 ビルド時にフレームワークを指定した場合は、消去時にフレームワークを指定する必要があります。

`-c|--configuration <CONFIGURATION>`

構成を定義します。 省略した場合は、既定で `Debug` に設定されます。 このプロパティは、ビルド時に指定した場合にのみ、消去時にも必要です。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できるレベルは、q[uiet]、m[inimal]、n[ormal]、d[etailed]、diag[nostic] です。

## <a name="examples"></a>例

プロジェクトの既定のビルドを消去します。

`dotnet clean`

リリース構成を使用してビルドされたプロジェクトを消去します。

`dotnet clean --configuration Release`

