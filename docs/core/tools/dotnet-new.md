---
title: "dotnet-new コマンド - .NET Core CLI | Microsoft Docs"
description: "dotnet-new コマンドは、現在のディレクトリに新しい .NET Core プロジェクトを作成します。"
keywords: "dotnet-new, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 14e6b4a2ffe5145a6d5d856c2149569b9ae39ff9
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-new"></a>dotnet-new

## <a name="name"></a>名前

`dotnet-new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。

## <a name="synopsis"></a>構文

```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>説明

`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。 

このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。

## <a name="arguments"></a>引数

`TEMPLATE`

コマンドが呼び出されたときにインスタンス化するテンプレート。 各テンプレートには、渡すことができるオプションが存在する場合があります。 詳細については、[テンプレートのオプション](#template-options)を参照してください。

このコマンドには、テンプレートの既定の一覧が含まれています。 使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。 次の表は、SDK にプレインストールされているテンプレートの一覧です。 テンプレートの既定の言語は、角かっこで示されます。

|テンプレートの説明  | テンプレート名  | 言語 |
|----------------------|----------------|-----------|
| コンソール アプリケーション  | コンソール        | [C#]、F#  |
| クラス ライブラリ        | classlib       | [C#]、F#  |
| 単体テスト プロジェクト    | mstest         | [C#]、F#  |
| xUnit テスト プロジェクト   | xunit          | [C#]、F#  |
| ASP.NET Core 空   | Web            | [C#]      |
| ASP.NET Core Web アプリ | mvc            | [C#]、F#  |
| ASP.NET Core Web API | webapi         | [C#]      |
| Nuget 構成         | nugetconfig    |           |
| Web 構成           | webconfig      |           |
| ソリューション ファイル        | sln            |           |

## <a name="options"></a>オプション

`-h|--help`

コマンドのヘルプを印刷します。 `dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。

`-l|--list`

指定した名前を含むテンプレートを列挙します。 `dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。 たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。

`-lang|--language {C#|F#}`

作成するテンプレートの言語。 使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。 一部のテンプレートでは無効です。

`-n|--name <OUTPUT_NAME>`

作成される出力の名前です。 名前が指定されていない場合、現在のディレクトリの名前が使用されます。

`-o|--output <OUTPUT_DIRECTORY>`

生成された出力を配置する場所。 既定値は、現在のディレクトリです。

`-all|--show-all`

`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。 `dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。 これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。

## <a name="template-options"></a>テンプレート オプション

プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。 コア テンプレートの場合、次のオプションが与えられています。

**console、xunit、mstest、web、webapi**

`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0` または `netcoreapp1.1` (既定値: `netcoreapp1.0`)

**mvc**

`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0` または `netcoreapp1.1` (`Default: netcoreapp1.0`)

`-au|--authentication` - 使う認証の種類。 値: `None` または `Individual` (既定値: `None`)

`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。 値: `true` または `false` (既定値: `false`)

**classlib**

`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0`、`netcoreapp1.1`、`netstandard1.0` から `netstandard1.6` (既定値: `netstandard1.4`)

## <a name="examples"></a>例

現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。

`dotnet new console -lang f#` 
   
現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。.NET Core 1.0 を対象にする認証はありません。  

`dotnet new mvc -au None -f netcoreapp1.0`
 
.NET Core 1.1 を対象にする新しい xUnit アプリケーションを作成します。

`dotnet new xunit --Framework netcoreapp1.1`

MVC に利用できるすべてのテンプレートを一覧表示します。

`dotnet new mvc -l`

