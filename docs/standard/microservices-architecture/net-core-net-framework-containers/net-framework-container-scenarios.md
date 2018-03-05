---
title: "Docker コンテナー用 .NET Framework を選択するタイミング"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker コンテナー用 .NET Framework を選択するタイミング"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eec258ff01bcfeb834fa7a1138fdf822fd00c996
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a><span data-ttu-id="39ea1-104">Docker コンテナー用 .NET Framework を選択するタイミング</span><span class="sxs-lookup"><span data-stu-id="39ea1-104">When to choose .NET Framework for Docker containers</span></span>

<span data-ttu-id="39ea1-105">.NET Core は新しいアプリケーションとアプリケーション パターンには大きな利点がありますが、既存の多くのシナリオでは引き続き .NET Framework が適切な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-105">While .NET Core offers significant benefits for new applications and application patterns, .NET Framework will continue to be a good choice for many existing scenarios.</span></span>

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a><span data-ttu-id="39ea1-106">既存アプリケーションを Windows Server コンテナーに直接移行する</span><span class="sxs-lookup"><span data-stu-id="39ea1-106">Migrating existing applications directly to a Windows Server container</span></span>

<span data-ttu-id="39ea1-107">マイクロサービスを作成していない場合は、デプロイメントを簡略にするためだけでも Docker コンテナーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="39ea1-107">You might want to use Docker containers just to simplify deployment, even if you are not creating microservices.</span></span> <span data-ttu-id="39ea1-108">たとえば、Docker に対する DevOps ワークフローを改善したいとします。コンテナーを使用すると、適切に分離されたテスト環境を確保でき、運用環境に移行したときに依存関係が失われて生じるデプロイメントの問題も解消できます。</span><span class="sxs-lookup"><span data-stu-id="39ea1-108">For example, perhaps you want to improve your DevOps workflow with Docker—containers can give you better isolated test environments and can also eliminate deployment issues caused by missing dependencies when you move to a production environment.</span></span> <span data-ttu-id="39ea1-109">このようなケースでは、単体のアプリケーションをデプロイする場合でも、現在の .NET Framework アプリケーションのために Docker および Windows コンテナーを使用するメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-109">In cases like these, even if you are deploying a monolithic application, it makes sense to use Docker and Windows Containers for your current .NET Framework applications.</span></span>

<span data-ttu-id="39ea1-110">このシナリオのほとんどのケースでは、既存アプリケーションを .NET Core に移行する必要は生じません。従来の .NET Framework を含む Docker コンテナーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="39ea1-110">In most cases for this scenario, you will not need to migrate your existing applications to .NET Core; you can use Docker containers that include the traditional .NET Framework.</span></span> <span data-ttu-id="39ea1-111">ただし、ASP.NET Core で新しいサービスを作成するなど、既存のアプリケーションを拡張する際には、代わりに .NET Core を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39ea1-111">However, a recommended approach is to use .NET Core as you extend an existing application, such as writing a new service in ASP.NET Core.</span></span>

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a><span data-ttu-id="39ea1-112">NET Core で使用できないサードパーティ製の .NET ライブラリや NuGet パッケージを使用する</span><span class="sxs-lookup"><span data-stu-id="39ea1-112">Using third-party .NET libraries or NuGet packages not available for .NET Core</span></span>

<span data-ttu-id="39ea1-113">サードパーティ ライブラリでは [.NET Standard](../../net-standard.md) の採用が迅速に進められています。これにより、.NET Core を含むすべての種類の .NET でコードを共有できるようになります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-113">Third-party libraries are quickly embracing the [.NET Standard](../../net-standard.md), which enables code sharing across all .NET flavors, including .NET Core.</span></span> <span data-ttu-id="39ea1-114">.NET Standard Library 2.0 以上では、異なるフレームワーク間での API サーフェスの互換性はかなり高くなっています。また、.NET Core 2.0 では、アプリケーションは既存の .NET Framework ライブラリを直接参照することもできます (「[compat shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="39ea1-114">With the .NET Standard Library 2.0 and beyond the API surface compatibility across different frameworks has become significantly larger and in .NET Core 2.0 applications can also directly reference existing .NET Framework libraries (see [compat shim](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).</span></span>

<span data-ttu-id="39ea1-115">ただし、.NET Standard 2.0 および .NET Core 2.0 以降の進歩が並外れているとしても、特定の NuGet パッケージが実行に Windows を必要とし、.NET Core をサポートしていないというケースはあります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-115">However, even with that exceptional progression since .NET Standard 2.0 and .NET Core 2.0, there might be cases where certain NuGet packages need Windows to run and might not support .NET Core.</span></span> <span data-ttu-id="39ea1-116">これらのパッケージがアプリケーションに不可欠な場合は、Windows コンテナー上で .NET Framework を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-116">If those packages are critical for your application, then you will need to use .NET Framework on Windows Containers.</span></span>

