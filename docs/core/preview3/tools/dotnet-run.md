---
title: "dotnet-run コマンド | .NET Core SDK"
description: "dotnet-run コマンドは、ソース コードからアプリケーションを実行する便利なオプションを提供します。"
keywords: "dotnet-run, CLI, CLI コマンド, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 495ff50b-cb30-4d30-8f20-beb3d5e7c31f
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 6f95125640e7341426c3a019771a6b8595d10e73

---

#<a name="dotnet-run"></a>dotnet-run

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


<!--HONumber=Nov16_HO3-->


