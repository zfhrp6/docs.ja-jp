---
title: "eShopOnContainers で DDD マイクロサービスの CQRS と CQS のアプローチを適用する"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | eShopOnContainers で DDD マイクロサービスの CQRS と CQS のアプローチを適用する"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 63e61a93aa2a162d7b48e0d423dab99dcea9d020
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a><span data-ttu-id="73134-104">eShopOnContainers で DDD マイクロサービスの CQRS と CQS のアプローチを適用する</span><span class="sxs-lookup"><span data-stu-id="73134-104">Applying CQRS and CQS approaches in a DDD microservice in eShopOnContainers</span></span>

<span data-ttu-id="73134-105">eShopOnContainers 参照アプリケーションの注文マイクロサービスの設計は、CQRS 原則に基づいています。</span><span class="sxs-lookup"><span data-stu-id="73134-105">The design of the ordering microservice at the eShopOnContainers reference application is based on CQRS principles.</span></span> <span data-ttu-id="73134-106">ただし、使用されているのは最もシンプルなアプローチ、つまり、コマンドからクエリを分離し、両方のアクションで同じデータベースを使用するというアプローチです。</span><span class="sxs-lookup"><span data-stu-id="73134-106">However, it uses the simplest approach, which is just separating the queries from the commands and using the same database for both actions.</span></span>

<span data-ttu-id="73134-107">これらのパターンの本質である重要なポイントは、クエリはべき等であるということです。つまり、システムにクエリを実行する回数にかかわらず、システムの状態が変わることはありません。トランザクション ロジック「書き込み」ドメイン モデルとは異なる「読み取り」データ モデルを使用することさえできますが、注文マイクロサービスは同一のデータベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="73134-107">The essence of those patterns, and the important point here, is that queries are idempotent: no matter how many times you query a system, the state of that system will not change You could even use a different “reads” data model than the transactional logic “writes” domain model, although the ordering microservices is using the same database.</span></span> <span data-ttu-id="73134-108">したがって、これは簡略化された CQRS アプローチです。</span><span class="sxs-lookup"><span data-stu-id="73134-108">Hence this is a simplified CQRS approach.</span></span>

<span data-ttu-id="73134-109">一方、コマンド (トランザクションとデータ更新をトリガーする) はシステムの状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="73134-109">On the other hand, commands, which trigger transactions and data updates, change state in the system.</span></span> <span data-ttu-id="73134-110">コマンドを使用する場合は、複雑さと、常に変化するビジネス ルールの扱いに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73134-110">With commands, you need to be careful when dealing with complexity and ever-changing business rules.</span></span> <span data-ttu-id="73134-111">ここで DDD の技法を適用すると、システムのモデル化を改善できます。</span><span class="sxs-lookup"><span data-stu-id="73134-111">This is the where you want to apply DDD techniques to have a better modeled system.</span></span>

<span data-ttu-id="73134-112">このガイドで示す DDD パターンを所かまわず適用すべきではありません。</span><span class="sxs-lookup"><span data-stu-id="73134-112">The DDD patterns presented in this guide should not be applied universally.</span></span> <span data-ttu-id="73134-113">これらのパターンは設計上の制約をもたらします。</span><span class="sxs-lookup"><span data-stu-id="73134-113">They introduce constraints on your design.</span></span> <span data-ttu-id="73134-114">こうした制約には、時間経過とともに品質が向上するなどの利点が伴います。システム状態を変更するコマンドや他のコードでは特にそう言えます。</span><span class="sxs-lookup"><span data-stu-id="73134-114">Those constraints provide benefits such as higher quality over time, especially in commands and other code that modifies system state.</span></span> <span data-ttu-id="73134-115">しかし、データの読み取りとクエリはこれらの制約によって複雑さが増し、利点はわずかです。</span><span class="sxs-lookup"><span data-stu-id="73134-115">However, those constraints add complexity with fewer benefits for reading and querying data.</span></span>

<span data-ttu-id="73134-116">そうしたパターンの 1 つは集計パターンです。これについては、後のセクションでさらに説明します。</span><span class="sxs-lookup"><span data-stu-id="73134-116">One such pattern is the Aggregate pattern, which we examine more in later sections.</span></span> <span data-ttu-id="73134-117">簡単に言うと、集約パターンでは、多数のドメイン オブジェクトがドメイン内で互いに持つリレーションシップの結果として、1 つの単位として処理されます。</span><span class="sxs-lookup"><span data-stu-id="73134-117">Briefly, in the Aggregate pattern, you treat many domain objects as a single unit as a result of their relationship in the domain.</span></span> <span data-ttu-id="73134-118">このパターンを採用しても、クエリに利点があるとは限りません。クエリ ロジックの複雑さが増す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73134-118">You might not always gain advantages from this pattern in queries; it can increase the complexity of query logic.</span></span> <span data-ttu-id="73134-119">読み取り専用クエリの場合、複数のオブジェクトを単一の集計として扱う利点はありません。</span><span class="sxs-lookup"><span data-stu-id="73134-119">For read-only queries, you do not get the advantages of treating multiple objects as a single Aggregate.</span></span> <span data-ttu-id="73134-120">複雑さが増すだけです。</span><span class="sxs-lookup"><span data-stu-id="73134-120">You only get the complexity.</span></span>

