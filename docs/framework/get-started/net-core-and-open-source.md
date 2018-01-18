---
title: ".NET Core とオープン ソース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc41a51a9c85b84f2f5365eb1650ebec37888652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="8d8f1-102">.NET Core とオープン ソース</span><span class="sxs-lookup"><span data-stu-id="8d8f1-102">.NET Core and Open-Source</span></span>
<span data-ttu-id="8d8f1-103">このトピックでは、.NET Core の概要のほか、詳細情報の入手方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-103">This topic provides a brief overview  of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="8d8f1-104">.NET Core に関するトピックの完全な一覧については、[「.NET Core のガイド」](../../core/index.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-104">To find the complete list of topics for .NET Core, visit the [.NET Core Guide](../../core/index.md).</span></span>
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a><span data-ttu-id="8d8f1-105">.NET Core とは何ですか?</span><span class="sxs-lookup"><span data-stu-id="8d8f1-105">What is .NET Core?</span></span>  
 <span data-ttu-id="8d8f1-106">.NET Core は、モジュール形式のクロスプラットフォームかつオープン ソースを実装した汎用の .NET Standard です。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-106">.NET Core is a general purpose, modular, cross-platform and open source implementation of the .NET Standard.</span></span> <span data-ttu-id="8d8f1-107">.NET Framework と同じ API の多くが含まれるほか (ただし、.NET Core の方が数が少ない)、ランタイム、フレームワーク、コンパイラ、およびさまざまなオペレーティング システムやチップ ターゲットをサポートするツールのコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-107">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="8d8f1-108">.NET Core の実装は、主に ASP.NET Core のワークロードによるものですが、新しい実装の必要性とユーザーの要望にも後押しされました。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-108">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="8d8f1-109">この実装は、デバイス、クラウド、および埋め込み/IoT のシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-109">It can be used in device, cloud and embedded/IoT scenarios.</span></span>  
  
 <span data-ttu-id="8d8f1-110">.NET Core を使用する場合、[.NET Core のホームページ](https://www.microsoft.com/net/core)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-110">To get started with .NET Core, please visit the [.NET Core homepage](https://www.microsoft.com/net/core).</span></span>  
  
 <span data-ttu-id="8d8f1-111">.NET Core の主な特徴を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-111">Here are the main characteristics of .NET Core:</span></span>  
  
-   <span data-ttu-id="8d8f1-112">**クロス プラットフォーム:** .NET Core には、ターゲットとするプラットフォームに関係なく、必要とするアプリケーション機能を実装したり、そのコードを再使用したりするための主な機能が備わっています。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-112">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="8d8f1-113">現在、Windows、Linux と macOS の 3 つの主要オペレーティング システム (OS) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-113">It currently supports three main operating systems (OS): Windows, Linux and macOS.</span></span> <span data-ttu-id="8d8f1-114">サポートされている複数の OS で、修正せずに動作するアプリやライブラリを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-114">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="8d8f1-115">サポートされるオペレーティング システムの一覧については、[「.NET Core Roadmap」](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core ロードマップ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-115">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
-   <span data-ttu-id="8d8f1-116">**オープン ソース:** .NET Core は [.NET Foundation ](http://www.dotnetfoundation.org/)が管理している多くのプロジェクトの 1 つで、[GitHub](https://github.com/) で入手することができます。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-116">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](http://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span>  <span data-ttu-id="8d8f1-117">.NET Core をオープン ソース プロジェクトとして使用すると、開発プロセスの透明性が高まるほか、コミュニティが活発化して交流が促進されます。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-117">Having .NET Core as an open source project promotes a more transparent development process and promotes an active and engaged community.</span></span>  
  
-   <span data-ttu-id="8d8f1-118">**柔軟な展開:** アプリを展開する主な方法には、フレームワークに依存する展開と自己完結型の展開の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-118">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="8d8f1-119">フレームワークに依存して展開する場合、アプリとサード パーティの依存関係のみがインストールされ、アプリを使用できるようにするには、.NET Core のシステム全体のバージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-119">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span>  <span data-ttu-id="8d8f1-120">自己完結型で展開する場合、アプリの作成に使用される .NET Core バージョンが、アプリやサード パーティの依存関係と共に展開され、他のバージョンと並行して実行することができます。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-120">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side-by-side with other versions.</span></span>    <span data-ttu-id="8d8f1-121">詳しくは、「[.NET Core アプリケーション展開](../../core/deploying/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-121">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

-   <span data-ttu-id="8d8f1-122">**モジュール形式:** .NET Core は、小規模のアセンブリ パッケージで NuGet を介してリリースされるためモジュール形式となっています。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-122">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="8d8f1-123">.NET Core はコア機能のほとんどが含まれる 1 つの大きなアセンブリではなく、中心的な機能が含まれる比較的小さなパッケージとして提供されています。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-123">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller feature-centric packages.</span></span> <span data-ttu-id="8d8f1-124">これによって開発モデルがよりアジャイル化されるため、必要な NuGet パッケージだけが含まれるようにアプリを最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-124">This enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="8d8f1-125">小さいアプリ領域の利点には、セキュリティの強化、サービスの削減、パフォーマンスの向上、従量課金モデルによるコスト削減などがあります。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-125">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="8d8f1-126">.NET Core プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="8d8f1-126">The .NET Core Platform</span></span>  
 <span data-ttu-id="8d8f1-127">.NET Core プラットフォームは複数コンポーネントで構成され、マネージ コンパイラ、ランタイム、基本クラス ライブラリ、および ASP.NET Core などの多数のアプリケーション モデルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-127">The .NET Core platform is made of several components, which includes the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="8d8f1-128">さまざまなコンポーネントの詳細や、実際の操作については、以下の [GitHub](https://github.com/) リポジトリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d8f1-128">You can learn more about the different components and get engaged, by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
-   [<span data-ttu-id="8d8f1-129">.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d8f1-129">.NET Core</span></span>](https://github.com/dotnet/core)  
  
-   [<span data-ttu-id="8d8f1-130">CoreFX - .NET Core foundational libraries (CoreFX - .NET Core の基本的なライブラリ)</span><span class="sxs-lookup"><span data-stu-id="8d8f1-130">CoreFX - .NET Core foundational libraries</span></span>](https://github.com/dotnet/corefx)  
  
-   [<span data-ttu-id="8d8f1-131">CoreCLR - .NET Core runtime (CoreCLR - .NET Core ランタイム)</span><span class="sxs-lookup"><span data-stu-id="8d8f1-131">CoreCLR - .NET Core runtime</span></span>](https://github.com/dotnet/coreclr)  
  
-   [<span data-ttu-id="8d8f1-132">CLI - .NET Core command-line tools (CLI - .NET Core のコマンドライン ツール)</span><span class="sxs-lookup"><span data-stu-id="8d8f1-132">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
-   [<span data-ttu-id="8d8f1-133">Roslyn - .NET Compiler Platform (.NET コンパイラ プラットフォーム)</span><span class="sxs-lookup"><span data-stu-id="8d8f1-133">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
-   [<span data-ttu-id="8d8f1-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d8f1-134">ASP.NET Core</span></span>](https://github.com/aspnet/home)  
  
## <a name="see-also"></a><span data-ttu-id="8d8f1-135">参照</span><span class="sxs-lookup"><span data-stu-id="8d8f1-135">See Also</span></span>  
 [<span data-ttu-id="8d8f1-136">.NET Core のホーム ページ</span><span class="sxs-lookup"><span data-stu-id="8d8f1-136">.NET Core homepage</span></span>](https://www.microsoft.com/net/core)  
 [<span data-ttu-id="8d8f1-137">.NET Core のガイド</span><span class="sxs-lookup"><span data-stu-id="8d8f1-137">.NET Core Guide</span></span>](../../core/index.md)  
 [<span data-ttu-id="8d8f1-138">ASP.NET Core ドキュメント</span><span class="sxs-lookup"><span data-stu-id="8d8f1-138">ASP.NET Core Documentation</span></span>](/aspnet/core/)
