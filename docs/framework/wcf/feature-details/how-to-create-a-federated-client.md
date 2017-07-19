---
title: "方法 : フェデレーション クライアントを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フェデレーション"
  - "WCF, フェデレーション"
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# 方法 : フェデレーション クライアントを作成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] での*フェデレーション サービス*用クライアントの作成は、主に次の 3 つの手順で構成されます。  
  
1.  [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)または同様のカスタム バインディングを構成します。適切なバインディングの作成[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : WSFederationHttpBinding を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)」を参照してください。または、フェデレーション サービスのメタデータ エンドポイントに対して [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を実行し、フェデレーション サービスおよび 1 つ以上のセキュリティ トークン サービスとの通信用の構成ファイルを作成します。  
  
2.  クライアントがセキュリティ トークン サービスと対話する際のさまざまな側面を制御する <xref:System.ServiceModel.Security.IssuedTokenClientCredential> のプロパティを設定します。  
  
3.  セキュリティ トークン サービスなど、特定のエンドポイントとのセキュリティ保護された通信に必要な証明書を許可する <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> のプロパティを設定します。  
  
> [!NOTE]
>  クライアントが、偽装された資格情報、<xref:System.ServiceModel.WSFederationHttpBinding> バインディングやカスタムの発行済みトークン、および非対称キーを使用すると、<xref:System.Security.Cryptography.CryptographicException> がスローされる可能性があります。<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> プロパティと <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> プロパティをそれぞれ <xref:System.IdentityModel.Tokens.SecurityKeyType> に設定すると、<xref:System.ServiceModel.WSFederationHttpBinding> バインディングとカスタムの発行済みトークンで非対称キーが使用されます。クライアントがメッセージを送信しようとするときに、クライアントが偽装している ID のユーザー プロファイルが存在しないと、<xref:System.Security.Cryptography.CryptographicException> がスローされます。この問題を回避するには、クライアント コンピューターにログオンした後、または `LoadUserProfile` を呼び出した後に、メッセージを送信します。  
  
 ここでは、これらの手順について詳しく説明します。適切なバインディングの作成[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : WSFederationHttpBinding を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)」を参照してください。フェデレーション サービスのしくみ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)」を参照してください。  
  
### フェデレーション サービスの構成を生成し、確認するには  
  
1.  コマンド ライン パラメーターとしてサービスのメタデータ URL のアドレスを使用し、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を実行します。  
  
2.  生成された構成ファイルを適切なエディターで開きます。  
  
3.  生成されたすべての [\<issuer\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) 要素と [\<issuerMetadata\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) 要素の属性と内容を調べます。これらは、[\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 要素またはカスタム バインド要素の [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) 要素内にあります。予期されたドメイン名やその他のアドレス情報がアドレスに含まれていることを確認します。この情報をチェックすることは重要です。それは、クライアントがこれらのアドレスに対して認証を行い、ユーザー名とパスワードの組み合わせなどの情報を公開する可能性があるためです。アドレスが予期されたアドレスではない場合、意図しない受信者に情報が公開されるおそれがあります。  
  
4.  コメント アウトされた \<`alternativeIssuedTokenParameters`\> 要素内の追加の [\<issuedTokenParameters\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) 要素をすべて調べます。Svcutil.exe ツールを使用してフェデレーション サービスの構成を生成するときに、フェデレーション サービスまたは任意の中間セキュリティ トークン サービスが、発行者アドレスを指定せずに、複数のエンドポイントを公開するセキュリティ トークン サービスのメタデータ アドレスを指定している場合、生成された構成ファイルは最初のエンドポイントを参照します。追加のエンドポイントは、コメント アウトされた \<`alternativeIssuedTokenParameters`\> 要素として構成ファイルに含まれます。  
  
     これらの \<`issuedTokenParameters`\> のいずれかが、既に構成に存在するものよりも適切かどうかを判断します。たとえば、セキュリティ トークン サービスに対する認証を行う際は、ユーザー名とパスワードの組み合わせよりも Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] トークンを使用する方が、クライアントにとって望ましい場合があります。  
  
    > [!NOTE]
    >  サービスと通信するまでに複数のセキュリティ トークン サービスをたどる必要がある場合は、中間セキュリティ トークン サービスがクライアントを不適切なセキュリティ トークン サービスにダイレクトする可能性があります。そのため、[\<issuedTokenParameters\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) 内のセキュリティ トークン サービスのエンドポイントが、予期されたセキュリティ トークン サービスであり、未確認のセキュリティ トークン サービスでないことを確認します。  
  
### コードで IssuedTokenClientCredential を構成するには  
  
