---
title: 信頼できるメッセージング プロトコル バージョン 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 8ff02bc6953ec1e5030dd0b592a352b7e23ab0d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496959"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="b8241-102">信頼できるメッセージング プロトコル バージョン 1.1</span><span class="sxs-lookup"><span data-stu-id="b8241-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="b8241-103">このトピックでは、Windows Communication Foundation (WCF) の実装の詳細を説明の Ws-reliablemessaging 2007/02 (バージョン 1.1) プロトコルは HTTP トランスポートを使用して相互運用のために必要なです。</span><span class="sxs-lookup"><span data-stu-id="b8241-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="b8241-104">WCF では、制約とこのトピックで説明した説明は、Ws-reliablemessaging 仕様に従います。</span><span class="sxs-lookup"><span data-stu-id="b8241-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="b8241-105">以降では、Ws-reliablemessaging 1.1 プロトコルを実装することに注意してください、[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="b8241-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="b8241-106">Ws-reliablemessaging 2007/02 プロトコルは、WCF で実装されて、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>です。</span><span class="sxs-lookup"><span data-stu-id="b8241-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="b8241-107">便宜上、ここでは次のロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8241-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="b8241-108">イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント。</span><span class="sxs-lookup"><span data-stu-id="b8241-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="b8241-109">レスポンダー : イニシエーターの要求を受け取るサービス。</span><span class="sxs-lookup"><span data-stu-id="b8241-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="b8241-110">このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8241-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="b8241-111">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="b8241-111">Prefix</span></span>|<span data-ttu-id="b8241-112">名前空間</span><span class="sxs-lookup"><span data-stu-id="b8241-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="b8241-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="b8241-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|<span data-ttu-id="b8241-114">netrm</span><span class="sxs-lookup"><span data-stu-id="b8241-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="b8241-115">s</span><span class="sxs-lookup"><span data-stu-id="b8241-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="b8241-116">wsa</span><span class="sxs-lookup"><span data-stu-id="b8241-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="b8241-117">wsse</span><span class="sxs-lookup"><span data-stu-id="b8241-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="b8241-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="b8241-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|<span data-ttu-id="b8241-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="b8241-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|<span data-ttu-id="b8241-120">wsp</span><span class="sxs-lookup"><span data-stu-id="b8241-120">wsp</span></span>|<span data-ttu-id="b8241-121">(WS-Policy 1.2 または WS-Policy 1.5 のいずれか)</span><span class="sxs-lookup"><span data-stu-id="b8241-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="b8241-122">メッセージング</span><span class="sxs-lookup"><span data-stu-id="b8241-122">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="b8241-123">シーケンスの作成</span><span class="sxs-lookup"><span data-stu-id="b8241-123">Sequence Creation</span></span>  
 <span data-ttu-id="b8241-124">WCF 実装`CreateSequence`と`CreateSequenceResponse`信頼できるメッセージングを確立するためにメッセージのシーケンスします。</span><span class="sxs-lookup"><span data-stu-id="b8241-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="b8241-125">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-125">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="b8241-126">B1101: WCF イニシエーターを使用して、同じエンドポイント参照として、`CreateSequence`メッセージの`ReplyTo`、`AcksTo`と`Offer/Endpoint`です。</span><span class="sxs-lookup"><span data-stu-id="b8241-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="b8241-127">R1102: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、オクテット単位で一致する同じ文字列表現のアドレス値が必要です。</span><span class="sxs-lookup"><span data-stu-id="b8241-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="b8241-128">WCF 応答側であることを確認の URI 部分、 `AcksTo`、`ReplyTo`と`Endpoint`シーケンスを作成する前に、エンドポイント参照は同じです。</span><span class="sxs-lookup"><span data-stu-id="b8241-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="b8241-129">R1103: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、同一の参照パラメーターのセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="b8241-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   <span data-ttu-id="b8241-130">WCF は強制されませんが、その参照を前提としていますのパラメーター、 `AcksTo`、`ReplyTo`と`Offer/Endpoint`エンドポイント参照に`CreateSequence`が同じパラメーターを使用する参照から、`ReplyTo`エンドポイント参照の受信確認と逆方向シーケンス メッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="b8241-131">B1104: WCF イニシエーターを生成しません、省略可能な`Expires`または`Offer/Expires`内の要素、`CreateSequence`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="b8241-132">B1105: にアクセスするとき、 `CreateSequence` WCF レスポンダーは、メッセージ、`Expires`値で、`CreateSequence`要素として、`Expires`値で、`CreateSequenceResponse`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="b8241-133">それ以外の場合、WCF レスポンダーを読み込んで、無視、`Expires`と`Offer/Expires`値。</span><span class="sxs-lookup"><span data-stu-id="b8241-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="b8241-134">B1106: にアクセスするとき、`CreateSequenceResponse`メッセージ、WCF イニシエーターは、省略可能な読み取り`Expires`値は使用しません。</span><span class="sxs-lookup"><span data-stu-id="b8241-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="b8241-135">B1107: WCF イニシエーターおよびレスポンダーは常に生成、省略可能な`IncompleteSequenceBehavior`内の要素、`CreateSequence/Offer`と`CreateSequenceResponse`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="b8241-136">B1108: WCF のみ使用する、`DiscardFollowingFirstGap`と`NoDiscard`の値が、`IncompleteSequenceBehavior`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="b8241-137">WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構を利用しています。</span><span class="sxs-lookup"><span data-stu-id="b8241-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="b8241-138">B1109: 場合`CreateSequence`が含まれています、`Offer`要素、一方向の WCF レスポンダーを拒否、用意されたシーケンスで応答して、`CreateSequenceResponse`せず、`Accept`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="b8241-139">B1110: 信頼できるメッセージング レスポンダーは、用意されたシーケンスを拒否する場合、新たに確立されたシーケンスが違反 WCF イニシエーター。</span><span class="sxs-lookup"><span data-stu-id="b8241-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="b8241-140">B1111: 場合`CreateSequence`が含まれていない、`Offer`要素、双方向の WCF レスポンダーを拒否、用意されたシーケンスで応答して、`CreateSequenceRefused`フォールトします。</span><span class="sxs-lookup"><span data-stu-id="b8241-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="b8241-141">R1112: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、`[address]` エンドポイント参照の `CreateSequenceResponse/Accept/AcksTo` プロパティは、バイト単位で `CreateSequence` メッセージの送信先 URI と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="b8241-142">R1113: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、イニシエーターからレスポンダーに流れる両方のシーケンスにあるすべてのメッセージは、同じエンドポイント参照に送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 <span data-ttu-id="b8241-143">WCF では、Ws-reliablemessaging を使用して、イニシエーターとレスポンダー間で信頼できるセッションを確立します。</span><span class="sxs-lookup"><span data-stu-id="b8241-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="b8241-144">WCF の Ws-reliablemessaging 実装では、一方向、要求/応答、信頼できるセッションは、双方向メッセージ パターンです。</span><span class="sxs-lookup"><span data-stu-id="b8241-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="b8241-145">`Offer` および `CreateSequence` で WS-ReliableMessaging の `CreateSequenceResponse` 機構を使用すると、相関する 2 つの逆方向シーケンスを確立できます。また、Offer 機構は、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。</span><span class="sxs-lookup"><span data-stu-id="b8241-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="b8241-146">WCF では、セッションのセッションの整合性をエンド ツー エンドの保護などのセキュリティ保証を提供するために現実的では、同じパーティを対象とするメッセージが同じ送信先に到達することを確認します。</span><span class="sxs-lookup"><span data-stu-id="b8241-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="b8241-147">また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="b8241-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="b8241-148">したがって、R1102、R1112、および R1113 制約は、WCF に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>  
  
 <span data-ttu-id="b8241-149">`CreateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-149">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="b8241-150">`CreateSequenceResponse` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-150">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="b8241-151">シーケンスを閉じる</span><span class="sxs-lookup"><span data-stu-id="b8241-151">Closing a Sequence</span></span>  
 <span data-ttu-id="b8241-152">WCF を使用して、`CloseSequence`と`CloseSequenceResponse`信頼性の高いメッセージング ソースによって開始されたシャット ダウンのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="b8241-153">WCF の信頼できるメッセージの送信先はシャット ダウンを開始していないと、WCF の信頼できるメッセージの送信元が信頼できるメッセージング送信先が開始シャット ダウンをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b8241-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="b8241-154">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-154">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="b8241-155">B1201: WCF の信頼できるメッセージの送信元は常に送信する`CloseSequence`メッセージ シーケンスをシャット ダウンします。</span><span class="sxs-lookup"><span data-stu-id="b8241-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="b8241-156">B1202: 信頼できるメッセージの送信元は、`CloseSequence` メッセージを送信する前に、すべてのシーケンス メッセージの受信確認を待機します。</span><span class="sxs-lookup"><span data-stu-id="b8241-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="b8241-157">B1203: 信頼できるメッセージの送信元は、シーケンスにメッセージが含まれない場合を除き、常にオプションの `LastMsgNumber` 要素を含めます。</span><span class="sxs-lookup"><span data-stu-id="b8241-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="b8241-158">R1204: 信頼できるメッセージの送信先は、`CloseSequence` メッセージを送信してシャットダウンを開始することはできません。</span><span class="sxs-lookup"><span data-stu-id="b8241-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="b8241-159">: B1205`CloseSequence`メッセージ、WCF の信頼できるメッセージの送信元は不完全な順序を考慮し、エラーが送信されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="b8241-160">`CloseSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-160">An example of a `CloseSequence` message.</span></span>  
  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="b8241-161">シーケンスの終了</span><span class="sxs-lookup"><span data-stu-id="b8241-161">Sequence Termination</span></span>  
 <span data-ttu-id="b8241-162">WCF を使用して、主に、`TerminateSequence/TerminateSequenceResponse`ハンドシェイクが完了した後、`CloseSequence/CloseSequenceResponse`ハンドシェイクです。</span><span class="sxs-lookup"><span data-stu-id="b8241-162">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="b8241-163">WCF の信頼できるメッセージの送信先は終了を開始していないと、信頼できるメッセージの送信元が信頼できるメッセージング送信先が開始終了をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b8241-163">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="b8241-164">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-164">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="b8241-165">B1301: WCF にイニシエーターのみ送信、`TerminateSequence`メッセージが正常に完了した後、`CloseSequence/CloseSequenceResponse`ハンドシェイクです。</span><span class="sxs-lookup"><span data-stu-id="b8241-165">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="b8241-166">R1302: WCF を検証する、`LastMsgNumber`要素がすべてにわたって一貫性のある`CloseSequence`と`TerminateSequence`と指定されたシーケンスのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-166">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="b8241-167">つまり、`LastMsgNumber` は、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在しないか、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在し、同一であるかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="b8241-167">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="b8241-168">B1303: `TerminateSequence` ハンドシェイクの後、`CloseSequence/CloseSequenceResponse` メッセージを受け取ると、信頼できるメッセージの送信先が `TerminateSequenceResponse` メッセージで応答します。</span><span class="sxs-lookup"><span data-stu-id="b8241-168">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="b8241-169">信頼できるメッセージの配信元は、`TerminateSequence` メッセージを送信する前に最終受信確認を受けるため、信頼できるメッセージの送信先ではシーケンスが終了したことが確実にわかり、すぐにリソースを再要求します。</span><span class="sxs-lookup"><span data-stu-id="b8241-169">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="b8241-170">B1304: 受信するときに、`TerminateSequence`メッセージの前に、`CloseSequence/CloseSequenceResponse`ハンドシェイクで、WCF の信頼できるメッセージの送信先が応答、`TerminateSequenceResponse`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-170">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="b8241-171">信頼できるメッセージの送信先でシーケンスが一貫していると判断した場合、信頼できるメッセージの送信先は、リソースを再要求する前にアプリケーションの送信先で指定された時間待機し、クライアントが最終受信確認を受け取ることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="b8241-171">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="b8241-172">それ以外の場合は、信頼できるメッセージの送信先はすぐにリソースを再要求し、`Faulted` イベントを発生させて、不明なシーケンスの終了をアプリケーションの送信先に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-172">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="b8241-173">`TerminateSequence` メッセージの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-173">An example of a `TerminateSequence` message.</span></span>  
  
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
  
### <a name="sequences"></a><span data-ttu-id="b8241-174">シーケンス</span><span class="sxs-lookup"><span data-stu-id="b8241-174">Sequences</span></span>  
 <span data-ttu-id="b8241-175">シーケンスに適用される制約を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-175">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="b8241-176">B1401:WCF を生成し、アクセス シーケンス番号より`xs:long`の最大包括値、9223372036854775807 します。</span><span class="sxs-lookup"><span data-stu-id="b8241-176">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="b8241-177">`Sequence` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-177">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="b8241-178">受信確認の要求</span><span class="sxs-lookup"><span data-stu-id="b8241-178">Request Acknowledgement</span></span>  
 <span data-ttu-id="b8241-179">WCF を使用して、 `AckRequested` keep-alive 機構としてヘッダー。</span><span class="sxs-lookup"><span data-stu-id="b8241-179">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="b8241-180">`AckRequested` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-180">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="b8241-181">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="b8241-181">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="b8241-182">WCF では、Ws-reliablemessaging で提供されるシーケンス受信確認の「抱き合わせ」機構を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8241-182">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="b8241-183">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-183">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="b8241-184">R1601: 2 つの逆方向シーケンスを確立した場合を使用して、`Offer`メカニズム、`SequenceAcknowledgement`目的の受信者に送信アプリケーション メッセージにヘッダーを含めることがあります。</span><span class="sxs-lookup"><span data-stu-id="b8241-184">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="b8241-185">リモートのエンドポイントは、追加された `SequenceAcknowledgement` ヘッダーにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-185">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="b8241-186">B1602: WCF を生成しません`SequenceAcknowledgement`ヘッダーを含む`Nack`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-186">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="b8241-187">WCF は、その各検証`Nack`要素は、シーケンス番号が含まれていますが、それ以外の場合は無視されます、`Nack`要素と値。</span><span class="sxs-lookup"><span data-stu-id="b8241-187">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="b8241-188">`SequenceAcknowledgement` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-188">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="b8241-189">WS-ReliableMessaging エラー</span><span class="sxs-lookup"><span data-stu-id="b8241-189">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="b8241-190">Ws-reliablemessaging エラーの WCF 実装に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-190">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="b8241-191">以下の制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-191">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="b8241-192">B1701: WCF を生成しません`MessageNumberRollover`エラーです。</span><span class="sxs-lookup"><span data-stu-id="b8241-192">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="b8241-193">B1702: SOAP 1.2 では、経由で、サービス エンドポイントが、接続の上限に達するし、新しい接続を処理できないときに WCF 生成、入れ子になった`CreateSequenceRefused`エラー サブコード`netrm:ConnectionLimitReached`の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b8241-193">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="b8241-194">WS-Addressing エラー</span><span class="sxs-lookup"><span data-stu-id="b8241-194">WS-Addressing Faults</span></span>  
 <span data-ttu-id="b8241-195">Ws-reliablemessaging は Ws-addressing を使用するため WCF Ws-reliablemessaging 実装を生成して Ws-addressing エラーを送信する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-195">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="b8241-196">このセクションでは、WCF は、明示的に生成し、Ws-reliablemessaging レイヤーで送信する Ws-addressing エラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b8241-196">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="b8241-197">B1801:WCF が生成し、送信、`Message Addressing Header Required`エラーに、次のいずれかが true の場合。</span><span class="sxs-lookup"><span data-stu-id="b8241-197">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="b8241-198">`CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `MessageId` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="b8241-198">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="b8241-199">`CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `ReplyTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="b8241-199">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="b8241-200">`CreateSequenceResponse`、`CloseSequenceResponse`、または `TerminateSequenceResponse` メッセージに `RelatesTo` ヘッダーがない。</span><span class="sxs-lookup"><span data-stu-id="b8241-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="b8241-201">B1802:WCF が生成し、送信、`Endpoint Unavailable`をリッスンしているエンドポイントがないことを示すフォールトでアドレス指定ヘッダーの検査に基づいてシーケンスを処理することができます、`CreateSequence`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-201">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="b8241-202">プロトコル コンポジション</span><span class="sxs-lookup"><span data-stu-id="b8241-202">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="b8241-203">WS-Addressing によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="b8241-203">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="b8241-204">WCF は Ws-addressing の 2 つのバージョンをサポートしています: Ws-addressing 2004/08 [WS-ADDR] と W3C Ws-addressing 1.0 に関する推奨事項 [WS ADDR コア] と [WS ADDR SOAP] です。</span><span class="sxs-lookup"><span data-stu-id="b8241-204">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="b8241-205">WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="b8241-205">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="b8241-206">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-206">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="b8241-207">R2101: WS-Addressing 2004/08 と WS-Addressing 1.0 の両方を WS-ReliableMessaging で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8241-207">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="b8241-208">R2102: 特定の WS-ReliableMessaging シーケンス、または `Offer` 機構を使用して関連付けられた逆方向シーケンスのペアでは、同じバージョンの WS-Addressing を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-208">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="b8241-209">SOAP によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="b8241-209">Composition with SOAP</span></span>  
 <span data-ttu-id="b8241-210">WCF には、SOAP 1.1 と Ws-reliablemessaging で SOAP 1.2 の両方の使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b8241-210">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="b8241-211">WS-Security と WS-SecureConversation によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="b8241-211">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="b8241-212">WCF では、Ws-secure Conversation をセキュリティで保護されたトランスポート (HTTPS)、Ws-security によるコンポジション、コンポジションを使用して、Ws-reliablemessaging シーケンスの保護を提供します。</span><span class="sxs-lookup"><span data-stu-id="b8241-212">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="b8241-213">WS-ReliableMessaging 1.1 プロトコル、WS-Security 1.1、および WS-Secure Conversation 1.3 プロトコルは一緒に使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-213">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="b8241-214">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-214">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="b8241-215">R2301: 個々 のメッセージの整合性だけでなく、Ws-reliablemessaging シーケンスの整合性と機密性を保護するために WCF に必要な Ws-secureconversation を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-215">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="b8241-216">R2302:AWS-Ws-reliablemessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-216">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="b8241-217">R2303: WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-217">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="b8241-218">B2304:WS-ReliableMessaging シーケンスまたは相関逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。</span><span class="sxs-lookup"><span data-stu-id="b8241-218">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="b8241-219">R2305: Ws-secureconversation、構成した場合、WCF レスポンダーする必要があります、`CreateSequence`メッセージが含まれて、`wsse:SecurityTokenReference`要素および`wsrm:UsesSequenceSTR`ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="b8241-219">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="b8241-220">`UsesSequenceSTR` ヘッダーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-220">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="b8241-221">SSL/TLS セッションによるコンポジション</span><span class="sxs-lookup"><span data-stu-id="b8241-221">Composition with SSL/TLS sessions</span></span>  
 <span data-ttu-id="b8241-222">WCF は、SSL/TLS セッションによるコンポジションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b8241-222">WCF does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="b8241-223">B2401: WCF を生成しません、`wsrm:UsesSequenceSSL`ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="b8241-223">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="b8241-224">R2402: 信頼できるメッセージングの発信側が送信する必要があります、 `CreateSequence` 、メッセージ、 `wsrm:UsesSequenceSSL` WCF レスポンダーにヘッダー。</span><span class="sxs-lookup"><span data-stu-id="b8241-224">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="b8241-225">WS-Policy によるコンポジション</span><span class="sxs-lookup"><span data-stu-id="b8241-225">Composition with WS-Policy</span></span>  
 <span data-ttu-id="b8241-226">WCF Ws-policy の 2 つのバージョンでサポートされる: Ws-policy 1.2 および Ws-policy 1.5 です。</span><span class="sxs-lookup"><span data-stu-id="b8241-226">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="b8241-227">WS-ReliableMessaging の WS-Policy アサーション</span><span class="sxs-lookup"><span data-stu-id="b8241-227">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="b8241-228">Ws-reliablemessaging の Ws-policy アサーションを使用する WCF`wsrm:RMAssertion`エンドポイントの機能を記述します。</span><span class="sxs-lookup"><span data-stu-id="b8241-228">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="b8241-229">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-229">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="b8241-230">B3001: WCF アタッチ`wsrmn:RMAssertion`Ws-policy アサーションを`wsdl:binding`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-230">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="b8241-231">WCF へのアタッチをサポートしている`wsdl:binding`と`wsdl:port`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-231">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="b8241-232">B3002: WCF では生成されません、`wsp:Optional`タグ。</span><span class="sxs-lookup"><span data-stu-id="b8241-232">B3002: WCF never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="b8241-233">B3003: にアクセスするとき、 `wsrmp:RMAssertion` Ws-policy アサーション、WCF は無視されます、`wsp:Optional`タグ、および、WS-RM ポリシーを必須として扱われます。</span><span class="sxs-lookup"><span data-stu-id="b8241-233">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="b8241-234">R3004: ため、WCF は、SSL/TLS セッションでは構成は、WCF は受け入れませんを指定するポリシー`wsrmp:SequenceTransportSecurity`です。</span><span class="sxs-lookup"><span data-stu-id="b8241-234">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="b8241-235">B3005: WCF は常に生成、`wsrmp:DeliveryAssurance`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-235">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="b8241-236">B3006: WCF は常を指定します、`wsrmp:ExactlyOnce`配信が保証されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-236">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="b8241-237">B3007: WCF が生成されます、Ws-reliablemessaging アサーションの以下のプロパティを読み取るし、WCF の上にコントロールを提供`ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="b8241-237">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="b8241-238">`RMAssertion` の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-238">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="b8241-239">WS-ReliableMessaging のフロー制御拡張</span><span class="sxs-lookup"><span data-stu-id="b8241-239">Flow Control WS-ReliableMessaging Extension</span></span>  
 <span data-ttu-id="b8241-240">WCF では、Ws-reliablemessaging の機能拡張を使用して、追加のオプションの厳密な制御をシーケンス メッセージ フローを提供します。</span><span class="sxs-lookup"><span data-stu-id="b8241-240">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="b8241-241">フロー制御が有効になって、`ReliableSessionBindingElement`の`FlowControlEnabled``boolean`プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="b8241-241">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="b8241-242">WCF に適用される制約の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8241-242">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="b8241-243">B4001: 信頼できるメッセージング フロー制御を有効にすると、WCF の生成、`netrm:BufferRemaining`内の要素拡張の要素、`SequenceAcknowledgement`ヘッダーを次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b8241-243">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="b8241-244">B4002: 信頼できるメッセージング フロー制御が有効になっている場合でも WCF しないため、`netrm:BufferRemaining`内の要素、`SequenceAcknowledgement`ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="b8241-244">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="b8241-245">B4003: 信頼できるメッセージの送信先を WCF を使用して`netrm:BufferRemaining`を示す新しいメッセージの数がのバッファーに格納できます。</span><span class="sxs-lookup"><span data-stu-id="b8241-245">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="b8241-246">B4004:When 信頼できるメッセージング フロー制御が有効になっている、信頼できるメッセージングを WCF ソースの値が使用`netrm:BufferRemaining`スロットル メッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="b8241-246">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="b8241-247">B4005: WCF 生成`netrm:BufferRemaining`整数、0 ~ 4096 の範囲、範囲値を 0 との間の整数値を読み取りますと`xs:int`の`maxInclusive`214748364 の値します。</span><span class="sxs-lookup"><span data-stu-id="b8241-247">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="b8241-248">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="b8241-248">Message Exchange Patterns</span></span>  
 <span data-ttu-id="b8241-249">このセクションでは、Ws-reliablemessaging をさまざまなメッセージ交換パターンに使用すると、WCF の動作がについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b8241-249">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="b8241-250">各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。</span><span class="sxs-lookup"><span data-stu-id="b8241-250">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="b8241-251">アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。</span><span class="sxs-lookup"><span data-stu-id="b8241-251">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="b8241-252">アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="b8241-252">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="b8241-253">一方向 : アドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="b8241-253">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="b8241-254">バインド</span><span class="sxs-lookup"><span data-stu-id="b8241-254">Binding</span></span>  
 <span data-ttu-id="b8241-255">WCF には、1 つの HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b8241-255">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="b8241-256">WCF では、HTTP 要求を使用して、すべてのメッセージ、イニシエーターからレスポンダーおよび HTTP 応答にレスポンダーからイニシエーターにすべてのメッセージを送信するを送信します。</span><span class="sxs-lookup"><span data-stu-id="b8241-256">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="b8241-257">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="b8241-258">WCF の発信側の送信、`CreateSequence`のないメッセージ`Offer`、HTTP 要求で要素と予想している、 `CreateSequenceResponse` HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-258">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="b8241-259">WCF レスポンダーは、シーケンスを作成し、転送、`CreateSequenceResponse`のないメッセージ`Accept`HTTP 応答での要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-259">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="b8241-260">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="b8241-260">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="b8241-261">WCF のイニシエーターを除くすべてのメッセージの返信の受信確認の処理、`CreateSequence`メッセージとエラー メッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-261">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="b8241-262">WCF 応答側が常にすべてのシーケンスに、HTTP 応答でスタンドアロンの受信確認を送信し、`AckRequested`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-262">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="b8241-263">CloseSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-263">CloseSequence Exchange</span></span>  
 <span data-ttu-id="b8241-264">WCF の発信側の送信、 `CloseSequence` 、HTTP 要求でメッセージを期待、 `CreateSequenceResponse` HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-264">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="b8241-265">WCF 応答側の送信、 `CloseSequenceResponse` HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-265">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="b8241-266">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-266">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="b8241-267">WCF の発信側の送信、 `TerminateSequence` 、HTTP 要求でメッセージを期待、 `TerminateSequenceResponse` HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-267">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="b8241-268">WCF 応答側の送信、 `TerminateSequenceResponse` HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-268">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="b8241-269">一方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="b8241-269">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="b8241-270">バインド</span><span class="sxs-lookup"><span data-stu-id="b8241-270">Binding</span></span>  
 <span data-ttu-id="b8241-271">WCF には、いずれか 1 つのシーケンスを使用して、一方向メッセージ交換パターンが用意されています受信送信用 HTTP チャネルとします。</span><span class="sxs-lookup"><span data-stu-id="b8241-271">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="b8241-272">WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="b8241-272">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="b8241-273">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8241-273">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="b8241-274">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-274">CreateSequence Exchange</span></span>  
 <span data-ttu-id="b8241-275">WCF の発信側の送信、`CreateSequence`のないメッセージ`Offer`HTTP 要求での要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-275">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="b8241-276">WCF レスポンダーは、シーケンスを作成し、転送、`CreateSequenceResponse`のないメッセージ`Accept`HTTP 要求での要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-276">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="b8241-277">双方向 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="b8241-277">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="b8241-278">バインド</span><span class="sxs-lookup"><span data-stu-id="b8241-278">Binding</span></span>  
 <span data-ttu-id="b8241-279">WCF は、2 つを使用して、完全に非同期の双方向メッセージ交換パターンでのシーケンス受信送信用 HTTP チャネルとします。</span><span class="sxs-lookup"><span data-stu-id="b8241-279">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="b8241-280">このメッセージ交換パターンは、限定された方法で `Request/Reply`、`Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b8241-280">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="b8241-281">WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="b8241-281">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="b8241-282">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8241-282">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="b8241-283">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-283">CreateSequence Exchange</span></span>  
 <span data-ttu-id="b8241-284">WCF の発信側が送信、 `CreateSequence` 、メッセージ、 `Offer` HTTP 要求での要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-284">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="b8241-285">WCF レスポンダーは、確実、`CreateSequence`が、`Offer`要素のシーケンスを作成し、送信、 `CreateSequenceResponse` 、メッセージ、`Accept`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-285">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="b8241-286">シーケンスの有効期間</span><span class="sxs-lookup"><span data-stu-id="b8241-286">Sequence Lifetime</span></span>  
 <span data-ttu-id="b8241-287">WCF は、2 つのシーケンスを 1 つの完全な双方向セッションとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="b8241-287">WCF treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="b8241-288">1 つのシーケンスをフォールトするエラーの生成時に、WCF には、リモート エンドポイントに両方のシーケンスをフォールトするが期待しています。</span><span class="sxs-lookup"><span data-stu-id="b8241-288">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="b8241-289">1 つのシーケンスをフォールトするエラーを読み取り、時に WCF フォールトの両方のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="b8241-289">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="b8241-290">WCF は、送信シーケンスを閉じるし、受信シーケンスでメッセージの処理を継続することができます。</span><span class="sxs-lookup"><span data-stu-id="b8241-290">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="b8241-291">反対に、WCF は、受信シーケンスの終了を処理し、送信シーケンスでメッセージを送信し続けます。</span><span class="sxs-lookup"><span data-stu-id="b8241-291">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="b8241-292">要求/応答および一方向のアドレス不可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="b8241-292">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="b8241-293">バインド</span><span class="sxs-lookup"><span data-stu-id="b8241-293">Binding</span></span>  
 <span data-ttu-id="b8241-294">WCF は、一方向および要求/応答メッセージ交換パターンを使用して 2 つの 1 つの HTTP チャネルのシーケンスします。</span><span class="sxs-lookup"><span data-stu-id="b8241-294">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="b8241-295">WCF では、HTTP 要求を使用して、すべてのメッセージ、イニシエーターからレスポンダーおよび HTTP 応答にレスポンダーからイニシエーターにすべてのメッセージを送信するを送信します。</span><span class="sxs-lookup"><span data-stu-id="b8241-295">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="b8241-296">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-296">CreateSequence Exchange</span></span>  
 <span data-ttu-id="b8241-297">WCF の発信側の送信、`CreateSequence`メッセージを`Offer`、HTTP 要求で要素と予想している、 `CreateSequenceResponse` HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-297">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="b8241-298">WCF レスポンダーは、シーケンスを作成し、転送、 `CreateSequenceResponse` 、メッセージ、 `Accept` HTTP 応答での要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-298">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="b8241-299">一方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="b8241-299">One-way Message</span></span>  
 <span data-ttu-id="b8241-300">一方向メッセージ交換を正常に完了するには、WCF 発信側は、HTTP 要求で要求シーケンス メッセージを送信し、受信スタンドアロン`SequenceAcknowledgement`HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-300">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="b8241-301">`SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-301">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="b8241-302">WCF レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードを含む応答を伴う要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="b8241-302">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="b8241-303">双方向のメッセージ</span><span class="sxs-lookup"><span data-stu-id="b8241-303">Two Way Messages</span></span>  
 <span data-ttu-id="b8241-304">双方向メッセージ交換プロトコルを正常に完了するは、WCF イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="b8241-304">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="b8241-305">応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8241-305">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="b8241-306">WCF レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードを含む応答を伴う要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="b8241-306">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="b8241-307">一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。</span><span class="sxs-lookup"><span data-stu-id="b8241-307">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="b8241-308">応答の再試行</span><span class="sxs-lookup"><span data-stu-id="b8241-308">Retrying Replies</span></span>  
 <span data-ttu-id="b8241-309">WCF は、双方向メッセージ交換プロトコルの相関関係の HTTP 要求-応答の相関関係に依存します。</span><span class="sxs-lookup"><span data-stu-id="b8241-309">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="b8241-310">このため、WCF のイニシエーターは停止しません、要求シーケンス メッセージが承認されるときに、要求シーケンス メッセージの再試行ではなくときに、HTTP 応答によって、 `SequenceAcknowledgement`、アプリケーション応答、またはエラー。</span><span class="sxs-lookup"><span data-stu-id="b8241-310">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="b8241-311">WCF レスポンダーは、応答が関連付けられている要求の HTTP 応答で応答を再試行します。</span><span class="sxs-lookup"><span data-stu-id="b8241-311">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="b8241-312">CloseSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-312">CloseSequence Exchange</span></span>  
 <span data-ttu-id="b8241-313">WCF の発信側が送信をすべての応答シーケンス メッセージおよびすべての一方向の要求シーケンス メッセージに対する受信確認を受信した後、 `CloseSequence` 、HTTP 要求で要求シーケンス メッセージし、予想している、 `CloseSequenceResponse` HTTP 応答でします。</span><span class="sxs-lookup"><span data-stu-id="b8241-313">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="b8241-314">要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。</span><span class="sxs-lookup"><span data-stu-id="b8241-314">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="b8241-315">WCF イニシエーターには、応答シーケンスの最終的なが含まれています。 つまり`SequenceAcknowledgement`上、`CloseSequence`メッセージと応答シーケンスがない、`CloseSequence`交換します。</span><span class="sxs-lookup"><span data-stu-id="b8241-315">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="b8241-316">WCF レスポンダーにより、すべての返信は、受信確認を送信、 `CloseSequenceResponse` HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-316">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="b8241-317">TerminateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-317">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="b8241-318">受信後、`CloseSequenceResponse`メッセージ、WCF の発信側の送信、 `TerminateSequence` 、HTTP 要求で要求シーケンス メッセージし、予想している、 `TerminateSequenceResponse` HTTP 応答でします。</span><span class="sxs-lookup"><span data-stu-id="b8241-318">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="b8241-319">`CloseSequence` 交換と同じように、要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。</span><span class="sxs-lookup"><span data-stu-id="b8241-319">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="b8241-320">WCF イニシエーターには、応答シーケンスの最終的なが含まれています。 つまり`SequenceAcknowledgement`上、`TerminateSequence`メッセージと応答シーケンスがない、`TerminateSequence`交換します。</span><span class="sxs-lookup"><span data-stu-id="b8241-320">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="b8241-321">WCF 応答側の送信、 `TerminateSequenceResponse` HTTP 応答でメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b8241-321">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="b8241-322">要求/応答 : アドレス可能なイニシエーター</span><span class="sxs-lookup"><span data-stu-id="b8241-322">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="b8241-323">バインド</span><span class="sxs-lookup"><span data-stu-id="b8241-323">Binding</span></span>  
 <span data-ttu-id="b8241-324">WCF は、2 つを使用して、要求/応答メッセージ交換パターンでのシーケンス受信送信用 HTTP チャネルとします。</span><span class="sxs-lookup"><span data-stu-id="b8241-324">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="b8241-325">このメッセージ交換パターンは、限定された方法で `Duplex, Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b8241-325">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="b8241-326">WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="b8241-326">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="b8241-327">すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8241-327">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="b8241-328">CreateSequence の交換</span><span class="sxs-lookup"><span data-stu-id="b8241-328">CreateSequence Exchange</span></span>  
 <span data-ttu-id="b8241-329">WCF の発信側が送信、 `CreateSequence` 、メッセージ、 `Offer` HTTP 要求での要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-329">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="b8241-330">WCF レスポンダーは、確実、`CreateSequence`が、`Offer`要素のシーケンスを作成し、送信、 `CreateSequenceResponse` 、メッセージ、`Accept`要素。</span><span class="sxs-lookup"><span data-stu-id="b8241-330">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="b8241-331">要求/応答の相関関係</span><span class="sxs-lookup"><span data-stu-id="b8241-331">Request/Reply Correlation</span></span>  
 <span data-ttu-id="b8241-332">次の状況は、すべての相関関係にある要求/応答で発生します。</span><span class="sxs-lookup"><span data-stu-id="b8241-332">The following applies to all correlated requests and replies:</span></span>  
  
-   <span data-ttu-id="b8241-333">WCF により、すべてのアプリケーション要求メッセージ下げ、`ReplyTo`エンドポイント参照と`MessageId`です。</span><span class="sxs-lookup"><span data-stu-id="b8241-333">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   <span data-ttu-id="b8241-334">WCF は、各アプリケーション要求メッセージのとしてローカル エンドポイント参照を適用`ReplyTo`です。</span><span class="sxs-lookup"><span data-stu-id="b8241-334">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="b8241-335">ローカル エンドポイント参照は、イニシエーターの `CreateSequence` メッセージの `ReplyTo` であり、レスポンダーの `CreateSequence` メッセージの `To` です。</span><span class="sxs-lookup"><span data-stu-id="b8241-335">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   <span data-ttu-id="b8241-336">WCF により、その受信要求メッセージ、`MessageId`と`ReplyTo`です。</span><span class="sxs-lookup"><span data-stu-id="b8241-336">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   <span data-ttu-id="b8241-337">WCF により、`ReplyTo`に定義されているすべてのアプリケーション要求メッセージのエンドポイント参照の URI がローカル エンドポイント参照に一致します。</span><span class="sxs-lookup"><span data-stu-id="b8241-337">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   <span data-ttu-id="b8241-338">WCF では、すべての応答が正しい負うことにより、`RelatesTo`と`To`に従ってヘッダー`wsa`要求/応答の相関ルール。</span><span class="sxs-lookup"><span data-stu-id="b8241-338">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
