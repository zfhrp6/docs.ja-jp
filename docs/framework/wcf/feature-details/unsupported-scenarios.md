---
title: "サポートされていないシナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
caps.latest.revision: "43"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a518f1bc6019aea0667f6be018e06bbcf36e6e9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unsupported-scenarios"></a>サポートされていないシナリオ
さまざまな理由から、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でサポートされていないセキュリティ シナリオがあります。 たとえば、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition は SSPI または Kerberos 認証プロトコルを実装しないため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、このプラットフォーム上での Windows 認証を使用するサービスの実行をサポートしません。 Windows XP Home Edition で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を実行している場合、ユーザー名/パスワードや HTTP/HTTPS 統合認証などの他の認証機構がサポートされます。  
  
## <a name="impersonation-scenarios"></a>偽装シナリオ  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>クライアントが非同期呼び出しを行うと、偽装 ID はフローしない場合がある  
 WCF クライアントが、偽装で Windows 認証を使用して WCF サービスへの非同期呼び出しを行うと、偽装 ID ではなくクライアント プロセスの ID で認証が行われる場合があります。  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP と有効化されたセキュリティ コンテキスト トークン クッキー  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では偽装はサポートされず、以下の条件に該当する場合、<xref:System.InvalidOperationException> が発生します。  
  
-   オペレーティング システムが [!INCLUDE[wxp](../../../../includes/wxp-md.md)] である。  
  
-   認証モードで Windows ID が生成された。  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> の <xref:System.ServiceModel.OperationBehaviorAttribute> プロパティが <xref:System.ServiceModel.ImpersonationOption.Required> に設定されます。  
  
-   状態ベースのセキュリティ コンテキスト トークン (SCT: Security Context Token) が作成された (既定では、作成は無効になっています)。  
  
 状態ベースの SCT はカスタム バインドの使用によってのみ作成できます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: セキュリティ コンテキストを作成、セキュリティで保護されたセッションのトークン](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md))。コードでトークンを有効にするには、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> メソッドまたは <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> メソッドを使用して、セキュリティ バインディング要素 (<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> または <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType>) を作成し、`requireCancellation` パラメーターを `false` に設定します。 このパラメーターは、SCT のキャッシュを参照します。 値を `false` に設定することによって、状態ベースの SCT 機能が有効になります。  
  
 または、構成では、トークンが有効にしても、<`customBinding`>、追加し、<`security`> 要素、および設定、`authenticationMode`属性を SecureConversation と`requireSecurityContextCancellation`属性を`true`です。  
  
> [!NOTE]
>  上記の要件は限定的です。 たとえば、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> は Windows ID を生成するバインド要素を作成しますが、SCT を確立しません。 したがって、`Required` で [!INCLUDE[wxp](../../../../includes/wxp-md.md)] オプションと共に使用できます。  
  
### <a name="possible-aspnet-conflict"></a>考えられる ASP.NET との競合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] と [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] はいずれも、偽装を有効にすることも無効にすることもできます。 このため、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションをホストしている場合に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] と [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の構成設定の間で競合が発生する可能性があります。 競合が発生した場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の設定が優先されます。ただし、<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> プロパティを <xref:System.ServiceModel.ImpersonationOption.NotAllowed> に設定している場合は、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の偽装設定が優先されます。  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>偽装を有効にすると、アセンブリの読み込みに失敗する場合がある  
 偽装されたコンテキストにアセンブリを読み込むためのアクセス権がない場合、共通言語ランタイム (CLR: Common Language Runtime) が AppDomain のアセンブリを初めて読み込もうとしたときに、その <xref:System.AppDomain> はエラーをキャッシュします。 この場合、偽装を元に戻した後、元に戻されたコンテキストにアセンブリを読み込むためのアクセス権があったとしても、それ以降のアセンブリの読み込みは失敗します。 これは、ユーザー コンテキストの変更後に、CLR が読み込みを再試行しないためです。 このエラーから回復するには、アプリケーション ドメインを再起動する必要があります。  
  
> [!NOTE]
>  <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> クラスの <xref:System.ServiceModel.Security.WindowsClientCredential> プロパティの既定値は <xref:System.Security.Principal.TokenImpersonationLevel.Identification> です。 ほとんどの場合、ID レベルの偽装コンテキストには、追加のアセンブリを読み込むための権限がありません。 これは既定値であるため、非常に一般的な状態として認識しておく必要があります。 ID レベルの偽装は、偽装プロセスが `SeImpersonate` 権限を持たない場合にも発生します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)です。  
  
### <a name="delegation-requires-credential-negotiation"></a>委任には資格情報ネゴシエーションが必要  
 委任で Kerberos 認証プロトコルを使用するには、資格情報ネゴシエーションを使用する Kerberos プロトコル ("マルチレッグ" Kerberos または "マルチステップ" Kerberos とも呼ばれます) を実装する必要があります。 資格情報ネゴシエーションを使用しない Kerberos 認証 (ワンショット Kerberos またはシングルレッグ Kerberos とも呼ばれる) を実装した場合は、例外がスローされます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]資格情報ネゴシエーションを実装する方法[Windows 認証エラーのデバッグ](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)です。  
  
