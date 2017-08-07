---
title: "dotnet-remove 参照コマンド - .NET Core CLI"
description: "dotnet-remove 参照コマンドは、プロジェクト間参照を削除する便利なオプションを提供します。"
keywords: "dotnet-remove, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 889c6b7e-a313-40b1-9fd3-6a6f4c52f1d0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e22f64370be4b56597a303d79d3aabe1ff22a78a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-remove-reference"></a>dotnet-remove 参照

## <a name="name"></a>名前

`dotnet-remove reference` - プロジェクト間参照を削除します。

## <a name="synopsis"></a>構文

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>説明

`dotnet remove reference` コマンドは、プロジェクトからプロジェクト参照を削除する便利なオプションを提供します。

## <a name="arguments"></a>引数

`PROJECT`

ターゲット プロジェクト ファイル。 指定されていない場合、現在のディレクトリで検索されます。

`PROJECT_REFERENCES`

削除するプロジェクト間 (P2P) 参照。 1 つまたは複数のプロジェクトを指定できます。 [glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-f|--framework <FRAMEWORK>`

特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、参照を削除します。

## <a name="examples"></a>例

指定したプロジェクトからプロジェクト参照を削除する:

`dotnet remove app/app.csproj reference lib/lib.csproj`

現在のディレクトリ内のプロジェクトから複数のプロジェクト参照を削除する:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

Unix/Linux で glob パターンを使用して複数のプロジェクト参照を削除する:

`dotnet remove app/app.csproj reference **/*.csproj`

