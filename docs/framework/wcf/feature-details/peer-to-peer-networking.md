---
title: "ピアツーピア ネットワーク"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 496c1191ebb55181ddb999a5a4327d5ff699828c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="f3ba2-102">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="f3ba2-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="f3ba2-103">ピア チャネルとは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のマルチパーティ対応ピアツーピア (P2P) 通信技術です。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="f3ba2-104">この技術によって、アプリケーション開発者は安全で拡張可能なメッセージ ベースの P2P 通信チャネルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="f3ba2-105">ピア チャネルのメリットを活用するマルチパーティ アプリケーションの一般的な例は、チャットなどの共同作業アプリケーションです。チャットでは、ユーザーのグループがサーバーなしのピアツーピア方式で互いに会話します。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="f3ba2-106">ピア チャネルを使用することで、顧客シナリオや企業シナリオでの P2P コラボレーション、コンテンツ配布、負荷分散、および分散処理が実現します。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="f3ba2-107">[!INCLUDE[wv](../../../../includes/wv-md.md)] では、すべての [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] と同様に、既定でピア チャネルが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="f3ba2-108">ピア チャネルのクラスにアクセスするには、プロジェクトに System.ServiceModel.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="f3ba2-109">次の各セクションには、ピアツーピア ネットワークに関する情報と、ピア チャネルのクラスを使用してピア対応のネットワーク アプリケーションを作成する方法が記載されています。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f3ba2-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f3ba2-110">In This Section</span></span>  
 <span data-ttu-id="f3ba2-111">[ピア チャネルのシナリオ](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): パブリケーション/サブスクリプション メッセージング、コラボレーション、分散処理、ゲームなど、ピア チャネル Api でサポートされる開発シナ リオをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="f3ba2-112">[ピア チャネルの概念](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): 説明がピア メッシュ、ピア ノード、ピア チャネルのセキュリティ、およびピア リゾルバー。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="f3ba2-113">[ピア チャネル アプリケーションの構築](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): ピア チャネル アプリケーションの開発に関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f3ba2-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="f3ba2-114">ピア チャネルのコード例</span><span class="sxs-lookup"><span data-stu-id="f3ba2-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="f3ba2-115">ピア チャネル カスタム ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="f3ba2-115">Peer Channel Custom Peer Resolver</span></span>](http://msdn.microsoft.com/en-us/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="f3ba2-116">ピア チャネル チームのブログ</span><span class="sxs-lookup"><span data-stu-id="f3ba2-116">Peer Channel Team blog</span></span>  
 <span data-ttu-id="f3ba2-117">[ピア チャネル チームのブログ](http://go.microsoft.com/fwlink/?LinkID=114530)(http://go.microsoft.com/fwlink/?LinkID=114530)</span><span class="sxs-lookup"><span data-stu-id="f3ba2-117">[Peer Channel Team Blog](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span></span>
