---
title: "dotnet-publish コマンド | Microsoft Docs"
description: "dotnet-publish コマンドは、.NET Core プロジェクトをディレクトリに発行します。"
keywords: "dotnet-publish, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 78487673d8fa07286605fb806f30083747b17386
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>名前

`dotnet-publish` - アプリケーションとそのすべての依存関係をフォルダーにパックし、発行できるようにします。

## <a name="synopsis"></a>構文

```
dotnet publish [project] [-f|--framework] [-r|--runtime] [-o|--output] [-c|--configuration] [--version-suffix] [-v|--verbosity]
dotnet publish [-h|--help]
```

## <a name="description"></a>説明

`dotnet publish` はアプリケーションをコンパイルし、プロジェクト ファイルに指定されたその依存関係を読み取り、結果のファイル セットをディレクトリに発行します。 出力の内容は次のとおりです。

1. アセンブリの中間言語 (IL) コード (拡張子 `*.dll`)。
2. *deps.json* ファイル。プロジェクトのすべての依存関係が含まれます。 
3. *Runtime.config.json* ファイル。アプリケーションが想定する共有ランタイムと、ランタイムの他の校正オプション (ガベージ コレクションの種類など) を指定します。
4. すべてのアプリケーションの依存関係。 これらは NuGet キャッシュから出力フォルダーにコピーされます。 

`dotnet publish` コマンドの出力は、実行のためにリモート コンピューターに展開できます。また、実行のためにアプリケーションを別のコンピューター (サーバーなど) に展開する方法として、公式に唯一サポートされている方法です。 プロジェクトに指定されている展開の種類によっては、リモート コンピューターに .NET Core 共有ランタイムをインストールしておく必要があります。 詳細については、「[.NET Core Application Deployment](../deploying/index.md)」 (.NET Core アプリケーションの配置) を参照してください。

## <a name="arguments"></a>引数

`project` 

発行するプロジェクトです。`project` が指定されていない場合は、既定で現在のディレクトリに設定されます。 

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-f|--framework <FRAMEWORK>`

指定したターゲット フレームワークのアプリケーションを発行します。 ターゲット フレームワークはプロジェクト ファイルに指定する必要があります。

`-r|--runtime <RUNTIME_IDENTIFIER>`

指定されたランタイムのアプリケーションを発行します。 これは、[自己完結型の展開](../deploying/index.md#self-contained-deployments-scd)を作成するときに使用されます。 使用できるランタイム ID (RID) については、[RID カタログ](../rid-catalog.md)に関するページを参照してください。 既定では、[フレームワークに依存するアプリ](../deploying/index.md#framework-dependent-deployments-fdd)が発行されます。

`-o|--output <OUTPUT_PATH>`

ディレクトリを配置する場所のパスを指定します。 指定しない場合、既定で *_./bin/[configuration]/[framework]/_* (ポータブル アプリケーションの場合) または *_./bin/[configuration]/[framework]/[runtime]_* (自己完結型の配置の場合) に設定されます。

`-c|--configuration {Debug|Release}`

プロジェクトのビルド時に使用する構成です。 既定値は `Debug` です。

`--version-suffix <VERSION_SUFFIX>`

プロジェクト ファイルのバージョン フィールドで `*` を置き換える必要がある値を定義します。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>例

現在のディレクトリ内にあるプロジェクトを発行します。

`dotnet publish`

指定されたプロジェクト ファイルを使用して、アプリケーションを発行します。

`dotnet publish ~/projects/app1/app1.csproj`
    
`netcoreapp1.1` フレームワークを使用して現在のディレクトリ内のプロジェクトを発行します。

`dotnet publish --framework netcoreapp1.1`
    
`netcoreapp1.1` フレームワークと `OS X 10.10` のランタイム (この RID はプロジェクト ファイルに存在している必要があります) を使用して、現在のアプリケーションを発行します。

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a>関連項目
* [フレームワーク](../../standard/frameworks.md)
* [ランタイム識別子 (RID) のカタログ](../rid-catalog.md)
