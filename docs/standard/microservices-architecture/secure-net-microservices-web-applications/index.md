---
title: "NET マイクロサービスおよび Web アプリケーションをセキュリティで保護する"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | .NET マイクロサービスおよび Web アプリケーションをセキュリティで保護する"
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
ms.openlocfilehash: 6281442f42b511170f83eaeb1c940a35a566e519
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="securing-net-microservices-and-web-applications"></a>NET マイクロサービスおよび Web アプリケーションをセキュリティで保護する

サービスによって公開されるリソースおよび API は多くの場合、特定の信頼されたユーザーまたはクライアントに制限する必要があります。 このような API レベルの信頼の決定を行うための最初の手順は、認証です。 認証は、ユーザーの ID を確実に突き止めるのプロセスです。

マイクロサービスのシナリオでは、通常、認証は一元的に処理されます。 API ゲートウェイを使用している場合は、図 11-1 に示すように、ゲートウェイが認証をするのに適しています。 このアプローチを使用する場合は、メッセージがゲートウェイから来たかどうかに関わらず、メッセージの認証に追加のセキュリティ保護がない限り、(API ゲートウェイなしで) 個々のマイクロサービスに直接到達できないようにする必要があります。

![](./media/image1.png)

**図 11-1**.  API ゲートウェイによる認証の一元管理

サービスに直接アクセスできる場合は、Azure Active Directory などの認証サービスやセキュリティ トークン サービス (STS) として機能する専用の認証マイクロサービスは、ユーザーを認証するために使用できます。 信頼の決定は、サービスとセキュリティ トークンまたは cookie 間で共有されます  (必要に応じて、これらは ASP.NET Core で[データ保護サービス](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)を使用して、アプリケーション間で共有できます)。このパターンを示したものが図 11-2 です。

![](./media/image2.png)

**図 11-2**.  ID マイクロサービスによる認証、信頼は認証トークンを使用して共有

## <a name="authenticating-using-aspnet-core-identity"></a>ASP.NET Core Identity を使用した認証

アプリケーションのユーザーを識別するための ASP.NET Core の主要なメカニズムは、[ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) メンバーシップ システムです。 ASP.NET Core Identity は、ユーザー情報 (サインイン情報、ロール、およびクレームを含む) を開発者によって構成されたデータ ストアに格納します。 通常、ASP.NET Core Identity データ ストアは、Microsoft.AspNetCore.Identity.EntityFrameworkCore パッケージで提供される、Entity Framework ストアです。 ただし、カスタム ストアまたはその他のサード パーティのパッケージを使用して、ID 情報を Azure Table Storage、DocumentDB、またはその他の場所に格納することができます。

次のコードは、個々のユーザー アカウントの認証が選択された ASP.NET Core Web アプリケーション プロジェクト テンプレートから取得されます。 これは Startup.ConfigureServices メソッドで EntityFramework.Core を使用して ASP.NET Core Identity を構成する方法を示します。

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

ASP.NET Core Identity が構成されると、サービスの Startup.Configure メソッドで app.UseIdentity を呼び出して有効にします。

ASP.NET Code Identity を使用すると、次の複数のシナリオが実現できます。

-   UserManager 型 (userManager.CreateAsync) を使用して、新しいユーザー情報を作成する。

-   SignInManager 型を使用してユーザーを認証する。 signInManager.SignInAsync を使用して直接サインインすることも、signInManager.PasswordSignInAsync を使用してユーザーのパスワードが正しいことを確認してからサインインすることもできます。

-   ブラウザーからの後続の要求にサインイン ユーザーの ID とクレームが含まれるように、cookie に格納されている情報 (ASP.NET Core Identity ミドルウェアで読み取られます) に基づいてユーザーを識別します。

ASP.NET Core Identity は [2 要素認証](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)もサポートしています。

ローカル ユーザーのデータ ストアを利用する認証シナリオや、cookie を使用して要求間で ID を保持する認証シナリオ (MVC web アプリケーションでは一般的) では、ASP.NET Core Identity が推奨されるソリューションです。

## <a name="authenticating-using-external-providers"></a>外部プロバイダーを使用した認証

