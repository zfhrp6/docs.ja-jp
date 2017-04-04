---
title: "dotnet-remove パッケージ コマンド - .NET Core CLI | Microsoft Docs"
description: "dotnet-remove パッケージ コマンドは、NuGet パッケージ参照をプロジェクトから削除する便利なオプションを提供します。"
keywords: "dotnet-remove, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2fcc8d37-16b3-4581-8038-832160e72d36
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: a321610540534a63bd12a8f878950b75e882c3d4
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-remove-package"></a>dotnet-remove パッケージ

## <a name="name"></a>名前

`dotnet-remove package` - プロジェクト ファイルからパッケージ参照を削除します。

## <a name="synopsis"></a>構文

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>説明

`dotnet remove package` コマンドは、NuGet パッケージ参照をプロジェクトから削除する便利なオプションを提供します。

## <a name="arguments"></a>引数

`PROJECT`

プロジェクト ファイルを指定します。 指定されていない場合、現在のディレクトリで検索されます。

`PACKAGE_NAME`

削除するパッケージ参照。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

## <a name="examples"></a>例

現在のディレクトリにあるプロジェクトから `Newtonsoft.Json` NuGet パッケージを削除する:

`dotnet remove package Newtonsoft.Json`
