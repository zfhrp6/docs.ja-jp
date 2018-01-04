---
title: "ピア チャネルのシナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4f989c46deff9c38e4737e48e077bf07240fa98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="peer-channel-scenarios"></a><span data-ttu-id="efdfc-102">ピア チャネルのシナリオ</span><span class="sxs-lookup"><span data-stu-id="efdfc-102">Peer Channel Scenarios</span></span>
<span data-ttu-id="efdfc-103">ピア チャネル API は、次の開発シナリオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="efdfc-103">The Peer Channel APIs support the following development scenarios.</span></span>  
  
## <a name="publicationsubscription-messaging"></a><span data-ttu-id="efdfc-104">パブリケーション/サブスクリプション メッセージング</span><span class="sxs-lookup"><span data-stu-id="efdfc-104">Publication/Subscription Messaging</span></span>  
 <span data-ttu-id="efdfc-105">パブリケーション/サブスクリプション アプリケーション (株価情報、ニュース見出しのパブリッシャー、スポーツの得点結果、天気予報など) を構築する企業では、ピア チャネルを使用することで、サーバーを使用しないアプリケーションを実現できます。</span><span class="sxs-lookup"><span data-stu-id="efdfc-105">Companies that build publication/subscription applications (for example, stock tickers, and publishers of news headlines, sports scores, and weather reports) can use Peer Channel to server-less applications.</span></span> <span data-ttu-id="efdfc-106">たとえば、ユーザーは、共通メッシュ (クライアント グループ) に参加することで、スポーツの最新の得点経過を取得でき、サーバーの負荷を増大させずに、最新の試合データを大量に伝達できます。</span><span class="sxs-lookup"><span data-stu-id="efdfc-106">For example, users can obtain the latest sports scores by joining a common mesh (or group of clients) and propagate the large amount of up-to-date game data without increasing the server load.</span></span> <span data-ttu-id="efdfc-107">これにより、データ プロバイダーは、サーバー ベース技術への投資を大幅に増大することなしに、これまでよりも高品質のサービスを提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="efdfc-107">This helps the data provider to give higher quality of service without substantially increasing the investment in server-based technologies.</span></span>  
  
## <a name="collaboration"></a><span data-ttu-id="efdfc-108">コラボレーション</span><span class="sxs-lookup"><span data-stu-id="efdfc-108">Collaboration</span></span>  
 <span data-ttu-id="efdfc-109">独立ソフトウェア ベンダー (ISV) は、ピアツーピアのアクティビティに参加するための緊密なグループをユーザーが作成できるようなアプリケーションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="efdfc-109">Independent software vendors (ISVs) can create applications that let people create tight groups for participation in peer-to-peer activities.</span></span> <span data-ttu-id="efdfc-110">たとえば、共同プロジェクトでのチームによる作業、友人による画像の共有、パーティ計画の各種作業などがあります。</span><span class="sxs-lookup"><span data-stu-id="efdfc-110">For example, this can include teams working on collaborative projects, picture-sharing between friends, party-planning activities, and more.</span></span> <span data-ttu-id="efdfc-111">従来、このようなアクティビティにはサーバーが必要でしたが、ピア チャネルでは、従来のサーバーとクライアントのモデルでは容易に実装できなかったオフライン アクセス シナリオを実現することにより、費用効果の高い方法でこのアクティビティを実現できるようになります。</span><span class="sxs-lookup"><span data-stu-id="efdfc-111">Traditionally, these activities always involve servers; however, Peer Channel provides a way of doing this in a more cost-efficient way by enabling offline access scenarios that are not as easily implemented under a traditional server-client model.</span></span>  
  
