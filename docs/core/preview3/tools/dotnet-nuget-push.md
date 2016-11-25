---
title: "dotnet-nuget-push コマンド | .NET Core SDK"
description: "dotnet-nuget-push コマンドでは、パッケージをサーバーにプッシュして発行します。"
keywords: "dotnet-nuget-push, CLI, CLI コマンド, .NET Core"
author: karann-msft
ms.author: mairaw
manager: wpickett
ms.date: 11/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f54d9adf-94f8-41cc-bb52-42f7ca3be6ff
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 04369a7f478cc77b6351f2fbee05d4e4ec8b19fb

---

#<a name="dotnet-nuget-push"></a>dotnet-nuget-push

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>名前 
`dotnet-nuget-push` - パッケージをサーバーにプッシュして発行します。 

## <a name="synopsis"></a>構文

`dotnet nuget push [<package>] [--help] [--source] [--symbols-source] 
    [--timeout] [--api-key] [--symbol-api-key] [--disable-buffering] [--no-symbols] 
    [--force-english-output] [--config-file] [--verbosity]`

## <a name="description"></a>説明

`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。 プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。 構成ファイルの詳細については、「[Configuring NuGet Behavior](https://docs.nuget.org/ndocs/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。 NuGet の既定の構成は、*%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。  

`-s|--source <SOURCE>`

サーバー URL を指定します。 DefaultPushSource 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。

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

`--config-file <FILE>`

NuGet の構成ファイルは、標準的な構成ファイルの検出とチェーン プロセスによって検出されたその他の構成ファイルに置き換えて、このコマンド専用に使用されます。 パスは絶対パスでも相対パスでもかまいません。
構成ファイルの詳細については、「[Configuring NuGet Behavior](https://docs.nuget.org/ndocs/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。 

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



<!--HONumber=Nov16_HO3-->


