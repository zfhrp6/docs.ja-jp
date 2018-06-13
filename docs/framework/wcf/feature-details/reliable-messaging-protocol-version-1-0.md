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
# <a name="reliable-messaging-protocol-version-10"></a>信頼できるメッセージング プロトコル バージョン 1.0
このトピックでは、Windows Communication Foundation (WCF) の実装の詳細を説明 Ws-reliable メッセージングの 2005 年 2 月 (バージョン 1.0) プロトコル、HTTP トランスポートを使用して相互運用のために必要です。 WCF では、制約とこのトピックで説明されている説明 Ws-reliablemessaging 仕様に従います。 WS-ReliableMessaging バージョン 1.0 プロトコルは、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 以降に実装されています。  
  
 Ws-reliablemessaging 2005 年 2 月で WCF でプロトコルが実装されている、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>です。  
  
 便宜上、ここでは次のロールを使用します。  
  
-   イニシエーター : WS-Reliable メッセージ シーケンスの作成を開始するクライアント  
  
-   レスポンダー : イニシエーターの要求を受け取るサービス  
  
 このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。  
  
|プレフィックス|名前空間|  
|------------|---------------|  
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>メッセージング  
  
### <a name="sequence-establishment-messages"></a>シーケンス確立メッセージ  
 WCF 実装`CreateSequence`と`CreateSequenceResponse`信頼性の高いメッセージ シーケンスを確立するためにメッセージ。 以下の制約が適用されます。  
  
-   B1101: WCF イニシエーターはのオプションの Expires 要素を生成しません、`CreateSequence`メッセージまたはの場合と、`CreateSequence`メッセージが含まれています、`Offer`要素、省略可能な`Expires`内の要素、`Offer`要素。  
  
-   B1102: にアクセスするとき、`CreateSequence`メッセージ、WCF`Responder`を送信および受信両方`Expires`要素が、存在しますが、値を使用しない場合。  
  
 WS-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構が導入されています。  
  
-   R1103 : `CreateSequence` に `Offer` 要素が含まれている場合、Reliable メッセージング レスポンダーは、シーケンスを受け入れ、`CreateSequenceResponse` 要素を含む `wsrm:Accept` で応答して、相関する 2 つの逆方向シーケンスを形成するか、`CreateSequence` 要求を拒否する必要があります。  
  
-   R1104 : 逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。  
  
-   R1105 : `AcksTo` の `ReplyTo` エンドポイント参照と `CreateSequence` エンドポイント参照には、オクテット単位で一致するアドレス値が必要です。  
  
     WCF 応答側であることを確認の URI 部分、`AcksTo`と`ReplyTo`Epr がシーケンスを作成する前に、と同じです。  
  
-   R1106 : `AcksTo` の `ReplyTo` および `CreateSequence` の各エンドポイント参照は、参照パラメーターの同じセットを持つ必要があります。  
  
     WCF は強制しませんが、想定の [参照パラメーター]`AcksTo`と`ReplyTo`で`CreateSequence`は同一からの参照パラメーターを使用して`ReplyTo`受信確認と逆方向シーケンス メッセージのエンドポイント参照します。  
  
-   R1107 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`ReplyTo` の `CreateSequence` エンドポイント参照に送信される必要があります。  
  
-   R1108 : Offer 機構を使用して 2 つの逆方向シーケンスを確立した場合、`[address]` の `wsrm:AcksTo` 要素の `wsrm:Accept` エンドポイント参照子要素の `CreateSequenceResponse` プロパティは、`CreateSequence` の送信先 URI とバイト単位で一致する必要があります。  
  
-   R1109 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、イニシエーターによって送信されたメッセージとレスポンダーによるメッセージの受信確認は、同じエンドポイント参照に送信される必要があります。  
  
     Ws-reliable メッセージングを使用して、イニシエーターとレスポンダー間で信頼できるセッションを確立するために WCF です。 WCF の Ws-reliablemessaging 実装は、信頼できるセッションが一方向、要求/応答、双方向メッセージ パターンです。 Ws-reliable メッセージング`Offer`機構で`CreateSequence` / `CreateSequenceResponse` 2 つの相関関係を持つ逆方向シーケンスを確立することができ、すべてのメッセージ エンドポイントに適したセッション プロトコルを提供します。 WCF では、セッションのセッションの整合性をエンド ツー エンドの保護などのセキュリティ保証を提供するために現実的では、同じパーティを対象とするメッセージが同じ送信先に到着することを確認します。 また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。 そのため、制約 R1104、R1105、および R1108 は、WCF に適用されます。  
  
 `CreateSequence` メッセージの例を次に示します。  
  
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
  
 `CreateSequenceResponse` メッセージの例を次に示します。  
  
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
  