## <a name="using-net-technologies-not-available-for-net-core"></a><span data-ttu-id="39ea1-117">.NET Core で使用できない .NET テクノロジを使用する</span><span class="sxs-lookup"><span data-stu-id="39ea1-117">Using .NET technologies not available for .NET Core</span></span> 

<span data-ttu-id="39ea1-118">一部の .NET Framework テクノロジは現在の .NET Core バージョン (このドキュメント作成時点のバージョン 2.0) では利用できません。</span><span class="sxs-lookup"><span data-stu-id="39ea1-118">Some .NET Framework technologies are not available in the current version of .NET Core (version 2.0 as of this writing).</span></span> <span data-ttu-id="39ea1-119">.NET Core の今後のリリース (.NET Core 2.x) で使用可能になるものもありますが、それ以外は .NET Core の対象となる新しいアプリケーション パターンには適用されず、使用可能にならない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-119">Some of them will be available in later .NET Core releases (.NET Core 2.x), but others do not apply to the new application patterns targeted by .NET Core and might never be available.</span></span>

<span data-ttu-id="39ea1-120">.NET Core 2.0 で利用できないテクノロジのほとんどを次に示します。</span><span class="sxs-lookup"><span data-stu-id="39ea1-120">The following list shows most of the technologies that are not available in .NET Core 2.0:</span></span>

-   <span data-ttu-id="39ea1-121">ASP.NET Web フォーム。</span><span class="sxs-lookup"><span data-stu-id="39ea1-121">ASP.NET Web Forms.</span></span> <span data-ttu-id="39ea1-122">このテクノロジは .NET Framework のみで利用できます。</span><span class="sxs-lookup"><span data-stu-id="39ea1-122">This technology is only available on .NET Framework.</span></span> <span data-ttu-id="39ea1-123">現時点では、ASP.NET Web フォームを .NET Core で使用できるようにする予定はありません。</span><span class="sxs-lookup"><span data-stu-id="39ea1-123">Currently there are no plans to bring ASP.NET Web Forms to .NET Core.</span></span>

