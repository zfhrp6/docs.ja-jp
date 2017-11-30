---
title: "Docker コンテナーを .NET Framework を選択します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker コンテナーを .NET Framework を選択します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1bf1f055f040e7f3dc575b7a04140ebf0c599f98
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a><span data-ttu-id="0bac0-104">Docker コンテナーを .NET Framework を選択します。</span><span class="sxs-lookup"><span data-stu-id="0bac0-104">When to choose .NET Framework for Docker containers</span></span>

<span data-ttu-id="0bac0-105">.NET Core では、新しいアプリケーションおよびアプリケーションのパターンの重要な利点が用意されています、.NET Framework は引き続きなります多くの既存のシナリオに適してします。</span><span class="sxs-lookup"><span data-stu-id="0bac0-105">While .NET Core offers significant benefits for new applications and application patterns, .NET Framework will continue to be a good choice for many existing scenarios.</span></span>

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a><span data-ttu-id="0bac0-106">Windows Server のコンテナーに直接既存のアプリケーションを移行します。</span><span class="sxs-lookup"><span data-stu-id="0bac0-106">Migrating existing applications directly to a Windows Server container</span></span>

<span data-ttu-id="0bac0-107">Microservices を作成していない場合でも、だけ展開を簡略化、Docker コンテナーを使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="0bac0-107">You might want to use Docker containers just to simplify deployment, even if you are not creating microservices.</span></span> <span data-ttu-id="0bac0-108">たとえば、Docker を使用した DevOps ワークフローを向上させたいおそらく — コンテナーがより分離されたテスト環境を移すことができるし、実稼働環境に移動すると、依存関係の欠落による配置の問題を回避できますも。</span><span class="sxs-lookup"><span data-stu-id="0bac0-108">For example, perhaps you want to improve your DevOps workflow with Docker—containers can give you better isolated test environments and can also eliminate deployment issues caused by missing dependencies when you move to a production environment.</span></span> <span data-ttu-id="0bac0-109">上記のような場合は、単体のアプリケーションを配置する場合でも理にかなって Docker と Windows コンテナーを使用して、現在の .NET Framework アプリケーション用にします。</span><span class="sxs-lookup"><span data-stu-id="0bac0-109">In cases like these, even if you are deploying a monolithic application, it makes sense to use Docker and Windows Containers for your current .NET Framework applications.</span></span>

<span data-ttu-id="0bac0-110">このシナリオのほとんどの場合、必要はありません、既存のアプリケーションを .NET Core; を移行するにはDocker コンテナーを含む従来の .NET Framework を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0bac0-110">In most cases for this scenario, you will not need to migrate your existing applications to .NET Core; you can use Docker containers that include the traditional .NET Framework.</span></span> <span data-ttu-id="0bac0-111">ただし、推奨される方法では、ASP.NET Core で新しいサービスを作成するなど、既存のアプリケーションを拡張するように、.NET Core を使用します。</span><span class="sxs-lookup"><span data-stu-id="0bac0-111">However, a recommended approach is to use .NET Core as you extend an existing application, such as writing a new service in ASP.NET Core.</span></span>

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a><span data-ttu-id="0bac0-112">.NET ライブラリのサード パーティ製または NuGet パッケージのない .NET Core を使用します。</span><span class="sxs-lookup"><span data-stu-id="0bac0-112">Using third-party .NET libraries or NuGet packages not available for .NET Core</span></span>

