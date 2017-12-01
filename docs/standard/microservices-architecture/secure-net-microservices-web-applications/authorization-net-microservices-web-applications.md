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
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>.NET microservices と web アプリケーションでの承認について

認証の後に、ASP.NET Core Web Api は、アクセスを承認する必要があります。 これにより、サービス Api によって認証されたユーザーに利用可能なすべてではなくにされます。 [承認](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)ユーザーのロールに基づいて行われますか、信頼性情報またはその他のヒューリスティックを調べることなどを含むカスタム ポリシーに基づくことができます。

ASP.NET Core MVC ルートへのアクセス制限は、アクション メソッドに (またはコント ローラーのアクションで承認が必要な場合は、コント ローラーのクラスを)、承認属性を適用する例を次に示すとして同じくらい簡単です。

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

既定では、パラメーターなしの承認属性を追加することは、そのコント ローラーまたはアクションの認証されたユーザーへのアクセスに制限されます。 特定のユーザーだけに利用できる API をさらに制限するには、必要な役割またはユーザーが満たす必要があるポリシーを指定する属性を展開することができます。

## <a name="implementing-role-based-authorization"></a>ロールベースの承認を実装します。

ASP.NET Core Id は、役割の組み込みの概念を持っています。 ユーザー以外は、ASP.NET Core Id はアプリケーションによって使用されるさまざまなロールに関する情報を格納し、どのロールに割り当てるユーザーの追跡します。 これらの割り当ては、RoleManager の種類 (更新プログラムの永続化された記憶域内のロール) および (を割り当てる、またはロールからユーザーの割り当てを解除できます) UserManager 型を持つプログラムで変更できます。

JWT ベアラ トークンによる認証を行う場合、ASP.NET Core JWT ベアラ認証ミドルウェアは、トークンに見つかりませんロール クレームに基づくユーザーのロールを設定します。 MVC アクションまたはコント ローラーが特定のロールのユーザーへのアクセスを制限するための次の例に示すように、承認ヘッダーにロール パラメーターを含めることができます。

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

この例では、管理者または PowerUser ロールのユーザーのみ (SetTime 操作を実行して) など、コントロール パネルの コント ローラーの Api にアクセスできます。 シャット ダウン API は、管理者ロールにユーザーにのみアクセスを許可するさらに制限します。

複数の役割であることが必要な次の例で示すように、複数の承認属性を使用します。

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

この例では呼び出す API1、ユーザーが必要です。

-   管理者である*または*PowerUser ロール*と*

-   RemoteEmployee ロールである*と*

-   CustomPolicy 承認のためのカスタム ハンドラーを満たします。

## <a name="implementing-policy-based-authorization"></a>ポリシー ベースの承認を実装します。

使用してカスタム承認規則を記述することができますも[承認ポリシー](https://docs.asp.net/en/latest/security/authorization/policies.html)です。 このセクションでは、概要を説明します。 詳細については、オンラインで使用できる[ASP.NET 承認ワーク ショップ](https://github.com/blowdart/AspNetAuthorizationWorkshop)です。

カスタム承認ポリシーは、サービスを使用して、Startup.ConfigureServices メソッドで登録されます。AddAuthorization メソッドです。 このメソッドは、AuthorizationOptions 引数を構成するデリゲートを受け取ります。

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

例のように、ポリシーがさまざまな種類の要件の関連付けることができます。 ポリシーは、登録後に適用できますアクションまたはコント ローラーに Authorize attribute のポリシーの引数として、ポリシーの名前を渡すことで (たとえば、 \[Authorize(Policy="EmployeesOnly")\]) ポリシーを持つことができます複数の要件だけでなく 1 つに示すようにこれらの例)。

前の例では、AddPolicy の最初の呼び出しは、ロールによって承認する方法でもです。 場合\[Authorize(Policy="AdministratorsOnly")\]管理者ロールのユーザーがアクセスできる専用の API に適用されます。

2 番目の AddPolicy 呼び出しでは、特定のクレームが存在する必要がありますを必要とする簡単な方法を示します。 RequireClaim メソッドは、また、必要に応じて、クレームの予期される値を受け取ります。 値を指定する場合、ユーザーがある両方の正しい種類のクレームと、指定された値のいずれかの場合にのみこの要件を満たします。 JWT ベアラ認証ミドルウェアを使用している場合、すべての JWT プロパティはユーザーの信頼性情報として使用可能になります。

ここで示すように、最も注目すべきポリシーは、3 番目の AddPolicy メソッドではカスタム承認要件を使用しているためです。 カスタム承認要件を使用すると、承認を実行する方法を細かく制御が大幅に向上ことができます。 これを行うには、これらの型を実装する必要があります。

-   IAuthorizationRequirement から派生して、要件の詳細を指定するフィールドを格納している必要条件の種類。 例では、これは、サンプル MinimumAgeRequirement タイプの時効フィールドです。

-   AuthorizationHandler を実装するハンドラー&lt;T&gt;ここで T は、ハンドラーが満たすことができる IAuthorizationRequirement の型。 ハンドラーには、ユーザーに関する情報を格納している指定されたコンテキストが要件を満たすかどうかをチェックする HandleRequirementAsync メソッドを実装する必要があります。

場合は、ユーザーは、コンテキストへの呼び出しの要件を満たしています。成功は、ユーザーを承認することを示すです。 複数の方法で、ユーザーが承認要件を満たすことがありますがある場合は、複数のハンドラーを作成することができます。

カスタム ポリシーの要件を AddPolicy 呼び出しに登録すると、に加えて必要もあります (サービス依存関係の挿入を使用してカスタム要求ハンドラーを登録します。AddTransient&lt;IAuthorizationHandler、MinimumAgeHandler&gt;())。

カスタム承認要件と、ユーザーの年齢を (DateOfBirth クレームに基づく) をチェックするためのハンドラーの例は、ASP.NET Core で使用できる[承認ドキュメント](https://docs.asp.net/en/latest/security/authorization/policies.html)です。

## <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET Core 認証**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **ASP.NET Core 承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **ロール ベースの承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **カスタムのポリシー ベースの承認**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[前](index.md) [次へ] (開発者向けのアプリのシークレット-storage.md)
