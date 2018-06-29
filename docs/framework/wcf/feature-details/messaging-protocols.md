---
title: メッセージング プロトコル
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: d188c79d3879ef383d24f56c81d66973266636bc
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37072723"
---
# <a name="messaging-protocols"></a>メッセージング プロトコル
Windows Communication Foundation (WCF) チャネル スタックには、内部メッセージ表現をワイヤ形式に変換し、特定のトランスポートを使用して送信するエンコーディングとトランスポート チャネルが採用しています。 Web サービスの相互運用性を確保するために、最も一般的に使用されるトランスポートは HTTP です。また、Web サービスが使用する最も一般的なエンコーディングは、XML ベースの SOAP 1.1、SOAP 1.2、および MTOM (Message Transmission Optimization Mechanism) です。  
  
 このトピックの内容で採用されている次のプロトコルの実装の詳細を WCF<xref:System.ServiceModel.Channels.HttpTransportBindingElement>です。  
  
|仕様/ドキュメント|Link|  
|-----------------------------|----------|  
|HTTP 1.1|http://www.ietf.org/rfc/rfc2616.txt|  
|SOAP 1.1 HTTP バインディング|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/、セクション 7|  
|SOAP 1.2 HTTP バインディング|http://www.w3.org/TR/soap12-part2/、セクション 7|  
  
 このトピックの内容を以下のプロトコルに関する WCF 実装の詳細<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>と<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>を使用します。  
  
|仕様/ドキュメント|Link|  
|-----------------------------|----------|  
|XML|http://www.w3.org/TR/REC-xml|  
|SOAP 1.1|http://www.w3.org/TR/2000/NOTE-SOAP-20000508/|  
|SOAP 1.2 コア|http://www.w3.org/TR/soap12-part1/|  
|WS-Addressing 2004/08|http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/|  
|W3C Web Services Addressing 1.0 - コア|http://www.w3.org/TR/2006/REC-ws-addr-core-20060509|  
|W3C Web Services Addressing 1.0 - SOAP バインディング|http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509|  
|W3C Web Services Addressing 1.0 - WSDL バインディング|http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/|  
W3C Web Services Addressing 1.0 - メタデータ|http://www.w3.org/TR/ws-addr-metadata/|  
|WSDL SOAP1.1 バインディング|http://www.w3.org/TR/wsdl/|  
|WSDL SOAP1.2 バインディング|http://www.w3.org/Submission/wsdl11soap12/|  
  
 このトピックの内容を以下のプロトコルに関する WCF 実装の詳細<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>を使用します。  
  
|仕様/ドキュメント|Link|  
|-----------------------------|----------|  
|XOP|http://www.w3.org/TR/xop10/|  
|MTOM および SOAP 1.2 バインディング|http://www.w3.org/TR/soap12-mtom/|  
|MTOM SOAP 1.1 バインディング|http://www.w3.org/Submission/soap11mtom10/|  
|MTOM WS-Policy アサーション|http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/。|  
  
 ここでは、次の XML 名前空間と関連付けられたプレフィックスが使用されます。  
  
|プレフィックス|名前空間 URI (Uniform Resource Identifier)|  
|------------|---------------------------------------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|s12|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://www.w3.org/2004/08/addressing|  
|wsam|http://www.w3.org/2007/05/addressing/metadata|  
|wsap|http://schemas.xmlsoap.org/ws/2004/09/policy/addressing|  
|wsa10|http://www.w3.org/2005/08/addressing|  
|wsaw10|http://www.w3.org/2006/05/addressing/wsdl|  
|xop|http://www.w3.org/2004/08/xop/include|  
|xmime|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
dp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a>SOAP 1.1 と SOAP 1.2  
  
### <a name="envelope-and-processing-model"></a>エンベロープと処理モデル  
 WCF では、次の Basic Profile 1.1 (BP11) および Basic Profile 1.0 (ssbp10) に従って、SOAP 1.1 エンベロープの処理を実装します。 SOAP 1.2 エンベロープの処理は、SOAP12-Part1 に従って実装されます。  
  
 このセクションでは、BP11 および SOAP12 パート 1 に関して、WCF によって実行される特定の実装の選択肢について説明します。  
  
#### <a name="mandatory-header-processing"></a>必須のヘッダー処理  
 マークされたヘッダーの処理規則に従います WCF`mustUnderstand`次のように、SOAP 1.1 と SOAP 1.2 の仕様で説明します。  
  
 WCF チャネル スタックに入ったメッセージは、たとえば関連付けられたバインド要素によって構成された個々 のチャネル、テキスト メッセージ エンコーディング、セキュリティ、信頼性の高いメッセージング、およびトランザクションによって処理されます。 各チャネルは、関連付けられた名前空間からヘッダーを認識し、認識済みとしてマークします。 メッセージがディスパッチャーに入ると、操作フォーマッタは対応するメッセージ コントラクトと操作コントラクトで想定されたヘッダーを読み取り、認識済みとしてマークします。 次に、ディスパッチャーは、`mustUnderstand` としてマークされているにもかかわらず、認識されていないヘッダーが残っていないかどうかを検証し、例外をスローします。 受信者を対象とする `mustUnderstand` ヘッダーが含まれたメッセージが、受信者のアプリケーション コードで処理されることはありません。  
  
 このようなレイヤー化された処理により、SOAP ノードのインフラストラクチャ レイヤーとアプリケーション レイヤーを次のように分離することが可能になります。  
  
-   B1111: 認識されないヘッダーが検出、メッセージは、WCF インフラストラクチャ チャネル スタックによって処理しますが、アプリケーションによって処理される前に  
  
     `mustUnderstand` ヘッダーの値は、SOAP 1.1 と SOAP 1.2 で異なります。 Basic Profile 1.1 では、SOAP 1.1 メッセージの `mustUnderstand` の値が 0 または 1 である必要があります。 SOAP 1.2 では、値として 0、1、`false`、および `true` を使用できますが、`xs:boolean` 値の正規表現 (`false`、`true`) を出力することをお勧めします。  
  
