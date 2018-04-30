---
title: dotnet list reference コマンド - .NET Core CLI
description: dotnet list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 946d3d523443fbe673b95dba95dbca327fde1699
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet list reference` - プロジェクト間参照を列挙します。

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

## <a name="examples"></a>使用例

指定したプロジェクトのプロジェクト参照を列挙する:

`dotnet list app/app.csproj reference`

現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:

`dotnet list reference`
