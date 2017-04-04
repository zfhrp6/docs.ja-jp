---
title: "dotnet-sln コマンド - .NET Core CLI | Microsoft Docs"
description: "dotnet-sln コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利なオプションを提供します。"
keywords: "dotnet-sln, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 2cdfd02f7735b106fde910b8906ba4dfae860952
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>名前

`dotnet-sln` - .NET Core ソリューション ファイルを変更します。

## <a name="synopsis"></a>構文

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add **/**
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove **/**
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>説明

`dotnet sln` コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利な方法を提供します。

## <a name="commands"></a>コマンド

`add <PROJECT> ...`

`add **/*`

ソリューション ファイルに 1 つまたは複数のプロジェクトを追加します。 [Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。

`remove <PROJECT> ...`

`remove **/*`

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

ソリューションにプロジェクトを追加する:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

現在のディレクトリのソリューションにプロジェクトを追加する:

`dotnet sln add todo-app.csproj`

ソリューションからプロジェクトを削除する:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

glob パターンを使用して、ソリューションに複数のプロジェクトを追加する:

`dotnet sln add **/**/*.fsproj`

