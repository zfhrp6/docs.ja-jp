---
title: "信頼できるメッセージング プロトコル バージョン 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a32c16067446459817e9943c2d729a67373a0333
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="529d1-102">信頼できるメッセージング プロトコル バージョン 1.0</span><span class="sxs-lookup"><span data-stu-id="529d1-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="529d1-103">ここでは、HTTP トランスポートを使用した相互運用に必要な WS-ReliableMessaging 2005/02 (バージョン 1.0) プロトコルに関する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 実装の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="529d1-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-104"> は、ここに記載した制約と説明に基づく WS-ReliableMessaging 仕様に従っています。</span><span class="sxs-lookup"><span data-stu-id="529d1-104"> follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="529d1-105">WS-ReliableMessaging バージョン 1.0 プロトコルは、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 以降に実装されています。</span><span class="sxs-lookup"><span data-stu-id="529d1-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="529d1-106">WS-ReliableMessaging 2005/02 プロトコルは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> に実装されます。</span><span class="sxs-lookup"><span data-stu-id="529d1-106">The WS-Reliable Messaging February 2005 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="529d1-107">便宜上、ここでは次のロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="529d1-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="529d1-108">イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント</span><span class="sxs-lookup"><span data-stu-id="529d1-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="529d1-109">レスポンダー : イニシエーターの要求を受け取るサービス</span><span class="sxs-lookup"><span data-stu-id="529d1-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="529d1-110">このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="529d1-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="529d1-111">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="529d1-111">Prefix</span></span>|<span data-ttu-id="529d1-112">名前空間</span><span class="sxs-lookup"><span data-stu-id="529d1-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="529d1-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="529d1-113">wsrm</span></span>|<span data-ttu-id="529d1-114">http://schemas.xmlsoap.org/ws/2005/02/rm</span><span class="sxs-lookup"><span data-stu-id="529d1-114">http://schemas.xmlsoap.org/ws/2005/02/rm</span></span>|  
|<span data-ttu-id="529d1-115">netrm</span><span class="sxs-lookup"><span data-stu-id="529d1-115">netrm</span></span>|<span data-ttu-id="529d1-116">http://schemas.microsoft.com/ws/2006/05/rm</span><span class="sxs-lookup"><span data-stu-id="529d1-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="529d1-117">s</span><span class="sxs-lookup"><span data-stu-id="529d1-117">s</span></span>|<span data-ttu-id="529d1-118">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="529d1-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="529d1-119">wsa</span><span class="sxs-lookup"><span data-stu-id="529d1-119">wsa</span></span>|<span data-ttu-id="529d1-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="529d1-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="529d1-121">wsse</span><span class="sxs-lookup"><span data-stu-id="529d1-121">wsse</span></span>|<span data-ttu-id="529d1-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="529d1-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="529d1-123">メッセージング</span><span class="sxs-lookup"><span data-stu-id="529d1-123">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="529d1-124">シーケンス確立メッセージ</span><span class="sxs-lookup"><span data-stu-id="529d1-124">Sequence Establishment Messages</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-125"> は、信頼性の高いメッセージ シーケンスを確立するために、`CreateSequence` メッセージと `CreateSequenceResponse` メッセージを実装しています。</span><span class="sxs-lookup"><span data-stu-id="529d1-125"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="529d1-126">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="529d1-126">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="529d1-127">B1101 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`CreateSequence` メッセージのオプションの Expires 要素を生成しません。また、`CreateSequence` メッセージに `Offer` 要素が含まれているときに、この `Expires` 要素内のオプションの `Offer` 要素も生成しません。</span><span class="sxs-lookup"><span data-stu-id="529d1-127">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="529d1-128">B1102: にアクセスするとき、`CreateSequence`メッセージ、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Responder`を送信および受信両方`Expires`要素が、存在しますが、値を使用しない場合。</span><span class="sxs-lookup"><span data-stu-id="529d1-128">B1102: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="529d1-129">WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構が導入されています。</span><span class="sxs-lookup"><span data-stu-id="529d1-129">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="529d1-130">R1103 : `CreateSequence` に `Offer` 要素が含まれている場合、Reliable メッセージング レスポンダーは、シーケンスを受け入れ、`CreateSequenceResponse` 要素を含む `wsrm:Accept` で応答して、相関する 2 つの逆方向シーケンスを形成するか、`CreateSequence` 要求を拒否する必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-130">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="529d1-131">R1104 : 逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-131">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="529d1-132">R1105 : `AcksTo` の `ReplyTo` エンドポイント参照と `CreateSequence` エンドポイント参照には、オクテット単位で一致するアドレス値が必要です。</span><span class="sxs-lookup"><span data-stu-id="529d1-132">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="529d1-133">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`AcksTo` EPR と `ReplyTo` EPR の URI 部分が同一であるかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="529d1-133">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="529d1-134">R1106 : `AcksTo` の `ReplyTo` および `CreateSequence` の各エンドポイント参照は、参照パラメーターの同じセットを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-134">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-135"> は、`AcksTo` の `ReplyTo` と `CreateSequence` の [参照パラメーター] が同一であることを強制するわけではありません。ただし、これらが同一であると想定した上で、受信確認と逆方向シーケンス メッセージに `ReplyTo` エンドポイント参照の [参照パラメーター] を使用します。</span><span class="sxs-lookup"><span data-stu-id="529d1-135"> does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="529d1-136">R1107 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-136">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="529d1-137">R1108 : Offer 機構を使用して 2 つの逆方向シーケンスを確立した場合、`[address]` の `wsrm:AcksTo` 要素の `wsrm:Accept` エンドポイント参照子要素の `CreateSequenceResponse` プロパティは、`CreateSequence` の送信先 URI とバイト単位で一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-137">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="529d1-138">R1109 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、イニシエーターによって送信されたメッセージとレスポンダーによるメッセージの受信確認は、同じエンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-138">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-139"> は、WS-ReliableMessaging を使用して、イニシエーターとレスポンダー間で信頼性できるセッションを確立します。</span><span class="sxs-lookup"><span data-stu-id="529d1-139"> uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-140"> の WS-ReliableMessaging 実装により、一方向、要求/応答、双方向の各メッセージ パターンの信頼できるセッションが実現します。</span><span class="sxs-lookup"><span data-stu-id="529d1-140">'s WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="529d1-141">Ws-reliable メッセージング`Offer`機構で`CreateSequence` / `CreateSequenceResponse` 2 つの相関関係を持つ逆方向シーケンスを確立することができ、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。</span><span class="sxs-lookup"><span data-stu-id="529d1-141">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="529d1-142">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、セッション整合性を保つためのエンドツーエンドの保護を含むこのようなセッションに対してセキュリティが保証されているため、同じパーティを対象とするメッセージが同じ送信先に到着することが事実上保証されます。</span><span class="sxs-lookup"><span data-stu-id="529d1-142">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="529d1-143">また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="529d1-143">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="529d1-144">したがって、制約 R1104、R1105、および R1108 が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用されています。</span><span class="sxs-lookup"><span data-stu-id="529d1-144">Therefore, constraints R1104, R1105, and R1108 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="529d1-145">`CreateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-145">An example of a `CreateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="529d1-146">`CreateSequenceResponse` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-146">An example of a `CreateSequenceResponse` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a><span data-ttu-id="529d1-147">シーケンス</span><span class="sxs-lookup"><span data-stu-id="529d1-147">Sequence</span></span>  
 <span data-ttu-id="529d1-148">シーケンスに適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-148">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="529d1-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を生成し、アクセスするシーケンス番号より`xs:long`の最大包括値、9223372036854775807 します。</span><span class="sxs-lookup"><span data-stu-id="529d1-149">B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="529d1-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage のアクション URI で空の本文の最終メッセージを常に生成されます。</span><span class="sxs-lookup"><span data-stu-id="529d1-150">B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="529d1-151">B1203 : アクション URI が http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage でない場合には、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `LastMessage` 要素を含むシーケンス ヘッダーを持つメッセージを受信および配信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-151">B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="529d1-152">シーケンス ヘッダーのサンプル</span><span class="sxs-lookup"><span data-stu-id="529d1-152">An example of a Sequence Header.</span></span>  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a><span data-ttu-id="529d1-153">AckRequested ヘッダー</span><span class="sxs-lookup"><span data-stu-id="529d1-153">AckRequested Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-154"> は、Keep-alive 機構として `AckRequested` ヘッダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="529d1-154"> uses `AckRequested` Header as a keep-alive mechanism.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-155"> は、オプションの `MessageNumber` 要素を生成しません。</span><span class="sxs-lookup"><span data-stu-id="529d1-155"> does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="529d1-156">`AckRequested` 要素を含む `MessageNumber` ヘッダーを持つメッセージを受信すると、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `MessageNumber` 要素の値を無視します。</span><span class="sxs-lookup"><span data-stu-id="529d1-156">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="529d1-157">SequenceAcknowledgement ヘッダー</span><span class="sxs-lookup"><span data-stu-id="529d1-157">SequenceAcknowledgement Header</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-158"> は、WS-ReliableMessaging で用意されているシーケンス受信確認の抱き合わせ機構を使用します。</span><span class="sxs-lookup"><span data-stu-id="529d1-158"> uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="529d1-159">R1401 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、目的の受信者に送信されるアプリケーション メッセージに、`SequenceAcknowledgement` ヘッダーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="529d1-159">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="529d1-160">B1402 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がシーケンス メッセージを受信する前に受信確認を生成する必要がある場合 (`AckRequested` メッセージに応える場合など)、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は範囲 0 ～ 0 を含む `SequenceAcknowledgement` ヘッダーを生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-160">B1402: When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="529d1-161">B1403 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`SequenceAcknowledgement` 要素をサポートしていますが、`Nack` 要素を含む `Nack` ヘッダーは生成しません。</span><span class="sxs-lookup"><span data-stu-id="529d1-161">B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="529d1-162">WS-ReliableMessaging エラー</span><span class="sxs-lookup"><span data-stu-id="529d1-162">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="529d1-163">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の WS-ReliableMessaging エラー実装に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-163">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="529d1-164">B1501 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`MessageNumberRollover` エラーを生成しません。</span><span class="sxs-lookup"><span data-stu-id="529d1-164">B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="529d1-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]エンドポイントが生成できる`CreateSequenceRefused`仕様」の説明に従ってエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="529d1-165">B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="529d1-166">B1503:When サービス エンドポイントは、接続の上限に達するし、新しい接続を処理できません[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]追加生成`CreateSequenceRefused`エラー サブコード`netrm:ConnectionLimitReached`次の例で示すように、です。</span><span class="sxs-lookup"><span data-stu-id="529d1-166">B1503:When the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="529d1-167">WS-Addressing エラー</span><span class="sxs-lookup"><span data-stu-id="529d1-167">WS-Addressing Faults</span></span>  
 <span data-ttu-id="529d1-168">WS-ReliableMessaging は WS-Addressing を使用するため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の WS-ReliableMessaging 実装は、WS-Addressing エラーを生成する場合があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-168">Because WS-Reliable Messaging uses WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="529d1-169">ここでは、WS-ReliableMessaging レイヤーで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が明示的に生成する WS-Addressing エラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="529d1-169">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="529d1-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]次のいずれかが当てはまる場合にメッセージのアドレス指定ヘッダーに必要なエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="529d1-170">B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="529d1-171">メッセージに `Sequence` ヘッダーと `Action` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="529d1-171">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="529d1-172">`CreateSequence` メッセージに `MessageId` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="529d1-172">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="529d1-173">`CreateSequence` メッセージに `ReplyTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="529d1-173">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="529d1-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]で欠落しているメッセージの返信アクションがサポートされていません、エラーが生成されます、`Sequence`ヘッダーがあり、`Action`が Ws-reliablemessaging 仕様で認識されないヘッダー。</span><span class="sxs-lookup"><span data-stu-id="529d1-174">B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="529d1-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]エラーをエンドポイントの検査に基づいて、シーケンスが処理されませんを示すために使用できないエンドポイント生成、`CreateSequence`メッセージのアドレス指定ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="529d1-175">B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="529d1-176">プロトコル コンポジション</span><span class="sxs-lookup"><span data-stu-id="529d1-176">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="529d1-177">WS-Addressing によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="529d1-177">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-178"> は、WS-Addressing の 2 つのバージョンをサポートしています。WS-Addressing 2004/08 [WS-ADDR] と、W3C WS-Addressing 1.0 Recommendation ([WS-ADDR-CORE] および [WS-ADDR-SOAP]) です。</span><span class="sxs-lookup"><span data-stu-id="529d1-178"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="529d1-179">WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="529d1-179">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="529d1-180">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-180">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="529d1-181">R2101: 両方 Ws-addressing 2004/08 と Ws-addressing 1.0 は、Ws-reliablemessaging で使用できます。</span><span class="sxs-lookup"><span data-stu-id="529d1-181">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="529d1-182">指定された Ws-reliablemessaging シーケンスまたは逆方向シーケンスを使用して相関関係のペアの全体で R2102:A 1 つのバージョンの Ws-addressing を使用する必要があります、`wsrm:Offer`メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="529d1-182">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="529d1-183">SOAP によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="529d1-183">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-184"> では、WS-ReliableMessaging で SOAP 1.1 と SOAP 1.2 の両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="529d1-184"> supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="529d1-185">WS-Security と WS-SecureConversation によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="529d1-185">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-186"> は、セキュリティで保護されたトランスポート (HTTPS)、WS-Security によるコンポジション、および WS-SecureConversation によるコンポジションを使用して、WS-ReliableMessaging シーケンスを保護します。</span><span class="sxs-lookup"><span data-stu-id="529d1-186"> provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="529d1-187">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-187">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="529d1-188">R2301: 個々 のメッセージの整合性だけでなく、Ws-reliablemessaging シーケンスの整合性と機密性を保護するために[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Ws-secureconversation を使用する必要がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-188">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="529d1-189">R2302:AWS-Ws-reliablemessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-189">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="529d1-190">R2303 : WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-190">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="529d1-191">B2304:WS-信頼できるメッセージのシーケンスまたは相関逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。</span><span class="sxs-lookup"><span data-stu-id="529d1-191">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="529d1-192">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ソースは、`wsse:SecurityTokenReference` メッセージの要素拡張セクションに、`CreateSequence` 要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-192">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="529d1-193">Ws-secure Conversation と共に構成 R2305:When、`CreateSequence`メッセージを含める必要があります、`wsse:SecurityTokenReference`要素。</span><span class="sxs-lookup"><span data-stu-id="529d1-193">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="529d1-194">WS-ReliableMessaging の WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="529d1-194">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-195"> は、WS-ReliableMessaging の `wsrm:RMAssertion` WS-Policy アサーションを使用して、エンドポイントの機能を記述します。</span><span class="sxs-lookup"><span data-stu-id="529d1-195"> uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="529d1-196">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-196">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="529d1-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsrm:RMAssertion` WS-Policy アサーションを `wsdl:binding` 要素にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="529d1-197">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-198"> は、`wsdl:binding` 要素および `wsdl:port` 要素へのアタッチをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="529d1-198"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="529d1-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Ws-reliablemessaging アサーションの以下の省略可能なプロパティをサポートし、上に制御を提供、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="529d1-199">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="529d1-200">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-200">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="529d1-201">WS-ReliableMessaging のフロー制御拡張</span><span class="sxs-lookup"><span data-stu-id="529d1-201">Flow Control WS-Reliable Messaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-202"> は、WS-Reliable Messaging の機能拡張を使用して、シーケンス メッセージ フローのさらに厳密な制御を実現します。</span><span class="sxs-lookup"><span data-stu-id="529d1-202"> uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="529d1-203">フロー制御が有効になって、`ReliableSessionBindingElement`の`FlowControlEnabled``bool`プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="529d1-203">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="529d1-204">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-204">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="529d1-205">B4001 : 信頼できるメッセージング フロー制御を有効にした場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `netrm:BufferRemaining` ヘッダーの要素拡張に `SequenceAcknowledgement` 要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-205">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="529d1-206">B4002 : 信頼できるメッセージング フロー制御を有効にした場合、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では `netrm:BufferRemaining` 要素が `SequenceAcknowledgement` ヘッダーに存在する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="529d1-206">B4002: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="529d1-207">B4003 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`netrm:BufferRemaining` を使用して、信頼できるメッセージングの送信先がバッファーに保持できる新しいメッセージの数を示します。</span><span class="sxs-lookup"><span data-stu-id="529d1-207">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="529d1-208">B4004:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]信頼性の高いメッセージング サービスは、信頼できるメッセージング送信先アプリケーションがすぐにメッセージを受信できない場合に送信されるメッセージの数を調整します。</span><span class="sxs-lookup"><span data-stu-id="529d1-208">B4004:The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="529d1-209">信頼できるメッセージングの送信先がメッセージをバッファーに保持する場合、要素の値が 0 になります。</span><span class="sxs-lookup"><span data-stu-id="529d1-209">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="529d1-210">B4005 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、0 ～ 4096 の整数値の `netrm:BufferRemaining` を生成し、0 ～ 214748364 (`xs:int` の `maxInclusive` 値) の整数値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="529d1-210">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="529d1-211">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="529d1-211">Message Exchange Patterns</span></span>  
 <span data-ttu-id="529d1-212">ここでは、WS-ReliableMessaging をさまざまなメッセージ交換パターンに使用する際の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="529d1-212">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="529d1-213">各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。</span><span class="sxs-lookup"><span data-stu-id="529d1-213">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="529d1-214">アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。</span><span class="sxs-lookup"><span data-stu-id="529d1-214">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="529d1-215">アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="529d1-215">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="529d1-216">一方向 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="529d1-216">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="529d1-217">バインド</span><span class="sxs-lookup"><span data-stu-id="529d1-217">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-218"> は、1 つの HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="529d1-218"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-219"> は、HTTP 要求を使用して RMS から RMD にすべてのメッセージを送信し、HTTP 応答を使用して RMD から RMS にすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-219"> uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="529d1-220">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="529d1-220">CreateSequence Exchange</span></span>  
 <span data-ttu-id="529d1-221">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含まない `CreateSequence` メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-221">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="529d1-222">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="529d1-222">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="529d1-223">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequence` メッセージで `CreateSequenceResponse` 要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="529d1-223">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="529d1-224">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="529d1-224">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="529d1-225">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`CreateSequence` メッセージとエラー メッセージを除くすべてのメッセージの応答で受信確認を処理します。</span><span class="sxs-lookup"><span data-stu-id="529d1-225">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="529d1-226">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンス メッセージと `AckRequested` メッセージの両方への応答として、常にスタンドアロンの受信確認を生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-226">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="529d1-227">TerminateSequence メッセージ</span><span class="sxs-lookup"><span data-stu-id="529d1-227">TerminateSequence message</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-228"> は、`TerminateSequence` を一方向操作として処理します。つまり、HTTP 応答には、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="529d1-228"> treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="529d1-229">一方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="529d1-229">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="529d1-230">バインド</span><span class="sxs-lookup"><span data-stu-id="529d1-230">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-231"> は、受信用 HTTP チャネルと送信用 HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="529d1-231"> provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-232"> は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-232"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="529d1-233">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="529d1-233">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="529d1-234">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="529d1-234">CreateSequence Exchange</span></span>  
 <span data-ttu-id="529d1-235">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含まない `CreateSequence` メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-235">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="529d1-236">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="529d1-236">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="529d1-237">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequenceResponse` エンドポイント参照によってアドレス指定された HTTP 要求で `ReplyTo` メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-237">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="529d1-238">双方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="529d1-238">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="529d1-239">バインド</span><span class="sxs-lookup"><span data-stu-id="529d1-239">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-240"> は、受信用 HTTP チャネルと送信用 HTTP チャネルで 2 つのシーケンスを使用して、完全に非同期の双方向メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="529d1-240"> provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-241"> は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-241"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="529d1-242">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="529d1-242">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="529d1-243">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="529d1-243">CreateSequence Exchange</span></span>  
 <span data-ttu-id="529d1-244">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含む `CreateSequence` メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-244">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="529d1-245">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="529d1-245">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-246"> は、`CreateSequenceResponse` の `CreateSequence` エンドポイント参照にアドレス指定された HTTP 要求で `ReplyTo` を送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-246"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="529d1-247">シーケンスの有効期間</span><span class="sxs-lookup"><span data-stu-id="529d1-247">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-248"> は、2 つのシーケンスを 1 つの完全な双方向セッションとして処理します。</span><span class="sxs-lookup"><span data-stu-id="529d1-248"> treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="529d1-249">一方のシーケンスをフォールトするエラーが生成されると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、リモート エンドポイントに両方のシーケンスをフォールトするよう要求します。</span><span class="sxs-lookup"><span data-stu-id="529d1-249">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="529d1-250">一方のシーケンスをフォールトするエラーを読み取ると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は両方のシーケンスをフォールトします。</span><span class="sxs-lookup"><span data-stu-id="529d1-250">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-251"> は、送信シーケンスを終了し、受信シーケンスで引き続きメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="529d1-251"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="529d1-252">逆に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信シーケンスの終了を処理し、送信シーケンスで引き続きメッセージを送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="529d1-252">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="529d1-253">要求/応答 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="529d1-253">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="529d1-254">バインド</span><span class="sxs-lookup"><span data-stu-id="529d1-254">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-255"> は、1 つの HTTP チャネルで 2 つのシーケンスを使用して、一方向の要求/応答メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="529d1-255"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-256"> は、HTTP 要求を使用して要求シーケンスのメッセージを送信し、HTTP 応答を使用して応答シーケンスのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-256"> uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="529d1-257">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="529d1-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="529d1-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含む `CreateSequence` メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="529d1-259">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="529d1-259">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="529d1-260">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequence` メッセージで `CreateSequenceResponse` 要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="529d1-260">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="529d1-261">一方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="529d1-261">One-way Message</span></span>  
 <span data-ttu-id="529d1-262">一方向メッセージ交換プロトコルを正常に完了するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答でスタンドアロンの `SequenceAcknowledgement` メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-262">To complete a one-way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="529d1-263">`SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-263">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="529d1-264">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードで要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="529d1-264">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="529d1-265">双方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="529d1-265">Two Way Messages</span></span>  
 <span data-ttu-id="529d1-266">双方向メッセージ交換プロトコルを正常に完了するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-266">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="529d1-267">応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d1-267">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="529d1-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードで要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="529d1-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="529d1-269">一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。</span><span class="sxs-lookup"><span data-stu-id="529d1-269">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="529d1-270">応答の再試行</span><span class="sxs-lookup"><span data-stu-id="529d1-270">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-271"> は、双方向メッセージ交換プロトコルの相関関係について、HTTP 要求/応答の相関関係に依存しています。</span><span class="sxs-lookup"><span data-stu-id="529d1-271"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="529d1-272">このため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、要求シーケンス メッセージが受信確認されたときではなく、HTTP 応答によって受信確認、ユーザー メッセージ、またはエラーが送信されたときに、要求シーケンス メッセージの再試行を停止します。</span><span class="sxs-lookup"><span data-stu-id="529d1-272">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="529d1-273">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答が関連付けられている要求の HTTP 要求レッグで応答を再試行します。</span><span class="sxs-lookup"><span data-stu-id="529d1-273">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="529d1-274">LastMessage の交換</span><span class="sxs-lookup"><span data-stu-id="529d1-274">LastMessage Exchange</span></span>  
 <span data-ttu-id="529d1-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求レッグで空の本文の最後のメッセージを生成し、送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-276"> は応答を要求しますが、実際の応答メッセージは無視します。</span><span class="sxs-lookup"><span data-stu-id="529d1-276"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="529d1-277">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答シーケンスの空の本文の最後のメッセージで、要求シーケンスの空の本文の最後のメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="529d1-277">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="529d1-278">アクション URI が http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage ではない最後のメッセージを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーが受信した場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は最後のメッセージで応答します。</span><span class="sxs-lookup"><span data-stu-id="529d1-278">If the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] replies with a last message.</span></span> <span data-ttu-id="529d1-279">双方向メッセージ交換プロトコルの場合、最後のメッセージでアプリケーション メッセージが送信されます。一方向メッセージ交換プロトコルの場合、最後のメッセージは空です。</span><span class="sxs-lookup"><span data-stu-id="529d1-279">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="529d1-280">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答シーケンスの空の本文の最後のメッセージに対する受信確認を要求しません。</span><span class="sxs-lookup"><span data-stu-id="529d1-280">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="529d1-281">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="529d1-281">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="529d1-282">すべての要求が有効な応答を受信すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求レッグで要求シーケンスの `TerminateSequence` メッセージを生成し、送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-282">When all requests have received a valid reply, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-283"> は応答を要求しますが、実際の応答メッセージは無視します。</span><span class="sxs-lookup"><span data-stu-id="529d1-283"> requires a response but ignores the actual response message.</span></span> <span data-ttu-id="529d1-284">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答シーケンスの `TerminateSequence` メッセージで、要求シーケンスの `TerminateSequence` メッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="529d1-284">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="529d1-285">通常のシャットダウン シーケンスでは、両方の `TerminateSequence` メッセージで完全な `SequenceAcknowledgement` を送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-285">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="529d1-286">要求/応答 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="529d1-286">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="529d1-287">バインド</span><span class="sxs-lookup"><span data-stu-id="529d1-287">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-288"> は、受信用 HTTP チャネルと送信用 HTTP チャネルで 2 つのシーケンスを使用して、要求/応答メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="529d1-288"> provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-289"> は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-289"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="529d1-290">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="529d1-290">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="529d1-291">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="529d1-291">CreateSequence Exchange</span></span>  
 <span data-ttu-id="529d1-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含む `CreateSequence` メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="529d1-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="529d1-293">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="529d1-293">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d1-294"> は、`CreateSequenceResponse` の `CreateSequence` エンドポイント参照にアドレス指定された HTTP 要求で `ReplyTo` を送信します。</span><span class="sxs-lookup"><span data-stu-id="529d1-294"> sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="529d1-295">要求/応答の相関関係</span><span class="sxs-lookup"><span data-stu-id="529d1-295">Request/Reply Correlation</span></span>  
 <span data-ttu-id="529d1-296">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、すべてのアプリケーション要求メッセージに `MessageId` と `ReplyTo` エンドポイント参照が保持されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="529d1-296">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="529d1-297">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、各アプリケーション要求メッセージで、`CreateSequence` メッセージの `ReplyTo` エンドポイント参照を適用します。</span><span class="sxs-lookup"><span data-stu-id="529d1-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="529d1-298">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、受信要求メッセージに `MessageId` と `ReplyTo` が保持されていることを要求します。</span><span class="sxs-lookup"><span data-stu-id="529d1-298">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="529d1-299">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequence` とすべてのアプリケーション要求メッセージのエンドポイント参照の URI が同一であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="529d1-299">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
