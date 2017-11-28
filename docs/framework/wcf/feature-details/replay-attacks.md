---
title: "リプレイ攻撃"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 81bca4572b6c4845674c63284f93c86fe5925bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="replay-attacks"></a><span data-ttu-id="1180b-102">リプレイ攻撃</span><span class="sxs-lookup"><span data-stu-id="1180b-102">Replay Attacks</span></span>
<span data-ttu-id="1180b-103">A*リプレイ攻撃*攻撃者は、2 つのパーティ間でメッセージのストリームをコピーし、1 つまたは複数のパーティのストリームをリプレイするときに発生します。</span><span class="sxs-lookup"><span data-stu-id="1180b-103">A *replay attack* occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="1180b-104">攻撃が和らげられていない場合、攻撃対象になったコンピューターはストリームを正当なメッセージとして処理するため、項目の順序が重複するなど、望ましくない状況に陥ります。</span><span class="sxs-lookup"><span data-stu-id="1180b-104">Unless mitigated, the computers subject to the attack process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a><span data-ttu-id="1180b-105">バインディングはリフレクション攻撃にさらされる可能性がある</span><span class="sxs-lookup"><span data-stu-id="1180b-105">Bindings May Be Subject to Reflection Attacks</span></span>  
 <span data-ttu-id="1180b-106">*リフレクション攻撃*からの応答として受信機と送信者に返信されるメッセージのリプレイです。</span><span class="sxs-lookup"><span data-stu-id="1180b-106">*Reflection attacks* are replays of messages back to a sender as if they came from the receiver as the reply.</span></span> <span data-ttu-id="1180b-107">標準*リプレイ検出*で、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]メカニズムが自動的に処理しないこれです。</span><span class="sxs-lookup"><span data-stu-id="1180b-107">The standard *replay detection* in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanism does not automatically handle this.</span></span>  
  
 <span data-ttu-id="1180b-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサービス モデルは、署名されたメッセージ ID を要求メッセージに追加し、署名された `relates-to` ヘッダーを応答メッセージに要求するため、既定でリフレクション攻撃が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="1180b-108">Reflection attacks are mitigated by default because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service model adds a signed message ID to request messages and expects a signed `relates-to` header on response messages.</span></span> <span data-ttu-id="1180b-109">その結果、要求メッセージを応答としてリプレイできません。</span><span class="sxs-lookup"><span data-stu-id="1180b-109">Consequently, the request message cannot be replayed as a response.</span></span> <span data-ttu-id="1180b-110">セキュリティで保護された信頼できるメッセージ (RM) シナリオでは、リフレクション攻撃は次の理由で軽減されます。</span><span class="sxs-lookup"><span data-stu-id="1180b-110">In secure reliable message (RM) scenarios, reflection attacks are mitigated because:</span></span>  
  
-   <span data-ttu-id="1180b-111">シーケンス メッセージの作成スキーマとシーケンス応答メッセージの作成スキーマが異なります。</span><span class="sxs-lookup"><span data-stu-id="1180b-111">The create sequence and create sequence response message schemas are different.</span></span>  
  
-   <span data-ttu-id="1180b-112">一方向シーケンスの場合、クライアントから送信されたシーケンス メッセージをクライアントに対してリプレイすることはできません。これは、クライアントがこのようなメッセージを認識できないためです。</span><span class="sxs-lookup"><span data-stu-id="1180b-112">For simplex sequences, sequence messages the client sends cannot be replayed back to it because the client cannot understand such messages.</span></span>  
  
