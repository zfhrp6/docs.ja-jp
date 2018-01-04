---
title: "信頼できるメッセージング プロトコル バージョン 1.1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67df8b539109d7e4dafcbc42ad7679643767021a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="9930b-102">信頼できるメッセージング プロトコル バージョン 1.1</span><span class="sxs-lookup"><span data-stu-id="9930b-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="9930b-103">ここでは、HTTP トランスポートを使用した相互運用に必要な WS-ReliableMessaging 2007/02 (バージョン 1.1) プロトコルに関する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 実装の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="9930b-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-104"> は、ここに記載した制約と説明に基づく WS-ReliableMessaging 仕様に従っています。</span><span class="sxs-lookup"><span data-stu-id="9930b-104"> follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="9930b-105">以降では、Ws-reliablemessaging 1.1 プロトコルを実装することに注意してください、[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9930b-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="9930b-106">WS-ReliableMessaging 2007/02 プロトコルは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] により <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> に実装されます。</span><span class="sxs-lookup"><span data-stu-id="9930b-106">The WS-ReliableMessaging February 2007 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="9930b-107">便宜上、ここでは次のロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="9930b-108">イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント。</span><span class="sxs-lookup"><span data-stu-id="9930b-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="9930b-109">レスポンダー : イニシエーターの要求を受け取るサービス。</span><span class="sxs-lookup"><span data-stu-id="9930b-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="9930b-110">このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="9930b-111">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="9930b-111">Prefix</span></span>|<span data-ttu-id="9930b-112">名前空間</span><span class="sxs-lookup"><span data-stu-id="9930b-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="9930b-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="9930b-113">wsrm</span></span>|<span data-ttu-id="9930b-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span><span class="sxs-lookup"><span data-stu-id="9930b-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span></span>|  
|<span data-ttu-id="9930b-115">netrm</span><span class="sxs-lookup"><span data-stu-id="9930b-115">netrm</span></span>|<span data-ttu-id="9930b-116">http://schemas.microsoft.com/ws/2006/05/rm</span><span class="sxs-lookup"><span data-stu-id="9930b-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="9930b-117">s</span><span class="sxs-lookup"><span data-stu-id="9930b-117">s</span></span>|<span data-ttu-id="9930b-118">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="9930b-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="9930b-119">wsa</span><span class="sxs-lookup"><span data-stu-id="9930b-119">wsa</span></span>|<span data-ttu-id="9930b-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="9930b-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="9930b-121">wsse</span><span class="sxs-lookup"><span data-stu-id="9930b-121">wsse</span></span>|<span data-ttu-id="9930b-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="9930b-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="9930b-123">wsrmp</span><span class="sxs-lookup"><span data-stu-id="9930b-123">wsrmp</span></span>|<span data-ttu-id="9930b-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="9930b-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="9930b-125">netrmp</span><span class="sxs-lookup"><span data-stu-id="9930b-125">netrmp</span></span>|<span data-ttu-id="9930b-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="9930b-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="9930b-127">wsp</span><span class="sxs-lookup"><span data-stu-id="9930b-127">wsp</span></span>|<span data-ttu-id="9930b-128">(WS-Policy 1.2 または WS-Policy 1.5 のいずれか)</span><span class="sxs-lookup"><span data-stu-id="9930b-128">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="9930b-129">メッセージング</span><span class="sxs-lookup"><span data-stu-id="9930b-129">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="9930b-130">シーケンスの作成</span><span class="sxs-lookup"><span data-stu-id="9930b-130">Sequence Creation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-131"> は、信頼できるメッセージ シーケンスを確立するために、`CreateSequence` メッセージと `CreateSequenceResponse` メッセージを実装します。</span><span class="sxs-lookup"><span data-stu-id="9930b-131"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="9930b-132">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9930b-132">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="9930b-133">B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`CreateSequence` メッセージの `ReplyTo`、`AcksTo`、および `Offer/Endpoint` と同じエンドポイント参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-133">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="9930b-134">R1102: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、オクテット単位で一致する同じ文字列表現のアドレス値が必要です。</span><span class="sxs-lookup"><span data-stu-id="9930b-134">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="9930b-135">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`AcksTo`、`ReplyTo`、および `Endpoint` の各エンドポイント参照の URI 部分が同一であるかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="9930b-135">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="9930b-136">R1103: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、同一の参照パラメーターのセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="9930b-136">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-137"> は、`AcksTo` の `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` エンドポイント参照の参照パラメーターが同一であることを強制しません。ただし、これらが同一であることを前提とした上で、`ReplyTo` エンドポイント参照からの参照パラメーターを受信確認と逆方向シーケンス メッセージに使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-137"> does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="9930b-138">B1104: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`Expires` メッセージでオプションの `Offer/Expires` 要素または `CreateSequence` 要素を生成しません。</span><span class="sxs-lookup"><span data-stu-id="9930b-138">B1104: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="9930b-139">B1105: `CreateSequence` メッセージにアクセスする場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`Expires` 要素の `CreateSequence` 値を `Expires` 要素の `CreateSequenceResponse` 値として使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-139">B1105: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="9930b-140">それ以外の場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは `Expires` 値および `Offer/Expires` 値を読み込んで無視します。</span><span class="sxs-lookup"><span data-stu-id="9930b-140">Otherwise, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="9930b-141">B1106: `CreateSequenceResponse` メッセージにアクセスする場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オプションの `Expires` 値を読み込みますが、使用しません。</span><span class="sxs-lookup"><span data-stu-id="9930b-141">B1106: When accessing the `CreateSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="9930b-142">B1107: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターおよびレスポンダーは、`IncompleteSequenceBehavior` 要素および `CreateSequence/Offer` 要素にオプションの `CreateSequenceResponse` 要素を必ず生成します。</span><span class="sxs-lookup"><span data-stu-id="9930b-142">B1107: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="9930b-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`DiscardFollowingFirstGap` 要素にある `NoDiscard` 値および `IncompleteSequenceBehavior` 値のみ使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="9930b-144">WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構を利用しています。</span><span class="sxs-lookup"><span data-stu-id="9930b-144">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="9930b-145">B1109: `CreateSequence` に `Offer` 要素が格納されている場合、一方向 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequenceResponse` 要素なしに `Accept` で応答することにより、用意されたシーケンスを拒否します。</span><span class="sxs-lookup"><span data-stu-id="9930b-145">B1109: If `CreateSequence` contains an `Offer` element, the one way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="9930b-146">B1110: 信頼できるメッセージング レスポンダーが用意されたシーケンスを拒否する場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは新しく確立されたシーケンスをエラーとします。</span><span class="sxs-lookup"><span data-stu-id="9930b-146">B1110: If a Reliable Messaging Responder rejects the offered sequence, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="9930b-147">B1111: `CreateSequence` に `Offer` 要素が格納されていない場合、双方向 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequenceRefused` フォールトで応答することにより用意されたシーケンスを拒否します。</span><span class="sxs-lookup"><span data-stu-id="9930b-147">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="9930b-148">R1112: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、`[address]` エンドポイント参照の `CreateSequenceResponse/Accept/AcksTo` プロパティは、バイト単位で `CreateSequence` メッセージの送信先 URI と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-148">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="9930b-149">R1113: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、イニシエーターからレスポンダーに流れる両方のシーケンスにあるすべてのメッセージは、同じエンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-149">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-150"> は、WS-ReliableMessaging を使用して、イニシエーターとレスポンダー間で信頼できるセッションを確立します。</span><span class="sxs-lookup"><span data-stu-id="9930b-150"> uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="9930b-151">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging 実装により、一方向、要求/応答、双方向の各メッセージ パターンの信頼できるセッションが実現します。</span><span class="sxs-lookup"><span data-stu-id="9930b-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="9930b-152">`Offer` および `CreateSequence` で WS-ReliableMessaging の `CreateSequenceResponse` 機構を使用すると、相関する 2 つの逆方向シーケンスを確立できます。また、Offer 機構は、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。</span><span class="sxs-lookup"><span data-stu-id="9930b-152">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="9930b-153">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、セッション整合性を保つためのエンドツーエンドの保護を含むこのようなセッションに対してセキュリティが保証されているため、同じパーティを対象とするメッセージが同じ送信先に到着することが事実上保証されます。</span><span class="sxs-lookup"><span data-stu-id="9930b-153">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="9930b-154">また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="9930b-154">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="9930b-155">R1102、R1112、および R1113 の制約に適用するため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9930b-155">Therefore, constraints R1102, R1112, and R1113 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="9930b-156">`CreateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-156">An example of a `CreateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>  
    <wsa:ReplyTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>   
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>  
      </wsrm:AcksTo>  
      <wsrm:Offer>  
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>  
        <wsrm:Endpoint>  
          <wsa:Address>http://Business456.com/clientA</wsa:Address>  
        </wsrm:Endpoint>  
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      </wsrm:Offer>  
    </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="9930b-157">`CreateSequenceResponse` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-157">An example of a `CreateSequenceResponse` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      <wsrm:Accept>  
        <wsrm:AcksTo>  
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>  
        </wsrm:AcksTo>  
      </wsrm:Accept>  
    </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="closing-a-sequence"></a><span data-ttu-id="9930b-158">シーケンスを閉じる</span><span class="sxs-lookup"><span data-stu-id="9930b-158">Closing a Sequence</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-159"> は、信頼できるメッセージの送信元が開始するシャットダウンに `CloseSequence` メッセージおよび `CloseSequenceResponse` メッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-159"> uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="9930b-160">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信先はシャットダウンを開始せず、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージング送信元は、信頼できるメッセージの送信先が開始するシャットダウンをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="9930b-160">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate shutdown and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="9930b-161">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9930b-161">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="9930b-162">B1201: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信元は、シーケンスをシャットダウンする場合に、常に `CloseSequence` メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-162">B1201: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="9930b-163">B1202: 信頼できるメッセージの送信元は、`CloseSequence` メッセージを送信する前に、すべてのシーケンス メッセージの受信確認を待機します。</span><span class="sxs-lookup"><span data-stu-id="9930b-163">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="9930b-164">B1203: 信頼できるメッセージの送信元は、シーケンスにメッセージが含まれない場合を除き、常にオプションの `LastMsgNumber` 要素を含めます。</span><span class="sxs-lookup"><span data-stu-id="9930b-164">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="9930b-165">R1204: 信頼できるメッセージの送信先は、`CloseSequence` メッセージを送信してシャットダウンを開始することはできません。</span><span class="sxs-lookup"><span data-stu-id="9930b-165">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="9930b-166">B1205: `CloseSequence` メッセージを受け取ると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信元はシーケンスが不完全と見なし、エラーを送信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-166">B1205: Upon receiving a `CloseSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="9930b-167">`CloseSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-167">An example of a `CloseSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
    </wsrm:CloseSequence>  
  </s:Body>  
</s:Envelope>  
Example CloseSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:CloseSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence-termination"></a><span data-ttu-id="9930b-168">シーケンスの終了</span><span class="sxs-lookup"><span data-stu-id="9930b-168">Sequence Termination</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-169"> は、`TerminateSequence/TerminateSequenceResponse` ハンドシェイクを完了した後、`CloseSequence/CloseSequenceResponse` ハンドシェイクを主に使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-169"> primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="9930b-170">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信先は終了を開始せず、信頼できるメッセージの送信元は、信頼できるメッセージの送信先が開始する終了をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="9930b-170">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="9930b-171">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9930b-171">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="9930b-172">B1301: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`TerminateSequence` ハンドシェイクが正常に完了した後にのみ、`CloseSequence/CloseSequenceResponse` メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-172">B1301: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="9930b-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`LastMsgNumber` 要素が、各シーケンスのすべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに対し一貫性があることを検証します。</span><span class="sxs-lookup"><span data-stu-id="9930b-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="9930b-174">つまり、`LastMsgNumber` は、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在しないか、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在し、同一であるかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="9930b-174">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="9930b-175">B1303: `TerminateSequence` ハンドシェイクの後、`CloseSequence/CloseSequenceResponse` メッセージを受け取ると、信頼できるメッセージの送信先が `TerminateSequenceResponse` メッセージで応答します。</span><span class="sxs-lookup"><span data-stu-id="9930b-175">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="9930b-176">信頼できるメッセージの配信元は、`TerminateSequence` メッセージを送信する前に最終受信確認を受けるため、信頼できるメッセージの送信先ではシーケンスが終了したことが確実にわかり、すぐにリソースを再要求します。</span><span class="sxs-lookup"><span data-stu-id="9930b-176">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="9930b-177">B1304: `TerminateSequence` ハンドシェイクの前に、`CloseSequence/CloseSequenceResponse` メッセージを受け取ると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信先が `TerminateSequenceResponse` メッセージで応答します。</span><span class="sxs-lookup"><span data-stu-id="9930b-177">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="9930b-178">信頼できるメッセージの送信先でシーケンスが一貫していると判断した場合、信頼できるメッセージの送信先は、リソースを再要求する前にアプリケーションの送信先で指定された時間待機し、クライアントが最終受信確認を受け取ることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="9930b-178">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="9930b-179">それ以外の場合は、信頼できるメッセージの送信先はすぐにリソースを再要求し、`Faulted` イベントを発生させて、不明なシーケンスの終了をアプリケーションの送信先に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-179">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="9930b-180">`TerminateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-180">An example of a `TerminateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
      </wsrm:TerminateSequence>  
  </s:Body>  
