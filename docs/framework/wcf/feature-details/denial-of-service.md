---
title: "サービス拒否 | Microsoft Docs"
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
  - "サービス拒否 [WCF]"
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# サービス拒否
サービス拒否は、メッセージを処理できなくしたり、メッセージ処理を大幅に遅延させたりするなど、システムに過大な負荷が生じた場合に発生します。  
  
## 過度のメモリ消費  
 一意のローカル名、名前空間、またはプレフィックスを大量に含んだ XML ドキュメントを読み込むと、問題が発生する場合があります。  <xref:System.Xml.XmlReader> から派生したクラスを使用している場合、<xref:System.Xml.XmlReader.LocalName%2A>、<xref:System.Xml.XmlReader.Prefix%2A>、または <xref:System.Xml.XmlReader.NamespaceUri%2A> のいずれかのプロパティが項目ごとに呼び出され、それによって返された文字列が <xref:System.Xml.NameTable> に追加されます。  <xref:System.Xml.NameTable> が保持するコレクションのサイズは決して減ることがありません。その結果、文字列ハンドルの実質的な "メモリ リーク" が発生する場合があります。  
  
 回避事項を次に示します。  
  
-   <xref:System.Xml.NameTable> からの派生クラスを作成し、最大サイズのクォータを指定します   \(<xref:System.Xml.NameTable> の使用を回避したり、サイズが上限に達したときに <xref:System.Xml.NameTable> を切り替えたりすることはできません\)。  
  
-   可能であれば、前述のプロパティを使用せずに、<xref:System.Xml.XmlReader.MoveToAttribute%2A> メソッドと <xref:System.Xml.XmlReader.IsStartElement%2A> メソッドを使用します。これらのメソッドでは、文字列が返されないため、<xref:System.Xml.NameTable> コレクションがあふれてしまう問題を回避できます。  
  
## 悪質なクライアントにより過度のライセンス要求がサービスに送信される  
 悪質なクライアントが過度のライセンス要求を実行してサービスを攻撃する場合、サーバーは過度のメモリを使用することになります。  
  
 回避方法 : <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> クラスの次のプロパティを使用します。  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A> : `SPNego` または `SSL` ネゴシエーションの後にサーバーがキャッシュする、期限付きの `SecurityContextToken` の最大数を制御します。  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A> : `SPNego` または `SSL` ネゴシエーションに続いてサーバーが発行する `SecurityContextTokens` の有効期限を制御します。  サーバーは、この期間の `SecurityContextToken` をキャッシュします。  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: サーバーで確立されているが、そのアプリケーション メッセージが処理されていない、セキュリティで保護されたメッセージ交換の最大数を制御します。  このクォータは、クライアントが、セキュリティで保護されたメッセージ交換をサービスで確立しないようにします。それによって、サービスはクライアントごとの状態を保持できますが、それらの状態を使用することはありません。  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A> : サービスが、セキュリティで保護されたメッセージ交換を、その当事者のクライアントからのアプリケーション メッセージを受信しなくても確立したままにする最長時間を制御します。  このクォータは、クライアントが、セキュリティで保護されたメッセージ交換をサービスで確立しないようにします。それによって、サービスはクライアントごとの状態を保持できますが、それらの状態を使用することはありません。  
  
## WSDualHttpBinding または二重カスタム バインディングにクライアント認証が必要になる  
 既定では、<xref:System.ServiceModel.WSDualHttpBinding> のセキュリティは有効になっています。  ただし、<xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> プロパティを <xref:System.ServiceModel.MessageCredentialType> に設定してクライアント認証を無効にすると、第 3 のサービスで悪質なユーザーからサービス拒否攻撃を受ける可能性があります。  これは、悪質なクライアントが、メッセージ ストリームを第 3 のサービスに送信するようサービスに指示できるためです。  
  
 これを防ぐには、このプロパティを `None` に設定しないようにします。  二重メッセージ パターンを持つカスタム バインディングを作成する場合もこの可能性があることに注意してください。  
  
