---
title: "dotnet-list 参照コマンド - .NET Core CLI | Microsoft Docs"
description: "dotnet-list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。"
keywords: "dotnet-list, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8f954a0c-03f8-4fbc-a529-b313ab12c623
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: fdaf2a6f66801be68507ccabe7e0f2fea5433e65
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-list-reference"></a>dotnet-list 参照

## <a name="name"></a>名前

`dotnet-list reference` - プロジェクト間参照を列挙します。

## <a name="synopsis"></a>構文

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a>説明

`dotnet list reference` コマンドは、特定のプロジェクトのプロジェクト参照を列挙する便利なオプションを提供します。

## <a name="arguments"></a>引数

`PROJECT`

参照の一覧取得に使うプロジェクト ファイルを指定します。 指定されていない場合、プロジェクト ファイルの現在のディレクトリで検索されます。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

## <a name="examples"></a>例

指定したプロジェクトのプロジェクト参照を列挙する:

`dotnet list app/app.csproj reference`

現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:

`dotnet list reference`

