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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98fe8ac04b7ac811802466cf63c58ea4cebd791e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-11"></a>信頼できるメッセージング プロトコル バージョン 1.1
ここでは、HTTP トランスポートを使用した相互運用に必要な WS-ReliableMessaging 2007/02 (バージョン 1.1) プロトコルに関する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 実装の詳細について説明します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、ここに記載した制約と説明に基づく WS-ReliableMessaging 仕様に従っています。 以降では、Ws-reliablemessaging 1.1 プロトコルを実装することに注意してください、[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]です。  
  
 WS-ReliableMessaging 2007/02 プロトコルは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] により <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> に実装されます。  
  
 便宜上、ここでは次のロールを使用します。  
  
-   イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント。  
  
-   レスポンダー : イニシエーターの要求を受け取るサービス。  
  
 このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。  
  
|プレフィックス|名前空間|  
|-|-|  
|wsrm|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|秒|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|wsp|(WS-Policy 1.2 または WS-Policy 1.5 のいずれか)|  
  
## <a name="messaging"></a>メッセージング  
  
### <a name="sequence-creation"></a>シーケンスの作成  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、信頼できるメッセージ シーケンスを確立するために、`CreateSequence` メッセージと `CreateSequenceResponse` メッセージを実装します。 以下の制約が適用されます。  
  
-   B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`CreateSequence` メッセージの `ReplyTo`、`AcksTo`、および `Offer/Endpoint` と同じエンドポイント参照を使用します。  
  
-   R1102: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、オクテット単位で一致する同じ文字列表現のアドレス値が必要です。  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`AcksTo`、`ReplyTo`、および `Endpoint` の各エンドポイント参照の URI 部分が同一であるかどうかを検証します。  
  
-   R1103: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、同一の参照パラメーターのセットが必要です。  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`AcksTo` の `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` エンドポイント参照の参照パラメーターが同一であることを強制しません。ただし、これらが同一であることを前提とした上で、`ReplyTo` エンドポイント参照からの参照パラメーターを受信確認と逆方向シーケンス メッセージに使用します。  
  
-   B1104: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`Expires` メッセージでオプションの `Offer/Expires` 要素または `CreateSequence` 要素を生成しません。  
  
-   B1105: `CreateSequence` メッセージにアクセスする場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`Expires` 要素の `CreateSequence` 値を `Expires` 要素の `CreateSequenceResponse` 値として使用します。 それ以外の場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは `Expires` 値および `Offer/Expires` 値を読み込んで無視します。  
  
-   B1106: `CreateSequenceResponse` メッセージにアクセスする場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オプションの `Expires` 値を読み込みますが、使用しません。  
  
-   B1107: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターおよびレスポンダーは、`IncompleteSequenceBehavior` 要素および `CreateSequence/Offer` 要素にオプションの `CreateSequenceResponse` 要素を必ず生成します。  
  
-   B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`DiscardFollowingFirstGap` 要素にある `NoDiscard` 値および `IncompleteSequenceBehavior` 値のみ使用します。  
  
    -   WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構を利用しています。  
  
-   B1109: `CreateSequence` に `Offer` 要素が格納されている場合、一方向 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequenceResponse` 要素なしに `Accept` で応答することにより、用意されたシーケンスを拒否します。  
  
-   B1110: 信頼できるメッセージング レスポンダーが用意されたシーケンスを拒否する場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは新しく確立されたシーケンスをエラーとします。  
  
-   B1111: `CreateSequence` に `Offer` 要素が格納されていない場合、双方向 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequenceRefused` フォールトで応答することにより用意されたシーケンスを拒否します。  
  
-   R1112: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、`[address]` エンドポイント参照の `CreateSequenceResponse/Accept/AcksTo` プロパティは、バイト単位で `CreateSequence` メッセージの送信先 URI と一致する必要があります。  
  
-   R1113: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、イニシエーターからレスポンダーに流れる両方のシーケンスにあるすべてのメッセージは、同じエンドポイント参照に送信される必要があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-ReliableMessaging を使用して、イニシエーターとレスポンダー間で信頼できるセッションを確立します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging 実装により、一方向、要求/応答、双方向の各メッセージ パターンの信頼できるセッションが実現します。 `Offer` および `CreateSequence` で WS-ReliableMessaging の `CreateSequenceResponse` 機構を使用すると、相関する 2 つの逆方向シーケンスを確立できます。また、Offer 機構は、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、セッション整合性を保つためのエンドツーエンドの保護を含むこのようなセッションに対してセキュリティが保証されているため、同じパーティを対象とするメッセージが同じ送信先に到着することが事実上保証されます。 また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。 R1102、R1112、および R1113 の制約に適用するため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]です。  
  
 `CreateSequence` メッセージの例を次に示します。  
  
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
  
 `CreateSequenceResponse` メッセージの例を次に示します。  
  
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
  