### <a name="sequence"></a>シーケンス  
 シーケンスに適用される制約を以下に示します。  
  
-   B1201:WCF を生成し、アクセス シーケンス番号より`xs:long`の最大包括値、9223372036854775807 します。  
  
-   B1202:WCF が常にアクション URI を空の本文の最終メッセージを生成のhttp://schemas.xmlsoap.org/ws/2005/02/rm/LastMessageします。  
  
-   B1203: WCF を受け取りを含むシーケンス ヘッダーを持つメッセージを配信する`LastMessage`要素のアクション URI がない限りhttp://schemas.xmlsoap.org/ws/2005/02/rm/LastMessageです。  
  
 シーケンス ヘッダーのサンプル  
  
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
  
### <a name="ackrequested-header"></a>AckRequested ヘッダー  
 WCF を使用して`AckRequested`keep-alive 機構としてヘッダー。 WCF は、省略可能なは生成されません`MessageNumber`要素。 メッセージを受信したときに、`AckRequested`ヘッダーが含まれていますが、`MessageNumber`要素、WCF は無視されます、`MessageNumber`要素の値を次の例で示すようにします。  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement ヘッダー  
 WCF では、Ws-reliablemessaging で提供されるシーケンス受信確認の抱き合わせ機構を使用します。  
  
-   R1401 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、目的の受信者に送信されるアプリケーション メッセージに、`SequenceAcknowledgement` ヘッダーを含めることができます。  
  
-   B1402: と WCF は、シーケンス メッセージを受信する前に受信確認を生成する必要があります (例についてを満たすために、`AckRequested`メッセージ)、WCF は生成、`SequenceAcknowledgement`次の例のように、範囲 0-0 を含むヘッダーをします。  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403: WCF を生成しません`SequenceAcknowledgement`ヘッダーを含む、`Nack`要素がサポートしている`Nack`要素。  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging エラー  
 Ws-reliablemessaging エラーの WCF 実装に適用される制約の一覧を次に示します。  
  
-   B1501: WCF を生成しません`MessageNumberRollover`エラーです。  
  
-   B1502:WCF エンドポイントが生成できる`CreateSequenceRefused`仕様」の説明に従ってエラーが発生します。  
  
-   WCF は、追加生成 B1503:When サービス エンドポイント、接続の上限に達するし、新しい接続を処理することはできません、`CreateSequenceRefused`エラー サブコード`netrm:ConnectionLimitReached`次の例で示すように、します。  
  
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
  
### <a name="ws-addressing-faults"></a>WS-Addressing エラー  
 Ws-reliablemessaging は Ws-addressing が使用するため、WCF Ws-reliablemessaging 実装は、Ws-addressing エラーを生成可能性があります。 このセクションでは、WCF は、Ws-reliablemessaging レイヤーで明示的に生成する Ws-addressing エラーについて説明します。  
  
-   B1601:WCF では、次のいずれかが true の場合、メッセージのアドレス指定ヘッダーに必要なエラーが生成されます。  
  
    -   メッセージに `Sequence` ヘッダーと `Action` ヘッダーがない。  
  
    -   `CreateSequence` メッセージに `MessageId` ヘッダーがない。  
  
    -   `CreateSequence` メッセージに `ReplyTo` ヘッダーがない。  
  
-   B1602:WCF アクションがサポートされていませんエラーを返信で欠落しているメッセージを生成する、`Sequence`ヘッダーがあり、`Action`が Ws-reliablemessaging 仕様で認識されないヘッダー。  
  
-   B1603:WCF がエラーをエンドポイントの検査に基づいて、シーケンスが処理されませんを示すために使用できないエンドポイントを生成、`CreateSequence`メッセージのアドレス指定ヘッダー。  
  
