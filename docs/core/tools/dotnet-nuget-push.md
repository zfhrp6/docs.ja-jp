---
title: dotnet nuget push コマンド - .NET Core CLI
description: dotnet nuget push コマンドでは、パッケージをサーバーにプッシュして発行します。
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 8a64f9cdc11d03bed82a132265c3b4e1de290807
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728577"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet nuget push` - パッケージをサーバーにプッシュして発行します。

## <a name="synopsis"></a>構文

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a>説明

`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。 プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。 構成ファイルの詳細については、「[Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。 NuGet の既定の構成は、*%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。

## <a name="arguments"></a>引数

`ROOT`

プッシュされるパッケージのファイル パスを指定します。

## <a name="options"></a>オプション

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-d|--disable-buffering`

メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。

`--force-english-output`

インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`-n|--no-symbols`

シンボルをプッシュしません (存在する場合でも)。

`--no-service-endpoint`

ソース URL に "api/v2/package" を追加しません。

`-s|--source <SOURCE>`

サーバー URL を指定します。 `DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。

`-sk|--symbol-api-key <API_KEY>`

シンボル サーバーの API キーです。

`-ss|--symbol-source <SOURCE>`

シンボル サーバーの URL を指定します。

`-t|--timeout <TIMEOUT>`

秒単位でサーバーにプッシュする場合のタイムアウトを指定します。 既定値は 300 秒 (5 分) です。 0 (0 秒) を指定すると、既定値が適用されます。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-d|--disable-buffering`

メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。

`--force-english-output`

インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`-n|--no-symbols`

シンボルをプッシュしません (存在する場合でも)。

`-s|--source <SOURCE>`

サーバー URL を指定します。 `DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。

`-sk|--symbol-api-key <API_KEY>`

シンボル サーバーの API キーです。

`-ss|--symbol-source <SOURCE>`

シンボル サーバーの URL を指定します。

`-t|--timeout <TIMEOUT>`

秒単位でサーバーにプッシュする場合のタイムアウトを指定します。 既定値は 300 秒 (5 分) です。 0 (0 秒) を指定すると、既定値が適用されます。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-d|--disable-buffering`

メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。

`--force-english-output`

インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-k|--api-key <API_KEY>`

サーバーの API キーです。

`-n|--no-symbols`

シンボルをプッシュしません (存在する場合でも)。

`-s|--source <SOURCE>`

サーバー URL を指定します。 `DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。

`-sk|--symbol-api-key <API_KEY>`

シンボル サーバーの API キーです。

`-ss|--symbol-source <SOURCE>`

シンボル サーバーの URL を指定します。

`-t|--timeout <TIMEOUT>`

秒単位でサーバーにプッシュする場合のタイムアウトを指定します。 既定値は 300 秒 (5 分) です。 0 (0 秒) を指定すると、既定値が適用されます。

---

## <a name="examples"></a>使用例

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