-   B1112: WCF 出力`mustUnderstand`SOAP エンベロープの値を 0 と SOAP 1.1 と SOAP 1.2 の両方のバージョンの場合は 1 です。 WCF は、値空間全体を受け入れる`xs:boolean`の`mustUnderstand`ヘッダー (0、1、 `false`、 `true`)  
  
#### <a name="soap-faults"></a>SOAP エラー  
 WCF に固有の SOAP エラー実装の一覧を次に示します。  
  
-   B2121: WCF は、次の SOAP 1.1 エラー コードを返します: `s11:mustUnderstand`、 `s11:Client`、および`s11:Server`です。  
  
-   B2122: WCF は、次の SOAP 1.2 エラー コードを返します: `s12:MustUnderstand`、 `s12:Sender`、および`s12:Receiver`です。  
  
### <a name="http-binding"></a>HTTP バインディング  
  
#### <a name="soap-11-http-binding"></a>SOAP 1.1 HTTP バインディング  
 WCF では、Basic Profile 1.1 仕様の次に説明セクション 3.4 に従って、SOAP1.1 HTTP バインディングを実装します。  
  
-   B2211: WCF サービスは HTTP POST 要求のリダイレクトを実装していません。  
  
-   B2212: WCF クライアントは、3.4.8 に従って HTTP クッキーをサポートします。  
  
#### <a name="soap-12-http-binding"></a>SOAP 1.2 HTTP バインディング  
 WCF は、SOAP 1.2-part 2 (SOAP12Part2) 仕様次に説明」の説明に従って、SOAP 1.2 HTTP バインディングを実装します。  
  
 SOAP 1.2 では、`application/soap+xml` メディア タイプの省略可能なアクション パラメーターが導入されました。 このパラメーターは、WS-Addressing を使用していない場合に、SOAP メッセージの本文を解析する必要なく、メッセージ ディスパッチを最適化する際に役立ちます。  
  
-   R2221 : `application/soap+xml` のアクション パラメーターが SOAP 1.2 要求に含まれている場合、対応する WSDL バインディング内の `soapAction` 要素の `wsoap12:operation` 属性と一致する必要があります。  
  
-   R2222 : WS-Addressing 2004/08 または WS-Addressing 1.0 を使用しているときに、`application/soap+xml` のアクション パラメーターが SOAP 1.2 メッセージに含まれている場合、`wsa:Action` と一致する必要があります。  
  
 WS-Addressing が無効になっているときに、受信要求にアクション パラメーターが含まれていない場合、メッセージの `Action` は指定されていないものと見なされます。  
  
## <a name="ws-addressing"></a>WS-Addressing  
 WCF には、3 つのバージョンの Ws-addressing が実装されています。  
  
-   WS-Addressing 2004/08  
  
-   W3C Web Services Addressing 1.0 コア (ADDR10-CORE) - SOAP バインディング (ADDR10-SOAP)  
  
-   WS-Addressing 1.0 - メタデータ  
  
### <a name="endpoint-references"></a>エンドポイント参照  
 WCF を実装している Ws-addressing のすべてのバージョンでは、エンドポイント参照を使用してエンドポイントを記述します。  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a>エンドポイント参照と WS-Addressing のバージョン  
 WCF は Ws-addressing を使用するインフラストラクチャ プロトコルの特定の数を実装して、`EndpointReference`要素および`W3C.WsAddressing.EndpointReferenceType`クラス (Ws-reliablemessaging、Ws-secureconversation、Ws-trust など)。 WCF では、いずれかのバージョンの Ws-addressing を他のインフラストラクチャ プロトコルと共に使用をサポートします。 WCF エンドポイントは、Ws-addressing のエンドポイントごとの 1 つのバージョンをサポートします。  
  
 R3111 での名前空間、`EndpointReference`要素または WCF エンドポイントと交換されるメッセージで使用される型がこのエンドポイントによって実装されている Ws-addressing のバージョンに一致する必要があります。  
  
 WCF エンドポイントは、Ws-reliablemessaging を実装している場合など、`AcksTo`ヘッダー内のようなエンドポイントによって返される`CreateSequenceResponse`Ws-addressing のバージョンを使用する、`EncodingBinding`要素は、このエンドポイントを指定します。  
  
#### <a name="endpoint-references-and-metadata"></a>エンドポイント参照とメタデータ  
 多くのシナリオでは、指定されたエンドポイントのメタデータまたはメタデータへの参照を伝達する必要があります。  
  
 B3121: WCF では、Ws-metadataexchange (MEX) 仕様のメタデータに含めるエンドポイント参照の値渡しまたは参照渡しのセクション 6 に示すメカニズムを採用しています。  
  
 WCF サービスであるトークン発行者によって発行された Security Assertions Markup Language (SAML) トークンを使用して認証が必要な場合を考えますhttp://sts.fabrikam123.comです。 WCF エンドポイントを使用してこの認証要件を記述する`sp:IssuedToken`が入れ子になったアサーション`sp:Issuer`トークンの発行者を指し示すアサーションです。 `sp:Issuer` アサーションにアクセスするクライアント アプリケーションは、トークン発行者のエンドポイントとの通信方法を知る必要があります。 クライアントは、トークン発行者に関するメタデータを知る必要があります。 MEX で定義されたエンドポイント参照のメタデータ拡張を使用して、WCF は、トークン発行者のメタデータへの参照を提供します。  
  
