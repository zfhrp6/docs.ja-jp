---
title: 信頼できるメッセージング プロトコル バージョン 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: f45a0d5e50e9ab8a07a203d2c40ad36ef298a40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497053"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="55575-102">信頼できるメッセージング プロトコル バージョン 1.0</span><span class="sxs-lookup"><span data-stu-id="55575-102">Reliable Messaging Protocol version 1.0</span></span>
<span data-ttu-id="55575-103">このトピックでは、Windows Communication Foundation (WCF) の実装の詳細を説明 Ws-reliable メッセージングの 2005 年 2 月 (バージョン 1.0) プロトコル、HTTP トランスポートを使用して相互運用のために必要です。</span><span class="sxs-lookup"><span data-stu-id="55575-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="55575-104">WCF では、制約とこのトピックで説明されている説明 Ws-reliablemessaging 仕様に従います。</span><span class="sxs-lookup"><span data-stu-id="55575-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="55575-105">WS-ReliableMessaging バージョン 1.0 プロトコルは、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 以降に実装されています。</span><span class="sxs-lookup"><span data-stu-id="55575-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].</span></span>  
  
 <span data-ttu-id="55575-106">Ws-reliablemessaging 2005 年 2 月で WCF でプロトコルが実装されている、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>です。</span><span class="sxs-lookup"><span data-stu-id="55575-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="55575-107">便宜上、ここでは次のロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="55575-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="55575-108">イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント</span><span class="sxs-lookup"><span data-stu-id="55575-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>  
  
-   <span data-ttu-id="55575-109">レスポンダー : イニシエーターの要求を受け取るサービス</span><span class="sxs-lookup"><span data-stu-id="55575-109">Responder: the service that receives the initiator's requests</span></span>  
  
 <span data-ttu-id="55575-110">このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="55575-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="55575-111">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="55575-111">Prefix</span></span>|<span data-ttu-id="55575-112">名前空間</span><span class="sxs-lookup"><span data-stu-id="55575-112">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="55575-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="55575-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|<span data-ttu-id="55575-114">netrm</span><span class="sxs-lookup"><span data-stu-id="55575-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="55575-115">s</span><span class="sxs-lookup"><span data-stu-id="55575-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="55575-116">wsa</span><span class="sxs-lookup"><span data-stu-id="55575-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="55575-117">wsse</span><span class="sxs-lookup"><span data-stu-id="55575-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a><span data-ttu-id="55575-118">メッセージング</span><span class="sxs-lookup"><span data-stu-id="55575-118">Messaging</span></span>  
  
### <a name="sequence-establishment-messages"></a><span data-ttu-id="55575-119">シーケンス確立メッセージ</span><span class="sxs-lookup"><span data-stu-id="55575-119">Sequence Establishment Messages</span></span>  
 <span data-ttu-id="55575-120">WCF 実装`CreateSequence`と`CreateSequenceResponse`信頼性の高いメッセージ シーケンスを確立するためにメッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="55575-121">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="55575-121">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="55575-122">B1101: WCF イニシエーターはのオプションの Expires 要素を生成しません、`CreateSequence`メッセージまたはの場合と、`CreateSequence`メッセージが含まれています、`Offer`要素、省略可能な`Expires`内の要素、`Offer`要素。</span><span class="sxs-lookup"><span data-stu-id="55575-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>  
  
-   <span data-ttu-id="55575-123">B1102: にアクセスするとき、`CreateSequence`メッセージ、WCF`Responder`を送信および受信両方`Expires`要素が、存在しますが、値を使用しない場合。</span><span class="sxs-lookup"><span data-stu-id="55575-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>  
  
 <span data-ttu-id="55575-124">WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構が導入されています。</span><span class="sxs-lookup"><span data-stu-id="55575-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="55575-125">R1103 : `CreateSequence` に `Offer` 要素が含まれている場合、Reliable メッセージング レスポンダーは、シーケンスを受け入れ、`CreateSequenceResponse` 要素を含む `wsrm:Accept` で応答して、相関する 2 つの逆方向シーケンスを形成するか、`CreateSequence` 要求を拒否する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>  
  
