---
title: .NET マイクロサービスと Web アプリケーションでの承認について
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | .NET マイクロサービスと Web アプリケーションでの承認について
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7b2981579f28c083a31d7af6ae42f4e3ca8bbd88
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105502"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>.NET マイクロサービスと Web アプリケーションでの承認について

認証の後に、ASP.NET Core Web API がアクセスを承認する必要があります。 このプロセスによって、サービスが一部の認証ユーザーに API を提供できますが、すべてのユーザーではありません。 [承認](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)は、ユーザーのロールまたはカスタム ポリシーに基づいて行われ、要求またはその他のヒューリスティックの調査が含まれる場合があります。

次の例に示すように、ASP.NET Core MVC ルートへのアクセス制限は、アクション メソッド (またはすべてのコントローラーのアクションで承認が必要な場合は、コントローラーのクラス) に Authorize 属性を適用するのと同じくらい簡単です。

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

既定では、パラメーターなしの Authorize 属性を追加すると、そのコントローラーまたはアクションの認証されたユーザーへのアクセスが制限されます。 特定のユーザーだけに利用できる API をさらに制限するには、ユーザーが満たす必要がある必要なロールまたはポリシーを指定するように属性を拡張することができます。

## <a name="implementing-role-based-authorization"></a>ロール ベースの承認の実装

ASP.NET Core ID には、ロールの概念が組み込まれています。 ユーザーに加えて、ASP.NET Core ID は、アプリケーションによって使用されるさまざまなロールに関する情報を格納し、どのユーザーがどのロールに割り当てられているかを追跡します。 これらの割り当ては、RoleManager の種類 (永続化された記憶域内のロールを更新します) および UserManager の種類 (ロールにユーザーを割り当てるかまたはロールからユーザーの割り当てを解除できます) によってプログラムで変更できます。

JWT ベアラ トークンによる認証を行う場合、ASP.NET Core JWT ベアラ認証ミドルウェアは、トークンで見つかったロール要求に基づいてユーザーのロールを入力します。 MVC アクションまたはコントローラーへのアクセスを特定のロールのユーザーに制限するために、次の例に示すように、Authorize ヘッダーに Roles パラメーターを含めることができます。

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

この例では、Administrator または PowerUser ロールのユーザーのみが、ControlPanel コントローラーの API (SetTime アクションの実行など) にアクセスできます。 ShutDown API は、Administrator ロールのユーザーのみにアクセスを許可するようにさらに制限します。

ユーザーに複数のロールが割り当てられていることを必須にするには、次の例で示すように、複数の Authorize 属性を使用します。

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

この例では、API1 を呼び出すために、ユーザーは次の条件を満たす必要があります。

-   Adminstrator *または* PowerUser ロールであり、*かつ*

-   RemoteEmployee ロールであり、*かつ*

-   CustomPolicy 承認のためのカスタム ハンドラーを満たしている。

## <a name="implementing-policy-based-authorization"></a>ポリシー ベースの承認の実装

カスタム承認規則も[承認ポリシー](https://docs.asp.net/en/latest/security/authorization/policies.html)を使用して記述できます。 このセクションでは、概要を説明します。 詳細については、オンラインの「[ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop)」(ASP.NET 承認ワークショップ) を参照してください。

カスタム承認ポリシーは、service.AddAuthorization メソッドを使用して、Startup.ConfigureServices メソッドに登録されます。 このメソッドは、AuthorizationOptions 引数を構成するデリゲートを受け取ります。

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

例に示すように、ポリシーをさまざまな種類の要件に関連付けることができます。 ポリシーが登録された後に、ポリシーの名前を Authorize 属性の Policy 引数として渡すことで、アクションまたはコントローラーにポリシーを適用できます (たとえば、\[Authorize(Policy="EmployeesOnly")\])。ポリシーは、これらの例に示すように 1 つだけでなく複数の要件を持つことができます。

前の例では、AddPolicy の最初の呼び出しは、ロールによる承認の代替の方法です。 \[Authorize(Policy="AdministratorsOnly")\] が API に適用される場合、Administrator ロールのユーザーのみがアクセスできます。

2 番目の AddPolicy の呼び出しは、特定の要求をユーザーに提示することをユーザーに義務付けるための簡単な方法を示しています。 RequireClaim メソッドは、また、必要に応じて、要求の予期される値を受け取ります。 値を指定する場合、ユーザーが正しい種類の要求と、指定された値のいずれかの両方を持っている場合にのみこの要件を満たします。 JWT ベアラ認証ミドルウェアを使用している場合、すべての JWT プロパティはユーザーの要求として使用可能になります。

ここで示す最も注目すべきポリシーは、カスタム承認要件を使用している 3 番目の AddPolicy メソッドです。 カスタム承認要件を使用すると、承認を実行する方法を細かく制御することができます。 これを機能させるには、次の種類を実装する必要があります。

-   IAuthorizationRequirement から派生し、要件の詳細を指定するフィールドを格納している要件の種類。 例では、これはサンプル MinimumAgeRequirement タイプの年齢フィールドです。

-   AuthorizationHandler&lt;T&gt; を実装するハンドラー。T は、ハンドラーが満たすことができる IAuthorizationRequirement の種類です。 このハンドラーは、ユーザーに関する情報を格納している指定されたコンテキストが要件を満たすかどうかをチェックする HandleRequirementAsync メソッドを実装する必要があります。

ユーザーが要件を満たす場合、context.Succeed への呼び出しが、ユーザーを承認されていることを示します。 ユーザーが承認要件を満たす方法が複数ある場合、複数のハンドラーを作成することができます。

カスタム ポリシーの要件の AddPolicy 呼び出しへの登録に加えて、依存関係の挿入を使用してカスタム要件ハンドラーも登録する必要があります (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;())。

カスタム承認要件およびユーザーの年齢 (DateOfBirth 要求に基づく) をチェックするハンドラーの例については、ASP.NET Core [承認ドキュメント](https://docs.asp.net/en/latest/security/authorization/policies.html)を参照してください。

## <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET Core の認証**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **ASP.NET Core の承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **ロール ベースの承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **カスタム ポリシー ベースの承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[前へ](index.md)
[次へ](developer-app-secrets-storage.md)
