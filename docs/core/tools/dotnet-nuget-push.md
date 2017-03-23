---
title: "dotnet-nuget-push コマンド | Microsoft Docs"
description: "dotnet-nuget-push コマンドでは、パッケージをサーバーにプッシュして発行します。"
keywords: "dotnet-nuget-push, CLI, CLI コマンド, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f54d9adf-94f8-41cc-bb52-42f7ca3be6ff
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 54ffd79cc9306ffcc5793990c3dc2e7534ed3f4b
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-nuget-push"></a>dotnet-nuget-push

## <a name="name"></a>名前

`dotnet-nuget-push` - パッケージをサーバーにプッシュして発行します。 

## <a name="synopsis"></a>構文

```
dotnet nuget push [<package>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-v|--verbosity]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>説明

`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。 プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。 構成ファイルの詳細については、「[Configuring NuGet Behavior](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。 NuGet の既定の構成は、*%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-s|--source <SOURCE>`

サーバー URL を指定します。 `DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。

`--symbols-source <SOURCE>`

シンボル サーバーの URL を指定します。

`-t|--timeout <TIMEOUT>`

秒単位でサーバーにプッシュする場合のタイムアウトを指定します。 既定値は 300 秒 (5 分) です。 0 を指定すると、この既定の設定値が指定されます。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`--symbol-api-key <API_KEY>`

シンボル サーバーの API キーです。

`-d|--disable-buffering`

メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。

`-n|--no-symbols`

シンボルをプッシュしないでください (存在する場合も含む)。

`--force-english-output`

すべてのログ出力を強制的に英語にします。 英語以外のコンピューター上で英語の出力を生成するという柔軟性があるだけでなく、このオプションで指定されたプラットフォーム全体での一貫性は、テキストのログを取得する自動化ツールに役立つ機能です。

`--verbosity <LEVEL>`

出力にこの量の詳細を表示します。 レベルには、`normal`、`quiet`、または `detailed` を指定できます。

## <a name="examples"></a>例

API キーを指定して、既定のプッシュ ソースに foo.nupkg をプッシュします。

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

API キーを指定して、カスタムのプッシュ ソース `http://customsource` に foo.nupkg をプッシュします。

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/` 

既定のプッシュ ソースに foo.nupkg をプッシュします。

`dotnet nuget push foo.nupkg` 

既定のシンボル ソースに foo.symbols.nupkg をプッシュします。

`dotnet nuget push foo.symbols.nupkg`

360 秒のタイムアウトを指定して、既定のプッシュ ソースに foo.nupkg をプッシュします。

`dotnet nuget push foo.nupkg --timeout 360`

既定のプッシュ ソースに現在のディレクトリ内のすべての .nupkg ファイルをプッシュします。

`dotnet nuget push *.nupkg`

カスタムの構成ファイル *./config/My.Config* を指定して、既定のプッシュ ソースに現在のディレクトリ内のすべての .nupkg ファイルをプッシュします。

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

最も高い詳細レベルで、既定のプッシュ ソースに現在のディレクトリ内のすべての .nupkg ファイルをプッシュします。

`dotnet nuget push *.nupkg --verbosity detailed`

