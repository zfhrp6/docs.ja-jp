---
title: .NET Core SDK 概要
description: .NET Core プロジェクトの作成に使用するライブラリとツールのセットである .NET Core SDK について説明します。
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 5fc04c3ef5a1502251a9caf0b6a5f5809faad5b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-sdk-overview"></a><span data-ttu-id="cee71-103">.NET Core SDK 概要</span><span class="sxs-lookup"><span data-stu-id="cee71-103">.NET Core SDK Overview</span></span> 

## <a name="introduction"></a><span data-ttu-id="cee71-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="cee71-104">Introduction</span></span>
<span data-ttu-id="cee71-105">.NET Core ソフトウェア開発キット (SDK) は一連のライブラリとツールであり、開発者はこれを利用して .NET Core のアプリケーションやライブラリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cee71-105">.NET Core Software Development Kit (SDK) is a set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="cee71-106">開発者にとって利用する機会の多いパッケージです。</span><span class="sxs-lookup"><span data-stu-id="cee71-106">This is the package that developers will most likely acquire.</span></span> 

<span data-ttu-id="cee71-107">次の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="cee71-107">It contains the following components:</span></span>

1. <span data-ttu-id="cee71-108">アプリケーションの作成に使用される .NET Core コマンド ライン ツール</span><span class="sxs-lookup"><span data-stu-id="cee71-108">The .NET Core Command Line Tools that are used to build applications</span></span>
2. <span data-ttu-id="cee71-109">アプリケーションを作成し、実行するための .NET Core (ライブラリとランタイム)</span><span class="sxs-lookup"><span data-stu-id="cee71-109">.NET Core (libraries and runtime) that allow applications to both be built and run</span></span>
3. <span data-ttu-id="cee71-110">[CLI コマンド](tools/index.md)を実行し、アプリケーションを実行するための `dotnet` ドライバー</span><span class="sxs-lookup"><span data-stu-id="cee71-110">The `dotnet` driver for running the [CLI commands](tools/index.md) as well as running applications</span></span>


## <a name="acquiring-the-net-core-sdk"></a><span data-ttu-id="cee71-111">.NET Core SDK を入手する</span><span class="sxs-lookup"><span data-stu-id="cee71-111">Acquiring the .NET Core SDK</span></span>
<span data-ttu-id="cee71-112">他のツールと同様に、最初にコンピューターにツールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cee71-112">As with any tooling, the first thing is to get the tools to your machine.</span></span> <span data-ttu-id="cee71-113">シナリオにもよりますが、ネイティブ インストーラーで SDK をインストールしたり、インストール シェル スクリプトを利用したりできます。</span><span class="sxs-lookup"><span data-stu-id="cee71-113">Depending on your scenario, you can either use the native installers to install the SDK or use the installation shell script.</span></span>

<span data-ttu-id="cee71-114">開発者のコンピューターでは、ネイティブ インストーラーが利用されることが多いです。</span><span class="sxs-lookup"><span data-stu-id="cee71-114">The native installers are primarily meant for developer's machines.</span></span> <span data-ttu-id="cee71-115">SDK はサポートされるプラットフォームのネイティブ インストール メカニズムにより配信されます。たとえば、Ubuntu の場合は DEB パッケージ、Windows の場合は MSI バンドルです。</span><span class="sxs-lookup"><span data-stu-id="cee71-115">The SDK is distributed using each supported platform's native install mechanism, for instance DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="cee71-116">これらのインストーラーは、インストール直後、ユーザーが SDK を使用するために必要とする環境をインストールし、設定します。</span><span class="sxs-lookup"><span data-stu-id="cee71-116">These installers will install and set up the environment as needed for the user to use the SDK immediately after the install.</span></span> <span data-ttu-id="cee71-117">ただし、コンピューター上で管理者特権も必要になります。</span><span class="sxs-lookup"><span data-stu-id="cee71-117">However, they also require administrative privileges on the machine.</span></span> <span data-ttu-id="cee71-118">インストール手順は、[.NET Core のインストール ガイド](https://aka.ms/dotnetcoregs)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="cee71-118">You can view the installation instructions on the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>

<span data-ttu-id="cee71-119">一方で、インストール スクリプトの場合、管理者特権は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="cee71-119">Install scripts, on the other hand, do not require administrative privileges.</span></span> <span data-ttu-id="cee71-120">ただし、いかなる前提条件もコンピューターにインストールされません。前提条件はすべてユーザーが手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cee71-120">However, they will also not install any prerequisites on the machine; you need to install all of the prerequisites manually.</span></span> <span data-ttu-id="cee71-121">スクリプトは、通常、管理者特権なしでツールをインストールするとき、ビルド サーバーを設定するために利用されます (上の前提条件警告に注意してください)。</span><span class="sxs-lookup"><span data-stu-id="cee71-121">The scripts are meant mostly for setting up build servers or when you wish to install the tools without admin privileges (do note the prerequisites caveat above).</span></span> <span data-ttu-id="cee71-122">詳細については、[インストール スクリプト参照](tools/dotnet-install-script.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cee71-122">You can find more information on the [install script reference topic](tools/dotnet-install-script.md).</span></span> <span data-ttu-id="cee71-123">CI ビルド サーバーで SDK を設定する方法については、「[SDK with CI servers](tools/using-ci-with-cli.md)」というドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cee71-123">If you are interested in how to set up SDK on your CI build server you can take a look at the [SDK with CI servers](tools/using-ci-with-cli.md) document.</span></span> 

<span data-ttu-id="cee71-124">既定では、SDK は "SxS" (side-by-side/横並び) 方式でインストールを実行します。</span><span class="sxs-lookup"><span data-stu-id="cee71-124">By default, the SDK will install in a "side-by-side" (SxS) manner.</span></span> <span data-ttu-id="cee71-125">つまり、1 台のコンピューター上で複数のバージョンの CLI ツールが共存できます。</span><span class="sxs-lookup"><span data-stu-id="cee71-125">This means that multiple versions of the CLI tools can coexist at any given time on a single machine.</span></span> <span data-ttu-id="cee71-126">正しいバージョンを使用する方法については、.NET Core コマンド ライン ツール トピックの[ドライバー セクション](tools/index.md#driver)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cee71-126">How the correct version gets used is explained in more detail in the [driver section](tools/index.md#driver) of .NET Core Command Line Tools topic.</span></span>
