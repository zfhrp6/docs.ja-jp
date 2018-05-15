---
title: NET マイクロサービスおよび Web アプリケーションをセキュリティで保護する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | .NET マイクロサービスおよび Web アプリケーションをセキュリティで保護する
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c2c7d692517c6a46225542936e05656db915bf0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="securing-net-microservices-and-web-applications"></a><span data-ttu-id="9cb77-103">NET マイクロサービスおよび Web アプリケーションをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="9cb77-103">Securing .NET Microservices and Web Applications</span></span>

<span data-ttu-id="9cb77-104">サービスによって公開されるリソースおよび API は多くの場合、特定の信頼されたユーザーまたはクライアントに制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cb77-104">It is often necessary for resources and APIs exposed by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="9cb77-105">このような API レベルの信頼の決定を行うための最初の手順は、認証です。</span><span class="sxs-lookup"><span data-stu-id="9cb77-105">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="9cb77-106">認証は、ユーザーの ID を確実に突き止めるのプロセスです。</span><span class="sxs-lookup"><span data-stu-id="9cb77-106">Authentication is the process of reliably ascertaining a user’s identity.</span></span>

<span data-ttu-id="9cb77-107">マイクロサービスのシナリオでは、通常、認証は一元的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-107">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="9cb77-108">API ゲートウェイを使用している場合は、図 11-1 に示すように、ゲートウェイが認証をするのに適しています。</span><span class="sxs-lookup"><span data-stu-id="9cb77-108">If you are using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 11-1.</span></span> <span data-ttu-id="9cb77-109">このアプローチを使用する場合は、メッセージがゲートウェイから来たかどうかに関わらず、メッセージの認証に追加のセキュリティ保護がない限り、(API ゲートウェイなしで) 個々のマイクロサービスに直接到達できないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cb77-109">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![](./media/image1.png)

<span data-ttu-id="9cb77-110">**図 11-1**. </span><span class="sxs-lookup"><span data-stu-id="9cb77-110">**Figure 11-1**.</span></span> <span data-ttu-id="9cb77-111">API ゲートウェイによる認証の一元管理</span><span class="sxs-lookup"><span data-stu-id="9cb77-111">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="9cb77-112">サービスに直接アクセスできる場合は、Azure Active Directory などの認証サービスやセキュリティ トークン サービス (STS) として機能する専用の認証マイクロサービスは、ユーザーを認証するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-112">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="9cb77-113">信頼の決定は、サービスとセキュリティ トークンまたは cookie 間で共有されます </span><span class="sxs-lookup"><span data-stu-id="9cb77-113">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="9cb77-114">(必要に応じて、これらは ASP.NET Core で[データ保護サービス](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)を使用して、アプリケーション間で共有できます)。このパターンを示したものが図 11-2 です。</span><span class="sxs-lookup"><span data-stu-id="9cb77-114">(These can be shared between applications, if needed, in ASP.NET Core with [data protection services](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 11-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="9cb77-115">**図 11-2**. </span><span class="sxs-lookup"><span data-stu-id="9cb77-115">**Figure 11-2**.</span></span> <span data-ttu-id="9cb77-116">ID マイクロサービスによる認証、信頼は認証トークンを使用して共有</span><span class="sxs-lookup"><span data-stu-id="9cb77-116">Authentication by identity microservice; trust is shared using an authorization token</span></span>

## <a name="authenticating-using-aspnet-core-identity"></a><span data-ttu-id="9cb77-117">ASP.NET Core Identity を使用した認証</span><span class="sxs-lookup"><span data-stu-id="9cb77-117">Authenticating using ASP.NET Core Identity</span></span>

<span data-ttu-id="9cb77-118">アプリケーションのユーザーを識別するための ASP.NET Core の主要なメカニズムは、[ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) メンバーシップ システムです。</span><span class="sxs-lookup"><span data-stu-id="9cb77-118">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="9cb77-119">ASP.NET Core Identity は、ユーザー情報 (サインイン情報、ロール、およびクレームを含む) を開発者によって構成されたデータ ストアに格納します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-119">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="9cb77-120">通常、ASP.NET Core Identity データ ストアは、Microsoft.AspNetCore.Identity.EntityFrameworkCore パッケージで提供される、Entity Framework ストアです。</span><span class="sxs-lookup"><span data-stu-id="9cb77-120">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the Microsoft.AspNetCore.Identity.EntityFrameworkCore package.</span></span> <span data-ttu-id="9cb77-121">ただし、カスタム ストアまたはその他のサード パーティのパッケージを使用して、ID 情報を Azure Table Storage、DocumentDB、またはその他の場所に格納することができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-121">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, DocumentDB, or other locations.</span></span>

