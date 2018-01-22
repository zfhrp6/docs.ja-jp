---
title: "Linux における .NET Core の前提条件"
description: "Linux マシンで .NET Core アプリケーションを開発、展開、および実行するために必要なサポートされている Linux のバージョンと .NET Core の依存関係。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 12/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: d3c5dde443f848831f7c0585633339c35213357b
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="18652-104">Linux における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="18652-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="18652-105">この記事では、Linux で .NET Core アプリケーションを開発するために必要な依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="18652-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="18652-106">後述のサポートされている Linux ディストリビューション/バージョンと依存関係は、Linux で .NET Core アプリを開発する次の 2 つの方法に適用されます。</span><span class="sxs-lookup"><span data-stu-id="18652-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="18652-107">好みのエディターでのコマンドライン</span><span class="sxs-lookup"><span data-stu-id="18652-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="18652-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="18652-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="18652-109">サポートされている Linux バージョン</span><span class="sxs-lookup"><span data-stu-id="18652-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18652-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18652-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="18652-111">.NET Core 2.0 は、1 つのオペレーティング システムとして Linux を扱います。</span><span class="sxs-lookup"><span data-stu-id="18652-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="18652-112">サポートされている Linux ディストリビューション用に、1 つの Linux ビルド (チップ アーキテクチャあたり) があります。</span><span class="sxs-lookup"><span data-stu-id="18652-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="18652-113">.NET Core 2.x は、次の Linux 64 ビット (`x86_64` または `amd64`) ディストリビューション/バージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="18652-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="18652-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="18652-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="18652-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="18652-115">CentOS 7</span></span>
 * <span data-ttu-id="18652-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="18652-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="18652-117">Fedora 25、Fedora 26</span><span class="sxs-lookup"><span data-stu-id="18652-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="18652-118">Debian 8.7 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="18652-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="18652-119">Ubuntu 17.04、Ubuntu 16.04、Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="18652-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="18652-120">Linux Mint 18、Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="18652-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="18652-121">openSUSE 42.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="18652-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="18652-122">SUSE Enterprise Linux (SLES) 12 SP2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="18652-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="18652-123">.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18652-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18652-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18652-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="18652-125">.NET Core 1.x は、次の Linux 64 ビット (`x86_64` または `amd64`) ディストリビューション/バージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="18652-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="18652-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="18652-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="18652-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="18652-127">CentOS 7</span></span>
