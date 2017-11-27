---
title: "ピアツーピア ネットワーキング シナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d23b1a64-2e08-4014-882a-c1dd766bdcc2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5d110d49ed93c1c53c257e4c01c3fc68eb2e0b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="peer-to-peer-networking-scenarios"></a><span data-ttu-id="be20b-102">ピアツーピア ネットワーキング シナリオ</span><span class="sxs-lookup"><span data-stu-id="be20b-102">Peer-to-Peer Networking Scenarios</span></span>
<span data-ttu-id="be20b-103">ピアツーピア ネットワーキングは次のシナリオを実現または強化します。</span><span class="sxs-lookup"><span data-stu-id="be20b-103">Peer-to-peer networking enables or enhances the following scenarios:</span></span>  
  
## <a name="real-time-communications-rtc"></a><span data-ttu-id="be20b-104">リアルタイム コミュニケーション (RTC)</span><span class="sxs-lookup"><span data-stu-id="be20b-104">Real-Time Communications (RTC)</span></span>  
  
-   <span data-ttu-id="be20b-105">サーバーなしのインスタント メッセージング</span><span class="sxs-lookup"><span data-stu-id="be20b-105">Serverless Instant Messaging</span></span>  
  
 <span data-ttu-id="be20b-106">RTC は現在既に行われています。</span><span class="sxs-lookup"><span data-stu-id="be20b-106">RTC exists today.</span></span> <span data-ttu-id="be20b-107">現在、コンピューターのユーザーは、他のユーザーとチャットすることや、音声またはビデオ通話で会話することができます。</span><span class="sxs-lookup"><span data-stu-id="be20b-107">Computer users can chat and have voice or video conversations with their peers today.</span></span> <span data-ttu-id="be20b-108">ただし、既存のプログラムと通信プロトコルの多くは、サーバーの機能に依存しています。</span><span class="sxs-lookup"><span data-stu-id="be20b-108">However, many of the existing programs and their communications protocols rely on servers to function.</span></span> <span data-ttu-id="be20b-109">サーバーの機能に依存した RTC 機能は、アドホック ワイヤレス ネットワークに参加している場合や、分離されたネットワークに属している場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="be20b-109">If you are participating in an ad-hoc wireless network or are a part of an isolated network, you are unable to use these RTC facilities.</span></span> <span data-ttu-id="be20b-110">ピアツーピア テクノロジによって、そうしたネットワーク環境でも RTC テクノロジを利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="be20b-110">Peer-to-peer technology allows the extension of RTC technologies to these additional networking environments.</span></span>  
  
-   <span data-ttu-id="be20b-111">リアルタイムのマッチメイキングとゲームプレイ</span><span class="sxs-lookup"><span data-stu-id="be20b-111">Real-time matchmaking and gameplay</span></span>  
  
 <span data-ttu-id="be20b-112">RTC と同様、リアルタイムのゲームプレイも現在行われています。</span><span class="sxs-lookup"><span data-stu-id="be20b-112">Similar to RTC, real-time game play exists today.</span></span> <span data-ttu-id="be20b-113">Web ベースのゲーム サイトが多数存在し、インターネット経由でのゲーム コミュニティを形成しています。</span><span class="sxs-lookup"><span data-stu-id="be20b-113">There are many Web-based game sites that cater to the gaming community via the Internet.</span></span> <span data-ttu-id="be20b-114">好みの似た他のゲーマーを見つけて、一緒にゲームをプレイすることができます。</span><span class="sxs-lookup"><span data-stu-id="be20b-114">They offer the ability to find other gamers with similar interests and play a game together.</span></span> <span data-ttu-id="be20b-115">問題は、ゲーム サイトがインターネット上だけに存在し、世界最高クラスのゲーマーと対戦したいと願っている熱心なゲーマーを対象にしていることです。</span><span class="sxs-lookup"><span data-stu-id="be20b-115">The problem is that the game sites exist only on the Internet and are geared toward the avid gamer who wants to play against the best gamers in the world.</span></span> <span data-ttu-id="be20b-116">このようなサイトは、その目的に役立つように統計を収集して提供しています。</span><span class="sxs-lookup"><span data-stu-id="be20b-116">These sites track and provide the statistics to help in the process.</span></span> <span data-ttu-id="be20b-117">ただし、それらのサイトでは、ゲーマーがさまざまなネットワーク環境の友人との間にアドホック ゲームをセットアップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="be20b-117">However, these sites do not allow a gamer to set up an ad-hoc game among friends in a variety of networking environments.</span></span> <span data-ttu-id="be20b-118">ピアツーピア ネットワーキングは、この機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="be20b-118">Peer-to-peer networking can provide this capability.</span></span>  
  
## <a name="collaboration"></a><span data-ttu-id="be20b-119">コラボレーション</span><span class="sxs-lookup"><span data-stu-id="be20b-119">Collaboration</span></span>  
  
