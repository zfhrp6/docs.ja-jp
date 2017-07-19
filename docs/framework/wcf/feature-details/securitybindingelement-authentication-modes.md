---
title: "SecurityBindingElement 認証モード | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# SecurityBindingElement 認証モード
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] には、クライアントとサービスが互いに認証するためのモードが複数あります。<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの静的メソッドまたは構成を使用して、この認証モード用のセキュリティ バインド要素を作成できます。このトピックでは、18 の認証モードについて簡単に説明します。  
  
 認証モードのいずれかで要素を使用する例については、「[方法 : 指定した認証モード用の SecurityBindingElement を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)」を参照してください。  
  
## 基本的な構成プログラミング  
 構成ファイルで認証モードを設定する手順を次に示します。  
  
#### 構成で認証モードを設定するには  
  
1.  [\<bindings\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 要素に、[\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)を追加します。  
  
2.  子要素として、[\<binding\>](../../../../docs/framework/misc/binding.md) 要素を `<customBinding>` 要素に追加します。  
  
3.  `<security>` 要素を `<binding>` 要素に追加します。  
  
4.  `authenticationMode` 属性を、以下で説明する値のいずれかに設定します。たとえば、次のコードによりモードは `AnonymousForCertificate` に設定されます。  
  
    ```  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### プログラムでモードを設定するには  
  
1.  戻り値の型を決めます。<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>、<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>、<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>、または <xref:System.ServiceModel.Channels.SecurityBindingElement> のいずれかを指定できます。  
  
2.  <xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの適切な静的メソッドを呼び出します。たとえば、次のコードは <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> メソッドを呼び出します。  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  カスタム バインディングを作成するにはバインド要素を使用します。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## モードの説明  
  
### AnonymousForCertificate  
 この認証モードでは、クライアントは匿名になり、X.509 証明書を使用してサービスが認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> メソッドによって返される <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> です。または、\<`security`\> 要素の `authenticationMode` 属性を `AnonymousForCertificate` に設定します。  
  
### AnonymousForSslNegotiated  
 この認証モードでは、クライアントが匿名になり、実行時にネゴシエートされる X.509 証明書を使用してサービスが認証されます。セキュリティ バインド要素は、最初のパラメーターに `false` の値が渡される場合に <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> メソッドによって返される <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> です。代わりに、`authenticationMode` 属性に `AnonymousForSslNegotiated` を設定します。  
  
### CertificateOverTransport  
 この認証モードでは、クライアントは、保証サポート トークン、つまりメッセージ署名を行うトークンとして SOAP 層に表示される X.509 証明書を使用して認証を行います。サービスはトランスポート層で X.509 証明書を使用して認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> メソッドによって返される <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> です。代わりに、`authenticationMode` 属性に `CertificateOverTransport` を設定します。  
  
### IssuedToken  
 この認証モードでは、クライアントはサービスに対する認証を行いません。代わりに、クライアントはセキュリティ トークン サービスに対して認証を行い、SAML トークンを受信します。その後、クライアントはサーバーに対してこのトークンを提示し、共有キーの情報を示します。サービスはクライアントに対して認証されませんが、そのサービスだけがキーを復号化できるように、セキュリティ トークン サービスは発行されたトークンの一部として共有キーを暗号化します。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> メソッドによって返される <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> です。代わりに、`authenticationMode` 属性を `IssuedToken` に設定します。  
  
### IssuedTokenForCertificate  
 この認証モードでは、クライアントはサービスに対する認証を行いません。代わりに、クライアントはセキュリティ トークン サービスに対して認証を行い、SAML トークンを受信します。その後、クライアントはサーバーに対してこのトークンを提示し、共有キーの情報を示します。発行済みトークンは、保証サポート トークンまたは所有者トークン \(メッセージ署名を行うトークン\) として SOAP 層に表示されます。サービスはクライアントに対して X.509 証明書を使用して認証します。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> メソッドによって返される <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> です。代わりに、`authenticationMode` 属性に `IssuedTokenForCertificate` を設定します。  
  
### IssuedTokenForSslNegotiated  
 この認証モードでは、クライアントはサービスに対する認証を行いません。代わりに、クライアントはセキュリティ トークン サービスに対して認証を行い、SAML トークンを受信します。その後、クライアントはサーバーに対してこのトークンを提示し、共有キーの情報を示します。発行済みトークンは、保証サポート トークンまたは所有者トークン \(メッセージ署名を行うトークン\) として SOAP 層に表示されます。サービスは X.509 証明書を使用して認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> メソッドによって返される <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> です。代わりに、`authenticationMode` 属性に `IssuedTokenForSslnegotiated` を設定します。  
  
### IssuedTokenOverTransport  
 この認証モードでは、クライアントはサービスに対する認証を行いません。代わりに、クライアントはセキュリティ トークン サービスに対して認証を行い、SAML トークンを受信します。その後、クライアントはサーバーに対してこのトークンを提示し、共有キーの情報を示します。発行済みトークンは、保証サポート トークンまたは所有者トークン \(メッセージ署名を行うトークン\) として SOAP 層に表示されます。サービスはトランスポート層で X.509 証明書を使用して認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> メソッドによって返される `TransportSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `IssuedTokenOverTransport` を設定します。  
  
### Kerberos  
 この認証モードでは、クライアントは Kerberos チケットを使用してサービスに対する認証を行います。また、その同じチケットによってサーバーが認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> メソッドによって返される `SymmetricSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `Kerberos` を設定します。  
  
> [!NOTE]
>  この認証モードを使用するには、サービス アカウントをサービス プリンシパル名 \(SPN: Service Principal Name\) に関連付ける必要があります。この関連付けを行うには、NETWORK SERVICE アカウントまたは LOCAL SYSTEM アカウントでサービスを実行します。または、SetSpn.exe ツールを使用して、サービス アカウントの SPN を作成します。いずれの場合も、クライアントは [\<servicePrincipalName\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) 要素で正しい SPN を使用するか、<xref:System.ServiceModel.EndpointAddress> コンストラクターを使用して正しい SPN を使用する必要があります。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  `Kerberos` 認証モードを使用する場合、<xref:System.Security.Principal.TokenImpersonationLevel> および <xref:System.Security.Principal.TokenImpersonationLevel> の各偽装レベルはサポートされません。  
  
### KerberosOverTransport  
 この認証モードでは、クライアントは Kerberos チケットを使用してサービスに対する認証を行います。Kerberos トークンは、保証サポート トークン、つまりメッセージ署名を行うトークンとして SOAP 層に表示されます。サービスはトランスポート層で X.509 証明書を使用して認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> メソッドによって返される `TransportSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `KerberosOverTransport` を設定します。  
  
> [!NOTE]
>  この認証モードを使用するには、サービス アカウントを SPN に関連付ける必要があります。この関連付けを行うには、NETWORK SERVICE アカウントまたは LOCAL SYSTEM アカウントでサービスを実行します。または、SetSpn.exe ツールを使用して、サービス アカウントの SPN を作成します。いずれの場合も、クライアントは [\<servicePrincipalName\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) 要素で正しい SPN を使用するか、<xref:System.ServiceModel.EndpointAddress> コンストラクターを使用して正しい SPN を使用する必要があります。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### MutualCertificate  
 この認証モードでは、クライアントは、保証サポート トークン、つまりメッセージ署名を行うトークンとして SOAP 層に表示される X.509 証明書を使用して認証を行います。また、サービスは X.509 証明書を使用して認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> メソッドによって返される `SymmetricSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `MutualCertificate` を設定します。  
  
### MutualCertificateDuplex  
 この認証モードでは、クライアントは、保証サポート トークン、つまりメッセージ署名を行うトークンとして SOAP 層に表示される X.509 証明書を使用して認証を行います。また、サービスは X.509 証明書を使用して認証されます。バインディングは、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> メソッドによって返される `AsymmetricSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `MutualCertificateDuplex` を設定します。  
  
### MutalSslNegotiation  
 この認証モードでは、クライアントとサービスは X.509 証明書を使用して認証を行います。セキュリティ バインド要素は、最初のパラメーターに `true` の値が渡される場合に <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> メソッドによって返される `SymmetricSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `MutualSslNegotiated` を設定します。  
  
### SecureConversation  
 セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> メソッドによって返される `SymmetricSecurityBindingElement` です。このメソッドは、パラメーターとして <xref:System.ServiceModel.Channels.SecurityBindingElement> を受け取り、初期化時にこれを使用してセキュリティで保護されたセッションを確立します。代わりに、`authenticationMode` 属性に `SecureConversation` を設定します。  
  
 ブートストラップ バインディングを指定していない場合は、ブートストラップのために `SspiNegotiated` 認証モードが使用されます。  
  
### SspiNegotiation  
 この認証モードでは、ネゴシエーション プロトコルを使用して、クライアントとサーバーの認証を行います。Kerberos を使用できる場合は Kerberos が使用され、それ以外の場合は、NTLM \(NT LanMan\) が使用されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> メソッドによって返される `SymmetricSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `SspiNegotiated` を設定します。  
  
### SspiNegotiatedOverTransport  
 この認証モードでは、ネゴシエーション プロトコルを使用して、クライアントとサーバーの認証を行います。Kerberos プロトコルを使用できる場合は Kerberos プロトコルが使用され、それ以外の場合は NTLM が使用されます。発行されたトークンは、保証サポート トークン、つまりメッセージ署名を行うトークンとして SOAP 層に表示されます。サービスは、トランスポート層で X.509 証明書により追加的に認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> メソッドによって返される `TransportSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `SspiNegotiatedOverTransport` を設定します。  
  
### UserNameForCertificate  
 この認証モードでは、クライアントは、署名付きサポート トークン、つまりメッセージ署名で署名されたトークンとして SOAP 層に表示されるユーザー名トークンを使用してサービスに対する認証を行います。X.509 証明書を使用したクライアントに対するサービス認証。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> メソッドによって返される `SymmetricSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `UserNameForCertificate` を設定します。  
  
 `UserNameForCertificate` 認証モードでは、クライアントとサービスの両方が WS\-Security 1.1 を使用している必要があります。  
  
### UserNameForSslNegotiated  
 この認証モードでは、クライアントは、署名付きサポート トークン、つまりメッセージ署名で署名されたトークンとして SOAP 層に表示されるユーザー名トークンを使用して認証を行います。サービスは X.509 証明書を使用して認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> メソッドによって返される `SymmetricSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `UserNameForSslNegotiated` を設定します。  
  
### UserNameOverTransport  
 この認証モードでは、クライアントは、署名付きサポート トークン、つまりメッセージ署名で署名されたトークンとして SOAP 層に表示されるユーザー名トークンを使用して認証を行います。サービスはトランスポート層で X.509 証明書を使用して認証されます。セキュリティ バインド要素は、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> メソッドによって返される `TransportSecurityBindingElement` です。代わりに、`authenticationMode` 属性に `UserNameOverTransport` を設定します。  
  
## 参照  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>   
 [方法 : 指定した認証モード用の SecurityBindingElement を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)