* <span data-ttu-id="18652-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="18652-128">Oracle Linux 7</span></span>
* <span data-ttu-id="18652-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="18652-129">Fedora 24</span></span>
* <span data-ttu-id="18652-130">Debian 8.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="18652-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="18652-131">Ubuntu 14.04、Ubuntu 16.04、Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="18652-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="18652-132">Ubuntu 16.10 は、.NET Core 1.1 の最新の修正プログラム リリースによってサポートされます</span><span class="sxs-lookup"><span data-stu-id="18652-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="18652-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="18652-133">Linux Mint 17</span></span>
* <span data-ttu-id="18652-134">openSUSE 42.1 以降のバージョン (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="18652-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="18652-135">.NET Core 1.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18652-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="18652-136">Linux ディストリビューションの依存関係</span><span class="sxs-lookup"><span data-stu-id="18652-136">Linux distribution dependencies</span></span>

<span data-ttu-id="18652-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="18652-137">The following are intended to be examples.</span></span> <span data-ttu-id="18652-138">選択した Linux ディストリビューションで、バージョンと名前が多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="18652-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="18652-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="18652-139">Ubuntu</span></span>

<span data-ttu-id="18652-140">Ubuntu ディストリビューションには、次のライブラリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="18652-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="18652-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="18652-141">libunwind8</span></span>
* <span data-ttu-id="18652-142">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="18652-142">liblttng-ust0</span></span>
* <span data-ttu-id="18652-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="18652-143">libcurl3</span></span>
* <span data-ttu-id="18652-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="18652-144">libssl1.0.0</span></span>
* <span data-ttu-id="18652-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="18652-145">libuuid1</span></span>
* <span data-ttu-id="18652-146">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="18652-146">libkrb5-3</span></span>
* <span data-ttu-id="18652-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="18652-147">zlib1g</span></span>
* <span data-ttu-id="18652-148">libicu52 (14.X 用)</span><span class="sxs-lookup"><span data-stu-id="18652-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="18652-149">libicu55 (16.X 用)</span><span class="sxs-lookup"><span data-stu-id="18652-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="18652-150">libicu57 (17.X 用)</span><span class="sxs-lookup"><span data-stu-id="18652-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="18652-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="18652-151">CentOS</span></span>

<span data-ttu-id="18652-152">CentOS ディストリビューションには、次のライブラリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="18652-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="18652-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="18652-153">libunwind</span></span>
* <span data-ttu-id="18652-154">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="18652-154">lttng-ust</span></span>
* <span data-ttu-id="18652-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="18652-155">libcurl</span></span>
* <span data-ttu-id="18652-156">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="18652-156">openssl-libs</span></span>
* <span data-ttu-id="18652-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="18652-157">libuuid</span></span>
* <span data-ttu-id="18652-158">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="18652-158">krb5-libs</span></span>
* <span data-ttu-id="18652-159">libicu</span><span class="sxs-lookup"><span data-stu-id="18652-159">libicu</span></span>
* <span data-ttu-id="18652-160">zlib</span><span class="sxs-lookup"><span data-stu-id="18652-160">zlib</span></span>

<span data-ttu-id="18652-161">依存関係の詳細については、「[Self-contained Linux applications (自己完結型 Linux アプリケーション)](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="18652-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="18652-162">ネイティブ インストーラーを使用した .NET Core の依存関係のインストール</span><span class="sxs-lookup"><span data-stu-id="18652-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="18652-163">.NET Core ネイティブ インストーラーは、サポートされている Linux ディストリビューション/バージョンに利用できます。</span><span class="sxs-lookup"><span data-stu-id="18652-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="18652-164">このネイティブ インストーラーは、サーバーへの admin (sudo) アクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="18652-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="18652-165">ネイティブ インストーラーを使用することの利点は、.NET Core ネイティブの依存関係がすべてインストールされることです。</span><span class="sxs-lookup"><span data-stu-id="18652-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="18652-166">また、ネイティブ インストーラーでは、.NET Core SDK もシステム全体にインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="18652-167">Linux では、2 つのインストーラー パッケージから選択できます。</span><span class="sxs-lookup"><span data-stu-id="18652-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="18652-168">フィードベースのパッケージ マネージャー (Ubuntu では apt-get、CentOS/RHEL では yum など) を使用する</span><span class="sxs-lookup"><span data-stu-id="18652-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="18652-169">パッケージ自体 (DEB または RPM) を使用する</span><span class="sxs-lookup"><span data-stu-id="18652-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="18652-170">.NET Core インストーラー スクリプトを使用したスクリプトのインストール</span><span class="sxs-lookup"><span data-stu-id="18652-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="18652-171">`dotnet-install` スクリプトは、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="18652-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="18652-172">次の場所からスクリプトをダウンロードできます: https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="18652-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="18652-173">インストーラーの bash スクリプトは、自動化シナリオと管理者以外のインストールで使用されます。</span><span class="sxs-lookup"><span data-stu-id="18652-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="18652-174">このスクリプトは、PowerShell のスイッチも読み取るので、Linux/OS X システムのスクリプトで使うことができます。</span><span class="sxs-lookup"><span data-stu-id="18652-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18652-175">スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="18652-176">Red Hat Enterprise Linux (RHEL) 7 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="18652-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="18652-177">RHEL 7 に .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="18652-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="18652-178">RHEL 7 サブスクリプションで利用できる Red Hat .NET チャネルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="18652-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="18652-179">Red Hat Enterprise 7 Server の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="18652-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="18652-180">Red Hat Enterprise 7 Workstation の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="18652-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="18652-181">Red Hat Enterprise 7 HPC Compute Node の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="18652-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="18652-182">scl ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="18652-183">.NET Core をインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18652-184">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18652-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="18652-185">.NET Core 2.0 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="18652-186">環境に対して .NET Core 2.0 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="18652-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18652-187">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18652-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="18652-188">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="18652-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="18652-189">.NET Core 1.1 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="18652-190">環境に対して .NET Core 1.1 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="18652-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="18652-191">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="18652-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="18652-192">.NET Core 1.0 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="18652-193">環境に対して .NET Core 1.0 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="18652-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="18652-194">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="18652-195">Red Hat .NET チャネル アクセスの登録に関するヘルプについては、Red Hat の「[Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)」 (.NET Core 1.1 ファースト ステップ ガイドの第 1 章) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18652-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="18652-196">.NET Core for Ubuntu 14.04、Ubuntu 16.04、Ubuntu 16.10 および Linux Mint 17、Linux Mint 18 (64 ビット)</span><span class="sxs-lookup"><span data-stu-id="18652-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="18652-197">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="18652-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18652-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18652-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="18652-199">信頼済みとして Microsoft プロダクト キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="18652-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="18652-200">必要なバージョンのホスト パッケージ フィードを設定します。</span><span class="sxs-lookup"><span data-stu-id="18652-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="18652-201">**Ubuntu 17.10**</span><span class="sxs-lookup"><span data-stu-id="18652-201">**Ubuntu 17.10**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   <span data-ttu-id="18652-202">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="18652-202">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="18652-203">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="18652-203">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="18652-204">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="18652-204">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="18652-205">.NET Core をインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-205">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.1.3
   ```

4. <span data-ttu-id="18652-206">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-206">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18652-207">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18652-207">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="18652-208">必要なバージョンのホスト パッケージ フィードを設定します。</span><span class="sxs-lookup"><span data-stu-id="18652-208">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="18652-209">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="18652-209">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="18652-210">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="18652-210">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="18652-211">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="18652-211">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="18652-212">Ubuntu または Linux Mint に、.NET Core 1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-212">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="18652-213">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-213">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="18652-214">Debian 8 または Debian 9 (64 ビット) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="18652-214">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="18652-215">Debian 8 または Debian 9 (64 ビット) 用の .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="18652-215">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="18652-216">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="18652-216">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="18652-217">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="18652-217">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18652-218">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18652-218">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="18652-219">システムのコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-219">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="18652-220">信頼済みの Microsoft プロダクト キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="18652-220">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="18652-221">Microsoft 製品フィードを登録します。</span><span class="sxs-lookup"><span data-stu-id="18652-221">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="18652-222">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="18652-222">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="18652-223">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="18652-223">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="18652-224">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-224">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="18652-225">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-225">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="18652-226">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-226">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18652-227">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18652-227">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="18652-228">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="18652-228">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="18652-229">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="18652-229">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="18652-230">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="18652-230">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="18652-231">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-231">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="18652-232">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-232">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="18652-233">.NET Core for Fedora 24、Fedora 25、または Fedora 26 (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="18652-233">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="18652-234">.NET Core 2.x を Fedora 26 または Fedora 25 にインストールするか、.NET Core 1.x を Fedora 24 にインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="18652-234">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="18652-235">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="18652-235">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="18652-236">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="18652-236">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18652-237">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18652-237">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="18652-238">**Fedora 26 または Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="18652-238">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="18652-239">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="18652-239">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="18652-240">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-240">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="18652-241">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-241">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="18652-242">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-242">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18652-243">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18652-243">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="18652-244">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="18652-244">**Fedora 24**</span></span>

2. <span data-ttu-id="18652-245">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="18652-245">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="18652-246">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="18652-246">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="18652-247">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="18652-247">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="18652-248">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-248">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="18652-249">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-249">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="18652-250">CentOS 7.1 (64 bit) および Oracle Linux 7.1 (64 bit) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="18652-250">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="18652-251">CentOS 7.1 (64 ビット) および Oracle Linux 7.1 (64 ビット) 用の .NET Core をインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="18652-251">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="18652-252">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="18652-252">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="18652-253">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="18652-253">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18652-254">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18652-254">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="18652-255">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="18652-255">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="18652-256">Microsoft 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-256">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="18652-257">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-257">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="18652-258">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-258">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18652-259">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18652-259">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="18652-260">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="18652-260">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="18652-261">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="18652-261">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="18652-262">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="18652-262">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="18652-263">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-263">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="18652-264">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-264">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="18652-265">.NET Core for SUSE Linux Enterprise Server (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="18652-265">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="18652-266">SUSE Linux Enterprise Server (SLES) 12 SP2 (64 ビット) 用の .NET Core 2.x をインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="18652-266">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="18652-267">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="18652-267">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="18652-268">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-268">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="18652-269">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-269">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="18652-270">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-270">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="18652-271">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-271">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="18652-272">.NET Core for openSUSE (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="18652-272">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="18652-273">openSUSE 用の .NET Core 2.x または openSUSE (64 ビット) 用の .NET Core 1.x をインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="18652-273">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="18652-274">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="18652-274">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="18652-275">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="18652-275">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="18652-276">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="18652-276">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="18652-277">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="18652-277">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="18652-278">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-278">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="18652-279">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="18652-279">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="18652-280">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-280">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="18652-281">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="18652-281">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="18652-282">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="18652-282">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="18652-283">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="18652-283">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="18652-284">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="18652-284">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="18652-285">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="18652-285">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="18652-286">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="18652-286">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="18652-287">サポートされている Linux ディストリビューション/バージョンの .NET Core 2.x で問題が発生している場合は、インストールしたディストリビューション/バージョンに対する [2.0 の既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18652-287">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="18652-288">サポートされている Linux ディストリビューション/バージョンの .NET Core 1.x で問題が発生している場合は、インストールしたディストリビューション/バージョンに対する [1.0.0 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)と [1.0.1 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18652-288">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
