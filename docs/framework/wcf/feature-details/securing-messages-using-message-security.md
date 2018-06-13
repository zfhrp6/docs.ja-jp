---
title: メッセージ セキュリティを使用したメッセージのセキュリティ保護
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1ebe2526e564ef24d20f1602fd5824b44e2e2bbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498691"
---
# <a name="securing-messages-using-message-security"></a><span data-ttu-id="974ae-102">メッセージ セキュリティを使用したメッセージのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="974ae-102">Securing Messages Using Message Security</span></span>
<span data-ttu-id="974ae-103">使用する場合、このセクションでは WCF メッセージ セキュリティを説明<xref:System.ServiceModel.NetMsmqBinding>です。</span><span class="sxs-lookup"><span data-stu-id="974ae-103">This section discusses WCF message security when using <xref:System.ServiceModel.NetMsmqBinding>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="974ae-104">このトピック全体を読み取る前にお勧めお読みになる[セキュリティの基本概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)です。</span><span class="sxs-lookup"><span data-stu-id="974ae-104">Before reading through this topic, it is recommended that you read [Security Concepts](../../../../docs/framework/wcf/feature-details/security-concepts.md).</span></span>  
  
 <span data-ttu-id="974ae-105">次の図は、WCF を使用してキューに置かれた通信の概念モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="974ae-105">The following illustration provides a conceptual model of queued communication using WCF.</span></span> <span data-ttu-id="974ae-106">この図および用語を使用して、トランスポート セキュリティの</span><span class="sxs-lookup"><span data-stu-id="974ae-106">This illustration and terminology are used to explain</span></span>  
  
 <span data-ttu-id="974ae-107">概念について解説します。</span><span class="sxs-lookup"><span data-stu-id="974ae-107">transport security concepts.</span></span>  
  
 <span data-ttu-id="974ae-108">![アプリケーション ダイアグラムをキューに置かれた](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "分散キュー図")</span><span class="sxs-lookup"><span data-stu-id="974ae-108">![Queued Application Diagram](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distributed-Queue-Figure")</span></span>  
  
 <span data-ttu-id="974ae-109">送信するには、WCF を使用してメッセージをキューに置かれた、WCF メッセージはメッセージ キュー (MSMQ) メッセージの本文として添付します。</span><span class="sxs-lookup"><span data-stu-id="974ae-109">When sending queued messages using WCF, the WCF message is attached as a body of the Message Queuing (MSMQ) message.</span></span> <span data-ttu-id="974ae-110">トランスポート セキュリティが MSMQ メッセージ全体を保護するのに対し、メッセージ (SOAP) セキュリティは MSMQ メッセージの本文だけを保護します。</span><span class="sxs-lookup"><span data-stu-id="974ae-110">While transport security secures the entire MSMQ message, message (or SOAP) security only secures the body of the MSMQ message.</span></span>  
  
 <span data-ttu-id="974ae-111">メッセージ セキュリティの重要な概念は、クライアントが受信側アプリケーション (サービス) のメッセージを保護する点にあります。これは、クライアントがターゲット キューのメッセージを保護するトランスポート セキュリティとは異なります。</span><span class="sxs-lookup"><span data-stu-id="974ae-111">The key concept of message security is that the client secures the message for the receiving application (service), unlike transport security where the client secures the message for the Target Queue.</span></span> <span data-ttu-id="974ae-112">そのため、MSMQ 役割を果たしますありませんメッセージ セキュリティを使用して、WCF メッセージをセキュリティで保護するときにします。</span><span class="sxs-lookup"><span data-stu-id="974ae-112">As such, MSMQ plays no part when securing the WCF message using message security.</span></span>  
  
 <span data-ttu-id="974ae-113">WCF メッセージ セキュリティは、証明書または Kerberos プロトコルなどの既存のセキュリティ インフラストラクチャと統合される WCF メッセージをセキュリティ ヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="974ae-113">WCF message security adds security headers to the WCF message that integrate with existing security infrastructures, such as a certificate or the Kerberos protocol.</span></span>  
  
## <a name="message-credential-type"></a><span data-ttu-id="974ae-114">メッセージ資格情報の種類</span><span class="sxs-lookup"><span data-stu-id="974ae-114">Message Credential Type</span></span>  
 <span data-ttu-id="974ae-115">メッセージ セキュリティを使用すると、サービスとクライアントは、資格情報を提示して相互を認証します。</span><span class="sxs-lookup"><span data-stu-id="974ae-115">Using message security, the service and client can present credentials to authenticate each another.</span></span> <span data-ttu-id="974ae-116">メッセージ セキュリティを選択するには、<xref:System.ServiceModel.NetMsmqBinding.Security%2A> モードを `Message` または `Both` (トランスポート セキュリティとメッセージ セキュリティの両方を使用) に設定します。</span><span class="sxs-lookup"><span data-stu-id="974ae-116">You can select message security by setting the <xref:System.ServiceModel.NetMsmqBinding.Security%2A> mode to `Message` or `Both` (that is, use both transport security and message security).</span></span>  
  
 <span data-ttu-id="974ae-117">サービスは、<xref:System.ServiceModel.ServiceSecurityContext.Current%2A> プロパティを使用して、クライアントを認証するために使用される資格情報を検査できます。</span><span class="sxs-lookup"><span data-stu-id="974ae-117">The service can use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to inspect the credential used to authenticate the client.</span></span> <span data-ttu-id="974ae-118">このプロパティを使用して承認チェックも追加できますが、これを実装するかどうかはサービスで選択します。</span><span class="sxs-lookup"><span data-stu-id="974ae-118">This can also be used for further authorization checks that the service chooses to implement.</span></span>  
  
 <span data-ttu-id="974ae-119">ここでは、さまざまな資格情報の種類およびそれらをキューで使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="974ae-119">This section explains the different credential types and how to use them with queues.</span></span>  
  
### <a name="certificate"></a><span data-ttu-id="974ae-120">証明書</span><span class="sxs-lookup"><span data-stu-id="974ae-120">Certificate</span></span>  
 <span data-ttu-id="974ae-121">資格情報の種類に証明書を設定すると、X509 証明書を使用してサービスとクライアントが識別されます。</span><span class="sxs-lookup"><span data-stu-id="974ae-121">The certificate credential type uses an X.509 certificate to identify the service and the client.</span></span>  
  
 <span data-ttu-id="974ae-122">一般的なシナリオでは、信頼された証明機関によってクライアントとサービスに有効な証明書が発行されます。</span><span class="sxs-lookup"><span data-stu-id="974ae-122">In a typical scenario, the client and the service are issued a valid certificate by a trusted certification authority.</span></span> <span data-ttu-id="974ae-123">その後、接続が確立され、クライアントは、サービスの証明書を使用してサービスの有効性を確認することにより、サービスを信頼できるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="974ae-123">Then the connection is established, the client authenticates the validity of the service using the service's certificate to decide whether it can trust the service.</span></span> <span data-ttu-id="974ae-124">同様に、サービスは、クライアントの証明書を使用してクライアントの信頼性を検証します。</span><span class="sxs-lookup"><span data-stu-id="974ae-124">Similarly, the service uses the client's certificate to validate the client trust.</span></span>  
  
 <span data-ttu-id="974ae-125">キューは切断されているため、クライアントとサービスが同時にオンライン状態にならない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-125">Given the disconnected nature of queues, the client and the service may not be online at the same time.</span></span> <span data-ttu-id="974ae-126">したがって、クライアントとサービスは、帯域外で証明書を交換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-126">As such, the client and service have to exchange certificates out-of-band.</span></span> <span data-ttu-id="974ae-127">特にクライアントは、信頼されたストア内にサービスの証明書 (証明機関にチェーンできる) を保持しているという理由で、正しいサービスと通信していると信じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-127">In particular, the client, by virtue of holding the service's certificate (which can be chained to a certification authority) in its trusted store, must trust that it is communicating with the correct service.</span></span> <span data-ttu-id="974ae-128">クライアントを認証する場合、サービスはメッセージに添付された X509 証明書を使用し、ストア内の証明書と照合してクライアントの信頼性を確認します。</span><span class="sxs-lookup"><span data-stu-id="974ae-128">For authenticating the client, the service uses the X.509 certificate attached with the message to matches it with the certificate in its store to verify the authenticity of the client.</span></span> <span data-ttu-id="974ae-129">この場合も、証明書は証明機関にチェーンされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-129">Again, the certificate must be chained to a certification authority.</span></span>  
  
 <span data-ttu-id="974ae-130">Windows を実行しているコンピューターでは、証明書は数種類のストアで保持されています。</span><span class="sxs-lookup"><span data-stu-id="974ae-130">On a computer running Windows, certificates are held in several kinds of stores.</span></span> <span data-ttu-id="974ae-131">別のストアの詳細については、次を参照してください。[証明書のストア](http://go.microsoft.com/fwlink/?LinkId=87787)です。</span><span class="sxs-lookup"><span data-stu-id="974ae-131">For more information about the different stores, see [Certificate stores](http://go.microsoft.com/fwlink/?LinkId=87787).</span></span>  
  
### <a name="windows"></a><span data-ttu-id="974ae-132">Windows</span><span class="sxs-lookup"><span data-stu-id="974ae-132">Windows</span></span>  
 <span data-ttu-id="974ae-133">メッセージ資格情報の種類に Windows を設定すると、Kerberos プロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="974ae-133">Windows message credential type uses the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="974ae-134">Kerberos プロトコルは、ドメインのユーザーを認証するためのセキュリティ機構で、認証済みユーザーは、ドメインの他のエンティティとの間にセキュリティで保護されたコンテキストを確立できます。</span><span class="sxs-lookup"><span data-stu-id="974ae-134">The Kerberos protocol is a security mechanism that authenticates users on a domain and allows the authenticated users to establish secure contexts with other entities on a domain.</span></span>  
  
 <span data-ttu-id="974ae-135">キューを使用した通信で Kerberos プロトコルを使用する場合の問題は、キー配布センター (KDC) が配布するクライアント ID を含むチケットの有効期間が比較的短いことです。</span><span class="sxs-lookup"><span data-stu-id="974ae-135">The problem with using the Kerberos protocol for queued communication is that the tickets that contain client identity that the Key Distribution Center (KDC) distributes are relatively short-lived.</span></span> <span data-ttu-id="974ae-136">A*有効期間*チケットの有効性を示す、Kerberos チケットに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="974ae-136">A *lifetime* is associated with the Kerberos ticket that indicates the validity of the ticket.</span></span> <span data-ttu-id="974ae-137">そのため、遅延が大きい場合、クライアントを認証するサービスに対してトークンがまだ有効であるかどうかを確信できなくなります。</span><span class="sxs-lookup"><span data-stu-id="974ae-137">As such, given high latency, you cannot be sure that the token is still valid for the service that authenticates the client.</span></span>  
  
 <span data-ttu-id="974ae-138">この種類の資格情報を使用する場合、SERVICE アカウントでサービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-138">Note that when using this credential type, the service must be running under the SERVICE account.</span></span>  
  
 <span data-ttu-id="974ae-139">メッセージ資格情報を選択すると、既定で Kerberos プロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="974ae-139">The Kerberos protocol is used by default when choosing message credential.</span></span> <span data-ttu-id="974ae-140">詳細については、次を参照してください。[探索 Kerberos、Windows 2000 でのセキュリティの配布用のプロトコル](http://go.microsoft.com/fwlink/?LinkId=87790)です。</span><span class="sxs-lookup"><span data-stu-id="974ae-140">For more information, see [Exploring Kerberos, the Protocol for Distributed Security in Windows 2000](http://go.microsoft.com/fwlink/?LinkId=87790).</span></span>  
  
### <a name="username-password"></a><span data-ttu-id="974ae-141">ユーザー名とパスワード</span><span class="sxs-lookup"><span data-stu-id="974ae-141">Username Password</span></span>  
 <span data-ttu-id="974ae-142">このプロパティを使用すると、クライアントは、メッセージのセキュリティ ヘッダーに含まれるユーザー名とパスワードを使用してサーバーに認証できます。</span><span class="sxs-lookup"><span data-stu-id="974ae-142">Using this property, the client can authenticate to the server using a username password in the security header of the message.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="974ae-143">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="974ae-143">IssuedToken</span></span>  
 <span data-ttu-id="974ae-144">クライアントは、セキュリティ トークン サービスを使用してトークンを発行できます。発行されたトークンをサービスへのメッセージに添付することで、クライアントが認証されます。</span><span class="sxs-lookup"><span data-stu-id="974ae-144">The client can use the security token service to issue a token that can then be attached to the message for the service to authenticate the client.</span></span>  
  
## <a name="using-transport-and-message-security"></a><span data-ttu-id="974ae-145">トランスポート セキュリティとメッセージ セキュリティの使用</span><span class="sxs-lookup"><span data-stu-id="974ae-145">Using Transport and Message Security</span></span>  
 <span data-ttu-id="974ae-146">トランスポート セキュリティとメッセージ セキュリティの両方を使用する場合は、トランスポート レベルと SOAP メッセージ レベルの両方で同じ証明書を使用してメッセージを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="974ae-146">When using both transport security and message security, the certificate used to secure the message both at the transport and the SOAP message level must be the same.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974ae-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="974ae-147">See Also</span></span>  
 [<span data-ttu-id="974ae-148">トランスポート セキュリティを使用したメッセージのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="974ae-148">Securing Messages Using Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [<span data-ttu-id="974ae-149">メッセージ キューを介したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="974ae-149">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 [<span data-ttu-id="974ae-150">セキュリティの概念</span><span class="sxs-lookup"><span data-stu-id="974ae-150">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [<span data-ttu-id="974ae-151">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="974ae-151">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
