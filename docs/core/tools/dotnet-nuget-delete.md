---
title: "dotnet nuget delete コマンド - .NET Core CLI"
description: "dotnet-nuget-delete コマンドは、サーバーからパッケージを削除または一覧から削除します。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 65fe52f07ed823b4f7518c5b1f2da1f7a61b0371
ms.contentlocale: ja-jp
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名前

`dotnet nuget delete` - サーバーからパッケージを削除または一覧から削除します。

## <a name="synopsis"></a>構文

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a>説明

`dotnet nuget delete` コマンドは、サーバーからパッケージを削除または一覧から削除します。 [nuget.org](https://www.nuget.org/) の場合、この操作ではパッケージを一覧から削除します。

## <a name="arguments"></a>引数

`PACKAGE_NAME`

削除するパッケージです。

`PACKAGE_VERSION`

削除するパッケージのバージョンです。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-s|--source <SOURCE>`

サーバー URL を指定します。 nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。 プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。

`--non-interactive`

ユーザーに入力や確認のメッセージ画面を表示しません。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`--force-english-output`

コマンドライン出力を強制的に英語にします。

## <a name="examples"></a>例

`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

ユーザーに資格情報やその他の入力を求めずに、`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
