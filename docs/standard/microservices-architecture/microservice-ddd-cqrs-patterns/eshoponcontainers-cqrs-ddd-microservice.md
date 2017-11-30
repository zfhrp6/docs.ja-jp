---
title: "EShopOnContainers で DDD マイクロ サービスに適用する CQRS および CQS のアプローチ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |EShopOnContainers で DDD マイクロ サービスに適用する CQRS および CQS のアプローチ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a2c4429a75ca47d4fbcde868b95e76bc65ea2bef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a><span data-ttu-id="84d52-104">EShopOnContainers で DDD マイクロ サービスに適用する CQRS および CQS のアプローチ</span><span class="sxs-lookup"><span data-stu-id="84d52-104">Applying CQRS and CQS approaches in a DDD microservice in eShopOnContainers</span></span>

<span data-ttu-id="84d52-105">EShopOnContainers 参照アプリケーションの順序付けマイクロ サービスの設計は、CQRS の原則に基づいています。</span><span class="sxs-lookup"><span data-stu-id="84d52-105">The design of the ordering microservice at the eShopOnContainers reference application is based on CQRS principles.</span></span> <span data-ttu-id="84d52-106">ただし、だけコマンドからのクエリを分離することと同じデータベースの操作の両方を使用して、最も単純なアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="84d52-106">However, it uses the simplest approach, which is just separating the queries from the commands and using the same database for both actions.</span></span>

<span data-ttu-id="84d52-107">これらのパターンと重要な点をここでは、重要な部分はクエリがべき等である: 何回かシステムでは、そのシステムの状態のクエリは変更されませんに関係なく、トランザクション ロジック「書き込み」よりも別の「読み取り」データ モデルを使用する可能性がありますもドメインは、順序付け microservices が同じデータベースを使用するモデルします。</span><span class="sxs-lookup"><span data-stu-id="84d52-107">The essence of those patterns, and the important point here, is that queries are idempotent: no matter how many times you query a system, the state of that system will not change You could even use a different “reads” data model than the transactional logic “writes” domain model, although the ordering microservices is using the same database.</span></span> <span data-ttu-id="84d52-108">そのため、これは、簡略化した CQRS 方法です。</span><span class="sxs-lookup"><span data-stu-id="84d52-108">Hence this is a simplified CQRS approach.</span></span>

<span data-ttu-id="84d52-109">その一方で、トランザクションおよびデータの更新をトリガーするには、コマンドは、システムの状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="84d52-109">On the other hand, commands, which trigger transactions and data updates, change state in the system.</span></span> <span data-ttu-id="84d52-110">コマンドを使用する場合に注意する必要があります。 複雑さと常に変化するビジネス ルールを処理します。</span><span class="sxs-lookup"><span data-stu-id="84d52-110">With commands, you need to be careful when dealing with complexity and ever-changing business rules.</span></span> <span data-ttu-id="84d52-111">これは、where をモデル化されたシステムがより適切に DDD 手法を適用します。</span><span class="sxs-lookup"><span data-stu-id="84d52-111">This is the where you want to apply DDD techniques to have a better modeled system.</span></span>

<span data-ttu-id="84d52-112">このガイドで紹介 DDD パターンを広く適用いない必要があります。</span><span class="sxs-lookup"><span data-stu-id="84d52-112">The DDD patterns presented in this guide should not be applied universally.</span></span> <span data-ttu-id="84d52-113">設計上の制約を導入します。</span><span class="sxs-lookup"><span data-stu-id="84d52-113">They introduce constraints on your design.</span></span> <span data-ttu-id="84d52-114">これらの制約では、随時、特にのコマンドやその他のシステム状態を変更するコード品質の向上などの利点があります。</span><span class="sxs-lookup"><span data-stu-id="84d52-114">Those constraints provide benefits such as higher quality over time, especially in commands and other code that modifies system state.</span></span> <span data-ttu-id="84d52-115">ただし、これらの制約は、読み取りやデータを照会する以下のメリットがありますの複雑さを追加します。</span><span class="sxs-lookup"><span data-stu-id="84d52-115">However, those constraints add complexity with fewer benefits for reading and querying data.</span></span>

