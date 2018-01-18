---
title: "Linux における .NET Core の前提条件"
description: "Linux マシンで .NET Core アプリケーションを開発、展開、および実行するために必要なサポートされている Linux のバージョンと .NET Core の依存関係。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: ec08d9fa3ad672400b61c269da0c6a70ed9ef2f5
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="bf19f-104">Linux における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="bf19f-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="bf19f-105">この記事では、Linux で .NET Core アプリケーションを開発するために必要な依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="bf19f-106">後述のサポートされている Linux ディストリビューション/バージョンと依存関係は、Linux で .NET Core アプリを開発する次の 2 つの方法に適用されます。</span><span class="sxs-lookup"><span data-stu-id="bf19f-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="bf19f-107">好みのエディターでのコマンドライン</span><span class="sxs-lookup"><span data-stu-id="bf19f-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="bf19f-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bf19f-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="bf19f-109">サポートされている Linux バージョン</span><span class="sxs-lookup"><span data-stu-id="bf19f-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf19f-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bf19f-111">.NET Core 2.0 は、1 つのオペレーティング システムとして Linux を扱います。</span><span class="sxs-lookup"><span data-stu-id="bf19f-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="bf19f-112">サポートされている Linux ディストリビューション用に、1 つの Linux ビルド (チップ アーキテクチャあたり) があります。</span><span class="sxs-lookup"><span data-stu-id="bf19f-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="bf19f-113">.NET Core 2.x は、次の Linux 64 ビット (`x86_64` または `amd64`) ディストリビューション/バージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bf19f-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="bf19f-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="bf19f-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="bf19f-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bf19f-115">CentOS 7</span></span>
 * <span data-ttu-id="bf19f-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="bf19f-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="bf19f-117">Fedora 25、Fedora 26</span><span class="sxs-lookup"><span data-stu-id="bf19f-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="bf19f-118">Debian 8.7 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bf19f-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="bf19f-119">Ubuntu 17.04、Ubuntu 16.04、Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="bf19f-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="bf19f-120">Linux Mint 18、Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="bf19f-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="bf19f-121">openSUSE 42.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bf19f-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="bf19f-122">SUSE Enterprise Linux (SLES) 12 SP2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bf19f-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="bf19f-123">.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf19f-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf19f-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bf19f-125">.NET Core 1.x は、次の Linux 64 ビット (`x86_64` または `amd64`) ディストリビューション/バージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bf19f-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="bf19f-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="bf19f-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="bf19f-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="bf19f-127">CentOS 7</span></span>
* <span data-ttu-id="bf19f-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="bf19f-128">Oracle Linux 7</span></span>
* <span data-ttu-id="bf19f-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="bf19f-129">Fedora 24</span></span>
* <span data-ttu-id="bf19f-130">Debian 8.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="bf19f-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="bf19f-131">Ubuntu 14.04、Ubuntu 16.04、Ubuntu 16.10\\*</span><span class="sxs-lookup"><span data-stu-id="bf19f-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\\*</span></span>
 * <span data-ttu-id="bf19f-132">Ubuntu 16.10 は、.NET Core 1.1 の最新の修正プログラム リリースによってサポートされます</span><span class="sxs-lookup"><span data-stu-id="bf19f-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="bf19f-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="bf19f-133">Linux Mint 17</span></span>
