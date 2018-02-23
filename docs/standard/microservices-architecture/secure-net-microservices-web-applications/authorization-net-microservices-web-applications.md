---
title: ".NET マイクロサービスと Web アプリケーションでの承認について"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | .NET マイクロサービスと Web アプリケーションでの承認について"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6cd7be9bc8216aecf85f99a76e859b411a8735b0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="fa340-104">.NET マイクロサービスと Web アプリケーションでの承認について</span><span class="sxs-lookup"><span data-stu-id="fa340-104">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="fa340-105">認証の後に、ASP.NET Core Web API がアクセスを承認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa340-105">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="fa340-106">このプロセスによって、サービスが一部の認証ユーザーに API を提供できますが、すべてのユーザーではありません。</span><span class="sxs-lookup"><span data-stu-id="fa340-106">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="fa340-107">[承認](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)は、ユーザーのロールまたはカスタム ポリシーに基づいて行われ、要求またはその他のヒューリスティックの調査が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fa340-107">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="fa340-108">次の例に示すように、ASP.NET Core MVC ルートへのアクセス制限は、アクション メソッド (またはすべてのコントローラーのアクションで承認が必要な場合は、コントローラーのクラス) に Authorize 属性を適用するのと同じくらい簡単です。</span><span class="sxs-lookup"><span data-stu-id="fa340-108">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="fa340-109">既定では、パラメーターなしの Authorize 属性を追加すると、そのコントローラーまたはアクションの認証されたユーザーへのアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="fa340-109">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="fa340-110">特定のユーザーだけに利用できる API をさらに制限するには、ユーザーが満たす必要がある必要なロールまたはポリシーを指定するように属性を拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="fa340-110">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="fa340-111">ロール ベースの承認の実装</span><span class="sxs-lookup"><span data-stu-id="fa340-111">Implementing role-based authorization</span></span>

<span data-ttu-id="fa340-112">ASP.NET Core ID には、ロールの概念が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="fa340-112">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="fa340-113">ユーザーに加えて、ASP.NET Core ID は、アプリケーションによって使用されるさまざまなロールに関する情報を格納し、どのユーザーがどのロールに割り当てられているかを追跡します。</span><span class="sxs-lookup"><span data-stu-id="fa340-113">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="fa340-114">これらの割り当ては、RoleManager の種類 (永続化された記憶域内のロールを更新します) および UserManager の種類 (ロールにユーザーを割り当てるかまたはロールからユーザーの割り当てを解除できます) によってプログラムで変更できます。</span><span class="sxs-lookup"><span data-stu-id="fa340-114">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="fa340-115">JWT ベアラ トークンによる認証を行う場合、ASP.NET Core JWT ベアラ認証ミドルウェアは、トークンで見つかったロール要求に基づいてユーザーのロールを入力します。</span><span class="sxs-lookup"><span data-stu-id="fa340-115">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="fa340-116">MVC アクションまたはコントローラーへのアクセスを特定のロールのユーザーに制限するために、次の例に示すように、Authorize ヘッダーに Roles パラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="fa340-116">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

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

<span data-ttu-id="fa340-117">この例では、Administrator または PowerUser ロールのユーザーのみが、ControlPanel コントローラーの API (SetTime アクションの実行など) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fa340-117">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="fa340-118">ShutDown API は、Administrator ロールのユーザーのみにアクセスを許可するようにさらに制限します。</span><span class="sxs-lookup"><span data-stu-id="fa340-118">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="fa340-119">ユーザーに複数のロールが割り当てられていることを必須にするには、次の例で示すように、複数の Authorize 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="fa340-119">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="fa340-120">この例では、API1 を呼び出すために、ユーザーは次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa340-120">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="fa340-121">Adminstrator *または* PowerUser ロールであり、*かつ*</span><span class="sxs-lookup"><span data-stu-id="fa340-121">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="fa340-122">RemoteEmployee ロールであり、*かつ*</span><span class="sxs-lookup"><span data-stu-id="fa340-122">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="fa340-123">CustomPolicy 承認のためのカスタム ハンドラーを満たしている。</span><span class="sxs-lookup"><span data-stu-id="fa340-123">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="fa340-124">ポリシー ベースの承認の実装</span><span class="sxs-lookup"><span data-stu-id="fa340-124">Implementing policy-based authorization</span></span>