<span data-ttu-id="9cb77-122">次のコードは、個々のユーザー アカウントの認証が選択された ASP.NET Core Web アプリケーション プロジェクト テンプレートから取得されます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-122">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="9cb77-123">これは Startup.ConfigureServices メソッドで EntityFramework.Core を使用して ASP.NET Core Identity を構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-123">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="9cb77-124">ASP.NET Core Identity が構成されると、サービスの Startup.Configure メソッドで app.UseIdentity を呼び出して有効にします。</span><span class="sxs-lookup"><span data-stu-id="9cb77-124">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s Startup.Configure method.</span></span>

<span data-ttu-id="9cb77-125">ASP.NET Code Identity を使用すると、次の複数のシナリオが実現できます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-125">Using ASP.NET Code Identity enables several scenarios:</span></span>

-   <span data-ttu-id="9cb77-126">UserManager 型 (userManager.CreateAsync) を使用して、新しいユーザー情報を作成する。</span><span class="sxs-lookup"><span data-stu-id="9cb77-126">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

-   <span data-ttu-id="9cb77-127">SignInManager 型を使用してユーザーを認証する。</span><span class="sxs-lookup"><span data-stu-id="9cb77-127">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="9cb77-128">signInManager.SignInAsync を使用して直接サインインすることも、signInManager.PasswordSignInAsync を使用してユーザーのパスワードが正しいことを確認してからサインインすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-128">You can use signInManager.SignInAsync to sign in directly, or signInManager.PasswordSignInAsync to confirm the user’s password is correct and then sign them in.</span></span>

