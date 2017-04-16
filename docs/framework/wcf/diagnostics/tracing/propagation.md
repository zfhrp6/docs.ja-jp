---
title: "伝達 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 伝達
このトピックでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] トレース モデルのアクティビティ伝達について説明します。  
  
## 伝達を使用したエンドポイント間でのアクティビティの関連付け  
 伝達を使用することで、複数のアプリケーション エンドポイントについて、同じ処理単位 \(要求など\) のエラー トレースを直接関連付けることができます。  さまざまなエンドポイントで発生した同じ処理単位のエラーは、アプリケーション ドメインが異なる場合でも同じアクティビティとしてグループ化されます。  これは、メッセージ ヘッダーで特定のアクティビティ ID を伝達することによって実現されます。  したがって、サーバーの内部エラーによってクライアントがタイムアウトした場合、これらのエラーは直接関係しているので、どちらも同じアクティビティに表示されます。  
  
 これを行うには、前述の例に示すように `ActivityTracing` 設定を使用します。  さらに、すべてのエンドポイントで `System.ServiceModel` トレース ソースの `propagateActivity` 属性を設定します。  
  
```  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity=”true” >  
```  
  
 アクティビティの伝達は構成可能な機能です。この機能を構成すると、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は TLS のアクティビティ ID が含まれたヘッダーを送信メッセージに追加します。  サーバー側の以降のトレースでこの ID を含めることにより、クライアントとサーバーのアクティビティを相互に関連付けることができます。  
  
## 伝達の定義  
 次のすべての条件に該当する場合に、アクティビティ M の gAId がアクティビティ N に伝達されます。  
  
-   M に起因して N が作成された。  
  
-   M の gAId を N が認識している。  
  
-   N の gAId と M の gAId が同じである。  
  
 次の XML スキーマに示すように、gAId は ActivityId メッセージ ヘッダーによって伝達されます。  
  
```  
<xsd:element name=”ActivityId” type=”integer” minOccurs=”0”>  
  <xsd:attribute name=”CorrelationId” type=”integer” minOccurs=”0”/>  
</xsd:element>  
```  
  
 メッセージ ヘッダーの例を次に示します。  
  
```  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"     
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"   
  
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## 伝達とアクティビティ境界  
 エンドポイント間でアクティビティ ID が伝達されると、メッセージの受信側は、その \(伝達された\) アクティビティ ID を使用して Start トレースと Stop トレースを出力します。  したがって、各トレース ソースごとに、該当の gAId を持つ Start\/Stop トレースが存在することになります。  複数のエンドポイントが同じプロセス内に存在し、同じトレース ソース名を使用している場合、同じ lAId \(同じ gAId、同じトレース ソース、同じプロセス\) を持つ複数の Start と Stop が作成されます。  
  
## 同期  
 異なるコンピューター上で実行されるエンドポイント間でイベントを同期するには、メッセージ内で伝達される ActivityId ヘッダーに CorrelationId を追加します。  ツールはこの ID を使用することにより、クロックにずれのあるコンピューター間でもイベントを同期できます。  具体的に言うと、サービス トレース ビューアー ツールは、エンドポイント間のメッセージ フローを示す際に、この ID を使用します。  
  
## 参照  
 [トレースの構成](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)   
 [サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)   
 [エンドツーエンドのトレースのシナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)   
 [サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)