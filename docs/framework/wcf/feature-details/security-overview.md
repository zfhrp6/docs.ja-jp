---
title: "セキュリティの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WCF, セキュリティ"
  - "Windows Communication Foundation, セキュリティ"
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
caps.latest.revision: 37
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 37
---
# セキュリティの概要
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、SOAP メッセージに基づく分散プログラミングのプラットフォームです。データを保護するには、クライアントとサービス間のメッセージをセキュリティで保護することが不可欠です。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、既存のセキュリティ インフラストラクチャと、認識されている SOAP メッセージのセキュリティ標準の両方に基づき、セキュリティで保護されたメッセージを交換する汎用的で相互運用可能なプラットフォームを提供します。  
  
> [!NOTE]
>  WCF セキュリティの包括的なガイドについては、「[WCF セキュリティ ガイダンス](http://go.microsoft.com/fwlink/?LinkID=158912)」を参照してください。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、HTTPS、Windows 統合セキュリティ、ユーザー認証のためのユーザー名とパスワードなど、既存の技術を使用してセキュリティで保護された分散アプリケーションを構築した経験のあるユーザーには、なじみのある概念を使用します。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、既存のセキュリティ インフラストラクチャを統合するだけではありません。セキュリティで保護された SOAP メッセージを使用して Windows のみのドメインを超えて分散セキュリティを拡張します。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] については、既存のプロトコルに加えて SOAP をプロトコルとして使用する大きな利点を兼ね備えた、既存のセキュリティ機構の実装と考えます。  たとえば、ユーザー名とパスワードや X.509 証明書など、クライアントまたはサービスを識別する資格情報には、相互運用可能な XML ベースの SOAP プロファイルがあります。  このプロファイルを使用して、XML デジタル署名や XML 暗号化などの公開仕様を利用するセキュリティで保護されたメッセージ交換を行います。  仕様の一覧については、「[システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)」を参照してください。  
  
 また他にも、Windows プラットフォームのコンポーネント オブジェクト モデル \(COM\) があり、セキュリティで保護された分散アプリケーションを実現します。  COM は、包括的なセキュリティ機構を有します。このセキュリティ機構により、セキュリティ コンテキストはコンポーネント間をフローできます。また、整合性、機密性、および認証を実現できます。  ただし COM では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が行うようなクロス プラットフォームでのセキュリティで保護されたメッセージ処理を実現できません。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して、Windows ドメインからインターネットにまで及ぶサービスとクライアントを構築できます。  情報セキュリティに対する確信を持てるビジネス重視の動的サービスを構築するには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の相互運用可能なメッセージが必須です。  
  
## Windows Communication Foundation セキュリティの利点  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、SOAP メッセージに基づく分散プログラミングのプラットフォームです。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用すると、サービスとサービス クライアントの両方の機能のアプリケーションを構築でき、他の無数のサービスやクライアントからのメッセージを作成および処理できます。  このような分散アプリケーションでは、メッセージをノード間でフローさせ、ファイアウォールを経由してインターネットに送信し、多くの SOAP 中継局を経由させることができます。  しかしこれは、さまざまなメッセージ セキュリティの脅威を招きます。  エンティティ間でメッセージ交換を行うときに [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティで軽減できる一般的な脅威の例をいくつか示します。  
  
-   機密情報を取得するネットワーク トラフィックの監視。  たとえば、オンライン バンキング シナリオを考えます。クライアントは口座間の資金の移動を要求します。  悪意のあるユーザーはメッセージを途中受信し、後で口座番号とパスワードを使用して、侵害した口座から資金を移動します。  
  
-   クライアントに気付かれることなくサービスとして動作する承認されていないエンティティ。  このシナリオでは、悪意のある \(承認されていない\) ユーザーがオンライン サービスとして動作し、クライアントからメッセージを途中受信して機密情報を取得します。  次にこの承認されていないユーザーは、盗んだデータを使用して侵害した口座から資金を転送します。  この攻撃は、*フィッシング攻撃*としても知られています。  
  
-   呼び出し元が意図したものと異なる結果を取得するようなメッセージの改ざん。  たとえば、預金先の口座番号を変更して、資金を承認されていない口座に移動できます。  
  
-   迷惑なハッカーは、同じ注文をリプレイします。  たとえば、オンライン書店は数百の注文を受け、注文していない顧客に書籍を送付します。  
  
-   クライアントを認証する能力の欠如。  この場合、サービスは、適切なユーザーがトランザクションを実行していることを保証できません。  
  
 転送セキュリティが提供する保証を簡単に説明すると次のようになります。  
  
-   サービス エンドポイント \(応答者\) の認証  
  
-   クライアント プリンシパル \(イニシエーター\) の認証  
  
-   メッセージの整合性  
  
-   メッセージの機密性  
  
-   リプレイの検出  
  
### 既存のセキュリティ インフラストラクチャとの統合  
 ほとんどの場合、Web サービス展開には、SSL \(Secure Sockets Layer\) や Kerberos プロトコルなどの既存のセキュリティ ソリューションが実装されています。  Active Directory を使用する Windows ドメインなど、既に展開されているセキュリティ インフラストラクチャを利用する場合もあります。  新しい技術を評価し採用している間に、これらの既存の技術と統合する必要が生じることはよくあります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティは、既存のトランスポート セキュリティ モデルを統合します。また、既存のインフラストラクチャを活用して SOAP メッセージ セキュリティに基づく新しいトランスポート セキュリティ モデルを実現することもできます。  
  
### 既存の認証モデルとの統合  
 すべての通信セキュリティ モデルにとって、通信のエンティティを識別し認証する機能は重要です。  この通信のエンティティは、"デジタル ID" または資格情報を使用し、通信先のピアで自身を認証します。  分散型の通信プラットフォームの発展により、さまざまな資格情報認証モデルや関連セキュリティ モデルが実装されてきました。  たとえば、インターネットでは、ユーザー名とパスワードを使用してユーザーを識別することが一般的に行われています。  イントラネットでは、ユーザーとサービスの認証をサポートする Kerberos ドメイン コントローラーの使用が一般的になりつつあります。  たとえば、2 つのビジネス パートナー間での特定のシナリオでは、証明書を使用してお互いにパートナーを認証する場合もあります。  
  
 同じサービスを企業内のユーザーや外部のパートナーまたはインターネット ユーザーに公開する Web サービスの世界では、インフラストラクチャがこのような既存のセキュリティ認証モデルとの統合に備えることが重要です。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティは、次のようなさまざまな資格情報の種類 \(認証モデル\) をサポートします。  
  
-   匿名の呼び出し元  
  
-   ユーザー名クライアント資格情報  
  
-   証明書クライアント資格情報  
  
-   Windows \(Kerberos プロトコルと NT LanMan \[NTLM\] の両方\)  
  
### 標準と相互運用  
 既存の大規模展開の世界では、均一性はほとんどありません。  分散型のコンピューティングまたは通信のプラットフォームでは、さまざまなベンダーから提供される技術を相互運用する必要があります。  同様に、セキュリティも相互運用可能である必要があります。  
  
 相互運用可能なセキュリティ システムを実現するため、Web サービス業界で活動する企業はさまざまな標準を作成してきました。  特にセキュリティに関して、注目すべき標準がいくつか提案されています。それは、WS\-Security の SOAP メッセージ セキュリティ \(標準化団体の OASIS で認められ正式には WS\-Security として知られる\)、WS\-Trust、WS\-SecureConversation、および WS\-SecurityPolicy です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、さまざまな相互運用可能なシナリオをサポートします。  <xref:System.ServiceModel.BasicHttpBinding> クラスは、基本セキュリティ プロファイル \(BSP\) を対象とし、<xref:System.ServiceModel.WSHttpBinding> クラスは、WS\-Security 1.1 や WS\-SecureConversation などの最新のセキュリティ標準を対象とします。  これらの標準に準拠することで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティは、Microsoft Windows 以外のオペレーティング システムやプラットフォームでホストされる Web サービスと相互運用および統合できます。  
  
## WCF セキュリティの機能領域  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティは、転送セキュリティ、アクセス制御、および監査の 3 つの主要な機能領域に分けられます。  この後の各セクションでは、これらの領域について簡単に説明します。また、詳細情報へのリンクを示します。  
  
### 転送セキュリティ  
 転送セキュリティには、整合性、機密性、および認証の 3 つの主要なセキュリティ機能があります。  *整合性*とは、メッセージが改ざんされているかどうかを検出する機能です。  *機密性*とは、目的の受信者以外のユーザーにはメッセージを読み取り不可にする機能のことです。これを実現するために暗号化が使用されます。  *認証*とは、提示された ID を検証する機能です。  これらの 3 つの機能を一緒に使用して、メッセージをある地点から別の地点に安全に到着させることができます。  
  
#### トランスポート セキュリティ モードとメッセージ セキュリティ モード  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で転送セキュリティを実装するには、*トランスポート* セキュリティ モードと*メッセージ* セキュリティ モードの 2 つの主要な機構を使用します。  
  
-   *トランスポート セキュリティ モード*では、HTTPS などのトランスポート レベルのプロトコルを使用して転送セキュリティを実現します。  トランスポート モードの利点は、広範囲に採用されていること、多くのプラットフォームで利用可能なこと、コンピューター処理上の複雑性が低いことです。  ただし、Point\-to\-Point からのメッセージだけのセキュリティを保護するという欠点もあります。  
  
-   一方、*メッセージ セキュリティ モード*は、WS\-Security \(および他の仕様\) を使用して転送セキュリティを実現します。  メッセージ セキュリティは、SOAP メッセージに直接適用され、また SOAP エンベロープ内にアプリケーション データと共に格納されるため、トランスポート プロトコルに依存しない、拡張性が高い、エンド ツー エンド \(Point\-to\-Point と対照\) のセキュリティが保証される、という利点があります。ただし、SOAP メッセージの XML の性質を処理する必要があるため、トランスポート セキュリティ モードよりも処理が数倍遅くなる欠点があります。  
  
 これらの相違点[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)」を参照してください。  
  
 3 番目のセキュリティ モードは、上記の 2 つのモードを使用し、その両方の利点を引き継ぎます。  このモードは、`TransportWithMessageCredential` と呼ばれます。  このモードでは、クライアントの認証にメッセージ セキュリティを使用し、サーバーの認証にトランスポート セキュリティを使用して、メッセージの機密性と整合性を実現します。  これにより、`TransportWithMessageCredential` セキュリティ モードでは、トランスポート セキュリティ モードと同じ速度で処理が実行され、メッセージ セキュリティ モードと同じ方法でクライアント認証の拡張性が提供されます。  ただし、メッセージ セキュリティ モードと異なり、完全なエンド ツー エンド セキュリティは提供されません。  
  
### アクセス制御  
 *アクセス制御*は、承認とも呼ばれます。  *承認*を使って、さまざまなユーザーにさまざまなデータ参照権限を持たせることができます。  たとえば、企業の人事ファイルには従業員の機密データが含まれているため、管理者だけが従業員データの参照を許可されます。  また、管理者は直接報告書のデータのみを参照できます。  このような場合、アクセス制御は、ロール \("manager"\) と管理者の特定 ID の両方に基づいて行われます \(ある管理者が別の管理者の部下のレコードを参照できないようにします\)。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のアクセス制御機能は、共通言語ランタイム \(CLR\) の <xref:System.Security.Permissions.PrincipalPermissionAttribute> との統合、および *ID モデル*として知られる一連の API により提供されます。  アクセス制御とクレームに基づく承認の詳細については、「[セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)」を参照してください。  
  
### 監査  
 *監査*とは、セキュリティ イベントを Windows イベント ログに記録することです。  認証の失敗 \(または成功\) などのセキュリティ関連のイベントをログに記録できます。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  プログラミングの詳細については、「[方法 : セキュリティ イベントを監査する](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)」を参照してください。  
  
## 参照  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 [サービスのセキュリティ保護](../../../../docs/framework/wcf/securing-services.md)   
 [一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)   
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [認証](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)   
 [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)   
 [フェデレーションと発行済みトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)   
 [セキュリティ ガイドラインとベスト プラクティス](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)   
 [構成ファイルを使用してサービスを構成する方法](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)   
 [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)   
 [エンドポイントの作成の概要](../../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)   
 [Windows Server AppFabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)