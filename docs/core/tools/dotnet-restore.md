---
title: "dotnet-restore コマンド | .NET Core SDK"
description: "dotnet restore コマンドを使用して、依存関係とプロジェクト固有のツールを復元する方法について説明します"
keywords: "dotnet-restore, CLI, CLI コマンド, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 60489b25-38de-47e6-bed1-59d9f42e2d46
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: 3c6c651aebfac0c27f340021d7779d37aa8bfe38

---

#<a name="dotnetrestore"></a>dotnet-restore

## <a name="name"></a>Name

`dotnet-restore`- プロジェクトの依存関係とツールを復元します。

## <a name="synopsis"></a>構文

`dotnet restore [root] [--help] [--force-english-output] [--source]  
    [--packages] [--disable-parallel] [--fallbacksource] [--configfile] 
    [--no-cache] [--infer-runtimes] [--verbosity] [--ignore-failed-sources]`

## <a name="description"></a>説明

`dotnet restore` コマンドでは NuGet を使用して、依存関係と、[project.json](project-json.md) ファイルに指定されているプロジェクト固有のツールを復元します。 既定では、依存関係とツールの復元は並列に実行されます。

依存関係を復元するには、NuGet で、パッケージを配置するフィードが必要になります。 フィードは、通常、NuGet.config 構成ファイルを通じて提供されます。CLI ツールがインストールされている場合は、既定のものがあります。 プロジェクト ディレクトリに独自の NuGet.config ファイルを作成することで、さらにフィードを指定できます。 フィードは、コマンド プロンプトでの呼び出しごとに指定することもできます。 

依存関係については、`--packages` 引数を使用して復元操作中に復元されたパッケージの配置場所を指定することができます。 指定しない場合は、既定の NuGet パッケージ キャッシュが使用されます。 すべてのオペレーティング システムのユーザーのホーム ディレクトリ内の `.nuget/packages` ディレクトリにあります (たとえば、Linux の場合は */home/user1*、Windows の場合は *C:\Users\user1*)。

プロジェクト固有のツールについては、`dotnet restore` はまず、ツールがパックされているパッケージを復元し、[project.json](project-json.md) に指定されているツールの依存関係の復元に進みます。 

## <a name="options"></a>オプション

`[root]` 
    
 復元するプロジェクトまたはプロジェクト フォルダーのリストです。 各値として、[project.json](project-json.md) または [global.json](global-json.md) ファイルへのパス、あるいはフォルダーへのパスを指定できます。 フォルダーが指定されている場合、復元操作ではすべてのサブディレクトリ内の [project.json](project-json.md) ファイルを再帰的に検索し、見つかった各 [project.json](project-json.md) ファイルに対して復元します。

`-h|--help`

コマンドの短いヘルプを印刷します。

 `--force-english-output`

インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

`-s|--source <SOURCE>`

復元操作時に使用する NuGet パッケージのソースを指定します。 これにより、NuGet.config ファイルに指定されているすべてのソースがオーバーライドされます。 このオプションを複数回指定することによって、複数のソースを指定できます。

`--packages <PACKAGES_DIRECTORY]`

復元されたパッケージを配置するディレクトリを指定します。 

`--disable-parallel`

複数プロジェクトの並行復元を無効にします。 

`-f|--fallbacksource <FEED>`

他のすべてのソースが失敗した場合に復元操作でフォールバックとして使用するパッケージ ソースのリストを指定します。 すべての有効なフィード形式を使用できます。 このオプションを複数回指定することによって、複数のフォールバック ソースを指定できます。

`--configfile <FILE>`

復元操作で使用する NuGet 構成ファイル (NuGet.config) です。

`--no-cache`

パッケージとの HTTP 要求をキャッシュしないように指定します。

`--infer-runtimes`

NuGet でレガシ リポジトリのランタイム識別子 (RID) を推測できるようにするための一時オプションです。

`--verbosity [LEVEL]`

使用するログの詳細度です。 指定できる値は、`Debug`、`Verbose`、`Information`、`Minimal`、`Warning`、`Error` です。

` --ignore-failed-sources`

バージョン要件を満たしているパッケージがある場合は、失敗したソースに関する警告のみです。

## <a name="examples"></a>例

現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore` 

指定されたパスで見つかった `app1` プロジェクトの依存関係とツールを復元します。

`dotnet restore ~/projects/app1/project.json`
    
フォールバック ソースとして指定されたファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore -f c:\packages\mypackages` 

フォールバック ソースとして指定された 2 つのファイル パスを使用して、現在のディレクトリでプロジェクトの依存関係とツールを復元します。

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages` 

現在のディレクトリでプロジェクトの依存関係とツールを復元し、出力にエラーのみを表示します。

`dotnet restore --verbosity Error`


<!--HONumber=Nov16_HO1-->


