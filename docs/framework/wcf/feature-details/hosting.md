---
title: Hosting2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f25f0c9e773bbadd992284adf6c79d77aaa2441c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hosting"></a><span data-ttu-id="d677e-102">ホスト</span><span class="sxs-lookup"><span data-stu-id="d677e-102">Hosting</span></span>
<span data-ttu-id="d677e-103">このセクションのトピックでは、サービス ホスティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d677e-103">The topics in the section describe service hosting.</span></span> <span data-ttu-id="d677e-104">インターネット インフォメーション サービス (IIS)、Windows プロセス アクティブ化サービス (WAS)、Windows Server AppFabric、Windows サービス、またはマネージ アプリケーションによっては、サービスをホストされていることができます: このオプションは、多くの場合と呼びます*セルフ ホスト*です。</span><span class="sxs-lookup"><span data-stu-id="d677e-104">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="d677e-105">信頼されていないホストからサービスや拡張機能を実行すると、セキュリティが損なわれるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="d677e-105">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d677e-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d677e-106">In This Section</span></span>  
 [<span data-ttu-id="d677e-107">インターネット インフォメーション サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="d677e-107">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 <span data-ttu-id="d677e-108">について説明する方法、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]サービスがインターネット インフォメーション サービスでホストされているまたは[Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496)です。</span><span class="sxs-lookup"><span data-stu-id="d677e-108">Describes how a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is hosted in Internet Information Services or [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496).</span></span>  
  
 [<span data-ttu-id="d677e-109">Windows プロセス アクティブ化サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="d677e-109">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="d677e-110">Windows プロセス アクティブ化サービス (WAS) で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d677e-110">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="d677e-111">Windows サービス アプリケーションのホスト</span><span class="sxs-lookup"><span data-stu-id="d677e-111">Hosting in a Windows Service Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="d677e-112">Windows サービスで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d677e-112">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="d677e-113">マネージ アプリケーションのホスト</span><span class="sxs-lookup"><span data-stu-id="d677e-113">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 <span data-ttu-id="d677e-114">マネージ アプリケーションで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d677e-114">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="d677e-115">IIS と WAS における構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="d677e-115">Configuration-Based Activation in IIS and WAS</span></span>](../../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="d677e-116">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが、.svc ファイルを使用せずに、IIS または WAS でホストされるしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d677e-116">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="d677e-117">複数の IIS サイト バインディングのサポート</span><span class="sxs-lookup"><span data-stu-id="d677e-117">Supporting Multiple IIS Site Bindings</span></span>](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="d677e-118">1 つの Web サイト上で同じ URI スキームを使用してサービスの複数のベース アドレスを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d677e-118">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d677e-119">参照</span><span class="sxs-lookup"><span data-stu-id="d677e-119">See Also</span></span>  
 [<span data-ttu-id="d677e-120">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="d677e-120">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="d677e-121">Windows Server App Fabric のホスティング機能</span><span class="sxs-lookup"><span data-stu-id="d677e-121">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
