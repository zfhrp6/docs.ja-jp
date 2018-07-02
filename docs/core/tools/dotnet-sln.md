---
title: dotnet sln コマンド - .NET Core CLI
description: dotnet-sln コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利なオプションを提供します。
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 65ae402ef5519863886c8cf833598f5314b4bdad
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207794"
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet sln` - .NET Core ソリューション ファイルを変更します。

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

`dotnet sln` コマンドを使用するには、ソリューション ファイルが既に存在している必要があります。 作成する必要がある場合、下の例のように [dotnet new](dotnet-new.md) コマンドを使用します。

```
dotnet new sln
```

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

## <a name="examples"></a>使用例

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
