---
title: '方法 : WCF サービスと WSE 3.0 クライアントを相互運用するために構成する'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 174ecd279f9380136532ce0d5105b7a71b6d88da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495110"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>方法 : WCF サービスと WSE 3.0 クライアントを相互運用するために構成する
Windows Communication Foundation (WCF) サービスは、Ws-addressing 仕様の 2004 年 8 月版を使用して WCF サービスが構成されている場合、Microsoft .NET (WSE) クライアント Web サービス拡張 3.0 とネットワーク レベルで互換性です。  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>WCF サービスを WSE 3.0 クライアントと相互運用できるようにするには  
  
1.  WCF サービス用のカスタム バインドを定義します。  
  
     メッセージ エンコーディングに 2004 年 8 月版の WS-Addressing 仕様が使用されるように指定するには、カスタム バインドを作成する必要があります。  
  
    1.  子を追加[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)を[\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)のサービスの構成ファイル。  
  
    2.  追加することにより、バインディングの名前を指定、 [\<バインディング >](../../../../docs/framework/misc/binding.md)を[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)と設定、`name`属性。  
  
    3.  認証モードと子を追加することで WSE 3.0 と互換性のあるメッセージをセキュリティ保護に使用される Ws-security の仕様のバージョンを指定[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を[ \<バインド >](../../../../docs/framework/misc/binding.md)です。  
  
         認証モードを設定するには、設定、`authenicationMode`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)です。 認証モードは、WSE 3.0 の設定不要のセキュリティ アサーションとほぼ同等です。 次の表は、WCF での認証モードを WSE 3.0 の設定不要のセキュリティ アサーションにマップします。  
  
        |WCF 認証モード|WSE 3.0 の設定不要のセキュリティ アサーション|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* 主な違いの 1 つ、`mutualCertificate10Security`と`mutualCertificate11Security`設定不要のセキュリティ アサーションは、WSE が SOAP メッセージをセキュリティ保護に使用する Ws-security 仕様のバージョン。 `mutualCertificate10Security` では WS-Security 1.0 が使用され、`mutualCertificate11Security` では WS-Security 1.1 が使用されます。 WCF, Ws-security 仕様のバージョンを指定、`messageSecurityVersion`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)です。  
  
         SOAP メッセージをセキュリティで保護するために使用する Ws-security 仕様のバージョンを設定するには、設定、`messageSecurityVersion`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)です。 WSE 3.0 と相互運用するには、`messageSecurityVersion` 属性の値を <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> に設定します。  
  
    4.  追加することで、WCF によって Ws-addressing 仕様の 2004 年 8 月版を使用する指定、 [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)設定と、`messageVersion`をその値に<xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>です。  
  
        > [!NOTE]
        >  SOAP 1.2 の使用時には、`messageVersion` 属性を <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A> に設定します。  
  
2.  サービスがカスタム バインドを使用するように指定します。  
  
    1.  設定、`binding`の属性、 [\<エンドポイント >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)要素を`customBinding`です。  
  
    2.  設定、`bindingConfiguration`の属性、 [\<エンドポイント >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)要素で指定された値を`name`の属性、 [\<バインディング >](../../../../docs/framework/misc/binding.md)カスタムバインディング。  
  
## <a name="example"></a>例  
 次のコード例では、`Service.HelloWorldService` が WSE 3.0 クライアントと相互運用するためにカスタム バインディングを使用するように指定します。 カスタム バインディングには 2004 年 8 月版の WS-Addressing が指定され、WS-Security 1.1 の一連の仕様が、交換されるメッセージのエンコードに使用されます。 メッセージは、<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> 認証モードを使用してセキュリティ保護されます。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 [方法 : システム指定のバインディングをカスタマイズする](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
