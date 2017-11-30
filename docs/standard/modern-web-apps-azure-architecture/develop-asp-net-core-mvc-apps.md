---
title: "ASP.NET Core MVC アプリの開発"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |ASP.NET Core MVC アプリの開発"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 54e7ed6fff9ac709e411d0ac1e345c63fd753201
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="b978e-103">ASP.NET Core MVC アプリを開発します。</span><span class="sxs-lookup"><span data-stu-id="b978e-103">Develop ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="b978e-104">"重要ではありませんが、正しく理解する最初の時間です。</span><span class="sxs-lookup"><span data-stu-id="b978e-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="b978e-105">これはさせるために、前回の非常に重要です。"</span><span class="sxs-lookup"><span data-stu-id="b978e-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="b978e-106">_-Andrew 狩猟と David Thomas_</span><span class="sxs-lookup"><span data-stu-id="b978e-106">_- Andrew Hunt and David Thomas_</span></span>

## <a name="summary"></a><span data-ttu-id="b978e-107">概要</span><span class="sxs-lookup"><span data-stu-id="b978e-107">Summary</span></span>

<span data-ttu-id="b978e-108">ASP.NET Core は、最新のクラウドに最適化された web アプリケーションを構築するためのプラットフォーム間、オープン ソース フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="b978e-108">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="b978e-109">ASP.NET Core アプリケーションは、軽量なテストの容易性と保守容易性の向上で有効にすると、依存関係の挿入の組み込みサポートを備えた、モジュール型です。</span><span class="sxs-lookup"><span data-stu-id="b978e-109">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling in greater testability and maintainability.</span></span> <span data-ttu-id="b978e-110">MVC で、ビュー ベースのアプリだけでなく最新の web Api の構築をサポートするには、組み合わせる ASP.NET Core は、エンタープライズ web アプリケーションのビルドに使用する強力なフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="b978e-110">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="b978e-111">応答への要求のマッピング</span><span class="sxs-lookup"><span data-stu-id="b978e-111">Mapping Requests to Responses</span></span>

<span data-ttu-id="b978e-112">中心には、ASP.NET Core アプリケーションは、発信応答を受信した要求をマップします。</span><span class="sxs-lookup"><span data-stu-id="b978e-112">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="b978e-113">低レベルでミドルウェア、これし、可能性がありますがカスタム ミドルウェアののみで構成される単純な ASP.NET Core アプリケーションと microservices です。</span><span class="sxs-lookup"><span data-stu-id="b978e-113">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="b978e-114">ASP.NET Core MVC を使用するときに使用できるやや高度のレベルでの観点で考える*ルート*、*コント ローラー*、および*アクション*です。</span><span class="sxs-lookup"><span data-stu-id="b978e-114">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of *routes*, *controllers*, and *actions*.</span></span> <span data-ttu-id="b978e-115">アプリケーションのルーティング テーブルと各着信要求を比較し、一致するルートが見つかった場合、関連付けられたアクション (コント ローラーに属する) メソッドが要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="b978e-115">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="b978e-116">一致するルートが見つからない場合は、(この場合、NotFound 結果を返す) をエラー ハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-116">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="b978e-117">ASP.NET Core MVC アプリには、従来のルート、属性のルート、またはその両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-117">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="b978e-118">従来のルートがルーティングを指定する、コードで定義されている*規則*のような構文を使用して、次の例。</span><span class="sxs-lookup"><span data-stu-id="b978e-118">Conventional routes are defined in code, specifying routing *conventions* using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="b978e-119">この例では"default"をという名前のルートがルーティング テーブルに追加されました。</span><span class="sxs-lookup"><span data-stu-id="b978e-119">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="b978e-120">定義のプレース ホルダーでルート テンプレート*コント ローラー*、*アクション*、および*id*です。コント ローラーとアクションのプレース ホルダーは、指定された既定値を持つ (「ホーム」と"Index"それぞれ)、id プレース ホルダーは省略可能 (のとなります。 したがって、、"?"を適用)。</span><span class="sxs-lookup"><span data-stu-id="b978e-120">It defines a route template with placeholders for *controller*, *action*, and *id*. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="b978e-121">規約ここで定義された状態は、要求の最初の部分と一致する 2 番目の部分には、アクション、コント ローラーの名前とし、必要に応じて、3 番目の部分を表す id パラメーター。</span><span class="sxs-lookup"><span data-stu-id="b978e-121">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="b978e-122">従来のルートは通常スタートアップ クラスのメソッドで、構成など、アプリケーションを 1 か所に定義されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-122">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="b978e-123">属性ルートをグローバルに指定された代わりに直接、コント ローラーとアクションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-123">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="b978e-124">これにより、ようにはるかに探索可能なときにする場合、特定のメソッドに参照しているわけでは、アプリケーションで 1 か所でルーティング情報が保持されないことの利点があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-124">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="b978e-125">属性のルートを持つを簡単に特定のアクションに対して複数のルートを指定したりできるようコント ローラーとアクション間のルートを結合します。</span><span class="sxs-lookup"><span data-stu-id="b978e-125">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="b978e-126">例:</span><span class="sxs-lookup"><span data-stu-id="b978e-126">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

<span data-ttu-id="b978e-127">[HttpGet] のルートを指定することができ、類似する属性を追加する必要がある分離 [ルート\]属性。</span><span class="sxs-lookup"><span data-stu-id="b978e-127">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route\] attributes.</span></span> <span data-ttu-id="b978e-128">属性のルートでは、次に示すようにコント ローラーまたはアクションの名前を繰り返す必要性を減らすトークンも使用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-128">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

