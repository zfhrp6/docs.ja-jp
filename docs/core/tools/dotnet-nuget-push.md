---
title: "dotnet-nuget-push コマンド - .NET Core CLI"
description: "dotnet-nuget-push コマンドでは、パッケージをサーバーにプッシュして発行します。"
keywords: "dotnet-nuget-push, CLI, CLI コマンド, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f54d9adf-94f8-41cc-bb52-42f7ca3be6ff
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 83da967d9d7432fcb422b88344ff597d45fc9e85
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-nuget-push"></a>dotnet-nuget push

## <a name="name"></a>名前

`dotnet-nuget push` - パッケージをサーバーにプッシュして発行します。

## <a name="synopsis"></a>構文

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>説明

`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。 プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。 構成ファイルの詳細については、「[Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。 NuGet の既定の構成は、*%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。

## <a name="arguments"></a>引数

`ROOT`

パッケージへのパスと、パッケージをサーバーにプッシュするための API キーを指定します。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-s|--source <SOURCE>`

サーバー URL を指定します。 `DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。

`--symbols-source <SOURCE>`

シンボル サーバーの URL を指定します。

`-t|--timeout <TIMEOUT>`

秒単位でサーバーにプッシュする場合のタイムアウトを指定します。 既定値は 300 秒 (5 分) です。 0 (0 秒) を指定すると、既定値が適用されます。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`--symbol-api-key <API_KEY>`

シンボル サーバーの API キーです。

`-d|--disable-buffering`

メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。

`-n|--no-symbols`

シンボルをプッシュしません (存在する場合でも)。

`--force-english-output`

すべてのログ出力を強制的に英語にします。

## <a name="examples"></a>例

API キーを指定して、既定のプッシュ ソースに *foo.nupkg* をプッシュします。

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

API キーを指定して、カスタム プッシュ ソース `http://customsource` に *foo.nupkg* をプッシュします。

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/` 

既定のプッシュ ソースに *foo.nupkg* をプッシュします。

`dotnet nuget push foo.nupkg` 

既定のシンボル ソースに *foo.symbols.nupkg* をプッシュします。

`dotnet nuget push foo.symbols.nupkg`

360 秒のタイムアウトを指定して、既定のプッシュ ソースに *foo.nupkg* をプッシュします。

`dotnet nuget push foo.nupkg --timeout 360`

既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。

`dotnet nuget push *.nupkg`

カスタムの構成ファイル *./config/My.Config* を指定して、既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

最も高い詳細レベルで、既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。

`dotnet nuget push *.nupkg --verbosity detailed`

