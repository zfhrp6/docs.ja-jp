---
title: "負荷分散 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "負荷分散 [WCF]"
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 負荷分散
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションの処理能力を増加する方法の 1 つは、アプリケーションを負荷分散されたサーバー ファームに配置することでスケール アウトすることです。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションは、ハードウェア ベースの負荷分散アプリケーションの他に Windows Network Load Balancing のようなソフトウェアによる負荷分散も含む、標準的な負荷分散手法を使用して負荷分散することが可能です。  
  
 以下のセクションでは、システム提供の各種のバインディングを使用して構築された [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションを負荷分散するときの考慮事項について説明します。  
  
## 基本 HTTP バインディングによる負荷分散  
 負荷分散の面から見た場合、<xref:System.ServiceModel.BasicHttpBinding> を使用して通信を行う [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションと、他の一般的なタイプの HTTP ネットワーク トラフィック \(静的な HTML コンテンツ、ASP.NET ページ、ASMX Web サービス\) との相違はありません。このバインディングを使用する [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] チャネルは本質的に状態がなく、チャネルが閉じると接続を終了します。したがって、<xref:System.ServiceModel.BasicHttpBinding> には既存の HTTP 負荷分散の手法で十分に対応できます。  
  
 既定では、<xref:System.ServiceModel.BasicHttpBinding> は、メッセージの接続 HTTP ヘッダーで `Keep-Alive` 値を送信することで、サポートするサービスにクライアントが永続的な接続を確立できるようにします。この構成では、以前に確立した接続を再使用して同じサーバーへの後続するメッセージを送信できるため、スループットが向上します。ただし、接続を再使用すると、クライアントが負荷分散ファーム内の特定サーバーと強く関連付けられてしまうため、ラウンドロビン方式の負荷分散の効果を損ねることがあります。これを回避するには、<xref:System.ServiceModel.Channels.CustomBinding> またはユーザー定義の <xref:System.ServiceModel.Channels.Binding> で <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> プロパティを使用して、サーバーの HTTP `Keep-Alive` を無効にできます。構成を使用してこれを行う例を次に示します。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] で導入された簡略化された構成を使用すると、次の簡略化された構成で同じ動作を実現できます。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme=”http” binding=”customBinding” />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
  
```  
  
 既定のエンドポイント、バインディング、および動作[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)」および「[WCF サービスの簡略化された構成](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
## WSHttp バインディングおよび WSDualHttp バインディングによる負荷分散  
 <xref:System.ServiceModel.WSHttpBinding> と <xref:System.ServiceModel.WSDualHttpBinding> はどちらも、既定のバインディング構成をいくつか変更すれば、HTTP の負荷分散手法を使用して負荷分散できます。  
  
-   セキュリティ コンテキストの確立を無効にします。これは、<xref:System.ServiceModel.WSHttpBinding> の <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> プロパティを `false` に設定することで実現されます。あるいは、セキュリティ セッションが必要な場合は、「[セキュリティで保護されたセッション](../../../docs/framework/wcf/feature-details/secure-sessions.md)」のトピックで説明しているステートフルなセキュリティ セッションを使用することも可能です。ステートフルなセキュリティ セッションは、セキュリティ セッションのすべての状態 \(ステート\) を保護セキュリティ トークンの一部として要求ごとに転送するため、サービスをステートレスな状態に保つことができます。ステートフルなセキュリティ セッションを有効にする場合、システムによって提供される <xref:System.ServiceModel.WSHttpBinding> と <xref:System.ServiceModel.WSDualHttpBinding> では、必要な構成設定が公開されないため、<xref:System.ServiceModel.Channels.CustomBinding> またはユーザー定義の <xref:System.ServiceModel.Channels.Binding> を使用する必要があります。  
  
-   信頼できるセッションを使用しないでください。この機能は既定で無効になっています。  
  
## Net.TCP バインディングの負荷分散  
 <xref:System.ServiceModel.NetTcpBinding> は、IP レイヤー負荷分散の手法を使用して負荷分散できます。ただし、<xref:System.ServiceModel.NetTcpBinding> は接続の待ち時間を減らすために、既定で TCP 接続のプールを作成します。この最適化は、負荷分散の基本的なメカニズムに干渉します。<xref:System.ServiceModel.NetTcpBinding> を最適化するための主な構成値はリース タイムアウトで、これは接続プール設定の一部です。接続プールによって、クライアントの接続がファーム内の特定サーバーと関連付けられます。このような接続の有効期間 \(これはリース タイムアウトの設定で制御される要素です\) が長くなるにつれて、ファーム内の各サーバーの負荷分散がうまくいかなくなります。その結果、平均呼び出し時間が増加します。したがって、<xref:System.ServiceModel.NetTcpBinding> を負荷分散シナリオで使用する場合は、バインディングによって使用される既定のリース タイムアウトを少なくすることを検討してください。負荷分散のシナリオでは、30 秒のリース タイムアウトから始めるのが合理的ですが、最適値はアプリケーションによって異なります。チャネルのリース タイムアウトおよびその他のトランスポート クォータの詳細については、「[トランスポート クォータ](../../../docs/framework/wcf/feature-details/transport-quotas.md)」を参照してください。  
  
 負荷分散のシナリオで最適なパフォーマンスを実現するには、<xref:System.ServiceModel.NetTcpSecurity> \(<xref:System.ServiceModel.SecurityMode> または <xref:System.ServiceModel.SecurityMode>\) を使用することを検討してください。  
  
## 参照  
 [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)