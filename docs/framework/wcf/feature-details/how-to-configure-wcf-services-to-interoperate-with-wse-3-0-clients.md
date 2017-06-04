---
title: "方法 : WCF サービスと WSE 3.0 クライアントを相互運用するために構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : WCF サービスと WSE 3.0 クライアントを相互運用するために構成する
[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが WS\-Addressing 仕様の 2004 年 8 月版を使用して構成されている場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスは Microsoft .NET クライアントの WSE \(Web サービス拡張\) 3.0 とネットワーク レベルで互換性があります。  
  
### WCF サービスを WSE 3.0 クライアントと相互運用できるようにするには  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのカスタム バインディングを定義します。  
  
     メッセージ エンコーディングに 2004 年 8 月版の WS\-Addressing 仕様が使用されるように指定するには、カスタム バインディングを作成する必要があります。  
  
    1.  サービスの構成ファイルの [\<bindings\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) に子要素として [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)を追加します。  
  
    2.  [\<binding\>](../../../../docs/framework/misc/binding.md)を [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)に追加して、`name` 属性を設定することにより、バインディングの名前を指定します。  
  
    3.  [\<binding\>](../../../../docs/framework/misc/binding.md)の子要素として[\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を追加することで、WSE 3.0 と互換性があるメッセージをセキュリティ保護するために使用される認証モードと WS\-Security 仕様のバージョンを指定します。  
  
         認証モードを設定するには、[\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の `authenicationMode` 属性を設定します。認証モードは、WSE 3.0 の設定不要のセキュリティ アサーションとほぼ同等です。次の表に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の認証モードと WSE 3.0 の設定不要のセキュリティ アサーションとの対応を示します。  
  
        |WCF 認証モード|WSE 3.0 の設定不要のセキュリティ アサーション|  
        |---------------|---------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`mutualCertificate10Security`\*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`mutualCertificate11Security`\*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`usernameForCertificateSecurity`|  
  
         \* `mutualCertificate10Security` と `mutualCertificate11Security` の設定不要のセキュリティ アサーションとの主な相違点の 1 つに、WSE が SOAP メッセージのセキュリティ保護で使用する WS\-Security 仕様のバージョンがあります。`mutualCertificate10Security` では WS\-Security 1.0 が使用され、`mutualCertificate11Security` では WS\-Security 1.1 が使用されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、WS\-Security 仕様のバージョンは [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の `messageSecurityVersion` 属性で指定されます。  
  
         セキュリティ保護された SOAP メッセージで使用される WS\-Security 仕様のバージョンを設定するには、[\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の `messageSecurityVersion` 属性を設定します。WSE 3.0 と相互運用するには、`messageSecurityVersion` 属性の値を <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> に設定します。  
  
    4.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が 2004 年 8 月版の WS\-Addressing 仕様を使用することを指定するには、[\<textMessageEncoding\>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)を追加し、その `messageVersion` の値を <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> に設定します。  
  
        > [!NOTE]
        >  SOAP 1.2 の使用時には、`messageVersion` 属性を <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A> に設定します。  
  
2.  サービスがカスタム バインディングを使用するように指定します。  
  
    1.  [\<endpoint\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)要素の `binding` 属性を `customBinding` に設定します。  
  
    2.  [\<endpoint\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)要素の `bindingConfiguration` 属性をカスタム バインディングの[\<binding\>](../../../../docs/framework/misc/binding.md)の `name` 属性で指定されている値に設定します。  
  
## 使用例  
 次のコード例では、`Service.HelloWorldService` が WSE 3.0 クライアントと相互運用するためにカスタム バインディングを使用するように指定します。カスタム バインディングには 2004 年 8 月版の WS\-Addressing が指定され、WS\-Security 1.1 の一連の仕様が、交換されるメッセージのエンコードに使用されます。メッセージは、<xref:System.ServiceModel.Configuration.AuthenticationMode> 認証モードを使用してセキュリティ保護されます。  
  
```  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        behaviorConfiguration="ServiceBehavior"   
        name="Service.HelloWorldService">  
        <endpoint binding="customBinding" address=""  
          bindingConfiguration="ServiceBinding"  
          contract="Service.IHelloWorld"></endpoint>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="ServiceBinding">  
          <security authenticationMode="AnonymousForCertificate"  
                  messageProtectionOrder="SignBeforeEncrypt"  
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"  
                  requireDerivedKeys="false">  
          </security>  
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">  
        <serviceCredentials>  
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>  
        </serviceCredentials>  
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## 参照  
 [方法 : システム指定のバインディングをカスタマイズする](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)