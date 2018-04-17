---
title: Docker コンテナー、イメージ、レジストリ
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9de37f9ee3a8fe7ce4a337fc548030b2aeadba55
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="f3c72-103">Docker コンテナー、イメージ、レジストリ</span><span class="sxs-lookup"><span data-stu-id="f3c72-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="f3c72-104">Docker を使用する場合を作成するアプリケーションまたはサービス、およびパッケージ、コンテナー イメージにその依存関係。</span><span class="sxs-lookup"><span data-stu-id="f3c72-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="f3c72-105">イメージとは、アプリケーションまたはサービスと、その構成と依存関係の静的な表現です。</span><span class="sxs-lookup"><span data-stu-id="f3c72-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="f3c72-106">アプリやサービスを実行するには、アプリのイメージは Docker ホストで実行されるコンテナーを作成するインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="f3c72-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="f3c72-107">コンテナーは、最初に開発環境または PC でテストされます。</span><span class="sxs-lookup"><span data-stu-id="f3c72-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="f3c72-108">イメージは、イメージのライブラリとして機能する、レジストリに保存します。</span><span class="sxs-lookup"><span data-stu-id="f3c72-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="f3c72-109">実稼働 orchestrators に展開する場合は、レジストリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3c72-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="f3c72-110">Docker は [Docker Hub](https://hub.docker.com/) 経由で公開レジストリを保守します。他のベンダーは、さまざまなイメージのコレクション用にレジストリを用意しています。</span><span class="sxs-lookup"><span data-stu-id="f3c72-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="f3c72-111">また、企業は自社の Docker イメージ用に非公開のレジストリをオンプレミスに持つことができます。</span><span class="sxs-lookup"><span data-stu-id="f3c72-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="f3c72-112">図 1-4 は、他のコンポーネントにイメージと Docker でレジストリを関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f3c72-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="f3c72-113">また、ベンダーから提供される複数のレジストリも示しています。</span><span class="sxs-lookup"><span data-stu-id="f3c72-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="f3c72-114">図 1-4: 分類の Docker の用語と概念</span><span class="sxs-lookup"><span data-stu-id="f3c72-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="f3c72-115">レジストリ内のイメージを配置することで、静的と変更できないアプリケーション ビット、その依存関係、フレームワーク レベルのすべてを含むを格納できます。</span><span class="sxs-lookup"><span data-stu-id="f3c72-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="f3c72-116">バージョン管理でき、複数の環境でイメージを展開し、したがっては一貫性のある展開ユニットを提供します。</span><span class="sxs-lookup"><span data-stu-id="f3c72-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="f3c72-117">プライベート イメージ レジストリは、オンプレミスでホストされているか、クラウドでは、次の状況に推奨されます。</span><span class="sxs-lookup"><span data-stu-id="f3c72-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="f3c72-118">機密保持のためにイメージを一般公開して共有することができない場合。</span><span class="sxs-lookup"><span data-stu-id="f3c72-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="f3c72-119">イメージと選択した展開環境間のネットワーク待機時間を最小限に抑えたい場合。</span><span class="sxs-lookup"><span data-stu-id="f3c72-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="f3c72-120">たとえば、実稼働環境が Azure の場合は、可能性がありますする、イメージの Azure コンテナー レジストリに格納できるように、ネットワークの待機時間が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="f3c72-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="f3c72-121">同様に、実稼働環境がオンプレミスの場合は、同じローカル ネットワーク内でオンプレミスの Docker Trusted Registry を使用できるようにする方法があります。</span><span class="sxs-lookup"><span data-stu-id="f3c72-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f3c72-122">[前] (docker terminology.md) [次へ] (Docker-アプリケーションのライフ サイクル/index.md)</span><span class="sxs-lookup"><span data-stu-id="f3c72-122">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>