1.  次のコード例に示すように、<xref:System.ServiceModel.ClientBase%601> クラスの <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> プロパティまたは <xref:System.ServiceModel.ChannelFactory> クラスから返された、<xref:System.ServiceModel.Description.ClientCredentials> クラスの <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> プロパティから <xref:System.ServiceModel.Security.IssuedTokenClientCredential> にアクセスします。  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2.  トークン キャッシュが不要な場合は、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> プロパティを `false` に設定します。<xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> プロパティにより、セキュリティ トークン サービスからのこれらのトークンをキャッシュするかどうかが制御されます。このプロパティを `false` に設定すると、クライアントは、以前のトークンがいまだに有効な場合でも、フェデレーション サービスに対してクライアント自体を再認証する必要があるときに、新しいトークンをセキュリティ トークン サービスに要求します。このプロパティを `true` に設定すると、クライアントは、トークンの有効期限が切れていない限り、フェデレーション サービスに対してクライアント自体を再認証する必要があるときに既存のトークンを再利用します。既定値は `true` です。  
  
3.  キャッシュされたトークンの制限時間を設ける必要がある場合は、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> プロパティを <xref:System.TimeSpan> 値に設定します。このプロパティは、トークンがキャッシュされる時間を指定します。指定の時間が経過すると、トークンはクライアントのキャッシュから削除されます。既定では、トークンは無期限でキャッシュされます。制限時間を 10 分に設定する例を次に示します。  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4.  省略可能。<xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> をパーセンテージに設定します。既定値は 60 \(パーセント\) です。このプロパティは、トークンの有効期間をパーセンテージで指定します。たとえば、発行されたトークンが 10 時間有効で、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> が 80 に設定されている場合、このトークンは 8 時間後に更新されます。この値を 80% に設定する例を次に示します。  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     トークンの有効期間と `IssuedTokenRenewalThresholdPercentage` 値によって決まる更新間隔は、キャッシュ時間が更新しきい時間よりも短い場合には、`MaxIssuedTokenCachingTime` 値によってオーバーライドされます。たとえば、`IssuedTokenRenewalThresholdPercentage` とトークンの有効期間を掛けた積が 8 時間であり、`MaxIssuedTokenCachingTime` 値が 10 分の場合、クライアントは、トークンの更新のために 10 分ごとにセキュリティ トークン サービスに連絡します。  
  
5.  <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> 以外のキー エントロピ モードが、メッセージ セキュリティやメッセージ資格情報付きトランスポート セキュリティを使用しないバインディング \(たとえば、バインディングに <xref:System.ServiceModel.Channels.SecurityBindingElement> が存在しない場合\) で必要な場合は、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> プロパティに適切な値を設定します。*エントロピ*モードにより、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> プロパティを使用して対称キーを制御できるかどうかが決まります。この既定値は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> であり、この場合、クライアントとトークン発行者の両方から、実際のキーを生成する際に組み合わせるデータが提供されます。これ以外の値は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> と <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> であり、それぞれクライアントまたはサーバーによってキー全体が指定されます。サーバーのデータのみを使用してキーを指定するよう、このプロパティを設定する例を次に示します。  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  セキュリティ トークン サービスまたはサービス バインディングに <xref:System.ServiceModel.Channels.SecurityBindingElement> が存在する場合、<xref:System.ServiceModel.Security.IssuedTokenClientCredential> で設定された <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> は、`SecurityBindingElement` の <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> プロパティによってオーバーライドされます。  
  
6.  <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> プロパティによって返されるコレクションに発行者固有のエンドポイント動作を追加して、これらの動作を構成します。  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### 構成で IssuedTokenClientCredential を構成するには  
  
1.  エンドポイントの動作で、[\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) 要素の子として [\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) 要素を作成します。  
  
2.  トークン キャッシュが不要な場合は、\<`issuedToken`\> 要素の `cacheIssuedTokens` 属性を `false` に設定します。  
  
