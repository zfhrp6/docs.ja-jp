---
title: "dotnet-remove 参照コマンド | Microsoft Docs"
description: "dotnet-remove 参照コマンドは、プロジェクト間参照を削除する便利なオプションを提供します。"
keywords: "dotnet-remove, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 889c6b7e-a313-40b1-9fd3-6a6f4c52f1d0
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 1f1a364b703c6b83a9b21ee420d62411bf9cd3ec
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-remove-reference"></a>dotnet-remove 参照

## <a name="name"></a>名前

`dotnet-remove reference` - プロジェクト間参照を参照します。

## <a name="synopsis"></a>構文

```
dotnet remove [project] reference [-f|--framework] <project_references>
dotnet remove reference [-h|--help]
```

## <a name="description"></a>説明

`dotnet remove reference` コマンドは、プロジェクトからプロジェクト参照を削除する便利なオプションを提供します。

## <a name="arguments"></a>引数

`project`

操作するプロジェクト ファイル。 指定されていない場合、現在のディレクトリで検索されます。

`project_references`

削除するプロジェクト間参照。 1 つまたは複数のプロジェクトを指定できます。 グロビング パターンは Unix/Linux ベースの端末で利用できます。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-f|--framework <FRAMEWORK>`

特定のフレームワークを対象にしている場合にのみ、参照を削除します。

## <a name="examples"></a>例

指定したプロジェクトからプロジェクト参照を削除する:

`dotnet remove app/app.csproj reference lib/lib.csproj`

現在のディレクトリ内のプロジェクトから複数のプロジェクト参照を削除する:

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

グロビング パターンを使用して複数のプロジェクト参照を削除する:

`dotnet remove app/app.csproj reference **/*.csproj`