</s:Envelope>  
Example TerminateSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:TerminateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequences"></a><span data-ttu-id="9930b-181">シーケンス</span><span class="sxs-lookup"><span data-stu-id="9930b-181">Sequences</span></span>  
 <span data-ttu-id="9930b-182">シーケンスに適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-182">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="9930b-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を生成し、アクセスするシーケンス番号より`xs:long`の最大包括値、9223372036854775807 します。</span><span class="sxs-lookup"><span data-stu-id="9930b-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="9930b-184">`Sequence` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-184">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="9930b-185">受信確認の要求</span><span class="sxs-lookup"><span data-stu-id="9930b-185">Request Acknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-186"> は、Keep-alive 機構として `AckRequested` ヘッダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-186"> uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="9930b-187">`AckRequested` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-187">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="9930b-188">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="9930b-188">SequenceAcknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-189"> は、WS-ReliableMessaging で用意されているシーケンス受信確認の抱き合わせ機構を使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-189"> uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="9930b-190">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9930b-190">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="9930b-191">R1601: 2 つの逆方向シーケンスを確立した場合を使用して、`Offer`メカニズム、`SequenceAcknowledgement`目的の受信者に送信アプリケーション メッセージにヘッダーを含めることがあります。</span><span class="sxs-lookup"><span data-stu-id="9930b-191">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="9930b-192">リモートのエンドポイントは、追加された `SequenceAcknowledgement` ヘッダーにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-192">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="9930b-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`SequenceAcknowledgement` 要素を含む `Nack` ヘッダーは生成しません。</span><span class="sxs-lookup"><span data-stu-id="9930b-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-194"> は、各 `Nack` 要素にシーケンス番号が格納されていることを検証しますが、シーケンス番号が格納されていない場合は、`Nack` 要素および値を無視します。</span><span class="sxs-lookup"><span data-stu-id="9930b-194"> validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="9930b-195">`SequenceAcknowledgement` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-195">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="9930b-196">WS-ReliableMessaging エラー</span><span class="sxs-lookup"><span data-stu-id="9930b-196">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="9930b-197">WS-ReliableMessaging エラーの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 実装に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-197">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="9930b-198">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9930b-198">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="9930b-199">B1701:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を生成しません`MessageNumberRollover`エラーです。</span><span class="sxs-lookup"><span data-stu-id="9930b-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="9930b-200">B1702: SOAP 1.2 では、サービス エンドポイントが接続制限に達し、新しい接続を処理できない場合、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は入れ子にした `CreateSequenceRefused` エラー サブコード `netrm:ConnectionLimitReached` を生成します。</span><span class="sxs-lookup"><span data-stu-id="9930b-200">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>  
  </s:Header>  
  <s:Body>  
    <s:Fault>  
      <s:Code>  
        <s:Value>s:Receiver</s:Value>  
        <s:Subcode>  
          <s:Value>wsrm:CreateSequenceRefused</s:Value>  
          <s:Subcode>  
            <s:Value>netrm:ConnectionLimitReached</s:Value>  
          </s:Subcode>  
        </s:Subcode>  
      </s:Code>  
      <s:Reason>  
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>  
      </s:Reason>  
    </s:Fault>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="9930b-201">WS-Addressing エラー</span><span class="sxs-lookup"><span data-stu-id="9930b-201">WS-Addressing Faults</span></span>  
 <span data-ttu-id="9930b-202">WS-ReliableMessaging は WS-Addressing を使用するため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の WS-ReliableMessaging 実装は、WS-Addressing エラーを生成して送信できます。</span><span class="sxs-lookup"><span data-stu-id="9930b-202">Because WS-ReliableMessaging uses WS-Addressing, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="9930b-203">ここでは、WS-ReliableMessaging レイヤーで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が明示的に生成および送信する WS-Addressing エラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9930b-203">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="9930b-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]生成し、送信、`Message Addressing Header Required`エラーに、次のいずれかが true の場合。</span><span class="sxs-lookup"><span data-stu-id="9930b-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="9930b-205">`CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `MessageId` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="9930b-205">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="9930b-206">`CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `ReplyTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="9930b-206">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="9930b-207">`CreateSequenceResponse`、`CloseSequenceResponse`、または `TerminateSequenceResponse` メッセージに `RelatesTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="9930b-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="9930b-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]生成し、送信、`Endpoint Unavailable`をリッスンしているエンドポイントがないことを示すフォールトでアドレス指定ヘッダーの検査に基づいてシーケンスを処理することができます、`CreateSequence`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="9930b-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="9930b-209">プロトコル コンポジション</span><span class="sxs-lookup"><span data-stu-id="9930b-209">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="9930b-210">WS-Addressing によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="9930b-210">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-211"> は、WS-Addressing の 2 つのバージョンをサポートしています。WS-Addressing 2004/08 [WS-ADDR] と、W3C WS-Addressing 1.0 Recommendation ([WS-ADDR-CORE] および [WS-ADDR-SOAP]) です。</span><span class="sxs-lookup"><span data-stu-id="9930b-211"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="9930b-212">WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="9930b-212">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="9930b-213">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-213">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="9930b-214">R2101: WS-Addressing 2004/08 と WS-Addressing 1.0 の両方を WS-ReliableMessaging で使用できます。</span><span class="sxs-lookup"><span data-stu-id="9930b-214">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="9930b-215">R2102: 特定の WS-ReliableMessaging シーケンス、または `Offer` 機構を使用して関連付けられた逆方向シーケンスのペアでは、同じバージョンの WS-Addressing を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-215">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="9930b-216">SOAP によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="9930b-216">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-217"> では、WS-ReliableMessaging で SOAP 1.1 と SOAP 1.2 の両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9930b-217"> supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="9930b-218">WS-Security と WS-SecureConversation によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="9930b-218">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-219"> は、セキュリティで保護されたトランスポート (HTTPS)、WS-Security によるコンポジション、および WS-SecureConversation によるコンポジションを使用して、WS-ReliableMessaging シーケンスを保護します。</span><span class="sxs-lookup"><span data-stu-id="9930b-219"> provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="9930b-220">WS-ReliableMessaging 1.1 プロトコル、WS-Security 1.1、および WS-Secure Conversation 1.3 プロトコルは一緒に使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-220">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="9930b-221">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-221">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="9930b-222">R2301: 個々のメッセージの整合性と機密性だけでなく、WS-ReliableMessaging シーケンスの整合性を保護するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では WS-SecureConversation を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-222">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="9930b-223">R2302:AWS-Ws-reliablemessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-223">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="9930b-224">R2303: WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-224">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="9930b-225">B2304:WS-ReliableMessaging シーケンスまたは相関逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。</span><span class="sxs-lookup"><span data-stu-id="9930b-225">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="9930b-226">R2305: WS-SecureConversation を使用して構成した場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーでは、`CreateSequence` メッセージに `wsse:SecurityTokenReference` 要素および `wsrm:UsesSequenceSTR` ヘッダーが含まれていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="9930b-226">R2305: When composed with WS-Secure Conversation, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="9930b-227">`UsesSequenceSTR` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-227">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="9930b-228">SSL/TLS セッションによるコンポジション</span><span class="sxs-lookup"><span data-stu-id="9930b-228">Composition with SSL/TLS sessions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-229"> は、次のようにSSL/TLS セッションによるコンポジションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9930b-229"> does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="9930b-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsrm:UsesSequenceSSL` ヘッダーを生成しません。</span><span class="sxs-lookup"><span data-stu-id="9930b-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="9930b-231">R2402: 信頼できるメッセージのイニシエーターは、`CreateSequence` レスポンダーに `wsrm:UsesSequenceSSL` ヘッダーが付いた [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージを送信できません。</span><span class="sxs-lookup"><span data-stu-id="9930b-231">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="9930b-232">WS-Policy によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="9930b-232">Composition with WS-Policy</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-233"> は、WS-Policy 1.2 および WS-Policy 1.5 の 2 つのバージョンの WS-Policy をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9930b-233"> supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="9930b-234">WS-ReliableMessaging の WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="9930b-234">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-235"> は、WS-ReliableMessaging の `wsrm:RMAssertion` WS-Policy アサーションを使用して、エンドポイントの機能を記述します。</span><span class="sxs-lookup"><span data-stu-id="9930b-235"> uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="9930b-236">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-236">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="9930b-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsrmn:RMAssertion` WS-Policy アサーションを `wsdl:binding` 要素にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="9930b-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-238"> は、`wsdl:binding` 要素および `wsdl:port` 要素へのアタッチをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9930b-238"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="9930b-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsp:Optional` タグを生成しません。</span><span class="sxs-lookup"><span data-stu-id="9930b-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="9930b-240">B3003: `wsrmp:RMAssertion` WS-Policy アサーションにアクセスする場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `wsp:Optional` タグを無視し、WS-RM ポリシーを必須のポリシーとして使用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-240">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="9930b-241">R3004: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は SSL/TLS セッションで構成できないため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `wsrmp:SequenceTransportSecurity` を指定するポリシーを受け付けません。</span><span class="sxs-lookup"><span data-stu-id="9930b-241">R3004: Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not compose with SSL/TLS sessions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="9930b-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、常に `wsrmp:DeliveryAssurance` 要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="9930b-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="9930b-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は常に `wsrmp:ExactlyOnce` 配信保証を指定します。</span><span class="sxs-lookup"><span data-stu-id="9930b-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="9930b-244">B3007:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]が生成されます、Ws-reliablemessaging アサーションの以下のプロパティを読み取るし、上に制御を提供、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="9930b-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="9930b-245">`RMAssertion` の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-245">An example of a `RMAssertion`.</span></span>  
  
    ```xml  
    <wsrmp:RMAssertion>  
      <wsp:Policy>  
        <wsrmp:SequenceSTR/>  
        <wsrmp:DeliveryAssurance>  
          <wsp:Policy>  
            <wsrmp:ExactlyOnce/>  
            <wsrmp:InOrder/>  
          </wsp:Policy>  
        </wsrmp:DeliveryAssurance>  
      </wsp:Policy>  
      <netrmp:InactivityTimeout Milliseconds="600000"/>  
      <netrmp:AcknowledgementInterval Milliseconds="200"/>  
    </wsrmp:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="9930b-246">WS-ReliableMessaging のフロー制御拡張</span><span class="sxs-lookup"><span data-stu-id="9930b-246">Flow Control WS-ReliableMessaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-247"> は、WS-ReliableMessaging の機能拡張を使用して、シーケンス メッセージ フローのさらに厳密な制御を実現します。</span><span class="sxs-lookup"><span data-stu-id="9930b-247"> uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="9930b-248">フロー制御が有効になって、`ReliableSessionBindingElement`の`FlowControlEnabled``boolean`プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="9930b-248">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="9930b-249">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-249">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="9930b-250">B4001: 信頼できるメッセージング フロー制御を有効にした場合、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `netrm:BufferRemaining` ヘッダーの要素拡張で `SequenceAcknowledgement` 要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="9930b-250">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="9930b-251">B4002: 信頼できるメッセージング フロー制御を有効にした場合でも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では `netrm:BufferRemaining` ヘッダーに `SequenceAcknowledgement` 要素は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9930b-251">B4002: Even when Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="9930b-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信先は、`netrm:BufferRemaining` を使用して、バッファーに保持できる新しいメッセージの数を示します。</span><span class="sxs-lookup"><span data-stu-id="9930b-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="9930b-253">B4004:When 信頼できるメッセージング フロー制御が有効になっている、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]信頼できるメッセージング送信元の値を使用して`netrm:BufferRemaining`スロットル メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-253">B4004:When Reliable Messaging Flow Control is enabled, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="9930b-254">B4005 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、0 ～ 4096 の整数値の `netrm:BufferRemaining` を生成し、0 ～ 214748364 (`xs:int` の `maxInclusive` 値) の整数値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="9930b-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="9930b-255">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="9930b-255">Message Exchange Patterns</span></span>  
 <span data-ttu-id="9930b-256">ここでは、WS-ReliableMessaging をさまざまなメッセージ交換パターンに使用する際の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="9930b-256">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="9930b-257">各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。</span><span class="sxs-lookup"><span data-stu-id="9930b-257">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="9930b-258">アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。</span><span class="sxs-lookup"><span data-stu-id="9930b-258">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="9930b-259">アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="9930b-259">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="9930b-260">一方向 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="9930b-260">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="9930b-261">バインド</span><span class="sxs-lookup"><span data-stu-id="9930b-261">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-262"> は、1 つの HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="9930b-262"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-263"> は、HTTP 要求を使用してイニシエーターからレスポンダーにすべてのメッセージを送信し、HTTP 応答を使用してレスポンダーからイニシエーターにすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-263"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="9930b-264">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-264">CreateSequence Exchange</span></span>  
 <span data-ttu-id="9930b-265">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素のない `Offer` メッセージを転送し、HTTP 応答で `CreateSequenceResponse` メッセージを待機します。</span><span class="sxs-lookup"><span data-stu-id="9930b-265">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="9930b-266">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成し、HTTP 応答で `CreateSequenceResponse` 要素のない `Accept` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-266">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="9930b-267">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="9930b-267">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="9930b-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`CreateSequence` メッセージとエラー メッセージを除くすべてのメッセージの応答で受信確認を処理します。</span><span class="sxs-lookup"><span data-stu-id="9930b-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="9930b-269">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、すべてのシーケンス メッセージと `AckRequested` メッセージへの HTTP 応答として、必ずスタンドアロンの受信確認を転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-269">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="9930b-270">CloseSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-270">CloseSequence Exchange</span></span>  
 <span data-ttu-id="9930b-271">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CloseSequence` メッセージを転送し、HTTP 応答で `CreateSequenceResponse` メッセージを待機します。</span><span class="sxs-lookup"><span data-stu-id="9930b-271">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="9930b-272">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、HTTP 応答で `CloseSequenceResponse` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-272">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="9930b-273">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-273">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="9930b-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `TerminateSequence` メッセージを転送し、HTTP 応答で `TerminateSequenceResponse` メッセージを待機します。</span><span class="sxs-lookup"><span data-stu-id="9930b-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="9930b-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、HTTP 応答で `TerminateSequenceResponse` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="9930b-276">一方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="9930b-276">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="9930b-277">バインド</span><span class="sxs-lookup"><span data-stu-id="9930b-277">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-278"> は、受信用 HTTP チャネルと送信用 HTTP チャネルで 1 つのシーケンスを使用する、一方向メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="9930b-278"> provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-279"> は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-279"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9930b-280">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9930b-280">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="9930b-281">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-281">CreateSequence Exchange</span></span>  
 <span data-ttu-id="9930b-282">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素のない `Offer` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-282">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="9930b-283">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成し、HTTP 要求で `CreateSequenceResponse` 要素のない `Accept` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-283">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="9930b-284">双方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="9930b-284">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="9930b-285">バインド</span><span class="sxs-lookup"><span data-stu-id="9930b-285">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-286"> には、受信用 HTTP チャネルと送信用 HTTP チャネルで 2 つのシーケンスを使用する、完全に非同期の双方向メッセージ交換パターンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9930b-286"> provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="9930b-287">このメッセージ交換パターンは、限定された方法で `Request/Reply`、`Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="9930b-287">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-288"> は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-288"> uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9930b-289">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9930b-289">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="9930b-290">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-290">CreateSequence Exchange</span></span>  
 <span data-ttu-id="9930b-291">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素のある `Offer` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-291">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="9930b-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequence` に `Offer` 要素があることを確認し、シーケンスを作成して `CreateSequenceResponse` 要素のない `Accept` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="9930b-293">シーケンスの有効期間</span><span class="sxs-lookup"><span data-stu-id="9930b-293">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-294"> は、2 つのシーケンスを 1 つの完全な双方向セッションとして処理します。</span><span class="sxs-lookup"><span data-stu-id="9930b-294"> treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="9930b-295">一方のシーケンスをフォールトするエラーが生成されると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、リモート エンドポイントに両方のシーケンスをフォールトするよう要求します。</span><span class="sxs-lookup"><span data-stu-id="9930b-295">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="9930b-296">一方のシーケンスをフォールトするエラーを読み取ると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は両方のシーケンスをフォールトします。</span><span class="sxs-lookup"><span data-stu-id="9930b-296">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-297"> は、送信シーケンスを終了し、受信シーケンスで引き続きメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="9930b-297"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="9930b-298">逆に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信シーケンスの終了を処理し、送信シーケンスで引き続きメッセージを送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="9930b-298">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="9930b-299">要求/応答および一方向のアドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="9930b-299">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="9930b-300">バインド</span><span class="sxs-lookup"><span data-stu-id="9930b-300">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-301"> は、1 つの HTTP チャネルで 2 つのシーケンスを使用して、一方向の要求/応答メッセージ交換パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="9930b-301"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-302"> は、HTTP 要求を使用してイニシエーターからレスポンダーにすべてのメッセージを送信し、HTTP 応答を使用してレスポンダーからイニシエーターにすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-302"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="9930b-303">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-303">CreateSequence Exchange</span></span>  
 <span data-ttu-id="9930b-304">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素がある `Offer` メッセージを転送し、HTTP 応答で `CreateSequenceResponse` メッセージを待機します。</span><span class="sxs-lookup"><span data-stu-id="9930b-304">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="9930b-305">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成し、HTTP 応答で `CreateSequenceResponse` 要素がある `Accept` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-305">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="9930b-306">一方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="9930b-306">One-way Message</span></span>  
 <span data-ttu-id="9930b-307">一方向メッセージ交換を正常に完了するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答でスタンドアロンの `SequenceAcknowledgement` メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-307">To complete a one-way message exchange successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="9930b-308">`SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-308">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="9930b-309">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードによる応答で要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="9930b-309">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="9930b-310">双方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="9930b-310">Two Way Messages</span></span>  
 <span data-ttu-id="9930b-311">双方向メッセージ交換プロトコルを正常に完了するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-311">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="9930b-312">応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9930b-312">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="9930b-313">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードで要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="9930b-313">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="9930b-314">一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。</span><span class="sxs-lookup"><span data-stu-id="9930b-314">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="9930b-315">応答の再試行</span><span class="sxs-lookup"><span data-stu-id="9930b-315">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-316"> は、双方向メッセージ交換プロトコルの相関関係について、HTTP 要求/応答の相関関係に依存しています。</span><span class="sxs-lookup"><span data-stu-id="9930b-316"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="9930b-317">このため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、要求シーケンス メッセージが受信確認されたときではなく、HTTP 応答によって `SequenceAcknowledgement`、アプリケーション応答、またはエラーが送信されたときに、要求シーケンス メッセージの再試行を停止します。</span><span class="sxs-lookup"><span data-stu-id="9930b-317">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="9930b-318">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答が関連付けられている要求の HTTP 要求で応答を再試行します。</span><span class="sxs-lookup"><span data-stu-id="9930b-318">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="9930b-319">CloseSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-319">CloseSequence Exchange</span></span>  
 <span data-ttu-id="9930b-320">すべての一方向の要求シーケンス メッセージが、すべての応答シーケンス メッセージおよび受信確認を受信した後、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンスに `CloseSequence` メッセージを転送し、HTTP 応答で `CloseSequenceResponse` を待機します。</span><span class="sxs-lookup"><span data-stu-id="9930b-320">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="9930b-321">要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。</span><span class="sxs-lookup"><span data-stu-id="9930b-321">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="9930b-322">つまり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`SequenceAcknowledgement` メッセージに応答シーケンスの最終的な `CloseSequence` を含め、応答シーケンスには `CloseSequence` 交換がありません。</span><span class="sxs-lookup"><span data-stu-id="9930b-322">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="9930b-323">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、すべての応答が受信確認されたことを確認し、HTTP 応答で `CloseSequenceResponse` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-323">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="9930b-324">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-324">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="9930b-325">`CloseSequenceResponse` メッセージを受け取った後、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは HTTP 要求で要求シーケンスに `TerminateSequence` メッセージを転送し、HTTP 応答で `TerminateSequenceResponse` を待機します。</span><span class="sxs-lookup"><span data-stu-id="9930b-325">After receiving the `CloseSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="9930b-326">`CloseSequence` 交換と同じように、要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。</span><span class="sxs-lookup"><span data-stu-id="9930b-326">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="9930b-327">つまり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`SequenceAcknowledgement` メッセージに応答シーケンスの最終的な `TerminateSequence` を含め、応答シーケンスには `TerminateSequence` 交換がありません。</span><span class="sxs-lookup"><span data-stu-id="9930b-327">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="9930b-328">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、HTTP 応答で `TerminateSequenceResponse` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-328">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="9930b-329">要求/応答 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="9930b-329">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="9930b-330">バインド</span><span class="sxs-lookup"><span data-stu-id="9930b-330">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-331"> には、受信用 HTTP チャネルと送信用 HTTP チャネルで 2 つのシーケンスを使用する、要求/応答メッセージ交換パターンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9930b-331"> provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="9930b-332">このメッセージ交換パターンは、限定された方法で `Duplex, Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="9930b-332">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-333"> は、HTTP 要求を使用してすべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="9930b-333"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="9930b-334">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9930b-334">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="9930b-335">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="9930b-335">CreateSequence Exchange</span></span>  
 <span data-ttu-id="9930b-336">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素のある `Offer` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-336">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="9930b-337">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequence` に `Offer` 要素があることを確認し、シーケンスを作成して `CreateSequenceResponse` 要素がある `Accept` メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="9930b-337">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="9930b-338">要求/応答の相関関係</span><span class="sxs-lookup"><span data-stu-id="9930b-338">Request/Reply Correlation</span></span>  
 <span data-ttu-id="9930b-339">次の状況は、すべての相関関係にある要求/応答で発生します。</span><span class="sxs-lookup"><span data-stu-id="9930b-339">The following applies to all correlated requests and replies:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-340"> は、すべてのアプリケーション要求メッセージに `ReplyTo` エンドポイント参照と `MessageId` が保持されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9930b-340"> ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-341"> は、各アプリケーション要求メッセージの `ReplyTo` としてローカル エンドポイント参照を適用します。</span><span class="sxs-lookup"><span data-stu-id="9930b-341"> applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="9930b-342">ローカル エンドポイント参照は、イニシエーターの `CreateSequence` メッセージの `ReplyTo` であり、レスポンダーの `CreateSequence` メッセージの `To` です。</span><span class="sxs-lookup"><span data-stu-id="9930b-342">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-343"> は、受信要求メッセージに `MessageId` と `ReplyTo` が保持されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9930b-343"> ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-344"> は、すべてのアプリケーション要求メッセージの `ReplyTo` エンドポイント参照の URI が、先に定義したローカル エンドポイント参照と一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9930b-344"> ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9930b-345"> は、`RelatesTo` 要求/応答の相関ルールに従い、すべての応答に正しい `To` ヘッダーおよび `wsa` ヘッダーが保持されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9930b-345"> ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
