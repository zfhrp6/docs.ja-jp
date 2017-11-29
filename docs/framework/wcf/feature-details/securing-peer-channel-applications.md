---
title: "セキュリティによるピア チャネル アプリケーションの保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02bad6b5c7460655f4d3a5851e4e74d7de12111f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="securing-peer-channel-applications"></a><span data-ttu-id="937e8-102">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="937e8-102">Securing Peer Channel Applications</span></span>
<span data-ttu-id="937e8-103">[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] での他のバインディングと同様に、`NetPeerTcpBinding` には、既定で有効にされているセキュリティがあり、トランスポート ベースのセキュリティとメッセージ ベースのセキュリティが提供されます。</span><span class="sxs-lookup"><span data-stu-id="937e8-103">Like other bindings under the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` has security enabled by default and offers both transport- and message-based security (or both).</span></span> <span data-ttu-id="937e8-104">このトピックでは、これら 2 種類のセキュリティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="937e8-104">This topic discusses these two types of security.</span></span> <span data-ttu-id="937e8-105">セキュリティの種類は、バインディング仕様のセキュリティ モード タグ (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`) で指定します。</span><span class="sxs-lookup"><span data-stu-id="937e8-105">The type of security is specified by the security mode tag in the binding specification (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).</span></span>  
  
## <a name="transport-based-security"></a><span data-ttu-id="937e8-106">トランスポート ベースのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="937e8-106">Transport-Based Security</span></span>  
 <span data-ttu-id="937e8-107">ピア チャネルでは、トランスポートをセキュリティで保護するための 2 種類の認証資格情報がサポートされます。両方とも、関連する `ClientCredentialSettings.Peer` で `ChannelFactory` プロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="937e8-107">Peer Channel supports two types of authentication credentials for securing transport, both of which require setting out the `ClientCredentialSettings.Peer` property on the associated `ChannelFactory`:</span></span>  
  
-   <span data-ttu-id="937e8-108">パスワード。</span><span class="sxs-lookup"><span data-stu-id="937e8-108">Password.</span></span> <span data-ttu-id="937e8-109">クライアントは、接続の認証に秘密パスワードの知識を利用します。</span><span class="sxs-lookup"><span data-stu-id="937e8-109">Clients use knowledge of a secret password to authenticate connections.</span></span> <span data-ttu-id="937e8-110">この種類の資格情報を使用する場合、`ClientCredentialSettings.Peer.MeshPassword` は、有効なパスワードと、必要に応じて `X509Certificate2` インスタンスを転送する必要があります。</span><span class="sxs-lookup"><span data-stu-id="937e8-110">When this credential type is used, `ClientCredentialSettings.Peer.MeshPassword` must carry a valid password and optionally an `X509Certificate2` instance.</span></span>  
  
-   <span data-ttu-id="937e8-111">証明書。</span><span class="sxs-lookup"><span data-stu-id="937e8-111">Certificate.</span></span> <span data-ttu-id="937e8-112">特定のアプリケーション認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="937e8-112">Specific application authentication is used.</span></span> <span data-ttu-id="937e8-113">この種類の資格情報を使用する場合は、<xref:System.IdentityModel.Selectors.X509CertificateValidator> で `ClientCredentialSettings.Peer.PeerAuthentication` の具体的な実装を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="937e8-113">When this credential type is used, you must use a concrete implementation of <xref:System.IdentityModel.Selectors.X509CertificateValidator> in `ClientCredentialSettings.Peer.PeerAuthentication`.</span></span>  
  
## <a name="message-based-security"></a><span data-ttu-id="937e8-114">メッセージ ベース セキュリティ</span><span class="sxs-lookup"><span data-stu-id="937e8-114">Message-Based Security</span></span>  
 <span data-ttu-id="937e8-115">メッセージ セキュリティを使用すると、アプリケーションで送信メッセージに署名できるので、メッセージが信頼されたパーティから送信されたこと、および転送中にメッセージが改ざんされていないことをすべての受信パーティが確認できます。</span><span class="sxs-lookup"><span data-stu-id="937e8-115">Using message security, an application can sign outgoing messages so that all receiving parties can verify the message is sent by a trusted party and that the message was not tampered with.</span></span> <span data-ttu-id="937e8-116">現在、ピア チャネルでは、X.509 資格情報メッセージの署名のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="937e8-116">Currently, Peer Channel supports only X.509 credential message signing.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="937e8-117">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="937e8-117">Best Practices</span></span>  
  
-   <span data-ttu-id="937e8-118">ここでは、ピア チャネル アプリケーションをセキュリティで保護するためのベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="937e8-118">This section discusses the best practices for securing Peer Channel applications.</span></span>  
  
