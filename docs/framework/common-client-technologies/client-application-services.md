---
title: クライアント アプリケーション サービス
ms.date: 03/30/2017
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
ms.openlocfilehash: d67b7467bdacdfca054d0ecd11a81c7d25b158f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743226"
---
# <a name="client-application-services"></a><span data-ttu-id="1f416-102">クライアント アプリケーション サービス</span><span class="sxs-lookup"><span data-stu-id="1f416-102">Client Application Services</span></span>
<span data-ttu-id="1f416-103">クライアント アプリケーション サービスにより、Microsoft ASP.NET 2.0 AJAX Extensions に含まれる [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] のログイン、ロール、およびプロファイル アプリケーション サービスを使用する Windows ベースのアプリケーションを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="1f416-103">Client application services make it easy for you to create Windows-based applications that use the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] login, roles, and profile application services included in the Microsoft ASP.NET 2.0 AJAX Extensions.</span></span> <span data-ttu-id="1f416-104">これらのサービスにより、複数の Web ベースおよび Windows ベースのアプリケーションで、単一のサーバーから提供されるユーザー情報とユーザー管理機能を共有できます。</span><span class="sxs-lookup"><span data-stu-id="1f416-104">These services enable multiple Web and Windows-based applications to share user information and user-management functionality from a single server.</span></span> <span data-ttu-id="1f416-105">たとえば、これらのサービスを使用して、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1f416-105">For example, you can use these services to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="1f416-106">ユーザーを認証します。</span><span class="sxs-lookup"><span data-stu-id="1f416-106">Authenticate a user.</span></span> <span data-ttu-id="1f416-107">認証サービスを使用して、ユーザー ID を検証することができます。</span><span class="sxs-lookup"><span data-stu-id="1f416-107">You can use the authentication service to verify a user's identity.</span></span>  
  
-   <span data-ttu-id="1f416-108">認証されたユーザーのロールを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f416-108">Determine the role or roles of an authenticated user.</span></span> <span data-ttu-id="1f416-109">ロール サービスを使用して、ユーザーのロールに応じてアプリケーションのユーザー インターフェイスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="1f416-109">You can use the roles service to change the user interface of your application depending on the user's role.</span></span> <span data-ttu-id="1f416-110">たとえば、管理者ロールのユーザーには機能を追加して提供することができます。</span><span class="sxs-lookup"><span data-stu-id="1f416-110">For example, you can provide additional features for users who are in an administrator role.</span></span>  
  
