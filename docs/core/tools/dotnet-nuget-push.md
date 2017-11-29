---
title: "dotnet nuget push コマンド - .NET Core CLI"
description: "dotnet nuget push コマンドでは、パッケージをサーバーにプッシュして発行します。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 6721615e4df820ab50ea4f79fbba30daeffe8165
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="20eb7-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="20eb7-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="20eb7-104">名前</span><span class="sxs-lookup"><span data-stu-id="20eb7-104">Name</span></span>

<span data-ttu-id="20eb7-105">`dotnet nuget push` - パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="20eb7-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="20eb7-106">構文</span><span class="sxs-lookup"><span data-stu-id="20eb7-106">Synopsis</span></span>

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="20eb7-107">説明</span><span class="sxs-lookup"><span data-stu-id="20eb7-107">Description</span></span>

<span data-ttu-id="20eb7-108">`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="20eb7-108">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="20eb7-109">プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。</span><span class="sxs-lookup"><span data-stu-id="20eb7-109">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="20eb7-110">構成ファイルの詳細については、「[Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="20eb7-110">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="20eb7-111">NuGet の既定の構成は、*%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="20eb7-111">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="20eb7-112">引数</span><span class="sxs-lookup"><span data-stu-id="20eb7-112">Arguments</span></span>

`ROOT`

<span data-ttu-id="20eb7-113">パッケージへのパスと、パッケージをサーバーにプッシュするための API キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="20eb7-113">Specify the path to the package and your API key to push the package to the server.</span></span>

## <a name="options"></a><span data-ttu-id="20eb7-114">オプション</span><span class="sxs-lookup"><span data-stu-id="20eb7-114">Options</span></span>

`-h|--help`

<span data-ttu-id="20eb7-115">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="20eb7-115">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="20eb7-116">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="20eb7-116">Specifies the server URL.</span></span> <span data-ttu-id="20eb7-117">`DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="20eb7-117">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`--symbols-source <SOURCE>`

<span data-ttu-id="20eb7-118">シンボル サーバーの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="20eb7-118">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="20eb7-119">秒単位でサーバーにプッシュする場合のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="20eb7-119">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="20eb7-120">既定値は 300 秒 (5 分) です。</span><span class="sxs-lookup"><span data-stu-id="20eb7-120">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="20eb7-121">0 (0 秒) を指定すると、既定値が適用されます。</span><span class="sxs-lookup"><span data-stu-id="20eb7-121">Specifying 0 (zero seconds) applies the default value.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="20eb7-122">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="20eb7-122">The API key for the server.</span></span>

`--symbol-api-key <API_KEY>`

<span data-ttu-id="20eb7-123">シンボル サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="20eb7-123">The API key for the symbol server.</span></span>

`-d|--disable-buffering`

<span data-ttu-id="20eb7-124">メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-124">Disables buffering when pushing to an HTTP(S) server to decrease memory usage.</span></span>

`-n|--no-symbols`

<span data-ttu-id="20eb7-125">シンボルをプッシュしません (存在する場合でも)。</span><span class="sxs-lookup"><span data-stu-id="20eb7-125">Doesn't push symbols (even if present).</span></span>

`--force-english-output`

<span data-ttu-id="20eb7-126">すべてのログ出力を強制的に英語にします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-126">Forces all logged output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="20eb7-127">例</span><span class="sxs-lookup"><span data-stu-id="20eb7-127">Examples</span></span>

<span data-ttu-id="20eb7-128">API キーを指定して、既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-128">Pushes *foo.nupkg* to the default push source, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="20eb7-129">API キーを指定して、カスタム プッシュ ソース `http://customsource` に *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-129">Push *foo.nupkg* to the custom push source `http://customsource`, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="20eb7-130">既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-130">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="20eb7-131">既定のシンボル ソースに *foo.symbols.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-131">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="20eb7-132">360 秒のタイムアウトを指定して、既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-132">Pushes *foo.nupkg* to the default push source, specifying a 360 second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="20eb7-133">既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-133">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="20eb7-134">カスタムの構成ファイル *./config/My.Config* を指定して、既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-134">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

<span data-ttu-id="20eb7-135">最も高い詳細レベルで、既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="20eb7-135">Push all *.nupkg* files in the current directory to the default push source with maximum verbosity:</span></span>

`dotnet nuget push *.nupkg --verbosity detailed`
