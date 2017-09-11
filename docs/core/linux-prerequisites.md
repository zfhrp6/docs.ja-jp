---
title: "Linux における .NET Core の前提条件"
description: "Linux マシンで .NET Core アプリケーションを開発、展開、および実行するために必要なサポートされている Linux のバージョンと .NET Core の依存関係。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 7bbb8405f39a52d2798fd1dbc78f3116cb3bedbb
ms.openlocfilehash: 9864ffa31caa007cb649a9e6e8913863d9cb2c35
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---

# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="c3fad-104">Linux における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="c3fad-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="c3fad-105">この記事では、Linux で .NET Core アプリケーションを開発するために必要な依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="c3fad-106">後述のサポートされている Linux ディストリビューション/バージョンと依存関係は、Linux で .NET Core アプリを開発する次の 2 つの方法に適用されます。</span><span class="sxs-lookup"><span data-stu-id="c3fad-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="c3fad-107">好みのエディターでのコマンドライン</span><span class="sxs-lookup"><span data-stu-id="c3fad-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="c3fad-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c3fad-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="c3fad-109">サポートされている Linux バージョン</span><span class="sxs-lookup"><span data-stu-id="c3fad-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c3fad-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c3fad-111">.NET Core 2.0 は、1 つのオペレーティング システムとして Linux を扱います。</span><span class="sxs-lookup"><span data-stu-id="c3fad-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="c3fad-112">サポートされている Linux ディストリビューション用に、1 つの Linux ビルド (チップ アーキテクチャあたり) があります。</span><span class="sxs-lookup"><span data-stu-id="c3fad-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="c3fad-113">NET Core 2.x は、次の Linux x64 ディストリビューション/バージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c3fad-113">NET Core 2.x is supported on the following Linux x64 distributions/versions:</span></span>

 * <span data-ttu-id="c3fad-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="c3fad-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="c3fad-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c3fad-115">CentOS 7</span></span>
 * <span data-ttu-id="c3fad-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c3fad-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="c3fad-117">Fedora 25、Fedora 26</span><span class="sxs-lookup"><span data-stu-id="c3fad-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="c3fad-118">Debian 8.7 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="c3fad-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="c3fad-119">Ubuntu 17.04、Ubuntu 16.04、Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c3fad-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="c3fad-120">Linux Mint 18、Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="c3fad-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="c3fad-121">openSUSE 42.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="c3fad-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="c3fad-122">SUSE Enterprise Linux (SLES) 12 SP2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="c3fad-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="c3fad-123">.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3fad-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3fad-124">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c3fad-125">.NET Core 1.x は、次の Linux x64 ディストリビューション/バージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c3fad-125">.NET Core 1.x is supported on the following Linux x64 distributions/versions:</span></span>