-   <span data-ttu-id="be20b-120">目的を果たすプロジェクト ワークスペース</span><span class="sxs-lookup"><span data-stu-id="be20b-120">Project workspaces solving a goal</span></span>  
  
 <span data-ttu-id="be20b-121">共有ワークスペース アプリケーションを使用すると、アドホック ワークグループの作成が可能になります。ワークグループの所有者は、グループの問題を解決するためのツールやコンテンツを共有ワークスペースに設定できます。</span><span class="sxs-lookup"><span data-stu-id="be20b-121">Shared workspace applications allow for the creation of ad-hoc workgroups and then allow the workgroup owners to populate the shared workspace with the tools and content that will allow the group to solve a problem.</span></span> <span data-ttu-id="be20b-122">たとえば、メッセージ ボード、生産性ツール、ファイルなどです。</span><span class="sxs-lookup"><span data-stu-id="be20b-122">This could include message boards, productivity tools, and files.</span></span>  
  
-   <span data-ttu-id="be20b-123">他のユーザーとのファイルの共有</span><span class="sxs-lookup"><span data-stu-id="be20b-123">Sharing files with others</span></span>  
  
 <span data-ttu-id="be20b-124">プロジェクト ワークスペース共有のサブセットとして、ファイルを共有する機能があります。</span><span class="sxs-lookup"><span data-stu-id="be20b-124">A subset of project workspace sharing is the ability to share files.</span></span> <span data-ttu-id="be20b-125">現在、この機能は最新バージョンの Windows に存在していますが、ピアツーピア ネットワーキングを通じて拡張することで、ファイルの内容を簡単なわかりやすい方法で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="be20b-125">Although this ability exists today with the current version of Windows, it can be enhanced through peer-to-peer networking to make file content available in an easy and friendly way.</span></span> <span data-ttu-id="be20b-126">インターネットのエッジまたはアドホック コンピューティング環境で、驚くほど豊富なコンテンツに簡単にアクセスできるようになると、ネットワーク コンピューティングの価値が高まります。</span><span class="sxs-lookup"><span data-stu-id="be20b-126">Allowing easy access to the incredible wealth of content at the edge of the Internet or in ad-hoc computing environments increases the value of network computing.</span></span>  
  
-   <span data-ttu-id="be20b-127">体験の共有</span><span class="sxs-lookup"><span data-stu-id="be20b-127">Sharing experiences</span></span>  
  
 <span data-ttu-id="be20b-128">ワイヤレス接続の広がりとともに、ピアツーピア ネットワーキングによってピア グループをオンラインでつなぎ、体験 (夕焼け、ロック コンサート、クルーズ バケーションなど) をリアルタイムで共有することが可能になりました。</span><span class="sxs-lookup"><span data-stu-id="be20b-128">With wireless connectivity becoming more prevalent, peer-to-peer networking allows you to be online in a group of peers and to be able to share your experiences (such as a sunset, a rock concert, or a vacation cruise) while they are occurring.</span></span>  
  
## <a name="content-distribution"></a><span data-ttu-id="be20b-129">コンテンツ配信</span><span class="sxs-lookup"><span data-stu-id="be20b-129">Content Distribution</span></span>  
  
-   <span data-ttu-id="be20b-130">テキスト メッセージ</span><span class="sxs-lookup"><span data-stu-id="be20b-130">Text messages</span></span>  
  
 <span data-ttu-id="be20b-131">ピアツーピア ネットワーキングによって、大規模なユーザー グループにテキストベースの情報をファイルやメッセージの形式で配信できます。</span><span class="sxs-lookup"><span data-stu-id="be20b-131">Peer-to-peer networking can allow for the dissemination of text-based information in the form of files or messages to a large group of users.</span></span> <span data-ttu-id="be20b-132">例としてニュース一覧があります。</span><span class="sxs-lookup"><span data-stu-id="be20b-132">An example is a news list.</span></span>  
  
-  
  
