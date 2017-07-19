---
title: "信頼できるメッセージング プロトコル バージョン 1.0 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 信頼できるメッセージング プロトコル バージョン 1.0
ここでは、HTTP トランスポートを使用した相互運用に必要な WS\-ReliableMessaging 2005\/02 \(バージョン 1.0\) プロトコルに関する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 実装の詳細について説明します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、ここに記載した制約と説明に基づく WS\-ReliableMessaging 仕様に従っています。WS\-ReliableMessaging バージョン 1.0 プロトコルは、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 以降に実装されています。  
  
 WS\-ReliableMessaging 2005\/02 プロトコルは、<xref:System.ServiceModel.Channels.ReliableSessionBindingElement> によって [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に実装されます。  
  
 便宜上、ここでは次のロールを使用します。  
  
-   イニシエーター : WS\-Reliable メッセージ シーケンスの作成を開始するクライアント  
  
-   レスポンダー : イニシエーターの要求を受け取るサービス  
  
 このドキュメントでは、次の表に示すプレフィックスと名前空間を使用します。  
  
|プレフィックス|名前空間|  
|-------------|----------|  
|wsrm|http:\/\/schemas.xmlsoap.org\/ws\/2005\/02\/rm|  
|netrm|http:\/\/schemas.microsoft.com\/ws\/2006\/05\/rm|  
|s|http:\/\/www.w3.org\/2003\/05\/soap\-envelope|  
|wsa|http:\/\/schemas.xmlsoap.org\/ws\/2005\/08\/addressing|  
|wsse|http:\/\/docs.oasis\-open.org\/wss\/2004\/01\/oasis\-200401\-wssecurity\-secext\-1.0.xsd|  
  
## メッセージング  
  
### シーケンス確立メッセージ  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、信頼性の高いメッセージ シーケンスを確立するために、`CreateSequence` メッセージと `CreateSequenceResponse` メッセージを実装しています。以下の制約が適用されます。  
  
-   B1101 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`CreateSequence` メッセージのオプションの Expires 要素を生成しません。また、`CreateSequence` メッセージに `Offer` 要素が含まれているときに、この `Offer` 要素内のオプションの `Expires` 要素も生成しません。  
  
-   B1102 : `CreateSequence` メッセージのアクセス時に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`Responder` は、両方の `Expires` 要素を送受信しますが \(存在する場合\)、値は使用しません。  
  
 WS\-ReliableMessaging では、セッションを形成する、相関する 2 つの逆方向シーケンスを確立するために、`Offer` 機構が導入されています。  
  
-   R1103 : `CreateSequence` に `Offer` 要素が含まれている場合、Reliable メッセージング レスポンダーは、シーケンスを受け入れ、`wsrm:Accept` 要素を含む `CreateSequenceResponse` で応答して、相関する 2 つの逆方向シーケンスを形成するか、`CreateSequence` 要求を拒否する必要があります。  
  
-   R1104 : 逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`CreateSequence` の `ReplyTo` エンドポイント参照に送信される必要があります。  
  
-   R1105 : `CreateSequence` の `AcksTo` エンドポイント参照と `ReplyTo` エンドポイント参照には、オクテット単位で一致するアドレス値が必要です。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`AcksTo` EPR と `ReplyTo` EPR の URI 部分が同一であるかどうかを検証します。  
  
-   R1106 : `CreateSequence` の `AcksTo` および `ReplyTo` の各エンドポイント参照は、参照パラメーターの同じセットを持つ必要があります。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`CreateSequence` の `AcksTo` と `ReplyTo` の \[参照パラメーター\] が同一であることを強制するわけではありません。ただし、これらが同一であると想定した上で、受信確認と逆方向シーケンス メッセージに `ReplyTo` エンドポイント参照の \[参照パラメーター\] を使用します。  
  
-   R1107 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、逆方向シーケンスでフローする `SequenceAcknowledgement` およびアプリケーション メッセージは、`CreateSequence` の `ReplyTo` エンドポイント参照に送信される必要があります。  
  
-   R1108 : Offer 機構を使用して 2 つの逆方向シーケンスを確立した場合、`CreateSequenceResponse` の `wsrm:Accept` 要素の `wsrm:AcksTo` エンドポイント参照子要素の `[address]` プロパティは、`CreateSequence` の送信先 URI とバイト単位で一致する必要があります。  
  
-   R1109 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、イニシエーターによって送信されたメッセージとレスポンダーによるメッセージの受信確認は、同じエンドポイント参照に送信される必要があります。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS\-ReliableMessaging を使用して、イニシエーターとレスポンダー間で信頼性できるセッションを確立します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の WS\-ReliableMessaging 実装により、一方向、要求\/応答、双方向の各メッセージ パターンの信頼できるセッションが実現します。`CreateSequence`\/`CreateSequenceResponse` で WS\-ReliableMessaging の `Offer` 機構を使用すると、相関する 2 つの逆方向シーケンスを確立でき、すべてのメッセージ エンドポイントに適したセッション プロトコルが提供されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、セッション整合性を保つためのエンドツーエンドの保護を含むこのようなセッションに対してセキュリティが保証されているため、同じパーティを対象とするメッセージが同じ送信先に到着することが事実上保証されます。また、これにより、アプリケーション メッセージにシーケンス受信確認を抱き合わせることができます。したがって、制約 R1104、R1105、および R1108 が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用されています。  
  
 `CreateSequence` メッセージの例を次に示します。  
  
```  
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
  
```  
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
  
### シーケンス  
 シーケンスに適用される制約を以下に示します。  
  
-   B1201 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`xs:long` の最大値 \(9223372036854775807\) 以下のシーケンス番号を生成し、これらの番号にアクセスします。  
  
-   B1202 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、アクション URI が http:\/\/schemas.xmlsoap.org\/ws\/2005\/02\/rm\/LastMessage である、空の本文を持つ最後のメッセージを必ず生成します。  
  
-   B1203 : アクション URI が http:\/\/schemas.xmlsoap.org\/ws\/2005\/02\/rm\/LastMessage でない場合には、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `LastMessage` 要素を含むシーケンス ヘッダーを持つメッセージを受信および配信します。  
  
 シーケンス ヘッダーのサンプル  
  
```  
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
  
### AckRequested ヘッダー  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、Keep\-alive 機構として `AckRequested` ヘッダーを使用します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、オプションの `MessageNumber` 要素を生成しません。`MessageNumber` 要素を含む `AckRequested` ヘッダーを持つメッセージを受信すると、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `MessageNumber` 要素の値を無視します。  
  
```  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### SequenceAcknowledgement ヘッダー  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS\-ReliableMessaging で用意されているシーケンス受信確認の抱き合わせ機構を使用します。  
  
-   R1401 : `Offer` 機構を使用して 2 つの逆方向シーケンスを確立した場合、目的の受信者に送信されるアプリケーション メッセージに、`SequenceAcknowledgement` ヘッダーを含めることができます。  
  
-   B1402 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がシーケンス メッセージを受信する前に受信確認を生成する必要がある場合 \(`AckRequested` メッセージに応える場合など\)、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は範囲 0 ～ 0 を含む `SequenceAcknowledgement` ヘッダーを生成します。  
  
    ```  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`Nack` 要素をサポートしていますが、`Nack` 要素を含む `SequenceAcknowledgement` ヘッダーは生成しません。  
  
### WS\-ReliableMessaging エラー  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の WS\-ReliableMessaging エラー実装に適用される制約を以下に示します。  
  
-   B1501 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`MessageNumberRollover` エラーを生成しません。  
  
-   B1502 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]エンドポイントは、仕様に記載されているように `CreateSequenceRefused` エラーを生成する場合があります。  
  
-   B1503 :サービス エンドポイントが接続制限に達したため、新しい接続を処理できない場合、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `CreateSequenceRefused` エラー サブコード `netrm:ConnectionLimitReached` を追加生成します。  
  
    ```  
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
  
### WS\-Addressing エラー  
 WS\-ReliableMessaging は WS\-Addressing を使用するため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の WS\-ReliableMessaging 実装は、WS\-Addressing エラーを生成する場合があります。ここでは、WS\-ReliableMessaging レイヤーで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が明示的に生成する WS\-Addressing エラーについて説明します。  
  
-   B1601 :次のいずれかに該当する場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は Message Addressing Header Required エラーを生成します。  
  
    -   メッセージに `Sequence` ヘッダーと `Action` ヘッダーがない。  
  
    -   `CreateSequence` メッセージに `MessageId` ヘッダーがない。  
  
    -   `CreateSequence` メッセージに `ReplyTo` ヘッダーがない。  
  
-   B1602 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`Sequence` ヘッダーがなく、WS\-Reliable Messaging 仕様では認識されない `Action` ヘッダーを持つメッセージへの応答として Action Not Supported エラーを生成します。  
  
-   B1603 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`CreateSequence` メッセージのアドレス指定ヘッダーの検査に基づいて、エンドポイントがそのシーケンスを処理しないことを示す Endpoint Unavailable エラーを生成します。  
  
## プロトコル コンポジション  
  
### WS\-Addressing によるコンポジション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS\-Addressing の 2 つのバージョンをサポートしています。WS\-Addressing 2004\/08 \[WS\-ADDR\] と、W3C WS\-Addressing 1.0 Recommendation \(\[WS\-ADDR\-CORE\] および \[WS\-ADDR\-SOAP\]\) です。  
  
 WS\-ReliableMessaging 仕様に記載されているのは、WS\-Addressing 2004\/08 だけですが、使用する WS\-Addressing のバージョンが制限されているわけではありません。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。  
  
-   R2101 :WS\-Addressing 2004\/08 と WS\-Addressing 1.0 の両方を WS\-ReliableMessaging で使用できます。  
  
-   R2102 :特定の WS\-ReliableMessaging シーケンス、または `wsrm:Offer` 機構を使用して関連付けられた逆方向シーケンスのペアでは、同じバージョンの WS\-Addressing を使用する必要があります。  
  
### SOAP によるコンポジション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、WS\-ReliableMessaging で SOAP 1.1 と SOAP 1.2 の両方を使用できます。  
  
### WS\-Security と WS\-SecureConversation によるコンポジション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、セキュリティで保護されたトランスポート \(HTTPS\)、WS\-Security によるコンポジション、および WS\-SecureConversation によるコンポジションを使用して、WS\-ReliableMessaging シーケンスを保護します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。  
  
-   R2301 :個々のメッセージの整合性と機密性だけでなく、WS\-ReliableMessaging シーケンスの整合性を保護するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では WS\-SecureConversation を使用する必要があります。  
  
-   R2302 :WS\-ReliableMessaging シーケンスを確立する前に、WS\-SecureConversation セッションを確立する必要があります。  
  
-   R2303 : WS\-ReliableMessaging シーケンスの有効期間が WS\-SecureConversation セッションの有効期間よりも長い場合は、対応する WS\-SecureConversation Renewal バインディングを使用して、WS\-SecureConversation によって確立された `SecurityContextToken` を更新する必要があります。  
  
-   B2304 :WS\-ReliableMessaging シーケンスまたは相関する逆方向シーケンスのペアは、必ず同じ WS\-SecureConversation セッションにバインドされます。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ソースは、`CreateSequence` メッセージの要素拡張セクションに、`wsse:SecurityTokenReference` 要素を生成します。  
  
-   R2305 :WS\-SecureConversation を使用して構成した場合、`CreateSequence` メッセージに `wsse:SecurityTokenReference` 要素が含まれている必要があります。  
  
## WS\-ReliableMessaging の WS\-Policy アサーション  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS\-ReliableMessaging の `wsrm:RMAssertion` WS\-Policy アサーションを使用して、エンドポイントの機能を記述します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。  
  
-   B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsrm:RMAssertion` WS\-Policy アサーションを `wsdl:binding` 要素に添付します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`wsdl:binding` 要素および `wsdl:port` 要素への添付をサポートしています。  
  
-   B3002 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS\-ReliableMessaging アサーションの以下のオプション プロパティをサポートしており、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の `ReliableMessagingBindingElement` でこれらのプロパティを制御できます。  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     例を次に示します。  
  
    ```  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## WS\-ReliableMessaging のフロー制御拡張  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS\-Reliable Messaging の機能拡張を使用して、シーケンス メッセージ フローのさらに厳密な制御を実現します。  
  
 フロー制御を有効にするには、`ReliableSessionBindingElement` の `FlowControlEnabled``bool` プロパティを `true` に設定します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に適用される制約を以下に示します。  
  
-   B4001 : 信頼できるメッセージング フロー制御を有効にした場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `SequenceAcknowledgement` ヘッダーの要素拡張に `netrm:BufferRemaining` 要素を生成します。  
  
-   B4002 : 信頼できるメッセージング フロー制御を有効にした場合、次の例に示すように、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では `netrm:BufferRemaining` 要素が `SequenceAcknowledgement` ヘッダーに存在する必要はありません。  
  
    ```  
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
  
-   B4003 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`netrm:BufferRemaining` を使用して、信頼できるメッセージングの送信先がバッファーに保持できる新しいメッセージの数を示します。  
  
-   B4004 :信頼できるメッセージングの送信先アプリケーションがメッセージを迅速に受信できない場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージング サービスは、送信するメッセージの数を抑制します。信頼できるメッセージングの送信先がメッセージをバッファーに保持する場合、要素の値が 0 になります。  
  
-   B4005 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、0 ～ 4096 の整数値の `netrm:BufferRemaining` を生成し、0 ～ 214748364 \(`xs:int` の `maxInclusive` 値\) の整数値を読み取ります。  
  
## メッセージ交換パターン  
 ここでは、WS\-ReliableMessaging をさまざまなメッセージ交換パターンに使用する際の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の動作について説明します。各メッセージ交換パターンについて、次の 2 つの展開シナリオを考えます。  
  
-   アドレス不可能なイニシエーター : イニシエーターはファイアウォールの内側にあります。レスポンダーは HTTP 応答でのみイニシエーターにメッセージを配信できます。  
  
-   アドレス可能なイニシエーター : イニシエーターとレスポンダーの両方に HTTP 要求を送信できます。つまり、逆方向の 2 つの HTTP 接続を確立できます。  
  
### 一方向 : アドレス不可能なイニシエーター  
  
#### バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、1 つの HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンを提供します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用して RMS から RMD にすべてのメッセージを送信し、HTTP 応答を使用して RMD から RMS にすべてのメッセージを送信します。  
  
#### CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含まない `CreateSequence` メッセージを生成します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていないことを確認します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequenceResponse` メッセージで `CreateSequence` 要求に応答します。  
  
#### SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、`CreateSequence` メッセージとエラー メッセージを除くすべてのメッセージの応答で受信確認を処理します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンス メッセージと `AckRequested` メッセージの両方への応答として、常にスタンドアロンの受信確認を生成します。  
  
#### TerminateSequence メッセージ  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`TerminateSequence` を一方向操作として処理します。つまり、HTTP 応答には、空の本文と HTTP 202 ステータス コードが含まれます。  
  
### 一方向 : アドレス可能なイニシエーター  
  
#### バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信用 HTTP チャネルと送信用 HTTP チャネルで 1 つのシーケンスを使用して、一方向メッセージ交換パターンを提供します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用してすべてのメッセージを送信します。すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含まない `CreateSequence` メッセージを生成します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていないことを確認します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`ReplyTo` エンドポイント参照によってアドレス指定された HTTP 要求で `CreateSequenceResponse` メッセージを送信します。  
  
### 双方向 : アドレス可能なイニシエーター  
  
#### バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信用 HTTP チャネルと送信用 HTTP チャネルで 2 つのシーケンスを使用して、完全に非同期の双方向メッセージ交換パターンを提供します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用してすべてのメッセージを送信します。すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含む `CreateSequence` メッセージを生成します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていることを確認します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`CreateSequence` の `ReplyTo` エンドポイント参照にアドレス指定された HTTP 要求で `CreateSequenceResponse` を送信します。  
  
#### シーケンスの有効期間  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、2 つのシーケンスを 1 つの完全な双方向セッションとして処理します。  
  
 一方のシーケンスをフォールトするエラーが生成されると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、リモート エンドポイントに両方のシーケンスをフォールトするよう要求します。一方のシーケンスをフォールトするエラーを読み取ると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は両方のシーケンスをフォールトします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、送信シーケンスを終了し、受信シーケンスで引き続きメッセージを処理できます。逆に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信シーケンスの終了を処理し、送信シーケンスで引き続きメッセージを送信することもできます。  
  
### 要求\/応答 : アドレス不可能なイニシエーター  
  
#### バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、1 つの HTTP チャネルで 2 つのシーケンスを使用して、一方向の要求\/応答メッセージ交換パターンを提供します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用して要求シーケンスのメッセージを送信し、HTTP 応答を使用して応答シーケンスのメッセージを送信します。  
  
#### CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含む `CreateSequence` メッセージを生成します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていることを確認します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequenceResponse` メッセージで `CreateSequence` 要求に応答します。  
  
#### 一方向のメッセージ  
 一方向メッセージ交換プロトコルを正常に完了するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答でスタンドアロンの `SequenceAcknowledgement` メッセージを受信します。`SequenceAcknowledgement` は、送信されたメッセージの受信確認を行う必要があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、受信確認、エラー、または空の本文と HTTP 202 ステータス コードで要求に応答できます。  
  
#### 双方向のメッセージ  
 双方向メッセージ交換プロトコルを正常に完了するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求で要求シーケンス メッセージを送信し、HTTP 応答で応答シーケンス メッセージを受信します。応答では、送信された要求シーケンス メッセージの受信確認を行う `SequenceAcknowledgement` を送信する必要があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、アプリケーション応答、エラー、または空の本文と HTTP 202 ステータス コードで要求に応答できます。  
  
 一方向のメッセージが存在することと、アプリケーション応答のタイミングもあるため、要求シーケンス メッセージのシーケンス番号と応答メッセージのシーケンス番号には相関関係はありません。  
  
#### 応答の再試行  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、双方向メッセージ交換プロトコルの相関関係について、HTTP 要求\/応答の相関関係に依存しています。このため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、要求シーケンス メッセージが受信確認されたときではなく、HTTP 応答によって受信確認、ユーザー メッセージ、またはエラーが送信されたときに、要求シーケンス メッセージの再試行を停止します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答が関連付けられている要求の HTTP 要求レッグで応答を再試行します。  
  
#### LastMessage の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求レッグで空の本文の最後のメッセージを生成し、送信します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は応答を要求しますが、実際の応答メッセージは無視します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答シーケンスの空の本文の最後のメッセージで、要求シーケンスの空の本文の最後のメッセージに応答します。  
  
 アクション URI が http:\/\/schemas.xmlsoap.org\/ws\/2005\/02\/rm\/LastMessage ではない最後のメッセージを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーが受信した場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は最後のメッセージで応答します。双方向メッセージ交換プロトコルの場合、最後のメッセージでアプリケーション メッセージが送信されます。一方向メッセージ交換プロトコルの場合、最後のメッセージは空です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答シーケンスの空の本文の最後のメッセージに対する受信確認を要求しません。  
  
#### TerminateSequence の交換  
 すべての要求が有効な応答を受信すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、HTTP 要求レッグで要求シーケンスの `TerminateSequence` メッセージを生成し、送信します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は応答を要求しますが、実際の応答メッセージは無視します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、応答シーケンスの `TerminateSequence` メッセージで、要求シーケンスの `TerminateSequence` メッセージに応答します。  
  
 通常のシャットダウン シーケンスでは、両方の `TerminateSequence` メッセージで完全な `SequenceAcknowledgement` を送信します。  
  
### 要求\/応答 : アドレス可能なイニシエーター  
  
#### バインディング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、受信用 HTTP チャネルと送信用 HTTP チャネルで 2 つのシーケンスを使用して、要求\/応答メッセージ交換パターンを提供します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTP 要求を使用してすべてのメッセージを送信します。すべての HTTP 応答に、空の本文と HTTP 202 ステータス コードが含まれます。  
  
#### CreateSequence の交換  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、オファーを含む `CreateSequence` メッセージを生成します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、シーケンスを作成する前に、`CreateSequence` にオファーが含まれていることを確認します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`CreateSequence` の `ReplyTo` エンドポイント参照にアドレス指定された HTTP 要求で `CreateSequenceResponse` を送信します。  
  
#### 要求\/応答の相関関係  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、すべてのアプリケーション要求メッセージに `MessageId` と `ReplyTo` エンドポイント参照が保持されていることを確認します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] イニシエーターは、各アプリケーション要求メッセージで、`CreateSequence` メッセージの `ReplyTo` エンドポイント参照を適用します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、受信要求メッセージに `MessageId` と `ReplyTo` が保持されていることを要求します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] レスポンダーは、`CreateSequence` とすべてのアプリケーション要求メッセージのエンドポイント参照の URI が同一であることを確認します。