-   <span data-ttu-id="55575-126">R1104 : 逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="55575-127">R1105 : `AcksTo` の `ReplyTo` エンドポイント参照と `CreateSequence` エンドポイント参照には、オクテット単位で一致するアドレス値が必要です。</span><span class="sxs-lookup"><span data-stu-id="55575-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>  
  
     <span data-ttu-id="55575-128">WCF 応答側であることを確認の URI 部分、`AcksTo`と`ReplyTo`Epr がシーケンスを作成する前に、と同じです。</span><span class="sxs-lookup"><span data-stu-id="55575-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="55575-129">R1106 : `AcksTo` の `ReplyTo` および `CreateSequence` の各エンドポイント参照は、参照パラメーターの同じセットを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>  
  
     <span data-ttu-id="55575-130">WCF は強制しませんが、想定の [参照パラメーター]`AcksTo`と`ReplyTo`で`CreateSequence`は同一からの参照パラメーターを使用して`ReplyTo`受信確認と逆方向シーケンス メッセージのエンドポイント参照します。</span><span class="sxs-lookup"><span data-stu-id="55575-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="55575-131">R1107 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="55575-132">R1108 : Offer 機構を使用して 2 つの逆方向シーケンスを確立した場合、`[address]` の `wsrm:AcksTo` 要素の `wsrm:Accept` エンドポイント参照子要素の `CreateSequenceResponse` プロパティは、`CreateSequence` の送信先 URI とバイト単位で一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>  
  
