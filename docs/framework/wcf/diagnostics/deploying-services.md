---
title: サービスの配置
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 4d9efcb4da064021d93345285982c0cbd29dde2e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="deploying-services"></a><span data-ttu-id="757f3-102">サービスの配置</span><span class="sxs-lookup"><span data-stu-id="757f3-102">Deploying Services</span></span>
<span data-ttu-id="757f3-103">このトピックでは、実行時環境に Windows Communication Foundation (WCF) アプリケーションを展開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="757f3-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="757f3-104">アプリケーションのホスト環境の選択</span><span class="sxs-lookup"><span data-stu-id="757f3-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="757f3-105">WCF サービスは、マネージ コードをサポートする任意の Windows プロセスで実行する設計されています。</span><span class="sxs-lookup"><span data-stu-id="757f3-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="757f3-106">アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="757f3-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="757f3-107">ホスティング環境の範囲は、最も単純なコンソール アプリケーション内、Windows サービスやインターネット インフォメーション サービス (IIS) のようなサーバー環境、あるいは Windows アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行にまで及びます。</span><span class="sxs-lookup"><span data-stu-id="757f3-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="757f3-108">WCF アプリケーションのさまざまなホスティング オプションを確認するを参照してください。[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="757f3-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757f3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="757f3-109">See Also</span></span>  
 [<span data-ttu-id="757f3-110">ホスティング</span><span class="sxs-lookup"><span data-stu-id="757f3-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="757f3-111">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="757f3-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
