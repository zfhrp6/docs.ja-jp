---
title: dotnet remove reference コマンド - .NET Core CLI
description: dotnet remove reference コマンドは、プロジェクト間参照を削除する便利なオプションを提供します。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 0b7fb2788ccc04b54bf02f0387141d501612c16d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-reference"></a>dotnet remove reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet remove reference` - プロジェクト間参照を削除します。

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

## <a name="examples"></a>使用例

指定したプロジェクトからプロジェクト参照を削除する:

`dotnet remove app/app.csproj reference lib/lib.csproj`

現在のディレクトリ内のプロジェクトから複数のプロジェクト参照を削除する:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

Unix/Linux で glob パターンを使用して複数のプロジェクト参照を削除する:

`dotnet remove app/app.csproj reference **/*.csproj`