```xml  
<sp:IssuedToken>  
  <sp:Issuer>  
    <wsa10:Address>  
      http://sts.fabrikam123.com  
    </wsa10:Address>  
    <wsa10:Metadata>  
      <mex:Metadata>  
        <mex:MetadataSection>  
          <mex:MetadataReference>  
            <wsa10:Address>  
              http://sts.fabrikam123.com/mex  
            </wsa10:Address>  
          </mex:MetadataReference>  
        </mex:MetadataSection>  
      </mex:Metadata>  
    </wsa10:Metadata>  
  </sp:Issuer>  
</sp:IssuedToken>  
```  
  
### <a name="message-addressing-headers"></a>メッセージのアドレス指定ヘッダー  
  
#### <a name="message-headers"></a>メッセージ ヘッダー  
 両方の Ws-addressing のバージョンでは、WCF を使用して、次のメッセージ ヘッダーの仕様で規定された`wsa:To`、 `wsa:ReplyTo`、 `wsa:Action`、 `wsa:MessageID`、および`wsa:RelatesTo`です。  
  
 B3211: Ws-addressing のバージョンをすべての WCF 適用することしますが、out of box、Ws-addressing メッセージ ヘッダーは生成されない`wsa:FaultTo`と`wsa:From`です。  
  
 WCF アプリケーションと対話するアプリケーションでは、これらのメッセージ ヘッダーと WCF は適切に処理を追加できます。  
  
#### <a name="reference-parameters-and-properties"></a>参照パラメーターと参照プロパティ  
 WCF は、エンドポイント参照のパラメーターと参照 p の処理を実装します。  
  
 参照プロパティの処理を実装しています。  
  
 B3221: Ws-addressing 2004/08 を使用するように構成時に WCF エンドポイントを区別せず参照のプロパティと参照パラメーターを処理します。  
  
### <a name="message-exchange-patterns"></a>メッセージ交換パターン  
 Web サービス操作呼び出しに関連するメッセージのシーケンスと呼びます、*メッセージ交換パターン*です。 一方向の WCF サポート、要求/応答、および双方向メッセージ交換パターンです。 このセクションでは、使用するメッセージ交換パターンによって異なるメッセージ処理に関する WS-Addressing の要件について説明します。  
  
 このセクション全体を通して、リクエスターが最初のメッセージを送信し、レスポンダーが最初のメッセージを受信します。  
  
#### <a name="one-way-message"></a>一方向のメッセージ  
 持つメッセージをサポートするために WCF エンドポイントが構成されている場合、指定された`Action`一方向パターンに従う、WCF エンドポイントに依存して、次の動作と要件です。 未指定のそれ以外の場合、両方のバージョンの Ws-addressing が WCF ではサポートされている動作とルールが適用されます。  
  
-   R3311 : リクエスターは、`wsa:To`、`wsa:Action`、およびエンドポイント参照によって指定されたすべての参照パラメーターのヘッダーを含める必要があります。 WS-Addressing 2004/08 を使用し、エンドポイント参照によって参照プロパティが指定されている場合、対応するヘッダーもメッセージに追加する必要があります。  
  
-   B3312 : リクエスターは、`MessageID`、`ReplyTo`、および `FaultTo` の各ヘッダーを含めることができます。 受信側のインフラストラクチャはこれらのヘッダーを無視し、ヘッダーはアプリケーションに渡されます。  
  
-   R3313 : HTTP を使用し、HTTP 応答レッグで送信するメッセージがない場合、レスポンダーは空の本文と HTTP 202 ステータス コードを含む HTTP 応答を送信する必要があります。  
  
     HTTP トランスポートを使用しており、操作コントラクトで一方向のメッセージが宣言されている場合でも、HTTP 応答を使用してインフラストラクチャ メッセージを送信できます。たとえば、信頼できるメッセージングでは、HTTP 応答で `SequenceAcknowledgement` メッセージを送信できます。  
  
-   B3314: WCF レスポンダーは、一方向のメッセージに応答のエラー メッセージを送信していません。  
  
#### <a name="request-reply"></a>要求/応答  
 含むメッセージ用の WCF エンドポイントを構成するとき、指定された`Action`要求/応答パターンに従う、WCF エンドポイントに依存して、動作と下記の要件です。 特に指定しない限り、両方のバージョンの Ws-addressing が WCF ではサポートされている動作とルールが適用されます。  
  
-   R3321: リクエスターは、要求に含める必要があります`wsa:To`、 `wsa:Action`、 `wsa:MessageID`、およびすべての参照パラメーターまたは参照プロパティ (またはその両方) のエンドポイント参照によって指定されたヘッダー。  
  
-   R3322 : WS-Addressing 2004/08 を使用する場合、`ReplyTo` も要求に含める必要があります。  
  
-   R3323: Ws-addressing 1.0 を使用する場合と`ReplyTo`と等しい [address] プロパティを使用して既定のエンドポイント参照、要求に存在しない"http://www.w3.org/2005/08/addressing/anonymous"を使用します。  
  
-   R3324: リクエスターを含める必要があります`wsa:To`、 `wsa:Action`、および`wsa:RelatesTo`応答メッセージのヘッダーだけでなくすべての参照パラメーターまたは参照プロパティ (またはその両方) で指定されたヘッダー、`ReplyTo`でエンドポイント参照、要求。  
  
### <a name="web-services-addressing-faults"></a>Web Services Addressing エラー  
 R3411: WCF は Ws-addressing 2004/08 で定義された次のエラーを生成します。  
  
|コード|原因|  
|----------|-----------|  
|wsa:DestinationUnreachable|このチャネル用に確立された応答アドレスとは異なる `ReplyTo` を使用してメッセージが到着しました。To ヘッダーに指定されたアドレスをリッスンしているエンドポイントはありません。|  
|wsa:ActionNotSupported|`Action` ヘッダーに指定されたアクションは、エンドポイントに関連付けられたインフラストラクチャ チャネルまたはディスパッチャーによって認識されません。|  
  
 R3412: WCF は Ws-addressing 1.0 で定義された次のエラーを生成します。  
  
