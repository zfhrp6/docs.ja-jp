---
title: "dotnet-pack コマンド - .NET Core CLI"
description: "dotnet-pack コマンドでは、.NET Core プロジェクトの NuGet パッケージを作成します。"
keywords: "dotnet-pack, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8dbbb3f7-b817-4161-a6c8-a3489d05e051
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 04b967fdf6578098caae8c21604c5d6160eb6775
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-pack"></a>dotnet-pack

## <a name="name"></a>名前

`dotnet-pack` - NuGet パッケージにコードをパックします。

## <a name="synopsis"></a>構文

`dotnet pack [<PROJECT>] [-o|--output] [--no-build] [--include-symbols] [--include-source] [-c|--configuration] [--version-suffix <VERSION_SUFFIX>] [-s|--serviceable] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>説明

`dotnet pack` コマンドはプロジェクトをビルドし、NuGet パッケージを作成します。 このコマンドの結果が NuGet パッケージです。 `--include-symbols` オプションが存在する場合、デバッグ シンボルを含む別のパッケージが作成されます。 

パックされるプロジェクトの NuGet 依存関係が *.nuspec* ファイルに追加されるため、パッケージのインストール時に適切に解決されます。 プロジェクト間参照はプロジェクト内にはパッケージ化されません。 現時点では、プロジェクト間の依存関係がある場合は、プロジェクトごとにパッケージが必要になります。

既定では、`dotnet pack` は最初にプロジェクトをビルドします。 この動作を避けたい場合は、`--no-build` オプションを渡します。 これは、コードが既にビルドされていることがわかっている場合の継続的インテグレーション (CI) ビルド シナリオで役立つことがよくあります。

パッキング プロセスのために `dotnet pack` コマンドに MSBuild のプロパティを使用できます。 詳細については、「[NuGet メタデータ プロパティ](csproj.md#nuget-metadata-properties)」と「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。

## <a name="arguments"></a>引数

`PROJECT` 
    
パックするプロジェクトです。 [csproj ファイル](csproj.md)またはディレクトリのいずれかへのパスです。 省略すると、既定で現在のディレクトリに設定されます。 

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-o|--output <OUTPUT_DIRECTORY>`

指定したディレクトリにビルド済みパッケージを配置します。 

`--no-build`

パッキングの前にプロジェクトをビルドしません。 

`--include-symbols`

シンボルの `nupkg` を生成します。 

`--include-source`

NuGet パッケージにソース ファイルを含めます。 ソース ファイルは、`nupkg` 内の `src` フォルダーに含まれます。 

`-c|--configuration <CONFIGURATION>`

プロジェクトのビルド時に使用する構成です。 指定しないと、構成は既定で `Debug` になります。

`--version-suffix <VERSION_SUFFIX>`

プロジェクトの `$(VersionSuffix)` MSBuild プロパティの値を定義します。

`-s|--serviceable`

パッケージに処理可能フラグを設定します。 詳しくは、「[.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing)」(.NET ブログ: .NET 4.5.1 は .NET NuGet ライブラリに対する Microsoft セキュリティ更新プログラムをサポートする) をご覧ください。

`--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>例

現在のディレクトリのプロジェクトをパックします。

`dotnet pack`

`app1` プロジェクトをパックします。

`dotnet pack ~/projects/app1/project.csproj`
    
プロジェクトを現在のディレクトリにパックし、`nupkgs` フォルダーに生成されたパッケージを配置します。

`dotnet pack --output nupkgs`

現在のディレクトリのプロジェクトを `nupkgs` フォルダーにパックし、ビルド ステップをスキップします。

`dotnet pack --no-build --output nupkgs`

*.csproj* ファイルで `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` として構成されているプロジェクトのバージョン サフィックスで、現在のプロジェクトをパックし、結果のパッケージ バージョンを指定されたサフィックスで更新します。

`dotnet pack --version-suffix "ci-1234"`

`PackageVersion` MSBuild プロパティで `2.1.0` にパッケージ バージョンを設定します。

`dotnet pack /p:PackageVersion=2.1.0`