### <a name="closing-a-sequence"></a>シーケンスを閉じる  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、信頼できるメッセージの送信元が開始するシャットダウンに `CloseSequence` メッセージおよび `CloseSequenceResponse` メッセージを使用します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信先はシャットダウンを開始せず、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージング送信元は、信頼できるメッセージの送信先が開始するシャットダウンをサポートしません。 以下の制約が適用されます。  
  
-   B1201: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信元は、シーケンスをシャットダウンする場合に、常に `CloseSequence` メッセージを送信します。  
  
-   B1202: 信頼できるメッセージの送信元は、`CloseSequence` メッセージを送信する前に、すべてのシーケンス メッセージの受信確認を待機します。  
  
-   B1203: 信頼できるメッセージの送信元は、シーケンスにメッセージが含まれない場合を除き、常にオプションの `LastMsgNumber` 要素を含めます。  
  
-   R1204: 信頼できるメッセージの送信先は、`CloseSequence` メッセージを送信してシャットダウンを開始することはできません。  
  
-   B1205: `CloseSequence` メッセージを受け取ると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信元はシーケンスが不完全と見なし、エラーを送信します。  
  
 `CloseSequence` メッセージの例を次に示します。  
  
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
  
### <a name="sequence-termination"></a>シーケンスの終了  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`TerminateSequence/TerminateSequenceResponse` ハンドシェイクを完了した後、`CloseSequence/CloseSequenceResponse` ハンドシェイクを主に使用します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信先は終了を開始せず、信頼できるメッセージの送信元は、信頼できるメッセージの送信先が開始する終了をサポートしません。 以下の制約が適用されます。  
  
-   B1301: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`TerminateSequence` ハンドシェイクが正常に完了した後にのみ、`CloseSequence/CloseSequenceResponse` メッセージを送信します。  
  
-   R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`LastMsgNumber` 要素が、各シーケンスのすべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに対し一貫性があることを検証します。 つまり、`LastMsgNumber` は、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在しないか、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在し、同一であるかのいずれかです。  
  
-   B1303: `TerminateSequence` ハンドシェイクの後、`CloseSequence/CloseSequenceResponse` メッセージを受け取ると、信頼できるメッセージの送信先が `TerminateSequenceResponse` メッセージで応答します。 信頼できるメッセージの配信元は、`TerminateSequence` メッセージを送信する前に最終受信確認を受けるため、信頼できるメッセージの送信先ではシーケンスが終了したことが確実にわかり、すぐにリソースを再要求します。  
  
-   B1304: `TerminateSequence` ハンドシェイクの前に、`CloseSequence/CloseSequenceResponse` メッセージを受け取ると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信先が `TerminateSequenceResponse` メッセージで応答します。 信頼できるメッセージの送信先でシーケンスが一貫していると判断した場合、信頼できるメッセージの送信先は、リソースを再要求する前にアプリケーションの送信先で指定された時間待機し、クライアントが最終受信確認を受け取ることができるようにします。 それ以外の場合は、信頼できるメッセージの送信先はすぐにリソースを再要求し、`Faulted` イベントを発生させて、不明なシーケンスの終了をアプリケーションの送信先に示します。  
  
 `TerminateSequence` メッセージの例を次に示します。  
  
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
  
### <a name="sequences"></a>シーケンス  
 シーケンスに適用される制約を以下に示します。  
  
-   B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を生成し、アクセスするシーケンス番号より`xs:long`の最大包括値、9223372036854775807 します。  
  
 `Sequence` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>受信確認の要求  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、Keep-alive 機構として `AckRequested` ヘッダーを使用します。  
  
 `AckRequested` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-ReliableMessaging で用意されているシーケンス受信確認の抱き合わせ機構を使用します。 以下の制約が適用されます。  
  
-   R1601: 2 つの逆方向シーケンスを確立した場合を使用して、`Offer`メカニズム、`SequenceAcknowledgement`目的の受信者に送信アプリケーション メッセージにヘッダーを含めることがあります。 リモートのエンドポイントは、追加された `SequenceAcknowledgement` ヘッダーにアクセスできる必要があります。  
  
-   B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`SequenceAcknowledgement` 要素を含む `Nack` ヘッダーは生成しません。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、各 `Nack` 要素にシーケンス番号が格納されていることを検証しますが、シーケンス番号が格納されていない場合は、`Nack` 要素および値を無視します。  
  
 `SequenceAcknowledgement` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging エラー  
 WS-ReliableMessaging エラーの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 実装に適用される制約を以下に示します。 以下の制約が適用されます。  
  