-   <span data-ttu-id="be20b-133">オーディオとビデオ</span><span class="sxs-lookup"><span data-stu-id="be20b-133">Audio and video</span></span>  
  
 <span data-ttu-id="be20b-134">ピアツーピア ネットワーキングを使用すると、大規模なコンサートや会社の会議などのオーディオまたはビデオ情報を、大規模なユーザー グループに配信できます。</span><span class="sxs-lookup"><span data-stu-id="be20b-134">Peer-to-peer networking can also allow for the dissemination of audio or video information to a large group of users, such as a large concert or company meeting.</span></span> <span data-ttu-id="be20b-135">現在、コンテンツを配信するには大容量のサーバーを構成して負荷を集め、数百人または数千人のユーザーに配信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be20b-135">To distribute the content today, you must configure high-capacity servers to collect and distribute the load to hundreds or thousands of users.</span></span> <span data-ttu-id="be20b-136">ピアツーピア ネットワーキングでは、わずかな数のピアだけが集中管理サーバーから実際にコンテンツを受信します。</span><span class="sxs-lookup"><span data-stu-id="be20b-136">With peer-to-peer networking, only a handful of peers would actually get their content from the centralized servers.</span></span> <span data-ttu-id="be20b-137">この情報は、これらのピアから数人の他のユーザーに配信され、情報を受け取ったユーザーからさらに他のユーザーに配信されます。</span><span class="sxs-lookup"><span data-stu-id="be20b-137">These peers would flood this information out to a few more people who send it to others, and so on.</span></span> <span data-ttu-id="be20b-138">コンテンツを配信する負荷は、クラウドのピア間で分散されます。</span><span class="sxs-lookup"><span data-stu-id="be20b-138">The load of distributing the content is distributed to the peers in the cloud.</span></span> <span data-ttu-id="be20b-139">コンテンツを受信したいピアは、最も近い配信元ピアを見つけ、そこからコンテンツを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="be20b-139">A peer that wants to receive the content would find the closest distributing peer and get the content from them.</span></span>  
  
-  
  
-   <span data-ttu-id="be20b-140">製品更新プログラムの配布</span><span class="sxs-lookup"><span data-stu-id="be20b-140">Distribution of product updates</span></span>  
  
 <span data-ttu-id="be20b-141">ピアツーピア ネットワーキングは、製品の更新プログラム (セキュリティ更新プログラムとサービス パック) などのソフトウェアを配布するための効率的なしくみを提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="be20b-141">Peer-to-peer networking can also provide an efficient mechanism to distribute software such as product updates (security updates and service packs).</span></span> <span data-ttu-id="be20b-142">ソフトウェア配布サーバーに接続できるピアは、製品の更新プログラムを取得し、それをグループの他のメンバーに伝播することができます。</span><span class="sxs-lookup"><span data-stu-id="be20b-142">A peer that has a connection to a software distribution server can obtain the product update and propagate it to the other members of its group.</span></span>  
  
-  
  
## <a name="distributed-processing"></a><span data-ttu-id="be20b-143">分散処理</span><span class="sxs-lookup"><span data-stu-id="be20b-143">Distributed Processing</span></span>  
  
-   <span data-ttu-id="be20b-144">タスクの分割と分散</span><span class="sxs-lookup"><span data-stu-id="be20b-144">Division and distribution of a task</span></span>  
  
 <span data-ttu-id="be20b-145">大規模なコンピューティング タスクの場合、まず最初に、ピアのコンピューティング リソースに適した、より小さい別々のコンピューティング タスクに分割することができます。</span><span class="sxs-lookup"><span data-stu-id="be20b-145">A large computing task can first be divided into separate smaller computing tasks well suited to the computing resources of a peer.</span></span> <span data-ttu-id="be20b-146">ピアは大規模なコンピューティング タスクの分割を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="be20b-146">A peer could do the dividing of the large computing task.</span></span> <span data-ttu-id="be20b-147">その後、ピアツーピア ネットワーキングによって個々のタスクをグループ内の別々のピアに分散できます。</span><span class="sxs-lookup"><span data-stu-id="be20b-147">Then, peer-to-peer networking can distribute the individual tasks to the separate peers in the group.</span></span> <span data-ttu-id="be20b-148">各ピアはコンピューティング タスクを実行し、集中管理された蓄積ポイントにタスクの結果を報告します。</span><span class="sxs-lookup"><span data-stu-id="be20b-148">Each peer performs its computing task and reports its result back to a centralized accumulation point.</span></span>  
  
-   <span data-ttu-id="be20b-149">コンピューター リソースの集約</span><span class="sxs-lookup"><span data-stu-id="be20b-149">Aggregation of computer resources</span></span>  
  
 <span data-ttu-id="be20b-150">ピアツーピア ネットワーキングを使用した分散処理のもう 1 つの方法として、アイドル プロセッサ時間に処理されるプログラムを各ピアで実行する方法があります。それらのプログラムは、集中管理サーバーによって調整される大規模なコンピューティング タスクの一部として実行されます。</span><span class="sxs-lookup"><span data-stu-id="be20b-150">Another way to utilize peer-to-peer networking for distributed processing is to run programs on each peer that run during idle processor times and are part of a larger computing task that is coordinated by a central server.</span></span> <span data-ttu-id="be20b-151">複数のコンピューターのプロセッサを集約することによって、ピアツーピア ネットワーキングは、ピア コンピューターのグループを、大規模なコンピューティング タスクに適した大規模な 1 個の並列プロセッサに変えることができます。</span><span class="sxs-lookup"><span data-stu-id="be20b-151">By aggregating the processors of multiple computers, peer-to-peer networking can turn a group of peer computers into a large parallel processor for large computing tasks.</span></span>  
  
-  
  
## <a name="see-also"></a><span data-ttu-id="be20b-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="be20b-152">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Collaboration>