<span data-ttu-id="73134-121">図 9-2 に示されているように、このガイドでは、DDD パターンをマイクロ サービスのトランザクション/更新領域 (つまり、コマンドによってトリガーされる部分) にのみ使用することを提案しています。</span><span class="sxs-lookup"><span data-stu-id="73134-121">As shown in Figure 9-2, this guide suggests using DDD patterns only in the transactional/updates area of your microservice (that is, as triggered by commands).</span></span> <span data-ttu-id="73134-122">クエリはよりシンプルなアプローチに従うことができ、CQRS アプローチに従ってコマンドから分離する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73134-122">Queries can follow a simpler approach and should be separated from commands, following a CQRS approach.</span></span>

<span data-ttu-id="73134-123">「クエリ サイド」を実装する場合、EF Core、AutoMapper プロジェクション、ストアド プロシージャ、ビュー、具体化されたビュー、マイクロ ORM など本格的な ORM の多様なアプローチから選択できます。</span><span class="sxs-lookup"><span data-stu-id="73134-123">For implementing the “queries side”, you can choose between many approaches, from your full-blown ORM like EF Core, AutoMapper projections, stored procedures, views, materialized views or a micro ORM.</span></span>

<span data-ttu-id="73134-124">このガイドと eShopOnContainers (具体的には注文マイクロサービス) では、[Dapper](https://github.com/StackExchange/dapper-dot-net) のようなマイクロ ORM を使用して直接的なクエリを実装します。</span><span class="sxs-lookup"><span data-stu-id="73134-124">In this guide and in eShopOnContainers (specifically the ordering microservice) we chose to implement straight queries using a micro ORM like [Dapper](https://github.com/StackExchange/dapper-dot-net).</span></span> <span data-ttu-id="73134-125">この場合、SQL ステートメントに基づくクエリを実装でき、わずかなオーバーヘッドしかない軽量フレームワークのおかげで、最良のパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="73134-125">This lets you implement any query based on SQL statements to get the best performance, thanks to a light framework with very little overhead.</span></span>

<span data-ttu-id="73134-126">このアプローチを使用するにあたり、モデルに加える更新が原因で SQL データベースにエンティティを保存する方法に影響が及ぶ場合は、Dapper など、クエリ実行のための独立した (EF 以外の) アプローチで使用される SQL クエリにも、別途更新が必要であることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="73134-126">Note that when you use this approach, any updates to your model that impact how entities are persisted to a SQL database also need separate updates to SQL queries used by Dapper or any other separate (non-EF) approaches to querying.</span></span>

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a><span data-ttu-id="73134-127">CQRS パターンと DDD パターンは最上位のアーキテクチャではない</span><span class="sxs-lookup"><span data-stu-id="73134-127">CQRS and DDD patterns are not top-level architectures</span></span>

<span data-ttu-id="73134-128">CQRS とほとんどの DDD のパターン (DDD レイヤー、または集計を伴うドメイン モデル) はアーキテクチャ スタイルではなく、アーキテクチャ パターンに過ぎないことを理解するのは重要です。</span><span class="sxs-lookup"><span data-stu-id="73134-128">It important to understand that CQRS and most DDD patterns (like DDD layers or a domain model with aggregates) are not architectural styles, but only architecture patterns.</span></span> <span data-ttu-id="73134-129">マイクロサービス、SOA、イベント駆動型アーキテクチャ (EDA) はアーキテクチャ スタイルの例です。</span><span class="sxs-lookup"><span data-stu-id="73134-129">Microservices, SOA, and event-driven architecture (EDA) are examples of architectural styles.</span></span> <span data-ttu-id="73134-130">これらは、多くのマイクロサービスなどの多数のコンポーネントで構成されるシステムを記述します。</span><span class="sxs-lookup"><span data-stu-id="73134-130">They describe a system of many components, such as many microservices.</span></span> <span data-ttu-id="73134-131">CQRS パターンと DDD パターンは、1 つのシステムまたはコンポーネント内にあるもの (この場合は、マイクロサービス内にあるもの) を記述します。</span><span class="sxs-lookup"><span data-stu-id="73134-131">CQRS and DDD patterns describe something inside a single system or component; in this case, something inside a microservice.</span></span>

<span data-ttu-id="73134-132">境界付けられたコンテキスト (BC) が異なると、採用されるパターンも異なります。</span><span class="sxs-lookup"><span data-stu-id="73134-132">Different Bounded Contexts (BCs) will employ different patterns.</span></span> <span data-ttu-id="73134-133">それぞれ責任が異なり、異なる解決策に至ります。</span><span class="sxs-lookup"><span data-stu-id="73134-133">They have different responsibilities, and that leads to different solutions.</span></span> <span data-ttu-id="73134-134">強調する価値がある点として、至る所で同じパターンを無理に当てはめると失敗に至ります。</span><span class="sxs-lookup"><span data-stu-id="73134-134">It is worth emphasizing that forcing the same pattern everywhere leads to failure.</span></span> <span data-ttu-id="73134-135">所かまわず CQRS パターンと DDD パターンを使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="73134-135">Do not use CQRS and DDD patterns everywhere.</span></span> <span data-ttu-id="73134-136">多くのサブシステム、BC、マイクロサービスはよりシンプルであり、シンプルな CRUD サービスや別のアプローチを使うとより簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="73134-136">Many subsystems, BCs, or microservices are simpler and can be implemented more easily using simple CRUD services or using another approach.</span></span>

<span data-ttu-id="73134-137">存在するアプリケーション アーキテクチャは 1 つだけです。つまり、自分が設計しているシステムまたはエンドツーエンド アプリケーションのアーキテクチャです (たとえば、マイクロサービス アーキテクチャ)。</span><span class="sxs-lookup"><span data-stu-id="73134-137">There is only one application architecture: the architecture of the system or end-to-end application you are designing (for example, the microservices architecture).</span></span> <span data-ttu-id="73134-138">しかし、そのアプリケーション内の境界付けられているコンテキストまたはマイクロサービスのそれぞれの設計には、アーキテクチャ パターン レベルの独自のトレードオフや内部設計の決定が反映されます。</span><span class="sxs-lookup"><span data-stu-id="73134-138">However, the design of each Bounded Context or microservice within that application reflects its own tradeoffs and internal design decisions at an architecture patterns level.</span></span> <span data-ttu-id="73134-139">CQRS または DDD など同じアーキテクチャ パターンを所かまわず適用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="73134-139">Do not try to apply the same architectural patterns like CQRS or DDD everywhere.</span></span>

####  <a name="additional-resources"></a><span data-ttu-id="73134-140">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="73134-140">Additional resources</span></span>

-   <span data-ttu-id="73134-141">**Martin Fowler。CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)</span><span class="sxs-lookup"><span data-stu-id="73134-141">**Martin Fowler. CQRS**
[*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)</span></span>

