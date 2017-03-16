---
title: "dotnet-pack コマンド | Microsoft Docs"
description: "dotnet-pack コマンドでは、.NET Core プロジェクトの NuGet パッケージを作成します。"
keywords: "dotnet-pack, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 88289a09a22bf20ec9089ec6a74269cd682a305b
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-pack"></a>dotnet-pack

## <a name="name"></a>名前

`dotnet-pack` - NuGet パッケージにコードをパックします。

## <a name="synopsis"></a>構文

```
dotnet pack [project] [-o|--output] [--no-build] [--include-symbols] [--include-source] [-c|--configuration] [--version-suffix] [-s|--serviceable] [-v|--verbosity]
dotnet pack [-h|--help]
```

## <a name="description"></a>説明

`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。 このコマンドの結果が NuGet パッケージです。 `--include-symbols` オプションが存在する場合、デバッグ シンボルを含む別のパッケージが作成されます。 

パックされるプロジェクトの NuGet 依存関係が `nuspec` ファイルに追加されるため、パッケージのインストール時に解決できます。 プロジェクト間参照はプロジェクト内にはパッケージ化されません。 現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。

`dotnet pack`では、既定で最初にプロジェクトがビルドされます。 これを避けたい場合は、`--no-build` オプションを渡します。 これは、コードが既にビルドされていることがわかっている場合などの継続的インテグレーション (CI) ビルド シナリオで役立ちます。 

## <a name="arguments"></a>引数

`project` 
    
パックするプロジェクトです。 [csproj ファイル](csproj.md)またはディレクトリのいずれかへのパスを指定できます。 省略すると、既定で現在のディレクトリに設定されます。 

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-o|--output <OUTPUT_DIRECTORY>`

指定したディレクトリにビルド済みパッケージを配置します。 

`--no-build`

パッキングの前にプロジェクトをビルドしません。 

`--include-symbols`

シンボルの nupkg を生成します。 

`--include-source`

NuGet パッケージにソース ファイルを含めます。 ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。 

`-c|--configuration <Debug|Release>`

プロジェクトのビルド時に使用する構成です。 指定しない場合、既定で `Debug` に設定されます。

`--version-suffix <VERSION_SUFFIX>`

プロジェクトの $(VersionSuffix) MSBuild プロパティの値を定義します。

`-s|--serviceable`

パッケージに処理可能フラグを設定します。 詳細については、https://aka.ms/nupkgservicing を参照してください。

`--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>例

現在のディレクトリのプロジェクトをパックします。

`dotnet pack`

app1 プロジェクトをパックします。

`dotnet pack ~/projects/app1/project.csproj`
    
プロジェクトを現在のディレクトリにパックし、指定したフォルダーに生成されたパッケージを配置します。

`dotnet pack --output nupkgs`

現在のディレクトリのプロジェクトを指定したフォルダーにパックし、ビルド ステップをスキップします。

`dotnet pack --no-build --output nupkgs`

現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。 プロジェクト バージョンのサフィックスは、*.csproj* ファイルの `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` として構成されます。

`dotnet pack --version-suffix "ci-1234"`
