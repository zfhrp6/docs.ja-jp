---
title: "基本的なプログラミング ライフサイクル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f5c45cad0b1e4ae1aa6b1963e9acdab47cd9203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="b9bd2-102">基本的なプログラミング ライフサイクル</span><span class="sxs-lookup"><span data-stu-id="b9bd2-102">Basic Programming Lifecycle</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="b9bd2-103"> では、アプリケーションは、同一のコンピューター上、インターネット上、異なるアプリケーション プラットフォーム上のいずれに存在しても、通信できます。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-103"> enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="b9bd2-104">ここでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションを構築するために必要な作業について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-104">This topic outlines the tasks that are required to build a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="b9bd2-105">実際のサンプル アプリケーションでは、次を参照してください。[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-105">For a working sample application, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="b9bd2-106">基本的なタスク</span><span class="sxs-lookup"><span data-stu-id="b9bd2-106">The Basic Tasks</span></span>  
 <span data-ttu-id="b9bd2-107">基本的な作業は、次の順序で行います。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-107">The basic tasks to perform are, in order:</span></span>  
  
1.  <span data-ttu-id="b9bd2-108">サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-108">Define the service contract.</span></span> <span data-ttu-id="b9bd2-109">サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="b9bd2-110">[サービス コントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-110"> [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="b9bd2-111">コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-111">Implement the contract.</span></span> <span data-ttu-id="b9bd2-112">サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="b9bd2-113">[サービス コントラクトを実装する](../../../docs/framework/wcf/implementing-service-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-113"> [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
3.  <span data-ttu-id="b9bd2-114">エンドポイントおよびその他の動作情報を指定して、サービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-114">Configure the service by specifying endpoints and other behavior information.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="b9bd2-115">[Services の構成](../../../docs/framework/wcf/configuring-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-115"> [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
4.  <span data-ttu-id="b9bd2-116">サービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-116">Host the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="b9bd2-117">[Services をホストしている](../../../docs/framework/wcf/hosting-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-117"> [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
5.  <span data-ttu-id="b9bd2-118">クライアント アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-118">Build a client application.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="b9bd2-119">[クライアントを構築](../../../docs/framework/wcf/building-clients.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-119"> [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
 <span data-ttu-id="b9bd2-120">このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="b9bd2-121">たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="b9bd2-122">また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="b9bd2-123">サービス コントラクトの開発の経験が、参照することも[拡張機能の概要](../../../docs/framework/wcf/introduction-to-extensibility.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md).</span></span> <span data-ttu-id="b9bd2-124">サービスに問題がある場合は確認[WCF トラブルシューティング クイック スタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)同一または類似した問題を持つ他のユーザーかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b9bd2-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bd2-125">参照</span><span class="sxs-lookup"><span data-stu-id="b9bd2-125">See Also</span></span>  
 [<span data-ttu-id="b9bd2-126">サービス コントラクトの実装</span><span class="sxs-lookup"><span data-stu-id="b9bd2-126">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