* <span data-ttu-id="bf19f-134">openSUSE 42.1 以降のバージョン (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="bf19f-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="bf19f-135">.NET Core 1.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf19f-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="bf19f-136">Linux ディストリビューションの依存関係</span><span class="sxs-lookup"><span data-stu-id="bf19f-136">Linux distribution dependencies</span></span>

<span data-ttu-id="bf19f-137">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-137">The following are intended to be examples.</span></span> <span data-ttu-id="bf19f-138">選択した Linux ディストリビューションで、バージョンと名前が多少異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf19f-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="bf19f-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bf19f-139">Ubuntu</span></span>

<span data-ttu-id="bf19f-140">Ubuntu ディストリビューションには、次のライブラリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf19f-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="bf19f-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="bf19f-141">libunwind8</span></span>
* <span data-ttu-id="bf19f-142">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="bf19f-142">liblttng-ust0</span></span>
* <span data-ttu-id="bf19f-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="bf19f-143">libcurl3</span></span>
* <span data-ttu-id="bf19f-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="bf19f-144">libssl1.0.0</span></span>
* <span data-ttu-id="bf19f-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="bf19f-145">libuuid1</span></span>
* <span data-ttu-id="bf19f-146">libkrb5</span><span class="sxs-lookup"><span data-stu-id="bf19f-146">libkrb5</span></span>
* <span data-ttu-id="bf19f-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="bf19f-147">zlib1g</span></span>
* <span data-ttu-id="bf19f-148">libicu52 (14.X 用)</span><span class="sxs-lookup"><span data-stu-id="bf19f-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="bf19f-149">libicu55 (16.X 用)</span><span class="sxs-lookup"><span data-stu-id="bf19f-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="bf19f-150">libicu57 (17.X 用)</span><span class="sxs-lookup"><span data-stu-id="bf19f-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="bf19f-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="bf19f-151">CentOS</span></span>

<span data-ttu-id="bf19f-152">CentOS ディストリビューションには、次のライブラリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf19f-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="bf19f-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="bf19f-153">libunwind</span></span>
* <span data-ttu-id="bf19f-154">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="bf19f-154">lttng-ust</span></span>
* <span data-ttu-id="bf19f-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="bf19f-155">libcurl</span></span>
* <span data-ttu-id="bf19f-156">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="bf19f-156">openssl-libs</span></span>
* <span data-ttu-id="bf19f-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="bf19f-157">libuuid</span></span>
* <span data-ttu-id="bf19f-158">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="bf19f-158">krb5-libs</span></span>
* <span data-ttu-id="bf19f-159">libicu</span><span class="sxs-lookup"><span data-stu-id="bf19f-159">libicu</span></span>
* <span data-ttu-id="bf19f-160">zlib</span><span class="sxs-lookup"><span data-stu-id="bf19f-160">zlib</span></span>

<span data-ttu-id="bf19f-161">依存関係の詳細については、「[Self-contained Linux applications (自己完結型 Linux アプリケーション)](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf19f-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="bf19f-162">ネイティブ インストーラーを使用した .NET Core の依存関係のインストール</span><span class="sxs-lookup"><span data-stu-id="bf19f-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="bf19f-163">.NET Core ネイティブ インストーラーは、サポートされている Linux ディストリビューション/バージョンに利用できます。</span><span class="sxs-lookup"><span data-stu-id="bf19f-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="bf19f-164">このネイティブ インストーラーは、サーバーへの admin (sudo) アクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="bf19f-165">ネイティブ インストーラーを使用することの利点は、.NET Core ネイティブの依存関係がすべてインストールされることです。</span><span class="sxs-lookup"><span data-stu-id="bf19f-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="bf19f-166">また、ネイティブ インストーラーでは、.NET Core SDK もシステム全体にインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="bf19f-167">Linux では、2 つのインストーラー パッケージから選択できます。</span><span class="sxs-lookup"><span data-stu-id="bf19f-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="bf19f-168">フィードベースのパッケージ マネージャー (Ubuntu では apt-get、CentOS/RHEL では yum など) を使用する</span><span class="sxs-lookup"><span data-stu-id="bf19f-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="bf19f-169">パッケージ自体 (DEB または RPM) を使用する</span><span class="sxs-lookup"><span data-stu-id="bf19f-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="bf19f-170">.NET Core インストーラー スクリプトを使用したスクリプトのインストール</span><span class="sxs-lookup"><span data-stu-id="bf19f-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="bf19f-171">`dotnet-install` スクリプトは、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf19f-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="bf19f-172">次の場所からスクリプトをダウンロードできます: https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="bf19f-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="bf19f-173">インストーラーの bash スクリプトは、自動化シナリオと管理者以外のインストールで使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf19f-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="bf19f-174">このスクリプトは、PowerShell のスイッチも読み取るので、Linux/OS X システムのスクリプトで使うことができます。</span><span class="sxs-lookup"><span data-stu-id="bf19f-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf19f-175">スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="bf19f-176">Red Hat Enterprise Linux (RHEL) 7 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf19f-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="bf19f-177">RHEL 7 に .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="bf19f-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="bf19f-178">RHEL 7 サブスクリプションで利用できる Red Hat .NET チャネルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="bf19f-179">Red Hat Enterprise 7 Server の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="bf19f-180">Red Hat Enterprise 7 Workstation の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="bf19f-181">Red Hat Enterprise 7 HPC Compute Node の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="bf19f-182">scl ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="bf19f-183">.NET Core をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf19f-184">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bf19f-185">.NET Core 2.0 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="bf19f-186">環境に対して .NET Core 2.0 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf19f-187">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bf19f-188">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="bf19f-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="bf19f-189">.NET Core 1.1 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="bf19f-190">環境に対して .NET Core 1.1 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="bf19f-191">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="bf19f-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="bf19f-192">.NET Core 1.0 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="bf19f-193">環境に対して .NET Core 1.0 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="bf19f-194">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="bf19f-195">Red Hat .NET チャネル アクセスの登録に関するヘルプについては、Red Hat の「[Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)」 (.NET Core 1.1 ファースト ステップ ガイドの第 1 章) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf19f-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="bf19f-196">.NET Core for Ubuntu 14.04、Ubuntu 16.04、Ubuntu 16.10 および Linux Mint 17、Linux Mint 18 (64 ビット)</span><span class="sxs-lookup"><span data-stu-id="bf19f-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="bf19f-197">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf19f-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="bf19f-199">信頼済みとして Microsoft プロダクト キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="bf19f-200">必要なバージョンのホスト パッケージ フィードを設定します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="bf19f-201">**Ubuntu 17.10**</span><span class="sxs-lookup"><span data-stu-id="bf19f-201">**Ubuntu 17.10**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   <span data-ttu-id="bf19f-202">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="bf19f-202">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="bf19f-203">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="bf19f-203">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="bf19f-204">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="bf19f-204">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="bf19f-205">.NET Core をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-205">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.1.3
   ```

4. <span data-ttu-id="bf19f-206">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-206">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf19f-207">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-207">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="bf19f-208">必要なバージョンのホスト パッケージ フィードを設定します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-208">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="bf19f-209">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="bf19f-209">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="bf19f-210">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="bf19f-210">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="bf19f-211">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="bf19f-211">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="bf19f-212">Ubuntu または Linux Mint に、.NET Core 1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-212">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="bf19f-213">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-213">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="bf19f-214">Debian 8 または Debian 9 (64 ビット) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf19f-214">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="bf19f-215">Debian 8 または Debian 9 (64 ビット) 用の .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="bf19f-215">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="bf19f-216">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-216">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="bf19f-217">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf19f-217">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf19f-218">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-218">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="bf19f-219">システムのコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-219">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="bf19f-220">信頼済みの Microsoft プロダクト キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-220">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="bf19f-221">Microsoft 製品フィードを登録します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-221">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="bf19f-222">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="bf19f-222">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="bf19f-223">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="bf19f-223">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="bf19f-224">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-224">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="bf19f-225">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-225">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="bf19f-226">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-226">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf19f-227">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-227">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="bf19f-228">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-228">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="bf19f-229">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-229">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="bf19f-230">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-230">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="bf19f-231">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-231">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="bf19f-232">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-232">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="bf19f-233">.NET Core for Fedora 24、Fedora 25、または Fedora 26 (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf19f-233">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="bf19f-234">.NET Core 2.x を Fedora 26 または Fedora 25 にインストールするか、.NET Core 1.x を Fedora 24 にインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-234">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="bf19f-235">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-235">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="bf19f-236">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf19f-236">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf19f-237">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-237">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bf19f-238">**Fedora 26 または Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="bf19f-238">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="bf19f-239">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-239">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="bf19f-240">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-240">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="bf19f-241">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-241">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="bf19f-242">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-242">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf19f-243">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-243">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bf19f-244">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="bf19f-244">**Fedora 24**</span></span>

2. <span data-ttu-id="bf19f-245">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-245">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="bf19f-246">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-246">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="bf19f-247">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-247">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="bf19f-248">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-248">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="bf19f-249">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-249">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="bf19f-250">CentOS 7.1 (64 bit) および Oracle Linux 7.1 (64 bit) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf19f-250">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="bf19f-251">CentOS 7.1 (64 ビット) および Oracle Linux 7.1 (64 ビット) 用の .NET Core をインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-251">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="bf19f-252">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-252">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="bf19f-253">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf19f-253">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf19f-254">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-254">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="bf19f-255">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-255">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="bf19f-256">Microsoft 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-256">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="bf19f-257">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-257">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="bf19f-258">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-258">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf19f-259">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-259">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="bf19f-260">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-260">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="bf19f-261">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-261">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="bf19f-262">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-262">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="bf19f-263">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-263">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="bf19f-264">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-264">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="bf19f-265">.NET Core for SUSE Linux Enterprise Server (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf19f-265">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="bf19f-266">SUSE Linux Enterprise Server (SLES) 12 SP2 (64 ビット) 用の .NET Core 2.x をインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-266">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="bf19f-267">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-267">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="bf19f-268">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-268">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="bf19f-269">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-269">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="bf19f-270">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-270">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="bf19f-271">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-271">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="bf19f-272">.NET Core for openSUSE (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="bf19f-272">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="bf19f-273">openSUSE 用の .NET Core 2.x または openSUSE (64 ビット) 用の .NET Core 1.x をインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-273">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="bf19f-274">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-274">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="bf19f-275">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bf19f-275">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bf19f-276">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-276">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="bf19f-277">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-277">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="bf19f-278">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-278">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="bf19f-279">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-279">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="bf19f-280">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-280">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bf19f-281">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="bf19f-281">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="bf19f-282">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-282">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="bf19f-283">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bf19f-283">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="bf19f-284">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-284">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="bf19f-285">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-285">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="bf19f-286">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf19f-286">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="bf19f-287">サポートされている Linux ディストリビューション/バージョンの .NET Core 2.x で問題が発生している場合は、インストールしたディストリビューション/バージョンに対する [2.0 の既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf19f-287">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="bf19f-288">サポートされている Linux ディストリビューション/バージョンの .NET Core 1.x で問題が発生している場合は、インストールしたディストリビューション/バージョンに対する [1.0.0 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)と [1.0.1 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf19f-288">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
