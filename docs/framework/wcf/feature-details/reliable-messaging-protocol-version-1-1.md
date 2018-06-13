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
# <a name="reliable-messaging-protocol-version-11"></a>信頼できるメッセージング プロトコル バージョン 1.1
このトピックでは、Windows Communication Foundation (WCF) の実装の詳細を説明の Ws-reliablemessaging 2007/02 (バージョン 1.1) プロトコルは HTTP トランスポートを使用して相互運用のために必要なです。 WCF では、制約とこのトピックで説明した説明は、Ws-reliablemessaging 仕様に従います。 以降では、Ws-reliablemessaging 1.1 プロトコルを実装することに注意してください、[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]です。  
  
 Ws-reliablemessaging 2007/02 プロトコルは、WCF で実装されて、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>です。  
  
 便宜上、ここでは次のロールを使用します。  
  
-   イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント。  
  
-   レスポンダー : イニシエーターの要求を受け取るサービス。  
  
 このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。  
  
|プレフィックス|名前空間|  
|-|-|  
|wsrm|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|wsp|(WS-Policy 1.2 または WS-Policy 1.5 のいずれか)|  
  
## <a name="messaging"></a>メッセージング  
  
### <a name="sequence-creation"></a>シーケンスの作成  
 WCF 実装`CreateSequence`と`CreateSequenceResponse`信頼できるメッセージングを確立するためにメッセージのシーケンスします。 以下の制約が適用されます。  
  
-   B1101: WCF イニシエーターを使用して、同じエンドポイント参照として、`CreateSequence`メッセージの`ReplyTo`、`AcksTo`と`Offer/Endpoint`です。  
  
-   R1102: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、オクテット単位で一致する同じ文字列表現のアドレス値が必要です。  
  
    -   WCF 応答側であることを確認の URI 部分、 `AcksTo`、`ReplyTo`と`Endpoint`シーケンスを作成する前に、エンドポイント参照は同じです。  
  
-   R1103: `AcksTo` メッセージの `ReplyTo`、`Offer/Endpoint`、および `CreateSequence` の各エンドポイント参照には、同一の参照パラメーターのセットが必要です。  
  
    -   WCF は強制されませんが、その参照を前提としていますのパラメーター、 `AcksTo`、`ReplyTo`と`Offer/Endpoint`エンドポイント参照に`CreateSequence`が同じパラメーターを使用する参照から、`ReplyTo`エンドポイント参照の受信確認と逆方向シーケンス メッセージ。  
  
-   B1104: WCF イニシエーターを生成しません、省略可能な`Expires`または`Offer/Expires`内の要素、`CreateSequence`メッセージ。  
  
-   B1105: にアクセスするとき、 `CreateSequence` WCF レスポンダーは、メッセージ、`Expires`値で、`CreateSequence`要素として、`Expires`値で、`CreateSequenceResponse`要素。 それ以外の場合、WCF レスポンダーを読み込んで、無視、`Expires`と`Offer/Expires`値。  
  
-   B1106: にアクセスするとき、`CreateSequenceResponse`メッセージ、WCF イニシエーターは、省略可能な読み取り`Expires`値は使用しません。  
  
-   B1107: WCF イニシエーターおよびレスポンダーは常に生成、省略可能な`IncompleteSequenceBehavior`内の要素、`CreateSequence/Offer`と`CreateSequenceResponse`要素。  
  
-   B1108: WCF のみ使用する、`DiscardFollowingFirstGap`と`NoDiscard`の値が、`IncompleteSequenceBehavior`要素。  
  
    -   WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構を利用しています。  
  
-   B1109: 場合`CreateSequence`が含まれています、`Offer`要素、一方向の WCF レスポンダーを拒否、用意されたシーケンスで応答して、`CreateSequenceResponse`せず、`Accept`要素。  
  
-   B1110: 信頼できるメッセージング レスポンダーは、用意されたシーケンスを拒否する場合、新たに確立されたシーケンスが違反 WCF イニシエーター。  
  
-   B1111: 場合`CreateSequence`が含まれていない、`Offer`要素、双方向の WCF レスポンダーを拒否、用意されたシーケンスで応答して、`CreateSequenceRefused`フォールトします。  
  