|コード|原因|  
|----------|-----------|  
|wsa10:InvalidAddressingHeader|重複する`wsa:To`、 `wsa:ReplyTo`、`wsa:From`または`wsa:MessageID`です。 重複する`wsa:RelatesTo`同じ`RelationshipType`です。|  
|wsa10:MessageAddressingHeaderRequired|必須の Addressing ヘッダーがありません。|  
|wsa10:DestinationUnreachable|このチャネル用に確立された応答アドレスとは異なる `ReplyTo` を使用してメッセージが到着しました。 To ヘッダーに指定されたアドレスをリッスンしているエンドポイントはありません。|  
|wsa10:ActionNotSupported|`Action` ヘッダーに指定されたアクションは、エンドポイントに関連付けられたインフラストラクチャ チャネルまたはディスパッチャーによって認識されません。|  
|wsa10:EndpointUnavailable|RM チャネルは、`CreateSequence` メッセージのアドレス指定ヘッダーの検査に基づいて、エンドポイントでシーケンスが処理されないことを示すために、このエラーを返しました。|  
  
 上記の 2 つの表に示すコードは、SOAP 1.1 の `FaultCode`、および SOAP 1.2 の `SubCode` (Code=Sender) に対応付けられています。  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 バインディングと WS-Policy アサーション  
  
#### <a name="indicating-use-of-ws-addressing"></a>WS-Addressing の使用の提示  
 WCF では、ポリシー アサーションを使用して、特定の Ws-addressing のバージョンのエンドポイントのサポートを示します。  
  
 次のポリシー アサーションには、エンドポイント ポリシー サブジェクト [WS-PA] が含まれており、そのエンドポイントで送受信されるメッセージでは WS-Addressing 2004/08 を使用する必要があることを示しています。  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 このポリシー アサーションは、WS-Addressing 2004/08 仕様を補うものです。  
  
 次のポリシー アサーションは、送受信されるメッセージでは WS-Addressing 1.0 を使用する必要があることを示しています。  
  
```xml
<wsam:Addressing/>   
```  
  
 次のポリシー アサーションには、エンドポイント ポリシー サブジェクト [WS-PA] が含まれており、そのエンドポイントで送受信されるメッセージでは WS-Addressing 2004/08 を使用する必要があることを示しています。  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 `wsaw10:UsingAddressing` 要素は、WS-Addressing-WSDL から借用したものです。この要素は、この仕様のセクション 3.1.2 に従って、WS-Policy のコンテキストで使用されます。  
  
 Addressing を使用しても、WSDL 1.1、SOAP 1.1、および SOAP 1.2 HTTP バインディングのセマンティクスが変更されるわけではありません。 たとえば、Addressing と WSDL SOAP 1.x HTTP バインディングを使用するエンドポイントに送信する要求に対して応答が求められている場合、この応答は HTTP 応答を使用して送信する必要があります。  
  
 HTTP 応答を使用して送信された応答の場合、WS-AM アサーションは次のようになります。  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 完全なポリシー アサーションは次のようになる場合があります。  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 ただし、リクエスターとレスポンダー間で 2 つの独立した逆方向の HTTP 接続を確立することによってメリットのあるメッセージ交換パターンがあります。たとえば、レスポンダーによって送信される要求されていない一方向のメッセージなどです。  
  
 WCF では、複合二重チャネル、入力メッセージの 1 つのチャネルを使用して、出力メッセージの使用は、他の場所を基になる 2 つのトランスポート チャネルから形成できる機能を提供します。 HTTP トランスポートの場合、複合二重によって 2 つの逆方向の HTTP 接続が実現します。 一方の接続はリクエスターがレスポンダーにメッセージを送信するために使用し、もう一方はレスポンダーがリクエスターにメッセージを返すために使用します。  
  
 個別の HTTP 要求を使用して送信された応答の場合、WS-AM アサーションは次のようになります。  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 完全なポリシー アサーションは次のようになる場合があります。  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 WSDL 1.1 SOAP 1.x HTTP バインディングを使用するエンドポイントで、エンドポイント ポリシー サブジェクト [WS-PA] を含む次のアサーションを使用する場合、リクエスターからレスポンダーおよびレスポンダーからリクエスターへのメッセージ フローにそれぞれ別の逆方向の HTTP 接続を使用する必要があります。  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 上記のステートメントにより、要求メッセージの `wsa:ReplyTo` ヘッダーに関する以下の要件が発生します。  
  
-   R3514: 要求メッセージにするエンドポイントに送信する必要があります、`ReplyTo`ヘッダーを`[address]`プロパティに等しくない"http://www.w3.org/2005/08/addressing/anonymous"エンドポイントが WSDL 1.1 SOAP 1.x HTTP バインディングを使用して、ポリシー代替手段を持つ場合、`wsap10:UsingAddressing`または`wsap:UsingAddressing`組み合わせるとアサーション`cdp:CompositeDuplex`添付します。  
  
-   R3515: 要求メッセージにするエンドポイントに送信する必要があります、`ReplyTo`ヘッダーを`[address]`プロパティを等しく"http://www.w3.org/2005/08/addressing/anonymous"、かない、`ReplyTo`ヘッダーはまったく、エンドポイントが WSDL 1.1 SOAP 1.x HTTP バインディングを使用して、ポリシー代替手段を持つ場合`wsap10:UsingAddressing`アサーションといいえ`cdp:CompositeDuplex`アサーションです。  
  
