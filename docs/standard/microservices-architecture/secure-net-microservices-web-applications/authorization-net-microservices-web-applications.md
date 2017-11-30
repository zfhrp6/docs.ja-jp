---
title: ".NET microservices と web アプリケーションでの承認について"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |.NET microservices と web アプリケーションでの承認について"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 51adda4f5bdb28154f17b9a988ee2d887bf1d461
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="a378d-104">.NET microservices と web アプリケーションでの承認について</span><span class="sxs-lookup"><span data-stu-id="a378d-104">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="a378d-105">認証の後に、ASP.NET Core Web Api は、アクセスを承認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a378d-105">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="a378d-106">これにより、サービス Api によって認証されたユーザーに利用可能なすべてではなくにされます。</span><span class="sxs-lookup"><span data-stu-id="a378d-106">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="a378d-107">[承認](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)ユーザーのロールに基づいて行われますか、信頼性情報またはその他のヒューリスティックを調べることなどを含むカスタム ポリシーに基づくことができます。</span><span class="sxs-lookup"><span data-stu-id="a378d-107">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="a378d-108">ASP.NET Core MVC ルートへのアクセス制限は、アクション メソッドに (またはコント ローラーのアクションで承認が必要な場合は、コント ローラーのクラスを)、承認属性を適用する例を次に示すとして同じくらい簡単です。</span><span class="sxs-lookup"><span data-stu-id="a378d-108">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

<span data-ttu-id="a378d-109">既定では、パラメーターなしの承認属性を追加することは、そのコント ローラーまたはアクションの認証されたユーザーへのアクセスに制限されます。</span><span class="sxs-lookup"><span data-stu-id="a378d-109">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="a378d-110">特定のユーザーだけに利用できる API をさらに制限するには、必要な役割またはユーザーが満たす必要があるポリシーを指定する属性を展開することができます。</span><span class="sxs-lookup"><span data-stu-id="a378d-110">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="a378d-111">ロールベースの承認を実装します。</span><span class="sxs-lookup"><span data-stu-id="a378d-111">Implementing role-based authorization</span></span>

<span data-ttu-id="a378d-112">ASP.NET Core Id は、役割の組み込みの概念を持っています。</span><span class="sxs-lookup"><span data-stu-id="a378d-112">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="a378d-113">ユーザー以外は、ASP.NET Core Id はアプリケーションによって使用されるさまざまなロールに関する情報を格納し、どのロールに割り当てるユーザーの追跡します。</span><span class="sxs-lookup"><span data-stu-id="a378d-113">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="a378d-114">これらの割り当ては、RoleManager の種類 (更新プログラムの永続化された記憶域内のロール) および (を割り当てる、またはロールからユーザーの割り当てを解除できます) UserManager 型を持つプログラムで変更できます。</span><span class="sxs-lookup"><span data-stu-id="a378d-114">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="a378d-115">JWT ベアラ トークンによる認証を行う場合、ASP.NET Core JWT ベアラ認証ミドルウェアは、トークンに見つかりませんロール クレームに基づくユーザーのロールを設定します。</span><span class="sxs-lookup"><span data-stu-id="a378d-115">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="a378d-116">MVC アクションまたはコント ローラーが特定のロールのユーザーへのアクセスを制限するための次の例に示すように、承認ヘッダーにロール パラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a378d-116">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

<span data-ttu-id="a378d-117">この例では、管理者または PowerUser ロールのユーザーのみ (SetTime 操作を実行して) など、コントロール パネルの コント ローラーの Api にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a378d-117">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="a378d-118">シャット ダウン API は、管理者ロールにユーザーにのみアクセスを許可するさらに制限します。</span><span class="sxs-lookup"><span data-stu-id="a378d-118">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="a378d-119">複数の役割であることが必要な次の例で示すように、複数の承認属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="a378d-119">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="a378d-120">この例では呼び出す API1、ユーザーが必要です。</span><span class="sxs-lookup"><span data-stu-id="a378d-120">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="a378d-121">管理者である*または*PowerUser ロール*と*</span><span class="sxs-lookup"><span data-stu-id="a378d-121">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="a378d-122">RemoteEmployee ロールである*と*</span><span class="sxs-lookup"><span data-stu-id="a378d-122">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="a378d-123">CustomPolicy 承認のためのカスタム ハンドラーを満たします。</span><span class="sxs-lookup"><span data-stu-id="a378d-123">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="a378d-124">ポリシー ベースの承認を実装します。</span><span class="sxs-lookup"><span data-stu-id="a378d-124">Implementing policy-based authorization</span></span>

