---
title: "方法 : 双方向フェデレーション バインディングを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 方法 : 双方向フェデレーション バインディングを作成する
<xref:System.ServiceModel.WSFederationHttpBinding> はデータグラムと要求\/応答メッセージの交換コントラクトのみをサポートします。双方向メッセージ交換コントラクトを使用するには、カスタム バインディングを作成する必要があります。次の手順は、構成の中でそれを行う方法を説明します。HTTP と TCP トランスポートにはメッセージ モード セキュリティを、TCP トランスポートには混合モード セキュリティを使用します。このトピックの最後に 3 つのバインディングすべてのサンプル コードがあります。  
  
 バインディングはコード内でも作成できます。作成するバインド要素スタックの詳細については、「[方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)」を参照してください。  
  
### HTTP で双方向カスタム フェデレーション バインディングを作成するには  
  
1.  構成ファイルの [\<bindings\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)[\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) 要素を作成します。  
  
2.  [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) 要素内で、`name` 属性が `FederationDuplexHttpMessageSecurityBinding` に設定された [\<binding\>](../../../../docs/framework/misc/binding.md) 要素を作成します。  
  
3.  [\<binding\>](../../../../docs/framework/misc/binding.md) 要素内で、`authenticationMode` 属性が `SecureConversation` に設定された [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素を作成します。  
  
4.  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素内で、`authenticationMode` 属性が `IssuedTokenForCertificate` または `IssuedTokenForSslNegotiated` に設定された [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) 要素を作成します。  
  
5.  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素に続いて、空の [\<compositeDuplex\>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) 要素を作成します。  
  
6.  [\<compositeDuplex\>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) 要素に続いて、空の [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素を作成します。  
  
7.  [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素に続いて、空の [\<httpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) 要素を作成します。  
  
### TCP メッセージ セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには  
  
1.  構成ファイルの [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)[\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素を作成します。  
  
2.  [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素内で、`name` 属性が `FederationDuplexTcpMessageSecurityBinding` に設定された [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素を作成します。  
  
3.  [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素内で、`authenticationMode` 属性が `SecureConversation` に設定された [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素を作成します。  
  
4.  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素内で、`authenticationMode` 属性が `IssuedTokenForCertificate` または `IssuedTokenForSslNegotiated` に設定された [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) 要素を作成します。  
  
5.  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素に続いて、空の [\<tcpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) 要素を作成します。  
  
### TCP 混合セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには  
  
1.  構成ファイルの [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)[\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素を作成します。  
  
2.  [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素内で、`name` 属性が `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` に設定された [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素を作成します。  
  
3.  [\<oneWay\>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) 要素内で、`authenticationMode` 属性が `SecureConversation` に設定された [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素を作成します。  
  
4.  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素内で、`authenticationMode` 属性が `IssuedTokenForCertificate` または `IssuedTokenForSslNegotiated` に設定された [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) 要素を作成します。  
  
5.  [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) 要素に続いて、空の [\<sslStreamSecurity\>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) 要素を作成します。  
  
6.  [\<sslStreamSecurity\>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) 要素に続いて、空の [\<tcpTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) 要素を作成します。  
  
## サンプル コード  
  
#### 3 つのバインディングの例  
  
1.  次のコードを構成ファイルに挿入します。  
  
## 使用例  
  
```  
  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
  
```