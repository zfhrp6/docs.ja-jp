---
title: "dotnet-clean コマンド | Microsoft Docs"
description: "dotnet-clean コマンドは現在のディレクトリを消去します。"
keywords: "dotnet-clean, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 3c00f4616932318b5dc5d77cbdf6c645696a4226
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-clean"></a>dotnet-clean

## <a name="name"></a>名前

`dotnet-clean` - プロジェクトの出力を消去します。 

## <a name="synopsis"></a>構文

```
dotnet clean [project] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity]
dotnet clean [--help] 
```

## <a name="description"></a>説明

`dotnet clean` コマンドは、以前のビルドの出力を消去します。 MSBuild ターゲットとして実装されます。そのため、プロジェクトが評価されます。 ビルド中に作成された出力のみが消去されます。 中間 (`obj`) と最終出力 (`bin`) フォルダーの両方が消去されます。 

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-o|--output <OUTPUT_DIRECTORY>`

ビルド済みバイナリが配置されたディレクトリ。 このオプションを指定する場合は、`--framework` を定義する必要もあります。 ビルド中にこのプロパティを指定しなかった場合、消去のためにそれを指定する必要はありません。

`-f|--framework <FRAMEWORK>`

ビルド時に指定されたフレームワーク。 ビルド中にこのプロパティを指定しなかった場合、消去のためにそれを指定する必要はありません。 フレームワークは、[project file](csproj.md) に定義する必要があります。

`-c|--configuration [Debug|Release]`

ビルドが実行された構成を定義します。  省略した場合は、既定で `Debug` に設定されます。 ビルド中にこのプロパティを指定しなかった場合、消去のためにそれを指定する必要はありません。

`-v|--verbosity <Quiet|Minimal|Normal|Diag>`

`dotnet clean` コマンドの呼び出しに使用される詳細度を定義します。 詳細レベルは、標準の [MSBuild 冗長レベル](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)です。 

## <a name="examples"></a>例

プロジェクトの既定のビルドを消去します。

`dotnet clean`

リリース構成を使用してビルドされたプロジェクトを消去します。

`dotnet clean --configuration Release`