-   R3516: 要求メッセージにするエンドポイントに送信する必要があります、`ReplyTo`ヘッダーを`[address]`プロパティを等しく"http://www.w3.org/2005/08/addressing/anonymous"エンドポイントが WSDL 1.1 SOAP 1.x HTTP バインディングを使用して、ポリシー代替手段を持つ場合`wsap:UsingAddressing`アサーションとありません`cdp:CompositeDuplex`アサーションです。  
  
 WS-Addressing の WSDL 仕様では、`<wsaw:Anonymous/>` ヘッダーの要件を示す 3 つのテキスト値 (required、optional、および prohibited) を持つ `wsa:ReplyTo` 要素を導入することにより、同様のプロトコル バインディングを記述することを試みています (セクション 3.2)。 残念ながら、このような要素の定義では、要素をアサーションとして使用する代替手段の共通部分をサポートするために、ドメイン固有の拡張を必要とするため、特に WS-Policy のコンテキストではアサーションとして使用することはできません。 また、このような要素の定義は、ネットワーク上のエンドポイントの動作に相反する `ReplyTo` ヘッダーの値を示すため、HTTP トランスポートに固有のものになります。  
  
#### <a name="action-definition"></a>アクション定義  
 WS-Addressing 2004/08 では、`wsa:Action` 要素の `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` 属性が定義されています。 WS-Addressing 1.0 WSDL バインディング (WS-ADDR10-WSDL) では、同様の属性として `wsaw10:Action` が定義されています。  
  
 この 2 つの属性の唯一の違いは、既定の Action パターンのセマンティクスです。これは、WS-ADDR のセクション 3.3.2 および WS-ADDR10-WSDL のセクション 4.4.4 にそれぞれ記載されています。  
  
 これは、同じ 2 つのエンドポイントが存在する適切`portType`(または WCF の用語では、コントラクト) が異なるバージョンの Ws-addressing を使用しています。 しかし、Action は `portType` によって定義され、`portType` を実装するエンドポイント間で変更できないことを考えると、両方の既定のアクション パターンをサポートすることは不可能になります。  
  
 この問題を解決するのには、WCF は、の 1 つのバージョンをサポートしている、`Action`属性。  
  
 B3521: WCF を使用して、`wsaw10:Action`属性`wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]`要素を決定する WS-ADDR10-WSDL で定義されている、`Action`エンドポイントが使用する Ws-addressing のバージョンに関係なく、対応するメッセージの URI。  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a>WSDL ポート内でのエンドポイント参照の使用  
 WS-ADDR10-WSDL のセクション 4.1 では、`wsdl:port` 要素を拡張して、WS-Addressing の観点でエンドポイントを記述する `<wsa10:EndpointReference…/>` 子要素を含めています。 WCF は Ws-addressing 2004/08 でこのユーティリティを拡張できるように`<wsa:EndpointReference…/>`の子要素として表示される`wsdl:port`です。  
  
-   R3531 : エンドポイントが `<wsaw10:UsingAddressing/>` ポリシー アサーションに関連付けられたポリシー代替手段を持つ場合、対応する `wsdl:port` 要素に `<wsa10:EndpointReference …/>` 子要素を含めることができます。  
  
-   R3532: 場合、`wsdl:port`子要素を含む`<wsa10:EndpointReference …/>`、`wsa10:EndpointReference/wsa10:Address`子要素の値の値に一致する必要があります、`@address`の兄弟要素の属性`wsdl:port` / `wsdl:location`要素。  
  
-   R3533 : エンドポイントが `<wsap:UsingAddressing/>` ポリシー アサーションに関連付けられたポリシー代替手段を持つ場合、対応する `wsdl:port` 要素に `<wsa:EndpointReference …/>` 子要素を含めることができます。  
  
-   R3534: 場合、`wsdl:port`子要素を含む`<wsa:EndpointReference …/>`、`wsa:EndpointReference/wsa:Address`子要素の値の値に一致する必要があります、`@address`の兄弟要素の属性`wsdl:port` / `wsdl:location`要素。  
  
### <a name="composition-with-ws-security"></a>WS-Security によるコンポジション  
 WS-ADDR および WS-ADDR10 のセキュリティに関する考慮事項のセクションに従って、メッセージ本文と共にすべてのアドレス指定メッセージ ヘッダーに署名し、これらをバインドすることをお勧めします。  
  
 メッセージの整合性を保護するために WS-Security を使用する場合は、メッセージの本文と共に、WS-Addressing メッセージ ヘッダーと、参照パラメーターまたは参照プロパティ (または両方) によって生成されたヘッダーに署名する必要があります。  
  
### <a name="examples"></a>使用例  
  
#### <a name="one-way-message"></a>一方向のメッセージ  
 このシナリオでは、送信者は一方向のメッセージを受信者に送信します。 SOAP 1.2、HTTP 1.1、および W3C WS-Addressing 1.0 を使用します。  
  
 要求メッセージの構造 : メッセージ ヘッダーには、`wsa10:To` 要素と `wsa10:Action` 要素が含まれます。 メッセージ本文には、アプリケーション名前空間の特定の `<app:Ping>` 要素が含まれます。  
  
 HTTP ヘッダー: POST の送信先の URI と一致する、`wsa10:To`要素。  
  
 Content-Type ヘッダーには、SOAP 1.2 で必要とされる値 `application/soap+xml` が含まれます。 また、`charset` パラメーターと `action` パラメーターも含まれます。 Content-Type ヘッダーの `action` パラメーターは、`wsa10:Action` メッセージ ヘッダーの値に一致します。  
  