-   <span data-ttu-id="55575-133">R1109 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、イニシエーターによって送信されたメッセージとレスポンダーによるメッセージの受信確認は、同じエンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>  
  
     <span data-ttu-id="55575-134">Ws-reliable メッセージングを使用して、イニシエーターとレスポンダー間で信頼できるセッションを確立するために WCF です。</span><span class="sxs-lookup"><span data-stu-id="55575-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="55575-135">WCF の Ws-reliablemessaging 実装は、信頼できるセッションが一方向、要求/応答、双方向メッセージ パターンです。</span><span class="sxs-lookup"><span data-stu-id="55575-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="55575-136">Ws-reliable メッセージング`Offer`機構で`CreateSequence` / `CreateSequenceResponse` 2 つの相関関係を持つ逆方向シーケンスを確立することができ、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。</span><span class="sxs-lookup"><span data-stu-id="55575-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="55575-137">WCF では、セッションのセッションの整合性をエンド ツー エンドの保護などのセキュリティ保証を提供するために現実的では、同じパーティを対象とするメッセージが同じ送信先に到着することを確認します。</span><span class="sxs-lookup"><span data-stu-id="55575-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="55575-138">また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="55575-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="55575-139">そのため、制約 R1104、R1105、および R1108 は、WCF に適用されます。</span><span class="sxs-lookup"><span data-stu-id="55575-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>  
  
 <span data-ttu-id="55575-140">`CreateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55575-140">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="55575-141">`CreateSequenceResponse` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55575-141">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="sequence"></a><span data-ttu-id="55575-142">シーケンス</span><span class="sxs-lookup"><span data-stu-id="55575-142">Sequence</span></span>  
 <span data-ttu-id="55575-143">シーケンスに適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="55575-143">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="55575-144">B1201:WCF を生成し、アクセス シーケンス番号より`xs:long`の最大包括値、9223372036854775807 します。</span><span class="sxs-lookup"><span data-stu-id="55575-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
-   <span data-ttu-id="55575-145">B1202:WCF が常にアクション URI を空の本文の最終メッセージを生成のhttp://schemas.xmlsoap.org/ws/2005/02/rm/LastMessageします。</span><span class="sxs-lookup"><span data-stu-id="55575-145">B1202:WCF always generates an empty-bodied last message with the action URI of http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
-   <span data-ttu-id="55575-146">B1203: WCF を受け取りを含むシーケンス ヘッダーを持つメッセージを配信する`LastMessage`要素のアクション URI がない限りhttp://schemas.xmlsoap.org/ws/2005/02/rm/LastMessageです。</span><span class="sxs-lookup"><span data-stu-id="55575-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.</span></span>  
  
 <span data-ttu-id="55575-147">シーケンス ヘッダーのサンプル</span><span class="sxs-lookup"><span data-stu-id="55575-147">An example of a Sequence Header.</span></span>  
  
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
  
### <a name="ackrequested-header"></a><span data-ttu-id="55575-148">AckRequested ヘッダー</span><span class="sxs-lookup"><span data-stu-id="55575-148">AckRequested Header</span></span>  
 <span data-ttu-id="55575-149">WCF を使用して`AckRequested`keep-alive 機構としてヘッダー。</span><span class="sxs-lookup"><span data-stu-id="55575-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="55575-150">WCF は、省略可能なは生成されません`MessageNumber`要素。</span><span class="sxs-lookup"><span data-stu-id="55575-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="55575-151">メッセージを受信したときに、`AckRequested`ヘッダーが含まれていますが、`MessageNumber`要素、WCF は無視されます、`MessageNumber`要素の値を次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="55575-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="55575-152">SequenceAcknowledgement ヘッダー</span><span class="sxs-lookup"><span data-stu-id="55575-152">SequenceAcknowledgement Header</span></span>  
 <span data-ttu-id="55575-153">WCF では、Ws-reliablemessaging で提供されるシーケンス受信確認の抱き合わせ機構を使用します。</span><span class="sxs-lookup"><span data-stu-id="55575-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="55575-154">R1401 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、目的の受信者に送信されるアプリケーション メッセージに、`SequenceAcknowledgement` ヘッダーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="55575-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>  
  
-   <span data-ttu-id="55575-155">B1402: と WCF は、シーケンス メッセージを受信する前に受信確認を生成する必要があります (例についてを満たすために、`AckRequested`メッセージ)、WCF は生成、`SequenceAcknowledgement`次の例のように、範囲 0-0 を含むヘッダーをします。</span><span class="sxs-lookup"><span data-stu-id="55575-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="55575-156">B1403: WCF を生成しません`SequenceAcknowledgement`ヘッダーを含む、`Nack`要素がサポートしている`Nack`要素。</span><span class="sxs-lookup"><span data-stu-id="55575-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="55575-157">WS-ReliableMessaging エラー</span><span class="sxs-lookup"><span data-stu-id="55575-157">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="55575-158">Ws-reliablemessaging エラーの WCF 実装に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55575-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>  
  
-   <span data-ttu-id="55575-159">B1501: WCF を生成しません`MessageNumberRollover`エラーです。</span><span class="sxs-lookup"><span data-stu-id="55575-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="55575-160">B1502:WCF エンドポイントが生成できる`CreateSequenceRefused`仕様」の説明に従ってエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="55575-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>  
  
-   <span data-ttu-id="55575-161">WCF は、追加生成 B1503:When サービス エンドポイント、接続の上限に達するし、新しい接続を処理することはできません、`CreateSequenceRefused`エラー サブコード`netrm:ConnectionLimitReached`次の例で示すように、します。</span><span class="sxs-lookup"><span data-stu-id="55575-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="55575-162">WS-Addressing エラー</span><span class="sxs-lookup"><span data-stu-id="55575-162">WS-Addressing Faults</span></span>  
 <span data-ttu-id="55575-163">Ws-reliablemessaging は Ws-addressing が使用するため、WCF Ws-reliablemessaging 実装は、Ws-addressing エラーを生成可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55575-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="55575-164">このセクションでは、WCF は、Ws-reliablemessaging レイヤーで明示的に生成する Ws-addressing エラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="55575-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>  
  
-   <span data-ttu-id="55575-165">B1601:WCF では、次のいずれかが true の場合、メッセージのアドレス指定ヘッダーに必要なエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="55575-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="55575-166">メッセージに `Sequence` ヘッダーと `Action` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="55575-166">A message is missing a `Sequence` header and an `Action` header.</span></span>  
  
    -   <span data-ttu-id="55575-167">`CreateSequence` メッセージに `MessageId` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="55575-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="55575-168">`CreateSequence` メッセージに `ReplyTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="55575-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>  
  
