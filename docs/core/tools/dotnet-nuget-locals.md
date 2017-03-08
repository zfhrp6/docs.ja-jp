---
title: "dotnet-nuget-locals コマンド | Microsoft Docs"
description: "dotnet-nuget-locals コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。"
keywords: "dotnet-nuget-locals, CLI, CLI コマンド, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 3d8ca57c3c9c25a59b98552784b057182c9100a3
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-nuget-locals"></a>dotnet-nuget-locals

## <a name="name"></a>名前

`dotnet-nuget-locals` - HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。 

## <a name="synopsis"></a>構文

```
dotnet nuget locals <cache_location> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

`<cache_location>` が次のいずれかの値の場合: `all`、`http-cache`、`packages-cache`、`global-packages`、または `temp`。

## <a name="description"></a>説明

`dotnet nuget locals` コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。

## <a name="arguments"></a>引数

`all`

指定された操作をすべてのキャッシュの種類 (HTTP 要求キャッシュ、グローバル パッケージ キャッシュ、一時的なキャッシュ) に適用することを指定します。

`http-cache`

指定した操作を HTTP 要求キャッシュのみに適用することを指定します。 その他のキャッシュの場所には影響しません。

`global-packages`

指定した操作をグローバル パッケージ キャッシュのみに適用することを指定します。 その他のキャッシュの場所には影響しません。

`temp`

指定した操作を一時的なキャッシュのみに適用することを指定します。 その他のキャッシュの場所には影響しません。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-c|--clear`

クリア オプションは、指定されたキャッシュの種類でクリア操作を実行するために使用されます。 キャッシュ ディレクトリの内容は、再帰的に削除されます。 実行中のユーザー/グループには、操作を成功させるために、キャッシュ ディレクトリ内のファイルへのアクセス許可がある必要があります。 アクセス許可がない場合は、ファイル/フォルダーがクリアされなかったことを示すエラーが表示されます。

`-l|--list`

一覧表示オプションは、指定されたキャッシュの種類の場所を表示するために使用されます。 

`--force-english-output`

コマンドライン出力を強制的に英語にします。

## <a name="examples"></a>例

すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) のパスを表示します。

`dotnet nuget locals –l all`

ローカルの HTTP キャッシュ ディレクトリのパスを表示します。

`dotnet nuget locals --list http-cache`

すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) のファイルをクリアします。

`dotnet nuget locals --clear all`

ローカルのグローバル キャッシュ ディレクトリのファイルをすべてクリアします。

`dotnet nuget locals -c global-packages`

ローカルの一時的なキャッシュ ディレクトリのファイルをすべてクリアします。

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>トラブルシューティング

`dotnet-nuget-locals` コマンドを使用しているときに発生する一般的な問題やエラーについては、「[Managing the NuGet cache](https://docs.microsoft.com/nuget/consume-packages/managing-the-nuget-cache)」 (NuGet キャッシュを管理する) をご覧ください。

