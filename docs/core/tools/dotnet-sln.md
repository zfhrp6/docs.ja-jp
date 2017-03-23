---
title: "dotnet-sln コマンド | Microsoft Docs"
description: "dotnet-sln コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利なオプションを提供します。"
keywords: "dotnet-sln, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 84c2a9cab36dcfa76f90d75c83f4988ba441b0a8
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>名前

`dotnet-sln` - .NET Core ソリューション ファイルを変更します。

## <a name="synopsis"></a>構文

```
dotnet sln [<solution_name>] add <project> <project>
dotnet sln [<solution_name>] add **/**
dotnet sln [<solution_name>] remove <project> <project>
dotnet sln [<solution_name>] remove **/**
dotnet sln [<solution_name>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>説明

`dotnet sln` コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利な方法を提供します。

## <a name="commands"></a>コマンド

`add <project>`

`add **/*`

ソリューション ファイルに&1; つまたは複数のプロジェクトを追加します。 グロビング パターンは Unix/Linux ベースの端末で利用できます。

`remove <project>`

`remove **/*`

ソリューション ファイルから&1; つまたは複数のプロジェクトを削除します。 グロビング パターンは Unix/Linux ベースの端末で利用できます。

`list`

ソリューション ファイルのすべてのプロジェクトを一覧表示します。

## <a name="arguments"></a>引数

`solution_name`

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

グロビング パターンを利用し、ソリューションに複数のプロジェクトを追加する:

`dotnet sln add **/**/*.fsproj`