-   <span data-ttu-id="1f416-111">サーバー上に存在する、ユーザーごとのアプリケーションの設定を保存してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1f416-111">Store and access per-user application settings located on the server.</span></span> <span data-ttu-id="1f416-112">Web 設定サービス (プロファイル サービスとも呼ばれます) を使用して、複数のアプリケーションや場所で設定を共有することができます。</span><span class="sxs-lookup"><span data-stu-id="1f416-112">You can use the Web settings service (also known as the profile service) to share settings across multiple applications and locations.</span></span>  
  
 <span data-ttu-id="1f416-113">クライアント アプリケーション サービスは、アプリケーション構成ファイルで指定できるクライアントのサービス プロバイダーの Web サービス拡張モデルを活用します。</span><span class="sxs-lookup"><span data-stu-id="1f416-113">Client application services take advantage of the Web services extensibility model through client service providers that you can specify in your application configuration files.</span></span> <span data-ttu-id="1f416-114">これらのサービス プロバイダーには、ネットワーク接続が利用できない場合、認証、ロール、および設定のデータのローカル キャッシュを使用するオフライン機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1f416-114">These service providers include offline functionality that uses a local cache for authentication, roles, and settings data when a network connection is unavailable.</span></span>  
  
 <span data-ttu-id="1f416-115">[!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] アプリケーション サービスの詳細については、「[ASP.NET アプリケーション サービスの概要](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f416-115">For more information about the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] application services, see [ASP.NET Application Services Overview](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f416-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1f416-116">In This Section</span></span>  
 [<span data-ttu-id="1f416-117">クライアント アプリケーション サービスの概要</span><span class="sxs-lookup"><span data-stu-id="1f416-117">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 <span data-ttu-id="1f416-118">クライアント アプリケーション サービス プロバイダーを介して使用できる機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f416-118">Describes the features available through the client application service providers.</span></span>  
  
 [<span data-ttu-id="1f416-119">方法 : クライアント アプリケーション サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="1f416-119">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 <span data-ttu-id="1f416-120">このトピックでは、Visual Studio プロジェクト デザイナーを使用して、アプリケーション サービスを有効にし、構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f416-120">Describes how to use the Visual Studio project designer to enable and configuration application services.</span></span> <span data-ttu-id="1f416-121">対応する App.config ファイルへの変更についても説明します。</span><span class="sxs-lookup"><span data-stu-id="1f416-121">Also describes the corresponding changes to your App.config file.</span></span>  
  
 [<span data-ttu-id="1f416-122">方法: クライアント アプリケーション サービスでユーザーのログインを実装する</span><span class="sxs-lookup"><span data-stu-id="1f416-122">How to: Implement User Login with Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 <span data-ttu-id="1f416-123">アプリケーションがクライアントの認証サービス プロバイダーを使用するよう構成される場合のユーザー検証方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f416-123">Describes how to validate a user when your application is configured to use a client authentication service provider.</span></span>  
  
 [<span data-ttu-id="1f416-124">チュートリアル : クライアント アプリケーション サービスの使用</span><span class="sxs-lookup"><span data-stu-id="1f416-124">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 <span data-ttu-id="1f416-125">すべてのクライアント アプリケーション サービスの機能を1 つのアプリケーションに結合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f416-125">Describes how to combine all client application services features in a single application.</span></span> <span data-ttu-id="1f416-126">このチュートリアルでは、エンド ツー エンドのガイダンスを示します。</span><span class="sxs-lookup"><span data-stu-id="1f416-126">This walkthrough provides end-to-end guidance.</span></span> <span data-ttu-id="1f416-127">たとえば、クライアント アプリケーション サービスのテストに使用できる ASP.NET Web サービス アプリケーションを作成する方法の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1f416-127">For example, it includes instructions on how to create an ASP.NET Web Service Application that you can use to test client application services.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1f416-128">参照</span><span class="sxs-lookup"><span data-stu-id="1f416-128">Reference</span></span>  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a><span data-ttu-id="1f416-129">参照</span><span class="sxs-lookup"><span data-stu-id="1f416-129">See Also</span></span>  
 [<span data-ttu-id="1f416-130">ASP.NET アプリケーション サービスの概要</span><span class="sxs-lookup"><span data-stu-id="1f416-130">ASP.NET Application Services Overview</span></span>](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [<span data-ttu-id="1f416-131">ASP.NET AJAX でのフォーム認証の使用</span><span class="sxs-lookup"><span data-stu-id="1f416-131">Using Forms Authentication with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [<span data-ttu-id="1f416-132">ASP.NET AJAX でのロール情報の使用</span><span class="sxs-lookup"><span data-stu-id="1f416-132">Using Roles Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [<span data-ttu-id="1f416-133">ASP.NET AJAX でのプロファイル情報の使用</span><span class="sxs-lookup"><span data-stu-id="1f416-133">Using Profile Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [<span data-ttu-id="1f416-134">ASP.NET の認証</span><span class="sxs-lookup"><span data-stu-id="1f416-134">ASP.NET Authentication</span></span>](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 <span data-ttu-id="1f416-135">[ロールを使用した承認の管理](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span><span class="sxs-lookup"><span data-stu-id="1f416-135">[Managing Authorization Using Roles](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span></span>  
 [<span data-ttu-id="1f416-136">アプリケーション設定の概要</span><span class="sxs-lookup"><span data-stu-id="1f416-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)