<span data-ttu-id="a378d-125">使用してカスタム承認規則を記述することができますも[承認ポリシー](https://docs.asp.net/en/latest/security/authorization/policies.html)です。</span><span class="sxs-lookup"><span data-stu-id="a378d-125">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="a378d-126">このセクションでは、概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="a378d-126">In this section we provide an overview.</span></span> <span data-ttu-id="a378d-127">詳細については、オンラインで使用できる[ASP.NET 承認ワーク ショップ](https://github.com/blowdart/AspNetAuthorizationWorkshop)です。</span><span class="sxs-lookup"><span data-stu-id="a378d-127">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="a378d-128">カスタム承認ポリシーは、サービスを使用して、Startup.ConfigureServices メソッドで登録されます。AddAuthorization メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a378d-128">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="a378d-129">このメソッドは、AuthorizationOptions 引数を構成するデリゲートを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a378d-129">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));
    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));
    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

<span data-ttu-id="a378d-130">例のように、ポリシーがさまざまな種類の要件の関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="a378d-130">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="a378d-131">ポリシーは、登録後に適用できますアクションまたはコント ローラーに Authorize attribute のポリシーの引数として、ポリシーの名前を渡すことで (たとえば、 \[Authorize(Policy="EmployeesOnly")\]) ポリシーを持つことができます複数の要件だけでなく 1 つに示すようにこれらの例)。</span><span class="sxs-lookup"><span data-stu-id="a378d-131">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="a378d-132">前の例では、AddPolicy の最初の呼び出しは、ロールによって承認する方法でもです。</span><span class="sxs-lookup"><span data-stu-id="a378d-132">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="a378d-133">場合\[Authorize(Policy="AdministratorsOnly")\]管理者ロールのユーザーがアクセスできる専用の API に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a378d-133">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="a378d-134">2 番目の AddPolicy 呼び出しでは、特定のクレームが存在する必要がありますを必要とする簡単な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a378d-134">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="a378d-135">RequireClaim メソッドは、また、必要に応じて、クレームの予期される値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a378d-135">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="a378d-136">値を指定する場合、ユーザーがある両方の正しい種類のクレームと、指定された値のいずれかの場合にのみこの要件を満たします。</span><span class="sxs-lookup"><span data-stu-id="a378d-136">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="a378d-137">JWT ベアラ認証ミドルウェアを使用している場合、すべての JWT プロパティはユーザーの信頼性情報として使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="a378d-137">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="a378d-138">ここで示すように、最も注目すべきポリシーは、3 番目の AddPolicy メソッドではカスタム承認要件を使用しているためです。</span><span class="sxs-lookup"><span data-stu-id="a378d-138">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="a378d-139">カスタム承認要件を使用すると、承認を実行する方法を細かく制御が大幅に向上ことができます。</span><span class="sxs-lookup"><span data-stu-id="a378d-139">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="a378d-140">これを行うには、これらの型を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a378d-140">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="a378d-141">IAuthorizationRequirement から派生して、要件の詳細を指定するフィールドを格納している必要条件の種類。</span><span class="sxs-lookup"><span data-stu-id="a378d-141">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="a378d-142">例では、これは、サンプル MinimumAgeRequirement タイプの時効フィールドです。</span><span class="sxs-lookup"><span data-stu-id="a378d-142">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="a378d-143">AuthorizationHandler を実装するハンドラー&lt;T&gt;ここで T は、ハンドラーが満たすことができる IAuthorizationRequirement の型。</span><span class="sxs-lookup"><span data-stu-id="a378d-143">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="a378d-144">ハンドラーには、ユーザーに関する情報を格納している指定されたコンテキストが要件を満たすかどうかをチェックする HandleRequirementAsync メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a378d-144">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="a378d-145">場合は、ユーザーは、コンテキストへの呼び出しの要件を満たしています。成功は、ユーザーを承認することを示すです。</span><span class="sxs-lookup"><span data-stu-id="a378d-145">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="a378d-146">複数の方法で、ユーザーが承認要件を満たすことがありますがある場合は、複数のハンドラーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a378d-146">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="a378d-147">カスタム ポリシーの要件を AddPolicy 呼び出しに登録すると、に加えて必要もあります (サービス依存関係の挿入を使用してカスタム要求ハンドラーを登録します。AddTransient&lt;IAuthorizationHandler、MinimumAgeHandler&gt;())。</span><span class="sxs-lookup"><span data-stu-id="a378d-147">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="a378d-148">カスタム承認要件と、ユーザーの年齢を (DateOfBirth クレームに基づく) をチェックするためのハンドラーの例は、ASP.NET Core で使用できる[承認ドキュメント](https://docs.asp.net/en/latest/security/authorization/policies.html)です。</span><span class="sxs-lookup"><span data-stu-id="a378d-148">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a378d-149">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="a378d-149">Additional resources</span></span>

-   <span data-ttu-id="a378d-150">**ASP.NET Core 認証**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="a378d-150">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="a378d-151">**ASP.NET Core 承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="a378d-151">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="a378d-152">**ロール ベースの承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="a378d-152">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="a378d-153">**カスタムのポリシー ベースの承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="a378d-153">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="a378d-154">[前](index.md) [次へ] (開発者向けのアプリのシークレット-storage.md)</span><span class="sxs-lookup"><span data-stu-id="a378d-154">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span></span>