```  
POST http://fabrikam123.com/Service HTTP/1.1  
Content-Type: application/soap+xml; charset=utf-8;    
              action="http://fabrikam123.com/Service/OneWay"  
Host: 131.107.72.15  
Content-Length: 1501  
Expect: 100-continue  
Proxy-Connection: Keep-Alive  
<s12:Envelope>  
  <s12:Header>  
    <wsa10:To s12:mustUnderstand="1">  
        http://fabrikam123.com/Service  
    </wsa10:To>  
    <wsa10:Action s12:mustUnderstand="1">  
        http://fabrikam123.com/Service/OneWay   
    </wsa10:Action>  
  </s12:Header>  
  <s12:Body>  
    <Ping xmlns="http://fabrikam123.com/Service/">  
      <Text>Hello World</Text>  
    </Ping>  
  </s12:Body>  
</s12:Envelope>  
```  
  
 受信側は、空の HTTP 応答と 202 ステータスで応答します。 HTTP 応答の一例を次に示します。  
  
```  
HTTP/1.1 202 Accepted  
Date: Fri, 15 Jul 2005 08:56:07 GMT  
Server: Microsoft-IIS/6.0  
MicrosoftOfficeWebServer: 5.0_Pub  
X-Powered-By: ASP.NET  
X-AspNet-Version: 2.0.50215  
Cache-Control: private  
Content-Length: 0  
```  
  
## <a name="soap-message-transmission-optimization-mechanism"></a>SOAP Message Transmission Optimization Mechanism  
 このセクションでは、HTTP SOAP MTOM の WCF 実装の詳細について説明します。 MTOM テクノロジは、従来の TEXT/XML エンコーディングまたは WCF バイナリ エンコーディングと同じクラスの SOAP メッセージ エンコーディング機構です。 MTOM には、次のような機能があります。  
  
-   XOP によって記述された XML エンコーディングおよびパッケージング機構。XOP は、Base64 で個別のバイナリ部分にエンコードされたバイナリ データを含む XML 情報項目を最適化します。  
  
-   XML Infoset と XOP パッケージの各バイナリ部分を個別の MIME パートにシリアル化する、XOP パッケージの MIME カプセル化。  
  
-   SOAP 1.x エンベロープに適用される MIME XOP エンコーディング。  
  
-   HTTP トランスポート バインディング。  
  
 WCF で HTTP 以外のトランスポートで MTOM を使用することができます。 しかし、ここでは HTTP に焦点を合わせます。  
  
 MTOM 形式では、MTOM 自体、XOP、および MIME に適用されるさまざまな仕様を利用します。 この仕様セットのモジュール性により、形式と処理のセマンティクスの要件を正確に再構築することが若干難しくなります。 このセクションでは、MTOM HTTP バインディングの形式と処理の要件について説明します。  
  
### <a name="mtom-message-encoding"></a>MTOM メッセージ エンコーディング  
  
#### <a name="generating-mtom-messages"></a>MTOM メッセージの生成  
 XOP のセクション 3.1 には、Base64 値を抽象的に定義された XOP パッケージに格納する要素情報項目を使用して、XML をエンコーディングするプロセスが記載されています。  
  
 次の一連の手順は、MTOM 固有のエンコーディング プロセスを示しています。  
  
1.  エンコードする SOAP エンベロープに記述されている要素情報項目が含まれていないことを確認、`[namespace name]`の"http://www.w3.org/2004/08/xop/include"および`[local name]`の`Include`します。  
  
2.  空の MIME パッケージを作成します。  
  
3.  元の XML Infoset 内で、最適化する要素情報項目を特定します。 項目を最適化する場合、要素情報項目の `[children]` を構成する文字は、`xs:base64Binary` の正規形式であることが必要です (XSD-2 セクション 3.2.16 の base64Binary を参照)。また、空白以外のコンテンツの前、インライン、または後に、空白文字を含めることはできません。  
  
4.  元の SOAP エンベロープのコピーである XOP SOAP エンベロープを作成します。ただし、このコピーには、前の手順で特定した各要素情報項目の子が含まれます。これらの子は、以下の手順に従って構築された `xop:Include` 要素情報項目に置き換えられています。  
  
    1.  置換対象の文字を Base64 でエンコードされたデータとして処理することにより、バイナリ データに変換します。  
  
    2.  R3133 および R3134 の各要件を満たす Content-ID ヘッダーの一意の値を生成します。  
  
    3.  バイナリ値を使用して、Content-Transfer-Encoding MIME ヘッダーを生成します。  
  
    4.  最適化する要素情報項目 (新しく挿入する `xop:Include` 要素情報項目の [parent]) に、`xmime:contentType` 属性情報項目が含まれている場合、`xmime:contentType` 属性の値を使用して Content-Type MIME ヘッダーを生成します。  
  
    5.  Base64 として処理された置換対象文字からデコードされたバイナリ データ、Content-ID ヘッダー (手順 4b. で生成)、Content- Transfer-Encoding ヘッダー (手順 4c. で生成)、および Content-Type ヘッダー (手順 4d. で生成した場合) で構成されたコンテンツを含む、新しいバイナリ MIME パートを生成します。  
  
    6.  値 cid: uri を持つ `href` 要素に `xop:Include` 属性を追加します。uri は、手順 4b. で生成した Content-ID ヘッダーの値から派生したものです。 削除、外側にある"\<"と">"URL エスケープ文字列、およびプレフィックスを追加、残りの文字`cid:`です。 RFC1738 と RFC2396 に従って、次の最小限の文字セットをエスケープする必要があります。 その他の文字もエスケープすることができます。  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  手順 4. の XOP SOAP エンベロープを含むルート MIME パートを作成します。  
  
6.  HTTP Content-Type ヘッダーなどの HTTP ヘッダーを書き込みます。  
  
7.  MIME パッケージを書き込みます。  
  
#### <a name="processing-mtom-messages"></a>MTOM メッセージの処理  
 MTOM メッセージの処理は、前述の「MTOM メッセージの生成」で説明したプロセスと正反対のプロセスになります。  
  
1.  ルート MIME パートに Content-Type `application/xop+xml` が含まれていることを確認します。  
  
