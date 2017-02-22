---
title: "dotnet-pack コマンド | Microsoft Docs"
description: "dotnet-pack コマンドでは、.NET Core プロジェクトの NuGet パッケージを作成します。"
keywords: "dotnet-pack, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 8e266f9b34923b0ab69140d78a20afeca00e0b7c

---

#<a name="dotnet-pack-net-core-tools-rc4"></a>dotnet-pack (.NET Core Tools RC4)

> [!WARNING]
> このトピックは .NET Core Tools RC4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[dotnet-pack](../../tools/dotnet-pack.md)」トピックを参照してください。

## <a name="name"></a>名前

`dotnet-pack` - NuGet パッケージにコードをパックします。

## <a name="synopsis"></a>構文

`dotnet pack [--help] [--output]  
    [--no-build] [--include-symbols]
    [--include-source] [--servicable]
    [--configuration]  [--version-suffix]
    [project]`  

## <a name="description"></a>説明

`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。 このコマンドの結果が NuGet パッケージです。 `--include-symbols` オプションが存在する場合、デバッグ シンボルを含む別のパッケージが作成されます。 

パックされるプロジェクトの NuGet 依存関係が `nuspec` ファイルに追加されるため、パッケージのインストール時に解決できます。 プロジェクト間参照はプロジェクト内にはパッケージ化されません。 現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。

`dotnet pack`では、既定で最初にプロジェクトがビルドされます。 これを避けたい場合は、`--no-build` オプションを渡します。 これは、コードが既にビルドされていることがわかっている場合などの継続的インテグレーション (CI) ビルド シナリオで役立ちます。 

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`[project]` 
    
パックするプロジェクトです。 [csproj ファイル](csproj.md)またはディレクトリのいずれかへのパスを指定できます。 省略すると、既定で現在のディレクトリに設定されます。 

`-o|--output <OUTPUT_DIRECTORY>`

指定したディレクトリにビルド済みパッケージを配置します。 

`--no-build`

パッキングの前にプロジェクトをビルドしません。 

`--include-source`

NuGet パッケージにソース ファイルを含めます。 ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。 

`--include-symbols`

シンボルの nupkg を作成します。 

`-c|--configuration <Debug|Release>`

プロジェクトのビルド時に使用する構成です。 指定しない場合、既定で `Debug` に設定されます。

`--version-suffix`

指定された文字列で `-*` パッケージ バージョン サフィックスのアスタリスクを更新します。

## <a name="examples"></a>例

現在のディレクトリのプロジェクトをパックします。

`dotnet pack`

app1 プロジェクトをパックします。

`dotnet pack ~/projects/app1/project.csproj`
    
プロジェクトを現在のディレクトリにパックし、指定したフォルダーに生成されたパッケージを配置します。

`dotnet pack --output nupkgs`

現在のディレクトリのプロジェクトを指定したフォルダーにパックし、ビルド ステップをスキップします。

`dotnet pack --no-build --output nupkgs`

現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。 たとえば、バージョン `1.0.0-*` は `1.0.0-ci-1234` に更新されます。

`dotnet pack --version-suffix "ci-1234"`


<!--HONumber=Feb17_HO2-->


