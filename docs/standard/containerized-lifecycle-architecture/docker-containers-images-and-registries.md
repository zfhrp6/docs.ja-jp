---
title: Docker コンテナー、イメージ、レジストリ
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: ff5a1f3e4b09ac9f7ea600d3f127523b96fcce55
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106364"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="2a674-103">Docker コンテナー、イメージ、レジストリ</span><span class="sxs-lookup"><span data-stu-id="2a674-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="2a674-104">Docker を使用する場合を作成するアプリケーションまたはサービス、およびパッケージ、コンテナー イメージにその依存関係。</span><span class="sxs-lookup"><span data-stu-id="2a674-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="2a674-105">イメージとは、アプリケーションまたはサービスと、その構成と依存関係の静的な表現です。</span><span class="sxs-lookup"><span data-stu-id="2a674-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="2a674-106">アプリやサービスを実行するには、アプリのイメージは Docker ホストで実行されるコンテナーを作成するインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="2a674-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="2a674-107">コンテナーは、最初に開発環境または PC でテストされます。</span><span class="sxs-lookup"><span data-stu-id="2a674-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="2a674-108">イメージは、イメージのライブラリとして機能する、レジストリに保存します。</span><span class="sxs-lookup"><span data-stu-id="2a674-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="2a674-109">実稼働 orchestrators に展開する場合は、レジストリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a674-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="2a674-110">Docker は [Docker Hub](https://hub.docker.com/) 経由で公開レジストリを保守します。他のベンダーは、さまざまなイメージのコレクション用にレジストリを用意しています。</span><span class="sxs-lookup"><span data-stu-id="2a674-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="2a674-111">また、企業は自社の Docker イメージ用に非公開のレジストリをオンプレミスに持つことができます。</span><span class="sxs-lookup"><span data-stu-id="2a674-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="2a674-112">図 1-4 は、他のコンポーネントにイメージと Docker でレジストリを関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2a674-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="2a674-113">また、ベンダーから提供される複数のレジストリも示しています。</span><span class="sxs-lookup"><span data-stu-id="2a674-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="2a674-114">図 1-4: 分類の Docker の用語と概念</span><span class="sxs-lookup"><span data-stu-id="2a674-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="2a674-115">レジストリ内のイメージを配置することで、静的と変更できないアプリケーション ビット、その依存関係、フレームワーク レベルのすべてを含むを格納できます。</span><span class="sxs-lookup"><span data-stu-id="2a674-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="2a674-116">バージョン管理でき、複数の環境でイメージを展開し、したがっては一貫性のある展開ユニットを提供します。</span><span class="sxs-lookup"><span data-stu-id="2a674-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="2a674-117">プライベート イメージ レジストリは、オンプレミスでホストされているか、クラウドでは、次の状況に推奨されます。</span><span class="sxs-lookup"><span data-stu-id="2a674-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="2a674-118">機密保持のためにイメージを一般公開して共有することができない場合。</span><span class="sxs-lookup"><span data-stu-id="2a674-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="2a674-119">イメージと選択した展開環境間のネットワーク待機時間を最小限に抑えたい場合。</span><span class="sxs-lookup"><span data-stu-id="2a674-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="2a674-120">たとえば、実稼働環境が Azure の場合は、可能性がありますする、イメージの Azure コンテナー レジストリに格納できるように、ネットワークの待機時間が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="2a674-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="2a674-121">同様に、実稼働環境がオンプレミスの場合は、同じローカル ネットワーク内でオンプレミスの Docker Trusted Registry を使用できるようにする方法があります。</span><span class="sxs-lookup"><span data-stu-id="2a674-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="2a674-122">[前へ](docker-terminology.md)
[次へ](Docker-application-lifecycle/index.md)</span><span class="sxs-lookup"><span data-stu-id="2a674-122">[Previous](docker-terminology.md)
[Next](Docker-application-lifecycle/index.md)</span></span>