-   B1701:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を生成しません`MessageNumberRollover`エラーです。  
  
-   B1702: SOAP 1.2 では、サービス エンドポイントが接続制限に達し、新しい接続を処理できない場合、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は入れ子にした `CreateSequenceRefused` エラー サブコード `netrm:ConnectionLimitReached` を生成します。  
  
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
  
### <a name="ws-addressing-faults"></a>WS-Addressing エラー  
 WS-ReliableMessaging は WS-Addressing を使用するため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の WS-ReliableMessaging 実装は、WS-Addressing エラーを生成して送信できます。 ここでは、WS-ReliableMessaging レイヤーで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が明示的に生成および送信する WS-Addressing エラーについて説明します。  
  
-   B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]生成し、送信、`Message Addressing Header Required`エラーに、次のいずれかが true の場合。  
  
    -   `CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `MessageId` ヘッダーがない。  
  
    -   `CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `ReplyTo` ヘッダーがない。  
  
    -   `CreateSequenceResponse`、`CloseSequenceResponse`、または `TerminateSequenceResponse` メッセージに `RelatesTo` ヘッダーがない。  
  
-   B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]生成し、送信、`Endpoint Unavailable`をリッスンしているエンドポイントがないことを示すフォールトでアドレス指定ヘッダーの検査に基づいてシーケンスを処理することができます、`CreateSequence`メッセージ。  
  
## <a name="protocol-composition"></a>プロトコル コンポジション  
  
### <a name="composition-with-ws-addressing"></a>WS-Addressing によるコンポジション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-Addressing の 2 つのバージョンをサポートしています。WS-Addressing 2004/08 [WS-ADDR] と、W3C WS-Addressing 1.0 Recommendation ([WS-ADDR-CORE] および [WS-ADDR-SOAP]) です。  
  
 WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。  
  
-   R2101: WS-Addressing 2004/08 と WS-Addressing 1.0 の両方を WS-ReliableMessaging で使用できます。  
  
-   R2102: 特定の WS-ReliableMessaging シーケンス、または `Offer` 機構を使用して関連付けられた逆方向シーケンスのペアでは、同じバージョンの WS-Addressing を使用する必要があります。  
  
### <a name="composition-with-soap"></a>SOAP によるコンポジション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、WS-ReliableMessaging で SOAP 1.1 と SOAP 1.2 の両方を使用できます。  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-Security と WS-SecureConversation によるコンポジション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、セキュリティで保護されたトランスポート (HTTPS)、WS-Security によるコンポジション、および WS-SecureConversation によるコンポジションを使用して、WS-ReliableMessaging シーケンスを保護します。 WS-ReliableMessaging 1.1 プロトコル、WS-Security 1.1、および WS-Secure Conversation 1.3 プロトコルは一緒に使う必要があります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。  
  
-   R2301: 個々のメッセージの整合性と機密性だけでなく、WS-ReliableMessaging シーケンスの整合性を保護するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では WS-SecureConversation を使用する必要があります。  
  
-   R2302:AWS-Ws-reliablemessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。  
  
-   R2303: WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。  
  
-   B2304:WS-ReliableMessaging シーケンスまたは相関逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。  
  
-   R2305: WS-SecureConversation を使用して構成した場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーでは、`CreateSequence` メッセージに `wsse:SecurityTokenReference` 要素および `wsrm:UsesSequenceSTR` ヘッダーが含まれていることが必要です。  
  
 `UsesSequenceSTR` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>SSL/TLS セッションによるコンポジション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、次のようにSSL/TLS セッションによるコンポジションをサポートしていません。  
  
-   B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsrm:UsesSequenceSSL` ヘッダーを生成しません。  
  
-   R2402: 信頼できるメッセージのイニシエーターは、`CreateSequence` レスポンダーに `wsrm:UsesSequenceSSL` ヘッダーが付いた [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージを送信できません。  
  
### <a name="composition-with-ws-policy"></a>WS-Policy によるコンポジション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-Policy 1.2 および WS-Policy 1.5 の 2 つのバージョンの WS-Policy をサポートしています。  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging の WS-Policy アサーション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-ReliableMessaging の `wsrm:RMAssertion` WS-Policy アサーションを使用して、エンドポイントの機能を記述します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。  
  
-   B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsrmn:RMAssertion` WS-Policy アサーションを `wsdl:binding` 要素にアタッチします。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsdl:binding` 要素および `wsdl:port` 要素へのアタッチをサポートしています。  
  
-   B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsp:Optional` タグを生成しません。  
  