-   <span data-ttu-id="55575-169">B1602:WCF アクションがサポートされていませんエラーを返信で欠落しているメッセージを生成する、`Sequence`ヘッダーがあり、`Action`が Ws-reliablemessaging 仕様で認識されないヘッダー。</span><span class="sxs-lookup"><span data-stu-id="55575-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>  
  
-   <span data-ttu-id="55575-170">B1603:WCF がエラーをエンドポイントの検査に基づいて、シーケンスが処理されませんを示すために使用できないエンドポイントを生成、`CreateSequence`メッセージのアドレス指定ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="55575-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="55575-171">プロトコル コンポジション</span><span class="sxs-lookup"><span data-stu-id="55575-171">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="55575-172">WS-Addressing によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="55575-172">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="55575-173">WCF は Ws-addressing の 2 つのバージョンをサポートしています: Ws-addressing 2004/08 [WS-ADDR] と W3C Ws-addressing 1.0 に関する推奨事項 [WS ADDR コア] と [WS ADDR SOAP] です。</span><span class="sxs-lookup"><span data-stu-id="55575-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="55575-174">WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="55575-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="55575-175">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55575-175">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="55575-176">R2101: 両方 Ws-addressing 2004/08 と Ws-addressing 1.0 は、Ws-reliablemessaging で使用できます。</span><span class="sxs-lookup"><span data-stu-id="55575-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="55575-177">指定された Ws-reliablemessaging シーケンスまたは逆方向シーケンスを使用して相関関係のペアの全体で R2102:A 1 つのバージョンの Ws-addressing を使用する必要があります、`wsrm:Offer`メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="55575-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="55575-178">SOAP によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="55575-178">Composition with SOAP</span></span>  
 <span data-ttu-id="55575-179">WCF には、SOAP 1.1 と Ws-reliablemessaging で SOAP 1.2 の両方の使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="55575-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="55575-180">WS-Security と WS-SecureConversation によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="55575-180">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="55575-181">WCF は、Ws-secure Conversation をセキュリティで保護されたトランスポート (HTTPS)、Ws-security によるコンポジション、コンポジションを使用して、Ws-reliablemessaging シーケンスの保護を提供します。</span><span class="sxs-lookup"><span data-stu-id="55575-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="55575-182">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55575-182">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="55575-183">R2301: 個々 のメッセージの整合性だけでなく、Ws-reliablemessaging シーケンスの整合性と機密性を保護するために WCF に必要な Ws-secureconversation を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="55575-184">R2302:AWS-Ws-reliablemessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>  
  