<span data-ttu-id="84d52-116">このような 1 つのパターンが、集計のパターンは、以降のセクションで詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="84d52-116">One such pattern is the Aggregate pattern, which we examine more in later sections.</span></span> <span data-ttu-id="84d52-117">簡単に、パターンでは、集計は、ドメイン内の関係の結果として 1 つの単位として多くのドメイン オブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="84d52-117">Briefly, in the Aggregate pattern, you treat many domain objects as a single unit as a result of their relationship in the domain.</span></span> <span data-ttu-id="84d52-118">クエリでは、このパターンから利点を常に利用可能性がありますできません。クエリ ロジックの複雑さに増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="84d52-118">You might not always gain advantages from this pattern in queries; it can increase the complexity of query logic.</span></span> <span data-ttu-id="84d52-119">読み取り専用のクエリでは、複数のオブジェクトを 1 つの集計として扱うことの利点は取得できません。</span><span class="sxs-lookup"><span data-stu-id="84d52-119">For read-only queries, you do not get the advantages of treating multiple objects as a single Aggregate.</span></span> <span data-ttu-id="84d52-120">のみ、複雑さを取得します。</span><span class="sxs-lookup"><span data-stu-id="84d52-120">You only get the complexity.</span></span>

<span data-ttu-id="84d52-121">図 9-2 に示すように、このガイドは、マイクロ サービスのトランザクション/更新領域にのみ (つまり、コマンドによってトリガーされる) と DDD パターンを使用してを提案します。</span><span class="sxs-lookup"><span data-stu-id="84d52-121">As shown in Figure 9-2, this guide suggests using DDD patterns only in the transactional/updates area of your microservice (that is, as triggered by commands).</span></span> <span data-ttu-id="84d52-122">クエリでは、簡単な方法は、および、CQRS 方法に従えば、コマンドから区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="84d52-122">Queries can follow a simpler approach and should be separated from commands, following a CQRS approach.</span></span>

<span data-ttu-id="84d52-123">「クエリ側」を実装するための EF コア、AutoMapper プロジェクション、ストアド プロシージャ、ビュー、具体化されたビューまたはマイクロ ORM などの本格的な ORM からさまざまな方法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="84d52-123">For implementing the “queries side”, you can choose between many approaches, from your full-blown ORM like EF Core, AutoMapper projections, stored procedures, views, materialized views or a micro ORM.</span></span>