-   <span data-ttu-id="9cb77-129">ブラウザーからの後続の要求にサインイン ユーザーの ID とクレームが含まれるように、cookie に格納されている情報 (ASP.NET Core Identity ミドルウェアで読み取られます) に基づいてユーザーを識別します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-129">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="9cb77-130">ASP.NET Core Identity は [2 要素認証](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9cb77-130">ASP.NET Core Identity also supports [two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="9cb77-131">ローカル ユーザーのデータ ストアを利用する認証シナリオや、cookie を使用して要求間で ID を保持する認証シナリオ (MVC web アプリケーションでは一般的) では、ASP.NET Core Identity が推奨されるソリューションです。</span><span class="sxs-lookup"><span data-stu-id="9cb77-131">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

## <a name="authenticating-using-external-providers"></a><span data-ttu-id="9cb77-132">外部プロバイダーを使用した認証</span><span class="sxs-lookup"><span data-stu-id="9cb77-132">Authenticating using external providers</span></span>

<span data-ttu-id="9cb77-133">ASP.NET Core は、ユーザーが [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) フローを経由してログインできるように、[外部認証プロバイダー](https://docs.microsoft.com/aspnet/core/security/authentication/social/)の使用もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9cb77-133">ASP.NET Core also supports using [external authentication providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) to let users log in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="9cb77-134">つまり、ユーザーは Microsoft、Google、Facebook、Twitter などのプロバイダーの既存の認証プロセスを使用してログインし、アプリケーションでこれらの ID を ASP.NET Core Identity に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-134">This means that users can log in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="9cb77-135">外部認証を使用するには、アプリケーションの HTTP 要求処理パイプラインに適切な認証ミドルウェアを含めます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-135">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="9cb77-136">このミドルウェアは、認証プロバイダーから URI ルートを返すために要求を処理し、ID 情報をキャプチャし、SignInManager.GetExternalLoginInfo メソッドを介して使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9cb77-136">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="9cb77-137">よく利用されている外部認証プロバイダーと、関連付けられている NuGet パッケージを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-137">Popular external authentication providers and their associated NuGet packages are shown below.</span></span>

<span data-ttu-id="9cb77-138">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span><span class="sxs-lookup"><span data-stu-id="9cb77-138">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span></span>

<span data-ttu-id="9cb77-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span><span class="sxs-lookup"><span data-stu-id="9cb77-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span></span>

<span data-ttu-id="9cb77-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span><span class="sxs-lookup"><span data-stu-id="9cb77-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span></span>

<span data-ttu-id="9cb77-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span><span class="sxs-lookup"><span data-stu-id="9cb77-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span></span>

<span data-ttu-id="9cb77-142">いずれの場合も、ミドルウェアは、Startup.Configure の app.Use{ExternalProvider}Authentication に似た登録メソッドの呼び出しに登録されます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-142">In all cases, the middleware is registered with a call to a registration method similar to app.Use{ExternalProvider}Authentication in Startup.Configure.</span></span> <span data-ttu-id="9cb77-143">これらの登録メソッドは、プロバイダーが必要とするアプリケーション ID と機密情報 (パスワードなど) を含むオプション オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-143">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="9cb77-144">外部認証プロバイダーは、([ASP.NET Core のドキュメントで説明されているように](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) ユーザーに ID へのアクセスを求めているアプリケーションを通知するため、アプリケーションの登録を求めます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-144">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="9cb77-145">ミドルウェアが Startup.Configure で登録されると、ユーザーに任意のコントローラー アクションからログインを求めることができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-145">Once the middleware is registered in Startup.Configure, you can prompt users to log in from any controller action.</span></span> <span data-ttu-id="9cb77-146">これを行うには、認証プロバイダー名とリダイレクト URL を含む AuthenticationProperties オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-146">To do this, you create an AuthenticationProperties object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="9cb77-147">そして、AuthenticationProperties オブジェクトを渡すチャレンジ応答を返します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-147">You then return a Challenge response that passes the AuthenticationProperties object.</span></span> <span data-ttu-id="9cb77-148">この例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-148">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="9cb77-149">redirectUrl パラメーターには、ユーザーが認証された後に外部プロバイダーがリダイレクトされる URL が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9cb77-149">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="9cb77-150">URL は、次の簡素化した例のように、外部の ID 情報に基づいてユーザーをサインインさせるアクションを表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cb77-150">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

<span data-ttu-id="9cb77-151">Visual Studio で ASP.NET コードの Web アプリケーション プロジェクトを作成するときに、**[個人のユーザー アカウント]** 認証オプションを選択すると、図 11-3 に示すように、外部プロバイダーでサインインするために必要なすべてのコードがすでにプロジェクト内にあります。</span><span class="sxs-lookup"><span data-stu-id="9cb77-151">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 11-3.</span></span>

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

<span data-ttu-id="9cb77-152">**図 11-3**. </span><span class="sxs-lookup"><span data-stu-id="9cb77-152">**Figure 11-3**.</span></span> <span data-ttu-id="9cb77-153">Web アプリケーション プロジェクトを作成するときに、外部の認証を使用するためのオプションを選択する</span><span class="sxs-lookup"><span data-stu-id="9cb77-153">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="9cb77-154">より多くの外部認証プロバイダーを使用するため、上記で一覧表示した外部の認証プロバイダーの他に、ミドルウェアを提供するサード パーティのパッケージが使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-154">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="9cb77-155">リストについては、GitHub で [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) のリポジトリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cb77-155">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="9cb77-156">もちろん、独自の外部認証ミドルウェアも作成できます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-156">It is also possible, of course, to create your own external authentication middleware.</span></span>

## <a name="authenticating-with-bearer-tokens"></a><span data-ttu-id="9cb77-157">ベアラー トークンによる認証</span><span class="sxs-lookup"><span data-stu-id="9cb77-157">Authenticating with bearer tokens</span></span>

<span data-ttu-id="9cb77-158">ASP.NET Core Identity (または Identity と外部認証プロバイダー) を使用した認証は、ユーザー情報を cookie に格納する多くの Web アプリケーションのシナリオに適してします。</span><span class="sxs-lookup"><span data-stu-id="9cb77-158">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="9cb77-159">しかし、それ以外のシナリオでは、cookie はデータを保持および送信する通常の方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="9cb77-159">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="9cb77-160">たとえば、Single Page Application (SPA)、ネイティブ クライアント、または他の Web API によってアクセスできる RESTful エンドポイントを公開する ASP.NET Core Web API では、代わりにベアラー トークン認証を使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="9cb77-160">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="9cb77-161">この種のアプリケーションでは cookie を使用しませんが、簡単にベアラー トークンを取得してそれを後続の要求の承認ヘッダーに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-161">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="9cb77-162">トークン認証を有効にするため、ASP.NET Core は [OAuth 2.0](https://oauth.net/2/) および [OpenID Connect](https://openid.net/connect/) を使用するための複数のオプションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9cb77-162">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="9cb77-163">OpenID Connect または OAuth 2.0 ID プロバイダーによる認証</span><span class="sxs-lookup"><span data-stu-id="9cb77-163">Authenticating with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="9cb77-164">ユーザー情報が Azure Active Directory または OpenID Connect または OAuth 2.0 をサポートする別の ID ソリューションに格納されている場合は、Microsoft.AspNetCore.Authentication.OpenIdConnect パッケージを使用して、OpenID Connect ワークフローの使用を認証することができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-164">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the Microsoft.AspNetCore.Authentication.OpenIdConnect package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="9cb77-165">たとえば、 [Azure Active Directory に対して認証](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)するには、ASP.NET Core Web アプリケーションは、次の例に示すように、そのパッケージのミドルウェアを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-165">For example, to [authenticate against Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), an ASP.NET Core web application can use middleware from that package as shown in the following example:</span></span>

```csharp
// Configure the OWIN pipeline to use OpenID Connect auth
app.UseOpenIdConnectAuthentication(new OpenIdConnectOptions
{
    ClientId = Configuration["AzureAD:ClientId"],
    Authority = String.Format(Configuration["AzureAd:AadInstance"],
    Configuration["AzureAd:Tenant"]),
    ResponseType = OpenIdConnectResponseType.IdToken,
    PostLogoutRedirectUri = Configuration["AzureAd:PostLogoutRedirectUri"]
});
```

<span data-ttu-id="9cb77-166">構成値は、アプリケーションが [Azure AD クライアントとして登録される](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad)ときに作成される Azure Active Directory 値です。</span><span class="sxs-lookup"><span data-stu-id="9cb77-166">The configuration values are Azure Active Directory values that are created when your application is [registered as an Azure AD client](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span></span> <span data-ttu-id="9cb77-167">アプリケーション内の複数のマイクロサービスがすべて Azure Active Directory 通じて認証されたユーザーを認証する必要がある場合、1 つのクライアント ID をこれらで共有することができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-167">A single client ID can be shared among multiple microservices in an application if they all need to authenticate users authenticated via Azure Active Directory.</span></span>

<span data-ttu-id="9cb77-168">このワークフローを使用すると、すべてのユーザー情報ストレージと認証が Azure Active Directory によって処理されるため、ASP.NET Core Identity ミドルウェアは必要ないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9cb77-168">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by Azure Active Directory.</span></span>

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="9cb77-169">ASP.NET Core サービスからのセキュリティ トークンの発行</span><span class="sxs-lookup"><span data-stu-id="9cb77-169">Issuing security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="9cb77-170">外部 ID プロバイダーを使用するよりも、ローカルの ASP.NET Core Identity ユーザーにセキュリティ トークンを発行する場合は、優れたサード パーティ ライブラリを利用することができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-170">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="9cb77-171">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) と [OpenIddict](https://github.com/openiddict/openiddict-core) は、ASP.NET Core Identity と簡単に統合して ASP.NET Core サービスからセキュリティ トークンを発行できるようにする OpenID Connect プロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="9cb77-171">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="9cb77-172">[IdentityServer4 ドキュメント](https://identityserver4.readthedocs.io/en/release/)には、ライブラリの詳しい使用方法が記載されています。</span><span class="sxs-lookup"><span data-stu-id="9cb77-172">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/release/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="9cb77-173">ただし、IdentityServer4 を使用してトークンを発行する基本的な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9cb77-173">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1.  <span data-ttu-id="9cb77-174">Startup.Configure メソッドで app.UseIdentityServer を呼び出して、IdentityServer4 をアプリケーションの HTTP 要求処理パイプラインに追加します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-174">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="9cb77-175">これにより、ライブラリが /connect/token などの OpenID Connect エンドポイントと OAuth2 エンドポイントに要求を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-175">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2.  <span data-ttu-id="9cb77-176">services.AddIdentityServer を呼び出して、Startup.ConfigureServices で IdentityServer4 を構成します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-176">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3.  <span data-ttu-id="9cb77-177">ID サーバーを構成するには、次のデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-177">You configure identity server by providing the following data:</span></span>

-   <span data-ttu-id="9cb77-178">署名に使用する[資格情報](https://identityserver4.readthedocs.io/en/release/topics/crypto.html)。</span><span class="sxs-lookup"><span data-stu-id="9cb77-178">The [credentials](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) to use for signing.</span></span>

-   <span data-ttu-id="9cb77-179">ユーザーがアクセスを要求する可能性がある [ID と API リソース](https://identityserver4.readthedocs.io/en/release/topics/resources.html)。</span><span class="sxs-lookup"><span data-stu-id="9cb77-179">The [Identity and API resources](https://identityserver4.readthedocs.io/en/release/topics/resources.html) that users might request access to:</span></span>

<!-- -->

-   <span data-ttu-id="9cb77-180">API リソースは、保護されたデータまたはユーザーがアクセス トークンを使用してアクセスできる機能を表します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-180">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="9cb77-181">認証を必要とする Web API (または API のセット) は、API リソースの一例です。</span><span class="sxs-lookup"><span data-stu-id="9cb77-181">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

-   <span data-ttu-id="9cb77-182">ID リソースは、ユーザーを識別するためにクライアントに与えられる情報 (クレーム) を表します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-182">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="9cb77-183">クレームには、ユーザー名、メール アドレスなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-183">The claims might include the user name, email address, and so on.</span></span>

<!-- -->

-   <span data-ttu-id="9cb77-184">トークンを要求するために接続する[クライアント](https://identityserver4.readthedocs.io/en/release/topics/clients.html)。</span><span class="sxs-lookup"><span data-stu-id="9cb77-184">The [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) that will be connecting in order to request tokens.</span></span>

-   <span data-ttu-id="9cb77-185">[ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) または代替手段など、ユーザー情報のためのストレージ メカニズム。</span><span class="sxs-lookup"><span data-stu-id="9cb77-185">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) or an alternative.</span></span>

<span data-ttu-id="9cb77-186">使用する IdentityServer4 のクライアントとリソースを指定するときに、適切な型の IEnumerable&lt;T&gt; コレクションをメモリ内のクライアントまたはリソースのストアを受け取るメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-186">When you specify clients and resources for IdentityServer4 to use, you can pass an IEnumerable&lt;T&gt; collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="9cb77-187">またはより複雑なシナリオでは、依存関係の挿入を通じて、クライアントまたはリソース プロバイダーの型を提供できます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-187">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="9cb77-188">カスタム IClientStore 型によって渡されるメモリ内のリソースおよびクライアントを使用する IdentityServer4 のサンプル構成は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="9cb77-188">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a><span data-ttu-id="9cb77-189">セキュリティ トークンの使用</span><span class="sxs-lookup"><span data-stu-id="9cb77-189">Consuming security tokens</span></span>

<span data-ttu-id="9cb77-190">OpenID Connect エンドポイントに対して認証する、または独自のセキュリティ トークンを発行することで、いくつかのシナリオをカバーすることはできます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-190">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="9cb77-191">しかし、異なるサービスで提供された有効なセキュリティ トークンを持つユーザーにアクセスを制限する必要があるサービスの場合はどうでしょうか。</span><span class="sxs-lookup"><span data-stu-id="9cb77-191">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="9cb77-192">そのシナリオでは、JWT トークンを処理する認証ミドルウェアが Microsoft.AspNetCore.Authentication.JwtBearer パッケージで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-192">For that scenario, authentication middleware that handles JWT tokens is available in the Microsoft.AspNetCore.Authentication.JwtBearer package.</span></span> <span data-ttu-id="9cb77-193">JWT は "[JSON Web トークン](https://tools.ietf.org/html/rfc7519)" を表し、セキュリティ クレームの通信のための一般的なセキュリティ トークン形式 (RFC 7519 で定義) です。</span><span class="sxs-lookup"><span data-stu-id="9cb77-193">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="9cb77-194">このようなトークンを使用するミドルウェアの使用方法の簡単な例は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="9cb77-194">A simple example of how to use middleware to consume such tokens might look like the following example.</span></span> <span data-ttu-id="9cb77-195">このコードは、ASP.NET Core MVC ミドルウェア (app.UseMvc) の呼び出しの前に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cb77-195">This code must precede calls to ASP.NET Core MVC middleware (app.UseMvc).</span></span>

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

<span data-ttu-id="9cb77-196">この使用法でのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9cb77-196">The parameters in this usage are:</span></span>

-   <span data-ttu-id="9cb77-197">Audience は、受信トークンの受信者またはそのトークンでアクセスできるリソースを表します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-197">Audience represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="9cb77-198">このパラメーターで指定された値がトークン内の aud パラメーターと一致しない場合、そのトークンは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-198">If the value specified in this parameter does not match the aud parameter in the token, the token will be rejected.</span></span>

-   <span data-ttu-id="9cb77-199">Authority は、トークン発行認証サーバーのアドレスです。</span><span class="sxs-lookup"><span data-stu-id="9cb77-199">Authority is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="9cb77-200">JWT ベアラー認証ミドルウェアでは、この URI を使用して、トークンの署名の検証に使用できる公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-200">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="9cb77-201">ミドルウェアは、トークン内の iss パラメーターがこの URI と一致していることも確認します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-201">The middleware also confirms that the iss parameter in the token matches this URI.</span></span>

-   <span data-ttu-id="9cb77-202">AutomaticAuthenticate は、トークンで定義されているユーザーが自動的にサインインされるかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="9cb77-202">AutomaticAuthenticate is a Boolean value that indicates whether the user defined by the token should be automatically signed in.</span></span>

<span data-ttu-id="9cb77-203">もう 1 つのパラメーター RequireHttpsMetadata は、この例では使用されません。</span><span class="sxs-lookup"><span data-stu-id="9cb77-203">Another parameter, RequireHttpsMetadata, is not used in this example.</span></span> <span data-ttu-id="9cb77-204">このパラメーターはテスト目的に便利です。証明書がない環境でテストができるように、このパラメーターを false に設定します。</span><span class="sxs-lookup"><span data-stu-id="9cb77-204">It is useful for testing purposes; you set this parameter to false so that you can test in environments where you do not have certificates.</span></span> <span data-ttu-id="9cb77-205">実際の展開では、JWT ベアラー トークンは常に HTTPS 経由でのみ渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cb77-205">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="9cb77-206">このミドルウェアを配置すると、JWT トークンが承認ヘッダーから自動的に抽出されます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-206">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="9cb77-207">これらのトークンは、逆シリアル化され、(Audience パラメーターと Authority パラメーターの値を使用して) 検証され、MVC アクションまたは認証フィルターが後で参照するユーザー情報として格納されます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-207">They are then deserialized, validated (using the values in the Audience and Authority parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="9cb77-208">JWT ベアラー認証ミドルウェアは、証明機関が利用できない場合に、ローカルの証明書を使用してトークンを検証するなどの高度なシナリオもサポートできます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-208">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="9cb77-209">このシナリオでは、JwtBearerOptions オブジェクトで TokenValidationParameters オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9cb77-209">For this scenario, you can specify a TokenValidationParameters object in the JwtBearerOptions object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9cb77-210">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="9cb77-210">Additional resources</span></span>

-   <span data-ttu-id="9cb77-211">**アプリケーション間で Cookie を共有する**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span><span class="sxs-lookup"><span data-stu-id="9cb77-211">**Sharing cookies between applications**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span></span>

-   <span data-ttu-id="9cb77-212">**Identity の概要**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="9cb77-212">**Introduction to Identity**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="9cb77-213">**Rick Anderson の SMS での 2 要素認証**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="9cb77-213">**Rick Anderson. Two-factor authentication with SMS**
[*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span></span>

-   <span data-ttu-id="9cb77-214">**Facebook、Google、および他の外部プロバイダーを使用する認証の有効化**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="9cb77-214">**Enabling authentication using Facebook, Google and other external providers**
[*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span></span>

-   <span data-ttu-id="9cb77-215">**Michell Anicas の OAuth 2 の概要**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="9cb77-215">**Michell Anicas. An Introduction to OAuth 2**
[*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span></span>

-   <span data-ttu-id="9cb77-216">**AspNet.Security.OAuth.Providers** (ASP.NET OAuth プロバイダーの GitHub リポジトリ)</span><span class="sxs-lookup"><span data-stu-id="9cb77-216">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span>
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   <span data-ttu-id="9cb77-217">**Danny Strockis の ASP.NET Core Web アプリへの Azure AD の統合**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span><span class="sxs-lookup"><span data-stu-id="9cb77-217">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app**
[*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span></span>

-   <span data-ttu-id="9cb77-218">**IdentityServer4 の公式ドキュメント**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span><span class="sxs-lookup"><span data-stu-id="9cb77-218">**IdentityServer4. Official documentation**
[*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="9cb77-219">[前へ] (../implement-resilient-applications/monitor-app-health.md) [次へ] (承認-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="9cb77-219">[Previous] (../implement-resilient-applications/monitor-app-health.md) [Next] (authorization-net-microservices-web-applications.md)</span></span>