-   <span data-ttu-id="55575-185">R2303 : WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="55575-186">B2304:WS-信頼できるメッセージのシーケンスまたは相関逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。</span><span class="sxs-lookup"><span data-stu-id="55575-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
     <span data-ttu-id="55575-187">WCF のソース生成、`wsse:SecurityTokenReference`の要素拡張セクション内の要素、`CreateSequence`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="55575-188">Ws-secure Conversation と共に構成 R2305:When、`CreateSequence`メッセージを含める必要があります、`wsse:SecurityTokenReference`要素。</span><span class="sxs-lookup"><span data-stu-id="55575-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="55575-189">WS-ReliableMessaging の WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="55575-189">WS-Reliable Messaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="55575-190">Ws-reliable メッセージングの Ws-policy アサーションを使用する WCF`wsrm:RMAssertion`エンドポイントの機能を記述します。</span><span class="sxs-lookup"><span data-stu-id="55575-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="55575-191">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55575-191">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="55575-192">B3001: WCF アタッチ`wsrm:RMAssertion`Ws-policy アサーションを`wsdl:binding`要素。</span><span class="sxs-lookup"><span data-stu-id="55575-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="55575-193">WCF へのアタッチをサポートしている`wsdl:binding`と`wsdl:port`要素。</span><span class="sxs-lookup"><span data-stu-id="55575-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="55575-194">B3002: WCF は Ws-reliablemessaging アサーションの以下の省略可能なプロパティをサポートし、WCF でそれらの制御を提供`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="55575-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     <span data-ttu-id="55575-195">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="55575-195">The following is an example.</span></span>  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="55575-196">WS-ReliableMessaging のフロー制御拡張</span><span class="sxs-lookup"><span data-stu-id="55575-196">Flow Control WS-Reliable Messaging Extension</span></span>  
 <span data-ttu-id="55575-197">WCF では、Ws-reliable Messaging の機能拡張を使用して、追加のオプションの厳密な制御をシーケンス メッセージ フローを提供します。</span><span class="sxs-lookup"><span data-stu-id="55575-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="55575-198">フロー制御が有効になって、`ReliableSessionBindingElement`の`FlowControlEnabled``bool`プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="55575-198">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``bool` property to `true`.</span></span> <span data-ttu-id="55575-199">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55575-199">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="55575-200">B4001: 信頼できるメッセージング フロー制御を有効にすると、WCF の生成、`netrm:BufferRemaining`内の要素拡張の要素、`SequenceAcknowledgement`ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="55575-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="55575-201">B4002: 信頼できるメッセージング フロー制御を有効にすると、WCF しないため、`netrm:BufferRemaining`に存在する要素`SequenceAcknowledgement`ヘッダーを次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="55575-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="55575-202">B4003: WCF を使用して`netrm:BufferRemaining`新しいメッセージの数、信頼できるメッセージの送信先を示すためのバッファーに格納できます。</span><span class="sxs-lookup"><span data-stu-id="55575-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>  
  
-   <span data-ttu-id="55575-203">B4004: 信頼できるメッセージングを WCF サービスが、信頼できるメッセージング送信先アプリケーションがすぐにメッセージを受信できない場合に送信されるメッセージの数を調整します。</span><span class="sxs-lookup"><span data-stu-id="55575-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="55575-204">信頼できるメッセージングの送信先がメッセージをバッファーに保持する場合、要素の値が 0 になります。</span><span class="sxs-lookup"><span data-stu-id="55575-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>  
  
-   <span data-ttu-id="55575-205">B4005: WCF 生成`netrm:BufferRemaining`整数、0 ~ 4096 の範囲、範囲値を 0 との間の整数値を読み取りますと`xs:int`の`maxInclusive`214748364 の値します。</span><span class="sxs-lookup"><span data-stu-id="55575-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="55575-206">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="55575-206">Message Exchange Patterns</span></span>  
 <span data-ttu-id="55575-207">Ws-reliable メッセージングは、さまざまなメッセージ交換パターンを使用する場合は、WCF の動作を説明します。</span><span class="sxs-lookup"><span data-stu-id="55575-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="55575-208">各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。</span><span class="sxs-lookup"><span data-stu-id="55575-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="55575-209">アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。</span><span class="sxs-lookup"><span data-stu-id="55575-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="55575-210">アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="55575-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="55575-211">一方向 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="55575-211">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="55575-212">バインド</span><span class="sxs-lookup"><span data-stu-id="55575-212">Binding</span></span>  
 <span data-ttu-id="55575-213">WCF には、1 つの HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="55575-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="55575-214">WCF では、HTTP 要求を使用して RMD から RMS へのすべてのメッセージを送信し、HTTP 応答に、RMS からのすべてメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="55575-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="55575-215">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="55575-215">CreateSequence Exchange</span></span>  
 <span data-ttu-id="55575-216">WCF のイニシエーターを生成、`CreateSequence`オファーを含まないメッセージです。</span><span class="sxs-lookup"><span data-stu-id="55575-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="55575-217">WCF レスポンダーは、`CreateSequence`シーケンスを作成する前にオファーがありません。</span><span class="sxs-lookup"><span data-stu-id="55575-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="55575-218">WCF 応答側に返信すると、`CreateSequence`要求、`CreateSequenceResponse`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="55575-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="55575-219">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="55575-220">WCF のイニシエーターを除くすべてのメッセージの返信の受信確認の処理、`CreateSequence`メッセージとエラー メッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="55575-221">WCF レスポンダーは常に両方のシーケンスへの応答でスタンドアロンの受信確認を生成し、`AckRequested`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>  
  