## <a name="protocol-composition"></a>プロトコル コンポジション  
  
### <a name="composition-with-ws-addressing"></a>WS-Addressing によるコンポジション  
 WCF は Ws-addressing の 2 つのバージョンをサポートしています: Ws-addressing 2004/08 [WS-ADDR] と W3C Ws-addressing 1.0 に関する推奨事項 [WS ADDR コア] と [WS ADDR SOAP] です。  
  
 WS-ReliableMessaging 仕様に記載されているのは、WS-Addressing 2004/08 だけですが、使用する WS-Addressing のバージョンが制限されているわけではありません。 WCF に適用される制約の一覧を次に示します。  
  
-   R2101: 両方 Ws-addressing 2004/08 と Ws-addressing 1.0 は、Ws-reliablemessaging で使用できます。  
  
-   指定された Ws-reliablemessaging シーケンスまたは逆方向シーケンスを使用して相関関係のペアの全体で R2102:A 1 つのバージョンの Ws-addressing を使用する必要があります、`wsrm:Offer`メカニズムです。  
  
### <a name="composition-with-soap"></a>SOAP によるコンポジション  
 WCF には、SOAP 1.1 と Ws-reliablemessaging で SOAP 1.2 の両方の使用がサポートされています。  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-Security と WS-SecureConversation によるコンポジション  
 WCF は、Ws-secure Conversation をセキュリティで保護されたトランスポート (HTTPS)、Ws-security によるコンポジション、コンポジションを使用して、Ws-reliablemessaging シーケンスの保護を提供します。 WCF に適用される制約の一覧を次に示します。  
  
-   R2301: 個々 のメッセージの整合性だけでなく、Ws-reliablemessaging シーケンスの整合性と機密性を保護するために WCF に必要な Ws-secureconversation を使用する必要があります。  
  
-   R2302:AWS-Ws-reliablemessaging シーケンスを確立する前にメッセージ交換をセキュリティで保護されたセッションを確立する必要があります。  
  
-   R2303 : WS-ReliableMessaging シーケンスの有効期間が WS-SecureConversation セッションの有効期間よりも長い場合は、対応する WS-SecureConversation Renewal バインディングを使用して、WS-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。  
  
-   B2304:WS-信頼できるメッセージのシーケンスまたは相関逆方向シーケンスのペアは、常に 1 つが Ws-secureconversation セッションにバインドします。  
  
     WCF のソース生成、`wsse:SecurityTokenReference`の要素拡張セクション内の要素、`CreateSequence`メッセージ。  
  
-   Ws-secure Conversation と共に構成 R2305:When、`CreateSequence`メッセージを含める必要があります、`wsse:SecurityTokenReference`要素。  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-ReliableMessaging の WS-Policy アサーション  
 Ws-reliable メッセージングの Ws-policy アサーションを使用する WCF`wsrm:RMAssertion`エンドポイントの機能を記述します。 WCF に適用される制約の一覧を次に示します。  
  
-   B3001: WCF アタッチ`wsrm:RMAssertion`Ws-policy アサーションを`wsdl:binding`要素。 WCF へのアタッチをサポートしている`wsdl:binding`と`wsdl:port`要素。  
  
-   B3002: WCF は Ws-reliablemessaging アサーションの以下の省略可能なプロパティをサポートし、WCF でそれらの制御を提供`ReliableMessagingBindingElement`:  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     次に例を示します。  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>WS-ReliableMessaging のフロー制御拡張  
 WCF では、Ws-reliable Messaging の機能拡張を使用して、追加のオプションの厳密な制御をシーケンス メッセージ フローを提供します。  
  
 フロー制御が有効になって、`ReliableSessionBindingElement`の`FlowControlEnabled``bool`プロパティを`true`です。 WCF に適用される制約の一覧を次に示します。  
  
-   B4001: 信頼できるメッセージング フロー制御を有効にすると、WCF の生成、`netrm:BufferRemaining`内の要素拡張の要素、`SequenceAcknowledgement`ヘッダー。  
  
-   B4002: 信頼できるメッセージング フロー制御を有効にすると、WCF しないため、`netrm:BufferRemaining`に存在する要素`SequenceAcknowledgement`ヘッダーを次の例で示すようにします。  
  
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
  