* <span data-ttu-id="c3fad-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="c3fad-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="c3fad-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c3fad-127">CentOS 7</span></span>
* <span data-ttu-id="c3fad-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c3fad-128">Oracle Linux 7</span></span>
* <span data-ttu-id="c3fad-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="c3fad-129">Fedora 24</span></span>
* <span data-ttu-id="c3fad-130">Debian 8.2 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="c3fad-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="c3fad-131">Ubuntu 14.04、Ubuntu 16.04、Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="c3fad-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="c3fad-132">Ubuntu 16.10 は、.NET Core 1.1 の最新の修正プログラム リリースによってサポートされます</span><span class="sxs-lookup"><span data-stu-id="c3fad-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="c3fad-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="c3fad-133">Linux Mint 17</span></span>
* <span data-ttu-id="c3fad-134">openSUSE 42.1 以降のバージョン (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="c3fad-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="c3fad-135">.NET Core 1.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3fad-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="c3fad-136">Linux ディストリビューションの依存関係</span><span class="sxs-lookup"><span data-stu-id="c3fad-136">Linux distribution dependencies</span></span>

### <a name="ubuntu"></a><span data-ttu-id="c3fad-137">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c3fad-137">Ubuntu</span></span>

<span data-ttu-id="c3fad-138">Ubuntu ディストリビューションには、次のライブラリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3fad-138">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="c3fad-139">libunwind8</span><span class="sxs-lookup"><span data-stu-id="c3fad-139">libunwind8</span></span>
* <span data-ttu-id="c3fad-140">libunwind8-dev</span><span class="sxs-lookup"><span data-stu-id="c3fad-140">libunwind8-dev</span></span>
* <span data-ttu-id="c3fad-141">gettext</span><span class="sxs-lookup"><span data-stu-id="c3fad-141">gettext</span></span>
* <span data-ttu-id="c3fad-142">libicu-dev</span><span class="sxs-lookup"><span data-stu-id="c3fad-142">libicu-dev</span></span>
* <span data-ttu-id="c3fad-143">liblttng-ust-dev</span><span class="sxs-lookup"><span data-stu-id="c3fad-143">liblttng-ust-dev</span></span>
* <span data-ttu-id="c3fad-144">libcurl4-openssl-dev</span><span class="sxs-lookup"><span data-stu-id="c3fad-144">libcurl4-openssl-dev</span></span>
* <span data-ttu-id="c3fad-145">libssl-dev</span><span class="sxs-lookup"><span data-stu-id="c3fad-145">libssl-dev</span></span>
* <span data-ttu-id="c3fad-146">uuid-dev</span><span class="sxs-lookup"><span data-stu-id="c3fad-146">uuid-dev</span></span>
* <span data-ttu-id="c3fad-147">unzip</span><span class="sxs-lookup"><span data-stu-id="c3fad-147">unzip</span></span>

### <a name="centos"></a><span data-ttu-id="c3fad-148">CentOS</span><span class="sxs-lookup"><span data-stu-id="c3fad-148">CentOS</span></span>

<span data-ttu-id="c3fad-149">CentOS ディストリビューションには、次のライブラリがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3fad-149">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="c3fad-150">deltarpm</span><span class="sxs-lookup"><span data-stu-id="c3fad-150">deltarpm</span></span>
* <span data-ttu-id="c3fad-151">epel-release</span><span class="sxs-lookup"><span data-stu-id="c3fad-151">epel-release</span></span>
* <span data-ttu-id="c3fad-152">unzip</span><span class="sxs-lookup"><span data-stu-id="c3fad-152">unzip</span></span>
* <span data-ttu-id="c3fad-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="c3fad-153">libunwind</span></span>
* <span data-ttu-id="c3fad-154">gettext</span><span class="sxs-lookup"><span data-stu-id="c3fad-154">gettext</span></span>
* <span data-ttu-id="c3fad-155">libcurl-devel</span><span class="sxs-lookup"><span data-stu-id="c3fad-155">libcurl-devel</span></span>
* <span data-ttu-id="c3fad-156">openssl-devel</span><span class="sxs-lookup"><span data-stu-id="c3fad-156">openssl-devel</span></span>
* <span data-ttu-id="c3fad-157">zlib</span><span class="sxs-lookup"><span data-stu-id="c3fad-157">zlib</span></span>
* <span data-ttu-id="c3fad-158">libicu-devel</span><span class="sxs-lookup"><span data-stu-id="c3fad-158">libicu-devel</span></span>

<span data-ttu-id="c3fad-159">依存関係の詳細については、「[Self-contained Linux applications (自己完結型 Linux アプリケーション)](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c3fad-159">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="c3fad-160">ネイティブ インストーラーを使用した .NET Core の依存関係のインストール</span><span class="sxs-lookup"><span data-stu-id="c3fad-160">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="c3fad-161">.NET Core ネイティブ インストーラーは、サポートされている Linux ディストリビューション/バージョンに利用できます。</span><span class="sxs-lookup"><span data-stu-id="c3fad-161">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="c3fad-162">このネイティブ インストーラーは、サーバーへの admin (sudo) アクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-162">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="c3fad-163">ネイティブ インストーラーを使用することの利点は、.NET Core ネイティブの依存関係がすべてインストールされることです。</span><span class="sxs-lookup"><span data-stu-id="c3fad-163">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="c3fad-164">また、ネイティブ インストーラーでは、.NET Core SDK もシステム全体にインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-164">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="c3fad-165">Linux では、2 つのインストーラー パッケージから選択できます。</span><span class="sxs-lookup"><span data-stu-id="c3fad-165">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="c3fad-166">フィードベースのパッケージ マネージャー (Ubuntu では apt-get、CentOS/RHEL では yum など) を使用する</span><span class="sxs-lookup"><span data-stu-id="c3fad-166">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="c3fad-167">パッケージ自体 (DEB または RPM) を使用する</span><span class="sxs-lookup"><span data-stu-id="c3fad-167">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="c3fad-168">.NET Core インストーラー スクリプトを使用したスクリプトのインストール</span><span class="sxs-lookup"><span data-stu-id="c3fad-168">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="c3fad-169">`dotnet-install` スクリプトは、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3fad-169">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="c3fad-170">スクリプトは [CLI GitHub リポジトリ](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="c3fad-170">You can download the scripts from the [CLI GitHub repo](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain).</span></span>

<span data-ttu-id="c3fad-171">インストーラーの bash スクリプトは、自動化シナリオと管理者以外のインストールで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3fad-171">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="c3fad-172">このスクリプトは、PowerShell のスイッチも読み取るので、Linux/OS X システムのスクリプトで使うことができます。</span><span class="sxs-lookup"><span data-stu-id="c3fad-172">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3fad-173">スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-173">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c3fad-174">Red Hat Enterprise Linux (RHEL) 7 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="c3fad-174">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c3fad-175">RHEL 7 に .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="c3fad-175">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="c3fad-176">RHEL 7 サブスクリプションで利用できる Red Hat .NET チャネルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-176">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="c3fad-177">Red Hat Enterprise 7 Server の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-177">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="c3fad-178">Red Hat Enterprise 7 Workstation の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-178">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="c3fad-179">Red Hat Enterprise 7 HPC Compute Node の場合は、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-179">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="c3fad-180">scl ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-180">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="c3fad-181">.NET Core をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-181">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c3fad-182">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-182">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c3fad-183">.NET Core 2.0 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-183">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="c3fad-184">環境に対して .NET Core 2.0 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-184">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3fad-185">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-185">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c3fad-186">**.NET Core 1.1**</span><span class="sxs-lookup"><span data-stu-id="c3fad-186">**.NET Core 1.1**</span></span>

<span data-ttu-id="c3fad-187">.NET Core 1.1 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-187">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="c3fad-188">環境に対して .NET Core 1.1 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-188">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="c3fad-189">**.NET Core 1.0**</span><span class="sxs-lookup"><span data-stu-id="c3fad-189">**.NET Core 1.0**</span></span>

<span data-ttu-id="c3fad-190">.NET Core 1.0 SDK とランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-190">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="c3fad-191">環境に対して .NET Core 1.0 SDK/ランタイムを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-191">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="c3fad-192">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-192">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="c3fad-193">Red Hat .NET チャネル アクセスの登録に関するヘルプについては、Red Hat の「[Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)」 (.NET Core 1.1 ファースト ステップ ガイドの第 1 章) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3fad-193">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="c3fad-194">.NET Core for Ubuntu 14.04、Ubuntu 16.04、Ubuntu 16.10 および Linux Mint 17、Linux Mint 18 (64 ビット)</span><span class="sxs-lookup"><span data-stu-id="c3fad-194">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="c3fad-195">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-195">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c3fad-196">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-196">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="c3fad-197">信頼済みとして Microsoft プロダクト キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-197">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="c3fad-198">必要なバージョンのホスト パッケージ フィードを設定します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-198">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="c3fad-199">**Ubuntu 17.04**</span><span class="sxs-lookup"><span data-stu-id="c3fad-199">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="c3fad-200">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="c3fad-200">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="c3fad-201">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="c3fad-201">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="c3fad-202">.NET Core をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-202">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="c3fad-203">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-203">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3fad-204">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-204">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="c3fad-205">必要なバージョンのホスト パッケージ フィードを設定します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-205">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="c3fad-206">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="c3fad-206">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="c3fad-207">**Ubuntu 16.04 / Linux Mint 18**</span><span class="sxs-lookup"><span data-stu-id="c3fad-207">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="c3fad-208">**Ubuntu 14.04 / Linux Mint 17**</span><span class="sxs-lookup"><span data-stu-id="c3fad-208">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="c3fad-209">Ubuntu または Linux Mint に、.NET Core 1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-209">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="c3fad-210">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-210">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="c3fad-211">Debian 8 または Debian 9 (64 ビット) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="c3fad-211">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="c3fad-212">Debian 8 または Debian 9 (64 ビット) 用の .NET Core をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="c3fad-212">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="c3fad-213">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-213">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="c3fad-214">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="c3fad-214">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c3fad-215">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-215">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="c3fad-216">システムのコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-216">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="c3fad-217">信頼済みの Microsoft プロダクト キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-217">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="c3fad-218">Microsoft 製品フィードを登録します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-218">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="c3fad-219">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="c3fad-219">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="c3fad-220">**Debian 8 (Jessie)**</span><span class="sxs-lookup"><span data-stu-id="c3fad-220">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="c3fad-221">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-221">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="c3fad-222">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-222">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3fad-223">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-223">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="c3fad-224">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-224">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="c3fad-225">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-225">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="c3fad-226">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-226">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="c3fad-227">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-227">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="c3fad-228">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-228">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="c3fad-229">.NET Core for Fedora 24、Fedora 25、または Fedora 26 (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="c3fad-229">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="c3fad-230">.NET Core for Fedora 26、Fedora 25 (.NET Core 2.x)、または Fedora 24 (.NET Core 1.x) をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="c3fad-230">To Install .NET Core for Fedora 26, Fedora 25 (.NET Core 2.x) or Fedora 24 (.NET Core 1.x):</span></span>

1. <span data-ttu-id="c3fad-231">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-231">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="c3fad-232">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="c3fad-232">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c3fad-233">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-233">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="c3fad-234">**Fedora 26 または Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="c3fad-234">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="c3fad-235">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-235">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="c3fad-236">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-236">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="c3fad-237">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-237">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="c3fad-238">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-238">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3fad-239">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-239">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="c3fad-240">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="c3fad-240">**Fedora 24**</span></span>

2. <span data-ttu-id="c3fad-241">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-241">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="c3fad-242">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-242">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="c3fad-243">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-243">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="c3fad-244">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-244">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="c3fad-245">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-245">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="c3fad-246">CentOS 7.1 (64 bit) および Oracle Linux 7.1 (64 bit) 用の .NET Core をインストールする</span><span class="sxs-lookup"><span data-stu-id="c3fad-246">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="c3fad-247">CentOS 7.1 (64 bit) および Oracle Linux 7.1 (64 bit) 用の .NET Core をインストールするには</span><span class="sxs-lookup"><span data-stu-id="c3fad-247">To Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="c3fad-248">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-248">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="c3fad-249">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="c3fad-249">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c3fad-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-250">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="c3fad-251">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-251">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="c3fad-252">Microsoft 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-252">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="c3fad-253">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-253">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="c3fad-254">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-254">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3fad-255">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-255">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="c3fad-256">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-256">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="c3fad-257">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-257">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="c3fad-258">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-258">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="c3fad-259">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-259">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="c3fad-260">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-260">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="c3fad-261">.NET Core for SUSE Linux Enterprise Server (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="c3fad-261">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="c3fad-262">.NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 ビット) をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="c3fad-262">To Install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="c3fad-263">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-263">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="c3fad-264">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-264">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="c3fad-265">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-265">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="c3fad-266">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-266">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="c3fad-267">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-267">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="c3fad-268">.NET Core for openSUSE (64 ビット) をインストールする</span><span class="sxs-lookup"><span data-stu-id="c3fad-268">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="c3fad-269">.NET Core 2.x for openSUSE または .NET Core 1.x for openSUSE (64 ビット) をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="c3fad-269">To Install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="c3fad-270">システムから**以前のプレビュー** バージョンの .NET Core を削除します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-270">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="c3fad-271">tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="c3fad-271">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c3fad-272">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-272">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="c3fad-273">Microsoft 署名キーを登録します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-273">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="c3fad-274">dotnet 製品フィードを追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-274">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="c3fad-275">.NET Core SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-275">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="c3fad-276">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-276">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c3fad-277">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="c3fad-277">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="c3fad-278">必須コンポーネントを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-278">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="c3fad-279">.NET Core SDK バイナリ (tarball) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c3fad-279">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="c3fad-280">.NET Core SDK バイナリを抽出します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-280">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="c3fad-281">パスに dotnet を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-281">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="c3fad-282">`dotnet --version` コマンドを実行して、インストールが成功したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c3fad-282">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="c3fad-283">サポートされている Linux ディストリビューション/バージョンの .NET Core 2.x で問題が発生している場合は、インストールしたディストリビューション/バージョンに対する [2.0 の既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3fad-283">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="c3fad-284">サポートされている Linux ディストリビューション/バージョンの .NET Core 1.x で問題が発生している場合は、インストールしたディストリビューション/バージョンに対する [1.0.0 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)と [1.0.1 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3fad-284">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>