-   <span data-ttu-id="1180b-113">双方向シーケンスの場合、2 つのシーケンス ID が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1180b-113">For duplex sequences, the two sequence IDs must be unique.</span></span> <span data-ttu-id="1180b-114">このため、送信シーケンス メッセージを受信シーケンス メッセージとしてリプレイできません (すべてのシーケンス ヘッダーと本文も署名されています)。</span><span class="sxs-lookup"><span data-stu-id="1180b-114">Thus, an outgoing sequence message cannot be replayed back as an incoming sequence message (all sequence headers and bodies are signed, too).</span></span>  
  
 <span data-ttu-id="1180b-115">リフレクション攻撃の影響を受けやすい唯一のバインディングは WS-Addressing を使用しないバインディング (WS-Addressing を無効にして、対称キー ベースのセキュリティを使用するカスタム バインディング) です。</span><span class="sxs-lookup"><span data-stu-id="1180b-115">The only bindings that are susceptible to reflection attacks are those without WS-Addressing: custom bindings that have WS-Addressing disabled and use the symmetric key-based security.</span></span> <span data-ttu-id="1180b-116"><xref:System.ServiceModel.BasicHttpBinding> は、既定では WS-Addressing を使用しませんが、この攻撃を受けやすい方法で対称キー ベースのセキュリティを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="1180b-116">The <xref:System.ServiceModel.BasicHttpBinding> does not use WS-Addressing by default, but it does not use symmetric key-based security in a way that allows it to be vulnerable to this attack.</span></span>  
  
 <span data-ttu-id="1180b-117">カスタム バインディングに対する攻撃を軽減するには、セキュリティ コンテキストを確立しないか、WS-Addressing ヘッダーを要求します。</span><span class="sxs-lookup"><span data-stu-id="1180b-117">The mitigation for custom bindings is to not establish security context or to require WS-Addressing headers.</span></span>  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a><span data-ttu-id="1180b-118">Web ファーム : 攻撃者が複数のノードに対して要求をリプレイする</span><span class="sxs-lookup"><span data-stu-id="1180b-118">Web Farm: Attacker Replays Request to Multiple Nodes</span></span>  
 <span data-ttu-id="1180b-119">クライアントは、Web ファームに実装されているサービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1180b-119">A client uses a service that is implemented on a Web farm.</span></span> <span data-ttu-id="1180b-120">攻撃者は、ファーム内の特定のノードに送信された要求を同じファーム内の別のノードに対してリプレイします。</span><span class="sxs-lookup"><span data-stu-id="1180b-120">An attacker replays a request that was sent to one node in the farm to another node in the farm.</span></span> <span data-ttu-id="1180b-121">また、サービスが再開されると、リプレイ キャッシュがフラッシュされ、攻撃者が要求をリプレイできるようになります </span><span class="sxs-lookup"><span data-stu-id="1180b-121">In addition, if a service is restarted, the replay cache is flushed, allowing an attacker to replay the request.</span></span> <span data-ttu-id="1180b-122">(このキャッシュには、以前使用されたメッセージ署名の値が格納されています。これにより、メッセージ署名は一度しか使用できないため、リプレイを防止できます。</span><span class="sxs-lookup"><span data-stu-id="1180b-122">(The cache contains used, previously seen message signature values and prevents replays so those signatures can be used only once.</span></span> <span data-ttu-id="1180b-123">リプレイ キャッシュは Web ファーム内で共有されません)。</span><span class="sxs-lookup"><span data-stu-id="1180b-123">Replay caches are not shared across a Web farm.)</span></span>  
  
 <span data-ttu-id="1180b-124">回避事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1180b-124">Mitigations include:</span></span>  
  
-   <span data-ttu-id="1180b-125">ステートフルなセキュリティ コンテキスト トークンと共にメッセージ モード セキュリティを使用します (セキュリティで保護されたメッセージ交換を有効にするかどうかは任意)。</span><span class="sxs-lookup"><span data-stu-id="1180b-125">Use message mode security with stateful security context tokens (with or without secure conversation enabled).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="1180b-126">[する方法: セキュリティ コンテキストを作成、セキュリティで保護されたセッションのトークン](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="1180b-126"> [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
-   <span data-ttu-id="1180b-127">トランスポート レベルのセキュリティを使用するようにサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="1180b-127">Configure the service to use transport-level security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1180b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="1180b-128">See Also</span></span>  
 [<span data-ttu-id="1180b-129">セキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="1180b-129">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="1180b-130">情報漏えいが起こる</span><span class="sxs-lookup"><span data-stu-id="1180b-130">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="1180b-131">特権の昇格</span><span class="sxs-lookup"><span data-stu-id="1180b-131">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="1180b-132">サービス拒否が起こる</span><span class="sxs-lookup"><span data-stu-id="1180b-132">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="1180b-133">改ざん</span><span class="sxs-lookup"><span data-stu-id="1180b-133">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [<span data-ttu-id="1180b-134">サポートされていないシナリオ</span><span class="sxs-lookup"><span data-stu-id="1180b-134">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
