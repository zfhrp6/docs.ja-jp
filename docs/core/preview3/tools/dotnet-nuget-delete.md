---
title: "dotnet-nuget-delete コマンド | .NET Core SDK"
description: "dotnet-nuget-delete コマンドは、サーバーからパッケージを削除または一覧から削除します。"
keywords: "dotnet-nuget-delete, CLI, CLI コマンド, .NET Core"
author: karann-msft
ms.author: mairaw
manager: wpickett
ms.date: 11/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: a338f91d33347d48eefe572ea61da5d58d5c639a

---

#<a name="dotnet-nuget-delete"></a>dotnet-nuget-delete

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>名前 
`dotnet-nuget-delete` - サーバーからパッケージを削除または一覧から削除します。 

## <a name="synopsis"></a>構文

`dotnet nuget delete [<package_name> <package_version>] 
    [--help] [--source] [--non-interactive] 
    [--api-key] [--force-english-output] [--verbosity] [--config-file]`

## <a name="description"></a>説明

`dotnet nuget delete` コマンドは、サーバーからパッケージを削除または一覧から削除します。 NuGet.org の場合、この操作ではパッケージを一覧から削除します。

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

`--verbosity <LEVEL>`

出力にこの量の詳細を表示します。 レベルには、`normal`、`quiet`、または `detailed` を指定できます。

`--config-file <FILE>`

NuGet の構成ファイルは、標準的な構成ファイルの検出とチェーン プロセスによって検出されたその他の構成ファイルに置き換えて、このコマンド専用に使用されます。 パスは絶対パスでも相対パスでもかまいません。
構成ファイルの詳細については、「[Configuring NuGet Behavior](https://docs.nuget.org/ndocs/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。 

## <a name="examples"></a>例

MyPackage パッケージのバージョン 1.0 を削除します。

`dotnet nuget delete MyPackage 1.0` 

ユーザーに資格情報やその他の入力を求めずに、MyPackage パッケージのバージョン 1.0 を削除します。

`dotnet nuget delete MyPackage 1.0 --non-interactive`

カスタムの構成ファイル *./config/My.Config* を指定して、MyPackage パッケージのバージョン 1.0 を削除します。

`dotnet nuget delete MyPackage 1.0 --config-file ./config/My.Config`

最も高い詳細レベルで、MyPackage パッケージのバージョン 1.0 を削除します。

`dotnet nuget delete MyPackage 1.0 --verbosity detailed`



<!--HONumber=Nov16_HO3-->


