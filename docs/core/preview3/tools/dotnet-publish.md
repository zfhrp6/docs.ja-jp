---
title: "dotnet-publish コマンド | .NET Core SDK"
description: "dotnet-publish コマンドは、.NET Core プロジェクトをディレクトリに発行します。"
keywords: "dotnet-publish, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8a7e1c52-5c57-4bf5-abad-727450ebeefd
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: e480c32faa22859de74e06f3a199fba1c0720c46

---

#<a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>Name

`dotnet-publish` - アプリケーションとそのすべての依存関係をフォルダーにパックし、発行できるようにします。

## <a name="synopsis"></a>構文

`dotnet publish [project] 
    [--help] [--framework]  
    [--runtime] [--output]  
    [--version-suffix] [--configuration]`

## <a name="description"></a>説明

`dotnet publish` はアプリケーションをコンパイルし、プロジェクト ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。 

ポータブル アプリの種類に応じて、結果のディレクトリには以下のものが含まれます。

1. *フレームワークに依存する展開* - アプリケーションの中間言語 (IL) コードとアプリケーションの管理対象となるすべての依存関係です。
2. *自己完結型の展開* - 上記と同じですが、対象となるプラットフォームのランタイム全体が含まれます。

詳細については、「[.NET Core Application Deployment](../deploying/index.md)」 (.NET Core アプリケーションの配置) を参照してください。

## <a name="options"></a>オプション

`[project]` 

発行するプロジェクトです。`[project]` が指定されていない場合は、既定で現在のディレクトリに設定されます。 

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-f|--framework <FRAMEWORK>`

指定されたフレームワーク識別子 (FID) のアプリケーションを発行します。 

`-r|--runtime <RUNTIME_IDENTIFIER>`

指定されたランタイムのアプリケーションを発行します。 使用できるランタイム ID (RID) については、[RID カタログ](../../rid-catalog.md)に関するページを参照してください。

`-o|--output <OUTPUT_PATH>`

ディレクトリを配置する場所のパスを指定します。 指定しない場合、既定で *_./bin/[configuration]/[framework]/_* (ポータブル アプリケーションの場合) または *_./bin/[configuration]/[framework]/[runtime]_* (自己完結型の配置の場合) に設定されます。

`--version-suffix [VERSION_SUFFIX]`

プロジェクト ファイルのバージョン フィールドで `*` を置き換える必要がある値を定義します。

`-c|--configuration [Debug|Release]`

発行時に使用する構成です。 既定値は `Debug` です。

## <a name="examples"></a>例

アプリケーションを発行します。

`dotnet publish`

指定されたプロジェクト ファイルを使用して、アプリケーションを発行します。

`dotnet publish ~/projects/app1/app1.csproj`
    
`netcoreapp1.0` フレームワークを使用して、現在のアプリケーションを発行します。

`dotnet publish --framework netcoreapp1.0`
    
`netcoreapp1.0` フレームワークと `OS X 10.10` のランタイム (この RID はプロジェクト ファイルに存在している必要があります) を使用して、現在のアプリケーションを発行します。

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

## <a name="see-also"></a>関連項目
* [フレームワーク](../../../standard/frameworks.md)
* [ランタイム識別子 (RID) のカタログ](../../rid-catalog.md)



<!--HONumber=Nov16_HO3-->