### <a name="enable-security-with-peer-channel-applications"></a><span data-ttu-id="937e8-119">ピア チャネル アプリケーションでセキュリティを有効にする</span><span class="sxs-lookup"><span data-stu-id="937e8-119">Enable Security with Peer Channel Applications</span></span>  
 <span data-ttu-id="937e8-120">ピア チャネル プロトコルは分散的な性質のため、セキュリティで保護されていないメッシュ内でメッシュ メンバーシップ、機密性、およびプライバシーを強化することは困難です。</span><span class="sxs-lookup"><span data-stu-id="937e8-120">Due to the distributed nature of the Peer Channel protocols, it is hard to enforce mesh membership, confidentiality, and privacy in an unsecured mesh.</span></span> <span data-ttu-id="937e8-121">クライアントとリゾルバー サービス間の通信をセキュリティで保護することも重要です。</span><span class="sxs-lookup"><span data-stu-id="937e8-121">It is also important to remember to secure communication between clients and the resolver service.</span></span> <span data-ttu-id="937e8-122">PNRP (Peer Name Resolution Protocol) では、セキュリティで保護された名前を使用してスプーフィングや他の一般的な攻撃を回避してください。</span><span class="sxs-lookup"><span data-stu-id="937e8-122">Under Peer Name Resolution Protocol (PNRP), use secure names to avoid spoofing and other common attacks.</span></span> <span data-ttu-id="937e8-123">カスタム リゾルバー サービスをセキュリティで保護するには、メッセージ ベース セキュリティおよびトランスポート ベース セキュリティの両方を含むリゾルバー サービスにアクセスするためにクライアントが使用する接続でセキュリティを有効にします。</span><span class="sxs-lookup"><span data-stu-id="937e8-123">Secure a custom resolver service by enabling security on the connection clients use to contact the resolver service, including both message- and transport-based security.</span></span>  
  
### <a name="use-the-strongest-possible-security-model"></a><span data-ttu-id="937e8-124">可能な限り強力なセキュリティ モデルを使用する</span><span class="sxs-lookup"><span data-stu-id="937e8-124">Use the Strongest Possible Security Model</span></span>  
 <span data-ttu-id="937e8-125">たとえば、メッシュの各メンバーを個々に識別する必要がある場合は、証明書ベースの認証モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="937e8-125">For example, if each member of the mesh needs to be individually identified, use certificate-based authentication model.</span></span> <span data-ttu-id="937e8-126">これが不可能な場合は、セキュリティ保護のための最新の推奨事項に従ってパスワード ベースの認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="937e8-126">If that is not possible, use password-based authentication following current recommendations to keep them secure.</span></span> <span data-ttu-id="937e8-127">推奨事項には、信頼されたパーティとのパスワードの共有、セキュリティで保護された媒介を使用するパスワードの転送、パスワードの頻繁な変更、強力なパスワード (8 文字以上で、1 文字以上の大文字/小文字、数字、特殊文字を含める) の確認などがあります。</span><span class="sxs-lookup"><span data-stu-id="937e8-127">This includes sharing passwords only with trusted parties, transmitting passwords using a secure medium, changing passwords frequently, and ensuring that passwords are strong (at least eight characters long, include at least one letter from both cases, a digit, and a special character).</span></span>  
  
### <a name="never-accept-self-signed-certificates"></a><span data-ttu-id="937e8-128">自己署名された証明書を受け入れない</span><span class="sxs-lookup"><span data-stu-id="937e8-128">Never Accept Self-Signed Certificates</span></span>  
 <span data-ttu-id="937e8-129">サブジェクト名に基づいて証明書の資格情報を受け入れないでください。</span><span class="sxs-lookup"><span data-stu-id="937e8-129">Never accept a certificate credential based on subject names.</span></span> <span data-ttu-id="937e8-130">証明書はだれもが作成でき、検証する名前をだれもが選択できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="937e8-130">Note that anyone can create a certificate, and anyone can choose a name that you are validating.</span></span> <span data-ttu-id="937e8-131">スプーフィングの可能性を回避するには、発行元証明機関 (信頼された発行者またはルート証明機関) の資格情報に基づいて証明書を検証します。</span><span class="sxs-lookup"><span data-stu-id="937e8-131">To avoid the possibility of spoofing, validate certificates based on issuing authority credentials (either a trusted issuer or a root certification authority).</span></span>  
  
### <a name="use-message-authentication"></a><span data-ttu-id="937e8-132">メッセージ認証を使用する</span><span class="sxs-lookup"><span data-stu-id="937e8-132">Use Message Authentication</span></span>  
 <span data-ttu-id="937e8-133">メッセージ認証を使用して、メッセージが信用されるソースから送信されていること、および送信中にメッセージが改ざんされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="937e8-133">Use message authentication to verify that a message originated from a trusted source and that no one has tampered with the message during transmission.</span></span> <span data-ttu-id="937e8-134">メッセージ認証を使用しないと、悪質なクライアントがメッセージを使用して容易に他人になりすましたり、メッセージを容易に改ざんしたりできます。</span><span class="sxs-lookup"><span data-stu-id="937e8-134">Without message authentication, it is easy for a malicious client to spoof or tamper with messages in the mesh.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="937e8-135">ピア チャネルのコード例</span><span class="sxs-lookup"><span data-stu-id="937e8-135">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="937e8-136">ピア チャネルのシナリオ</span><span class="sxs-lookup"><span data-stu-id="937e8-136">Peer Channel Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="937e8-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="937e8-137">See Also</span></span>  
 [<span data-ttu-id="937e8-138">ピア チャネルのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="937e8-138">Peer Channel Security</span></span>](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="937e8-139">ピア チャネル アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="937e8-139">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
