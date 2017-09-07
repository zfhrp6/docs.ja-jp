---
title: "dotnet-nuget-locals コマンド - .NET Core CLI"
description: "dotnet-nuget-locals コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。"
keywords: "dotnet-nuget-locals, CLI, CLI コマンド, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2c9ea7b3b7c61b347cb7c56254773290f04a0cd6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-nuget-locals"></a>dotnet-nuget locals

## <a name="name"></a>名前

`dotnet-nuget locals` - ローカル NuGet リソースをクリアまたはリストします。 

## <a name="synopsis"></a>構文

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a>説明

`dotnet nuget locals` コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーのローカルの NuGet リソースをクリアまたは一覧表示します。

## <a name="arguments"></a>引数

`CACHE_LOCATION`

次のいずれかの値です。

`all`

指定された操作をすべてのキャッシュの種類 (HTTP 要求キャッシュ、グローバル パッケージ キャッシュ、一時的なキャッシュ) に適用することを指定します。

`http-cache`

指定した操作を HTTP 要求キャッシュのみに適用することを指定します。 その他のキャッシュの場所には影響しません。

`global-packages`

指定した操作をグローバル パッケージ キャッシュのみに適用することを指定します。 その他のキャッシュの場所には影響しません。

`temp`

指定した操作を一時キャッシュのみに適用することを指定します。 その他のキャッシュの場所には影響しません。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-c|--clear`

クリア オプションは、指定されたキャッシュの種類でクリア操作を実行します。 キャッシュ ディレクトリの内容は、再帰的に削除されます。 実行中のユーザー/グループには、キャッシュ ディレクトリ内のファイルへのアクセス許可が必要です。 アクセス許可がない場合は、ファイル/フォルダーがクリアされなかったことを示すエラーが表示されます。

`-l|--list`

一覧表示オプションは、指定されたキャッシュの種類の場所を表示するために使用されます。 

`--force-english-output`

コマンドライン出力を強制的に英語にします。

## <a name="examples"></a>例

すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) のパスを表示します。

`dotnet nuget locals –l all`

ローカルの HTTP キャッシュ ディレクトリのパスを表示します。

`dotnet nuget locals --list http-cache`

すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) からすべてのファイルをクリアします。

`dotnet nuget locals --clear all`

ローカルのグローバル キャッシュ ディレクトリのファイルをすべてクリアします。

`dotnet nuget locals -c global-packages`

ローカルの一時的なキャッシュ ディレクトリのファイルをすべてクリアします。

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>トラブルシューティング

`dotnet nuget locals` コマンドを使うときの一般的な問題やエラーについては、「[Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache)」 (NuGet キャッシュを管理する) をご覧ください。

