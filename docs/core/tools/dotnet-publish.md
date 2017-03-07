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
ms.assetid: 8a7e1c52-5c57-4bf5-abad-727450ebeefd
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 1cf1611ab83874ad44855521d21040d102206338

---

#<a name="dotnet-publish"></a>dotnet-publish

> [!WARNING]
> このトピックは .NET Core Tools Preview 2 を対象としています。 .NET Core Tools RC4 バージョンについては、「[dotnet-publish (.NET Core Tools RC4)](../preview3/tools/dotnet-publish.md)」トピックを参照してください。

## <a name="name"></a>名前

`dotnet-publish` - アプリケーションとそのすべての依存関係をフォルダーにパックし、発行できるようにします。

## <a name="synopsis"></a>構文

`dotnet publish [project] 
    [--help] [--framework]  
    [--runtime] [--build-base-path] [--output]  
    [--version-suffix] [--configuration] [--native-subdirectory] [--no-build]`

## <a name="description"></a>説明

`dotnet publish` はアプリケーションをコンパイルし、[project.json](project-json.md) ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。 

ポータブル アプリの種類に応じて、結果のディレクトリには以下のものが含まれます。

1. *ポータブル アプリケーション* - アプリケーションの中間言語 (IL) コードとアプリケーションの管理対象となるすべての依存関係です。
    * *ネイティブの依存関係を持つポータブル アプリケーション* - 上記と同じ。ネイティブの各依存関係のサポートされるプラットフォームのサブディレクトリがあります。 
2. *自己完結型アプリケーション* - 上記と同じですが、対象となるプラットフォームのランタイム全体が含まれます。

詳細については、「[.NET Core Application Deployment](../deploying/index.md)」 (.NET Core アプリケーションの配置) を参照してください。

## <a name="options"></a>オプション

`[project]` 

発行するプロジェクトです。`[project]` が指定されていない場合は、既定で現在のディレクトリに設定されます。 この値として、[project.json](project-json.md) ファイルへのパス、または [project.json](project-json.md) ファイルを含むプロジェクト ディレクトリへのパスを指定できます。 [project.json](project-json.md) ファイルが見つからない場合、`dotnet publish` はエラーをスローします。 

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-f|--framework <FRAMEWORK>`

指定されたフレームワーク識別子 (FID) のアプリケーションを発行します。 指定しない場合、FID は [project.json](project-json.md#frameworks) から読み取られます。 有効なフレームワークが見つからない場合、コマンドはエラーをスローします。 複数の有効なフレームワークが見つかった場合、コマンドはすべての有効なフレームワークに対して発行します。 

`-r|--runtime <RUNTIME_IDENTIFIER>`

指定されたランタイムのアプリケーションを発行します。 使用できるランタイム ID (RID) については、[RID カタログ](../rid-catalog.md)に関するページを参照してください。

`-b|--build-base-path <OUTPUT_DIRECTORY>`

一時出力を配置するディレクトリ。

`-o|--output <OUTPUT_PATH>`

ディレクトリを配置する場所のパスを指定します。 指定しない場合、既定で *_./bin/[configuration]/[framework]/_* (ポータブル アプリケーションの場合) または *_./bin/[configuration]/[framework]/[runtime]_* (自己完結型の配置の場合) に設定されます。

`--version-suffix [VERSION_SUFFIX]`

project.json ファイルのバージョン フィールドで `*` を置き換える必要がある値を定義します。

`-c|--configuration [Debug|Release]`

発行時に使用する構成です。 既定値は `Debug` です。

`[--native-subdirectory]`: 出力に依存関係パッケージのネイティブ資産からのサブディレクトリを含めるための一時的なメカニズムです。 

`[--no-build]`: 発行前にプロジェクトをビルドしません。

## <a name="examples"></a>例

`project.json` で見つかったフレームワークを使用して、アプリケーションを発行します。 `project.json` に [runtimes](project-json.md#runtimes) ノードが含まれている場合は、現在のプラットフォームの RID を発行します。

`dotnet publish`

指定された [project.json](project-json.md) を使用して、アプリケーションを発行します。

`dotnet publish ~/projects/app1/project.json`
    
`netcoreapp1.0` フレームワークを使用して、現在のアプリケーションを発行します。

`dotnet publish --framework netcoreapp1.0`
    
`netcoreapp1.0` フレームワークと `OS X 10.10` のランタイム (この RID は `project.json` [runtimes](project-json.md#runtimes) ノードに存在している必要があります) を使用して、現在のアプリケーションを発行します。

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

## <a name="see-also"></a>関連項目
* [フレームワーク](../../standard/frameworks.md)
* [ランタイム識別子 (RID) のカタログ](../rid-catalog.md)


<!--HONumber=Feb17_HO2-->