-   <span data-ttu-id="73134-142">**Greg Young。CQS と CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)</span><span class="sxs-lookup"><span data-stu-id="73134-142">**Greg Young. CQS vs. CQRS**
[*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)</span></span>

-   <span data-ttu-id="73134-143">**Greg Young。CQRS ドキュメント**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)</span><span class="sxs-lookup"><span data-stu-id="73134-143">**Greg Young. CQRS Documents**
[*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)</span></span>

-   <span data-ttu-id="73134-144">**Greg Young。CQRS、タスク ベースの UI、イベント ソーシング**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)</span><span class="sxs-lookup"><span data-stu-id="73134-144">**Greg Young. CQRS, Task Based UIs and Event Sourcing**
[*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)</span></span>

-   <span data-ttu-id="73134-145">**Udi Dahan。明解化された CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span><span class="sxs-lookup"><span data-stu-id="73134-145">**Udi Dahan. Clarified CQRS**
[*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span></span>

-   <span data-ttu-id="73134-146">**CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span><span class="sxs-lookup"><span data-stu-id="73134-146">**CQRS**
[*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span></span>

-   <span data-ttu-id="73134-147">**イベント ソースシング (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)</span><span class="sxs-lookup"><span data-stu-id="73134-147">**Event-Sourcing (ES)**
[*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="73134-148">[前へ] (apply-simplified-microservice-cqrs-ddd-patterns.md) [次へ] (cqrs-microservice-reads.md)</span><span class="sxs-lookup"><span data-stu-id="73134-148">[Previous] (apply-simplified-microservice-cqrs-ddd-patterns.md) [Next] (cqrs-microservice-reads.md)</span></span>