#### <a name="terminatesequence-message"></a><span data-ttu-id="55575-222">TerminateSequence メッセージ</span><span class="sxs-lookup"><span data-stu-id="55575-222">TerminateSequence message</span></span>  
 <span data-ttu-id="55575-223">WCF の扱い`TerminateSequence`一方向の操作、つまり、HTTP 応答が空の本文と HTTP 202 ステータス コード。</span><span class="sxs-lookup"><span data-stu-id="55575-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="55575-224">一方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="55575-224">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="55575-225">バインド</span><span class="sxs-lookup"><span data-stu-id="55575-225">Binding</span></span>  
 <span data-ttu-id="55575-226">WCF には、1 つのシーケンスでは、受信、送信用 Http チャネルとを使用して、一方向メッセージ交換パターンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="55575-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="55575-227">WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="55575-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="55575-228">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="55575-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="55575-229">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="55575-229">CreateSequence Exchange</span></span>  
 <span data-ttu-id="55575-230">WCF のイニシエーターを生成、`CreateSequence`オファーを含まないメッセージです。</span><span class="sxs-lookup"><span data-stu-id="55575-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="55575-231">WCF レスポンダーは、確実、`CreateSequence`シーケンスを作成する前にオファーがありません。</span><span class="sxs-lookup"><span data-stu-id="55575-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="55575-232">WCF 応答側の送信、`CreateSequenceResponse`メッセージ、HTTP 要求で対処するための`ReplyTo`エンドポイント参照します。</span><span class="sxs-lookup"><span data-stu-id="55575-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="55575-233">双方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="55575-233">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="55575-234">バインド</span><span class="sxs-lookup"><span data-stu-id="55575-234">Binding</span></span>  
 <span data-ttu-id="55575-235">WCF には、受信と送信の HTTP チャネルで 2 つのシーケンスを使用して、完全に非同期の双方向メッセージ交換パターンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="55575-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="55575-236">WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="55575-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="55575-237">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="55575-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="55575-238">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="55575-238">CreateSequence Exchange</span></span>  
 <span data-ttu-id="55575-239">WCF のイニシエーターを生成、`CreateSequence`メッセージに提供します。</span><span class="sxs-lookup"><span data-stu-id="55575-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="55575-240">WCF レスポンダーは、確実、`CreateSequence`シーケンスを作成する前に、プランがします。</span><span class="sxs-lookup"><span data-stu-id="55575-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="55575-241">WCF が送信、`CreateSequenceResponse`にアドレス指定された HTTP 要求で、`CreateSequence`の`ReplyTo`エンドポイント参照します。</span><span class="sxs-lookup"><span data-stu-id="55575-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="55575-242">シーケンスの有効期間</span><span class="sxs-lookup"><span data-stu-id="55575-242">Sequence Lifetime</span></span>  
 <span data-ttu-id="55575-243">WCF は、2 つのシーケンスを 1 つの完全な双方向セッションとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="55575-243">WCF treats the two sequences as one fully duplex session.</span></span>  
  
 <span data-ttu-id="55575-244">1 つのシーケンスをフォールトするエラーの生成時に、WCF には、リモート エンドポイントに両方のシーケンスをフォールトするが期待しています。</span><span class="sxs-lookup"><span data-stu-id="55575-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="55575-245">1 つのシーケンスをフォールトするエラーを読み取り、時に WCF フォールトの両方のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="55575-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="55575-246">WCF は、送信シーケンスを閉じるし、受信シーケンスでメッセージの処理を継続することができます。</span><span class="sxs-lookup"><span data-stu-id="55575-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="55575-247">反対に、WCF は、受信シーケンスの終了を処理し、送信シーケンスでメッセージを送信し続けます。</span><span class="sxs-lookup"><span data-stu-id="55575-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="55575-248">要求/応答 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="55575-248">Request-Reply, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="55575-249">バインド</span><span class="sxs-lookup"><span data-stu-id="55575-249">Binding</span></span>  
 <span data-ttu-id="55575-250">WCF は、一方向および要求/応答メッセージ交換パターンを使用して 2 つの 1 つの HTTP チャネルのシーケンスします。</span><span class="sxs-lookup"><span data-stu-id="55575-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="55575-251">WCF では、HTTP 要求を使用して、要求シーケンスのメッセージを送信して、HTTP 応答を使用して、応答シーケンスのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="55575-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="55575-252">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="55575-252">CreateSequence Exchange</span></span>  
 <span data-ttu-id="55575-253">WCF のイニシエーターを生成、`CreateSequence`メッセージに提供します。</span><span class="sxs-lookup"><span data-stu-id="55575-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="55575-254">WCF レスポンダーは、確実、`CreateSequence`シーケンスを作成する前に、プランがします。</span><span class="sxs-lookup"><span data-stu-id="55575-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="55575-255">WCF 応答側に返信すると、`CreateSequence`要求、`CreateSequenceResponse`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="55575-256">一方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="55575-256">One-way Message</span></span>  
 <span data-ttu-id="55575-257">一方向メッセージ交換プロトコルを正常に完了するには、WCF 発信側は、HTTP 要求で要求シーケンス メッセージを送信し、受信スタンドアロン`SequenceAcknowledgement`HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="55575-258">`SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="55575-259">WCF レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードを含む応答を伴う要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="55575-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="55575-260">双方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="55575-260">Two Way Messages</span></span>  
 <span data-ttu-id="55575-261">双方向メッセージ交換プロトコルを正常に完了するは、WCF イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="55575-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="55575-262">応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55575-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="55575-263">WCF レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードを含む応答を伴う要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="55575-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="55575-264">一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。</span><span class="sxs-lookup"><span data-stu-id="55575-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="55575-265">応答の再試行</span><span class="sxs-lookup"><span data-stu-id="55575-265">Retrying Replies</span></span>  
 <span data-ttu-id="55575-266">WCF は、双方向メッセージ交換プロトコルの相関関係の HTTP 要求-応答の相関関係に依存します。</span><span class="sxs-lookup"><span data-stu-id="55575-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="55575-267">このため、WCF のイニシエーターは停止しません、要求シーケンス メッセージが受信確認が、HTTP 応答によって受信確認、ユーザー メッセージ、または障害時ではなく、要求シーケンス メッセージを再試行しています。</span><span class="sxs-lookup"><span data-stu-id="55575-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="55575-268">WCF レスポンダーは、応答が関連付けられている要求の HTTP 要求レッグで応答を再試行します。</span><span class="sxs-lookup"><span data-stu-id="55575-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>  
  
#### <a name="lastmessage-exchange"></a><span data-ttu-id="55575-269">LastMessage の交換</span><span class="sxs-lookup"><span data-stu-id="55575-269">LastMessage Exchange</span></span>  
 <span data-ttu-id="55575-270">WCF イニシエーターは、生成し、HTTP 要求レッグで空の本文最終メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="55575-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="55575-271">WCF では、応答が必要ですが、実際の応答メッセージは無視されます。</span><span class="sxs-lookup"><span data-stu-id="55575-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="55575-272">WCF レスポンダーは、要求シーケンスの空の本文最後のメッセージに応答シーケンスの空の本文最後のメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="55575-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>  
  
 <span data-ttu-id="55575-273">WCF 応答側がアクション URI がでない最後のメッセージを受け取った場合http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage、最後のメッセージを WCF 添えて応答します。</span><span class="sxs-lookup"><span data-stu-id="55575-273">If the WCF Responder receives a last message in which the action URI is not http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF replies with a last message.</span></span> <span data-ttu-id="55575-274">双方向メッセージ交換プロトコルの場合、最後のメッセージでアプリケーション メッセージが送信されます。一方向メッセージ交換プロトコルの場合、最後のメッセージは空です。</span><span class="sxs-lookup"><span data-stu-id="55575-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>  
  
 <span data-ttu-id="55575-275">WCF 応答側では、応答シーケンスの空の本文最後のメッセージの受信確認は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="55575-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="55575-276">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="55575-276">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="55575-277">WCF のイニシエーターが生成し、要求シーケンスを送信するすべての要求が、有効な応答を受信したときに`TerminateSequence`HTTP 要求レッグでメッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="55575-278">WCF では、応答が必要ですが、実際の応答メッセージは無視されます。</span><span class="sxs-lookup"><span data-stu-id="55575-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="55575-279">要求シーケンスに返信すると、WCF レスポンダー`TerminateSequence`応答シーケンスのメッセージ`TerminateSequence`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="55575-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>  
  
 <span data-ttu-id="55575-280">通常のシャットダウン シーケンスでは、両方の `TerminateSequence` メッセージで完全な `SequenceAcknowledgement` を送信します。</span><span class="sxs-lookup"><span data-stu-id="55575-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="55575-281">要求/応答 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="55575-281">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="55575-282">バインド</span><span class="sxs-lookup"><span data-stu-id="55575-282">Binding</span></span>  
 <span data-ttu-id="55575-283">WCF には、2 つのシーケンスでは、受信、送信用 HTTP チャネルとを使用して要求/応答メッセージ交換パターンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="55575-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="55575-284">WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="55575-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="55575-285">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="55575-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="55575-286">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="55575-286">CreateSequence Exchange</span></span>  
 <span data-ttu-id="55575-287">WCF のイニシエーターを生成、`CreateSequence`メッセージに提供します。</span><span class="sxs-lookup"><span data-stu-id="55575-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="55575-288">WCF レスポンダーは、確実、`CreateSequence`シーケンスを作成する前に、プランがします。</span><span class="sxs-lookup"><span data-stu-id="55575-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="55575-289">WCF が送信、`CreateSequenceResponse`にアドレス指定された HTTP 要求で、`CreateSequence`の`ReplyTo`エンドポイント参照します。</span><span class="sxs-lookup"><span data-stu-id="55575-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="55575-290">要求/応答の相関関係</span><span class="sxs-lookup"><span data-stu-id="55575-290">Request/Reply Correlation</span></span>  
 <span data-ttu-id="55575-291">WCF イニシエーターにより、すべてのアプリケーション要求メッセージ下げ、`MessageId`と`ReplyTo`エンドポイント参照します。</span><span class="sxs-lookup"><span data-stu-id="55575-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="55575-292">WCF のイニシエーターが適用されます、`CreateSequence`メッセージの`ReplyTo`各アプリケーション要求メッセージのエンドポイント参照します。</span><span class="sxs-lookup"><span data-stu-id="55575-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="55575-293">WCF レスポンダーは、その受信要求メッセージが必要です、`MessageId`と`ReplyTo`です。</span><span class="sxs-lookup"><span data-stu-id="55575-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="55575-294">WCF レスポンダーは、両方のエンドポイント参照の URI を提供する、`CreateSequence`とすべてのアプリケーション要求メッセージが同一です。</span><span class="sxs-lookup"><span data-stu-id="55575-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>