## <a name="distributed-processing-and-compute-clusters"></a><span data-ttu-id="efdfc-112">分散処理と計算クラスター</span><span class="sxs-lookup"><span data-stu-id="efdfc-112">Distributed Processing and Compute Clusters</span></span>  
 <span data-ttu-id="efdfc-113">一般に、計算クラスターと分散処理は、財務モデルや天気モデル、人間の DNA のデコードなどの大規模計算で使用します。</span><span class="sxs-lookup"><span data-stu-id="efdfc-113">Compute clusters and distributed processing are typically used for large-scale computations, such as financial/weather modeling and decoding human DNA.</span></span> <span data-ttu-id="efdfc-114">通常、このような計算は、サーバーを使用して計算クラスターに参加するすべてのクライアントにタスクを個別に割り当てることで実行されます。</span><span class="sxs-lookup"><span data-stu-id="efdfc-114">Typically, this is done by having servers individually assign tasks to all clients participating in the computation cluster.</span></span> <span data-ttu-id="efdfc-115">このサーバーには追加の要求が生じる場合もあります。たとえば、特定の期間内にすべてのタスクを終了させるため、各タスクに複数のコンピューターが必要となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="efdfc-115">These servers may also have additional demands; for example, all tasks may need to be completed within a certain duration, requiring more than one machine for each task.</span></span> <span data-ttu-id="efdfc-116">また、タスクを実行しているあるクライアントが停止した場合は、別のクライアントでそのタスクを引き継いで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efdfc-116">Additionally, if any client running a task goes down, another client must be able to take over that task and perform work on it.</span></span> <span data-ttu-id="efdfc-117">さらに、一貫性のある結果を確保するために複数のクライアントで同じタスクを実行しなければならない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="efdfc-117">Likewise, more than one client may have to run the same task to ensure consistent results.</span></span> <span data-ttu-id="efdfc-118">サーバーは、このようなクライアントの調整を実行できますが、個別にタスクを受け取るクライアントが、タスクに関係するサーバーの要件を決定し、計算メッシュを使用してタスクを完了する方法を特定するピアツーピア ソリューションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="efdfc-118">Although servers can run this type of client coordination, you can create a peer-to-peer solution where the clients receiving a task independently determine the server requirements around the task and use a compute mesh to determine how to complete that task.</span></span>  
  
## <a name="gaming"></a><span data-ttu-id="efdfc-119">ゲーム</span><span class="sxs-lookup"><span data-stu-id="efdfc-119">Gaming</span></span>  
 <span data-ttu-id="efdfc-120">ピア チャネルを使用することで、アプリケーション開発者はサーバーを使用しないバージョンのゲームを作成できます。このゲームでは、中央サーバーを使用するのではなくピアツーピア メカニズムによって、ゲームの動作を他のプレーヤーに転送したり他のプレーヤーと同期したりします。</span><span class="sxs-lookup"><span data-stu-id="efdfc-120">Using Peer Channel, application developers can create server-less versions of their games where game moves get transmitted to and synchronized with other players by a peer-to-peer mechanism rather than through a central server.</span></span> <span data-ttu-id="efdfc-121">小規模の ISV では、これにより、中央サーバーの配置、保守、サービス提供などに関連する運用コストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="efdfc-121">For small ISVs, this helps remove operational costs associated with deploying, maintaining, and servicing central servers.</span></span> <span data-ttu-id="efdfc-122">ピアツーピア アーキテクチャを使用して記述されたゲームは、インターネットや有線または無線のローカル ネットワークでプレイできます。</span><span class="sxs-lookup"><span data-stu-id="efdfc-122">Games written using a peer-to-peer architecture can be played across the Internet, or in wired or wireless local networks.</span></span> <span data-ttu-id="efdfc-123">さらに、ロビーやゲーム内チャットなどのゲームのアクティビティをピアツーピア ネットワークを使用して開発できます。</span><span class="sxs-lookup"><span data-stu-id="efdfc-123">Secondary gaming activities, such as lobby and in-game chat can be developed using a peer-to-peer network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efdfc-124">参照</span><span class="sxs-lookup"><span data-stu-id="efdfc-124">See Also</span></span>  
 [<span data-ttu-id="efdfc-125">ピア チャネルの概要</span><span class="sxs-lookup"><span data-stu-id="efdfc-125">Peer Channel Concepts</span></span>](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
