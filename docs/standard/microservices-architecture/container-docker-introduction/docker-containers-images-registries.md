---
title: "Docker コンテナー、イメージ、およびレジストリ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker コンテナー、イメージ、およびレジストリ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="873ca-104">Docker コンテナー、イメージ、およびレジストリ</span><span class="sxs-lookup"><span data-stu-id="873ca-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="873ca-105">Docker を使用して、開発者は、コンテナー イメージにその依存関係にアプリケーションまたはサービス、およびパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="873ca-105">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="873ca-106">イメージは、アプリケーションまたはサービス構成およびその依存関係の静的な表現です。</span><span class="sxs-lookup"><span data-stu-id="873ca-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="873ca-107">アプリやサービスを実行するには、アプリのイメージは Docker ホストで実行されるコンテナーを作成するインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="873ca-107">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="873ca-108">コンテナーは、開発環境または PC で最初にテストされます。</span><span class="sxs-lookup"><span data-stu-id="873ca-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="873ca-109">開発者は、イメージのライブラリとして機能し、実稼働 orchestrators に展開する場合に必要なレジストリ内でイメージを格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="873ca-109">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="873ca-110">Docker を管理を使用してパブリック レジストリ[Docker Hub](https://hub.docker.com/); 他のベンダーは、別のイメージのコレクションのレジストリを提供します。</span><span class="sxs-lookup"><span data-stu-id="873ca-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="873ca-111">また、企業がプライベート レジストリを持つことができます独自のイメージの Docker オンプレミスです。</span><span class="sxs-lookup"><span data-stu-id="873ca-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="873ca-112">図 2-4 は、他のコンポーネントにイメージと Docker でレジストリを関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="873ca-112">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="873ca-113">ベンダーからの複数のレジストリの内容も表示されます。</span><span class="sxs-lookup"><span data-stu-id="873ca-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="873ca-114">**図 2-4**です。</span><span class="sxs-lookup"><span data-stu-id="873ca-114">**Figure 2-4**.</span></span> <span data-ttu-id="873ca-115">Docker の用語と概念の分類</span><span class="sxs-lookup"><span data-stu-id="873ca-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="873ca-116">レジストリにイメージを配置すると、フレームワーク レベルのすべての依存関係を含む、変更できない静的なアプリケーション ビットを保存できます。</span><span class="sxs-lookup"><span data-stu-id="873ca-116">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="873ca-117">それらのイメージでは、しでバージョン管理および複数の環境に配置でき、したがっては一貫性のある展開ユニットを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="873ca-117">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="873ca-118">プライベート イメージ レジストリ、ホストされているか、オンプレミスまたはクラウドでは、推奨されるときに。</span><span class="sxs-lookup"><span data-stu-id="873ca-118">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="873ca-119">画像は必要があります機密性により公開されている共有されません。</span><span class="sxs-lookup"><span data-stu-id="873ca-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="873ca-120">イメージと、選択したデプロイ環境間の最小のネットワーク待機時間にします。</span><span class="sxs-lookup"><span data-stu-id="873ca-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="873ca-121">たとえば、実稼働環境が Azure クラウドの場合は、可能性がありますする、イメージの Azure コンテナー レジストリに格納できるように、ネットワークの待機時間が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="873ca-121">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="873ca-122">同様の方法で、運用環境が、オンプレミスでの場合に、内部設置型 Docker Trusted Registry 同じローカル ネットワーク内で使用できることができます。</span><span class="sxs-lookup"><span data-stu-id="873ca-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="873ca-123">[前](docker terminology.md) [次へ] (../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="873ca-123">[Previous] (docker-terminology.md) [Next] (../net-core-net-framework-containers/index.md)</span></span>
