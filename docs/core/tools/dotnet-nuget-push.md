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
# <a name="dotnet-nuget-push"></a><span data-ttu-id="2467b-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="2467b-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2467b-104">name</span><span class="sxs-lookup"><span data-stu-id="2467b-104">Name</span></span>

<span data-ttu-id="2467b-105">`dotnet nuget push` - パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="2467b-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2467b-106">構文</span><span class="sxs-lookup"><span data-stu-id="2467b-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2467b-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2467b-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2467b-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2467b-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2467b-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2467b-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="2467b-110">説明</span><span class="sxs-lookup"><span data-stu-id="2467b-110">Description</span></span>

<span data-ttu-id="2467b-111">`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="2467b-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="2467b-112">プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。</span><span class="sxs-lookup"><span data-stu-id="2467b-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="2467b-113">構成ファイルの詳細については、「[Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2467b-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="2467b-114">NuGet の既定の構成は、*%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="2467b-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="2467b-115">引数</span><span class="sxs-lookup"><span data-stu-id="2467b-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="2467b-116">プッシュされるパッケージのファイル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="2467b-117">オプション</span><span class="sxs-lookup"><span data-stu-id="2467b-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2467b-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2467b-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="2467b-119">メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="2467b-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="2467b-120">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="2467b-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="2467b-121">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="2467b-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="2467b-122">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="2467b-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="2467b-123">シンボルをプッシュしません (存在する場合でも)。</span><span class="sxs-lookup"><span data-stu-id="2467b-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="2467b-124">ソース URL に "api/v2/package" を追加しません。</span><span class="sxs-lookup"><span data-stu-id="2467b-124">Doesn't append "api/v2/package" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="2467b-125">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-125">Specifies the server URL.</span></span> <span data-ttu-id="2467b-126">`DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="2467b-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="2467b-127">シンボル サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="2467b-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="2467b-128">シンボル サーバーの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="2467b-129">秒単位でサーバーにプッシュする場合のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="2467b-130">既定値は 300 秒 (5 分) です。</span><span class="sxs-lookup"><span data-stu-id="2467b-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="2467b-131">0 (0 秒) を指定すると、既定値が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2467b-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2467b-132">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2467b-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="2467b-133">メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="2467b-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="2467b-134">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="2467b-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="2467b-135">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="2467b-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="2467b-136">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="2467b-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="2467b-137">シンボルをプッシュしません (存在する場合でも)。</span><span class="sxs-lookup"><span data-stu-id="2467b-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="2467b-138">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-138">Specifies the server URL.</span></span> <span data-ttu-id="2467b-139">`DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="2467b-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="2467b-140">シンボル サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="2467b-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="2467b-141">シンボル サーバーの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="2467b-142">秒単位でサーバーにプッシュする場合のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="2467b-143">既定値は 300 秒 (5 分) です。</span><span class="sxs-lookup"><span data-stu-id="2467b-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="2467b-144">0 (0 秒) を指定すると、既定値が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2467b-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2467b-145">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2467b-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="2467b-146">メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="2467b-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="2467b-147">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="2467b-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="2467b-148">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="2467b-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="2467b-149">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="2467b-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="2467b-150">シンボルをプッシュしません (存在する場合でも)。</span><span class="sxs-lookup"><span data-stu-id="2467b-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="2467b-151">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-151">Specifies the server URL.</span></span> <span data-ttu-id="2467b-152">`DefaultPushSource` 構成値が NuGet 構成ファイルに設定されない限り、このオプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="2467b-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="2467b-153">シンボル サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="2467b-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="2467b-154">シンボル サーバーの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="2467b-155">秒単位でサーバーにプッシュする場合のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="2467b-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="2467b-156">既定値は 300 秒 (5 分) です。</span><span class="sxs-lookup"><span data-stu-id="2467b-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="2467b-157">0 (0 秒) を指定すると、既定値が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2467b-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="2467b-158">使用例</span><span class="sxs-lookup"><span data-stu-id="2467b-158">Examples</span></span>

<span data-ttu-id="2467b-159">API キーを指定して、既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="2467b-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="2467b-160">API キーを指定して、カスタム プッシュ ソース `http://customsource` に *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="2467b-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="2467b-161">既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="2467b-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="2467b-162">既定のシンボル ソースに *foo.symbols.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="2467b-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="2467b-163">360 秒のタイムアウトを指定して、既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="2467b-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="2467b-164">既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="2467b-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="2467b-165">カスタムの構成ファイル *./config/My.Config* を指定して、既定のプッシュ ソースに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="2467b-165">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
