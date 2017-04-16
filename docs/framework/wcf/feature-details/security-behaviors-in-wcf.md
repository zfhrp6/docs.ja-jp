---
title: "Windows Communication Foundation のセキュリティ動作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
caps.latest.revision: 23
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 23
---
# Windows Communication Foundation のセキュリティ動作
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、さまざまな動作によって、サービス レベルまたはエンドポイント レベルで実行時の動作が変更されます \(一般的な動作[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[サービスのランタイム動作の指定](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)」を参照してください\)。*"セキュリティ動作"* により、資格情報、認証、承認、および監査ログの制御が可能になります。動作は、プログラムまたは構成を通じて使用できます。ここでは、セキュリティ機能に関連する以下の動作の構成について説明します。  
  
-   [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
-   [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).  
  
-   [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md).  
  
-   [\<serviceSecurityAudit\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)。この要素を使用すると、クライアントがメタデータを取得するためにアクセスできる、セキュリティで保護されたエンドポイントを指定することもできます。  
  
## 動作を使用した資格情報の設定  
 サービスまたはクライアントの資格情報の値を設定するには、[\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)と [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)を使用します。基になるバインディング構成によって、資格情報を設定する必要があるかどうかが決まります。たとえば、セキュリティ モードが `None` に設定されている場合、クライアントとサービスは相互に認証を行わないため、どの種類の資格情報も必要ありません。  
  
 一方、サービス バインディングでは、クライアント資格情報の種類が必要になることがあります。その場合は、動作を使用して資格情報の値を設定することが必要になる場合があります \(使用できる資格情報の種類[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[資格情報の種類の選択](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)」を参照してください\)。Windows 資格情報を使用して認証を行う場合などは、実際の資格情報の値が環境によって自動的に設定されるため、資格情報の別のセットを指定する場合を除き、資格情報の値を明示的に設定する必要がないこともあります。  
  
 すべてのサービス資格情報は、[\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)の子要素として存在します。サービス資格情報として使用される証明書を次の例に示します。  
  
```  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"   
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## サービス資格情報  
 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) には 4 つの子要素があります。以下のセクションでは、これらの要素とそれぞれの使い方について説明します。  
  
### \<serviceCertificate\> 要素  
 メッセージ セキュリティ モードを使用しているクライアントへのサービスの認証に使用する X.509 証明書を指定するには、この要素を使用します。定期的に更新される証明書を使用している場合は、証明書のサムプリントが変更されます。その場合、証明書を同じサブジェクト名で再発行できるため、`X509FindType` としてサブジェクト名を使用します。  
  
 この要素の使い方[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : クライアントの資格情報の値を指定する](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)」を参照してください。  
  
### \<clientCertificate\> 要素の \<certificate\>  
 [\<certificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) 要素は、サービスがクライアントと安全に通信するために、クライアントの証明書をあらかじめ持っている必要がある場合に使用します。このような状況は、双方向通信パターンを使用する場合に生じます。より一般的な要求\/応答パターンでは、クライアントが自身の証明書を要求に含め、サービスはこの証明書を使用して、クライアントへの応答をセキュリティで保護します。ただし、双方向通信パターンには要求も応答もありません。サービスは、クライアントの証明書を通信から推測できないため、クライアントへのメッセージをセキュリティで保護するためにクライアントの証明書が前もって必要になります。このため、クライアントの証明書を帯域外方式で取得し、この要素を使用して証明書を指定する必要があります。双方向サービス[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)」を参照してください。  
  
### \<clientCertificate\> 要素の \<authentication\>  
 [\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) 要素を使用すると、クライアントを認証する方法をカスタマイズできます。`CertificateValidationMode` 属性は、`None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust`、または `Custom` に設定できます。既定のレベルは `ChainTrust` に設定され、チェーンの最上位の*ルート証明機関*で終了する証明書の階層構造で各証明書を検索するよう指定します。これは最もセキュリティで保護されているモードです。また、値を `PeerOrChainTrust` に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 \(ピア信頼\) も受け入れるよう指定します。自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。クライアントを展開するときは、代わりに `ChainTrust` 値を使用します。また、値を `Custom` に設定することもできます。`Custom` 値に設定する場合は、`CustomCertificateValidatorType` 属性を、証明書の検証に使用するアセンブリと型に設定する必要もあります。独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。  
  
### \<issuedTokenAuthentication\> 要素  
 発行されるトークンのシナリオには、3 つの段階があります。まず、サービスにアクセスしようとしているクライアントは、*セキュリティ トークン サービス* \(STS\) に回されます。次に、STS がクライアントを認証し、その後、クライアントにトークン \(通常は、SAML \(Security Assertions Markup Language\) トークン\) を発行します。最後に、クライアントがトークンを持ってサービスに戻ります。サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。[\<issuedTokenAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 要素は、このようなセキュリティ トークン サービス証明書のリポジトリです。証明書を追加するには、[\<knownCertificates\>](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md) を使用します。次の例に示すように、証明書ごとに [\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) を挿入します。  
  
```  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 既定では、証明書はセキュリティ トークン サービスから取得する必要があります。このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。  
  
 `SamlSecurityToken` セキュリティ トークンを発効する*セキュリティ トークン サービス* \(STS\) を利用するフェデレーション アプリケーション内の [\<allowedAudienceUris\>](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md) コレクションを使用する必要があります。STS がセキュリティ トークンを発行する場合、このセキュリティ トークンに `SamlAudienceRestrictionCondition` を追加して、セキュリティ トークンの提供先となる Web サービスの URI を指定できます。これにより、受け取り側 `SamlSecurityTokenAuthenticator` Web サービスは、次のようにしてこのチェックが行われるように指定することで、発行されたセキュリティ トークンがこの Web サービスを対象としていることを確認できます。  
  
-   [\<issuedTokenAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) の `audienceUriMode` 属性を `Always`または `BearerKeyOnly` に設定します。  
  
-   このコレクションに URI を追加して、有効な URI のセットを指定します。それには、各 URI に [\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) を挿入します。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 この構成要素の使い方[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : フェデレーション サービスで資格情報を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)」を参照してください。  
  
#### 匿名の CardSpace ユーザーの許可  
 `<IssuedTokenAuthentication>` 要素の `AllowUntrustedRsaIssuers` 属性を `true` に設定すると、任意の RSA キー ペアで署名された自己発行トークンを提示することがすべてのクライアントに明示的に許可されます。このキーには、発行者のデータが関連付けられていないため、発行者は*信頼できません*。[!INCLUDE[infocard](../../../../includes/infocard-md.md)] ユーザーは、ID の自己提供クレームを含む自己発行カードを作成できます。この機能を使用するときは十分に注意してください。この機能を使用する場合は、RSA 公開キーを、ユーザー名と一緒にデータベースに格納する必要のある比較的安全なパスワードとして考えます。サービスへのクライアント アクセスを許可する前に、クライアントから提示された RSA 公開キーを、提示されたユーザー名に対応する格納済みの公開キーと比較して検証します。これは、ユーザーが各自のユーザー名を登録し、自己発行の RSA 公開キーに関連付けることができる登録プロセスが確立されていることが前提となります。  
  
## クライアント資格情報  
 クライアント資格情報は、相互認証が必要な場合にサービスに対するクライアントの認証に使用されます。また、このセクションを使用して、クライアントがサービスの証明書によってサービスへのメッセージをセキュリティで保護する必要がある場合に使用するサービス証明書を指定することもできます。  
  
 セキュリティ トークン サービスまたはローカル発行者から発行されたトークンを使用するフェデレーション シナリオの一部として、クライアントを構成することもできます。フェデレーション シナリオ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[フェデレーションと発行済みトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)」を参照してください。次のコードに示すように、すべてのクライアント資格情報は、[\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)にあります。  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"     
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"   
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### \<clientCertifictate\> 要素  
 この要素で、クライアントの認証に使用する証明書を設定します。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : クライアントの資格情報の値を指定する](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### \<httpDigest\>  
 この機能は、Windows の Active Directory およびインターネット インフォメーション サービス \(IIS\) と共に有効にする必要があります。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「[IIS 6.0 のダイジェスト認証](http://go.microsoft.com/fwlink/?LinkId=88443)」を参照してください。  
  
#### \<issuedToken\> 要素  
 [\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) には、トークンのローカル発行者やセキュリティ トークン サービスで使用する動作の構成に使用する要素が含まれます。ローカル発行者を使用するようにクライアントを構成する手順については、「[方法 : ローカル発行者を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)」を参照してください。  
  
#### \<ocalIssuerAddress\>  
 既定のセキュリティ トークン サービス アドレスを指定します。この要素を使用するのは、<xref:System.ServiceModel.WSFederationHttpBinding> がセキュリティ トークン サービスに URL を提供しない場合、またはフェデレーション バインディングの発行者アドレスが http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous または `null` の場合です。そのような場合、<xref:System.ServiceModel.Description.ClientCredentials> は、ローカルの発行者およびバインディングのアドレスと共に構成し、その発行者と通信するために使用する必要があります。  
  
#### \<issuerChannelBehaviors\>  
 セキュリティ トークン サービスとの通信時に使用する  クライアントの動作を追加するには、[\<issuerChannelBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を使用します。[\<endpointBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) セクションでクライアントの動作を定義します。定義された動作を使用するには、\<`add`\> 要素を `<issuerChannelBehaviors>` 要素に追加し、2 つの属性を設定します。次の例に示すように、`issuerAddress` をセキュリティ トークン サービスの URL に設定し、`behaviorConfiguration` 属性を定義済みのエンドポイントの動作の名前に設定します。  
  
```  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### \<serviceCertificate\> 要素  
 サービス証明書の認証を制御するには、この要素を使用します。  
  
 [\<defaultCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) 要素には、サービスで証明書が指定されていないときに使用する証明書を 1 つ格納できます。  
  
 特定のサービスに関連付けられているサービス証明書を設定するには、[\<scopedCertificates\>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)[\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) と  を使用します。`<add>` 要素には、証明書をサービスに関連付けるために使用する `targetUri` 属性があります。  
  
 [\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) 要素は、証明書の認証に使用する信頼のレベルを指定します。既定のレベルは "ChainTrust" に設定され、チェーンの最上位の信頼された証明機関で終了する証明書の階層構造で各証明書を検索するよう指定します。これは最もセキュリティで保護されているモードです。また、値を "PeerOrChainTrust" に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 \(ピア信頼\) も受け入れることを指定します。自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。クライアントを展開するときは、代わりに "ChainTrust" 値を使用します。値を "Custom" または "None" に設定できます。"Custom" 値を使用するには、`CustomCertificateValidatorType` 属性も証明書の検証に使用するアセンブリと型に設定する必要があります。独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : カスタム証明書検証を使用するサービスを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 [\<authentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) `RevocationMode 要素には、証明書が失効していないかどうかをチェックする方法を指定する`  属性が含まれます。既定値は "online" です。この場合、証明書が失効していないかどうかが自動的にチェックされます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## ServiceAuthorization  
 [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) 要素には、承認、カスタム ロール プロバイダー、および偽装に影響する要素が含まれます。  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスは、サービス メソッドに適用されます。この属性は、保護メソッドの使用を承認するときに使用するユーザー グループを指定します。既定値は "UseWindowsGroups" で、リソースにアクセスしようとしている ID を Windows グループ \("管理者" や "ユーザー" など\) で検索するよう指定します。次のコードに示すように、"UseAspNetRoles" を指定して、\<`system.web` \> 要素の下で構成されるカスタム ロール プロバイダーを使用することもできます。  
  
```  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 `principalPermissionMode` 属性で `roleProviderName` を使用する方法を次のコードに示します。  
  
```  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## セキュリティ監査の構成  
 書き込み先のログとログに記録するイベントの種類を指定するには、[\<serviceSecurityAudit\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) を使用します。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
```  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## セキュリティで保護されたメタデータ交換  
 メタデータをクライアントにエクスポートすると、構成やクライアント コードのダウンロードが可能になるため、サービスとクライアントの開発者にとって便利です。サービスが悪意のあるユーザーに公開されないようにするために、SSL over HTTP \(HTTPS\) 機構を使用して転送をセキュリティで保護できます。転送を保護するには、まず、サービスをホストしているコンピューターの特定のポートに適切な X.509 証明書をバインドする必要があります \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).\)次に、[\<serviceMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)`HttpsGetEnabled`をサービス構成に追加し、`true` 属性を  に設定します。最後に、次の例に示すように、`HttpsGetUrl` 属性をサービス メタデータ エンドポイントの URL に設定します。  
  
```  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## 参照  
 [監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)   
 [Windows Server AppFabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)