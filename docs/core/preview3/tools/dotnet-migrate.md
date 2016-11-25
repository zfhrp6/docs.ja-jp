---
title: "dotnet-migrate コマンド | .NET Core SDK"
description: "dotnet-migrate コマンドは、プロジェクトとそのすべての依存関係を移行します。"
keywords: "dotnet-migrate, CLI, CLI コマンド, .NET Core"
author: mairaw
manager: wpickett
ms.date: 11/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 70285a83-4103-4617-be8b-d0e1e9a4a91d
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 150d70e3f0a80f7f6e733abee3691a0fe420919f

---

#<a name="dotnet-migrate"></a>dotnet-migrate

## <a name="name"></a>名前 
dotnet-migrate -- Preview 2 .NET Core プロジェクトを Preview 3 .NET Core プロジェクトに移行します。

## <a name="synopsis"></a>構文

`dotnet migrate [--help] [--template-file]  
    [--sdk-package-version] [--xproj-file]  
    [--skip-project-references]  [--report-file] [--format-report-file-json]
    [--skip-backup]
    [<arguments>]`

## <a name="description"></a>説明
`dotnet migrate` コマンドは、有効な Preview 2 `project.json` ベースのプロジェクトを有効な Preview 3 `csproj` プロジェクトに移行します。 既定では、このコマンドは、ルート プロジェクトとルート プロジェクトに含まれるすべてのプロジェクト参照を移行します。 この動作は、実行時に `--skip-project-references` オプションを使用して、無効にすることができます。 

移行は次のいずれかで実行できます。

* 1 つのプロジェクト。移行する `project.json` ファイルを指定する
* `global.json` ファイルに指定されたすべてのディレクトリ。`global.json` ファイルへのパスを渡す
* 再帰的に特定のディレクトリのすべてのサブディレクトリ 

移行コマンドは、`backup` ディレクトリ内に移行された `project.json` ファイルを保持します。ディレクトリが存在しない場合は作成されます。 これは、`--skip-backup` オプションを使用すると、オーバーライドされます。 

既定では、移行操作は、標準出力 (STDOUT) に移行プロセスの状態を出力します。 `--report-file` オプションを使用する場合、出力は指定したファイルにも保存されます。 

Preview 3 の時点で、`dotnet migrate` コマンドは、有効な Preview 2 `project.json` ファイルのみをサポートしています。 つまり、このコマンドを使用して、古い DNX や Preview 1 `project.json` ファイルを直接 csproj に移行することはできません。最初に Preview 2 project.json ファイルに移行して、csproj ファイルに移行する必要があります。 今後、Preview 1 プロジェクトのサポートも追加する予定です。 

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-t|--template-file <TEMPLATE_FILE>`

移行に使用するテンプレートの csproj ファイル。 既定では、使用される `dotnet new` によってドロップされるテンプレートと同じテンプレートです。 

`-v|--sdk-package-version <VERSION>`

移行されたアプリで参照される sdk パッケージのバージョン。 既定は、dotnet new 内の sdk のバージョンです。

`-x|--xproj-file <FILE>`

使用する xproj ファイルへのパス。 プロジェクト ディレクトリに複数の xproj がある場合に必要です。

`-s|--skip-project-references [Debug|Release]`

プロジェクト参照の移行をスキップします。 既定では、プロジェクト参照は再帰的に移行されます。

`-r|--report-file <REPORT_FILE>`

移行レポートをコンソールだけでなく、ファイルに出力します。

`--format-report-file-json <REPORT_FILE>`

ユーザー メッセージではなく、json として移行レポート ファイルを出力します。

`--skip-backup`

移行が成功した後に、project.json、global.json、および \*.xproj の `backup` ディレクトリへの移動をスキップします。

## <a name="examples"></a>例

現在のディレクトリのプロジェクトとそのプロジェクト間の依存関係をすべて移行します。

`dotnet migrate`

`global.json` ファイルがポイントするすべてのプロジェクトを移行します。

`dotnet migrate path/to/global.json`

現在のプロジェクトのみを移行し、プロジェクト間の依存関係は移行しません。特定の SDK バージョンを使用します。

`dotnet migrate -s -v 1.0.0-preview3`




<!--HONumber=Nov16_HO3-->