## 監査イベント ログがいっぱいになる可能性がある  
 悪意のあるユーザーに監査が有効になっていることを知られると、その攻撃者に監査エントリの書き込みにつながる無効なメッセージを送信される可能性があります。  このような方法で監査ログに書き込みが行われると、監査システムに障害が発生します。  
  
 これを防ぐには、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> プロパティを `true` に設定し、イベント ビューアーのプロパティを使用して監査動作を制御します。  イベント ビューアーを使用してイベント ログを表示および管理する方法の[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 「[イベント ビューアー](http://go.microsoft.com/fwlink/?LinkId=186123)」を参照してください。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## IAuthorizationPolicy の無効な実装によりサービスが停止する可能性がある  
 欠陥のある <xref:System.IdentityModel.Policy.IAuthorizationPolicy> インターフェイスの実装で <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> メソッドを呼び出すと、サービスが停止する可能性があります。  
  
 回避方法 : 信頼されたコードのみを使用します。  つまり、ユーザーが記述しテストしたコード、または信頼されたプロバイダーが提供するコードのみを使用します。  十分な検討を行わずに、<xref:System.IdentityModel.Policy.IAuthorizationPolicy> の信頼されない拡張をユーザーのコードに接続することを許可しないでください。  これは、サービスの実装で使用されるすべての拡張に当てはまります。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、アプリケーション コードと、拡張ポイントを使用して接続される外部コードを区別しません。  
  
## Kerberos の最大トークン サイズの変更が必要になる場合がある  
 クライアントが多数のグループ \(実際の数はグループにより異なるが、約 900\) に属している場合、メッセージ ヘッダーのブロックが 64 KB を超えると問題が発生する場合があります。  このような場合は、最大 Kerberos トークンサイズを Microsoft サポート オンラインの「[Internet Explorer Kerberos 認証は、IIS に接続している十分なバッファーのため、機能しません。](http://go.microsoft.com/fwlink/?LinkId=89176)」で説明されているとおりに増加できます。最大 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージ サイズを Kerberos トークンの増加に合わせて増加させることが必要な場合もあります。  
  
## 自動登録によってコンピューターに同一サブジェクト名の証明書が複数発生する  
 *自動登録*は、証明書用のユーザーとコンピューターを自動で登録する [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] の機能です。  この機能が有効になっているドメイン上にコンピューターがある場合、新しいコンピューターがネットワークに参加するたびに、クライアント認証を目的とする X.509 証明書が自動的に作成されローカル コンピューターの個人用証明書のストアに自動で挿入されます。  ただし、自動登録では、キャッシュに作成されたすべての証明書に同じサブジェクト名が使用されます。  
  
 この影響で、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを自動登録のドメインで開始できない場合があります。  コンピューターの完全修飾ドメイン ネーム システム \(DNS\) 名を持つ証明書が複数あるため、既定サービスの X.509 資格情報検索の条件が不明確になり、このような問題が発生します。  この場合、1 つは自動登録で作成された証明書、もう 1 つは自己発行された証明書です。  
  
 これを防ぐには、より厳密な [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)の検索条件を使用して、使用する正確な証明書を参照します。  たとえば、<xref:System.Security.Cryptography.X509Certificates.X509FindType> オプションを使用し、一意の拇印 \(ハッシュ\) により証明書を指定します。  
  
 自動登録機能の[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 「[Windows Server 2003 の証明書自動登録](http://go.microsoft.com/fwlink/?LinkId=95166)」を参照してください。  
  
## 複数の代替サブジェクト名の最後が承認に使用される  
 まれなケースとして X.509 証明書に複数の代替サブジェクト名が含まれる場合、その代替サブジェクト名を使用して承認を行うと、承認は失敗する場合があります。  
  
## ACL を使用して構成ファイルを保護する  
 [!INCLUDE[infocard](../../../../includes/infocard-md.md)] で発行されたトークンについては、必須およびオプションのクレームをコードおよび構成ファイルに指定できます。  これにより、対応する要素が、セキュリティ トークン サービスに送信される `RequestSecurityToken` メッセージに送出されます。  攻撃者は、コードまたは構成を変更して必須またはオプションのクレームを削除でき、対象サービスへのアクセスが許可されていないトークンをセキュリティ トークン サービスに発行させることができます。  
  
 これを防ぐには、コンピューターにアクセスして構成ファイルを変更する必要があります。  アクセス制御リスト \(ACL: Access Control List\) を使用して構成ファイルをセキュリティで保護します。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、コードが構成から読み込まれる前に、そのコードをアプリケーション ディレクトリまたはグローバル アセンブリ キャッシュに格納する必要があります。  ディレクトリの ACL を使用してディレクトリをセキュリティで保護します。  
  
## 1 つのサービスに対して、セキュリティで保護されたセッションが最大数に達する  
 クライアントがサービスにより正常に認証され、セキュリティで保護されたセッションがサービスと共に確立されると、クライアントがセッションをキャンセルするか、セッションの期限が切れるまで、サービスはそのセッションを追跡します。  セッションが確立されるたびに、1 つのサービスで同時にアクティブにできるセッションは上限に近づいていきます。  この上限に達した場合、1 つ以上のアクティブなセッションが期限切れになるかまたはクライアントによりキャンセルされるまで、そのサービスで新しいセッションの作成を試みるクライアントは拒否されます。  クライアントは 1 つのサービスで複数のセッションを保持できますが、その各セッションは上限に反映されます。  
  
> [!NOTE]
>  ステートフルなセッションを使用する場合、前の段落は適用されません。  ステートフルなセッション[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)」を参照してください。  
  
 これを防ぐには、<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの <xref:System.ServiceModel.Channels.SecurityBindingElement> プロパティを設定して、アクティブなセッションの最大数とセッションの最長有効期間の制限を設定します。  
  
## 参照  
 [セキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)   
 [情報の漏えい](../../../../docs/framework/wcf/feature-details/information-disclosure.md)   
 [権限の昇格](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)   
 [Denial of Service](../../../../docs/framework/wcf/feature-details/denial-of-service.md)   
 [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)   
 [改変](../../../../docs/framework/wcf/feature-details/tampering.md)   
 [サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)