-   R1112: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、`[address]` エンドポイント参照の `CreateSequenceResponse/Accept/AcksTo` プロパティは、バイト単位で `CreateSequence` メッセージの送信先 URI と一致する必要があります。  
  
-   R1113: 2 つの逆方向シーケンスが `Offer` 機構を使用して確立された場合、イニシエーターからレスポンダーに流れる両方のシーケンスにあるすべてのメッセージは、同じエンドポイント参照に送信される必要があります。  
  
 WCF では、Ws-reliablemessaging を使用して、イニシエーターとレスポンダー間で信頼できるセッションを確立します。 WCF の Ws-reliablemessaging 実装では、一方向、要求/応答、信頼できるセッションは、双方向メッセージ パターンです。 `Offer` および `CreateSequence` で WS-ReliableMessaging の `CreateSequenceResponse` 機構を使用すると、相関する 2 つの逆方向シーケンスを確立できます。また、Offer 機構は、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。 WCF では、セッションのセッションの整合性をエンド ツー エンドの保護などのセキュリティ保証を提供するために現実的では、同じパーティを対象とするメッセージが同じ送信先に到達することを確認します。 また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。 したがって、R1102、R1112、および R1113 制約は、WCF に適用されます。  
  
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
 WCF を使用して、`CloseSequence`と`CloseSequenceResponse`信頼性の高いメッセージング ソースによって開始されたシャット ダウンのメッセージ。 WCF の信頼できるメッセージの送信先はシャット ダウンを開始していないと、WCF の信頼できるメッセージの送信元が信頼できるメッセージング送信先が開始シャット ダウンをサポートしていません。 以下の制約が適用されます。  
  
-   B1201: WCF の信頼できるメッセージの送信元は常に送信する`CloseSequence`メッセージ シーケンスをシャット ダウンします。  
  
-   B1202: 信頼できるメッセージの送信元は、`CloseSequence` メッセージを送信する前に、すべてのシーケンス メッセージの受信確認を待機します。  
  
-   B1203: 信頼できるメッセージの送信元は、シーケンスにメッセージが含まれない場合を除き、常にオプションの `LastMsgNumber` 要素を含めます。  
  
-   R1204: 信頼できるメッセージの送信先は、`CloseSequence` メッセージを送信してシャットダウンを開始することはできません。  
  
-   : B1205`CloseSequence`メッセージ、WCF の信頼できるメッセージの送信元は不完全な順序を考慮し、エラーが送信されます。  
  
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
 WCF を使用して、主に、`TerminateSequence/TerminateSequenceResponse`ハンドシェイクが完了した後、`CloseSequence/CloseSequenceResponse`ハンドシェイクです。 WCF の信頼できるメッセージの送信先は終了を開始していないと、信頼できるメッセージの送信元が信頼できるメッセージング送信先が開始終了をサポートしていません。 以下の制約が適用されます。  
  
-   B1301: WCF にイニシエーターのみ送信、`TerminateSequence`メッセージが正常に完了した後、`CloseSequence/CloseSequenceResponse`ハンドシェイクです。  
  
-   R1302: WCF を検証する、`LastMsgNumber`要素がすべてにわたって一貫性のある`CloseSequence`と`TerminateSequence`と指定されたシーケンスのメッセージ。 つまり、`LastMsgNumber` は、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在しないか、すべての `CloseSequence` メッセージおよび `TerminateSequence` メッセージに存在し、同一であるかのいずれかです。  
  
-   B1303: `TerminateSequence` ハンドシェイクの後、`CloseSequence/CloseSequenceResponse` メッセージを受け取ると、信頼できるメッセージの送信先が `TerminateSequenceResponse` メッセージで応答します。 信頼できるメッセージの配信元は、`TerminateSequence` メッセージを送信する前に最終受信確認を受けるため、信頼できるメッセージの送信先ではシーケンスが終了したことが確実にわかり、すぐにリソースを再要求します。  
  
-   B1304: 受信するときに、`TerminateSequence`メッセージの前に、`CloseSequence/CloseSequenceResponse`ハンドシェイクで、WCF の信頼できるメッセージの送信先が応答、`TerminateSequenceResponse`メッセージ。 信頼できるメッセージの送信先でシーケンスが一貫していると判断した場合、信頼できるメッセージの送信先は、リソースを再要求する前にアプリケーションの送信先で指定された時間待機し、クライアントが最終受信確認を受け取ることができるようにします。 それ以外の場合は、信頼できるメッセージの送信先はすぐにリソースを再要求し、`Faulted` イベントを発生させて、不明なシーケンスの終了をアプリケーションの送信先に示します。  
  
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
  