2.  パッケージのルート MIME パートを XML ドキュメントとして解析して、SOAP エンベロープを作成します。 文字エンコーディングは、ルート MIME パートの Content-Type の `charset` パラメーターによって決まります。  
  
3.  作成した SOAP エンベロープ内の各要素情報項目について、以下の処理を行います。これらの要素情報項目には、[children] プロパティの唯一のメンバーとして、`xop:Include` 要素情報項目が含まれています。  
  
    1.  プレフィックス `cid:` を削除し、`@href` 要素の `xop:Include` 属性の値に含まれるすべての URI エスケープ シーケンスのエスケープを解除します (RFC 2396)。 結果の文字列を囲む"\<"、">"です。  
  
    2.  Content-ID ヘッダーの値が手順 3a. で取得した文字列に一致する MIME パートを検索します。  
  
    3.  各項目の `xop:Include` プロパティに出現する `children` 要素情報項目を、手順 3b. で特定した MIME パートのエンティティ本体の正規 Base64 エンコーディング (XSD-2 セクション 3.2.16 の base64Binary を参照) を表す文字情報項目に置き換えます (`xop:Include` 要素情報項目をパッケージ パーツから再構築したデータに効率的に置き換えます)。  
  
#### <a name="http-content-type-header"></a>HTTP Content-Type ヘッダー  
 次は、SOAP 1.x MTOM でエンコードされたメッセージ、MTOM 仕様に記載された要件の HTTP Content-type ヘッダーの形式の WCF 説明の一覧を示しますされ、MTOM および RFC 2387 に基づいてから派生されます。  
  
-   R4131 : HTTP Content-Type ヘッダーには、multipart/related (大文字と小文字は区別されません) とそのパラメーターの値が必要です。 パラメーター名では、大文字と小文字は区別されません。 パラメーターの順序は重要ではありません。  
  
-   MIME メッセージの Content-Type ヘッダーのすべての Backus-Naur Form (BNF) については、RFC 2045 のセクション 5.1 に記載されています。  
  
-   R4132 : HTTP Content-Type ヘッダーには、二重引用符で囲まれた値 `application/xop+xml` が指定された型パラメーターが必要です。  
  
 テキストでは、すべて multipart/related メディアの型パラメーターのほとんど含まれているなどの予約済みの文字が二重引用符を使用する要件は、RFC 2387 に明示ありませんが、"\@"または「/」したがって二重引用符を必要とマークを付けます。  
  
-   R4133 : HTTP Content-Type ヘッダーには、start パラメーターを含める必要があります。このパラメーターには、SOAP 1.x エンベロープを含む MIME パートの Content-ID ヘッダーの値を二重引用符で囲んで指定します。 start パラメーターを省略する場合は、最初の MIME パートに SOAP 1.x エンベロープを含める必要があります。  
  
-   R4134 : SOAP 1.1 MTOM でエンコードされたメッセージの HTTP Content-Type ヘッダーには、start-info パラメーターを含める必要があります。このパラメーターには、値 text/xml を二重引用符で囲んで指定します。  
  
-   R4135 : SOAP 1.2 MTOM でエンコードされたメッセージの HTTP Content-Type ヘッダーには、start-info パラメーターを含める必要があります。このパラメーターには、値 `application/soap+xml` を二重引用符で囲んで指定します。  
  
-   R4136 : SOAP 1.x MTOM でエンコードされたメッセージの HTTP Content-Type ヘッダーには、boundary パラメーターを含める必要があります。このパラメーターには、RFC 2046 のセクション 5.1.1 で定義された MIME 境界の BNF に一致する (二重引用符で囲まれた) 値を指定します。  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     次に例を示します。  
  
     正  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     正  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     誤  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a>Infoset MIME パート  
 SOAP 1.x エンベロープは、XOP MIME パッケージのルート部分としてカプセル化され、多くの場合、`infoset` パートと呼ばれます。  
  
-   R4141 : SOAP 1.x エンベロープは、XOP MIME パッケージのルート部分としてカプセル化する必要があります。これは `infoset` パートと呼ばれ、HTTP Content-Type から参照されます。  
  
-   R4142 : SOAP `Infoset` パートには、`Content-ID`、`Content-Transfer-Encoding`、および `Content-Type` の各 MIME ヘッダーを含める必要があります。  
  
 Content-ID ヘッダーの形式は、RFC 2045 で次のように定義されています。  
  
```  
"Content-ID" ":" msg-id  
```  
  
 ここで、`msg-id` は、RFC 2822 で次のように定義されています (RFC 2045 で参照されている RFC 822 は、RFC 2822 に置き換えられています)。  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 実質的に、電子メール アドレスで囲まれたと"\<"と">"です。 `[CFWS]` プレフィックスとサフィックスは、コメントを伝達するために RFC 2822 で追加されたものですが、相互運用性を維持する場合は、使用しないことをお勧めします。  
  
 R4143 : Infoset MIME パートの Content-ID ヘッダーの値は、RFC 2822 の `msg-id` の定義内容から `[CFWS]` プレフィックスとサフィックスの部分を省略した形式に従う必要があります。  
  
 多くの MIME 実装で囲まれた値の要件が緩和"\<"と">"は電子メール アドレスを使用して`absoluteURI`で囲まれた"\<"、">"電子メール アドレス以外に、します。 このバージョンの WCF では、フォームの CONTENT-ID MIME ヘッダーの値を使用します。  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 R4144 : MTOM プロセッサは、次の厳密でない `msg-id` に一致する Content-ID ヘッダーの値を受け入れる必要があります。  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 MIME (RFC 2045) では、MIME パートのコンテンツのエンコーディングを伝達する Content-Transfer-Encoding ヘッダーを使用できます。 Content-Transfer-Encoding に定義されている既定値は 7 ビットですが、これはほとんどの SOAP メッセージに適していません。そのため、Content-Transfer-Encoding ヘッダーの相互運用性を高めるために、以下を行う必要があります。  
  
