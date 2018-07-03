---
title: マイクロサービス アプリケーション レイヤーと Web API を設計する
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | マイクロサービス アプリケーション レイヤーと Web API を設計する'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: e5c7e0acb0496aebce4d9cbe8cb51ced0c7166a2
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106607"
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="b6aaf-103">マイクロサービス アプリケーション レイヤーと Web API を設計する</span><span class="sxs-lookup"><span data-stu-id="b6aaf-103">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="b6aaf-104">SOLID の原則と依存関係の挿入を使用する</span><span class="sxs-lookup"><span data-stu-id="b6aaf-104">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="b6aaf-105">SOLID の原則は、最新のミッション クリティカル アプリケーション (DDD のパターンを使用したマイクロサービスの開発など) で使用する重要な技法です。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="b6aaf-106">SOLID は、次の 5 つの基本原則をグループ化する頭文字で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-106">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="b6aaf-107">単一責任 (Single Responsibility) の原則</span><span class="sxs-lookup"><span data-stu-id="b6aaf-107">Single Responsibility principle</span></span>

-   <span data-ttu-id="b6aaf-108">開放/閉鎖 (Open/closed) の原則</span><span class="sxs-lookup"><span data-stu-id="b6aaf-108">Open/closed principle</span></span>

-   <span data-ttu-id="b6aaf-109">リスコフの置換 (Liskov substitution) 原則</span><span class="sxs-lookup"><span data-stu-id="b6aaf-109">Liskov substitution principle</span></span>

-   <span data-ttu-id="b6aaf-110">インターフェイス分離 (Interface Segregation) の原則</span><span class="sxs-lookup"><span data-stu-id="b6aaf-110">Interface Segregation principle</span></span>

-   <span data-ttu-id="b6aaf-111">依存関係逆転 (Dependency Inversion) の原則</span><span class="sxs-lookup"><span data-stu-id="b6aaf-111">Dependency Inversion principle</span></span>

<span data-ttu-id="b6aaf-112">SOLID はむしろ、アプリケーションまたはマイクロサービス内部レイヤーの設計方法と、それらの間の依存関係の分離方法について述べています。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="b6aaf-113">ドメインには無関係ですが、アプリケーションの技術的な設計には関係しています。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="b6aaf-114">最後の原則、つまり依存関係逆転 (DI) 原則に従って、インフラストラクチャ レイヤーを他のレイヤーから分離できます。それにより、DDD レイヤーの優れた分離実装が可能になります。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-114">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="b6aaf-115">DI は、依存関係逆転原則を実装する 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-115">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="b6aaf-116">オブジェクトとその依存関係の間の疎結合を実現するための手法です。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="b6aaf-117">クラスがそのアクションを実行するために必要なオブジェクトは、コラボレーターを直接インスタンス化したり、静的参照を使ったりするのではなく、クラスに提供 (または「挿入」) されます。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-117">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="b6aaf-118">ほとんどの場合、クラスはコンストラクターを使って依存関係を宣言することで、明示的な依存関係の原則に従うことができます。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="b6aaf-119">通常、DI は特定の制御の反転 (Inversion of Control: IoC) コンテナーに基づきます。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-119">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="b6aaf-120">ASP.NET Core には簡単な組み込み IoC コンテナーが備わっていますが、Autofac や Ninject などのお気に入りの IoC コンテナーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="b6aaf-121">SOLID の原則に従うことで、クラスは必然的に小さく、十分に考慮された、簡単にテストできるものになる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="b6aaf-122">しかし、クラスに挿入されている依存関係が多すぎるかどうかはどのように把握できますか。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="b6aaf-123">コンストラクターによって DI を使用している場合、コンストラクターのパラメーター数を確認するだけで簡単にわかります。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="b6aaf-124">依存関係が多すぎる場合、一般に、クラスで行おうとしていることが多すぎるサイン ([コードのにおい](http://deviq.com/code-smells/)) であり、単一責任の原則に違反する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-124">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="b6aaf-125">SOLID の詳細を取り上げた別のガイドがあります。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="b6aaf-126">そのため、このガイドで必要となるのは、これらのトピックに関する最小限の知識のみです。</span><span class="sxs-lookup"><span data-stu-id="b6aaf-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b6aaf-127">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="b6aaf-127">Additional resources</span></span>

-   <span data-ttu-id="b6aaf-128">**SOLID: 基本的な OOP 原則**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="b6aaf-128">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="b6aaf-129">**制御の反転コンテナーと依存関係の挿入パターン**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="b6aaf-129">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="b6aaf-130">**Steve Smith。new は接着剤である**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="b6aaf-130">**Steve Smith. New is Glue**
[*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b6aaf-131">[前へ](nosql-database-persistence-infrastructure.md)
[次へ](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="b6aaf-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
