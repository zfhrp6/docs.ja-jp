---
title: "サービスの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75069b00fa07078ff0eb2d49e64f046d5415d154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-services"></a><span data-ttu-id="c4523-102">サービスの配置</span><span class="sxs-lookup"><span data-stu-id="c4523-102">Deploying Services</span></span>
<span data-ttu-id="c4523-103">ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションをランタイム環境に配置する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c4523-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="c4523-104">アプリケーションのホスト環境の選択</span><span class="sxs-lookup"><span data-stu-id="c4523-104">Choosing the Hosting Environment for Your Application</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c4523-105"> サービスは、マネージ コードをサポートする任意の Windows プロセスで実行されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="c4523-105"> services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="c4523-106">アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4523-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="c4523-107">ホスティング環境の範囲は、最も単純なコンソール アプリケーション内、Windows サービスやインターネット インフォメーション サービス (IIS) のようなサーバー環境、あるいは Windows アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行にまで及びます。</span><span class="sxs-lookup"><span data-stu-id="c4523-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="c4523-108">さまざまなホスティング オプションを確認する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]アプリケーションを参照してください[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="c4523-108">To review the different hosting options for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4523-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4523-109">See Also</span></span>  
 [<span data-ttu-id="c4523-110">ホスティング</span><span class="sxs-lookup"><span data-stu-id="c4523-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="c4523-111">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="c4523-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