-   R4145 : SOAP Infoset パートに、Content-Transfer-Encoding ヘッダーを含める必要があります。  
  
-   R4146 : SOAP エンベロープの文字エンコーディングが UTF-8 の場合、Content-Transfer-Encoding ヘッダーの値は 8 ビットであることが必要です。  
  
-   R4147 : SOAP エンベロープの文字エンコーディングが UTF-16 の場合、Content-Transfer-Encoding ヘッダーの値はバイナリであることが必要です。  
  
-   以下の要件は、XOP のセクション 5 に基づいています。  
  
-   R4148: SOAP1.1 Infoset パートには、メディアの種類のアプリケーション/xop + xml でのコンテンツ タイプ ヘッダーを含める必要があり、パラメーターの入力"text/xml"および文字セットを =  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   R4149: SOAP Infoset パートはメディアの種類のコンテンツ タイプ ヘッダーを含める必要があります`application/xop+xml`パラメーターを入力し、="`application/soap+xml`"と`charset`です。  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     XOP では、`charset` の `application/xop+xml` パラメーターは省略可能と定義されていますが、`charset` メディア タイプの `text/xml` パラメーターについては、BP 1.1 の要件と同様の相互運用性が必要とされます。  
  
-   R41410 : `type` パラメーターと `charset` パラメーターは、SOAP 1.x Infoset パートの Content-Type ヘッダーに含まれている必要があります。  
  
#### <a name="wcf-endpoint-support-for-mtom"></a>WCF エンドポイントによる MTOM のサポート  
 MTOM の目的は、SOAP メッセージをエンコードして、Base64 でエンコードされたデータを最適化することです。 制約は次のとおりです。  
  
-   R4151 : Base64 でエンコードされたデータを含むすべての要素情報項目を最適化できます。  
  
-   B4152: WCF では、base64 でエンコードされたデータが含まれ、長さが 1024 バイトを超える要素情報項目を最適化します。  
  
 MTOM を使用するように構成 WCF エンドポイントは常に MTOM でエンコードされたメッセージを送信します。 必要な条件を満たすパートがない場合でも、メッセージは MTOM でエンコードされます (SOAP エンベロープを含む単一の MIME パートを持つ MIME パッケージとしてシリアル化されます)。  
  
### <a name="ws-policy-assertion-for-mtom"></a>MTOM の WS-Policy アサーション  
 WCF では、次のポリシー アサーションを使用して、エンドポイントで MTOM の使用方法を指定します。  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   R4211 : 上記のポリシー アサーションには、エンドポイント ポリシー サブジェクトが含まれており、MTOM を使用して、エンドポイントで送受信されるすべてのメッセージを最適化する必要があることを示しています。  
  
-   B4212: MTOM の最適化を使用するように構成、WCF エンドポイントに MTOM ポリシー アサーションを追加、対応する関連付けられているポリシー`wsdl:binding`です。  
  
### <a name="composition-with-ws-security"></a>WS-Security によるコンポジション  
 MTOM は、次のようなエンコード メカニズム`text/xml`および WCF バイナリ XML。 MTOM は、WS-Security とその他の WS-* プロトコルによる自然なコンポジションを提供します。WS-Security を使用してセキュリティ保護されたメッセージは、MTOM を使用して最適化できます。  
  
### <a name="examples"></a>使用例  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>MTOM を使用してエンコードされた WCF SOAP 1.1 メッセージ  
  
```  
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1  
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"  
Content-Type: multipart/related;type="application/xop+xml";  
              start="<http://tempuri.org/0>";start-info="text/xml";  
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
Host: 131.107.72.15  
Content-Length: 1501  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Body>  
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">  
      <array>  
        <xop:Include   
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"   
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </array>  
    </EchoBinaryAsString>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/1/632618206521093670>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
…Binary Content..  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
```  
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>MTOM を使用してエンコードされた WCF Secure SOAP 1.2 メッセージ  
 この例では、WS-Security を使用して保護されたメッセージを MTOM と SOAP 1.2 を使用してエンコードします。 エンコーディングの対象として特定されたバイナリ部分は、`BinarySecurityToken`、暗号化された署名に対応する `CipherValue` の `EncryptedData`、および暗号化された本文の内容です。 なお、`CipherValue`の`EncryptedKey`がいないで識別された最適化のため、WCF の長さが 1024 バイト未満であるためです。  
  
```  
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1  
Content-Type: multipart/related; type="application/xop+xml";  
              start="<http://tempuri.org/0>";  
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";  
              start-info="application/soap+xml";   
              action="http://xmlsoap.org/echoBinaryAsString"  
Host: 131.107.72.15  
Content-Length: 1941  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
  <s:Header>  
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">  
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>  
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>  
      </u:Timestamp>  
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">  
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </o:BinarySecurityToken>  
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedKey>  
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">  
        <o:SecurityTokenReference>  
          <o:Reference URI="#_1"/>  
        </o:SecurityTokenReference>  
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>  
      </c:DerivedKeyToken>  
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:DataReference URI="#_3"/>  
        <e:DataReference URI="#_4"/>  
      </e:ReferenceList>  
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:Reference URI="#_2"/>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>  
          <e:CipherValue>  
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
          </e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedData>  
    </o:Security>  
  </s:Header>  
  <s:Body u:Id="_0">  
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
          <o:Reference URI="#_2"/>  
        </o:SecurityTokenReference>  
      </KeyInfo>  
      <e:CipherData>  
        <e:CipherValue>  
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
        </e:CipherValue>  
      </e:CipherData>  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/1/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary content of BinarySecurityToken - X509 Certificate...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/2/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted primary signature...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/3/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted Body...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--  
```
