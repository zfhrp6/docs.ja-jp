---
title: "JSON Web トークン ハンドラー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 6772d484fa4d0ed3948ecee26adb2cf886340f11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="json-web-token-handler"></a><span data-ttu-id="c2b99-102">JSON Web トークン ハンドラー</span><span class="sxs-lookup"><span data-stu-id="c2b99-102">JSON Web Token Handler</span></span>
<span data-ttu-id="c2b99-103">Windows Identity Foundation の JSON Web トークン ハンドラー拡張機能を使用すると、アプリケーションで JSON Web トークン (JWT) を作成して検証できます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-103">The JSON Web Token Handler extension for Windows Identity Foundation enables you to create and validate JSON Web Tokens (JWT) in your applications.</span></span> <span data-ttu-id="c2b99-104">JWT トークン ハンドラーは、他の組み込みセキュリティ トークン ハンドラーのような WIF パイプラインで実行されるように構成できますが、別個に使用して軽量のアプリケーションでトークン検証を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-104">The JWT Token Handler can be configured to run in the WIF pipeline like other built-in security token handlers, but it can also be used independently to perform token validation in lightweight applications.</span></span> <span data-ttu-id="c2b99-105">Microsoft Azure Active Directory での認証など、OAuth 2.0 ベアラー トークン スキームを使用している場合は、JWT トークン ハンドラーが特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-105">The JWT Token Handler is particularly useful when using an OAuth 2.0 bearer token scheme, such as authenticating to Windows Azure Active Directory.</span></span>  
  
 <span data-ttu-id="c2b99-106">JWT トークン ハンドラーは、NuGet パッケージとして入手できます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-106">The JWT Token Handler is available as a NuGet package.</span></span> <span data-ttu-id="c2b99-107">詳細については、「[JSON Web トークン ハンドラー パッケージのダウンロード](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2b99-107">See [Downloading the JSON Web Token Handler Package](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) for more information.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="c2b99-108">シナリオ</span><span class="sxs-lookup"><span data-stu-id="c2b99-108">Scenarios</span></span>  
 <span data-ttu-id="c2b99-109">JWT トークン ハンドラーにより、次の主要なシナリオが可能になります。</span><span class="sxs-lookup"><span data-stu-id="c2b99-109">The JWT Token Handler enables the following key scenarios:</span></span>  
  
-   <span data-ttu-id="c2b99-110">**サーバー アプリケーションで JWT トークンを検証する**: このシナリオでは、Litware という会社が、WIF を使用して Web サインオン要求を処理するサーバー アプリケーションを保有しています。</span><span class="sxs-lookup"><span data-stu-id="c2b99-110">**Validate a JWT Token in a Server Application**: In this scenario, a company named Litware has a server application that uses WIF to handle web sign-on requests.</span></span> <span data-ttu-id="c2b99-111">Litware は、アプリケーションが認証に JWT トークンを使用できるようにしたいと思っています。</span><span class="sxs-lookup"><span data-stu-id="c2b99-111">Litware wants to enable their application to use JWT tokens for authentication.</span></span> <span data-ttu-id="c2b99-112">このアプリケーションが JWT トークン ハンドラーで更新された後、アプリケーション構成が更新されて、WIF パイプラインに JWT トークン ハンドラーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-112">The application is updated with the JWT Token Handler, and then the application configuration is updated to add the JWT Token Handler in the WIF pipeline.</span></span> <span data-ttu-id="c2b99-113">更新が行われてから新しい要求が WIF パイプラインに入ると、新しいハンドラーを使用して JWT トークンが検証され、正常な認証が行われます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-113">After the updates have been made and a new request enters the WIF pipeline, the JWT token is validated using the new handler and successful authentication occurs.</span></span>  
  
-   <span data-ttu-id="c2b99-114">**REST Web サービスで JWT トークンを検証する**: このシナリオでは、Litware という会社が、Microsoft Azure Active Directory で保護された REST Web サービスを利用しています。</span><span class="sxs-lookup"><span data-stu-id="c2b99-114">**Validate a JWT Token in a REST Web Service**: In this scenario, a company named Litware has a REST web service that is secured by Windows Azure Active Directory.</span></span> <span data-ttu-id="c2b99-115">Web サービスへの要求は、正常な認証時 JWT トークンを発行する Microsoft Azure AD により認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2b99-115">Requests to the web service must be authenticated by Windows Azure AD, which issues a JWT token upon successful authentication.</span></span> <span data-ttu-id="c2b99-116">Litware には、Web サービスへのアクセスが必要なクライアント アプリケーションがあります。</span><span class="sxs-lookup"><span data-stu-id="c2b99-116">Litware has a client application that needs to access the web service.</span></span> <span data-ttu-id="c2b99-117">このクライアントが Web サービスに要求を行い、Microsoft Azure AD から取得した JWT トークンを提示した後、Web サービスにより JWT トークン ハンドラーを使用してトークンが検証されます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-117">The client makes a request to the web service and presents its JWT token from Windows Azure AD, which is then validated by the web service using the JWT Token Handler.</span></span> <span data-ttu-id="c2b99-118">JWT トークン ハンドラーがトークンを検証した後、Web サービスによって目的のリソースがクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-118">After the JWT Token Handler has validated the token, the desired resource is returned to the client by the web service.</span></span>  
  
## <a name="features"></a><span data-ttu-id="c2b99-119">機能</span><span class="sxs-lookup"><span data-stu-id="c2b99-119">Features</span></span>  
 <span data-ttu-id="c2b99-120">JWT トークン ハンドラーには、次の機能が備わっています。</span><span class="sxs-lookup"><span data-stu-id="c2b99-120">The JWT Token Handler offers the following features:</span></span>  
  
-   <span data-ttu-id="c2b99-121">**JWT トークンを検証する**: JWT トークンは、アプリケーションの WIF パイプラインの一部として、または WIF とは別個に呼び出されたトークン ハンドラーの検証ロジックにより簡単に検証できます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-121">**Validate a JWT Token**: JWT tokens can be easily validated by the token handler’s validation logic, either as a part of the application’s WIF pipeline or called independently of WIF</span></span>  
  
-   <span data-ttu-id="c2b99-122">**JWT トークンを作成する**: JWT トークン ハンドラーを使用すると、下位サービスの承認用に JWT トークンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c2b99-122">**Create a JWT Token**: The JWT Token Handler can be used to create JWT tokens for authorization in downstream services</span></span>
