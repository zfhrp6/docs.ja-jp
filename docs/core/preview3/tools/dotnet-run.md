---
title: "dotnet-run コマンド | Microsoft Docs"
description: "dotnet-run コマンドは、ソース コードからアプリケーションを実行する便利なオプションを提供します。"
keywords: "dotnet-run, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 3f9d50dcc58ad4af836a6b19d8daf7bb6bf60341

---

#<a name="dotnet-run-net-core-tools-rc4"></a>dotnet-run (.NET Core Tools RC4)

> [!WARNING]
> このトピックは .NET Core Tools RC4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[dotnet-run](../../tools/dotnet-run.md)」トピックを参照してください。

## <a name="name"></a>名前 

dotnet-run -- 明示的なコンパイルや起動コマンドなしで、ソース コードを 'インプレース' で実行します。

## <a name="synopsis"></a>構文

`dotnet run [--help] [--framework] [--configuration]
    [--project] [[--] [application arguments]]`

## <a name="description"></a>説明
`dotnet run` コマンドは、1 つのコマンドを使用して、ソース コードからアプリケーションを実行する便利なオプションを提供します。 ソース コードをコンパイルし、出力プログラムを生成してから、そのプログラムを実行します。 このコマンドは高速の反復開発に役立ちます。ソース分散プログラム (Web サイトなど) を実行する場合にも使用できます。

このコマンドは、プログラムを起動する前に、.NET アセンブリにソース入力をビルドする [dotnet build](dotnet-build.md) に依存します。 このコマンドと、ソース入力の処理に関する要件はすべてビルド コマンドから継承されます。 これらの要件の詳細については、ビルド コマンドのドキュメントを参照してください。

出力ファイルは子の *bin* フォルダーに書き込まれます。フォルダーが存在しない場合は、作成されます。 必要に応じて、ファイルは上書きされます。 一時ファイルは子の *obj* フォルダーに書き込まれます。  

複数のフレームワークが指定されているプロジェクトの場合、`dotnet run` は最初に .NET Core フレームワークを選択します。 フレームワークが存在しない場合は、エラーが発生します。 他のフレームワークを指定するには、`--framework` 引数を使用します。

`dotnet run` コマンドは、ビルド済みのアセンブリではなく、プロジェクトのコンテキストで使用する必要があります。 代わりにポータブル アプリケーション DLL の実行を試みる場合は、以下の例のようにコマンドなしで [dotnet](dotnet.md) を使用する必要があります。
 
`dotnet myapp.dll`

`dotnet` ドライバーの詳細については、「[.NET Core Command Line Tools (CLI)](index.md)」 (.NET Core コマンド ライン ツール (CLI)) を参照してください。

## <a name="options"></a>オプション

`--`

実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。 この後の引数はすべて実行中のアプリケーションに渡されます。 

`-h|--help`

コマンドの短いヘルプを印刷します。

`-f`, `--framework <FRAMEWORK_IDENTIFIER>`

指定されたフレームワーク識別子 (FID) のアプリケーションを実行します。 

`-c`, `--configuration <Debug|Release>`

発行時に使用する構成です。 既定値は `Debug` です。

`-p`, `--project [PATH]`

実行するプロジェクトを指定します。 [csproj](csproj.md) ファイルへのパス、または [csproj](csproj.md) ファイルを含むディレクトリへのパスを指定できます。 指定しない場合は、既定で現在のディレクトリに設定されます。 

## <a name="examples"></a>例

現在のディレクトリのプロジェクトを実行します。`dotnet run` 

指定されたプロジェクトを実行します。

`dotnet run --project /projects/proj1/proj1.csproj`

現在のディレクトリのプロジェクトを実行します (この例では、`--` 引数が使用されているため、`--help` 引数が実行中のアプリケーションに渡されます)。

`dotnet run --configuration Release -- --help`


<!--HONumber=Feb17_HO2-->