<span data-ttu-id="84d52-124">このガイドでと選びました。 マイクロを使用した直線のクエリを実装する eShopOnContainers (具体的には、順序付けマイクロ サービス) の ORM のような[Dapper](https://github.com/StackExchange/dapper-dot-net)です。</span><span class="sxs-lookup"><span data-stu-id="84d52-124">In this guide and in eShopOnContainers (specifically the ordering microservice) we chose to implement straight queries using a micro ORM like [Dapper](https://github.com/StackExchange/dapper-dot-net).</span></span> <span data-ttu-id="84d52-125">これにより、最適なパフォーマンスを非常にわずかなオーバーヘッド明るい framework 感謝を取得する SQL ステートメントに基づいて任意のクエリを実装できます。</span><span class="sxs-lookup"><span data-stu-id="84d52-125">This lets you implement any query based on SQL statements to get the best performance, thanks to a light framework with very little overhead.</span></span>

<span data-ttu-id="84d52-126">このアプローチを使用するときに SQL データベースへのエンティティの保存方法に影響するモデルの更新も必要があります Dapper またはクエリを実行する、他の独立した (非 EF) アプローチによって使用される SQL クエリを個別の更新プログラムに注意してください。</span><span class="sxs-lookup"><span data-stu-id="84d52-126">Note that when you use this approach, any updates to your model that impact how entities are persisted to a SQL database also need separate updates to SQL queries used by Dapper or any other separate (non-EF) approaches to querying.</span></span>

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a><span data-ttu-id="84d52-127">CQRS と DDD パターンは最上位レベル アーキテクチャではありません。</span><span class="sxs-lookup"><span data-stu-id="84d52-127">CQRS and DDD patterns are not top-level architectures</span></span>

<span data-ttu-id="84d52-128">その CQRS および (DDD レイヤーやなどの集計にドメイン モデル) のほとんどの DDD パターンを理解することが重要はないアーキテクチャのスタイルはアーキテクチャ パターンのみです。</span><span class="sxs-lookup"><span data-stu-id="84d52-128">It important to understand that CQRS and most DDD patterns (like DDD layers or a domain model with aggregates) are not architectural styles, but only architecture patterns.</span></span> <span data-ttu-id="84d52-129">Microservices、SOA、およびイベント ドリブンのアーキテクチャ (EDA) は、アーキテクチャのスタイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="84d52-129">Microservices, SOA, and event-driven architecture (EDA) are examples of architectural styles.</span></span> <span data-ttu-id="84d52-130">これらには、多くの microservices など、多くのコンポーネントのシステムがについて説明します。</span><span class="sxs-lookup"><span data-stu-id="84d52-130">They describe a system of many components, such as many microservices.</span></span> <span data-ttu-id="84d52-131">CQRS と DDD パターンが 1 つのシステムまたはコンポーネントの内部をについて説明します。ここでは、マイクロ サービス内で何か。</span><span class="sxs-lookup"><span data-stu-id="84d52-131">CQRS and DDD patterns describe something inside a single system or component; in this case, something inside a microservice.</span></span>

<span data-ttu-id="84d52-132">異なる範囲指定されたコンテキスト (BCs) は、さまざまなパターンを採用します。</span><span class="sxs-lookup"><span data-stu-id="84d52-132">Different Bounded Contexts (BCs) will employ different patterns.</span></span> <span data-ttu-id="84d52-133">異なる役割が付いており、さまざまなソリューションにつながります。</span><span class="sxs-lookup"><span data-stu-id="84d52-133">They have different responsibilities, and that leads to different solutions.</span></span> <span data-ttu-id="84d52-134">エラーにつながるどこからでも同じパターンを強制する強調しておきます。</span><span class="sxs-lookup"><span data-stu-id="84d52-134">It is worth emphasizing that forcing the same pattern everywhere leads to failure.</span></span> <span data-ttu-id="84d52-135">どこからでも CQRS と DDD パターンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="84d52-135">Do not use CQRS and DDD patterns everywhere.</span></span> <span data-ttu-id="84d52-136">多くのサブシステム、BCs、microservices は簡単や単純な CRUD サービスを使用してまたは別のアプローチを使用してより簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="84d52-136">Many subsystems, BCs, or microservices are simpler and can be implemented more easily using simple CRUD services or using another approach.</span></span>

<span data-ttu-id="84d52-137">1 つだけのアプリケーションのアーキテクチャがある: (microservices アーキテクチャなど) の設計は、システムまたはエンド ツー エンドのアプリケーションのアーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="84d52-137">There is only one application architecture: the architecture of the system or end-to-end application you are designing (for example, the microservices architecture).</span></span> <span data-ttu-id="84d52-138">ただし、各範囲指定されたコンテキスト、またはそのアプリケーション内のマイクロ サービスの設計には、独自のトレードオフとアーキテクチャ パターン レベルでの内部設計に関する決定事項が反映されます。</span><span class="sxs-lookup"><span data-stu-id="84d52-138">However, the design of each Bounded Context or microservice within that application reflects its own tradeoffs and internal design decisions at an architecture patterns level.</span></span> <span data-ttu-id="84d52-139">同じアーキテクチャ パターン CQRS または DDD のようにすべての場所を適用しないでください。</span><span class="sxs-lookup"><span data-stu-id="84d52-139">Do not try to apply the same architectural patterns like CQRS or DDD everywhere.</span></span>

####  <a name="additional-resources"></a><span data-ttu-id="84d52-140">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="84d52-140">Additional resources</span></span>

-   <span data-ttu-id="84d52-141">**Martin Fowler。CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)</span><span class="sxs-lookup"><span data-stu-id="84d52-141">**Martin Fowler. CQRS**
[*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)</span></span>

-   <span data-ttu-id="84d52-142">**Greg Young です。CQS vs です。CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)</span><span class="sxs-lookup"><span data-stu-id="84d52-142">**Greg Young. CQS vs. CQRS**
[*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)</span></span>

-   <span data-ttu-id="84d52-143">**Greg Young です。CQRS ドキュメント**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)</span><span class="sxs-lookup"><span data-stu-id="84d52-143">**Greg Young. CQRS Documents**
[*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)</span></span>

-   <span data-ttu-id="84d52-144">**Greg Young です。CQRS、タスク ベースの Ui とイベントのソースとして**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)</span><span class="sxs-lookup"><span data-stu-id="84d52-144">**Greg Young. CQRS, Task Based UIs and Event Sourcing**
[*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)</span></span>

-   <span data-ttu-id="84d52-145">**Udi Dahan です。CQRS が明確にされました**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span><span class="sxs-lookup"><span data-stu-id="84d52-145">**Udi Dahan. Clarified CQRS**
[*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span></span>

-   <span data-ttu-id="84d52-146">**CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span><span class="sxs-lookup"><span data-stu-id="84d52-146">**CQRS**
[*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)</span></span>

-   <span data-ttu-id="84d52-147">**イベント ソース (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)</span><span class="sxs-lookup"><span data-stu-id="84d52-147">**Event-Sourcing (ES)**
[*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="84d52-148">[前](apply-simplified-microservice-cqrs-ddd-patterns.md) [次へ] (cqrs マイクロ サービス reads.md)</span><span class="sxs-lookup"><span data-stu-id="84d52-148">[Previous] (apply-simplified-microservice-cqrs-ddd-patterns.md) [Next] (cqrs-microservice-reads.md)</span></span>
