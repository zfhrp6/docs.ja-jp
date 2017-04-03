---
title: "dotnet-restore コマンド - .NET Core CLI | Microsoft Docs"
description: "dotnet restore コマンドを使用して、依存関係とプロジェクト固有のツールを復元する方法について説明します。"
keywords: "dotnet-restore, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fd7a5769-afbe-4838-bbaf-3ae0cfcbb914
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 92da0806eb6c365a4622668242edc28d9966ed26
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-restore"></a>dotnet-restore

## <a name="name"></a>名前

`dotnet-restore` - プロジェクトの依存関係とツールを復元します。

## <a name="synopsis"></a>構文

`dotnet restore [<ROOT>] [-s|--source] [-r|--runtime] [--packages] [--disable-parallel] [--configfile] [--no-cache] [--ignore-failed-sources] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>説明

`dotnet restore` コマンドでは NuGet を使用して、依存関係と、プロジェクト ファイルに指定されているプロジェクト固有のツールを復元します。 既定では、依存関係とツールの復元は並列に実行されます。

依存関係を復元するには、NuGet で、パッケージを配置するフィードが必要になります。 フィードは、通常、*NuGet.config* 構成ファイルを通じて提供されます。 既定の構成ファイルは、CLI ツールがインストールされている場合に提供されます。 プロジェクト ディレクトリに独自の *NuGet.config* ファイルを作成して、さらにフィードを指定します。 コマンド プロンプトで呼び出すごとにフィードをさらに指定することもできます。 

依存関係については、`--packages` 引数を使用して、復元操作中に復元されたパッケージの配置場所を指定します。 指定されていない場合は、既定の NuGet パッケージ キャッシュが使用されます。これは、すべてのオペレーティング システムのユーザーのホーム ディレクトリ内の `.nuget/packages` ディレクトリにあります (たとえば、Linux の場合は */home/user1*、Windows の場合は *C:\Users\user1*)。

プロジェクト固有のツールについては、`dotnet restore` はまず、ツールがパックされているパッケージを復元し、プロジェクト ファイルに指定されているツールの依存関係の復元に進みます。

## <a name="arguments"></a>引数

`ROOT` 
    
復元するプロジェクト ファイルへのオプションのパスです。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-s|--source <SOURCE>`

復元操作時に使用する NuGet パッケージのソースを指定します。 これにより、*NuGet.config* ファイルに指定されているすべてのソースがオーバーライドされます。 このオプションを複数回指定することによって、複数のソースを指定できます。

`-r|--runtime <RUNTIME_IDENTIFIER>`

パッケージの復元用のランタイムを指定します。 これは、*.csproj* ファイルの `<RuntimeIdentifiers>` タグに明示的にリストされていないランタイムのパッケージを復元するために使用されます。 ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。 このオプションを複数回指定して、複数の RID を指定します。

`--packages <PACKAGES_DIRECTORY]`

復元されるパッケージのディレクトリを指定します。 

`--disable-parallel`

複数プロジェクトの並行復元を無効にします。 

`--configfile <FILE>`

復元操作で使用する NuGet 構成ファイル (*NuGet.config*) です。

`--no-cache`

パッケージとの HTTP 要求をキャッシュしないように指定します。

`--ignore-failed-sources`

バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。

`--no-dependencies`

プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。

`--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>例

現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore` 

指定されたパスで見つかった `app1` プロジェクトの依存関係とツールを復元します。

`dotnet restore ~/projects/app1/app1.csproj`
    
ソースとして指定されたファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore -s c:\packages\mypackages` 

ソースとして指定された 2 つのファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages` 

現在のディレクトリでプロジェクトの依存関係とツールを復元し、出力にエラーのみを表示します。

`dotnet restore --verbosity Error`

