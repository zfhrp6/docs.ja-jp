---
title: "dotnet-sln コマンド - .NET Core CLI"
description: "dotnet-sln コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利なオプションを提供します。"
keywords: "dotnet-sln, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 04/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 606929fbcafddf47abf5da6d3c8ce97d5af06909
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>名前

`dotnet-sln` - .NET Core ソリューション ファイルを変更します。

## <a name="synopsis"></a>構文

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>説明

`dotnet sln` コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利な方法を提供します。

## <a name="commands"></a>コマンド

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

ソリューション ファイルに 1 つまたは複数のプロジェクトを追加します。 [Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

ソリューション ファイルから 1 つまたは複数のプロジェクトを削除します。 [Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。

`list`

ソリューション ファイルのすべてのプロジェクトを一覧表示します。

## <a name="arguments"></a>引数

`SOLUTION_NAME`

使用するソリューション ファイル。 指定されていない場合、現在のディレクトリで検索されます。 ディレクトリに複数のソリューション ファイルがある場合、1 つを指定する必要があります。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

## <a name="examples"></a>例

ソリューションに 1 つの C# プロジェクトを追加する:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

ソリューションから 1 つの C# プロジェクトを削除する:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

ソリューションに複数の C# プロジェクトを追加する:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

ソリューションから複数の C# プロジェクトを削除する:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

glob パターンを使用して、C# ソリューションに複数のプロジェクトを追加する:

`dotnet sln todo.sln add **/*.csproj`

glob パターンを使用して、C# ソリューションから複数のプロジェクトを削除する:

`dotnet sln todo.sln remove **/*.csproj`

