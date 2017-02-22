---
title: "dotnet-publish コマンド | Microsoft Docs"
description: "dotnet-publish コマンドは、.NET Core プロジェクトをディレクトリに発行します。"
keywords: "dotnet-publish, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 0d222382640fc239760f8f51c69f1f306674d7ca

---

#<a name="dotnet-publish-net-core-tools-rc4"></a>dotnet-publish (.NET Core Tools RC4)

> [!WARNING]
> このトピックは .NET Core Tools RC4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[dotnet-publish](../../tools/dotnet-publish.md)」トピックを参照してください。

## <a name="name"></a>名前

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



<!--HONumber=Feb17_HO2-->


