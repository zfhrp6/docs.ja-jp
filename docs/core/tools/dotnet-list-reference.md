---
title: "dotnet list reference コマンド - .NET Core CLI"
description: "dotnet list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.contentlocale: ja-jp
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-list-reference"></a>dotnet list reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名前

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

## <a name="examples"></a>例

指定したプロジェクトのプロジェクト参照を列挙する:

`dotnet list app/app.csproj reference`

現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:

`dotnet list reference`