3.  キャッシュされたトークンの制限時間を設ける必要がある場合は、\<`issuedToken`\> 要素の `maxIssuedTokenCachingTime` 属性を適切な値に設定します。次に例を示します。  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4.  既定値以外の値にする場合は、\<`issuedToken`\> 要素の `issuedTokenRenewalThresholdPercentage` 属性を適切な値に設定します。次に例を示します。  
  
    ```  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5.  メッセージ セキュリティやメッセージ資格情報付きトランスポート セキュリティを使用しないバインディングで `CombinedEntropy` 以外のキー エントロピ モードが必要な場合 \(たとえば、バインディングに `SecurityBindingElement` が存在しない場合\) は、必要に応じて次のように `<issuedToken>` 要素の `defaultKeyEntropyMode` 属性を `ServerEntropy` または `ClientEntropy` に設定します。  
  
    ```  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6.  省略可能。\<`issuedToken`\> 要素の子として \<`issuerChannelBehaviors`\> 要素を作成して、発行者固有のカスタム エンドポイント動作を構成します。動作ごとに、\<`issuerChannelBehaviors`\> 要素の子として \<`add`\> 要素を作成します。\<`add`\> 要素の `issuerAddress` 属性を設定して、動作の発行者アドレスを指定します。\<`add`\> 要素の `behaviorConfiguration` 属性を設定して、動作自体を指定します。  
  
    ```  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### コードで X509CertificateRecipientClientCredential を構成するには  
  
1.  <xref:System.ServiceModel.ClientBase%601> クラスまたは <xref:System.ServiceModel.ChannelFactory> プロパティの <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> プロパティが持つ <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> プロパティを介して、次のように <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> にアクセスします。  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2.  特定のエンドポイントの証明書として <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> インスタンスを使用できる場合は、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> プロパティによって返されるコレクションの <xref:System.Collections.Generic.ICollection%601.Add%2A> メソッドを使用します。  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3.  <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> インスタンスが使用できない場合は、次の例に示すように、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> メソッドを使用します。  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### 構成で X509CertificateRecipientClientCredential を構成するには  
  
1.  その要素自体がエンドポイント動作の [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 要素の子要素である [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 要素の子として、[\<scopedCertificates\>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) 要素を作成します。  
  
2.  `<scopedCertificates>` 要素の子要素として `<add>` 要素を作成します。適切な証明書を参照するように `storeLocation`、`storeName`、`x509FindType`、`findValue` の各属性の値を指定します。次の例に示すように、`targetUri` 属性を、証明書が使用されるエンドポイントのアドレスを指定する値に設定します。  
  
    ```  
    <scopedCertificates>  
     <add targetUri="http://fabrikam.com/sts"   
          storeLocation="CurrentUser"  
          storeName="TrustedPeople"  
          x509FindType="FindBySubjectName"  
          findValue="FabrikamSTS" />  
    </scopedCertificates>  
    ```  
  
## 使用例  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> クラスのインスタンスをコードで構成する例を、次のコード サンプルに示します。  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## .NET Framework セキュリティ  
 情報の漏えいを防ぐために、Svcutil.exe ツールを使用してフェデレーション エンドポイントからのメタデータを処理するクライアントでは、生成されたセキュリティ トークン サービス アドレスが予期されたものであることを確認する必要があります。これが特に重要なのは、セキュリティ トークン サービスが複数のエンドポイントを公開する場合です。この場合、Svcutil.exe ツールは、複数のエンドポイントうちの最初のエンドポイントを使用する構成ファイルを生成しますが、このエンドポイントは、クライアントが使用する必要のあるエンドポイントと異なる場合があるためです。  
  
## LocalIssuer が必要な場合  
 チェーン内の 2 番目から最後までのセキュリティ トークン サービスによって発行者アドレスまたは発行者メタデータ アドレスが指定されている場合、Svcutil.exe の既定の出力では、ローカル発行者が使用されません。クライアントで常にローカル発行者を使用する場合は、この点に注意が必要です。  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> クラスの <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>、および <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> プロパティの設定[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : ローカル発行者を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)」を参照してください。  
  
## 範囲指定された証明書  
 証明書ネゴシエーションを使用しないという一般的な理由により、任意のセキュリティ トークン サービスとの通信用のサービス証明書を指定する必要がある場合は、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> プロパティを使用して指定できます。<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> メソッドは、パラメーターとして <xref:System.Uri> と <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> を受け取ります。指定した証明書は、指定した URI のエンドポイントと通信するときに使用されます。または、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> メソッドを使用して、<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> プロパティによって返されるコレクションに証明書を追加することもできます。  
  
> [!NOTE]
>  特定の URI に範囲指定された証明書というクライアントの概念は、該当する URI でエンドポイントを公開するサービスへの送信呼び出しを行うアプリケーションにだけ適用されます。これは、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential> クラスの <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> によって返されたコレクション内のサーバーで構成された証明書など、発行済みトークンの署名に使用される証明書には適用されません。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : フェデレーション サービスで資格情報を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## 参照  
 [フェデレーション サンプル](../../../../docs/framework/wcf/samples/federation-sample.md)   
 [方法 : WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)   
 [方法 : WSFederationHttpBinding を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)   
 [方法 : フェデレーション サービスで資格情報を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [方法 : ローカル発行者を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [メタデータを使用する場合のセキュリティ上の考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)   
 [方法 : セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)