<span data-ttu-id="b978e-129">ASP.NET Core MVC は、特定の要求は、ルートに一致していないが、メソッドが呼び出されたアクションの前に、[モデル バインディング](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding)と[モデルの検証](https://docs.microsoft.com/aspnet/core/mvc/models/validation)要求でします。</span><span class="sxs-lookup"><span data-stu-id="b978e-129">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) and [model validation](https://docs.microsoft.com/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="b978e-130">モデル バインディングが呼び出されるアクション メソッドのパラメーターとして指定された .NET 型、入力方向の HTTP データを変換する役割を担当します。</span><span class="sxs-lookup"><span data-stu-id="b978e-130">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="b978e-131">たとえば、アクション メソッドには、int id パラメーターが必要ですが場合、モデル バインドは、要求の一部として指定された値からこのパラメーターを指定しようとします。</span><span class="sxs-lookup"><span data-stu-id="b978e-131">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="b978e-132">これを行うには、モデル バインディングは、ポストされたフォーム内の値、ルート、自体の値およびクエリ文字列の値を検索します。</span><span class="sxs-lookup"><span data-stu-id="b978e-132">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="b978e-133">Id 値があると仮定した場合、変換されますを整数アクション メソッドに渡される前にします。</span><span class="sxs-lookup"><span data-stu-id="b978e-133">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="b978e-134">モデルをバインドした後は、アクション メソッドを呼び出す前にモデルの検証が行われます。</span><span class="sxs-lookup"><span data-stu-id="b978e-134">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="b978e-135">モデルの検証では、モデルの種類、省略可能な属性を使用し、指定されたモデル オブジェクトが特定のデータ要件に準拠していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-135">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="b978e-136">特定の値として指定できるなどのために必要なまたは特定の長さまたは数値の範囲に制限されます、します。検証属性が指定されたモデルがその要件に準拠していない場合は、プロパティ ModelState.IsValid が false に設定され失敗する検証規則のセットは要求を行うクライアントに送信する使用可能です。</span><span class="sxs-lookup"><span data-stu-id="b978e-136">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="b978e-137">モデルの検証を使用している場合は、常にチェックするモデルが無効なデータでは、アプリが破損しないようにする、任意の状態変更コマンドを実行する前に有効であることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-137">If you are using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="b978e-138">使用することができます、[フィルター](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)すべてのアクションでこのコードを追加する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="b978e-138">You can use a [filter](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="b978e-139">ASP.NET Core MVC フィルターは、一般的なポリシーと横断的関心事は対象となるごとに適用できるように、要求のグループをインターセプトする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="b978e-139">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="b978e-140">または個々 のアクション、全体のコント ローラーにグローバルにアプリケーションのフィルターを適用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-140">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="b978e-141">ASP.NET Core MVC をサポートしている web Api、 [*コンテンツ ネゴシエーション*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting)応答を書式設定する方法を指定する要求を許可します。</span><span class="sxs-lookup"><span data-stu-id="b978e-141">For web APIs, ASP.NET Core MVC supports [*content negotiation*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="b978e-142">要求で指定されたヘッダーに基づき、データを返すアクションは XML、JSON、または別のサポートされている形式で応答をフォーマットします。</span><span class="sxs-lookup"><span data-stu-id="b978e-142">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="b978e-143">この機能は、別のデータ形式の要件を持つ複数のクライアントによって使用される同じ API を使用します。</span><span class="sxs-lookup"><span data-stu-id="b978e-143">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="b978e-144">参照: 応答への要求のマッピング</span><span class="sxs-lookup"><span data-stu-id="b978e-144">References – Mapping Requests to Responses</span></span>
> - <span data-ttu-id="b978e-145">**コント ローラー アクションへのルーティング**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="b978e-145">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="b978e-146">**モデル バインディング**https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span><span class="sxs-lookup"><span data-stu-id="b978e-146">**Model Binding** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span></span>
> - <span data-ttu-id="b978e-147">**モデルの検証**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="b978e-147">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="b978e-148">**フィルター** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span><span class="sxs-lookup"><span data-stu-id="b978e-148">**Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="b978e-149">依存関係の操作</span><span class="sxs-lookup"><span data-stu-id="b978e-149">Working with Dependencies</span></span>

<span data-ttu-id="b978e-150">ASP.NET Core の組み込みサポートがあり、内部的に使用すると呼ばれる手法[依存性の注入](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)です。</span><span class="sxs-lookup"><span data-stu-id="b978e-150">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="b978e-151">依存関係の挿入は、アプリケーションのさまざまな部分との間の疎結合を有効になっている手法です。</span><span class="sxs-lookup"><span data-stu-id="b978e-151">Dependency injection is a technique that enabled loose coupling between different parts of an application.</span></span> <span data-ttu-id="b978e-152">やすくテスト用または交換できるように、アプリケーションの部分に分離するためよりゆるやかに結合の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b978e-152">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="b978e-153">また、アプリケーションの 1 つの部分で変更が、アプリケーションで別の場所に予期しない影響を与える必要がある可能性を低減します。</span><span class="sxs-lookup"><span data-stu-id="b978e-153">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="b978e-154">依存関係の挿入は依存関係の逆転原則に基づいて、多くの場合、開く/閉じる原則を達成するキー。</span><span class="sxs-lookup"><span data-stu-id="b978e-154">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="b978e-155">アプリケーションがその依存関係にどのように処理する方法を評価するときに注意してください、[静的窓](http://deviq.com/static-cling/)決まり、コードを格言を覚えておく"[新しいはグルー](http://ardalis.com/new-is-glue)"。</span><span class="sxs-lookup"><span data-stu-id="b978e-155">When evaluating how your application works with its dependencies, beware of the [static cling](http://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](http://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="b978e-156">静的窓は、クラスは、静的メソッドへの呼び出しを加えるか、静的プロパティは、副作用または依存関係インフラストラクチャ上にあるアクセスに発生します。</span><span class="sxs-lookup"><span data-stu-id="b978e-156">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="b978e-157">たとえば、メソッドを静的メソッドをさらに、データベースに書き込むと、呼び出しがある場合、メソッドが密に結合されて、データベース。</span><span class="sxs-lookup"><span data-stu-id="b978e-157">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="b978e-158">メソッドをそのデータベースの呼び出しを中断しているものが中断します。</span><span class="sxs-lookup"><span data-stu-id="b978e-158">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="b978e-159">そのようなテスト、静的な呼び出しのモック作成商用のモック ライブラリ必要またはのいずれかの場所でテスト データベースをテストするため、このようなメソッドのテストは非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="b978e-159">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="b978e-160">特には完全にステートレスで、インフラストラクチャの依存を持たない静的の呼び出しを呼び出すし、結合または (コードを静的な呼び出し自体に結合) を超えるテストの容易性に影響を与えるありませんしても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="b978e-160">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="b978e-161">多くの開発者は、静的窓とグローバル状態は、のリスクを理解はまだ密コードの特定の実装を介して直接インスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="b978e-161">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="b978e-162">「新しいはグルー」は目的としてこの結合のアラームと new キーワードの使用の一般的な condemnation されません。</span><span class="sxs-lookup"><span data-stu-id="b978e-162">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the new keyword.</span></span> <span data-ttu-id="b978e-163">同様、静的メソッドの呼び出しで外部の依存関係を通常がない型の新しいインスタンスは厳重に実装の詳細にコードを結合するまたはするテストが難しくします。</span><span class="sxs-lookup"><span data-stu-id="b978e-163">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="b978e-164">クラスがインスタンス化されるたびにすぐだけ簡単なをする意味がハード コードする特定のインスタンスを特定の場所であるかどうか、またはより優れた設計の依存関係としては、そのインスタンスを要求することが検討してください。</span><span class="sxs-lookup"><span data-stu-id="b978e-164">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="b978e-165">依存関係を宣言します。</span><span class="sxs-lookup"><span data-stu-id="b978e-165">Declare Your Dependencies</span></span>

<span data-ttu-id="b978e-166">ASP.NET Core が構築されています。 メソッドを持つし、クラスが引数としてそれらの要求、依存関係を宣言します。</span><span class="sxs-lookup"><span data-stu-id="b978e-166">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="b978e-167">ASP.NET アプリケーションがクラスでは、スタートアップ、セットアップして通常自体がいくつかの時点の依存関係の挿入をサポートするために構成されています。</span><span class="sxs-lookup"><span data-stu-id="b978e-167">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="b978e-168">依存関係のコンス トラクター、要求すること、スタートアップ クラスにコンス トラクターがある場合は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="b978e-168">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

<span data-ttu-id="b978e-169">スタートアップ クラスは、明示的な型の要件がないことに興味深いです。</span><span class="sxs-lookup"><span data-stu-id="b978e-169">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="b978e-170">特殊なスタートアップ基底クラスから継承されません。 また、特定のインターフェイスは実装。</span><span class="sxs-lookup"><span data-stu-id="b978e-170">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="b978e-171">付けることができます、コンス トラクターもそうでないと、必要な数だけ、コンス トラクターにパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-171">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="b978e-172">アプリケーションを構成したら、web ホストの開始時にするように指示したを使用するスタートアップ クラスを呼び出すし、スタートアップ クラスに必要なすべての依存関係を設定する依存関係の挿入を使用します。</span><span class="sxs-lookup"><span data-stu-id="b978e-172">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="b978e-173">もちろん、ASP.NET Core によって使用されるサービス コンテナーで構成されていないパラメーターを要求すると、例外が表示されますが、依存関係にオプションを使用している限り、コンテナーが認識、自分の好きを要求することができます。</span><span class="sxs-lookup"><span data-stu-id="b978e-173">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="b978e-174">依存関係の挿入は、スタートアップ インスタンスを作成するときに、一から ASP.NET Core アプリケーションに組み込まれてです。</span><span class="sxs-lookup"><span data-stu-id="b978e-174">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="b978e-175">スタートアップ クラスの存在に停止しません。</span><span class="sxs-lookup"><span data-stu-id="b978e-175">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="b978e-176">Configure メソッド内の依存関係を要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="b978e-176">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="b978e-177">ConfigureServices メソッドは、この動作を例外IServiceCollection 型のパラメーターを 1 つだけがかかる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-177">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="b978e-178">依存関係の挿入をサポートして一方で、サービス コンテナーにオブジェクトを追加する必要があり、IServiceCollection パラメーターを介して現在構成されているすべてのサービスへのアクセス権を持つ、別のために本当に必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b978e-178">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="b978e-179">したがって、パラメーターとして必要なサービスを要求するか ConfigureServices で IServiceCollection で作業してスタートアップ クラスのすべての部分で ASP.NET Core services コレクションで定義されている依存関係を操作できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-179">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="b978e-180">特定のサービスがスタートアップ クラスで使用できることを確認する必要がある場合、それらを構成できます WebHostBuilder とその ConfigureServices メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b978e-180">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="b978e-181">スタートアップ クラスは、独自のサービスをフィルターするミドルウェアをコント ローラーから、ASP.NET Core アプリケーションの他の部分を構成する方法のモデルです。</span><span class="sxs-lookup"><span data-stu-id="b978e-181">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="b978e-182">いずれの場合に従う必要があります、[明示的な依存関係の原則](http://deviq.com/explicit-dependencies-principle/)、要求、依存関係はなく、直接、それらを作成して、アプリケーション全体の依存関係の挿入を活用することです。</span><span class="sxs-lookup"><span data-stu-id="b978e-182">In each case, you should follow the [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="b978e-183">実装では、特にサービスとインフラストラクチャを使用または副作用があるオブジェクトを直接インスタンス化する場所と方法に注意します。</span><span class="sxs-lookup"><span data-stu-id="b978e-183">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="b978e-184">アプリケーション主要で定義されているし、特定の実装の種類へのハードコード参照を引数として渡されたの抽象化の操作を優先します。</span><span class="sxs-lookup"><span data-stu-id="b978e-184">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="b978e-185">アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="b978e-185">Structuring the Application</span></span>

<span data-ttu-id="b978e-186">モノリシックなアプリケーションには、通常 1 つのエントリ ポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="b978e-186">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="b978e-187">ASP.NET Core web アプリケーションの場合は、ASP.NET Core web プロジェクトがエントリ ポイントになります。</span><span class="sxs-lookup"><span data-stu-id="b978e-187">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="b978e-188">ただし、ことを意味して、ソリューションは、1 つのプロジェクトだけで構成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-188">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="b978e-189">次の問題を分離するために別のレイヤーにアプリケーションを中断すると便利です。</span><span class="sxs-lookup"><span data-stu-id="b978e-189">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="b978e-190">レイヤーに分割した後を別個のカプセル化の向上を実現するのに役立てることができるプロジェクト フォルダーより先に進むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b978e-190">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="b978e-191">ASP.NET Core アプリケーションと、これらの目標を実現するために最適な方法は、第 5 章で説明したクリーン アーキテクチャの変形です。</span><span class="sxs-lookup"><span data-stu-id="b978e-191">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="b978e-192">この方法は、次のアプリケーションのソリューションで構成されます別個のライブラリの UI、インフラストラクチャ、および ApplicationCore 用です。</span><span class="sxs-lookup"><span data-stu-id="b978e-192">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="b978e-193">これらのプロジェクトだけでなく別のテスト プロジェクトが含まれますも (テストは 9 章で説明しています)。</span><span class="sxs-lookup"><span data-stu-id="b978e-193">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="b978e-194">アプリケーションのオブジェクト モデルとのインターフェイスは、ApplicationCore プロジェクトに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-194">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="b978e-195">このプロジェクトは、できるだけ少ないの依存関係のあるし、ソリューション内の他のプロジェクトが参照されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-195">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="b978e-196">永続化する必要があるビジネス エンティティは、直接依存していないインフラストラクチャ サービスにも、ApplicationCore プロジェクトで定義されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-196">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="b978e-197">永続化を実行する方法や、ユーザーに通知を送信する方法など、実装の詳細は、インフラストラクチャのプロジェクトで保持されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-197">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="b978e-198">このプロジェクトは、Entity Framework のコアなどの実装に固有のパッケージは、参照は、プロジェクト外部のこれらの実装に関する詳細情報を公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="b978e-198">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="b978e-199">インフラストラクチャ サービスとのリポジトリが ApplicationCore プロジェクトで定義されているインターフェイスを実装する必要があります、永続化の実装を担当しています取得し、ApplicationCore で定義されたエンティティを格納します。</span><span class="sxs-lookup"><span data-stu-id="b978e-199">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="b978e-200">ASP.NET Core プロジェクト自体は、UI レベルの問題を担当するビジネス ロジックまたはインフラストラクチャの詳細を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="b978e-200">The ASP.NET Core project itself is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="b978e-201">実際には、理想的には、含めることはできませんでも、依存関係により、2 つのプロジェクト間の依存関係が追加されていない誤って、インフラストラクチャ プロジェクトでします。</span><span class="sxs-lookup"><span data-stu-id="b978e-201">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="b978e-202">これは、各プロジェクトのクラスをレジストリに DI ルールを定義することができる StructureMap のようにサード パーティ製 DI コンテナーを使用して実現できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-202">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="b978e-203">実装の詳細からアプリケーションを分離する方法は、個々 の Docker コンテナーで、展開、アプリケーション呼び出し microservices をことです。</span><span class="sxs-lookup"><span data-stu-id="b978e-203">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="b978e-204">これは問題と 2 つのプロジェクト間 DI を活用することよりも分離のさらに大きく分離を提供が、複雑さが増大します。</span><span class="sxs-lookup"><span data-stu-id="b978e-204">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="b978e-205">組織の機能</span><span class="sxs-lookup"><span data-stu-id="b978e-205">Feature Organization</span></span>

<span data-ttu-id="b978e-206">既定では、ASP.NET Core アプリケーションは、コント ローラーとビュー、およびよく ViewModels を含めるには、そのフォルダー構造を整理します。</span><span class="sxs-lookup"><span data-stu-id="b978e-206">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="b978e-207">通常、これらのサーバー側の構造をサポートするためにクライアント側のコードは wwwroot フォルダーに個別に格納されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-207">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="b978e-208">ただし、大規模なアプリケーションであっても、多くの場合、特定の機能で作業する場合は、これらのフォルダー間を移動する必要があるために、この組織に問題が発生可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-208">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="b978e-209">これは各フォルダーのファイルとサブフォルダーの数が増大すると、ソリューション エクスプ ローラーのスクロールの大量の結果として得られるより困難になってを取得します。</span><span class="sxs-lookup"><span data-stu-id="b978e-209">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="b978e-210">この問題の 1 つのソリューションは、アプリケーション コードを整理することです。*機能*ではなくファイルの種類。</span><span class="sxs-lookup"><span data-stu-id="b978e-210">One solution to this problem is to organize application code by *feature* instead of by file type.</span></span> <span data-ttu-id="b978e-211">この組織のスタイルを通常呼びます機能フォルダまたは機能のスライス (も参照してください:[垂直スライス](http://deviq.com/vertical-slices/))。</span><span class="sxs-lookup"><span data-stu-id="b978e-211">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](http://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="b978e-212">ASP.NET Core MVC には、この目的のための領域がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b978e-212">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="b978e-213">領域を使用して、コント ローラーとビュー (だけでなくフォルダー、関連付けられているモデル) 領域の各フォルダー内の個別セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-213">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="b978e-214">図 7-1 は、領域の使用例のフォルダー構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="b978e-214">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="b978e-215">図 7-1 サンプル領域組織</span><span class="sxs-lookup"><span data-stu-id="b978e-215">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="b978e-216">領域を使用する場合は、所属する領域の名前、コント ローラーを装飾する属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-216">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="b978e-217">また、領域のサポートをルートに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-217">You also need to add area support to your routes:</span></span>

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="b978e-218">領域の組み込みサポート、に加えてに独自のフォルダー構造、および属性とのカスタム ルートの代わりに規則を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b978e-218">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="b978e-219">これは、ようにするとして、ビュー、コント ローラーなど、階層を平坦化に維持して、関連するすべての機能ごとに 1 つの場所にファイルを参照してください、簡単に別のフォルダーが含まれていなかった機能フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="b978e-219">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="b978e-220">ASP.NET Core では、組み込みの規則の種類を使用して、その動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="b978e-220">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="b978e-221">変更したり、これらの規則を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b978e-221">You can modify or replace these conventions.</span></span> <span data-ttu-id="b978e-222">たとえば、その名前空間 (これは通常、コント ローラーが配置されているフォルダーに関連している) に基づく指定されたコント ローラーの機能名を自動的に取得する規則を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-222">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

```csharp
FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

<span data-ttu-id="b978e-223">として指定するこの規約オプション ConfigureServices でアプリケーションを MVC のサポートを追加する場合。</span><span class="sxs-lookup"><span data-stu-id="b978e-223">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="b978e-224">ASP.NET Core MVC は、ビューの場所にも、規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="b978e-224">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="b978e-225">ビューは、(上、FeatureConvention によって提供される機能名を使用)、機能のフォルダーで見つかることができるように、カスタム規則を含むメソッドをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="b978e-225">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="b978e-226">この方法の詳細し、MSDN の記事から実際のサンプルをダウンロードできます[ASP.NET Core MVC 用機能スライス](https://msdn.microsoft.com/magazine/mt763233.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="b978e-226">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="b978e-227">横断的関心事</span><span class="sxs-lookup"><span data-stu-id="b978e-227">Cross-Cutting Concerns</span></span>

<span data-ttu-id="b978e-228">アプリケーションが増すにつれて、重複を排除し、整合性を維持する横断的関心事取り出しをますます重要になります。</span><span class="sxs-lookup"><span data-stu-id="b978e-228">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="b978e-229">横断的関心事 ASP.NET Core アプリケーションでの例は、その他の多くを使用する必要がある場合、認証、モデルの検証規則、出力キャッシュ、およびエラー処理を示します。</span><span class="sxs-lookup"><span data-stu-id="b978e-229">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="b978e-230">ASP.NET Core MVC[フィルター](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)にする前に、または要求処理パイプライン内の特定の手順の後にコードを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b978e-230">ASP.NET Core MVC [filters](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="b978e-231">たとえば、フィルターでは、前におよび、操作の実行後、または前後にアクションの結果、モデル バインディングの前後を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-231">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="b978e-232">また、パイプラインの残りの部分へのアクセスを制御するのに承認フィルターを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b978e-232">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="b978e-233">図 7-2 に示します要求方法の実行フローのフィルターを構成されている場合。</span><span class="sxs-lookup"><span data-stu-id="b978e-233">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![要求は、承認フィルター、リソースのフィルター、モデル バインド、アクション フィルター、アクションの実行とアクション結果の変換、例外フィルター、結果のフィルター、およびを介して結果実行処理されます。](./media/image7-2.png)

<span data-ttu-id="b978e-236">フィルターと要求パイプラインを介して図 7-2 要求の実行。</span><span class="sxs-lookup"><span data-stu-id="b978e-236">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="b978e-237">フィルターをコント ローラーまたはアクションに適用できるように、通常、属性として実装されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-237">Filters are usually implemented as attributes, so you can apply them controllers or actions.</span></span> <span data-ttu-id="b978e-238">この方法では、レベルの上書きをアクションまたはコント ローラー レベルで指定されたフィルターをベースに構築で指定されたフィルターで追加されたときにそれ自体はグローバル フィルターをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b978e-238">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="b978e-239">たとえば、\[ルート\]属性は、コント ローラーとアクション間のルートをビルドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b978e-239">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="b978e-240">同様に、承認をコント ローラー レベルで構成されているし、次の例に示すように、個々 のアクションによってオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="b978e-240">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="b978e-241">最初のメソッドで、ログインは、コント ローラー レベルの設定、承認フィルターをオーバーライドするのに AllowAnonymous フィルター (属性) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b978e-241">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="b978e-242">ForgotPassword アクション (およびその他のアクション AllowAnonymous 属性を持たないクラスで) には、認証された要求が必要です。</span><span class="sxs-lookup"><span data-stu-id="b978e-242">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="b978e-243">共通のエラー処理ポリシー Api の形式での重複を回避するのには、フィルターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-243">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="b978e-244">たとえば、一般的な API ポリシーは、モデルの検証が失敗した場合、NotFound 応答が存在しないキーを参照している要求と BadRequest 応答を返すにです。</span><span class="sxs-lookup"><span data-stu-id="b978e-244">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="b978e-245">次の例では、これら 2 つのポリシーの動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="b978e-245">The following example demonstrates these two policies in action:</span></span>

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="b978e-246">次のように条件付きコードが散在し、アクション メソッドを許可しません。</span><span class="sxs-lookup"><span data-stu-id="b978e-246">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="b978e-247">代わりに、必要に応じてごとに適用できるフィルターにポリシーをプルします。</span><span class="sxs-lookup"><span data-stu-id="b978e-247">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="b978e-248">この例では、次の属性で、コマンドは、API に送られるたびに発生する必要があります、モデルの検証チェックを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="b978e-248">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

<span data-ttu-id="b978e-249">同様に、レコードが存在し、アクションを実行すると、アクションでこれらのチェックを実行する必要がなくなる前に、404 エラーを返すかどうかにチェックするフィルターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-249">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="b978e-250">取り込まれた一般的な規則と、UI からインフラストラクチャ コードとビジネス ロジックを分離するようにソリューションを構成した、MVC アクション メソッドがシン非常に高くする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-250">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="b978e-251">詳細を読み取ることができますフィルターを実装して、MSDN の記事から実際のサンプルのダウンロードについて[現実世界 ASP.NET Core MVC フィルター](https://msdn.microsoft.com/magazine/mt767699.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="b978e-251">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="b978e-252">参照: アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="b978e-252">References – Structuring Applications</span></span>
> - <span data-ttu-id="b978e-253">**領域**</span><span class="sxs-lookup"><span data-stu-id="b978e-253">**Areas**</span></span>  
> <span data-ttu-id="b978e-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span><span class="sxs-lookup"><span data-stu-id="b978e-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span></span>
> - <span data-ttu-id="b978e-255">**MSDN-ASP.NET core MVC 機能スライス**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx></span><span class="sxs-lookup"><span data-stu-id="b978e-255">**MSDN – Feature Slices for ASP.NET Core MVC**
<https://msdn.microsoft.com/magazine/mt763233.aspx></span></span>
> - <span data-ttu-id="b978e-256">**フィルター**</span><span class="sxs-lookup"><span data-stu-id="b978e-256">**Filters**</span></span>  
> <span data-ttu-id="b978e-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span><span class="sxs-lookup"><span data-stu-id="b978e-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span></span>
> - <span data-ttu-id="b978e-258">**MSDN-ASP.NET Core MVC フィルターの現実の世界**</span><span class="sxs-lookup"><span data-stu-id="b978e-258">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
> <span data-ttu-id="b978e-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span><span class="sxs-lookup"><span data-stu-id="b978e-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span></span>

## <a name="security"></a><span data-ttu-id="b978e-260">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b978e-260">Security</span></span>

<span data-ttu-id="b978e-261">Web アプリケーションの保護は、さまざまな考慮事項と、大規模なトピックです。</span><span class="sxs-lookup"><span data-stu-id="b978e-261">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="b978e-262">セキュリティには、その最も基本的なレベルでの特定の要求からのものとし、その要求はリソースへのアクセスのみがあることを確認するを把握することを確認が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b978e-262">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that that request only has access to resources it should.</span></span> <span data-ttu-id="b978e-263">認証は、既知のエンティティから送信された要求を扱うかどうかに表示する、信頼できるデータ ストアの要求で指定された資格情報を比較するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="b978e-263">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="b978e-264">承認は、ユーザー id に基づいて特定のリソースへのアクセスを制限するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="b978e-264">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="b978e-265">3 番目のセキュリティ上の懸念をする必要がありますには、少なくとも、第三者に傍受からの要求を保護する[SSL は、アプリケーションによって使用されていることを確認してください。](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl)です。</span><span class="sxs-lookup"><span data-stu-id="b978e-265">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="b978e-266">認証</span><span class="sxs-lookup"><span data-stu-id="b978e-266">Authentication</span></span>

<span data-ttu-id="b978e-267">ASP.NET Core の Id とは、アプリケーションのログインの機能をサポートするために使用することができます、メンバーシップ システムです。</span><span class="sxs-lookup"><span data-stu-id="b978e-267">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="b978e-268">ローカル ユーザー アカウントのサポートと Microsoft アカウント、Twitter、Facebook、Google などのようなプロバイダーから外部ログイン プロバイダーのサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="b978e-268">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="b978e-269">ASP.NET Core Id だけでなく、アプリケーションが windows 認証を使用して、またはサード パーティ id プロバイダーと同様に[Identity Server](https://github.com/IdentityServer/IdentityServer4)です。</span><span class="sxs-lookup"><span data-stu-id="b978e-269">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="b978e-270">ASP.NET Core の Id は、個々 のユーザー アカウント オプションが選択されている場合、新しいプロジェクト テンプレートに含まれます。</span><span class="sxs-lookup"><span data-stu-id="b978e-270">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="b978e-271">このテンプレートには、登録、ログイン、外部ログイン、パスワードを忘れた場合、および追加の機能のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b978e-271">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="b978e-272">図 7-3 選択個々 のユーザー アカウントをあらかじめ構成された Id を持っています。</span><span class="sxs-lookup"><span data-stu-id="b978e-272">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="b978e-273">Id のサポートは、スタートアップ時に、ConfigureServices と構成の両方で構成されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-273">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="b978e-274">構成メソッドに、その UseIdentity が UseMvc する前に表示されることが重要です。</span><span class="sxs-lookup"><span data-stu-id="b978e-274">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="b978e-275">Identity ConfigureServices でを構成する場合、AddDefaultTokenProviders への呼び出しがわかります。</span><span class="sxs-lookup"><span data-stu-id="b978e-275">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="b978e-276">これは、web 通信をセキュリティで保護するために使用する可能性がありますが、代わりに自身の id を確認するには、SMS またはそれらの順序で電子メールによってユーザーに送信できるメッセージを作成するプロバイダーを参照するトークンを行うには関係ありません。</span><span class="sxs-lookup"><span data-stu-id="b978e-276">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="b978e-277">詳細について[2 要素認証を構成する](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)と[外部ログイン プロバイダーを有効にする](https://docs.microsoft.com/aspnet/core/security/authentication/social/)公式の ASP.NET Core docs からです。</span><span class="sxs-lookup"><span data-stu-id="b978e-277">You can learn more about [configuring two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) and [enabling external login providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="b978e-278">承認</span><span class="sxs-lookup"><span data-stu-id="b978e-278">Authorization</span></span>

<span data-ttu-id="b978e-279">承認の最も単純な形式では、匿名ユーザーにアクセスを制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-279">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="b978e-280">適用すると、これを行う、 \[Authorize\]属性を特定のコント ローラーまたはアクションにします。</span><span class="sxs-lookup"><span data-stu-id="b978e-280">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="b978e-281">ロールを使用している場合のように、特定のロールに属しているユーザーにアクセスを制限する属性をさらに拡張できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-281">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="b978e-282">この場合、いずれか (または両方) の HRManager または Finance ロールに属しているユーザーは、SalaryController へのアクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="b978e-282">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="b978e-283">(複数に 1 つだけでなく) 複数のロールにユーザーが属していることを必要とするには、適用できます属性を複数回ごとに必要な役割を指定します。</span><span class="sxs-lookup"><span data-stu-id="b978e-283">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="b978e-284">多くのさまざまなコント ローラーとアクションの文字列が望ましくない繰り返しにつながる可能性が特定のロールのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="b978e-284">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="b978e-285">承認規則をカプセル化、承認ポリシーを構成して適用するときに、個々 のロールではなく、ポリシーを指定、 \[Authorize\]属性。</span><span class="sxs-lookup"><span data-stu-id="b978e-285">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="b978e-286">この方法でポリシーを使用して、特定のロールまたはそれに適用される規則が制限されているアクションの種類を区切ることができます。</span><span class="sxs-lookup"><span data-stu-id="b978e-286">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="b978e-287">後で、特定のリソースへのアクセスを必要とする新しいロールを作成する場合だけ更新できますですべての役割の一覧を更新するのではなく、ポリシーをすべて\[Authorize\]属性。</span><span class="sxs-lookup"><span data-stu-id="b978e-287">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="b978e-288">クレーム</span><span class="sxs-lookup"><span data-stu-id="b978e-288">Claims</span></span>

<span data-ttu-id="b978e-289">クレームは、認証済みユーザーのプロパティを表す名前値のペアです。</span><span class="sxs-lookup"><span data-stu-id="b978e-289">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="b978e-290">たとえば、クレームとしてユーザーの従業員数を格納する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-290">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="b978e-291">クレームは、承認ポリシーの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-291">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="b978e-292">"EmployeeOnly"と呼ばれるポリシーを作成することがこの例で示すように"EmployeeNumber"と呼ばれるクレームの存在を必要とします。</span><span class="sxs-lookup"><span data-stu-id="b978e-292">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

<span data-ttu-id="b978e-293">このポリシーを使用し、でした、 \[Authorize\]上記とれたコント ローラーとアクションを保護する属性。</span><span class="sxs-lookup"><span data-stu-id="b978e-293">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="b978e-294">Web Api をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="b978e-294">Securing Web APIs</span></span>

<span data-ttu-id="b978e-295">ほとんどの web Api には、トークン ベースの認証システムを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-295">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="b978e-296">トークンの認証です。 ステートレスおよび拡張できるよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="b978e-296">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="b978e-297">認証プロバイダーを使用する必要があります、トークン ベースの認証システムでクライアントを認証最初。</span><span class="sxs-lookup"><span data-stu-id="b978e-297">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="b978e-298">成功した場合、クライアントには、これは単に意味のある暗号化された文字列の文字のトークンが発行されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-298">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="b978e-299">クライアントは、API に要求を発行する必要があります、ときに、このトークンを要求のヘッダーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="b978e-299">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="b978e-300">サーバーは、要求ヘッダーについては、要求が完了する前に、トークンを検証します。</span><span class="sxs-lookup"><span data-stu-id="b978e-300">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="b978e-301">図 7-4 では、この手順を示します。</span><span class="sxs-lookup"><span data-stu-id="b978e-301">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="b978e-303">**図 7-4 です。**</span><span class="sxs-lookup"><span data-stu-id="b978e-303">**Figure 7-4.**</span></span> <span data-ttu-id="b978e-304">Web Api のトークン ベース認証。</span><span class="sxs-lookup"><span data-stu-id="b978e-304">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="b978e-305">参照: セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b978e-305">References – Security</span></span>
> - <span data-ttu-id="b978e-306">**ドキュメントのセキュリティの概要**</span><span class="sxs-lookup"><span data-stu-id="b978e-306">**Security Docs Overview**</span></span>  
> <span data-ttu-id="b978e-307">https://docs.microsoft.com/aspnet/core/security/</span><span class="sxs-lookup"><span data-stu-id="b978e-307">https://docs.microsoft.com/aspnet/core/security/</span></span>
> - <span data-ttu-id="b978e-308">**ASP.NET Core アプリケーションで SSL を適用します。**</span><span class="sxs-lookup"><span data-stu-id="b978e-308">**Enforcing SSL in an ASP.NET Core App**</span></span>  
> <span data-ttu-id="b978e-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span><span class="sxs-lookup"><span data-stu-id="b978e-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span></span>
> - <span data-ttu-id="b978e-310">**Identity の概要**</span><span class="sxs-lookup"><span data-stu-id="b978e-310">**Introduction to Identity**</span></span>  
> <span data-ttu-id="b978e-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span><span class="sxs-lookup"><span data-stu-id="b978e-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span></span>
> - <span data-ttu-id="b978e-312">**承認の概要**</span><span class="sxs-lookup"><span data-stu-id="b978e-312">**Introduction to Authorization**</span></span>  
> <span data-ttu-id="b978e-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span><span class="sxs-lookup"><span data-stu-id="b978e-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span></span>
> - <span data-ttu-id="b978e-314">**Azure App Service で API アプリの認証と承認**</span><span class="sxs-lookup"><span data-stu-id="b978e-314">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
> <span data-ttu-id="b978e-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span><span class="sxs-lookup"><span data-stu-id="b978e-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span></span>

## <a name="client-communication"></a><span data-ttu-id="b978e-316">クライアントとの通信</span><span class="sxs-lookup"><span data-stu-id="b978e-316">Client Communication</span></span>

<span data-ttu-id="b978e-317">ページの提供とに加えて web Api を使用してデータの要求に応答して、ASP.NET Core アプリケーションは接続されているクライアントと直接通信できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-317">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="b978e-318">この送信の通信には、さまざまなトランスポート テクノロジ、最も一般的なされている Websocket を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-318">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="b978e-319">ASP.NET Core SignalR は、ライブラリをアプリケーションにリアルタイムのサーバーからクライアントへの通信機能の種類に容易です。</span><span class="sxs-lookup"><span data-stu-id="b978e-319">ASP.NET Core SignalR is a library that makes it simple to kind of real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="b978e-320">SignalR では、さまざまなトランスポート テクノロジ、Websocket を含むをサポートしており、多くの開発者から実装の詳細を抽象化します。</span><span class="sxs-lookup"><span data-stu-id="b978e-320">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="b978e-321">ASP.NET Core SignalR は現在開発中および ASP.NET Core の次のリリースで提供されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-321">ASP.NET Core SignalR is currently under development, and will be available in the next release of ASP.NET Core.</span></span> <span data-ttu-id="b978e-322">ただし、他の[ソース Websocket ライブラリを開きます](https://github.com/radu-matei/websocket-manager)は現在使用できません。</span><span class="sxs-lookup"><span data-stu-id="b978e-322">However, other [open source WebSockets libraries](https://github.com/radu-matei/websocket-manager) are currently available.</span></span>

<span data-ttu-id="b978e-323">リアルタイムのクライアントとの通信、Websocket を直接またはその他の手法を使用してがさまざまなアプリケーション シナリオで役に立つかどうか。</span><span class="sxs-lookup"><span data-stu-id="b978e-323">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="b978e-324">次に、それらの例の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="b978e-324">Some examples include:</span></span>

-   <span data-ttu-id="b978e-325">ライブ チャット ルーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="b978e-325">Live chat room applications</span></span>

-   <span data-ttu-id="b978e-326">アプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="b978e-326">Monitoring applications</span></span>

-   <span data-ttu-id="b978e-327">ジョブの進行状況の更新</span><span class="sxs-lookup"><span data-stu-id="b978e-327">Job progress updates</span></span>

-   <span data-ttu-id="b978e-328">通知</span><span class="sxs-lookup"><span data-stu-id="b978e-328">Notifications</span></span>

-   <span data-ttu-id="b978e-329">対話型のフォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="b978e-329">Interactive forms applications</span></span>

<span data-ttu-id="b978e-330">アプリケーションにクライアントとの通信を構築するときに、2 つのコンポーネントは通常があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-330">When building client communication into your applications, there are typically two components:</span></span>

-   <span data-ttu-id="b978e-331">サーバー側の接続マネージャー (SignalR ハブ、WebSocketManager WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="b978e-331">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

-   <span data-ttu-id="b978e-332">クライアント側ライブラリ</span><span class="sxs-lookup"><span data-stu-id="b978e-332">Client-side library</span></span>

<span data-ttu-id="b978e-333">クライアントがブラウザー-モバイル アプリ、コンソール アプリに制限されて、他のネイティブ アプリは、SignalR/Websocket を使用しても通信できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-333">Clients are not limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="b978e-334">次の簡単なプログラムには、WebSocketManager サンプル アプリケーションの一部として、コンソールにチャット アプリケーションに送信されるすべての内容がエコーされます。</span><span class="sxs-lookup"><span data-stu-id="b978e-334">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }
    
    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }
    
    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
```

<span data-ttu-id="b978e-335">発生する、アプリケーションがクライアント アプリケーションと直接通信およびリアルタイム コミュニケーションがアプリのユーザーを向上させるかどうかを検討する方法を検討してください。</span><span class="sxs-lookup"><span data-stu-id="b978e-335">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="b978e-336">参照: クライアントとの通信</span><span class="sxs-lookup"><span data-stu-id="b978e-336">References – Client Communication</span></span>
> - <span data-ttu-id="b978e-337">**ASP.NET Core SignalR**</span><span class="sxs-lookup"><span data-stu-id="b978e-337">**ASP.NET Core SignalR**</span></span>  
> <span data-ttu-id="b978e-338"><https://github.com/aspnet/SignalR></span><span class="sxs-lookup"><span data-stu-id="b978e-338"><https://github.com/aspnet/SignalR></span></span>
> - <span data-ttu-id="b978e-339">**WebSocket マネージャー**</span><span class="sxs-lookup"><span data-stu-id="b978e-339">**WebSocket Manager**</span></span>  
> <span data-ttu-id="b978e-340">https://github.com/radu-matei/websocket-manager</span><span class="sxs-lookup"><span data-stu-id="b978e-340">https://github.com/radu-matei/websocket-manager</span></span>

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="b978e-341">ドメイン Driven Design: を適用することですか。</span><span class="sxs-lookup"><span data-stu-id="b978e-341">Domain-Driven Design – Should You Apply It?</span></span>

<span data-ttu-id="b978e-342">ドメインに基づくデザイン (DDD) に注目することを重視するソフトウェアの構築を柔軟な方法は、*ビジネス ドメイン*です。</span><span class="sxs-lookup"><span data-stu-id="b978e-342">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the *business domain*.</span></span> <span data-ttu-id="b978e-343">通信およびビジネス ドメイン expert(s)、実際のシステムのしくみ、開発者に関連付けることができるユーザーとの対話に重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="b978e-343">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="b978e-344">たとえば、株取引を処理するシステムを構築する場合、ドメインの専門家には、経験豊富な株式仲買可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-344">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="b978e-345">DDD 大規模で複雑なビジネス問題に対処するように設計されたされ、ほとんどの場合より小さいより簡単なアプリケーションでは、適切なとはへの投資を理解して、ドメインのモデリングが価値はありません。</span><span class="sxs-lookup"><span data-stu-id="b978e-345">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="b978e-346">(非技術的な利害関係者およびコントリビューターを含む)、チームが開発する必要があります DDD 手法に従ってソフトウェアを作成するときに、*ユビキタス言語*問題領域にします。</span><span class="sxs-lookup"><span data-stu-id="b978e-346">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a *ubiquitous language* for the problem space.</span></span> <span data-ttu-id="b978e-347">つまり、モデル化される実際の概念、ソフトウェアと同じと概念 (データベース テーブルなど) の保持に存在する構造体を同じ用語を使用してください。</span><span class="sxs-lookup"><span data-stu-id="b978e-347">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="b978e-348">したがって、ユビキタス言語で説明する概念の基礎を成して必要があります、*ドメイン モデル*です。</span><span class="sxs-lookup"><span data-stu-id="b978e-348">Thus, the concepts described in the ubiquitous language should form the basis for your *domain model*.</span></span>

<span data-ttu-id="b978e-349">ドメイン モデルは、相互作用するか、システムの動作を表すオブジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b978e-349">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="b978e-350">これらのオブジェクトは、次のカテゴリに分類されます可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-350">These objects may fall into the following categories:</span></span>

-   <span data-ttu-id="b978e-351">[エンティティ](http://deviq.com/entity/)id のスレッドを持つオブジェクトとして表示されています。</span><span class="sxs-lookup"><span data-stu-id="b978e-351">[Entities](http://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="b978e-352">エンティティは、通常は、後で取得できるキーを使用して永続化に格納します。</span><span class="sxs-lookup"><span data-stu-id="b978e-352">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

-   <span data-ttu-id="b978e-353">[集計](http://deviq.com/aggregate-pattern/)、単位として永続化するオブジェクトのグループとして表示されています。</span><span class="sxs-lookup"><span data-stu-id="b978e-353">[Aggregates](http://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

-   <span data-ttu-id="b978e-354">[オブジェクトの値](http://deviq.com/value-object/)、そのプロパティ値の合計に基づいて比較できる概念として表示されています。</span><span class="sxs-lookup"><span data-stu-id="b978e-354">[Value objects](http://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="b978e-355">たとえば、最初と最後の日付から成る DateRange です。</span><span class="sxs-lookup"><span data-stu-id="b978e-355">For example, DateRange consisting of a start and end date.</span></span>

-   <span data-ttu-id="b978e-356">[ドメインのイベント](https://martinfowler.com/eaaDev/DomainEvent.html)システムで起こっているか、システムの他の部分に関心のあるものとして表示されています。</span><span class="sxs-lookup"><span data-stu-id="b978e-356">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="b978e-357">DDD ドメイン モデルがモデル内で複雑な動作をカプセル化する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b978e-357">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="b978e-358">エンティティ、具体的には、だけを実行することはできませんのプロパティのコレクション。</span><span class="sxs-lookup"><span data-stu-id="b978e-358">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="b978e-359">ドメイン モデルでは、動作がないし、システムの状態を表す単、ときと呼ばれます、 [anemic モデル](http://deviq.com/anemic-model/)が指定されて DDD のことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b978e-359">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](http://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="b978e-360">これらの種類のモデルだけでなく DDD は通常、さまざまなパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="b978e-360">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

-   <span data-ttu-id="b978e-361">[リポジトリ](http://deviq.com/repository-pattern/)、永続化の詳細情報を抽出します。</span><span class="sxs-lookup"><span data-stu-id="b978e-361">[Repository](http://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

-   <span data-ttu-id="b978e-362">[ファクトリ](https://en.wikipedia.org/wiki/Factory_method_pattern)、複雑なオブジェクトの作成をカプセル化するためです。</span><span class="sxs-lookup"><span data-stu-id="b978e-362">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

-   <span data-ttu-id="b978e-363">依存する動作の動作をトリガーから分離することをドメインで構成するイベント。</span><span class="sxs-lookup"><span data-stu-id="b978e-363">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

-   <span data-ttu-id="b978e-364">[サービス](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)インフラストラクチャの実装の詳細をカプセル化する複雑な動作、またはその両方です。</span><span class="sxs-lookup"><span data-stu-id="b978e-364">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

-   <span data-ttu-id="b978e-365">[コマンド](https://en.wikipedia.org/wiki/Command_pattern)を切り離すためには、コマンドを発行、およびそれ自体のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b978e-365">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

-   <span data-ttu-id="b978e-366">[仕様](http://deviq.com/specification-pattern/)クエリの詳細をカプセル化するためです。</span><span class="sxs-lookup"><span data-stu-id="b978e-366">[Specification](http://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="b978e-367">DDD では、疎結合、カプセル化、およびコードの単体テストを使用して簡単に検証できるようにする、先ほど説明したクリーンなアーキテクチャを使用することも推奨します。</span><span class="sxs-lookup"><span data-stu-id="b978e-367">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="b978e-368">DDD するときに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-368">When Should You Apply DDD</span></span>

<span data-ttu-id="b978e-369">DDD は重要なビジネス (だけ技術ではない) の複雑さに大規模なアプリケーションに最適です。</span><span class="sxs-lookup"><span data-stu-id="b978e-369">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="b978e-370">アプリケーションは、ドメインの専門家が認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-370">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="b978e-371">ドメイン モデル自体で、ビジネス ルールとだけを格納して、データ ストアからさまざまなレコードの現在の状態を取得する以外の相互作用を表すは重要な動作をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-371">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="b978e-372">DDD はならないときに適用します。</span><span class="sxs-lookup"><span data-stu-id="b978e-372">When Shouldn't You Apply DDD</span></span>

<span data-ttu-id="b978e-373">DDD には、モデリング、アーキテクチャ、および可能性がありますいないことを示しますより小さい、アプリケーションまたは CRUD (作成/読み取り/更新/削除) だけでは基本的にアプリケーションの通信への投資が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b978e-373">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="b978e-374">DDD, の後、アプリケーションが動作を持たない anemic のモデルがドメインにあることを確認する場合は、実際のアプローチを再検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-374">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="b978e-375">アプリケーションでは、DDD, は必要はありませんか、データベース、またはユーザー インターフェイスではなく、ドメイン モデルでビジネス ロジックをカプセル化する、アプリケーションのリファクタリングのサポートが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-375">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="b978e-376">アプリケーションのトランザクションまたはより複雑な領域だけのシンプルな CRUD またはアプリケーションの部分は読み取り専用ため DDD をのみを使用するハイブリッド アプローチになります。</span><span class="sxs-lookup"><span data-stu-id="b978e-376">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="b978e-377">たとえば、レポートを表示する、またはダッシュ ボードにデータを視覚化するデータのクエリを実行している場合、集計の制約がある必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b978e-377">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="b978e-378">このような要件については、独立した、シンプルな読み取りモデルがまったく問題ありませんが。</span><span class="sxs-lookup"><span data-stu-id="b978e-378">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="b978e-379">– ドメイン ドリブン デザインの参照</span><span class="sxs-lookup"><span data-stu-id="b978e-379">References – Domain-Driven Design</span></span>
> - <span data-ttu-id="b978e-380">**DDD 簡潔な表現 (StackOverflow Answer).**</span><span class="sxs-lookup"><span data-stu-id="b978e-380">**DDD in Plain English (StackOverflow Answer)**</span></span>  
> <span data-ttu-id="b978e-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span><span class="sxs-lookup"><span data-stu-id="b978e-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span></span>

## <a name="deployment"></a><span data-ttu-id="b978e-382">配置</span><span class="sxs-lookup"><span data-stu-id="b978e-382">Deployment</span></span>

<span data-ttu-id="b978e-383">ホストされる場所に関係なく、ASP.NET Core アプリケーションを展開するプロセスでは、いくつかの手順があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-383">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="b978e-384">最初の手順が実行すると、アプリケーションを発行するには CLI コマンドを発行、dotnet を使用します。</span><span class="sxs-lookup"><span data-stu-id="b978e-384">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="b978e-385">アプリケーションをコンパイルし、すべての指定したフォルダに、アプリケーションの実行に必要なファイルの配置このされます。</span><span class="sxs-lookup"><span data-stu-id="b978e-385">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="b978e-386">Visual Studio から展開するときにこの手順は自動的を実行します。</span><span class="sxs-lookup"><span data-stu-id="b978e-386">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="b978e-387">発行フォルダーには、アプリケーションとその依存関係の .exe と .dll ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b978e-387">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="b978e-388">自己完結型アプリケーションでは、.NET ランタイムのバージョンも含まれます。</span><span class="sxs-lookup"><span data-stu-id="b978e-388">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="b978e-389">ASP.NET Core アプリケーションには、構成ファイル、静的クライアント資産、および MVC ビューも含まれます。</span><span class="sxs-lookup"><span data-stu-id="b978e-389">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="b978e-390">ASP.NET Core アプリケーションはコンソール アプリケーション、サーバーが起動し、アプリケーション (またはサーバー) がクラッシュした場合の再起動と同時に起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-390">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="b978e-391">プロセス マネージャは、このプロセスの自動化に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-391">A process manager can be used to automate this process.</span></span> <span data-ttu-id="b978e-392">ASP.NET Core の最も一般的なプロセス マネージャーは、Nginx Linux および IIS での Apache や Windows 上の Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="b978e-392">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="b978e-393">プロセス マネージャーだけでなく Kestrel web サーバーでホストされる ASP.NET Core アプリケーションがリバース プロキシ サーバーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-393">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="b978e-394">リバース プロキシ サーバーでは、インターネットから HTTP 要求を受け取り、いくつかの予備処理後に Kestrel に転送します。</span><span class="sxs-lookup"><span data-stu-id="b978e-394">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="b978e-395">リバース プロキシ サーバーは、アプリケーションのセキュリティ レイヤーを提供し、(インターネットからのトラフィックに対して公開) のエッジ展開に必要な。</span><span class="sxs-lookup"><span data-stu-id="b978e-395">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="b978e-396">Kestrel は比較的新しいし、ある種の攻撃に対する防御がまだ提供していません。</span><span class="sxs-lookup"><span data-stu-id="b978e-396">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="b978e-397">Kestrel もサポートされていません、同じポートで複数のアプリケーションをホストしているため、同じポートと IP アドレスで複数のアプリケーションをホストできるようにしてホスト ヘッダーなどの手法を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b978e-397">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![インターネットに kestrel](./media/image7-5.png)

<span data-ttu-id="b978e-399">図 7-5 リバース プロキシ サーバーの背後に Kestrel でホストされる ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b978e-399">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="b978e-400">もう 1 つのシナリオをリバース プロキシは役に立ちます SSL または HTTPS を使用して複数のアプリケーションをセキュリティで保護を開始します。</span><span class="sxs-lookup"><span data-stu-id="b978e-400">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="b978e-401">この例では、リバース プロキシのみは SSL を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b978e-401">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="b978e-402">リバース プロキシ サーバーと Kestrel 間の通信でした HTTP 上で行わ、図 7-6 に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b978e-402">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="b978e-403">図 7-6 リバース プロキシの HTTPS で保護されたサーバーの背後にホストされている ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b978e-403">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="b978e-404">急速に普及アプローチ、ASP.NET Core アプリケーションでホストし、ローカル ホストまたはクラウド ベースをホストするために、Azure にデプロイされた Docker コンテナーを開始します。</span><span class="sxs-lookup"><span data-stu-id="b978e-404">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="b978e-405">Docker コンテナーでは、Kestrel で実行されている、アプリケーション コードが含まれ、リバース プロキシ サーバーの背後に配置できるように上記のようにします。</span><span class="sxs-lookup"><span data-stu-id="b978e-405">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="b978e-406">Azure でアプリケーションをホストしている場合は、いくつかのサービスを提供する専用の仮想アプライアンスとして Microsoft Azure アプリケーション ゲートウェイを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b978e-406">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="b978e-407">個々 のアプリケーションに対してリバース プロキシとして動作しているだけでなく、アプリケーション ゲートウェイは、次の機能を提供することも。</span><span class="sxs-lookup"><span data-stu-id="b978e-407">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

-   <span data-ttu-id="b978e-408">HTTP の負荷分散</span><span class="sxs-lookup"><span data-stu-id="b978e-408">HTTP load balancing</span></span>

-   <span data-ttu-id="b978e-409">SSL オフロード (インターネットのみに SSL)</span><span class="sxs-lookup"><span data-stu-id="b978e-409">SSL offload (SSL only to Internet)</span></span>

-   <span data-ttu-id="b978e-410">エンド ツー エンドの SSL</span><span class="sxs-lookup"><span data-stu-id="b978e-410">End to End SSL</span></span>

-   <span data-ttu-id="b978e-411">複数のサイトのルーティング (1 つのアプリケーション ゲートウェイ上の最大 20 件までのサイトを統合)</span><span class="sxs-lookup"><span data-stu-id="b978e-411">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

-   <span data-ttu-id="b978e-412">Web アプリケーション ファイアウォール</span><span class="sxs-lookup"><span data-stu-id="b978e-412">Web application firewall</span></span>

-   <span data-ttu-id="b978e-413">Websocket のサポート</span><span class="sxs-lookup"><span data-stu-id="b978e-413">Websocket support</span></span>

-   <span data-ttu-id="b978e-414">高度な診断</span><span class="sxs-lookup"><span data-stu-id="b978e-414">Advanced diagnostics</span></span>

<span data-ttu-id="b978e-415">*章 10 での Azure のデプロイ オプションについて説明します。*</span><span class="sxs-lookup"><span data-stu-id="b978e-415">*Learn more about Azure deployment options in Chapter 10.*</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="b978e-416">-展開の参照</span><span class="sxs-lookup"><span data-stu-id="b978e-416">References – Deployment</span></span>
> - <span data-ttu-id="b978e-417">**ホストと展開の概要**</span><span class="sxs-lookup"><span data-stu-id="b978e-417">**Hosting and Deployment Overview**</span></span>  
> <span data-ttu-id="b978e-418"><https://docs.microsoft.com/aspnet/core/publishing/></span><span class="sxs-lookup"><span data-stu-id="b978e-418"><https://docs.microsoft.com/aspnet/core/publishing/></span></span>
> - <span data-ttu-id="b978e-419">**リバース プロキシで Kestrel を使用する場合**</span><span class="sxs-lookup"><span data-stu-id="b978e-419">**When to use Kestrel with a reverse proxy**</span></span>  
> <span data-ttu-id="b978e-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span><span class="sxs-lookup"><span data-stu-id="b978e-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span></span>
> - <span data-ttu-id="b978e-421">**Docker での ASP.NET Core アプリケーションのホスト**</span><span class="sxs-lookup"><span data-stu-id="b978e-421">**Host ASP.NET Core apps in Docker**</span></span>  
> <span data-ttu-id="b978e-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span><span class="sxs-lookup"><span data-stu-id="b978e-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span></span>
> - <span data-ttu-id="b978e-423">**Azure アプリケーション ゲートウェイの概要**</span><span class="sxs-lookup"><span data-stu-id="b978e-423">**Introducing Azure Application Gateway**</span></span>  
> <span data-ttu-id="b978e-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span><span class="sxs-lookup"><span data-stu-id="b978e-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b978e-425">[前](一般的なのクライアント-側-web-technologies.md) [次へ] (work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="b978e-425">[Previous] (common-client-side-web-technologies.md) [Next] (work-with-data-in-asp-net-core-apps.md)</span></span>
