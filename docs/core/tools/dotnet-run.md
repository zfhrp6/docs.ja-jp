---
title: "dotnet-run コマンド | Microsoft Docs"
description: "dotnet-run コマンドは、ソース コードからアプリケーションを実行する便利なオプションを提供します。"
keywords: "dotnet-run, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 60bb9160e43788539b0dc6bcf1372bb925e9ba22
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-run"></a>dotnet-run

## <a name="name"></a>名前 

`dotnet-run` -- 明示的なコンパイルや起動コマンドなしで、ソース コードを 'インプレース' で実行します。

## <a name="synopsis"></a>構文

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a>説明

`dotnet run` コマンドは、1 つのコマンドを使用して、ソース コードからアプリケーションを実行する便利なオプションを提供します。 コマンド ラインの短期間の反復開発に便利です。 このコマンドは [`dotnet build`](dotnet-build.md) コマンドに依存し、コードをビルドします。そのため、プロジェクトを最初に復元する必要があるなど、ビルドに要件があれば、それが `dotnet run` にも適用されます。 

出力ファイルは既定の場所である `bin/<configuration>/<target>` に書き出されます。 たとえば、`netcoreapp1.0` というアプリケーションがあり、`dotnet run` を実行する場合、`bin/Debug/netcoreapp1.0` に出力されます。 必要に応じて、ファイルは上書きされます。 一時ファイルは `obj` ディレクトリに置かれます。 

フレームワークを複数指定するプロジェクトの場合、`--framework` オプションを利用してアプリケーションを実行するフレームワークを指定しない限り、`dotnet run` にはエラーが表示されます。

`dotnet run` コマンドは、ビルド済みのアセンブリではなく、プロジェクトのコンテキストで使用する必要があります。 代わりにポータブル アプリケーション DLL の実行を試みる場合は、以下の例のようにコマンドなしで [dotnet](dotnet.md) を使用する必要があります。
 
`dotnet myapp.dll`

`dotnet` ドライバーの詳細については、「[.NET Core Command Line Tools (CLI)](index.md)」 (.NET Core コマンド ライン ツール (CLI)) を参照してください。

アプリケーションを実行するために、`dotnet run` コマンドは、NuGet キャッシュから共有ランタイムの外にあるアプリケーションの依存関係を解決します。 そのため、このコマンドを利用してアプリケーションを本稼働実行することは推奨されません。 代わりに、[`dotnet publish`](dotnet-publish.md) コマンドを利用して[展開を作成](../deploying/index.md)し、それを本稼働で利用します。 

## <a name="options"></a>オプション

`--`

実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。 この後の引数はすべて実行中のアプリケーションに渡されます。 

`-h|--help`

コマンドの短いヘルプを印刷します。

`-c|--configuration {Debug|Release}`

プロジェクトのビルド時に使用する構成です。 既定値は `Debug` です。

`-f|--framework <FRAMEWORK_IDENTIFIER>`

指定されたフレームワークを利用してアプリをビルドし、実行します。 フレームワークはプロジェクト ファイルに指定する必要があります。

`-p|--project <PATH>`

実行するプロジェクト ファイルのパスを指定します。 [csproj](csproj.md) ファイルへのパス、または [csproj](csproj.md) ファイルを含むディレクトリへのパスを指定できます。 指定しない場合は、既定で現在のディレクトリに設定されます。 

## <a name="examples"></a>例

現在のディレクトリのプロジェクトを実行します。

`dotnet run` 

指定されたプロジェクトを実行します。

`dotnet run --project /projects/proj1/proj1.csproj`

現在のディレクトリのプロジェクトを実行します (この例では、`--` 引数が使用されているため、`--help` 引数が実行中のアプリケーションに渡されます)。

`dotnet run --configuration Release -- --help`
