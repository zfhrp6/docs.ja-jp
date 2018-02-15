---
title: "Docker コンテナー、イメージ、およびレジストリ"
description: "Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0cccead8833c63f19b359f830f555e7ff31daa1a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="c609f-104">Docker コンテナー、イメージ、およびレジストリ</span><span class="sxs-lookup"><span data-stu-id="c609f-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="c609f-105">Docker を使用する場合を作成するアプリケーションまたはサービス、およびパッケージ、コンテナー イメージにその依存関係。</span><span class="sxs-lookup"><span data-stu-id="c609f-105">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="c609f-106">イメージは、アプリケーションまたはサービス構成およびその依存関係の静的な表現です。</span><span class="sxs-lookup"><span data-stu-id="c609f-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="c609f-107">アプリやサービスを実行するには、アプリのイメージは Docker ホストで実行されるコンテナーを作成するインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="c609f-107">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="c609f-108">コンテナーは、開発環境または PC で最初にテストされます。</span><span class="sxs-lookup"><span data-stu-id="c609f-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="c609f-109">イメージは、イメージのライブラリとして機能する、レジストリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c609f-109">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="c609f-110">実稼働 orchestrators に展開する場合は、レジストリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c609f-110">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="c609f-111">Docker を管理を使用してパブリック レジストリ[Docker Hub](https://hub.docker.com/); 他のベンダーは、別のイメージのコレクションのレジストリを提供します。</span><span class="sxs-lookup"><span data-stu-id="c609f-111">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="c609f-112">また、企業がプライベート レジストリを持つことができます独自のイメージの Docker オンプレミスです。</span><span class="sxs-lookup"><span data-stu-id="c609f-112">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="c609f-113">図 1-4 は、他のコンポーネントにイメージと Docker でレジストリを関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c609f-113">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="c609f-114">ベンダーからの複数のレジストリの内容も表示されます。</span><span class="sxs-lookup"><span data-stu-id="c609f-114">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="c609f-115">図 1-4: 分類の Docker の用語と概念</span><span class="sxs-lookup"><span data-stu-id="c609f-115">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="c609f-116">レジストリ内のイメージを配置することで、静的と変更できないアプリケーション ビット、その依存関係、フレームワーク レベルのすべてを含むを格納できます。</span><span class="sxs-lookup"><span data-stu-id="c609f-116">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="c609f-117">バージョン管理でき、複数の環境でイメージを展開し、したがっては一貫性のある展開ユニットを提供します。</span><span class="sxs-lookup"><span data-stu-id="c609f-117">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="c609f-118">プライベート イメージ レジストリは、オンプレミスでホストされているか、クラウドでは、次の状況に推奨されます。</span><span class="sxs-lookup"><span data-stu-id="c609f-118">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="c609f-119">画像は必要があります機密性により公開されている共有されません。</span><span class="sxs-lookup"><span data-stu-id="c609f-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="c609f-120">イメージと、選択したデプロイ環境間の最小のネットワーク待機時間にします。</span><span class="sxs-lookup"><span data-stu-id="c609f-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="c609f-121">たとえば、実稼働環境が Azure の場合は、可能性がありますする、イメージの Azure コンテナー レジストリに格納できるように、ネットワークの待機時間が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="c609f-121">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="c609f-122">同様の方法で、運用環境が、オンプレミスでの場合に、内部設置型 Docker Trusted Registry 同じローカル ネットワーク内で使用できることができます。</span><span class="sxs-lookup"><span data-stu-id="c609f-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="c609f-123">[前](docker terminology.md) [次へ] (Docker-アプリケーションのライフ サイクル/index.md)</span><span class="sxs-lookup"><span data-stu-id="c609f-123">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>
