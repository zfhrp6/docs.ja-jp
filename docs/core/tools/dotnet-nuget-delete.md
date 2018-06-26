---
title: dotnet nuget delete コマンド - .NET Core CLI
description: dotnet-nuget-delete コマンドは、サーバーからパッケージを削除または一覧から削除します。
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 1b58136d0bc04947f0a5baba320e5e6b3e45e2f1
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728415"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet nuget delete` - サーバーからパッケージを削除または一覧から削除します。

## <a name="synopsis"></a>構文

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a>説明

`dotnet nuget delete` コマンドは、サーバーからパッケージを削除または一覧から削除します。 [nuget.org](https://www.nuget.org/) の場合、この操作ではパッケージを一覧から削除します。

## <a name="arguments"></a>引数

`PACKAGE_NAME`

削除するパッケージの名前または ID です。

`PACKAGE_VERSION`

削除するパッケージのバージョンです。

## <a name="options"></a>オプション

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--force-english-output`

 インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`--no-service-endpoint` ソース URL に "api/v2/package" を追加しません。

`--non-interactive`

ユーザーに入力や確認のメッセージ画面を表示しません。

`-s|--source <SOURCE>`

サーバー URL を指定します。 nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。 プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--force-english-output`

 インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`--non-interactive`

ユーザーに入力や確認のメッセージ画面を表示しません。

`-s|--source <SOURCE>`

サーバー URL を指定します。 nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。 プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--force-english-output`

 インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`--non-interactive`

ユーザーに入力や確認のメッセージ画面を表示しません。

`-s|--source <SOURCE>`

サーバー URL を指定します。 nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。 プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。

---

## <a name="examples"></a>使用例

`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

ユーザーに資格情報やその他の入力を求めずに、`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
