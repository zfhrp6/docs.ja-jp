---
title: "dotnet-restore コマンド | Microsoft Docs"
description: "dotnet restore コマンドを使用して、依存関係とプロジェクト固有のツールを復元する方法について説明します。"
keywords: "dotnet-restore, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fd7a5769-afbe-4838-bbaf-3ae0cfcbb914
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: a55cd932045a59f08146dff367a87eb6fe61f6e5
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-restore"></a>dotnet-restore

## <a name="name"></a>名前

`dotnet-restore` - プロジェクトの依存関係とツールを復元します。

## <a name="synopsis"></a>構文

```
dotnet restore [root] [-s|--source] [-r|--runtime] [--packages] [--disable-parallel] [--configfile] [--no-cache] [--ignore-failed-sources] [--no-dependencies] [-v|--verbosity]
dotnet restore [-h|--help]
```

## <a name="description"></a>説明

`dotnet restore` コマンドでは NuGet を使用して、依存関係と、プロジェクト ファイルに指定されているプロジェクト固有のツールを復元します。 既定では、依存関係とツールの復元は並列に実行されます。

依存関係を復元するには、NuGet で、パッケージを配置するフィードが必要になります。 フィードは、通常、NuGet.config 構成ファイルを通じて提供されます。CLI ツールがインストールされている場合は、既定のものがあります。 プロジェクト ディレクトリに独自の NuGet.config ファイルを作成することで、さらにフィードを指定できます。 フィードは、コマンド プロンプトでの呼び出しごとに指定することもできます。 

依存関係については、`--packages` 引数を使用して復元操作中に復元されたパッケージの配置場所を指定することができます。 指定しない場合は、既定の NuGet パッケージ キャッシュが使用されます。 すべてのオペレーティング システムのユーザーのホーム ディレクトリ内の `.nuget/packages` ディレクトリにあります (たとえば、Linux の場合は */home/user1*、Windows の場合は *C:\Users\user1*)。

プロジェクト固有のツールについては、`dotnet restore` はまず、ツールがパックされているパッケージを復元し、プロジェクト ファイルに指定されているツールの依存関係の復元に進みます。

## <a name="options"></a>オプション

`root` 
    
復元するプロジェクト ファイルへのオプションのパスです。 

`-h|--help`

コマンドの短いヘルプを印刷します。

`-s|--source <SOURCE>`

復元操作時に使用する NuGet パッケージのソースを指定します。 これにより、NuGet.config ファイルに指定されているすべてのソースがオーバーライドされます。 このオプションを複数回指定することによって、複数のソースを指定できます。

`--packages <PACKAGES_DIRECTORY]`

復元されたパッケージを配置するディレクトリを指定します。 

`--disable-parallel`

複数プロジェクトの並行復元を無効にします。 

`--configfile <FILE>`

復元操作で使用する NuGet 構成ファイル (NuGet.config) です。

`--no-cache`

パッケージとの HTTP 要求をキャッシュしないように指定します。

` --ignore-failed-sources`

バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。

`--no-dependencies`

P2P 参照を含むプロジェクトを復元するときに、ルート プロジェクトだけの参照を復元しないでください。

`--verbosity <LEVEL>`

出力にこの量の詳細を表示します。 レベルには、`normal`、`quiet`、または `detailed` を指定できます。

## <a name="examples"></a>例

現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore` 

指定されたパスで見つかった `app1` プロジェクトの依存関係とツールを復元します。

`dotnet restore ~/projects/app1/app1.csproj`
    
フォールバック ソースとして指定されたファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore -f c:\packages\mypackages` 

フォールバック ソースとして指定された&2; つのファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages` 

現在のディレクトリでプロジェクトの依存関係とツールを復元し、出力にエラーのみを表示します。

`dotnet restore --verbosity Error`

