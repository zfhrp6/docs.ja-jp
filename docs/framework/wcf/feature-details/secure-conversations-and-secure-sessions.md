---
title: "セキュリティ保護されたメッセージ交換とセッション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d519640c40daf248a01a19f0450f3aea8de6cc04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="secure-conversations-and-secure-sessions"></a><span data-ttu-id="fde62-102">セキュリティ保護されたメッセージ交換とセッション</span><span class="sxs-lookup"><span data-stu-id="fde62-102">Secure Conversations and Secure Sessions</span></span>
<span data-ttu-id="fde62-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の特徴の 1 つは、相互に認証を行い暗号化とデジタル署名のプロセスについて同意する、2 つのエンドポイント間でのセキュリティ保護されたセッションを確立する機能にあります。</span><span class="sxs-lookup"><span data-stu-id="fde62-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to establish secure sessions between two endpoints that authenticate each other and agree upon an encryption and digital signature process.</span></span> <span data-ttu-id="fde62-104">たとえば、サービス エンドポイントは、クライアント エンドポイントに対して認証のために X.509 証明書に基づいたセキュリティ トークンを送信するよう要求する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fde62-104">For example, the service endpoint might require a client endpoint to send a security token based upon an X.509 certificate for authentication.</span></span> <span data-ttu-id="fde62-105">クライアントの認証が終わると、サービス エンドポイントはセキュリティ コンテキスト トークン (SCT: Security Context Token) をクライアントに返します。このセッションにおける後続のすべてのメッセージは、このセキュリティ トークンを使用してセキュリティ保護されます。</span><span class="sxs-lookup"><span data-stu-id="fde62-105">Once the client is authenticated, the service endpoint returns a security context token (SCT) back to the client that is then used to secure all subsequent messages within the session.</span></span> <span data-ttu-id="fde62-106">セキュリティで保護されたセッションが確立されると、SCT には対称キーが含まれるため、2 つのエンドポイント間で交換される一連のメッセージの効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="fde62-106">Establishing this secure session enables the set of messages that are exchanged between the two endpoints to be more efficient, because the SCT has a symmetric key.</span></span> <span data-ttu-id="fde62-107">X.509 証明書の基盤となる非対称キーでは、デジタル署名の生成やデータの暗号化を行う場合に、対称キーに比べて非常に大きな計算能力が必要になります。</span><span class="sxs-lookup"><span data-stu-id="fde62-107">Asymmetric keys, which X.509 certificates are based upon, require significantly more computational power than symmetric keys when generating a digital signature or encrypting a set of data.</span></span>  
  
 <span data-ttu-id="fde62-108">ブートス トラップのポリシー (の 6.2.7 セクションで定義されている、 [Ws-securitypolicy](http://go.microsoft.com/fwlink/?LinkId=99817)標準)、チャネルをセキュリティで保護し、/SCT RST および RSTR/SCT 交換する前にクライアントを認証するために使用するメッセージのセキュリティ アサーションを格納します。</span><span class="sxs-lookup"><span data-stu-id="fde62-108">The bootstrap policy (defined in section 6.2.7 of the [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standard) contains the message security assertions used to secure the channel and authenticate the client prior to the RST/SCT and RSTR/SCT exchange.</span></span> <span data-ttu-id="fde62-109">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の標準バインディングの中には、セキュリティで保護されたメッセージ交換を使用するかどうかを制御する `Security.Message.EstablishSecurityContext` プロパティを持つものがあります。</span><span class="sxs-lookup"><span data-stu-id="fde62-109">Certain [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard bindings have a `Security.Message.EstablishSecurityContext` property which controls whether secure conversation is used.</span></span> <span data-ttu-id="fde62-110">カスタム バインドを使用してブートス トラップが使用するか、入れ子になったのセキュリティ バインド要素で示されます。 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)または呼び出すことによって、構成ファイルで<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>のコードにします。</span><span class="sxs-lookup"><span data-stu-id="fde62-110">When using custom bindings the bootstrap is indicated by nesting security binding elements, either through [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) in the configuration file, or by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> in code.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fde62-111">セッションを参照してください[セッションを使用した](../../../../docs/framework/wcf/using-sessions.md)です。</span><span class="sxs-lookup"><span data-stu-id="fde62-111"> sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde62-112">参照</span><span class="sxs-lookup"><span data-stu-id="fde62-112">See Also</span></span>  
 [<span data-ttu-id="fde62-113">セッション、インスタンス化、および同時実行</span><span class="sxs-lookup"><span data-stu-id="fde62-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="fde62-114">方法 : セッションを必要とするサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="fde62-114">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