-   B1401:WCF を生成し、アクセス シーケンス番号より`xs:long`の最大包括値、9223372036854775807 します。  
  
 `Sequence` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>受信確認の要求  
 WCF を使用して、 `AckRequested` keep-alive 機構としてヘッダー。  
  
 `AckRequested` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF では、Ws-reliablemessaging で提供されるシーケンス受信確認の「抱き合わせ」機構を使用します。 以下の制約が適用されます。  
  
-   R1601: 2 つの逆方向シーケンスを確立した場合を使用して、`Offer`メカニズム、`SequenceAcknowledgement`目的の受信者に送信アプリケーション メッセージにヘッダーを含めることがあります。 リモートのエンドポイントは、追加された `SequenceAcknowledgement` ヘッダーにアクセスできる必要があります。  
  
-   B1602: WCF を生成しません`SequenceAcknowledgement`ヘッダーを含む`Nack`要素。 WCF は、その各検証`Nack`要素は、シーケンス番号が含まれていますが、それ以外の場合は無視されます、`Nack`要素と値。  
  
 `SequenceAcknowledgement` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging エラー  
 Ws-reliablemessaging エラーの WCF 実装に適用される制約の一覧を次に示します。 以下の制約が適用されます。  
  
-   B1701: WCF を生成しません`MessageNumberRollover`エラーです。  
  
-   B1702: SOAP 1.2 では、経由で、サービス エンドポイントが、接続の上限に達するし、新しい接続を処理できないときに WCF 生成、入れ子になった`CreateSequenceRefused`エラー サブコード`netrm:ConnectionLimitReached`の次の例に示すようにします。  
  
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
 Ws-reliablemessaging は Ws-addressing を使用するため WCF Ws-reliablemessaging 実装を生成して Ws-addressing エラーを送信する可能性があります。 このセクションでは、WCF は、明示的に生成し、Ws-reliablemessaging レイヤーで送信する Ws-addressing エラーについて説明します。  
  
