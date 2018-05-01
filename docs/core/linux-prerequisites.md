---
title: Linux における .NET Core の前提条件
description: Linux マシンで .NET Core アプリケーションを開発、展開、および実行するために必要なサポートされている Linux のバージョンと .NET Core の依存関係。
author: jralexander
ms.author: johalex
ms.date: 04/19/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 9d986ed56bbc6f803988fde4b5500cd5d5364050
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="bf5ea-103">Linux における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="bf5ea-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="bf5ea-104">この記事では、Linux で .NET Core アプリケーションを開発するために必要な依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="bf5ea-105">後述のサポートされている Linux ディストリビューション/バージョンと依存関係は、Linux で .NET Core アプリを開発する次の 2 つの方法に適用されます。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="bf5ea-106">好みのエディターでのコマンドライン</span><span class="sxs-lookup"><span data-stu-id="bf5ea-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="bf5ea-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bf5ea-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="bf5ea-108">.NET Core SDK パッケージは、運用サーバー/環境には必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="bf5ea-109">運用環境に展開されるアプリに必要なものは、.NET Core ランタイム パッケージだけです。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="bf5ea-110">.NET Core ランタイムは自己完結型の展開の一部としてアプリと供に展開されますが、フレームワークに依存して展開されるアプリでは個別に展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="bf5ea-111">フレームワークに依存する展開と自己完結型の展開について詳しくは、「[.NET Core アプリケーションの展開](./deploying/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="bf5ea-112">具体的なガイドラインについては、「[Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」(自己完結型 Linux アプリケーション) もご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="bf5ea-113">サポートされている Linux バージョン</span><span class="sxs-lookup"><span data-stu-id="bf5ea-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf5ea-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bf5ea-115">.NET Core 2.x は、1 つのオペレーティング システムとして Linux を扱います。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="bf5ea-116">サポートされている Linux ディストリビューション用に、1 つの Linux ビルド (チップ アーキテクチャあたり) があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="bf5ea-117">.NET Core 2.x は、次の Linux 64 ビット (`x86_64` または `amd64`) ディストリビューション/バージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-117">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="bf5ea-118">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="bf5ea-118">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="bf5ea-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bf5ea-119">CentOS 7</span></span>
* <span data-ttu-id="bf5ea-120">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="bf5ea-120">Oracle Linux 7</span></span>
* <span data-ttu-id="bf5ea-121">Fedora 27、26</span><span class="sxs-lookup"><span data-stu-id="bf5ea-121">Fedora 27, 26</span></span>
* <span data-ttu-id="bf5ea-122">Debian 9、8.7 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bf5ea-122">Debian 9, 8.7 or later versions</span></span>
* <span data-ttu-id="bf5ea-123">Ubuntu 17.10、16.04、14.04</span><span class="sxs-lookup"><span data-stu-id="bf5ea-123">Ubuntu 17.10, 16.04, 14.04</span></span>
* <span data-ttu-id="bf5ea-124">Linux Mint 18、17</span><span class="sxs-lookup"><span data-stu-id="bf5ea-124">Linux Mint 18, 17</span></span>
* <span data-ttu-id="bf5ea-125">openSUSE 42.3 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bf5ea-125">openSUSE 42.3 or later versions</span></span>
* <span data-ttu-id="bf5ea-126">SUSE Enterprise Linux (SLES) 12 Service Pack 2 以降</span><span class="sxs-lookup"><span data-stu-id="bf5ea-126">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later</span></span>

