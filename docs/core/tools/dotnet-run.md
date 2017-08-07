---
title: "dotnet-run コマンド - .NET Core CLI"
description: "dotnet-run コマンドは、ソース コードからアプリケーションを実行する便利なオプションを提供します。"
keywords: "dotnet-run, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f0a6fce4f83808076b7cbcabdaa948badde2cf80
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-run"></a>dotnet-run

## <a name="name"></a>名前 

`dotnet-run` -- 明示的なコンパイルや起動コマンドなしで、ソース コードを実行します。

## <a name="synopsis"></a>構文

`dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]] [-h|--help]`

## <a name="description"></a>説明

`dotnet run` コマンドは、1 つのコマンドを使用して、ソース コードからアプリケーションを実行する便利なオプションを提供します。 コマンド ラインからの短期間の反復開発に便利です。 このコマンドは [`dotnet build`](dotnet-build.md) コマンドに依存し、コードをビルドします。 そのため、プロジェクトを最初に復元する必要があるなど、ビルドに要件があれば、それが `dotnet run` にも適用されます。 

出力ファイルは既定の場所である `bin/<configuration>/<target>` に書き込まれます。 たとえば、`netcoreapp1.0` というアプリケーションがあり、`dotnet run` を実行する場合、`bin/Debug/netcoreapp1.0` に出力されます。 必要に応じて、ファイルは上書きされます。 一時ファイルは `obj` ディレクトリに置かれます。 

フレームワークを複数指定するプロジェクトの場合、`-f|--framework <FRAMEWORK>` オプションを使用してフレームワークを指定しない限り、`dotnet run` を実行するとエラーが発生します。

`dotnet run` コマンドは、ビルド済みのアセンブリではなく、プロジェクトのコンテキストで使用されます。 代わりにフレームワークに依存するアプリケーション DLL の実行を試みる場合は、コマンドなしで [dotnet](dotnet.md) を実行する必要があります。 たとえば、`myapp.dll` を実行する場合は、次のコードを使用します。
 
```
dotnet myapp.dll
```

`dotnet` ドライバーの詳細については、「[.NET Core Command Line Tools (CLI)](index.md)」 (.NET Core コマンド ライン ツール (CLI)) を参照してください。

アプリケーションを実行するために、`dotnet run` コマンドは、NuGet キャッシュから共有ランタイムの外にあるアプリケーションの依存関係を解決します。 このコマンドではキャッシュされた依存関係を使用するため、`dotnet run` を使用してアプリケーションを実稼働環境で実行することは推奨されません。 代わりに、[`dotnet publish`](dotnet-publish.md) コマンドを使用して[展開を作成](../deploying/index.md)し、発行された出力を展開します。 

## <a name="options"></a>オプション

`--`

実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。 この後の引数はすべて実行中のアプリケーションに渡されます。 

`-h|--help`

コマンドの短いヘルプを印刷します。

`-c|--configuration <CONFIGURATION>`

プロジェクトのビルド時に使用する構成です。 既定値は `Debug` です。

`-f|--framework <FRAMEWORK>`

指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。 フレームワークはプロジェクト ファイルに指定する必要があります。

`-p|--project <PATH/PROJECT.csproj>`

プロジェクト ファイルのパスと名前を指定します  (注を参照)。指定しない場合は、既定で現在のディレクトリに設定されます。

> [!NOTE]
> `-p|--project` オプションでプロジェクト ファイルのパスと名前を使用します。 CLI の回帰により、この時点でフォルダー パスを指定できなくなります。 詳細およびこの問題の追跡については、「[dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992)」 (dotnet run -p でプロジェクトを開始できない (dotnet/cli #5992)) を参照してください。

## <a name="examples"></a>例

現在のディレクトリのプロジェクトを実行します。

`dotnet run` 

指定されたプロジェクトを実行します。

`dotnet run --project /projects/proj1/proj1.csproj`

現在のディレクトリのプロジェクトを実行します (この例では、`--` 引数が使用されているため、`--help` 引数がアプリケーションに渡されます)。

`dotnet run --configuration Release -- --help`