-   B1801:WCF が生成し、送信、`Message Addressing Header Required`エラーに、次のいずれかが true の場合。  
  
    -   `CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `MessageId` ヘッダーがない。  
  
    -   `CreateSequence`、`CloseSequence`、または `TerminateSequence` メッセージに `ReplyTo` ヘッダーがない。  
  
    -   `CreateSequenceResponse`、`CloseSequenceResponse`、または `TerminateSequenceResponse` メッセージに `RelatesTo` ヘッダーがない。  
  
-   B1802:WCF が生成し、送信、`Endpoint Unavailable`をリッスンしているエンドポイントがないことを示すフォールトでアドレス指定ヘッダーの検査に基づいてシーケンスを処理することができます、`CreateSequence`メッセージ。  
  
## <a name="protocol-composition"></a>プロトコル コンポジション  
  
### <a name="composition-with-ws-addressing"></a>WS-Addressing によるコンポジション  
 WCF は Ws-addressing の 2 つのバージョンをサポートしています: Ws-addressing 2004/08 [WS-ADDR] と W3C Ws-addressing 1.0 に関する推奨事項 [WS ADDR コア] と [WS ADDR SOAP] です。  
  
 WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。 WCF に適用される制約の一覧を次に示します。  
  
-   R2101: WS-Addressing 2004/08 と WS-Addressing 1.0 の両方を WS-ReliableMessaging で使用できます。  
  
-   R2102: 特定の WS-ReliableMessaging シーケンス、または `Offer` 機構を使用して関連付けられた逆方向シーケンスのペアでは、同じバージョンの WS-Addressing を使用する必要があります。  
  
### <a name="composition-with-soap"></a>SOAP によるコンポジション  
 WCF には、SOAP 1.1 と Ws-reliablemessaging で SOAP 1.2 の両方の使用がサポートされています。  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-Security と WS-SecureConversation によるコンポジション  
 WCF では、Ws-secure Conversation をセキュリティで保護されたトランスポート (HTTPS)、Ws-security によるコンポジション、コンポジションを使用して、Ws-reliablemessaging シーケンスの保護を提供します。 WS-ReliableMessaging 1.1 プロトコル、WS-Security 1.1、および WS-Secure Conversation 1.3 プロトコルは一緒に使う必要があります。 WCF に適用される制約の一覧を次に示します。  
  
-   R2301: 個々 のメッセージの整合性だけでなく、Ws-reliablemessaging シーケンスの整合性と機密性を保護するために WCF に必要な Ws-secureconversation を使用する必要があります。  
  
-   R2302:AWS-Ws-reliablemessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。  
  
-   R2303: WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。  
  
-   B2304:WS-ReliableMessaging シーケンスまたは相関逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。  
  
-   R2305: Ws-secureconversation、構成した場合、WCF レスポンダーする必要があります、`CreateSequence`メッセージが含まれて、`wsse:SecurityTokenReference`要素および`wsrm:UsesSequenceSTR`ヘッダー。  
  
 `UsesSequenceSTR` ヘッダーの例を次に示します。  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>SSL/TLS セッションによるコンポジション  
 WCF は、SSL/TLS セッションによるコンポジションをサポートしていません。  
  
-   B2401: WCF を生成しません、`wsrm:UsesSequenceSSL`ヘッダー。  
  
-   R2402: 信頼できるメッセージングの発信側が送信する必要があります、 `CreateSequence` 、メッセージ、 `wsrm:UsesSequenceSSL` WCF レスポンダーにヘッダー。  
  
### <a name="composition-with-ws-policy"></a>WS-Policy によるコンポジション  
 WCF Ws-policy の 2 つのバージョンでサポートされる: Ws-policy 1.2 および Ws-policy 1.5 です。  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging の WS-Policy アサーション  
 Ws-reliablemessaging の Ws-policy アサーションを使用する WCF`wsrm:RMAssertion`エンドポイントの機能を記述します。 WCF に適用される制約の一覧を次に示します。  
  
-   B3001: WCF アタッチ`wsrmn:RMAssertion`Ws-policy アサーションを`wsdl:binding`要素。 WCF へのアタッチをサポートしている`wsdl:binding`と`wsdl:port`要素。  
  
-   B3002: WCF では生成されません、`wsp:Optional`タグ。  
  
-   B3003: にアクセスするとき、 `wsrmp:RMAssertion` Ws-policy アサーション、WCF は無視されます、`wsp:Optional`タグ、および、WS-RM ポリシーを必須として扱われます。  
  
-   R3004: ため、WCF は、SSL/TLS セッションでは構成は、WCF は受け入れませんを指定するポリシー`wsrmp:SequenceTransportSecurity`です。  
  
-   B3005: WCF は常に生成、`wsrmp:DeliveryAssurance`要素。  
  
-   B3006: WCF は常を指定します、`wsrmp:ExactlyOnce`配信が保証されます。  
  
-   B3007: WCF が生成されます、Ws-reliablemessaging アサーションの以下のプロパティを読み取るし、WCF の上にコントロールを提供`ReliableSessionBindingElement`:  
  
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
 WCF では、Ws-reliablemessaging の機能拡張を使用して、追加のオプションの厳密な制御をシーケンス メッセージ フローを提供します。  
  
 フロー制御が有効になって、`ReliableSessionBindingElement`の`FlowControlEnabled``boolean`プロパティを`true`です。 WCF に適用される制約の一覧を次に示します。  
  
-   B4001: 信頼できるメッセージング フロー制御を有効にすると、WCF の生成、`netrm:BufferRemaining`内の要素拡張の要素、`SequenceAcknowledgement`ヘッダーを次の例で示すようにします。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: 信頼できるメッセージング フロー制御が有効になっている場合でも WCF しないため、`netrm:BufferRemaining`内の要素、`SequenceAcknowledgement`ヘッダー。  
  
-   B4003: 信頼できるメッセージの送信先を WCF を使用して`netrm:BufferRemaining`を示す新しいメッセージの数がのバッファーに格納できます。  
  
-   B4004:When 信頼できるメッセージング フロー制御が有効になっている、信頼できるメッセージングを WCF ソースの値が使用`netrm:BufferRemaining`スロットル メッセージを転送します。  
  
-   B4005: WCF 生成`netrm:BufferRemaining`整数、0 ~ 4096 の範囲、範囲値を 0 との間の整数値を読み取りますと`xs:int`の`maxInclusive`214748364 の値します。  
  
## <a name="message-exchange-patterns"></a>メッセージ交換パターン  
 このセクションでは、Ws-reliablemessaging をさまざまなメッセージ交換パターンに使用すると、WCF の動作がについて説明します。 各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。  
  
-   アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。  
  
-   アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。  
  
### <a name="one-way-non-addressable-initiator"></a>一方向 : アドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF には、1 つの HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して、すべてのメッセージ、イニシエーターからレスポンダーおよび HTTP 応答にレスポンダーからイニシエーターにすべてのメッセージを送信するを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側の送信、`CreateSequence`のないメッセージ`Offer`、HTTP 要求で要素と予想している、 `CreateSequenceResponse` HTTP 応答でメッセージ。 WCF レスポンダーは、シーケンスを作成し、転送、`CreateSequenceResponse`のないメッセージ`Accept`HTTP 応答での要素。  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF のイニシエーターを除くすべてのメッセージの返信の受信確認の処理、`CreateSequence`メッセージとエラー メッセージ。 WCF 応答側が常にすべてのシーケンスに、HTTP 応答でスタンドアロンの受信確認を送信し、`AckRequested`メッセージ。  
  
#### <a name="closesequence-exchange"></a>CloseSequence の交換  
 WCF の発信側の送信、 `CloseSequence` 、HTTP 要求でメッセージを期待、 `CreateSequenceResponse` HTTP 応答でメッセージ。 WCF 応答側の送信、 `CloseSequenceResponse` HTTP 応答でメッセージ。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence の交換  
 WCF の発信側の送信、 `TerminateSequence` 、HTTP 要求でメッセージを期待、 `TerminateSequenceResponse` HTTP 応答でメッセージ。 WCF 応答側の送信、 `TerminateSequenceResponse` HTTP 応答でメッセージ。  
  
### <a name="one-way-addressable-initiator"></a>一方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF には、いずれか 1 つのシーケンスを使用して、一方向メッセージ交換パターンが用意されています受信送信用 HTTP チャネルとします。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側の送信、`CreateSequence`のないメッセージ`Offer`HTTP 要求での要素。 WCF レスポンダーは、シーケンスを作成し、転送、`CreateSequenceResponse`のないメッセージ`Accept`HTTP 要求での要素。  
  
### <a name="duplex-addressable-initiator"></a>双方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF は、2 つを使用して、完全に非同期の双方向メッセージ交換パターンでのシーケンス受信送信用 HTTP チャネルとします。 このメッセージ交換パターンは、限定された方法で `Request/Reply`、`Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側が送信、 `CreateSequence` 、メッセージ、 `Offer` HTTP 要求での要素。 WCF レスポンダーは、確実、`CreateSequence`が、`Offer`要素のシーケンスを作成し、送信、 `CreateSequenceResponse` 、メッセージ、`Accept`要素。  
  
