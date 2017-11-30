---
title: "分散アプリケーションのセキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
caps.latest.revision: "32"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 842ce0efefcc026ad33d9be3b2b681fcfc9c0b59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="distributed-application-security"></a>分散アプリケーションのセキュリティ
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] セキュリティは、転送セキュリティ、アクセス制御、および監査の 3 つの主要な機能領域に分けられます。 転送セキュリティは、整合性、機密性、および認証を実現します。 転送セキュリティは、トランスポート セキュリティ、メッセージ セキュリティ、または `TransportWithMessageCredential` のいずれかによって提供されます。  
  
 概要については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]メッセージ セキュリティを参照してください[セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)です。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]その他の 2 つの[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]セキュリティを参照してください[承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)と[監査](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)です。  
  
## <a name="transfer-security-scenarios"></a>転送セキュリティのシナリオ  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 転送セキュリティを使用する一般的なシナリオには、次のようなものがあります。  
  
-   Windows を使用した、セキュリティで保護された転送。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントおよびサービスが Windows ドメイン (または Windows フォレスト) で展開されます。 メッセージには個人データが含まれるため、要件には、クライアントとサービスの相互認証、メッセージの整合性、および機密性が含まれます。 また、特定のトランザクションが発生したという証明も必要であり、たとえば、メッセージの受信側では署名情報を記録する必要があります。  
  
-   `UserName` と HTTPS を使用した、セキュリティで保護された転送。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントおよびサービスを、インターネット経由で動作するように開発する必要があります。 クライアント資格情報を使用して、ユーザー名とパスワードの組み合わせをデータベースに照らして認証します。 サービスは、信頼された SSL (Secure Sockets Layer) 証明書を使用して HTTPS アドレスに展開されます。 メッセージはインターネット経由で転送されるため、クライアントとサービスは相互認証する必要があり、メッセージの機密性と整合性を転送時に維持する必要があります。  
  
-   証明書を使用した、セキュリティで保護された転送。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントおよびサービスを、パブリック インターネット経由で動作するように開発する必要があります。 クライアントとサービスには共に証明書があり、それを使用してメッセージをセキュリティ保護できます。 クライアントとサービスは、インターネットを使用して相互に通信し、メッセージの整合性、機密性、および相互認証を必要とする高価値のトランザクションを実行します。  
  
## <a name="integrity-confidentiality-and-authentication"></a>整合性、機密性、および認証  
 整合性、機密性、および認証の 3 つの機能は、合わせて転送セキュリティと呼ばれます。 転送セキュリティは、分散アプリケーションに対する脅威の軽減に役立つ機能を提供します。 転送セキュリティを構成するこれら 3 つの機能について、次の表で簡単に説明します。  
  
|関数|説明|  
|--------------|-----------------|  
|整合性|*整合性*データが完全で正確な 1 つのポイントから、別のスキャンが、多くのアクターによって読み取られた後に特に保証します。 整合性は、データの改ざんを防止するために保持する必要があり、一般にメッセージのデジタル署名によって実現されます。|  
|機密性|*機密性*は、メッセージが目的の閲覧者以外によって読み取られていないことを保証します。 たとえば、クレジット カード番号などは、インターネット経由で送信されるときに機密性を保持する必要があります。 機密性は、多くの場合、公開キー/秘密キー スキームを使用するデータ暗号化によって実現されます。|  
|認証|*認証*はクレームされた id の検証。 たとえば、銀行口座の使用時には、口座の実際の所有者だけが預金の引き出しを許可されるようにすることが必須です。 認証は、さまざまな手段によって実現できます。 一般的な方法の 1 つとして、ユーザー/パスワード システムがあります。 また、サードパーティから提供される X.509 証明書を使用する方法もあります。|  
  
## <a name="security-modes"></a>セキュリティ モード  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意されている転送セキュリティの各モードを次の表に示します。  
  
|モード|説明|  
|----------|-----------------|  
|なし|トランスポート層とメッセージ層でセキュリティが一切提供されません。 以外の既定ではこのモードを使用して定義済みバインディングのいずれも、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)要素または、コード、使用するとき、<xref:System.ServiceModel.BasicHttpBinding>クラスです。|  
|Transport|HTTPS など、セキュリティで保護されたトランスポートを使用して、整合性、機密性、および相互認証を実現します。|  
|メッセージ|SOAP メッセージ セキュリティを使用して、整合性、機密性、および相互認証を実現します。 SOAP メッセージは、WS-Security 標準に従ってセキュリティ保護されます。|  
|混在モード|トランスポート セキュリティを使用して、整合性、機密性、およびサーバー認証を実現します。 クライアント認証のためにメッセージ セキュリティ (WS-Security およびその他の標準) を使用します。<br /><br /> (このモードの列挙体は `TransportWithMessageCredential` になります)。|  
|両方|両方のレベルで保護と認証を実行します。 このモードでのみ使用可能な[ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)要素。|  
  
