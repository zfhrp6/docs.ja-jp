---
title: "WIF コード サンプル インデックス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6711f01a-4743-43ce-95ab-5e2302a363ea
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6fc9a9b9e5eb739f50c8835a84c7514cf2c5038b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wif-code-sample-index"></a><span data-ttu-id="c29a5-102">WIF コード サンプル インデックス</span><span class="sxs-lookup"><span data-stu-id="c29a5-102">WIF Code Sample Index</span></span>
<span data-ttu-id="c29a5-103">次は、Windows Identity Foundation 4.5 のコード サンプルです。</span><span class="sxs-lookup"><span data-stu-id="c29a5-103">The following are code samples for Windows Identity Foundation 4.5:</span></span>  
  
-   <span data-ttu-id="c29a5-104">[ClaimsAwareWebApp](http://go.microsoft.com/fwlink/?LinkID=248405) - このサンプルでは、(Web サイトではなく) 従来の ASP.NET アプリケーションにおける認証表出化 (Visual Studio 11 の ID およびアクセス ツールからローカルのテスト用セキュリティ トークンサービスに) の基本的な使用方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-104">[ClaimsAwareWebApp](http://go.microsoft.com/fwlink/?LinkID=248405) - this sample demonstrates basic use of authentication externalization (to the local test Security Token Service from the Identity and Access Tool for Visual Studio 11) on a classic ASP.NET application (as opposed to a web site).</span></span>  
  
-   <span data-ttu-id="c29a5-105">[ClaimsAwareWebService](http://go.microsoft.com/fwlink/?LinkID=248406) - このサンプルでは、従来の WCF サービスにおける認証表出化の基本的な使用方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-105">[ClaimsAwareWebService](http://go.microsoft.com/fwlink/?LinkID=248406) - this sample demonstrates basic use of authentication externalization on a classic WCF service.</span></span>  
  
-   <span data-ttu-id="c29a5-106">[ClaimsAwareMvcApplication](http://go.microsoft.com/fwlink/?LinkID=248407) - このサンプルでは、非ブランケット保護や LogOn コントローラーの外に認証をリダイレクトする形式に準拠するコードなど、WIF と MVC を統合する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-106">[ClaimsAwareMvcApplication](http://go.microsoft.com/fwlink/?LinkID=248407) - this sample demonstrates how to integrate WIF with MVC, including non-blanket protection and code which honors the forms authentication redirects out of the LogOn controller.</span></span>  
  
-   <span data-ttu-id="c29a5-107">[ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) - このサンプルでは、(tokenreplycache ではなく) ファーム対応セッション キャッシュを確認できます。大きな Cookie を交換せず、参照でセッションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-107">[ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) - this sample demonstrates a farm ready session cache (as opposed to a tokenreplycache) so that you can use sessions by reference instead of exchanging big cookies.</span></span> <span data-ttu-id="c29a5-108">また、ファームで Cookie を保護する簡単な方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-108">It also demonstrates an easier way of securing cookies in a farm.</span></span>  
  
-   <span data-ttu-id="c29a5-109">[ClaimsAwareFormsAuthentication](http://go.microsoft.com/fwlink/?LinkID=248409) - この非常に単純なサンプルでは、.NET 4.5 で、ユーザーの認証方法に関係なく、プリンシパルの要求を取得できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-109">[ClaimsAwareFormsAuthentication](http://go.microsoft.com/fwlink/?LinkID=248409) - this very simple sample demonstrates that in .NET 4.5 you get claims in your principals regardless of how you authenticate your users.</span></span>  
  
-   <span data-ttu-id="c29a5-110">[ClaimsBasedAuthorization](http://go.microsoft.com/fwlink/?LinkID=248410)- このサンプルでは、CLaimsAuthorizationManager クラスと ClaimsAuthorizationModule を利用し、独自の認証ポリシーを適用する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-110">[ClaimsBasedAuthorization](http://go.microsoft.com/fwlink/?LinkID=248410)- this samples shows how to use your CLaimsAuthorizationManager class and the ClaimsAuthorizationModule for applying your own authorization policies.</span></span>  
  
-   <span data-ttu-id="c29a5-111">[FederationMetadata](http://go.microsoft.com/fwlink/?LinkID=248411) – このサンプルでは、メタデータ ドキュメントの動的生成 (カスタム STS 側で) と動的使用 (証明書利用者アプリケーション側で) の両方を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-111">[FederationMetadata](http://go.microsoft.com/fwlink/?LinkID=248411) – this sample demonstrates both dynamic generation (on a custom STS) and dynamic consumption (on a relying party application) of metadata documents.</span></span>  
  
-   <span data-ttu-id="c29a5-112">[CustomToken](http://go.microsoft.com/fwlink/?LinkID=248412) – このサンプルでは、単純 Web トークン (SWT) という種類のトークンをカスタムで作成する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c29a5-112">[CustomToken](http://go.microsoft.com/fwlink/?LinkID=248412) – this sample demonstrates how to build a custom Simple Web Token (SWT) token type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c29a5-113">参照</span><span class="sxs-lookup"><span data-stu-id="c29a5-113">See Also</span></span>  
 [<span data-ttu-id="c29a5-114">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="c29a5-114">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)
