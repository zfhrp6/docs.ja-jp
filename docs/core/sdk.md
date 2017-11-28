---
title: ".NET Core SDK 概要"
description: ".NET Core プロジェクトの作成に使用するライブラリとツールのセットである .NET Core SDK について説明します。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
ms.openlocfilehash: 8f3d0f5b3bccdd1ca25fa1202c2c727e402fe668
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="net-core-sdk-overview"></a><span data-ttu-id="144b2-104">.NET Core SDK 概要</span><span class="sxs-lookup"><span data-stu-id="144b2-104">.NET Core SDK Overview</span></span> 

## <a name="introduction"></a><span data-ttu-id="144b2-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="144b2-105">Introduction</span></span>
<span data-ttu-id="144b2-106">.NET Core ソフトウェア開発キット (SDK) は一連のライブラリとツールであり、開発者はこれを利用して .NET Core のアプリケーションやライブラリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="144b2-106">.NET Core Software Development Kit (SDK) is a set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="144b2-107">開発者にとって利用する機会の多いパッケージです。</span><span class="sxs-lookup"><span data-stu-id="144b2-107">This is the package that developers will most likely acquire.</span></span> 

<span data-ttu-id="144b2-108">次の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="144b2-108">It contains the following components:</span></span>

1. <span data-ttu-id="144b2-109">アプリケーションの作成に使用される .NET Core コマンド ライン ツール</span><span class="sxs-lookup"><span data-stu-id="144b2-109">The .NET Core Command Line Tools that are used to build applications</span></span>
2. <span data-ttu-id="144b2-110">アプリケーションを作成し、実行するための .NET Core (ライブラリとランタイム)</span><span class="sxs-lookup"><span data-stu-id="144b2-110">.NET Core (libraries and runtime) that allow applications to both be built and run</span></span>
3. <span data-ttu-id="144b2-111">[CLI コマンド](tools/index.md)を実行し、アプリケーションを実行するための `dotnet` ドライバー</span><span class="sxs-lookup"><span data-stu-id="144b2-111">The `dotnet` driver for running the [CLI commands](tools/index.md) as well as running applications</span></span>


## <a name="acquiring-the-net-core-sdk"></a><span data-ttu-id="144b2-112">.NET Core SDK を入手する</span><span class="sxs-lookup"><span data-stu-id="144b2-112">Acquiring the .NET Core SDK</span></span>
<span data-ttu-id="144b2-113">他のツールと同様に、最初にコンピューターにツールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="144b2-113">As with any tooling, the first thing is to get the tools to your machine.</span></span> <span data-ttu-id="144b2-114">シナリオにもよりますが、ネイティブ インストーラーで SDK をインストールしたり、インストール シェル スクリプトを利用したりできます。</span><span class="sxs-lookup"><span data-stu-id="144b2-114">Depending on your scenario, you can either use the native installers to install the SDK or use the installation shell script.</span></span>

<span data-ttu-id="144b2-115">開発者のコンピューターでは、ネイティブ インストーラーが利用されることが多いです。</span><span class="sxs-lookup"><span data-stu-id="144b2-115">The native installers are primarily meant for developer's machines.</span></span> <span data-ttu-id="144b2-116">SDK はサポートされるプラットフォームのネイティブ インストール メカニズムにより配信されます。たとえば、Ubuntu の場合は DEB パッケージ、Windows の場合は MSI バンドルです。</span><span class="sxs-lookup"><span data-stu-id="144b2-116">The SDK is distributed using each supported platform's native install mechanism, for instance DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="144b2-117">これらのインストーラーは、インストール直後、ユーザーが SDK を使用するために必要とする環境をインストールし、設定します。</span><span class="sxs-lookup"><span data-stu-id="144b2-117">These installers will install and set up the environment as needed for the user to use the SDK immediately after the install.</span></span> <span data-ttu-id="144b2-118">ただし、コンピューター上で管理者特権も必要になります。</span><span class="sxs-lookup"><span data-stu-id="144b2-118">However, they also require administrative privileges on the machine.</span></span> <span data-ttu-id="144b2-119">インストール手順は、[.NET Core のインストール ガイド](https://aka.ms/dotnetcoregs)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="144b2-119">You can view the installation instructions on the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>

<span data-ttu-id="144b2-120">一方で、インストール スクリプトの場合、管理者特権は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="144b2-120">Install scripts, on the other hand, do not require administrative privileges.</span></span> <span data-ttu-id="144b2-121">ただし、いかなる前提条件もコンピューターにインストールされません。前提条件はすべてユーザーが手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="144b2-121">However, they will also not install any prerequisites on the machine; you need to install all of the prerequisites manually.</span></span> <span data-ttu-id="144b2-122">スクリプトは、通常、管理者特権なしでツールをインストールするとき、ビルド サーバーを設定するために利用されます (上の前提条件警告に注意してください)。</span><span class="sxs-lookup"><span data-stu-id="144b2-122">The scripts are meant mostly for setting up build servers or when you wish to install the tools without admin privileges (do note the prerequisites caveat above).</span></span> <span data-ttu-id="144b2-123">詳細については、[インストール スクリプト参照](tools/dotnet-install-script.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="144b2-123">You can find more information on the [install script reference topic](tools/dotnet-install-script.md).</span></span> <span data-ttu-id="144b2-124">CI ビルド サーバーで SDK を設定する方法については、「[SDK with CI servers](tools/using-ci-with-cli.md)」というドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="144b2-124">If you are interested in how to set up SDK on your CI build server you can take a look at the [SDK with CI servers](tools/using-ci-with-cli.md) document.</span></span> 

<span data-ttu-id="144b2-125">既定では、SDK は "SxS" (side-by-side/横並び) 方式でインストールを実行します。</span><span class="sxs-lookup"><span data-stu-id="144b2-125">By default, the SDK will install in a "side-by-side" (SxS) manner.</span></span> <span data-ttu-id="144b2-126">つまり、1 台のコンピューター上で複数のバージョンの CLI ツールが共存できます。</span><span class="sxs-lookup"><span data-stu-id="144b2-126">This means that multiple versions of the CLI tools can coexist at any given time on a single machine.</span></span> <span data-ttu-id="144b2-127">正しいバージョンを使用する方法については、.NET Core コマンド ライン ツール トピックの[ドライバー セクション](tools/index.md#driver)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="144b2-127">How the correct version gets used is explained in more detail in the [driver section](tools/index.md#driver) of .NET Core Command Line Tools topic.</span></span>