## <a name="credentials-and-transfer-security"></a>資格情報と転送セキュリティ  
 A *credential*はクレームされた id または機能のいずれかを確立するために表示されるデータ。 資格情報の提示には、データ自体の提示とデータの所有証明の提示が関与します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、トランスポートとメッセージの両方のセキュリティ レベルで、さまざまな種類の資格情報がサポートされています。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインディング用の資格情報の種類を指定できます。  
  
 多くの国や地域での資格情報の例として、運転免許証があります。 免許証には、個人の ID と資格を表すデータが記載されます。 この免許証には、所有者の写真という形式で所有の証明が含まれています。 免許証は、政府機関など、信頼された証明機関によって発行されます。 免許証には発行機関印が押され (国や地域によってはホログラムが使用され) ており、これによって、改ざんあるいは偽造されたものではないことが示されています。  
  
 一例として、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされている、ユーザー名と (X.509) 証明書の 2 種類の資格情報を考えてみます。  
  
 ユーザー名資格情報では、ユーザー名がクレーム ID を表し、パスワードが所有権の証明を行います。 この場合の信頼された証明機関とは、ユーザー名とパスワードを検証するシステムです。  
  
 証明書資格情報では、サブジェクト名、サブジェクト代替名、または証明書内の特定のフィールドを使用して、クレーム ID と資格を表すことができます。 資格情報に含まれるデータの所有権の証明は、署名の生成のために関連付けられた秘密キーを使用して行われます。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]転送セキュリティをプログラミングして、資格情報を指定するを参照してください。[バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)と[セキュリティ動作](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)です。  
  
### <a name="transport-client-credential-types"></a>トランスポート クライアント資格情報の種類  
 転送セキュリティを使用するアプリケーションを作成するときに使用できる値を次の表に示します。 これらの値は、コードまたはバインディング設定で使用できます。  
  
|設定|説明|  
|-------------|-----------------|  
|なし|クライアントが資格情報を提示する必要がないことを指定します。 匿名クライアントであると解釈されます。|  
|Basic|基本認証を指定します。  詳細については、RFC2617 を参照してください"[HTTP Authentication: Basic and Digest Authentication](http://go.microsoft.com/fwlink/?LinkId=88313)。"。|  
|Digest|ダイジェスト認証を指定します。  詳細については、RFC2617 を参照してください"[HTTP Authentication: Basic and Digest Authentication](http://go.microsoft.com/fwlink/?LinkId=88313)。"。|  
|Ntlm|Windows ドメインで SSPI ネゴシエーションを使用する Windows 認証を指定します。<br /><br /> SSPI ネゴシエーションの結果、Kerberos プロトコルまたは NTLM (NT LanMan) を使用することになります。|  
|Windows|Windows ドメインで SSPI を使用する Windows 認証を指定します。 SSPI では、認証サービスとして Kerberos プロトコルまたは NTLM が選択されます。<br /><br /> SSPI は、最初に Kerberos プロトコルの使用を試み、使用できない場合は NTLM を使用します。|  
|証明書|証明書 (通常は X.509) を使用して、クライアント認証を実行します。|  
  
### <a name="message-client-credential-types"></a>メッセージ クライアント資格情報の種類  
 メッセージ セキュリティを使用するアプリケーションを作成するときに使用できる値を次の表に示します。 これらの値は、コードまたはバインディング設定で使用できます。  
  
|設定|説明|  
|-------------|-----------------|  
|なし|サービスが匿名クライアントとやり取りを行うことが可能になります。|  
|Windows|Windows 資格情報の認証済みコンテキストで SOAP メッセージ交換を実行できるようにします。 SSPI ネゴシエーション機構を使用して、認証サービスとして Kerberos プロトコルまたは NTLM を選択します。|  
|[ユーザー名]|ユーザー名資格情報を使用したクライアントの認証をサービスで要求できるようにします。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、署名の生成やデータの暗号化など、ユーザー名を使用した暗号化操作が許可されないことに注意してください。 そのため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ユーザー名資格情報を使用する場合は、トランスポートが強制的にセキュリティで保護されます。|  
|証明書|証明書を使用したクライアントの認証を、サービスで要求することが可能になります。|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|[!INCLUDE[infocard](../../../../includes/infocard-md.md)] を使用したクライアントの認証をサービスで要求できるようにします。|  
  
### <a name="programming-credentials"></a>資格情報のプログラミング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] プログラミング モデルにより、クライアント資格情報の種類ごとに、サービス動作とチャネル動作を使用して、資格情報の値と検証コントロールを指定できます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティには、サービス資格情報動作とチャネル資格情報動作の 2 種類の資格情報があります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の資格情報動作は、実際のデータ、つまりバインディングによって示されるセキュリティ要件を満たすために使用される資格情報を指定します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、クライアント クラスは、操作呼び出しとメッセージ間で変換されるランタイム コンポーネントです。 すべてのクライアントが <xref:System.ServiceModel.ClientBase%601> クラスを継承します。 基本クラスの <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> プロパティにより、クライアント資格情報のさまざまな値を指定できます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサービス動作は、プログラムによってサービスを制御するために、サービス コントラクト (インターフェイス) を実装するクラスに適用される属性です。 <xref:System.ServiceModel.Description.ServiceCredentials> クラスにより、サービス資格情報の証明書を指定でき、さらにクライアント資格情報のさまざまな種類に対応するクライアント検証設定を指定できます。  
  
### <a name="negotiation-model-for-message-security"></a>メッセージ セキュリティのネゴシエーション モデル  
 メッセージ セキュリティ モードでは、クライアント側でサービス資格情報が帯域外で構成されるように転送のセキュリティを設定できます。 たとえば、Windows 証明書ストアに格納されている証明書を使用する場合は、Microsoft 管理コンソール (MMC: Microsoft Management Console) スナップインなどのツールを使用する必要があります。  
  
 また、メッセージ セキュリティ モードでは、初期ネゴシエーションの一環としてサービス資格情報がクライアントと交換されるように転送のセキュリティを実行できます。 ネゴシエーションを有効にするには、<xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティを `true` に設定します。  
  
## <a name="see-also"></a>関連項目  
 [エンドポイントの作成の概要](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