## <a name="cryptography"></a>暗号  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>対称キーを使用する場合にのみサポートされる SHA-256  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、さまざまな暗号化アルゴリズムと署名ダイジェスト作成アルゴリズムをサポートしています。これらのアルゴリズムは、システム指定のバインディングでアルゴリズム スイートを使用して指定できます。 セキュリティを強化するため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、署名ダイジェスト ハッシュを作成するためにセキュア ハッシュ アルゴリズム (SHA: Secure Hash Algorithm) 2 (具体的には SHA-256) をサポートしています。 このリリースは、Kerberos キーなどの対称キーを使用する場合、およびメッセージに署名するために X.509 証明書を使用しない場合に限り SHA-256 をサポートします。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が現時点で RSA-SHA256 をサポートしていないため、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] では (X.509 証明書で使用する) RSA 署名に SHA-256 ハッシュを使用できません。  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>サポートされていない FIPS 準拠の SHA-256 ハッシュ  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、FIPS 準拠の SHA-256 ハッシュをサポートしていません。したがって、FIPS 準拠のアルゴリズムを使用する必要のあるシステムでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、SHA-256 を使用するアルゴリズム スイートをサポートしません。  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>レジストリを編集すると、FIPS 準拠のアルゴリズムが失敗する場合がある  
 連邦情報処理規格 (FIPS: Federal Information Processing Standards) 準拠のアルゴリズムを有効または無効にするには、Microsoft 管理コンソール (MMC: Microsoft Management Console) のローカル セキュリティ設定スナップインを使用します。 レジストリでこの設定にアクセスすることもできます。 ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、レジストリを使用した設定のリセットをサポートしていません。 値を 1 または 0 以外に設定すると、CLR とオペレーティング システム間で不整合が発生する可能性があります。  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS 準拠の AES 暗号化の制限  
 FIPS 準拠の AES 暗号化は、ID レベルの偽装での双方向コールバックでは機能しません。  
  
### <a name="cngksp-certificates"></a>CNG/KSP 証明書  
 *Cryptography API: Next Generation (CNG)*は、CryptoAPI 用の長期的な置換です。 この API は、アンマネージ コードで使用可能な[!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[lserver](../../../../includes/lserver-md.md)]以降の Windows バージョン。  
  
 .NET framework 4.6.1 と以前のバージョンは、従来の CryptoAPI CNG/KSP 証明書の処理に使用するためこれらの証明書をサポートしています。 .NET Framework 4.6.1 と以前のバージョンで証明書の使用には、例外が発生します。  
  
 証明書に KSP が使用されているかどうかを知る方法は 2 つあります。  
  
-   `p/invoke` を `CertGetCertificateContextProperty` に対して実行し、返された `dwProvType` で `CertGetCertificateContextProperty` を調べる。  
  
-   使用して、`certutil`証明書を照会するためのコマンドラインからコマンド。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][証明書のトラブルシューティングに関する Certutil のタスク](http://go.microsoft.com/fwlink/?LinkId=120056)です。  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>ASP.NET の偽装と ASP.NET 互換を使用する必要がある場合にメッセージ セキュリティが失敗する  
 次の設定の組み合わせはクライアント認証の妨げとなる可能性があるため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] はこの組み合わせをサポートしていません。  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の偽装を有効にしている。 これは、Web.config ファイルに設定して、`impersonate`の属性、<`identity`> 要素を`true`です。  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]互換性モードが有効になって、`aspNetCompatibilityEnabled`の属性、 [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)に`true`です。  
  
-   メッセージ モード セキュリティを使用している。  
  
 これを回避するには、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換モードを無効にします。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換モードが必要である場合は、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の偽装機能を無効にし、代わりに [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で提供される偽装機能を使用します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)です。  
  
## <a name="ipv6-literal-address-failure"></a>IPv6 リテラル アドレス エラー  
 クライアントとサービスが同じコンピューター上に存在し、サービスに対して IPv6 リテラル アドレスが使用されている場合は、セキュリティ要求が失敗します。  
  
 IPv6 リテラル アドレスは、サービスとクライアントがそれぞれ異なるコンピューター上に存在する場合に機能します。  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>フェデレーション信頼での WSDL 取得エラー  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、フェデレーション信頼チェーンの各ノードに対してドキュメントが正確に 1 つだけ要求されます。 エンドポイントを指定するときにループにならないように注意する必要があります。 ループになる場合の例の 1 つは、フェデレーション信頼チェーンの WSDL ダウンロードの使用で、同じ WSDL ドキュメントの中に複数のリンクがある場合です。 この問題がよく発生するシナリオは、セキュリティ トークン サーバーとセキュリティ トークン サービスが同じ ServiceHost の中にあるフェデレーション サービスです。  
  
 そのような状況の例は次の 3 つのエンドポイント アドレスを使うサービスです。  
  
-   http://localhost/CalculatorService/service (サービス)  
  
-   http://localhost/CalculatorService/issue_ticket (セキュリティ トークン サービス)  
  
-   http://localhost/CalculatorService/mex (メタデータ エンドポイント)  
  
 これによって例外がスローされます。  
  
 このシナリオでエラーを避けるには、`issue_ticket` エンドポイントを別のところに置きます。  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL インポート属性が失われる可能性  
 WSDL インポートの際に、WCF は `<wst:Claims>` テンプレート内の `RST` 要素にあるインポート属性を追跡できなくなることがあります。 これは、クレームの種類のコレクションを直接使用する代わりに `<Claims>` を直接 `WSFederationHttpBinding.Security.Message.TokenRequestParameters` または `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` 内で指定した場合に、WSDL インポートの際に発生します。  インポートが属性を失うので、WSDL を介して正しいバインディングのラウンド トリップが行われません。したがって、クライアント側で不適切になります。  
  
 解決策は、インポートを行った後、クライアント側で直接バインディングを変更することです。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [情報漏えいが起こる](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [特権の昇格](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [サービス拒否が起こる](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [改ざん](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