<span data-ttu-id="bf5ea-127">.NET Core 2.x でサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS のバージョン、ライフサイクル ポリシー リンクの完全なリストについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」(.NET Core 2.x がサポートされる OS のバージョン) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-127">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf5ea-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-128">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bf5ea-129">.NET Core 1.x は、次の Linux 64 ビット (`x86_64` または `amd64`) ディストリビューション/バージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-129">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="bf5ea-130">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="bf5ea-130">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="bf5ea-131">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bf5ea-131">CentOS 7</span></span>
* <span data-ttu-id="bf5ea-132">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="bf5ea-132">Oracle Linux 7</span></span>
* <span data-ttu-id="bf5ea-133">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="bf5ea-133">Fedora 26</span></span>
* <span data-ttu-id="bf5ea-134">Debian 8.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bf5ea-134">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="bf5ea-135">Ubuntu 16.04、14.04</span><span class="sxs-lookup"><span data-stu-id="bf5ea-135">Ubuntu 16.04, 14.04</span></span>
* <span data-ttu-id="bf5ea-136">Linux Mint 18、17</span><span class="sxs-lookup"><span data-stu-id="bf5ea-136">Linux Mint 18, 17</span></span>
* <span data-ttu-id="bf5ea-137">openSUSE 42.3 以降のバージョン (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-137">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="bf5ea-138">.NET Core 1.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-138">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="bf5ea-139">Linux ディストリビューションの依存関係</span><span class="sxs-lookup"><span data-stu-id="bf5ea-139">Linux distribution dependencies</span></span>

<span data-ttu-id="bf5ea-140">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-140">The following are intended to be examples.</span></span> <span data-ttu-id="bf5ea-141">選択した Linux ディストリビューションで、バージョンと名前が多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-141">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="bf5ea-142">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bf5ea-142">Ubuntu</span></span>

<span data-ttu-id="bf5ea-143">Ubuntu ディストリビューションには、次のライブラリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-143">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="bf5ea-144">libunwind8</span><span class="sxs-lookup"><span data-stu-id="bf5ea-144">libunwind8</span></span>
* <span data-ttu-id="bf5ea-145">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="bf5ea-145">liblttng-ust0</span></span>
* <span data-ttu-id="bf5ea-146">libcurl3</span><span class="sxs-lookup"><span data-stu-id="bf5ea-146">libcurl3</span></span>
* <span data-ttu-id="bf5ea-147">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="bf5ea-147">libssl1.0.0</span></span>
* <span data-ttu-id="bf5ea-148">libuuid1</span><span class="sxs-lookup"><span data-stu-id="bf5ea-148">libuuid1</span></span>
* <span data-ttu-id="bf5ea-149">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="bf5ea-149">libkrb5-3</span></span>
* <span data-ttu-id="bf5ea-150">zlib1g</span><span class="sxs-lookup"><span data-stu-id="bf5ea-150">zlib1g</span></span>
* <span data-ttu-id="bf5ea-151">libicu52 (14.x 用)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-151">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="bf5ea-152">libicu55 (16.x 用)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-152">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="bf5ea-153">libicu57 (17.x 用)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-153">libicu57 (for 17.x)</span></span>

### <a name="centos"></a><span data-ttu-id="bf5ea-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="bf5ea-154">CentOS</span></span>

<span data-ttu-id="bf5ea-155">CentOS ディストリビューションには、次のライブラリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-155">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="bf5ea-156">libunwind</span><span class="sxs-lookup"><span data-stu-id="bf5ea-156">libunwind</span></span>
* <span data-ttu-id="bf5ea-157">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="bf5ea-157">lttng-ust</span></span>
* <span data-ttu-id="bf5ea-158">libcurl</span><span class="sxs-lookup"><span data-stu-id="bf5ea-158">libcurl</span></span>
* <span data-ttu-id="bf5ea-159">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="bf5ea-159">openssl-libs</span></span>
* <span data-ttu-id="bf5ea-160">libuuid</span><span class="sxs-lookup"><span data-stu-id="bf5ea-160">libuuid</span></span>
* <span data-ttu-id="bf5ea-161">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="bf5ea-161">krb5-libs</span></span>
* <span data-ttu-id="bf5ea-162">libicu</span><span class="sxs-lookup"><span data-stu-id="bf5ea-162">libicu</span></span>
* <span data-ttu-id="bf5ea-163">zlib</span><span class="sxs-lookup"><span data-stu-id="bf5ea-163">zlib</span></span>

<span data-ttu-id="bf5ea-164">依存関係の詳細については、「[Self-contained Linux applications (自己完結型 Linux アプリケーション)](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-164">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="bf5ea-165">ネイティブ インストーラーを使用した .NET Core の依存関係のインストール</span><span class="sxs-lookup"><span data-stu-id="bf5ea-165">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="bf5ea-166">.NET Core ネイティブ インストーラーは、サポートされている Linux ディストリビューション/バージョンに利用できます。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-166">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="bf5ea-167">このネイティブ インストーラーは、サーバーへの admin (sudo) アクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-167">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="bf5ea-168">ネイティブ インストーラーを使用することの利点は、.NET Core ネイティブの依存関係がすべてインストールされることです。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-168">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="bf5ea-169">また、ネイティブ インストーラーでは、.NET Core SDK もシステム全体にインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-169">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="bf5ea-170">Linux では、2 つのインストーラー パッケージから選択できます。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-170">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="bf5ea-171">フィードベースのパッケージ マネージャー (Ubuntu では apt-get、CentOS/RHEL では yum など) を使用する</span><span class="sxs-lookup"><span data-stu-id="bf5ea-171">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="bf5ea-172">パッケージ自体 (DEB または RPM) を使用する</span><span class="sxs-lookup"><span data-stu-id="bf5ea-172">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="bf5ea-173">.NET Core インストーラー スクリプトを使用したスクリプトのインストール</span><span class="sxs-lookup"><span data-stu-id="bf5ea-173">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="bf5ea-174">[dotnet-install スクリプト](./tools/dotnet-install-script.md)は、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-174">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="bf5ea-175">このスクリプトは [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh) からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-175">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="bf5ea-176">インストーラーの bash スクリプトは、自動化シナリオと管理者以外のインストールで使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-176">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="bf5ea-177">このスクリプトは、PowerShell のスイッチも読み取るので、Linux/OS X システムのスクリプトで使うことができます。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-177">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a><span data-ttu-id="bf5ea-178">サポートされている Red Hat Enterprise Linux (RHEL) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf5ea-178">Install .NET Core for supported Red Hat Enterprise Linux (RHEL) versions</span></span>

<span data-ttu-id="bf5ea-179">.NET Core をサポートされている RHEL のバージョンにインストールするには:</span><span class="sxs-lookup"><span data-stu-id="bf5ea-179">To install .NET Core on supported RHEL versions:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf5ea-180">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-180">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bf5ea-181">最新のインストール情報については、サポートされている RHEL のバージョンの [.NET Core 2.x SDK とランタイムのインストーラーの説明](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-181">To ensure you have the latest installation information, follow the [.NET Core 2.x SDK and Runtime Installer instructions](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current) for supported RHEL versions.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf5ea-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-182">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bf5ea-183">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-183">**.NET Core 1.1**</span></span>

1. <span data-ttu-id="bf5ea-184">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-184">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2.  <span data-ttu-id="bf5ea-185">Red Hat Enterprise Linux インストール情報での最新の .NET Core 1.1 については、[.NET Core 1.1 の使用開始ガイド](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)をご覧ください</span><span class="sxs-lookup"><span data-stu-id="bf5ea-185">For the latest .NET Core 1.1 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)</span></span>
     
<span data-ttu-id="bf5ea-186">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-186">**.NET Core 1.0**</span></span>

1. <span data-ttu-id="bf5ea-187">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-187">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2.  <span data-ttu-id="bf5ea-188">Red Hat Enterprise Linux インストール情報での最新の .NET Core 1.0 については、[.NET Core 1.0 の使用開始ガイド](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)をご覧ください</span><span class="sxs-lookup"><span data-stu-id="bf5ea-188">For the latest .NET Core 1.0 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.0 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)</span></span>

<span data-ttu-id="bf5ea-189">Red Hat .NET チャネル アクセスの登録に関するヘルプについては、Red Hat の「[Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)」 (.NET Core 1.1 ファースト ステップ ガイドの第 1 章) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-189">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a><span data-ttu-id="bf5ea-190">サポートされている Ubuntu および Linux Mint のディストリビューション/バージョン (64 ビット) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf5ea-190">Install .NET Core for supported Ubuntu and Linux Mint distributions/versions (64 bit)</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf5ea-191">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-191">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="bf5ea-192">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-192">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-193">サポートされている Ubuntu および Linux Mint のディストリビューション/バージョン (64 ビット) に .NET Core 2.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-193">Install .NET Core 2.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):</span></span>

<span data-ttu-id="bf5ea-194">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-194">**.NET Core 2.0**</span></span>

|<span data-ttu-id="bf5ea-195">ランタイム/SDK</span><span class="sxs-lookup"><span data-stu-id="bf5ea-195">Runtimes / SDKs</span></span>          |<span data-ttu-id="bf5ea-196">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="bf5ea-196">Ubuntu 17.10</span></span>  |<span data-ttu-id="bf5ea-197">Ubuntu 16.04 / Linux Mint 18</span><span class="sxs-lookup"><span data-stu-id="bf5ea-197">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="bf5ea-198">Ubuntu 14.04 / Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="bf5ea-198">Ubuntu 14.04 / Linux Mint 17</span></span>|
|-------------------------|--------------|----------------------------|----------------------------|
|<span data-ttu-id="bf5ea-199">.NET Core ランタイム 2.0.6</span><span class="sxs-lookup"><span data-stu-id="bf5ea-199">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="bf5ea-200">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-200">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[<span data-ttu-id="bf5ea-201">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-201">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[<span data-ttu-id="bf5ea-202">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-202">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|<span data-ttu-id="bf5ea-203">.NET Core ランタイム 2.0.5</span><span class="sxs-lookup"><span data-stu-id="bf5ea-203">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="bf5ea-204">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-204">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[<span data-ttu-id="bf5ea-205">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-205">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[<span data-ttu-id="bf5ea-206">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-206">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|<span data-ttu-id="bf5ea-207">.NET Core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="bf5ea-207">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="bf5ea-208">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-208">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[<span data-ttu-id="bf5ea-209">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-209">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[<span data-ttu-id="bf5ea-210">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-210">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|<span data-ttu-id="bf5ea-211">.NET Core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="bf5ea-211">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="bf5ea-212">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-212">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[<span data-ttu-id="bf5ea-213">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-213">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[<span data-ttu-id="bf5ea-214">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-214">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |

<span data-ttu-id="bf5ea-215">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-215">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="bf5ea-216">Visual Studio で .NET Core 2.1 を使用するには、[Visual Studio 2017 15.7 Preview 1 以降をインストールする](https://www.visualstudio.com/vs/preview)必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-216">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="bf5ea-217">ランタイム/SDK</span><span class="sxs-lookup"><span data-stu-id="bf5ea-217">Runtimes / SDKs</span></span>                  |<span data-ttu-id="bf5ea-218">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="bf5ea-218">Ubuntu 17.10</span></span>    |<span data-ttu-id="bf5ea-219">Ubuntu 16.04 / Linux Mint 18</span><span class="sxs-lookup"><span data-stu-id="bf5ea-219">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="bf5ea-220">Ubuntu 14.04 / Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="bf5ea-220">Ubuntu 14.04 / Linux Mint 17</span></span>|
|---------------------------------|----------------|----------------------------|----------------------------|
|<span data-ttu-id="bf5ea-221">.NET Core ランタイム 2.1.0-preview2</span><span class="sxs-lookup"><span data-stu-id="bf5ea-221">.NET Core Runtime 2.1.0-preview2</span></span> |[<span data-ttu-id="bf5ea-222">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-222">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview2)|[<span data-ttu-id="bf5ea-223">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-223">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview2)            |[<span data-ttu-id="bf5ea-224">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-224">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview2)            |
|<span data-ttu-id="bf5ea-225">.NET Core ランタイム 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="bf5ea-225">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="bf5ea-226">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-226">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview1)|[<span data-ttu-id="bf5ea-227">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-227">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview1)            |[<span data-ttu-id="bf5ea-228">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-228">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview1)            |
|<span data-ttu-id="bf5ea-229">.NET Core SDK 2.1.300-preview2</span><span class="sxs-lookup"><span data-stu-id="bf5ea-229">.NET Core SDK 2.1.300-preview2</span></span>   |[<span data-ttu-id="bf5ea-230">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-230">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview2)|[<span data-ttu-id="bf5ea-231">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-231">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview2)            |[<span data-ttu-id="bf5ea-232">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-232">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview2)
|<span data-ttu-id="bf5ea-233">.NET Core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="bf5ea-233">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="bf5ea-234">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-234">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview1)|[<span data-ttu-id="bf5ea-235">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-235">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview1)            |[<span data-ttu-id="bf5ea-236">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-236">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview1)            |


# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf5ea-237">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-237">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="bf5ea-238">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-238">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-239">サポートされている Ubuntu および Linux Mint のディストリビューション/バージョン (64 ビット) に .NET Core 1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-239">Install .NET Core 1.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):</span></span>

| <span data-ttu-id="bf5ea-240">ランタイム/SDK</span><span class="sxs-lookup"><span data-stu-id="bf5ea-240">Runtimes / SDKs</span></span>         |<span data-ttu-id="bf5ea-241">Ubuntu 16.04 / Linux Mint 18</span><span class="sxs-lookup"><span data-stu-id="bf5ea-241">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="bf5ea-242">Ubuntu 14.04 / Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="bf5ea-242">Ubuntu 14.04 / Linux Mint 17</span></span>|
|-------------------------|----------------------------|----------------------------|
|<span data-ttu-id="bf5ea-243">.NET Core ランタイム 1.1.7</span><span class="sxs-lookup"><span data-stu-id="bf5ea-243">.NET Core Runtime 1.1.7</span></span>  |[<span data-ttu-id="bf5ea-244">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-244">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="bf5ea-245">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-245">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="bf5ea-246">.NET Core ランタイム 1.1.6</span><span class="sxs-lookup"><span data-stu-id="bf5ea-246">.NET Core Runtime 1.1.6</span></span>  |[<span data-ttu-id="bf5ea-247">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-247">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="bf5ea-248">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-248">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="bf5ea-249">.NET Core ランタイム 1.0.10</span><span class="sxs-lookup"><span data-stu-id="bf5ea-249">.NET Core Runtime 1.0.10</span></span> |[<span data-ttu-id="bf5ea-250">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-250">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="bf5ea-251">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-251">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="bf5ea-252">.NET Core ランタイム 1.0.9</span><span class="sxs-lookup"><span data-stu-id="bf5ea-252">.NET Core Runtime 1.0.9</span></span>  |[<span data-ttu-id="bf5ea-253">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-253">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="bf5ea-254">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-254">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="bf5ea-255">.NET Core SDK 1.1.8</span><span class="sxs-lookup"><span data-stu-id="bf5ea-255">.NET Core SDK 1.1.8</span></span>      |[<span data-ttu-id="bf5ea-256">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-256">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="bf5ea-257">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-257">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="bf5ea-258">.NET Core SDK 1.1.7</span><span class="sxs-lookup"><span data-stu-id="bf5ea-258">.NET Core SDK 1.1.7</span></span>      |[<span data-ttu-id="bf5ea-259">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-259">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="bf5ea-260">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-260">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="bf5ea-261">.NET Core SDK 1.0.4</span><span class="sxs-lookup"><span data-stu-id="bf5ea-261">.NET Core SDK 1.0.4</span></span>      |[<span data-ttu-id="bf5ea-262">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-262">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="bf5ea-263">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-263">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="bf5ea-264">.NET Core SDK 1.0.1</span><span class="sxs-lookup"><span data-stu-id="bf5ea-264">.NET Core SDK 1.0.1</span></span>      |[<span data-ttu-id="bf5ea-265">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-265">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="bf5ea-266">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-266">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a><span data-ttu-id="bf5ea-267">サポートされている Debian のバージョン (64 ビット) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf5ea-267">Install .NET Core for supported Debian versions (64 bit)</span></span>

<span data-ttu-id="bf5ea-268">サポートされている Debian のバージョン (64 ビット) に .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="bf5ea-268">To install .NET Core on supported Debian versions (64 bit):</span></span>

> [!NOTE]
> <span data-ttu-id="bf5ea-269">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-269">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf5ea-270">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-270">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="bf5ea-271">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-271">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-272">サポートされている Debian のバージョン (64 ビット) に .NET Core 2.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-272">Install .NET Core 2.x on supported Debian versions (64 bit):</span></span>

<span data-ttu-id="bf5ea-273">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-273">**.NET Core 2.0**</span></span>

|<span data-ttu-id="bf5ea-274">ランタイム/SDK</span><span class="sxs-lookup"><span data-stu-id="bf5ea-274">Runtimes / SDKs</span></span>          |<span data-ttu-id="bf5ea-275">Debian 9</span><span class="sxs-lookup"><span data-stu-id="bf5ea-275">Debian 9</span></span>       |<span data-ttu-id="bf5ea-276">Debian 8</span><span class="sxs-lookup"><span data-stu-id="bf5ea-276">Debian 8</span></span>       |
|-------------------------|---------------|---------------|
|<span data-ttu-id="bf5ea-277">.NET Core ランタイム 2.0.6</span><span class="sxs-lookup"><span data-stu-id="bf5ea-277">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="bf5ea-278">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-278">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[<span data-ttu-id="bf5ea-279">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-279">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|<span data-ttu-id="bf5ea-280">.NET Core ランタイム 2.0.5</span><span class="sxs-lookup"><span data-stu-id="bf5ea-280">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="bf5ea-281">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-281">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[<span data-ttu-id="bf5ea-282">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-282">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|<span data-ttu-id="bf5ea-283">.NET Core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="bf5ea-283">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="bf5ea-284">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-284">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[<span data-ttu-id="bf5ea-285">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-285">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|<span data-ttu-id="bf5ea-286">.NET Core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="bf5ea-286">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="bf5ea-287">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-287">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[<span data-ttu-id="bf5ea-288">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-288">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |

<span data-ttu-id="bf5ea-289">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-289">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="bf5ea-290">Visual Studio で .NET Core 2.1 を使用するには、[Visual Studio 2017 15.7 Preview 1 以降をインストールする](https://www.visualstudio.com/vs/preview)必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-290">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="bf5ea-291">ランタイム/SDK</span><span class="sxs-lookup"><span data-stu-id="bf5ea-291">Runtimes / SDKs</span></span>                  |<span data-ttu-id="bf5ea-292">Debian 9</span><span class="sxs-lookup"><span data-stu-id="bf5ea-292">Debian 9</span></span>       |<span data-ttu-id="bf5ea-293">Debian 8</span><span class="sxs-lookup"><span data-stu-id="bf5ea-293">Debian 8</span></span>       |
|---------------------------------|---------------|---------------|
|<span data-ttu-id="bf5ea-294">.NET Core ランタイム 2.1.0-preview2</span><span class="sxs-lookup"><span data-stu-id="bf5ea-294">.NET Core Runtime 2.1.0-preview2</span></span> |[<span data-ttu-id="bf5ea-295">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-295">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview2)   |[<span data-ttu-id="bf5ea-296">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-296">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview2)   |
|<span data-ttu-id="bf5ea-297">.NET Core ランタイム 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="bf5ea-297">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="bf5ea-298">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-298">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview1)   |[<span data-ttu-id="bf5ea-299">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-299">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview1)   |
|<span data-ttu-id="bf5ea-300">.NET Core SDK 2.1.300-preview2</span><span class="sxs-lookup"><span data-stu-id="bf5ea-300">.NET Core SDK 2.1.300-preview2</span></span>   |[<span data-ttu-id="bf5ea-301">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-301">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview2)   |[<span data-ttu-id="bf5ea-302">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-302">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview2)   |
|<span data-ttu-id="bf5ea-303">.NET Core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="bf5ea-303">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="bf5ea-304">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-304">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview1)   |[<span data-ttu-id="bf5ea-305">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-305">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview1)   |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf5ea-306">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-306">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="bf5ea-307">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-307">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-308">Debian 9 または Debian 8 に .NET Core 1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-308">Install .NET Core 1.x on Debian 9 or Debian 8:</span></span>

* <span data-ttu-id="bf5ea-309">.NET Core ランタイム 1.1.7 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-309">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-310">.NET Core ランタイム 1.1.6 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-310">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-311">.NET Core ランタイム 1.0.10 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-311">.NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-312">.NET Core ランタイム 1.0.9 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-312">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-313">.NET Core SDK 1.1.8 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-313">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-314">.NET Core SDK 1.1.7 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-314">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-315">.NET Core SDK 1.0.4 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-315">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-316">.NET Core SDK 1.0.1 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-316">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a><span data-ttu-id="bf5ea-317">サポートされている Fedora のバージョン (64 ビット) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf5ea-317">Install .NET Core for supported Fedora versions (64 bit)</span></span>

<span data-ttu-id="bf5ea-318">サポートされている Fedora のバージョンに .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="bf5ea-318">To install .NET Core on supported Fedora versions:</span></span>

> [!NOTE]
> <span data-ttu-id="bf5ea-319">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-319">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf5ea-320">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-320">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="bf5ea-321">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-321">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-322">サポートされている Fedora のバージョン (64 ビット) に .NET Core 2.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-322">Install .NET Core 2.x on supported Fedora versions (64 bit):</span></span>

<span data-ttu-id="bf5ea-323">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-323">**.NET Core 2.0**</span></span>

|<span data-ttu-id="bf5ea-324">ランタイム/SDK</span><span class="sxs-lookup"><span data-stu-id="bf5ea-324">Runtimes / SDKs</span></span>          |<span data-ttu-id="bf5ea-325">Fedora 26 以降</span><span class="sxs-lookup"><span data-stu-id="bf5ea-325">Fedora 26 or later</span></span> |<span data-ttu-id="bf5ea-326">Fedora 25 以前</span><span class="sxs-lookup"><span data-stu-id="bf5ea-326">Fedora 25 or previous</span></span> |
|-------------------------|-------------------|----------------------|
|<span data-ttu-id="bf5ea-327">.NET Core ランタイム 2.0.6</span><span class="sxs-lookup"><span data-stu-id="bf5ea-327">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="bf5ea-328">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-328">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[<span data-ttu-id="bf5ea-329">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-329">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|<span data-ttu-id="bf5ea-330">.NET Core ランタイム 2.0.5</span><span class="sxs-lookup"><span data-stu-id="bf5ea-330">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="bf5ea-331">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-331">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[<span data-ttu-id="bf5ea-332">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-332">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|<span data-ttu-id="bf5ea-333">.NET Core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="bf5ea-333">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="bf5ea-334">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-334">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[<span data-ttu-id="bf5ea-335">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-335">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|<span data-ttu-id="bf5ea-336">.NET Core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="bf5ea-336">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="bf5ea-337">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-337">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[<span data-ttu-id="bf5ea-338">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-338">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

<span data-ttu-id="bf5ea-339">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-339">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="bf5ea-340">Visual Studio で .NET Core 2.1 を使用するには、[Visual Studio 2017 15.7 Preview 1 以降をインストールする](https://www.visualstudio.com/vs/preview)必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-340">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="bf5ea-341">ランタイム/SDK</span><span class="sxs-lookup"><span data-stu-id="bf5ea-341">Runtimes / SDKs</span></span>                  |<span data-ttu-id="bf5ea-342">Fedora 26 以降</span><span class="sxs-lookup"><span data-stu-id="bf5ea-342">Fedora 26 or later</span></span> |<span data-ttu-id="bf5ea-343">Fedora 25 以前</span><span class="sxs-lookup"><span data-stu-id="bf5ea-343">Fedora 25 or previous</span></span> |
|---------------------------------|-------------------|----------------------|
|<span data-ttu-id="bf5ea-344">.NET Core ランタイム 2.1.0-preview2</span><span class="sxs-lookup"><span data-stu-id="bf5ea-344">.NET Core Runtime 2.1.0-preview2</span></span> |[<span data-ttu-id="bf5ea-345">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-345">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview2)       |[<span data-ttu-id="bf5ea-346">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-346">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.1.0-preview2)           |
|<span data-ttu-id="bf5ea-347">.NET Core ランタイム 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="bf5ea-347">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="bf5ea-348">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-348">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview1)       |[<span data-ttu-id="bf5ea-349">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-349">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.1.0-preview1)           |
|<span data-ttu-id="bf5ea-350">.NET Core SDK 2.1.300-preview2</span><span class="sxs-lookup"><span data-stu-id="bf5ea-350">.NET Core SDK 2.1.300-preview2</span></span>   |[<span data-ttu-id="bf5ea-351">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-351">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview2)       |[<span data-ttu-id="bf5ea-352">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-352">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.300-preview2)           |
|<span data-ttu-id="bf5ea-353">.NET Core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="bf5ea-353">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="bf5ea-354">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-354">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview1)       |[<span data-ttu-id="bf5ea-355">インストール リンク</span><span class="sxs-lookup"><span data-stu-id="bf5ea-355">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.300-preview1)           |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf5ea-356">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-356">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="bf5ea-357">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-357">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-358">サポートされている Fedora のバージョン (64 ビット) に .NET Core 1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-358">Install .NET Core 1.x supported Fedora versions (64 bit):</span></span>

<span data-ttu-id="bf5ea-359">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-359">**Fedora 24**</span></span>

* <span data-ttu-id="bf5ea-360">.NET Core ランタイム 1.1.7 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-360">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-361">.NET Core ランタイム 1.1.6 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-361">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-362">.NET Core SDK 1.1.8 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-362">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-363">.NET Core SDK 1.1.7 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-363">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-364">.NET Core SDK 1.0.1 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-364">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span></span>

<span data-ttu-id="bf5ea-365">**Fedora 23**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-365">**Fedora 23**</span></span>

* <span data-ttu-id="bf5ea-366">.NET Core ランタイム 1.0.9 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-366">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-367">.NET Core SDK 1.0.4 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-367">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-368">.NET Core SDK 1.0.1 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-368">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a><span data-ttu-id="bf5ea-369">サポートされている CentOS および Oracle Linux のディストリビューション/バージョン (64 ビット) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf5ea-369">Install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit)</span></span>

<span data-ttu-id="bf5ea-370">サポートされている CentOS および Oracle Linux のディストリビューション/バージョン (64 ビット) 用の .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="bf5ea-370">To install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

> [!NOTE]
> <span data-ttu-id="bf5ea-371">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-371">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf5ea-372">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-372">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="bf5ea-373">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-373">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-374">サポートされている CentOS および Oracle Linux のディストリビューション/バージョン (64 ビット) に .NET Core 2.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-374">Install .NET Core 2.x on supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

<span data-ttu-id="bf5ea-375">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-375">**.NET Core 2.0**</span></span>

* <span data-ttu-id="bf5ea-376">.NET Core ランタイム 2.0.6 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-376">.NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)</span></span>
* <span data-ttu-id="bf5ea-377">.NET Core ランタイム 2.0.5 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-377">.NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)</span></span>
* <span data-ttu-id="bf5ea-378">.NET Core SDK 2.1.103 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-378">.NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)</span></span>
* <span data-ttu-id="bf5ea-379">.NET Core SDK 2.0.3 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-379">.NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)</span></span>
 
<span data-ttu-id="bf5ea-380">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-380">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="bf5ea-381">Visual Studio で .NET Core 2.1 を使用するには、[Visual Studio 2017 15.7 Preview 1 以降をインストールする](https://www.visualstudio.com/vs/preview/)必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-381">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview/).</span></span>

* <span data-ttu-id="bf5ea-382">.NET Core ランタイム 2.1.0-preview2 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview2)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-382">.NET Core Runtime 2.1.0-preview2 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview2)</span></span>
* <span data-ttu-id="bf5ea-383">.NET Core ランタイム 2.1.0-preview1 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-383">.NET Core Runtime 2.1.0-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)</span></span>
* <span data-ttu-id="bf5ea-384">.NET Core SDK 2.1.300-preview2 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview2)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-384">.NET Core SDK 2.1.300-preview2 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview2)</span></span>
* <span data-ttu-id="bf5ea-385">.NET Core SDK 2.1.300-preview1 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-385">.NET Core SDK 2.1.300-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf5ea-386">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-386">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="bf5ea-387">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-387">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-388">サポートされている CentOS および Oracle Linux のディストリビューション/バージョン (64 ビット) に .NET Core 1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-388">Install .NET Core 1.x on supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

* <span data-ttu-id="bf5ea-389">.NET Core ランタイム 1.1.7 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-389">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-390">.NET Core ランタイム 1.1.6 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-390">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-391">.NET Core ランタイム 1.0.10 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-391">.NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-392">.NET Core ランタイム 1.0.9 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-392">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-393">.NET Core SDK 1.1.8 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-393">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-394">.NET Core SDK 1.1.7 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-394">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-395">.NET Core SDK 1.0.4 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-395">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-396">.NET Core SDK 1.0.1 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-396">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a><span data-ttu-id="bf5ea-397">サポートされている SUSE Linux Enterprise Server および OpenSUSE のディストリビューション/バージョン (64 ビット) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf5ea-397">Install .NET Core for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit)</span></span>

<span data-ttu-id="bf5ea-398">サポートされている SUSE Linux Enterprise Server および OpenSUSE のディストリビューション/バージョン (64 ビット) 用の .NET Core 2.x をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="bf5ea-398">To install .NET Core 2.x for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf5ea-399">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-399">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="bf5ea-400">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-400">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-401">サポートされている SUSE Linux Enterprise Server および OpenSUSE のディストリビューション/バージョン (64 ビット) に .NET Core 2.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-401">Install .NET Core 2.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

<span data-ttu-id="bf5ea-402">**.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-402">**.NET Core 2.0**</span></span>

* <span data-ttu-id="bf5ea-403">.NET Core ランタイム 2.0.6 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-403">.NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)</span></span>
* <span data-ttu-id="bf5ea-404">.NET Core ランタイム 2.0.5 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-404">.NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)</span></span>
* <span data-ttu-id="bf5ea-405">.NET Core SDK 2.1.103 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-405">.NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)</span></span>
* <span data-ttu-id="bf5ea-406">.NET Core SDK 2.0.3 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-406">.NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)</span></span>
 
<span data-ttu-id="bf5ea-407">**.NET Core 2.1**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-407">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="bf5ea-408">Visual Studio で .NET Core 2.1 を使用するには、[Visual Studio 2017 15.7 Preview 1 以降をインストールする](https://www.visualstudio.com/vs/preview)必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-408">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

* <span data-ttu-id="bf5ea-409">.NET Core ランタイム 2.1.0-preview2 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview2)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-409">.NET Core Runtime 2.1.0-preview2 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview2)</span></span>
* <span data-ttu-id="bf5ea-410">.NET Core ランタイム 2.1.0-preview1  [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-410">.NET Core Runtime 2.1.0-preview1  [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)</span></span>
* <span data-ttu-id="bf5ea-411">.NET Core SDK 2.1.300-preview2 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview2)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-411">.NET Core SDK 2.1.300-preview2 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview2)</span></span>
* <span data-ttu-id="bf5ea-412">.NET Core SDK 2.1.300-preview1 [インストール リンク](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-412">.NET Core SDK 2.1.300-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf5ea-413">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf5ea-413">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="bf5ea-414">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-414">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf5ea-415">サポートされている SUSE Linux Enterprise Server および OpenSUSE のディストリビューション/バージョン (64 ビット) に .NET Core 1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-415">Install .NET Core 1.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

<span data-ttu-id="bf5ea-416">**SUSE Linux Enterprise Server 13.2**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-416">**SUSE Linux Enterprise Server 13.2**</span></span>

* <span data-ttu-id="bf5ea-417">.NET Core ランタイム 1.1.7 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-417">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-418">.NET Core ランタイム 1.1.6 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-418">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-419">.NET Core SDK 1.1.7 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-419">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)</span></span>

<span data-ttu-id="bf5ea-420">**openSUSE 24**</span><span class="sxs-lookup"><span data-stu-id="bf5ea-420">**openSUSE 24**</span></span>

* <span data-ttu-id="bf5ea-421">.NET Core SDK 1.0.4 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-421">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)</span></span>
* <span data-ttu-id="bf5ea-422">.NET Core SDK 1.0.1 [インストール リンク](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="bf5ea-422">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)</span></span>

---

> [!IMPORTANT]
> <span data-ttu-id="bf5ea-423">サポートされている Linux ディストリビューション/バージョンへの .NET Core のインストールに問題がある場合は、インストールしているディストリビューション/バージョンに関する以下のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf5ea-423">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>
> * [<span data-ttu-id="bf5ea-424">.NET Core 2.1 の既知の問題</span><span class="sxs-lookup"><span data-stu-id="bf5ea-424">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [<span data-ttu-id="bf5ea-425">.NET Core 2.0 の既知の問題</span><span class="sxs-lookup"><span data-stu-id="bf5ea-425">.NET Core 2.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [<span data-ttu-id="bf5ea-426">.NET Core 1.1 の既知の問題</span><span class="sxs-lookup"><span data-stu-id="bf5ea-426">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [<span data-ttu-id="bf5ea-427">.NET Core 1.0 の既知の問題</span><span class="sxs-lookup"><span data-stu-id="bf5ea-427">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)