#### <a name="sequence-lifetime"></a>シーケンスの有効期間  
 WCF は、2 つのシーケンスを 1 つの完全な双方向セッションとして処理されます。  
  
 1 つのシーケンスをフォールトするエラーの生成時に、WCF には、リモート エンドポイントに両方のシーケンスをフォールトするが期待しています。 1 つのシーケンスをフォールトするエラーを読み取り、時に WCF フォールトの両方のシーケンス。  
  
 WCF は、送信シーケンスを閉じるし、受信シーケンスでメッセージの処理を継続することができます。 反対に、WCF は、受信シーケンスの終了を処理し、送信シーケンスでメッセージを送信し続けます。  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>要求/応答および一方向のアドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF は、一方向および要求/応答メッセージ交換パターンを使用して 2 つの 1 つの HTTP チャネルのシーケンスします。 WCF では、HTTP 要求を使用して、すべてのメッセージ、イニシエーターからレスポンダーおよび HTTP 応答にレスポンダーからイニシエーターにすべてのメッセージを送信するを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側の送信、`CreateSequence`メッセージを`Offer`、HTTP 要求で要素と予想している、 `CreateSequenceResponse` HTTP 応答でメッセージ。 WCF レスポンダーは、シーケンスを作成し、転送、 `CreateSequenceResponse` 、メッセージ、 `Accept` HTTP 応答での要素。  
  