ASP.NET Core は、ユーザーが [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) フローを経由してログインできるように、[外部認証プロバイダー](https://docs.microsoft.com/aspnet/core/security/authentication/social/)の使用もサポートしています。 つまり、ユーザーは Microsoft、Google、Facebook、Twitter などのプロバイダーの既存の認証プロセスを使用してログインし、アプリケーションでこれらの ID を ASP.NET Core Identity に関連付けることができます。

外部認証を使用するには、アプリケーションの HTTP 要求処理パイプラインに適切な認証ミドルウェアを含めます。 このミドルウェアは、認証プロバイダーから URI ルートを返すために要求を処理し、ID 情報をキャプチャし、SignInManager.GetExternalLoginInfo メソッドを介して使用できるようにします。

よく利用されている外部認証プロバイダーと、関連付けられている NuGet パッケージを以下に示します。

**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount

**Google:** Microsoft.AspNetCore.Authentication.Google

**Facebook:** Microsoft.AspNetCore.Authentication.Facebook

**Twitter:** Microsoft.AspNetCore.Authentication.Twitter

いずれの場合も、ミドルウェアは、Startup.Configure の app.Use{ExternalProvider}Authentication に似た登録メソッドの呼び出しに登録されます。 これらの登録メソッドは、プロバイダーが必要とするアプリケーション ID と機密情報 (パスワードなど) を含むオプション オブジェクトを取得します。 外部認証プロバイダーは、([ASP.NET Core のドキュメントで説明されているように](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) ユーザーに ID へのアクセスを求めているアプリケーションを通知するため、アプリケーションの登録を求めます。

ミドルウェアが Startup.Configure で登録されると、ユーザーに任意のコントローラー アクションからログインを求めることができます。 これを行うには、認証プロバイダー名とリダイレクト URL を含む AuthenticationProperties オブジェクトを作成します。 そして、AuthenticationProperties オブジェクトを渡すチャレンジ応答を返します。 この例を次のコードに示します。

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

redirectUrl パラメーターには、ユーザーが認証された後に外部プロバイダーがリダイレクトされる URL が含まれています。 URL は、次の簡素化した例のように、外部の ID 情報に基づいてユーザーをサインインさせるアクションを表す必要があります。

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

Visual Studio で ASP.NET コードの Web アプリケーション プロジェクトを作成するときに、**[個人のユーザー アカウント]** 認証オプションを選択すると、図 11-3 に示すように、外部プロバイダーでサインインするために必要なすべてのコードがすでにプロジェクト内にあります。

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

**図 11-3**.  Web アプリケーション プロジェクトを作成するときに、外部の認証を使用するためのオプションを選択する

より多くの外部認証プロバイダーを使用するため、上記で一覧表示した外部の認証プロバイダーの他に、ミドルウェアを提供するサード パーティのパッケージが使用できます。 リストについては、GitHub で [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) のリポジトリを参照してください。

もちろん、独自の外部認証ミドルウェアも作成できます。

## <a name="authenticating-with-bearer-tokens"></a>ベアラー トークンによる認証

ASP.NET Core Identity (または Identity と外部認証プロバイダー) を使用した認証は、ユーザー情報を cookie に格納する多くの Web アプリケーションのシナリオに適してします。 しかし、それ以外のシナリオでは、cookie はデータを保持および送信する通常の方法ではありません。

たとえば、Single Page Application (SPA)、ネイティブ クライアント、または他の Web API によってアクセスできる RESTful エンドポイントを公開する ASP.NET Core Web API では、代わりにベアラー トークン認証を使用するのが一般的です。 この種のアプリケーションでは cookie を使用しませんが、簡単にベアラー トークンを取得してそれを後続の要求の承認ヘッダーに含めることができます。 トークン認証を有効にするため、ASP.NET Core は [OAuth 2.0](https://oauth.net/2/) および [OpenID Connect](http://openid.net/connect/) を使用するための複数のオプションをサポートしています。

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a>OpenID Connect または OAuth 2.0 ID プロバイダーによる認証

ユーザー情報が Azure Active Directory または OpenID Connect または OAuth 2.0 をサポートする別の ID ソリューションに格納されている場合は、Microsoft.AspNetCore.Authentication.OpenIdConnect パッケージを使用して、OpenID Connect ワークフローの使用を認証することができます。 たとえば、 [Azure Active Directory に対して認証](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)するには、ASP.NET Core Web アプリケーションは、次の例に示すように、そのパッケージのミドルウェアを使用できます。

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

構成値は、アプリケーションが [Azure AD クライアントとして登録される](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad)ときに作成される Azure Active Directory 値です。 アプリケーション内の複数のマイクロサービスがすべて Azure Active Directory 通じて認証されたユーザーを認証する必要がある場合、1 つのクライアント ID をこれらで共有することができます。

このワークフローを使用すると、すべてのユーザー情報ストレージと認証が Azure Active Directory によって処理されるため、ASP.NET Core Identity ミドルウェアは必要ないことに注意してください。

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a>ASP.NET Core サービスからのセキュリティ トークンの発行

外部 ID プロバイダーを使用するよりも、ローカルの ASP.NET Core Identity ユーザーにセキュリティ トークンを発行する場合は、優れたサード パーティ ライブラリを利用することができます。

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) と [OpenIddict](https://github.com/openiddict/openiddict-core) は、ASP.NET Core Identity と簡単に統合して ASP.NET Core サービスからセキュリティ トークンを発行できるようにする OpenID Connect プロバイダーです。 [IdentityServer4 ドキュメント](https://identityserver4.readthedocs.io/en/release/)には、ライブラリの詳しい使用方法が記載されています。 ただし、IdentityServer4 を使用してトークンを発行する基本的な手順は次のとおりです。

1.  Startup.Configure メソッドで app.UseIdentityServer を呼び出して、IdentityServer4 をアプリケーションの HTTP 要求処理パイプラインに追加します。 これにより、ライブラリが /connect/token などの OpenID Connect エンドポイントと OAuth2 エンドポイントに要求を提供することができます。

2.  services.AddIdentityServer を呼び出して、Startup.ConfigureServices で IdentityServer4 を構成します。

3.  ID サーバーを構成するには、次のデータを提供します。

-   署名に使用する[資格情報](https://identityserver4.readthedocs.io/en/release/topics/crypto.html)。

-   ユーザーがアクセスを要求する可能性がある [ID と API リソース](https://identityserver4.readthedocs.io/en/release/topics/resources.html)。

<!-- -->

-   API リソースは、保護されたデータまたはユーザーがアクセス トークンを使用してアクセスできる機能を表します。 認証を必要とする Web API (または API のセット) は、API リソースの一例です。

-   ID リソースは、ユーザーを識別するためにクライアントに与えられる情報 (クレーム) を表します。 クレームには、ユーザー名、メール アドレスなどが含まれます。

<!-- -->

-   トークンを要求するために接続する[クライアント](https://identityserver4.readthedocs.io/en/release/topics/clients.html)。

-   [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) または代替手段など、ユーザー情報のためのストレージ メカニズム。

使用する IdentityServer4 のクライアントとリソースを指定するときに、適切な型の IEnumerable&lt;T&gt; コレクションをメモリ内のクライアントまたはリソースのストアを受け取るメソッドに渡すことができます。 またはより複雑なシナリオでは、依存関係の挿入を通じて、クライアントまたはリソース プロバイダーの型を提供できます。

カスタム IClientStore 型によって渡されるメモリ内のリソースおよびクライアントを使用する IdentityServer4 のサンプル構成は、次の例のようになります。

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a>セキュリティ トークンの使用

OpenID Connect エンドポイントに対して認証する、または独自のセキュリティ トークンを発行することで、いくつかのシナリオをカバーすることはできます。 しかし、異なるサービスで提供された有効なセキュリティ トークンを持つユーザーにアクセスを制限する必要があるサービスの場合はどうでしょうか。

そのシナリオでは、JWT トークンを処理する認証ミドルウェアが Microsoft.AspNetCore.Authentication.JwtBearer パッケージで使用できます。 JWT は "[JSON Web トークン](https://tools.ietf.org/html/rfc7519)" を表し、セキュリティ クレームの通信のための一般的なセキュリティ トークン形式 (RFC 7519 で定義) です。 このようなトークンを使用するミドルウェアの使用方法の簡単な例は、次の例のようになります。 このコードは、ASP.NET Core MVC ミドルウェア (app.UseMvc) の呼び出しの前に置く必要があります。

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

この使用法でのパラメーターは次のとおりです。

-   Audience は、受信トークンの受信者またはそのトークンでアクセスできるリソースを表します。 このパラメーターで指定された値がトークン内の aud パラメーターと一致しない場合、そのトークンは拒否されます。

-   Authority は、トークン発行認証サーバーのアドレスです。 JWT ベアラー認証ミドルウェアでは、この URI を使用して、トークンの署名の検証に使用できる公開キーを取得します。 ミドルウェアは、トークン内の iss パラメーターがこの URI と一致していることも確認します。

-   AutomaticAuthenticate は、トークンで定義されているユーザーが自動的にサインインされるかどうかを示すブール値です。

もう 1 つのパラメーター RequireHttpsMetadata は、この例では使用されません。 このパラメーターはテスト目的に便利です。証明書がない環境でテストができるように、このパラメーターを false に設定します。 実際の展開では、JWT ベアラー トークンは常に HTTPS 経由でのみ渡す必要があります。

このミドルウェアを配置すると、JWT トークンが承認ヘッダーから自動的に抽出されます。 これらのトークンは、逆シリアル化され、(Audience パラメーターと Authority パラメーターの値を使用して) 検証され、MVC アクションまたは認証フィルターが後で参照するユーザー情報として格納されます。

JWT ベアラー認証ミドルウェアは、証明機関が利用できない場合に、ローカルの証明書を使用してトークンを検証するなどの高度なシナリオもサポートできます。 このシナリオでは、JwtBearerOptions オブジェクトで TokenValidationParameters オブジェクトを指定できます。

## <a name="additional-resources"></a>その他の技術情報

-   **アプリケーション間で cookie を共有する**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

-   **Identity の概要**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Rick Anderson の SMS での 2 要素認証**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)

-   **Facebook、Google、他の外部プロバイダーを使用する認証の有効化**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)

-   **Michell Anicas の OAuth 2 の概要**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

-   **AspNet.Security.OAuth.Providers** (ASP.NET OAuth プロバイダーの GitHub リポジトリ)
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   **Danny Strockis の ASP.NET Core Web アプリへの Azure AD の統合**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

-   **IdentityServer4 の公式ドキュメント**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)


>[!div class="step-by-step"]
[前へ] (../implement-resilient-applications/monitor-app-health.md) [次へ] (承認-net-microservices-web-applications.md)