-   B3003: `wsrmp:RMAssertion` WS-Policy アサーションにアクセスする場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `wsp:Optional` タグを無視し、WS-RM ポリシーを必須のポリシーとして使用します。  
  
-   R3004: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は SSL/TLS セッションで構成できないため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `wsrmp:SequenceTransportSecurity` を指定するポリシーを受け付けません。  
  
-   B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、常に `wsrmp:DeliveryAssurance` 要素を生成します。  
  
-   B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は常に `wsrmp:ExactlyOnce` 配信保証を指定します。  
  
-   B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-ReliableMessaging アサーションの以下のプロパティを生成して読み込み、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の `ReliableSessionBindingElement` でこれらのプロパティを制御します。  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     `RMAssertion` の例を次に示します。  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a>WS-ReliableMessaging のフロー制御拡張  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-ReliableMessaging の機能拡張を使用して、シーケンス メッセージ フローのさらに厳密な制御を実現します。  
  
 フロー制御が有効になって、`ReliableSessionBindingElement`の`FlowControlEnabled``boolean`プロパティを`true`です。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。  
  
-   B4001: 信頼できるメッセージング フロー制御を有効にした場合、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `netrm:BufferRemaining` ヘッダーの要素拡張で `SequenceAcknowledgement` 要素を生成します。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: 信頼できるメッセージング フロー制御を有効にした場合でも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では `netrm:BufferRemaining` ヘッダーに `SequenceAcknowledgement` 要素は必要ありません。  
  
-   B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージの送信先は、`netrm:BufferRemaining` を使用して、バッファーに保持できる新しいメッセージの数を示します。  
  
-   B4004:When 信頼できるメッセージング フロー制御が有効になっている、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]信頼できるメッセージング送信元の値を使用して`netrm:BufferRemaining`スロットル メッセージを転送します。  
  
-   B4005 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、0 ～ 4096 の整数値の `netrm:BufferRemaining` を生成し、0 ～ 214748364 (`xs:int` の `maxInclusive` 値) の整数値を読み取ります。  
  
## <a name="message-exchange-patterns"></a>メッセージ交換パターン  
 ここでは、WS-ReliableMessaging をさまざまなメッセージ交換パターンに使用する際の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の動作について説明します。 各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。  
  
-   アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。  
  
-   アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。  
  
### <a name="one-way-non-addressable-initiator"></a>一方向 : アドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、1 つの HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンを提供します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用してイニシエーターからレスポンダーにすべてのメッセージを送信し、HTTP 応答を使用してレスポンダーからイニシエーターにすべてのメッセージを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素のない `Offer` メッセージを転送し、HTTP 応答で `CreateSequenceResponse` メッセージを待機します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成し、HTTP 応答で `CreateSequenceResponse` 要素のない `Accept` メッセージを転送します。  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`CreateSequence` メッセージとエラー メッセージを除くすべてのメッセージの応答で受信確認を処理します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、すべてのシーケンス メッセージと `AckRequested` メッセージへの HTTP 応答として、必ずスタンドアロンの受信確認を転送します。  
  
#### <a name="closesequence-exchange"></a>CloseSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CloseSequence` メッセージを転送し、HTTP 応答で `CreateSequenceResponse` メッセージを待機します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、HTTP 応答で `CloseSequenceResponse` メッセージを転送します。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `TerminateSequence` メッセージを転送し、HTTP 応答で `TerminateSequenceResponse` メッセージを待機します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、HTTP 応答で `TerminateSequenceResponse` メッセージを転送します。  
  
### <a name="one-way-addressable-initiator"></a>一方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信用 HTTP チャネルと送信用 HTTP チャネルで 1 つのシーケンスを使用する、一方向メッセージ交換パターンを提供します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用してすべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素のない `Offer` メッセージを転送します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成し、HTTP 要求で `CreateSequenceResponse` 要素のない `Accept` メッセージを転送します。  
  
### <a name="duplex-addressable-initiator"></a>双方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、受信用 HTTP チャネルと送信用 HTTP チャネルで 2 つのシーケンスを使用する、完全に非同期の双方向メッセージ交換パターンが用意されています。 このメッセージ交換パターンは、限定された方法で `Request/Reply`、`Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用してすべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素のある `Offer` メッセージを転送します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequence` に `Offer` 要素があることを確認し、シーケンスを作成して `CreateSequenceResponse` 要素のない `Accept` メッセージを転送します。  
  