<span data-ttu-id="fa340-125">カスタム承認規則も[承認ポリシー](https://docs.asp.net/en/latest/security/authorization/policies.html)を使用して記述できます。</span><span class="sxs-lookup"><span data-stu-id="fa340-125">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="fa340-126">このセクションでは、概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="fa340-126">In this section we provide an overview.</span></span> <span data-ttu-id="fa340-127">詳細については、オンラインの「[ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop)」(ASP.NET 承認ワークショップ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa340-127">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="fa340-128">カスタム承認ポリシーは、service.AddAuthorization メソッドを使用して、Startup.ConfigureServices メソッドに登録されます。</span><span class="sxs-lookup"><span data-stu-id="fa340-128">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="fa340-129">このメソッドは、AuthorizationOptions 引数を構成するデリゲートを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="fa340-129">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="fa340-130">例に示すように、ポリシーをさまざまな種類の要件に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="fa340-130">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="fa340-131">ポリシーが登録された後に、ポリシーの名前を Authorize 属性の Policy 引数として渡すことで、アクションまたはコントローラーにポリシーを適用できます (たとえば、\[Authorize(Policy="EmployeesOnly")\])。ポリシーは、これらの例に示すように 1 つだけでなく複数の要件を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="fa340-131">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="fa340-132">前の例では、AddPolicy の最初の呼び出しは、ロールによる承認の代替の方法です。</span><span class="sxs-lookup"><span data-stu-id="fa340-132">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="fa340-133">\[Authorize(Policy="AdministratorsOnly")\] が API に適用される場合、Administrator ロールのユーザーのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="fa340-133">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="fa340-134">2 番目の AddPolicy の呼び出しは、特定の要求をユーザーに提示することをユーザーに義務付けるための簡単な方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fa340-134">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="fa340-135">RequireClaim メソッドは、また、必要に応じて、要求の予期される値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="fa340-135">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="fa340-136">値を指定する場合、ユーザーが正しい種類の要求と、指定された値のいずれかの両方を持っている場合にのみこの要件を満たします。</span><span class="sxs-lookup"><span data-stu-id="fa340-136">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="fa340-137">JWT ベアラ認証ミドルウェアを使用している場合、すべての JWT プロパティはユーザーの要求として使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="fa340-137">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="fa340-138">ここで示す最も注目すべきポリシーは、カスタム承認要件を使用している 3 番目の AddPolicy メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fa340-138">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="fa340-139">カスタム承認要件を使用すると、承認を実行する方法を細かく制御することができます。</span><span class="sxs-lookup"><span data-stu-id="fa340-139">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="fa340-140">これを機能させるには、次の種類を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa340-140">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="fa340-141">IAuthorizationRequirement から派生し、要件の詳細を指定するフィールドを格納している要件の種類。</span><span class="sxs-lookup"><span data-stu-id="fa340-141">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="fa340-142">例では、これはサンプル MinimumAgeRequirement タイプの年齢フィールドです。</span><span class="sxs-lookup"><span data-stu-id="fa340-142">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="fa340-143">AuthorizationHandler&lt;T&gt; を実装するハンドラー。T は、ハンドラーが満たすことができる IAuthorizationRequirement の種類です。</span><span class="sxs-lookup"><span data-stu-id="fa340-143">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="fa340-144">このハンドラーは、ユーザーに関する情報を格納している指定されたコンテキストが要件を満たすかどうかをチェックする HandleRequirementAsync メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa340-144">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="fa340-145">ユーザーが要件を満たす場合、context.Succeed への呼び出しが、ユーザーを承認されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fa340-145">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="fa340-146">ユーザーが承認要件を満たす方法が複数ある場合、複数のハンドラーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="fa340-146">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="fa340-147">カスタム ポリシーの要件の AddPolicy 呼び出しへの登録に加えて、依存関係の挿入を使用してカスタム要件ハンドラーも登録する必要があります (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;())。</span><span class="sxs-lookup"><span data-stu-id="fa340-147">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="fa340-148">カスタム承認要件およびユーザーの年齢 (DateOfBirth 要求に基づく) をチェックするハンドラーの例については、ASP.NET Core [承認ドキュメント](https://docs.asp.net/en/latest/security/authorization/policies.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa340-148">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fa340-149">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="fa340-149">Additional resources</span></span>

-   <span data-ttu-id="fa340-150">**ASP.NET Core 認証**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="fa340-150">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="fa340-151">**ASP.NET Core 承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="fa340-151">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="fa340-152">**ロールベースの承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="fa340-152">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="fa340-153">**カスタム ポリシーベースの承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="fa340-153">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="fa340-154">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="fa340-154">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span></span>
