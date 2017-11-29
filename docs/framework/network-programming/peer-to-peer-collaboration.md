---
title: "ピアツーピア コラボレーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3928c6b3690bd03a4365d21d5fbf2f4bd2a4f457
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="peer-to-peer-collaboration"></a><span data-ttu-id="dbc24-102">ピアツーピア コラボレーション</span><span class="sxs-lookup"><span data-stu-id="dbc24-102">Peer-to-Peer Collaboration</span></span>
<span data-ttu-id="dbc24-103">ピアツーピア ネットワーキングは、インターネットのエッジに存在する比較的処理能力の高いコンピューター (パーソナル コンピューター) を、単なるクライアントベースのコンピューティング以上のタスクに利用する方法です。</span><span class="sxs-lookup"><span data-stu-id="dbc24-103">Peer-to-peer networking is the utilization of the relatively powerful computers (personal computers) that exist at the edge of the Internet for more than just client-based computing tasks.</span></span> <span data-ttu-id="dbc24-104">最新のパーソナル コンピューター (PC) は、非常に高速なプロセッサに大容量のメモリとハード ディスクを備えています。しかし、電子メールや Web 閲覧などの一般的なコンピューティング タスクを実行するとき、それらはいずれも最大活用されていません。</span><span class="sxs-lookup"><span data-stu-id="dbc24-104">The modern personal computer (PC) has a very fast processor, vast memory, and a large hard disk, none of which are being fully utilized when performing common computing tasks such as e-mail and Web browsing.</span></span> <span data-ttu-id="dbc24-105">最新の PC は、さまざまな種類のアプリケーションでクライアントとサーバーの両方 (ピア) として簡単に機能できます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-105">The modern PC can easily act as both a client and server (a peer) for many types of applications.</span></span>  
  
-   <span data-ttu-id="dbc24-106">ピアツーピア コラボレーションのインフラストラクチャは、Windows Vista 以降のプラットフォームの "近くの人と接続" サービスを利用する Microsoft Windows ピアツーピア インフラストラクチャを簡略化した実装です。</span><span class="sxs-lookup"><span data-stu-id="dbc24-106">The Peer-to-Peer Collaboration Infrastructure is a simplified implementation of the Microsoft Windows Peer-to-Peer Infrastructure that leverages the People Near Me service in Windows Vista and later platforms.</span></span> <span data-ttu-id="dbc24-107">"近くの人と接続" サービスが機能するサブネット内のピア対応アプリケーションでの使用に適していますが、インターネットのエンドポイントや連絡先も処理できます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-107">It is best used for peer-enabled applications within a subnet for which the People Near Me service operates, although it can service internet endpoints or contacts as well.</span></span> <span data-ttu-id="dbc24-108">一般的な連絡先マネージャーが組み込まれており、それを Live Messenger やその他の Live 対応アプリケーションで使用して、連絡先エンドポイント、空き時間、プレゼンスを確認できます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-108">It incorporates the common Contact Manager that is used by Live Messenger and other Live-aware applications to determine contact endpoints, availability, and presence.</span></span>  
  
-  
  
## <a name="collaboration-applications"></a><span data-ttu-id="dbc24-109">コラボレーション アプリケーション</span><span class="sxs-lookup"><span data-stu-id="dbc24-109">Collaboration Applications</span></span>  
 <span data-ttu-id="dbc24-110">一般的なピアツーピア コラボレーション アプリケーションで実行されるステップは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dbc24-110">A typical peer-to-peer collaboration application is comprised of the following steps:</span></span>  
  
-   <span data-ttu-id="dbc24-111">ピアが、コラボレーション セッションをホストすることに関心があるピアの ID を確認します。</span><span class="sxs-lookup"><span data-stu-id="dbc24-111">Peer determines the identity of a peer who is interested in hosting a collaboration session</span></span>  
  
-   <span data-ttu-id="dbc24-112">セッションをホストする要求が送信され、ホスト ピアが、コラボレーション活動を管理することに同意します。</span><span class="sxs-lookup"><span data-stu-id="dbc24-112">A request to host a session is sent, somehow, and the host peer agrees to manage collaboration activity.</span></span>  
  
-   <span data-ttu-id="dbc24-113">ホストがサブネット上の連絡先 (要求元を含む) をセッションに招待します。</span><span class="sxs-lookup"><span data-stu-id="dbc24-113">The host invites contacts on the subnet (including the requestor) to a session.</span></span>  
  
-   <span data-ttu-id="dbc24-114">コラボレーションを希望するすべてのピアが、ホストを連絡先マネージャーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-114">All peers who want to collaborate may add the host to their contact managers.</span></span>  
  
