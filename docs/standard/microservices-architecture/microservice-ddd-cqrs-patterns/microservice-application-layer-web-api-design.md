---
title: "マイクロ サービスのアプリケーション層および Web API を設計します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |マイクロ サービスのアプリケーション層および Web API を設計します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7509b470a30005dd48fa88eefa91f7ed241e4e09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="5acb0-104">マイクロ サービスのアプリケーション層および Web API を設計します。</span><span class="sxs-lookup"><span data-stu-id="5acb0-104">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="5acb0-105">純色の基本原則と依存関係の挿入を使用します。</span><span class="sxs-lookup"><span data-stu-id="5acb0-105">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="5acb0-106">純色の原則は、DDD パターンを持つマイクロ サービスの開発など、モダンでミッション クリティカルなアプリケーションで使用する重要な手法です。</span><span class="sxs-lookup"><span data-stu-id="5acb0-106">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="5acb0-107">実線は頭字語を 5 つのグループの基本原則です。</span><span class="sxs-lookup"><span data-stu-id="5acb0-107">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="5acb0-108">1 つの責任の原則</span><span class="sxs-lookup"><span data-stu-id="5acb0-108">Single Responsibility principle</span></span>

-   <span data-ttu-id="5acb0-109">開く/閉じる原則</span><span class="sxs-lookup"><span data-stu-id="5acb0-109">Open/closed principle</span></span>

-   <span data-ttu-id="5acb0-110">リスコフ置換原則</span><span class="sxs-lookup"><span data-stu-id="5acb0-110">Liskov substitution principle</span></span>

-   <span data-ttu-id="5acb0-111">分離の逆転原則</span><span class="sxs-lookup"><span data-stu-id="5acb0-111">Inversion Segregation principle</span></span>

-   <span data-ttu-id="5acb0-112">依存関係の逆転原則</span><span class="sxs-lookup"><span data-stu-id="5acb0-112">Dependency Inversion principle</span></span>

<span data-ttu-id="5acb0-113">ソリッドは、およびそれらの間の依存関係を分離アプリケーションまたはマイクロ サービス内部レイヤーをデザインする方法に関する詳細があります。</span><span class="sxs-lookup"><span data-stu-id="5acb0-113">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="5acb0-114">ドメインは、アプリケーションの技術的なデザインには無関係です。</span><span class="sxs-lookup"><span data-stu-id="5acb0-114">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="5acb0-115">最後の原則に従って、依存関係の逆転 (DI) の原則に従ってには、これによりより分離の実装 DDD レイヤー、レイヤーの残りの部分から、インフラストラクチャ レイヤーを分離することができます。</span><span class="sxs-lookup"><span data-stu-id="5acb0-115">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="5acb0-116">DI は、依存関係の反転の原則を実装する 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="5acb0-116">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="5acb0-117">これは、オブジェクトとその依存関係間の疎結合を実現するための手法です。</span><span class="sxs-lookup"><span data-stu-id="5acb0-117">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="5acb0-118">、の共同作業者を直接インスタンス化または静的参照を使用して、ではなく、オブジェクト クラスがそのアクションを実行する必要があるに提供される (または「に挿入された」) クラス。</span><span class="sxs-lookup"><span data-stu-id="5acb0-118">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="5acb0-119">ほとんどの場合、クラスは、明示的な依存関係の原則に従うように、コンス トラクターを使用して、その依存関係を宣言します。</span><span class="sxs-lookup"><span data-stu-id="5acb0-119">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="5acb0-120">DI は、通常、特定の制御の反転 (IoC) コンテナーに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5acb0-120">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="5acb0-121">ASP.NET Core の単純な組み込みの IoC コンテナーを提供しますが、Autofac または Ninject と同様に、お気に入り IoC コンテナーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5acb0-121">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="5acb0-122">純色の原則に従うと、によって、クラス傾向があります必然的に小さく、十分に考慮された、簡単にテストします。</span><span class="sxs-lookup"><span data-stu-id="5acb0-122">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="5acb0-123">どのように知ることができる多すぎる依存関係が、クラスに挿入されているかどうかですか。</span><span class="sxs-lookup"><span data-stu-id="5acb0-123">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="5acb0-124">DI コンス トラクターを使用する場合は、簡単に、コンス トラクターのパラメーターの数を調べるだけで検出されるがあります。</span><span class="sxs-lookup"><span data-stu-id="5acb0-124">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="5acb0-125">多すぎる依存関係がある場合は、これは、記号、通常 (、[コードの匂い](http://deviq.com/code-smells/)) クラスが多すぎる、実行しようとしは単一の責任の原則に違反する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5acb0-125">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="5acb0-126">実線を詳しく説明する他のガイドがかかります。</span><span class="sxs-lookup"><span data-stu-id="5acb0-126">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="5acb0-127">そのため、このガイドでは、するためにこれらのトピックの最小限のナレッジだけが必要です。</span><span class="sxs-lookup"><span data-stu-id="5acb0-127">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="5acb0-128">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="5acb0-128">Additional resources</span></span>

-   <span data-ttu-id="5acb0-129">**実線: 基本的な OOP 原則**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="5acb0-129">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="5acb0-130">**コントロールのコンテナーと依存性の注入パターンの反転**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="5acb0-130">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="5acb0-131">**Steve Smith です。新しいはグルー**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="5acb0-131">**Steve Smith. New is Glue**
[*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5acb0-132">[前](nosql-データベースの永続化-infrastructure.md) [次へ] (microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="5acb0-132">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span></span>
