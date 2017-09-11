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

# <a name="dotnet-nuget-push"></a><span data-ttu-id="0602b-104">dotnet-nuget push</span><span class="sxs-lookup"><span data-stu-id="0602b-104">dotnet-nuget push</span></span>

## <a name="name"></a><span data-ttu-id="0602b-105">名前</span><span class="sxs-lookup"><span data-stu-id="0602b-105">Name</span></span>

<span data-ttu-id="0602b-106">`dotnet-nuget push` - パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="0602b-106">`dotnet-nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0602b-107">構文</span><span class="sxs-lookup"><span data-stu-id="0602b-107">Synopsis</span></span>

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="0602b-108">説明</span><span class="sxs-lookup"><span data-stu-id="0602b-108">Description</span></span>

<span data-ttu-id="0602b-109">`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="0602b-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="0602b-110">プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。</span><span class="sxs-lookup"><span data-stu-id="0602b-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="0602b-111">構成ファイルの詳細については、「[Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0602b-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="0602b-112">NuGet の既定の構成は、*%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="0602b-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="0602b-113">引数</span><span class="sxs-lookup"><span data-stu-id="0602b-113">Arguments</span></span>

`ROOT`

<span data-ttu-id="0602b-114">パッケージへのパスと、パッケージをサーバーにプッシュするための API キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="0602b-114">Specify the path to the package and your API key to push the package to the server.</span></span>

## <a name="options"></a><span data-ttu-id="0602b-115">オプション</span><span class="sxs-lookup"><span data-stu-id="0602b-115">Options</span></span>

`-h|--help`

<span data-ttu-id="0602b-116">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="0602b-116">Prints out a short help for the command.</span></span>  

`-s|--source <SOURCE>`

<span data-ttu-id="0602b-117">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="0602b-117">Specifies the server URL.</span></span> <span data-ttu-id="0602b-118">`DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="0602b-118">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`--symbols-source <SOURCE>`

<span data-ttu-id="0602b-119">シンボル サーバーの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="0602b-119">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="0602b-120">秒単位でサーバーにプッシュする場合のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="0602b-120">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="0602b-121">既定値は 300 秒 (5 分) です。</span><span class="sxs-lookup"><span data-stu-id="0602b-121">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="0602b-122">0 (0 秒) を指定すると、既定値が適用されます。</span><span class="sxs-lookup"><span data-stu-id="0602b-122">Specifying 0 (zero seconds) applies the default value.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0602b-123">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="0602b-123">The API key for the server.</span></span>

`--symbol-api-key <API_KEY>`

<span data-ttu-id="0602b-124">シンボル サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="0602b-124">The API key for the symbol server.</span></span>

`-d|--disable-buffering`

<span data-ttu-id="0602b-125">メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="0602b-125">Disables buffering when pushing to an HTTP(S) server to decrease memory usage.</span></span>

`-n|--no-symbols`

<span data-ttu-id="0602b-126">シンボルをプッシュしません (存在する場合でも)。</span><span class="sxs-lookup"><span data-stu-id="0602b-126">Doesn't push symbols (even if present).</span></span>

`--force-english-output`

<span data-ttu-id="0602b-127">すべてのログ出力を強制的に英語にします。</span><span class="sxs-lookup"><span data-stu-id="0602b-127">Forces all logged output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="0602b-128">例</span><span class="sxs-lookup"><span data-stu-id="0602b-128">Examples</span></span>

<span data-ttu-id="0602b-129">API キーを指定して、既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="0602b-129">Pushes *foo.nupkg* to the default push source, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="0602b-130">API キーを指定して、カスタム プッシュ ソース `http://customsource` に *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="0602b-130">Push *foo.nupkg* to the custom push source `http://customsource`, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/` 

<span data-ttu-id="0602b-131">既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="0602b-131">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg` 

<span data-ttu-id="0602b-132">既定のシンボル ソースに *foo.symbols.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="0602b-132">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="0602b-133">360 秒のタイムアウトを指定して、既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="0602b-133">Pushes *foo.nupkg* to the default push source, specifying a 360 second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="0602b-134">既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="0602b-134">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="0602b-135">カスタムの構成ファイル *./config/My.Config* を指定して、既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="0602b-135">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

<span data-ttu-id="0602b-136">最も高い詳細レベルで、既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="0602b-136">Push all *.nupkg* files in the current directory to the default push source with maximum verbosity:</span></span>

`dotnet nuget push *.nupkg --verbosity detailed`

