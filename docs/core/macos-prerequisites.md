---
title: "Mac における .NET Core の前提条件"
description: "macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: 5aac7566f532312c890bad07c901929ae826ece3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="0cabf-104">macOS における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="0cabf-104">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="0cabf-105">この記事では、macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="0cabf-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="0cabf-106">後述のサポート対象 OS のバージョンと依存関係は、Mac で .NET Core アプリを開発する 3 つの方法 ([好きなエディターでコマンド ラインを使用](tutorials/using-with-xplat-cli.md)、[Visual Studio Code を使用](https://code.visualstudio.com/)、および [Visual Studio for Mac を使用](https://www.visualstudio.com/vs/visual-studio-mac/)) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="0cabf-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="0cabf-107">サポート対象の macOS のバージョン</span><span class="sxs-lookup"><span data-stu-id="0cabf-107">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0cabf-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0cabf-108">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="0cabf-109">.NET Core 2.x は、macOS の次のバージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0cabf-109">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="0cabf-110">macOS 10.12 "Sierra" 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="0cabf-110">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="0cabf-111">.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cabf-111">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0cabf-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0cabf-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0cabf-113">.NET Core 1.x は、macOS の次のバージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0cabf-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="0cabf-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="0cabf-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="0cabf-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="0cabf-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="0cabf-116">.NET Core 1.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cabf-116">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="0cabf-117">.NET Core の依存関係</span><span class="sxs-lookup"><span data-stu-id="0cabf-117">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0cabf-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0cabf-118">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="0cabf-119">[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="0cabf-119">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="0cabf-120">macOS でインストールに関する問題が発生した場合は、[既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)に関するトピックで、インストールされているバージョンに関する記述をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0cabf-120">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0cabf-121">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0cabf-121">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="0cabf-122">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="0cabf-122">**.NET Core 1.x**</span></span>

<span data-ttu-id="0cabf-123">macOS で実行する場合、.NET Core 1.x には OpenSSL が必要になります。</span><span class="sxs-lookup"><span data-stu-id="0cabf-123">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="0cabf-124">OpenSSL を取得する簡単な方法は、macOS の [Homebrew ("brew")](https://brew.sh/) パッケージ マネージャーを使用することです。</span><span class="sxs-lookup"><span data-stu-id="0cabf-124">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="0cabf-125">*brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して OpenSSL をインストールします。</span><span class="sxs-lookup"><span data-stu-id="0cabf-125">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="0cabf-126">[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="0cabf-126">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="0cabf-127">macOS でインストールに関する問題が発生した場合は、「[1.0.0 Known Issues (1.0.0 の既知の問題)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)」と「[1.0.1 Known Issues (1.0.1 の既知の問題)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)」のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0cabf-127">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit"></a><span data-ttu-id="0cabf-128">開けるファイルの最大数を増やす</span><span class="sxs-lookup"><span data-stu-id="0cabf-128">Increase the maximum open file limit</span></span>

<span data-ttu-id="0cabf-129">開けるファイルに関する macOS の既定の最大数では、プロジェクトの復元や単体テストの実行など、一部の .NET Core ワークロードに十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="0cabf-129">The default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="0cabf-130">この上限は次の手順で増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="0cabf-130">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="0cabf-131">テキスト エディターを利用し、新しいファイル _/Library/LaunchDaemons/limit.maxfiles.plist_ を作成し、以下のコンテンツでファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="0cabf-131">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. <span data-ttu-id="0cabf-132">端末ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0cabf-132">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="0cabf-133">Mac を再起動して設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="0cabf-133">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="0cabf-134">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="0cabf-134">Visual Studio for Mac</span></span>

<span data-ttu-id="0cabf-135">.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0cabf-135">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="0cabf-136">ただし、Mac 上の統合開発環境で .NET Core アプリケーションを開発する場合には、[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0cabf-136">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="0cabf-137">macOS 上で Visual Studio for Mac を使用して .NET Core で開発を行うには、以下のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="0cabf-137">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="0cabf-138">サポートされているバージョンの macOS オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="0cabf-138">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="0cabf-139">OpenSSL (.NET Core 1.x のみ。NET Core 2.x では、macOS でネイティブ利用できるセキュリティ サービスが利用されます。)</span><span class="sxs-lookup"><span data-stu-id="0cabf-139">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="0cabf-140">.NET Core SDK for Mac</span><span class="sxs-lookup"><span data-stu-id="0cabf-140">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="0cabf-141">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="0cabf-141">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)