<span data-ttu-id="0bac0-113">サードパーティ製のライブラリが採用すばやく、 [.NET 標準](https://docs.microsoft.com/dotnet/standard/net-standard)コードを .NET Core を含む、すべての .NET フレーバー間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="0bac0-113">Third-party libraries are quickly embracing the [.NET Standard](https://docs.microsoft.com/dotnet/standard/net-standard), which enables code sharing across all .NET flavors, including .NET Core.</span></span> <span data-ttu-id="0bac0-114">.NET 標準ライブラリ 2.0 以降の API サーフェスさまざまなフレームワークの間で互換性が大きくなり、.NET Core 2.0 のアプリケーションは直接も既存の .NET Framework ライブラリを参照 (を参照してください[compatshim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work))。</span><span class="sxs-lookup"><span data-stu-id="0bac0-114">With the .NET Standard Library 2.0 and beyond the API surface compatibility across different frameworks has become significantly larger and in .NET Core 2.0 applications can also directly reference existing .NET Framework libraries (see [compat shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).</span></span>

<span data-ttu-id="0bac0-115">ただし、その例外的な進行している .NET 標準 2.0 と .NET Core 2.0 以降を使用する場合でも場合もあります一部の NuGet パッケージが Windows を実行する必要があるし、.NET Core をサポートしていない可能性。</span><span class="sxs-lookup"><span data-stu-id="0bac0-115">However, even with that exceptional progression since .NET Standard 2.0 and .NET Core 2.0, there might be cases where certain NuGet packages need Windows to run and might not support .NET Core.</span></span> <span data-ttu-id="0bac0-116">これらのパッケージが、アプリケーションの重要な場合は、Windows コンテナーを .NET Framework を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bac0-116">If those packages are critical for your application, then you will need to use .NET Framework on Windows Containers.</span></span>

## <a name="usingnet-technologies-not-available-for-net-core"></a><span data-ttu-id="0bac0-117">.NET Core では利用できません Using.NET テクノロジ</span><span class="sxs-lookup"><span data-stu-id="0bac0-117">Using.NET technologies not available for .NET Core</span></span> 

<span data-ttu-id="0bac0-118">一部の .NET Framework テクノロジは、.NET Core (このドキュメントの作成時点でバージョン 2.0) の現在のバージョンでご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="0bac0-118">Some .NET Framework technologies are not available in the current version of .NET Core (version 2.0 as of this writing).</span></span> <span data-ttu-id="0bac0-119">.NET Core の今後のリリースで利用可能なそれらの一部になります (.NET Core 2.x)、その他のユーザーのパターンは、.NET Core の対象となるし、利用できない可能性があります、新しいアプリケーションには適用されません。</span><span class="sxs-lookup"><span data-stu-id="0bac0-119">Some of them will be available in later .NET Core releases (.NET Core 2.x), but others do not apply to the new application patterns targeted by .NET Core and might never be available.</span></span>

<span data-ttu-id="0bac0-120">.NET Core 2.0 では使用できない、テクノロジのほとんどを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0bac0-120">The following list shows most of the technologies that are not available in .NET Core 2.0:</span></span>

-   <span data-ttu-id="0bac0-121">ASP.NET Web フォームです。</span><span class="sxs-lookup"><span data-stu-id="0bac0-121">ASP.NET Web Forms.</span></span> <span data-ttu-id="0bac0-122">このテクノロジは、.NET Framework をできるだけです。</span><span class="sxs-lookup"><span data-stu-id="0bac0-122">This technology is only available on .NET Framework.</span></span> <span data-ttu-id="0bac0-123">現時点では、ASP.NET Web フォームを .NET Core で使用できるようにする予定はありません。</span><span class="sxs-lookup"><span data-stu-id="0bac0-123">Currently there are no plans to bring ASP.NET Web Forms to .NET Core.</span></span>

-   <span data-ttu-id="0bac0-124">WCF サービス。</span><span class="sxs-lookup"><span data-stu-id="0bac0-124">WCF services.</span></span> <span data-ttu-id="0bac0-125">場合でも、 [WCF クライアント ライブラリ](https://github.com/dotnet/wcf).NET Core から WCF サービスを利用することはできます。</span><span class="sxs-lookup"><span data-stu-id="0bac0-125">Even when a [WCF-Client library](https://github.com/dotnet/wcf) is available to consume WCF services from .NET Core.</span></span> <span data-ttu-id="0bac0-126">mid 2017 時点での WCF サーバーの実装は .NET Framework で使用できるのみです。</span><span class="sxs-lookup"><span data-stu-id="0bac0-126">as of mid-2017, the WCF server implementation is only available on .NET Framework.</span></span> <span data-ttu-id="0bac0-127">このシナリオは、.NET Core の将来のリリースについて検討する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0bac0-127">This scenario might be considered for future releases of .NET Core.</span></span>

-   <span data-ttu-id="0bac0-128">ワークフローに関連するサービスです。</span><span class="sxs-lookup"><span data-stu-id="0bac0-128">Workflow-related services.</span></span> <span data-ttu-id="0bac0-129">Windows Workflow Foundation (WF)、(WCF + 1 つのサービスでの WF) ワークフロー サービスと WCF データ サービス (旧称 ADO.NET Data Services) では、.NET Framework で使用できるのみです。</span><span class="sxs-lookup"><span data-stu-id="0bac0-129">Windows Workflow Foundation (WF), Workflow Services (WCF + WF in a single service), and WCF Data Services (formerly known as ADO.NET Data Services) are only available on .NET Framework.</span></span> <span data-ttu-id="0bac0-130">現在のプランを .NET Core にするためにはありません。</span><span class="sxs-lookup"><span data-stu-id="0bac0-130">There are currently no plans to bring them to .NET Core.</span></span>

<span data-ttu-id="0bac0-131">公式に一覧表示、テクノロジだけでなく[.NET Core ロードマップ](https://github.com/aspnet/Home/wiki/Roadmap)、その他の機能は、.NET Core に移植する場合があります。</span><span class="sxs-lookup"><span data-stu-id="0bac0-131">In addition to the technologies listed in the official [.NET Core roadmap](https://github.com/aspnet/Home/wiki/Roadmap), other features might be ported to .NET Core.</span></span> <span data-ttu-id="0bac0-132">完全な一覧を参照としてタグ付けされたアイテム[ポートからコア](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core)CoreFX GitHub サイトです。</span><span class="sxs-lookup"><span data-stu-id="0bac0-132">For a full list, look at the items tagged as [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) on the CoreFX GitHub site.</span></span> <span data-ttu-id="0bac0-133">この一覧は、.NET Core をこれらのコンポーネントをさせる Microsoft からのコミットメントを表さない注: 項目は単に、コミュニティからの要求をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="0bac0-133">Note that this list does not represent a commitment from Microsoft to bring those components to .NET Core—the items simply capture requests from the community.</span></span> <span data-ttu-id="0bac0-134">上に示したコンポーネントについて注意する場合は、自分の声が聞こえるようには、GitHub のディスカッションに参加していることを検討します。</span><span class="sxs-lookup"><span data-stu-id="0bac0-134">If you care about any of the components listed above, consider participating in the discussions on GitHub so that your voice can be heard.</span></span> <span data-ttu-id="0bac0-135">また、何か足りないと感じた場合は、[CoreFX リポジトリで新しい案件を作成](https://github.com/dotnet/corefx/issues/new)してください。</span><span class="sxs-lookup"><span data-stu-id="0bac0-135">And if you think something is missing, please [file a new issue in the CoreFX repository](https://github.com/dotnet/corefx/issues/new).</span></span>

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a><span data-ttu-id="0bac0-136">プラットフォームまたは .NET Core をサポートしていない API を使用</span><span class="sxs-lookup"><span data-stu-id="0bac0-136">Using a platform or API that does not support .NET Core</span></span>

<span data-ttu-id="0bac0-137">一部の Microsoft またはサード パーティのプラットフォームでは、.NET Core をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0bac0-137">Some Microsoft or third-party platforms do not support .NET Core.</span></span> <span data-ttu-id="0bac0-138">たとえば、一部の Azure サービスは、されていない .NET Core で利用できるよう SDK を提供します。</span><span class="sxs-lookup"><span data-stu-id="0bac0-138">For example, some Azure services provide an SDK that is not yet available for consumption on .NET Core.</span></span> <span data-ttu-id="0bac0-139">これは、機能は、すべての Azure サービスの .NET Core を最終的に使用するため、一時的なです。</span><span class="sxs-lookup"><span data-stu-id="0bac0-139">This is temporary, because all Azure services will eventually use .NET Core.</span></span> <span data-ttu-id="0bac0-140">など、 [Azure DocumentDB の SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) 2016 年 11 月 16 日でプレビューとしてリリースされましたが安定したバージョンとして一般公開 (GA) ではようになりました。</span><span class="sxs-lookup"><span data-stu-id="0bac0-140">For example, the [Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) was released as a preview on November 16, 2016, but it is now generally available (GA) as a stable version.</span></span>

<span data-ttu-id="0bac0-141">その間は、任意のプラットフォームまたは Azure のサービスもサポートしていない場合 .NET Core そのクライアント API と、.NET Framework での Azure サービスまたはクライアント SDK から同等の REST API を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0bac0-141">In the meantime, if any platform or service in Azure still doesn’t support .NET Core with its client API, you can use the equivalent REST API from the Azure service or the client SDK on .NET Framework.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0bac0-142">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0bac0-142">Additional resources</span></span>

-   <span data-ttu-id="0bac0-143">**.NET core ガイド**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)</span><span class="sxs-lookup"><span data-stu-id="0bac0-143">**.NET Core Guide**
[*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)</span></span>

-   <span data-ttu-id="0bac0-144">**.NET Framework から .NET Core への移植**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)</span><span class="sxs-lookup"><span data-stu-id="0bac0-144">**Porting from .NET Framework to .NET Core**
[*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)</span></span>

-   <span data-ttu-id="0bac0-145">**Docker のガイドに .NET framework**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)</span><span class="sxs-lookup"><span data-stu-id="0bac0-145">**.NET Framework on Docker Guide**
[*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)</span></span>

-   <span data-ttu-id="0bac0-146">**.NET コンポーネントの概要**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)</span><span class="sxs-lookup"><span data-stu-id="0bac0-146">**.NET Components Overview**
[*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="0bac0-147">[前](net-コア-コンテナーの scenarios.md) [次へ] (コンテナーのフレームワークの選択-factors.md)</span><span class="sxs-lookup"><span data-stu-id="0bac0-147">[Previous] (net-core-container-scenarios.md) [Next] (container-framework-choice-factors.md)</span></span>