-   <span data-ttu-id="39ea1-124">WCF サービス。</span><span class="sxs-lookup"><span data-stu-id="39ea1-124">WCF services.</span></span> <span data-ttu-id="39ea1-125">[WCF クライアント ライブラリ](https://github.com/dotnet/wcf)を使用して .NET Core の WCF サービスを利用できる場合でも、</span><span class="sxs-lookup"><span data-stu-id="39ea1-125">Even when a [WCF-Client library](https://github.com/dotnet/wcf) is available to consume WCF services from .NET Core.</span></span> <span data-ttu-id="39ea1-126">2017 年中頃の時点では、WCF サーバーは .NET Framework のみに実装できます。</span><span class="sxs-lookup"><span data-stu-id="39ea1-126">as of mid-2017, the WCF server implementation is only available on .NET Framework.</span></span> <span data-ttu-id="39ea1-127">このシナリオは、.NET Core の将来のリリースで検討される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-127">This scenario might be considered for future releases of .NET Core.</span></span>

-   <span data-ttu-id="39ea1-128">ワークフロー関連サービス。</span><span class="sxs-lookup"><span data-stu-id="39ea1-128">Workflow-related services.</span></span> <span data-ttu-id="39ea1-129">Windows Workflow Foundation (WF)、ワークフロー サービス (1 つのサービスに WCF と WF) および WCF Data Services (旧称: ADO.NET Data Services) は、NET Framework でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="39ea1-129">Windows Workflow Foundation (WF), Workflow Services (WCF + WF in a single service), and WCF Data Services (formerly known as ADO.NET Data Services) are only available on .NET Framework.</span></span> <span data-ttu-id="39ea1-130">現在、この機能を .NET Core に含める計画はありません。</span><span class="sxs-lookup"><span data-stu-id="39ea1-130">There are currently no plans to bring them to .NET Core.</span></span>

<span data-ttu-id="39ea1-131">公式の [.NET Core ロードマップ](https://github.com/aspnet/Home/wiki/Roadmap)に記載されているテクノロジに加え、他の機能が .NET Core に移植される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-131">In addition to the technologies listed in the official [.NET Core roadmap](https://github.com/aspnet/Home/wiki/Roadmap), other features might be ported to .NET Core.</span></span> <span data-ttu-id="39ea1-132">完全な一覧については、CoreFX GitHub サイトで [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) のタグが付いた項目をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39ea1-132">For a full list, look at the items tagged as [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) on the CoreFX GitHub site.</span></span> <span data-ttu-id="39ea1-133">この一覧は Microsoft がこれらのコンポーネントを .NET Core に提供することを約束するものではなく、単にコミュニティの要望に応じた項目であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="39ea1-133">Note that this list does not represent a commitment from Microsoft to bring those components to .NET Core — the items simply capture requests from the community.</span></span> <span data-ttu-id="39ea1-134">前述のコンポーネントが気になる場合には、GitHub でのディスカッションに参加して意見を述べることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="39ea1-134">If you care about any of the components listed above, consider participating in the discussions on GitHub so that your voice can be heard.</span></span> <span data-ttu-id="39ea1-135">また、何か足りないと感じた場合は、[CoreFX リポジトリで新しい案件を作成](https://github.com/dotnet/corefx/issues/new)してください。</span><span class="sxs-lookup"><span data-stu-id="39ea1-135">And if you think something is missing, please [file a new issue in the CoreFX repository](https://github.com/dotnet/corefx/issues/new).</span></span>

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a><span data-ttu-id="39ea1-136">.NET Core をサポートしていないプラットフォームまたは API を使用する</span><span class="sxs-lookup"><span data-stu-id="39ea1-136">Using a platform or API that does not support .NET Core</span></span>

<span data-ttu-id="39ea1-137">Microsoft やサードパーティ製のプラットフォームの中には、.NET Core をサポートしないものもあります。</span><span class="sxs-lookup"><span data-stu-id="39ea1-137">Some Microsoft or third-party platforms do not support .NET Core.</span></span> <span data-ttu-id="39ea1-138">たとえば、一部の Azure サービスでは、.NET Core ではまだ使用できない SDK が提供されます。</span><span class="sxs-lookup"><span data-stu-id="39ea1-138">For example, some Azure services provide an SDK that is not yet available for consumption on .NET Core.</span></span> <span data-ttu-id="39ea1-139">すべての Azure サービスはいずれは .NET Core を使用するようになるため、これは一時的な状態です。</span><span class="sxs-lookup"><span data-stu-id="39ea1-139">This is temporary, because all Azure services will eventually use .NET Core.</span></span> <span data-ttu-id="39ea1-140">たとえば、[Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) は、2016 年 11 月 16 日にプレビューとしてリリースされましたが、現在は安定したバージョンである一般公開 (GA) になっています。</span><span class="sxs-lookup"><span data-stu-id="39ea1-140">For example, the [Azure DocumentDB SDK for .NET Core](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) was released as a preview on November 16, 2016, but it is now generally available (GA) as a stable version.</span></span>

<span data-ttu-id="39ea1-141">この間、Azure のプラットフォームまたはサービスがクライアント API で .NET Core をまだサポートしていない場合は、Azure サービスまたはクライアント SDK の同等の REST API を .NET Framework で使用できます。</span><span class="sxs-lookup"><span data-stu-id="39ea1-141">In the meantime, if any platform or service in Azure still doesn’t support .NET Core with its client API, you can use the equivalent REST API from the Azure service or the client SDK on .NET Framework.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="39ea1-142">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="39ea1-142">Additional resources</span></span>

-   <span data-ttu-id="39ea1-143">**.NET Core ガイド**
    [*https://docs.microsoft.com/dotnet/core/index*](../../../core/index.md)</span><span class="sxs-lookup"><span data-stu-id="39ea1-143">**.NET Core Guide**
[*https://docs.microsoft.com/dotnet/core/index*](../../../core/index.md)</span></span>

-   <span data-ttu-id="39ea1-144">**.NET Framework から .NET Core への移植**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](../../../core/porting/index.md)</span><span class="sxs-lookup"><span data-stu-id="39ea1-144">**Porting from .NET Framework to .NET Core**
[*https://docs.microsoft.com/dotnet/core/porting/index*](../../../core/porting/index.md)</span></span>

-   <span data-ttu-id="39ea1-145">**Docker 上の .NET Framework ガイド**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](../../../framework/docker/index.md)</span><span class="sxs-lookup"><span data-stu-id="39ea1-145">**.NET Framework on Docker Guide**
[*https://docs.microsoft.com/dotnet/framework/docker/*](../../../framework/docker/index.md)</span></span>

-   <span data-ttu-id="39ea1-146">**.NET コンポーネントの概要**
    [*https://docs.microsoft.com/dotnet/standard/components*](../../components.md)</span><span class="sxs-lookup"><span data-stu-id="39ea1-146">**.NET Components Overview**
[*https://docs.microsoft.com/dotnet/standard/components*](../../components.md)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="39ea1-147">[前へ] (net-core-container-scenarios.md) [次へ] (container-framework-choice-factors.md)</span><span class="sxs-lookup"><span data-stu-id="39ea1-147">[Previous] (net-core-container-scenarios.md) [Next] (container-framework-choice-factors.md)</span></span>