-   <span data-ttu-id="dbc24-115">ほとんどのピアが、適切なタイミングで招待への応答 (承諾または拒否) をホスト ピアに送信します。</span><span class="sxs-lookup"><span data-stu-id="dbc24-115">Most peers will send invitation responses, whether accepted or declined, back to the host peer in a timely fashion.</span></span>  
  
-   <span data-ttu-id="dbc24-116">コラボレーションを希望するすべてのピアが、ホスト ピアにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="dbc24-116">All peers who want to collaborate will subscribe to the host peer.</span></span>  
  
-   <span data-ttu-id="dbc24-117">ピアが初期コラボレーション活動を実行している間、ホスト ピアはリモート ピアを連絡先マネージャーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-117">While the peers are performing their initial collaboration activity, the host peer may add remote peers to its contact manager.</span></span> <span data-ttu-id="dbc24-118">また、招待へのすべての応答を処理して、どのピアが承諾または拒否したか、どのピアが未応答かを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbc24-118">It also processes all invitation responses to determine who has accepted, who has declined, and who has not answered.</span></span>  <span data-ttu-id="dbc24-119">未応答のピアへの招待を取り消したり、他の活動を実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-119">It may cancel invitations to those who have not answered, or perform some other activity.</span></span>  
  
-   <span data-ttu-id="dbc24-120">この時点で、ホスト ピアは招待したすべてのピアとのコラボレーション セッションを開始できます。または、コラボレーション インフラストラクチャにアプリケーションを登録できます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-120">At this point, the host peer can start a collaboration session with all invited peers, or register an application with the collaboration infrastructure.</span></span>  <span data-ttu-id="dbc24-121">P2P アプリケーションは、ピアツーピア コラボレーション インフラストラクチャと <xref:System.Net.PeerToPeer.Collaboration> 名前空間を使用して、ゲーム、掲示板、会議、およびその他のサーバーなしのプレゼンス アプリケーションの通信を調整します。</span><span class="sxs-lookup"><span data-stu-id="dbc24-121">P2P applications use the Peer-to-Peer Collaboration Infrastructure and the <xref:System.Net.PeerToPeer.Collaboration> namespace to coordinate communications for games, bulletin boards, conferencing, and other serverless presence applications.</span></span>  
  
-  
  
## <a name="peer-to-peer-networking-security"></a><span data-ttu-id="dbc24-122">ピアツーピア ネットワーキングのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="dbc24-122">Peer-to-Peer Networking Security</span></span>  
 <span data-ttu-id="dbc24-123">Active Directory ドメインでは、ドメイン コントローラーが Kerberos を使用した認証サービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="dbc24-123">In an Active Directory domain, domain controllers provide authentication services using Kerberos.</span></span> <span data-ttu-id="dbc24-124">サーバーなしのピア環境では、ピアは独自の認証を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbc24-124">In a serverless peer environment, the peers must provide their own authentication.</span></span> <span data-ttu-id="dbc24-125">ピアツーピア ネットワーキングでは、どのノードも CA として活動できるため、各ピアの信頼されたルート ストアにルート証明書は不要です。</span><span class="sxs-lookup"><span data-stu-id="dbc24-125">For Peer-to-Peer Networking, any node can act as a CA, removing the requirement of a root certificate in each peer's trusted root store.</span></span> <span data-ttu-id="dbc24-126">認証は、X.509 証明書として書式設定された自己署名証明書を使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-126">Authentication is provided using self-signed certificates, formatted as X.509 certificates.</span></span> <span data-ttu-id="dbc24-127">これらの証明書は各ピアによって作成されます。各ピアは、公開キーおよび秘密キーのペアと、秘密キーを使用して署名された証明書を生成します。</span><span class="sxs-lookup"><span data-stu-id="dbc24-127">These are certificates that are created by each peer, which generates the public key/private key pair and the certificate that is signed using the private key.</span></span> <span data-ttu-id="dbc24-128">自己署名証明書は、認証のために、また、ピア エンティティについての情報を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="dbc24-128">The self-signed certificate is used for authentication and to provide information about the peer entity.</span></span> <span data-ttu-id="dbc24-129">X.509 認証と同様に、ピア ネットワーキング認証は、信頼された公開キーまでさかのぼることができる証明書チェーンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="dbc24-129">Like X.509 authentication, peer networking authentication relies upon a chain of certificates tracing back to a public key that is trusted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc24-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbc24-130">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Collaboration>  
 [<span data-ttu-id="dbc24-131">System.Net.PeerToPeer.Collaboration 名前空間について</span><span class="sxs-lookup"><span data-stu-id="dbc24-131">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