-   B4003: WCF を使用して`netrm:BufferRemaining`新しいメッセージの数、信頼できるメッセージの送信先を示すためのバッファーに格納できます。  
  
-   B4004: 信頼できるメッセージングを WCF サービスが、信頼できるメッセージング送信先アプリケーションがすぐにメッセージを受信できない場合に送信されるメッセージの数を調整します。 信頼できるメッセージングの送信先がメッセージをバッファーに保持する場合、要素の値が 0 になります。  
  
-   B4005: WCF 生成`netrm:BufferRemaining`整数、0 ~ 4096 の範囲、範囲値を 0 との間の整数値を読み取りますと`xs:int`の`maxInclusive`214748364 の値します。  
  
## <a name="message-exchange-patterns"></a>メッセージ交換パターン  
 Ws-reliable メッセージングは、さまざまなメッセージ交換パターンを使用する場合は、WCF の動作を説明します。 各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。  
  
-   アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。  
  
-   アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。  
  
### <a name="one-way-non-addressable-initiator"></a>一方向 : アドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF には、1 つの HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して RMD から RMS へのすべてのメッセージを送信し、HTTP 応答に、RMS からのすべてメッセージを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`オファーを含まないメッセージです。 WCF レスポンダーは、`CreateSequence`シーケンスを作成する前にオファーがありません。 WCF 応答側に返信すると、`CreateSequence`要求、`CreateSequenceResponse`メッセージ。  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF のイニシエーターを除くすべてのメッセージの返信の受信確認の処理、`CreateSequence`メッセージとエラー メッセージ。 WCF レスポンダーは常に両方のシーケンスへの応答でスタンドアロンの受信確認を生成し、`AckRequested`メッセージ。  
  
#### <a name="terminatesequence-message"></a>TerminateSequence メッセージ  
 WCF の扱い`TerminateSequence`一方向の操作、つまり、HTTP 応答が空の本文と HTTP 202 ステータス コード。  
  
### <a name="one-way-addressable-initiator"></a>一方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF には、1 つのシーケンスでは、受信、送信用 Http チャネルとを使用して、一方向メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`オファーを含まないメッセージです。 WCF レスポンダーは、確実、`CreateSequence`シーケンスを作成する前にオファーがありません。 WCF 応答側の送信、`CreateSequenceResponse`メッセージ、HTTP 要求で対処するための`ReplyTo`エンドポイント参照します。  
  
### <a name="duplex-addressable-initiator"></a>双方向 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF には、受信と送信の HTTP チャネルで 2 つのシーケンスを使用して、完全に非同期の双方向メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`メッセージに提供します。 WCF レスポンダーは、確実、`CreateSequence`シーケンスを作成する前に、プランがします。 WCF が送信、`CreateSequenceResponse`にアドレス指定された HTTP 要求で、`CreateSequence`の`ReplyTo`エンドポイント参照します。  
  
#### <a name="sequence-lifetime"></a>シーケンスの有効期間  
 WCF は、2 つのシーケンスを 1 つの完全な双方向セッションとして処理されます。  
  
 1 つのシーケンスをフォールトするエラーの生成時に、WCF には、リモート エンドポイントに両方のシーケンスをフォールトするが期待しています。 1 つのシーケンスをフォールトするエラーを読み取り、時に WCF フォールトの両方のシーケンス。  
  
 WCF は、送信シーケンスを閉じるし、受信シーケンスでメッセージの処理を継続することができます。 反対に、WCF は、受信シーケンスの終了を処理し、送信シーケンスでメッセージを送信し続けます。  
  
### <a name="request-reply-non-addressable-initiator"></a>要求/応答 : アドレス不可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF は、一方向および要求/応答メッセージ交換パターンを使用して 2 つの 1 つの HTTP チャネルのシーケンスします。 WCF では、HTTP 要求を使用して、要求シーケンスのメッセージを送信して、HTTP 応答を使用して、応答シーケンスのメッセージを送信します。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`メッセージに提供します。 WCF レスポンダーは、確実、`CreateSequence`シーケンスを作成する前に、プランがします。 WCF 応答側に返信すると、`CreateSequence`要求、`CreateSequenceResponse`メッセージ。  
  
