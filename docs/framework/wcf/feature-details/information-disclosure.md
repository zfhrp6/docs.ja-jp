---
title: "情報の漏えい"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1bf20f11e7077c981e73aa087c654b9cf0c87bcb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="information-disclosure"></a>情報の漏えい
情報が漏えいすると、攻撃者はシステムに関する重要情報を入手できます。 そのため、どのような情報を公開しているか、また、その情報が悪意のあるユーザーによって使用される可能性があるかどうかに常に気を配る必要があります。 考えられる情報漏えい攻撃とその軽減策を以下に示します。  
  
## <a name="message-security-and-http"></a>メッセージ セキュリティと HTTP  
 HTTP トランスポート層でメッセージ レベルのセキュリティを使用している場合は、メッセージ レベルのセキュリティで HTTP ヘッダーが保護されないことに注意してください。 HTTP ヘッダーを保護する唯一の方法は、HTTP ではなく、HTTPS トランスポートを使用することです。 HTTPS トランスポートを使用すると、HTTP ヘッダーを含むメッセージ全体が SSL (Secure Sockets Layer) プロトコルを使用して暗号化されます。  
  
## <a name="policy-information"></a>ポリシー情報  
 ポリシーをセキュリティで保護することが重要です。特に、機密事項が含まれる発行済みトークンの要件や、トークン発行者の情報がポリシーで公開されるフェデレーション シナリオでは重要です。 このような場合は、フェデレーション サービスのポリシー エンドポイントをセキュリティで保護し、発行済みトークンに含まれるクレームの種類などサービスに関する情報が攻撃者の手に渡らないようにしたり、クライアントが悪意のあるトークン発行者にリダイレクトされたりしないようにすることをお勧めします。 たとえば、攻撃者は、フェデレーション信頼チェーンが man-in-the-middle 攻撃を実行する発行者で終了するように再構成することで、ユーザー名/パスワードのペアを発見することがあります。 また、ポリシーの取得によってバインディングを取得するフェデレーション クライアントの場合は、取得したフェデレーション信頼チェーンに含まれる発行者の信頼性を検証することもお勧めします。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]フェデレーション シナリオを参照して[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)です。  
  
## <a name="memory-dumps-can-reveal-claim-information"></a>メモリ ダンプによるクレーム情報の漏えい  
 アプリケーションにエラーが発生した場合、ワトソン博士などによって作成されたログ ファイルには、クレーム情報が含まれることがあります。 この情報はサポート チームなどの他のエンティティに対してエクスポートしないでください。プライベートなデータを含むクレーム情報もエクスポートされます。 ログ ファイルを未知のエンティティに送信しないようにすることで、クレーム情報が漏えいするリスクを軽減できます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=89160)です。  
  
## <a name="endpoint-addresses"></a>エンドポイント アドレス  
 エンドポイント アドレスには、エンドポイントとの通信に必要な情報が含まれます。 SOAP セキュリティでは、クライアントとサーバーとの間で対称キーをネゴシエートするために交換されるセキュリティ ネゴシエーション メッセージに、完全なアドレスが含まれている必要があります。 セキュリティ ネゴシエーションはブートストラップ プロセスであるため、このプロセスの間、アドレス ヘッダーを暗号化することはできません。 したがって、アドレスには機密データを含めないようにします。そうしないと、情報漏えい攻撃につながります。  
  
## <a name="certificates-transferred-unencrypted"></a>暗号化されていない証明書の転送  
 クライアントの認証に X.509 証明書を使用する場合、証明書は SOAP ヘッダー内で暗号化されずに転送されます。 これは潜在的に個人を特定できる情報 (PII) の漏えいにつながるので注意が必要です。 トランスポート レベルのセキュリティでメッセージが暗号化される `TransportWithMessageCredential` モードでは、これは問題とはなりません。  
  
## <a name="service-references"></a>サービス参照  
 サービス参照は、別のサービスへの参照です。 たとえば、サービスは、操作の過程でクライアントにサービス参照を渡すことがあります。 サービス参照を使用しても、 *id 検証機能を信頼*、アプリケーション データまたはターゲットに資格情報などの情報を公開する前に、対象プリンシパルの id を保証するために内部コンポーネントです。 リモートの信頼できる ID が検証できない、または正しくない場合、送信側は、送信者自身、アプリケーション、またはユーザーが侵害されるおそれのあるデータを開示しないようにする必要があります。  
  
 回避策は次のとおりです。  
  
-   サービス参照は信頼できるものと仮定されています。 サービス参照インスタンスを転送する場合は、改ざんされていないことを必ず確認するよう注意してください。  
  
-   一部のアプリケーションで得られるユーザー エクスペリエンスでは、サービス参照内のデータと、リモート ホストによって信頼性が証明されているデータに基づいて、対話により信頼を確立することができます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、このような機能のための拡張ポイントが用意されていますが、実装はユーザーが行う必要があります。  
  
## <a name="ntlm"></a>NTLM  
 Windows ドメイン環境の既定では、Windows 認証は Kerberos プロトコルを使用して、ユーザーの認証と承認を行います。 何かの理由で Kerberos プロトコルを使用できない場合は、その代替システムとして NTLM (NT LAN Manager) が使用されます。 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> プロパティを `false` に設定することで、この動作を無効にできます。 NTLM を許可する場合は、次の点に注意してください。  
  
-   NTLM はクライアントのユーザー名を公開します。 ユーザー名を非公開にしておく必要がある場合は、バインディングの `AllowNTLM` プロパティを `false` に設定します。  
  
-   NTLM は、サーバー認証を提供しません。 したがって、認証プロトコルとして NTLM が使用されていると、クライアントは自分が適切なサービスと通信しているかどうかを確認できません。  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>クライアント資格情報または無効な ID の指定による強制的な NTLM の使用  
 クライアントの作成時に、ドメイン名なしでクライアント資格情報を指定するか、無効なサーバー ID を指定すると、Kerberos プロトコルではなく NTLM が使用されます (`AlllowNtlm` プロパティが `true` に設定されている場合)。 NTLM ではサーバー認証を行わないため、情報が漏えいするおそれがあります。  
  
 たとえば、次の [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコードに示すように、ドメイン名なしで Windows クライアント資格情報を指定できます。  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 このコードではドメイン名が指定されておらず、そのため NTLM が使用されます。  
  
 ドメインを指定していても、エンドポイント ID 機能を使用して無効なサービス プリンシパル名を指定した場合は、NTLM が使用されます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]エンドポイント id を指定するを参照してください。[サービス Id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [特権の昇格](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [サービス拒否が起こる](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [改ざん](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
