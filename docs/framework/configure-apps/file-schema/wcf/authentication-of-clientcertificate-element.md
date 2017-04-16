---
title: "&lt;clientCertificate&gt; 要素の &lt;authentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# &lt;clientCertificate&gt; 要素の &lt;authentication&gt;
サービスによって使用されるクライアント証明書の認証動作を指定します。  
  
## 構文  
  
```  
  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|customCertificateValidatorType|省略可能な文字列。  カスタム型の検証に使用される型およびアセンブリです。  `certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。|  
|certificateValidationMode|省略可能な列挙体です。  資格情報の検証に使用されるモードのいずれかを指定します。  この属性は [System.Servicemodel.Security.X509CertificateValidationMode](assetId:///System.Servicemodel.Security.X509CertificateValidationMode?qualifyHint=False&amp;autoUpgrade=True) 型です。  `Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。  既定値は、`ChainTrust` です。|  
|includeWindowsGroups|省略可能なブール。  セキュリティ コンテキストに Windows グループが含まれているかどうかを指定します。  この属性を `true` に設定すると、グループ全体が拡張されるため、パフォーマンスに影響が及びます。  ユーザーが属するグループの一覧を生成する必要がない場合は、この属性を `false` に設定します。|  
|mapClientCertificateToWindowsAcccount|ブール型。  証明書を使用してクライアントを Windows ID にマップできるかどうかを指定します。  これを行うには、Active Directory が有効である必要があります。|  
|revocationMode|省略可能な列挙体です。  証明書失効リスト \(RCL\) のチェックに使用されるモードのいずれかです。  既定値は、`Online` です。  この値は、HTTP トランスポート セキュリティを使用する場合は無視されます。|  
|trustedStoreLocation|省略可能な列挙体です。  2 つのシステム格納場所 \(`LocalMachine` または `CurrentUser`\) のいずれかです。  この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。  指定された格納場所の **\[信頼されたユーザー\]** ストアに対して検証が実行されます。  既定値は、`CurrentUser` です。|  
  
## customCertificateValidatorType 属性  
  
|値|説明|  
|-------|--------|  
|String|タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。|  
  
## certificateValidationMode 属性  
  
|値|説明|  
|-------|--------|  
|列挙型|None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom のいずれかの値にします。<br /><br /> 詳細については、「[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。|  
  
## revocationMode 属性  
  
|値|説明|  
|-------|--------|  
|列挙型|NoCheck、Online、Offline のいずれかの値にします。  詳細については、「[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。|  
  
## trustedStoreLocation 属性  
  
|値|説明|  
|-------|--------|  
|列挙型|`LocalMachine` または `CurrentUser` のいずれかの値にします。  既定値は、`CurrentUser` です。  クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。  クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|サービスに対するクライアントの認証に使用する X.509 証明書を定義します。|  
  
## 解説  
 `<authentication>` 要素は、<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> クラスに対応します。  この要素を使用すると、クライアントを認証する方法をカスタマイズできます。  `certificateValidationMode` 属性は、`None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust`、または `Custom` に設定できます。  既定のレベルは `ChainTrust` に設定され、チェーンの最上位の*ルート証明機関*で終了する証明書の階層構造で各証明書を検索するよう指定します。  これは最もセキュリティで保護されているモードです。  また、値を `PeerOrChainTrust` に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 \(ピア信頼\) も受け入れるよう指定します。  自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。  クライアントを展開するときは、代わりに `ChainTrust` 値を使用します。  
  
 また、値を `Custom` に設定することもできます。  `Custom` 値に設定する場合は、`customCertificateValidatorType` 属性を、証明書の検証に使用するアセンブリと型に設定する必要もあります。  独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。  詳細については、「[方法 : カスタム証明書検証を使用するサービスを作成する](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)」を参照してください。  
  
## 使用例  
 次のコードは、`<authentication>` 要素の X.509 証明書とカスタム検証タイプを指定します。  
  
```  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## 参照  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>   
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>   
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>   
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>   
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [方法 : カスタム証明書検証を使用するサービスを作成する](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)   
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)