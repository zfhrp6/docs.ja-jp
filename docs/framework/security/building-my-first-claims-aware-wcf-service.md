---
title: クレーム対応の WCF サービスを初めて構築する
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3b88835cc7836d9d6c323de3c0386b3f4c7c3078
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399614"
---
# <a name="building-my-first-claims-aware-wcf-service"></a><span data-ttu-id="7766e-102">クレーム対応の WCF サービスを初めて構築する</span><span class="sxs-lookup"><span data-stu-id="7766e-102">Building My First Claims-Aware WCF Service</span></span>
## <a name="applies-to"></a><span data-ttu-id="7766e-103">対象</span><span class="sxs-lookup"><span data-stu-id="7766e-103">Applies To</span></span>  
  
-   <span data-ttu-id="7766e-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="7766e-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="7766e-105">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="7766e-105">Windows Communication Foundation (WCF)</span></span>  
  
## <a name="overview"></a><span data-ttu-id="7766e-106">概要</span><span class="sxs-lookup"><span data-stu-id="7766e-106">Overview</span></span>  
 <span data-ttu-id="7766e-107">このトピックでは、WIF を使用してクレーム対応 WCF サービスをビルドするシナリオの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="7766e-107">This topic outlines the scenario of building claims-aware WCF services using WIF.</span></span> <span data-ttu-id="7766e-108">クレーム対応 Web サービスのシナリオには、通常、Web サービス、エンド ユーザー、セキュリティ トークン サービス (STS) の 3 つ参加要素が存在します。</span><span class="sxs-lookup"><span data-stu-id="7766e-108">There are usually three participants in a claims-aware web service scenario: the web service itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="7766e-109">次の図は、このシナリオについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="7766e-109">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="7766e-110">![WIF 基本クレームに対応する WCF サービス](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span><span class="sxs-lookup"><span data-stu-id="7766e-110">![WIF Basic Claims Aware WCF Service](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span></span>  
  
1.  <span data-ttu-id="7766e-111">WCF サービス クライアント (エージェントと呼ばれることもあります) は、WIF を使用して資格情報を STS に送信します。認証が正常に行われると、STS はそのエージェントに対してトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="7766e-111">The WCF service client (sometimes called agent) uses WIF to send credentials to the STS and upon successful authentication, the agent is issued a token by the STS.</span></span>  
  
2.  <span data-ttu-id="7766e-112">エージェントは、この STS によって発行されたトークンを WCF サービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="7766e-112">The agent sends this STS-issued token to the WCF service.</span></span>  
  
3.  <span data-ttu-id="7766e-113">クレーム対応 WCF サービスは、STS とその STS が発行したトークンを信頼するように構成され、</span><span class="sxs-lookup"><span data-stu-id="7766e-113">The claims-aware WCF service is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="7766e-114">WIF を使用してトークンを検証し、解析します。</span><span class="sxs-lookup"><span data-stu-id="7766e-114">The claims-aware WCF service uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="7766e-115">開発者は、承認の実装などのアプリケーションのニーズに応じて、適切な WIF API と種類 (**ClaimsPrincipal** など) を使用します。</span><span class="sxs-lookup"><span data-stu-id="7766e-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincipal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="7766e-116">.NET 4.5 以降、WIF は .NET Framework パッケージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="7766e-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="7766e-117">.NET Framework で直接 WIF クラスを使用できるようになったため、.NET でクレームベースの ID をより深く統合できるようになり、クレームを簡単に使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7766e-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="7766e-118">WIF 4.5 を使用すると、クレーム対応アプリケーションの開発を開始する目的で、帯域外コンポーネントをインストールする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="7766e-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="7766e-119">WIF クラスは、さまざまなアセンブリに分散されています。主なものは、System.Security.Claims、System.IdentityModel、および System.IdentityModel.Services です。</span><span class="sxs-lookup"><span data-stu-id="7766e-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="7766e-120">STS は、認証が正常に行われたときにトークンを発行するサービスです。</span><span class="sxs-lookup"><span data-stu-id="7766e-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="7766e-121">Microsoft では、2 つの業界標準 STS を提供します。</span><span class="sxs-lookup"><span data-stu-id="7766e-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="7766e-122">[Active Directory フェデレーション サービス (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="7766e-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="7766e-123">[Windows Azure アクセス制御サービス (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517)です。</span><span class="sxs-lookup"><span data-stu-id="7766e-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="7766e-124">AD FS 2.0 は、Windows Server R2 に含まれており、設置型シナリオの STS として使用できます。</span><span class="sxs-lookup"><span data-stu-id="7766e-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="7766e-125">Azure Active Directory アクセス制御 (Access Control Service または ACS とも呼ばれます) は、Microsoft Azure の一部として提供されるクラウド サービスです。</span><span class="sxs-lookup"><span data-stu-id="7766e-125">Azure Active Directory Access Control (also known as Access Control Service or ACS) is a cloud service, offered as part of Microsoft Azure.</span></span> <span data-ttu-id="7766e-126">テストまたは学習の目的で、他の STS を使用して、クレーム対応アプリケーションをビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7766e-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="7766e-127">たとえばの一部であるローカル開発用 STS を使用することができます、 [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849)は自由に利用可能なオンラインです。</span><span class="sxs-lookup"><span data-stu-id="7766e-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="7766e-128">WIF を使用して最初の要求に対応する WCF サービスをビルドするを参照してください。[操作方法: WCF Web サービス アプリケーションの WIF を有効にする](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="7766e-128">To build your first claims-aware WCF service using WIF, see [How To: Enable WIF for a WCF Web Service Application](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7766e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="7766e-129">See Also</span></span>  
 [<span data-ttu-id="7766e-130">WIF の概要</span><span class="sxs-lookup"><span data-stu-id="7766e-130">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