#### <a name="one-way-message"></a>一方向のメッセージ  
 一方向メッセージ交換を正常に完了するには、WCF 発信側は、HTTP 要求で要求シーケンス メッセージを送信し、受信スタンドアロン`SequenceAcknowledgement`HTTP 応答でメッセージ。 `SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。  
  
 WCF レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードを含む応答を伴う要求に応答します。  
  
#### <a name="two-way-messages"></a>双方向のメッセージ  
 双方向メッセージ交換プロトコルを正常に完了するは、WCF イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。 応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。  
  
 WCF レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードを含む応答を伴う要求に応答します。  
  
 一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。  
  
#### <a name="retrying-replies"></a>応答の再試行  
 WCF は、双方向メッセージ交換プロトコルの相関関係の HTTP 要求-応答の相関関係に依存します。 このため、WCF のイニシエーターは停止しません、要求シーケンス メッセージが承認されるときに、要求シーケンス メッセージの再試行ではなくときに、HTTP 応答によって、 `SequenceAcknowledgement`、アプリケーション応答、またはエラー。 WCF レスポンダーは、応答が関連付けられている要求の HTTP 応答で応答を再試行します。  
  
#### <a name="closesequence-exchange"></a>CloseSequence の交換  
 WCF の発信側が送信をすべての応答シーケンス メッセージおよびすべての一方向の要求シーケンス メッセージに対する受信確認を受信した後、 `CloseSequence` 、HTTP 要求で要求シーケンス メッセージし、予想している、 `CloseSequenceResponse` HTTP 応答でします。  
  
 要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。 WCF イニシエーターには、応答シーケンスの最終的なが含まれています。 つまり`SequenceAcknowledgement`上、`CloseSequence`メッセージと応答シーケンスがない、`CloseSequence`交換します。  
  
 WCF レスポンダーにより、すべての返信は、受信確認を送信、 `CloseSequenceResponse` HTTP 応答でメッセージ。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence の交換  
 受信後、`CloseSequenceResponse`メッセージ、WCF の発信側の送信、 `TerminateSequence` 、HTTP 要求で要求シーケンス メッセージし、予想している、 `TerminateSequenceResponse` HTTP 応答でします。  
  
 `CloseSequence` 交換と同じように、要求シーケンスを終了すると、暗黙的に応答シーケンスが終了します。 WCF イニシエーターには、応答シーケンスの最終的なが含まれています。 つまり`SequenceAcknowledgement`上、`TerminateSequence`メッセージと応答シーケンスがない、`TerminateSequence`交換します。  
  
 WCF 応答側の送信、 `TerminateSequenceResponse` HTTP 応答でメッセージ。  
  
### <a name="requestreply-addressable-initiator"></a>要求/応答 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF は、2 つを使用して、要求/応答メッセージ交換パターンでのシーケンス受信送信用 HTTP チャネルとします。 このメッセージ交換パターンは、限定された方法で `Duplex, Addressable` イニシエーター メッセージ交換パターンに組み込むことができます。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF の発信側が送信、 `CreateSequence` 、メッセージ、 `Offer` HTTP 要求での要素。 WCF レスポンダーは、確実、`CreateSequence`が、`Offer`要素のシーケンスを作成し、送信、 `CreateSequenceResponse` 、メッセージ、`Accept`要素。  
  
#### <a name="requestreply-correlation"></a>要求/応答の相関関係  
 次の状況は、すべての相関関係にある要求/応答で発生します。  
  
-   WCF により、すべてのアプリケーション要求メッセージ下げ、`ReplyTo`エンドポイント参照と`MessageId`です。  
  
-   WCF は、各アプリケーション要求メッセージのとしてローカル エンドポイント参照を適用`ReplyTo`です。 ローカル エンドポイント参照は、イニシエーターの `CreateSequence` メッセージの `ReplyTo` であり、レスポンダーの `CreateSequence` メッセージの `To` です。  
  
-   WCF により、その受信要求メッセージ、`MessageId`と`ReplyTo`です。  
  
-   WCF により、`ReplyTo`に定義されているすべてのアプリケーション要求メッセージのエンドポイント参照の URI がローカル エンドポイント参照に一致します。  
  
-   WCF では、すべての応答が正しい負うことにより、`RelatesTo`と`To`に従ってヘッダー`wsa`要求/応答の相関ルール。