#### <a name="one-way-message"></a>一方向のメッセージ  
 一方向メッセージ交換プロトコルを正常に完了するには、WCF 発信側は、HTTP 要求で要求シーケンス メッセージを送信し、受信スタンドアロン`SequenceAcknowledgement`HTTP 応答でメッセージ。 `SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。  
  
 WCF レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードを含む応答を伴う要求に応答できます。  
  
#### <a name="two-way-messages"></a>双方向のメッセージ  
 双方向メッセージ交換プロトコルを正常に完了するは、WCF イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。 応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。  
  
 WCF レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードを含む応答を伴う要求に応答できます。  
  
 一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。  
  
#### <a name="retrying-replies"></a>応答の再試行  
 WCF は、双方向メッセージ交換プロトコルの相関関係の HTTP 要求-応答の相関関係に依存します。 このため、WCF のイニシエーターは停止しません、要求シーケンス メッセージが受信確認が、HTTP 応答によって受信確認、ユーザー メッセージ、または障害時ではなく、要求シーケンス メッセージを再試行しています。 WCF レスポンダーは、応答が関連付けられている要求の HTTP 要求レッグで応答を再試行します。  
  
#### <a name="lastmessage-exchange"></a>LastMessage の交換  
 WCF イニシエーターは、生成し、HTTP 要求レッグで空の本文最終メッセージを送信します。 WCF では、応答が必要ですが、実際の応答メッセージは無視されます。 WCF レスポンダーは、要求シーケンスの空の本文最後のメッセージに応答シーケンスの空の本文最後のメッセージに応答します。  
  
 WCF 応答側がアクション URI がでない最後のメッセージを受け取った場合http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage、最後のメッセージを WCF 添えて応答します。 双方向メッセージ交換プロトコルの場合、最後のメッセージでアプリケーション メッセージが送信されます。一方向メッセージ交換プロトコルの場合、最後のメッセージは空です。  
  
 WCF 応答側では、応答シーケンスの空の本文最後のメッセージの受信確認は必要ありません。  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence の交換  
 WCF のイニシエーターが生成し、要求シーケンスを送信するすべての要求が、有効な応答を受信したときに`TerminateSequence`HTTP 要求レッグでメッセージ。 WCF では、応答が必要ですが、実際の応答メッセージは無視されます。 要求シーケンスに返信すると、WCF レスポンダー`TerminateSequence`応答シーケンスのメッセージ`TerminateSequence`メッセージ。  
  
 通常のシャットダウン シーケンスでは、両方の `TerminateSequence` メッセージで完全な `SequenceAcknowledgement` を送信します。  
  
### <a name="requestreply-addressable-initiator"></a>要求/応答 : アドレス可能なイニシエーター  
  
#### <a name="binding"></a>バインド  
 WCF には、2 つのシーケンスでは、受信、送信用 HTTP チャネルとを使用して要求/応答メッセージ交換パターンが用意されています。 WCF では、HTTP 要求を使用して、すべてのメッセージを送信します。 すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### <a name="createsequence-exchange"></a>CreateSequence の交換  
 WCF のイニシエーターを生成、`CreateSequence`メッセージに提供します。 WCF レスポンダーは、確実、`CreateSequence`シーケンスを作成する前に、プランがします。 WCF が送信、`CreateSequenceResponse`にアドレス指定された HTTP 要求で、`CreateSequence`の`ReplyTo`エンドポイント参照します。  
  
#### <a name="requestreply-correlation"></a>要求/応答の相関関係  
 WCF イニシエーターにより、すべてのアプリケーション要求メッセージ下げ、`MessageId`と`ReplyTo`エンドポイント参照します。 WCF のイニシエーターが適用されます、`CreateSequence`メッセージの`ReplyTo`各アプリケーション要求メッセージのエンドポイント参照します。 WCF レスポンダーは、その受信要求メッセージが必要です、`MessageId`と`ReplyTo`です。 WCF レスポンダーは、両方のエンドポイント参照の URI を提供する、`CreateSequence`とすべてのアプリケーション要求メッセージが同一です。