#### <a name="sequence-lifetime"></a>シーケンスの有効期間  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、2 つのシーケンスを 1 つの完全な双方向セッションとして処理します。  
  
 一方のシーケンスをフォールトするエラーが生成されると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、リモート エンドポイントに両方のシーケンスをフォールトするよう要求します。 一方のシーケンスをフォールトするエラーを読み取ると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は両方のシーケンスをフォールトします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、送信シーケンスを終了し、受信シーケンスで引き続きメッセージを処理できます。 逆に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信シーケンスの終了を処理し、送信シーケンスで引き続きメッセージを送信することもできます。  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>要求/応答および一方向のアドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、1 つの HTTP チャネルで 2 つのシーケンスを使用して、一方向の要求/応答メッセージ交換パターンを提供します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用してイニシエーターからレスポンダーにすべてのメッセージを送信し、HTTP 応答を使用してレスポンダーからイニシエーターにすべてのメッセージを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素がある `Offer` メッセージを転送し、HTTP 応答で `CreateSequenceResponse` メッセージを待機します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成し、HTTP 応答で `CreateSequenceResponse` 要素がある `Accept` メッセージを転送します。  
  
#### <a name="one-way-message"></a>一方向のメッセージ  
 一方向メッセージ交換を正常に完了するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答でスタンドアロンの `SequenceAcknowledgement` メッセージを受信します。 `SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードによる応答で要求に応答します。  
  
#### <a name="two-way-messages"></a>双方向のメッセージ  
 双方向メッセージ交換プロトコルを正常に完了するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。 応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードで要求に応答できます。  
  
 一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。  
  
#### <a name="retrying-replies"></a>応答の再試行  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、双方向メッセージ交換プロトコルの相関関係について、HTTP 要求/応答の相関関係に依存しています。 このため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、要求シーケンス メッセージが受信確認されたときではなく、HTTP 応答によって `SequenceAcknowledgement`、アプリケーション応答、またはエラーが送信されたときに、要求シーケンス メッセージの再試行を停止します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答が関連付けられている要求の HTTP 要求で応答を再試行します。  
  
#### <a name="closesequence-exchange"></a>CloseSequence の交換  
 すべての一方向の要求シーケンス メッセージが、すべての応答シーケンス メッセージおよび受信確認を受信した後、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンスに `CloseSequence` メッセージを転送し、HTTP 応答で `CloseSequenceResponse` を待機します。  
  
 要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。 つまり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`SequenceAcknowledgement` メッセージに応答シーケンスの最終的な `CloseSequence` を含め、応答シーケンスには `CloseSequence` 交換がありません。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、すべての応答が受信確認されたことを確認し、HTTP 応答で `CloseSequenceResponse` メッセージを転送します。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence の交換  
 `CloseSequenceResponse` メッセージを受け取った後、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは HTTP 要求で要求シーケンスに `TerminateSequence` メッセージを転送し、HTTP 応答で `TerminateSequenceResponse` を待機します。  
  
 `CloseSequence` 交換と同じように、要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。 つまり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`SequenceAcknowledgement` メッセージに応答シーケンスの最終的な `TerminateSequence` を含め、応答シーケンスには `TerminateSequence` 交換がありません。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、HTTP 応答で `TerminateSequenceResponse` メッセージを転送します。  
  
### <a name="requestreply-addressable-initiator"></a>要求/応答 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、受信用 HTTP チャネルと送信用 HTTP チャネルで 2 つのシーケンスを使用する、要求/応答メッセージ交換パターンが用意されています。 このメッセージ交換パターンは、限定された方法で `Duplex, Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用してすべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で `CreateSequence` 要素のある `Offer` メッセージを転送します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequence` に `Offer` 要素があることを確認し、シーケンスを作成して `CreateSequenceResponse` 要素がある `Accept` メッセージを転送します。  
  
#### <a name="requestreply-correlation"></a>要求/応答の相関関係  
 次の状況は、すべての相関関係にある要求/応答で発生します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、すべてのアプリケーション要求メッセージに `ReplyTo` エンドポイント参照と `MessageId` が保持されていることを確認します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、各アプリケーション要求メッセージの `ReplyTo` としてローカル エンドポイント参照を適用します。 ローカル エンドポイント参照は、イニシエーターの `CreateSequence` メッセージの `ReplyTo` であり、レスポンダーの `CreateSequence` メッセージの `To` です。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信要求メッセージに `MessageId` と `ReplyTo` が保持されていることを確認します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、すべてのアプリケーション要求メッセージの `ReplyTo` エンドポイント参照の URI が、先に定義したローカル エンドポイント参照と一致していることを確認します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`RelatesTo` 要求/応答の相関ルールに従い、すべての応答に正しい `To` ヘッダーおよび `wsa` ヘッダーが保持されていることを確認します。
