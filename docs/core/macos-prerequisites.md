---
title: "Mac における .NET Core の前提条件"
description: "macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 07/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8feaee2cbfa55e23bd49c0ab76d995f15be343b4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="prerequisites-for-net-core-on-mac"></a><span data-ttu-id="b3ca3-104">Mac における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="b3ca3-104">Prerequisites for .NET Core on Mac</span></span>

<span data-ttu-id="b3ca3-105">この記事では、macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="b3ca3-106">後述のサポート対象 OS のバージョンと依存関係は、Mac で .NET Core アプリを開発する 3 つの方法 ([好きなエディターでコマンド ラインを使用](tutorials/using-with-xplat-cli.md)、[Visual Studio Code を使用](https://code.visualstudio.com/)、および [Visual Studio for Mac を使用](https://www.visualstudio.com/vs/visual-studio-mac/)) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="b3ca3-107">サポート対象の macOS のバージョン</span><span class="sxs-lookup"><span data-stu-id="b3ca3-107">Supported macOS versions</span></span>

<span data-ttu-id="b3ca3-108">.NET Core は、macOS の次のバージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-108">.NET Core is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="b3ca3-109">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="b3ca3-109">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="b3ca3-110">macOS 10.11 "El Capitan" (.NET Core 1.x のみ)</span><span class="sxs-lookup"><span data-stu-id="b3ca3-110">macOS 10.11 "El Capitan" (.NET Core 1.x only)</span></span>

<span data-ttu-id="b3ca3-111">サポート対象のオペレーティング システムの完全なリストは、「[Supported OS Versions (サポート対象の OS のバージョン)](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions)」の記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-111">See [Supported OS Versions](https://github.com/dotnet/core/blob/master/roadmap.md#supported-os-versions) for the complete list of supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="b3ca3-112">.NET Core の依存関係</span><span class="sxs-lookup"><span data-stu-id="b3ca3-112">.NET Core dependencies</span></span>

<span data-ttu-id="b3ca3-113">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="b3ca3-113">**.NET Core 1.x**</span></span>

<span data-ttu-id="b3ca3-114">macOS で実行する場合、.NET Core 1.x には OpenSSL が必要になります。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-114">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="b3ca3-115">OpenSSL を取得する簡単な方法は、macOS の [Homebrew ("brew")](https://brew.sh/) パッケージ マネージャーを使用することです。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-115">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="b3ca3-116">*brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して OpenSSL をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-116">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="b3ca3-117">[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-117">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="b3ca3-118">macOS でインストールに関する問題が発生した場合は、「[1.0.0 Known Issues (1.0.0 の既知の問題)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)」と「[1.0.1 Known Issues (1.0.1 の既知の問題)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)」のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-118">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

<span data-ttu-id="b3ca3-119">**.NET Core 2.x**</span><span class="sxs-lookup"><span data-stu-id="b3ca3-119">**.NET Core 2.x**</span></span>

<span data-ttu-id="b3ca3-120">[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-120">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="b3ca3-121">macOS でインストールに関する問題が発生した場合は、[既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)に関するトピックで、インストールされているバージョンに関する記述をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-121">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="b3ca3-122">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="b3ca3-122">Visual Studio for Mac</span></span>

<span data-ttu-id="b3ca3-123">.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-123">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="b3ca3-124">ただし、Mac 上の統合開発環境で .NET Core アプリケーションを開発する場合には、[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-124">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="b3ca3-125">macOS 上で Visual Studio for Mac を使用して .NET Core で開発を行うには、以下のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="b3ca3-125">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="b3ca3-126">サポートされているバージョンの macOS オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="b3ca3-126">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="b3ca3-127">OpenSSL (.NET Core 1.x のみ。NET Core 2.x では、macOS でネイティブ利用できるセキュリティ サービスが利用されます。)</span><span class="sxs-lookup"><span data-stu-id="b3ca3-127">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="b3ca3-128">.NET Core SDK for Mac</span><span class="sxs-lookup"><span data-stu-id="b3ca3-128">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="b3ca3-129">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="b3ca3-129">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

