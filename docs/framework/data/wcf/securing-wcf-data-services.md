---
title: "WCF Data Services のセキュリティ保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88d480982682718bd8fd62f5b4c2b4057d704bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="securing-wcf-data-services"></a>WCF Data Services のセキュリティ保護
このトピックでは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] と、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] をサポートするサービスにアクセスするアプリケーションの開発、配置、および実行に特有のセキュリティの注意点について説明します。 このほかに、安全な [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションを作成するための推奨事項にも従うようにしてください。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ベースの [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスをセキュリティで保護する方法を計画するときには、認証 (プリンシパルの ID を発見および確認するプロセス) と承認 (認証されたプリンシパルが要求されたリソースにアクセスできるかどうかを判断するプロセス) の両方を解決する必要があります。 また、SSL を使用してメッセージを暗号化するかどうかを検討する必要もあります。  
  
## <a name="authenticating-client-requests"></a>クライアント要求の認証  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、認証を独自に実装する代わりにデータ サービス ホストに依存しています。 したがって、ネットワーク ホストによって受信要求が既に認証されていること、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] によって提供されるインターフェイスを使用して要求のプリンシパルが正しく識別されていることが前提とされます。 これらの認証オプションとアプローチの詳細については[OData および認証シリーズ](http://go.microsoft.com/fwlink/?LinkId=200381)です。  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>WCF Data Service の認証オプション  
 次の表に、WCF Data Service への要求を認証するために使用できる認証メカニズムを示します。  
  
|認証オプション|説明|  
|----------------------------|-----------------|  
|匿名認証|匿名 HTTP 認証が有効になっている場合は、すべてのプリンシパルがデータ サービスに接続できます。 匿名アクセスには資格情報は必要ありません。 このオプションは、だれでもデータ サービスにアクセスできるようにする場合にのみ使用します。|  
|基本認証とダイジェスト認証|ユーザー名とパスワードで構成される資格情報が認証に必要です。 Windows 以外のクライアントの認証がサポートされます。 **セキュリティに関する注意:**基本認証資格情報 (ユーザー名とパスワード) はクリア テキストで送信され、受け取ることができます。 ダイジェスト認証では、指定された資格情報に基づくハッシュが送信されるため、基本認証に比べて安全です。 ただし、どちらの方法も man-in-the-middle 攻撃を受ける可能性があります。 これらの認証方法を使用する場合は、SSL (Secure Sockets Layer) を使用してクライアントとデータ サービスの間の通信を暗号化することを検討してください。 <br /><br /> Microsoft インターネット インフォメーション サービス (IIS) には、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションの HTTP 要求に対する基本認証とダイジェスト認証の実装が用意されています。 この Windows 認証プロバイダーの実装を使用すると、.NET Framework クライアント アプリケーションで、資格情報を要求の HTTP ヘッダーでデータ サービスに渡して Windows ユーザーの認証をシームレスにネゴシエートできます。 詳細については、次を参照してください。[ダイジェスト認証のテクニカル リファレンス](http://go.microsoft.com/fwlink/?LinkId=200408)です。<br /><br /> データ サービスで Windows 資格情報以外のカスタム認証サービスに基づく基本認証を使用する場合は、認証用のカスタム [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] HTTP モジュールを実装する必要があります。<br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]カスタムの基本的な認証スキームを使用する方法[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]、上の投稿をご覧ください[カスタム基本認証](http://go.microsoft.com/fwlink/?LinkID=200388)で、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]および認証シリーズ。|  
|Windows 認証|Windows ベースの資格情報の交換には、NTLM または Kerberos が使用されます。 このメカニズムは基本認証やダイジェスト認証より安全ですが、クライアントが Windows ベースのアプリケーションである必要があります。 IIS には、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションの HTTP 要求に対する Windows 認証の実装も用意されています。 詳細については、次を参照してください。 [ASP.NET フォーム認証の概要](http://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708)です。<br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]Windows 認証を併用する方法[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]、上の投稿をご覧ください[Windows 認証](http://go.microsoft.com/fwlink/?LinkID=200384)で、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]および認証シリーズ。|  
|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] フォーム認証|フォーム認証では、独自のコードを使用してユーザーを認証し、認証トークンをクッキーまたはページ URL に保存できます。 作成したログイン フォームを使用してユーザーのユーザー名とパスワードを認証します。 認証されない要求はログイン ページにリダイレクトされ、ここでユーザーが資格情報を入力してフォームを送信します。 アプリケーションで要求を認証する場合、後続の要求で使用する ID を再確立するためのキーが含まれたチケットをシステムが発行します。 詳細については、次を参照してください。[フォーム認証プロバイダー](http://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47)です。 **セキュリティに関する注意:**既定では、フォーム認証チケットを含む cookie が保護されていないでフォーム認証を使用する場合、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションです。 認証チケットと最初のログイン資格情報の両方を保護するには、SSL を要求することを検討してください。 <br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]使用する方法での認証のフォーム[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]、上の投稿をご覧ください[フォーム認証](http://go.microsoft.com/fwlink/?LinkID=200389)で、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]および認証シリーズ。|  
|クレーム ベースの認証|要求ベースの認証では、データ サービスは、ユーザーを認証する「サードパーティ」の信頼された id プロバイダー サービスに依存します。 ID プロバイダーは、データ サービス リソースへのアクセスを要求しているユーザーを確実に認証し、要求されたリソースへのアクセスを許可するトークンを発行します。 このトークンがデータ サービスに提示され、そのアクセス トークンを発行した識別情報サービスとの信頼関係に基づいてユーザーのアクセスが許可されます。<br /><br /> クレーム ベースの認証プロバイダーの利点は、信頼ドメイン間でさまざまな種類のクライアントの認証に使用できることです。 このようなサードパーティ プロバイダーを使用することにより、ユーザーの管理と認証の要件をデータ サービスからオフロードできます。 OAuth 2.0 は、サービスとしてのフェデレーション認証のために Microsoft Azure AppFabric アクセス制御によってサポートされているクレーム ベースの認証プロトコルであり、 REST ベースのサービスをサポートします。 [!INCLUDE[crexample](../../../../includes/crexample-md.md)]OAuth 2.0 を使用する方法[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]、上の投稿をご覧ください[OData と OAuth](http://go.microsoft.com/fwlink/?LinkId=200514)で、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]および認証シリーズ。|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>クライアント ライブラリの認証  
 既定では、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] サービスに要求を送信する際、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] クライアント ライブラリから資格情報は提供されません。 データ サービスでユーザー認証のためにログイン資格情報が要求されている場合は、<xref:System.Net.NetworkCredential> の <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> プロパティからアクセスできる <xref:System.Data.Services.Client.DataServiceContext> で資格情報を渡すことができます。以下に例を示します。  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 詳細については、次を参照してください。[する方法: データ サービス要求のクライアント資格情報の指定](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)です。  
  
 クレーム ベースのトークンやクッキーなど、<xref:System.Net.NetworkCredential> オブジェクトでは指定できないログイン資格情報がデータ サービスで要求されている場合は、手動で HTTP 要求のヘッダー (通常は `Authorization` と `Cookie`) を設定する必要があります。 この種の認証シナリオの詳細については、投稿をご覧ください。 [OData と認証: クライアント側のフック](http://go.microsoft.com/fwlink/?LinkID=200385)です。 要求メッセージの HTTP ヘッダーを設定する方法の例は、次を参照してください。[する方法: クライアント要求のヘッダーを設定](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)です。  
  
## <a name="impersonation"></a>偽装  
 データ サービスは通常、データ サービスをホストしているワーカー プロセスの資格情報を使用して、要求されたリソース (サーバー上のファイル、データベースなど) にアクセスします。 偽装を使用しているときは、要求を出しているユーザーの Window ID (ユーザー アカウント) で [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションを実行できます。 偽装は、IIS を使用してユーザーを認証するアプリケーションで使用されるのが一般的です。この場合、要求されたリソースへのアクセスにそのプリンシパルの資格情報が使用されます。 詳細については、次を参照してください。 [ASP.NET の偽装](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d)です。  
  
## <a name="configuring-data-service-authorization"></a>データ サービスの承認の構成  
 承認とは、事前に行われた認証に基づいて識別されるプリンシパルまたはプロセスにアプリケーション リソースへのアクセスを許可することです。 一般に、データ サービスのユーザーには、クライアント アプリケーションで必要とされている操作を実行するのに十分な権限のみを与えるようにします。  
  
### <a name="restrict-access-to-data-service-resources"></a>データ サービス リソースへのアクセスの制限  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービスにアクセスできるすべてのユーザーにデータ サービス リソース (エンティティ セットおよびサービス操作) に対する共通の読み取りおよび書き込みのアクセス権が既定で付与されます。 読み取りおよび書き込みのアクセスを定義する規則は、データ サービスによって公開される各エンティティ セットおよびサービス操作に対して個別に定義できます。 読み取りおよび書き込みの両方のアクセスを、クライアント アプリケーションで必要なリソースのみに制限することをお勧めします。 詳細については、次を参照してください。[リソース アクセスの最小要件](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements)です。  
  
### <a name="implement-role-based-interceptors"></a>ロール ベースのインターセプターの実装  
 インターセプターを使用すると、データ サービス リソースに対する要求を、データ サービスによって処理される前にインターセプトすることができます。 詳細については、次を参照してください。[インターセプター](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)です。 インターセプターを使用すると、要求を行っている認証されたユーザーに基づいて承認決定を行うことができます。 [!INCLUDE[crexample](../../../../includes/crexample-md.md)]認証されたユーザー id に基づいて、データ サービス リソースへのアクセスを制限する方法を参照してください[する方法: データ サービス メッセージを傍受](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md)です。  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>永続化データ ストアとローカル リソースへのアクセスの制限  
 永続化ストアにアクセスするためのアカウントには、データベースまたはファイル システムでデータ サービスの要件をサポートするのに十分な権限のみを与えるようにしてください。 匿名認証が使用されている場合は、そのアカウントがホスト アプリケーションの実行に使用されます。 詳細については、「 [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)」を参照してください。 偽装を使用する場合は、認証されたユーザーにそれらのリソースへのアクセスを (通常は Windows グループの一部として) 許可する必要があります。  
  
## <a name="other-security-considerations"></a>その他のセキュリティの考慮事項  
  
### <a name="secure-the-data-in-the-payload"></a>ペイロードのデータの保護  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] は HTTP プロトコルに基づいています。 データ サービスで実装されている認証によっては、HTTP メッセージのヘッダーに重要なユーザー資格情報が含まれている場合があります。 メッセージの本文にも、保護する必要がある貴重な顧客データが含まれている場合があります。 いずれの場合も、SSL を使用してその情報をネットワークで保護することをお勧めします。  
  
### <a name="ignored-message-headers-and-cookies"></a>無視されるメッセージ ヘッダーとクッキー  
 HTTP 要求のヘッダーは、コンテンツ タイプとリソースの場所を宣言するもの以外は無視されます。また、データ サービスによって設定されることはありません。  
  
 クッキーは、認証方式の一部としては使用できますが ([!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] フォーム認証を使用する場合など)、 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では無視されます。 データ サービスのホストによって処理されることはありますが、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ランタイムによって分析されたり返されたりすることはありません。 応答で送信されたクッキーが [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリで処理されることもありません。  
  
### <a name="custom-hosting-requirements"></a>カスタム ホストの要件  
 既定では、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は IIS でホストされる [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションとして作成されます。 そのため、データ サービスでこのプラットフォームのセキュリティ動作を活用できます。 カスタム ホストによってホストされる [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を定義することもできます。 詳細については、次を参照してください。[データ サービスのホスティング](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)です。 データ サービスをホストするコンポーネントとプラットフォームでは、データ サービスへの攻撃を防ぐために次のセキュリティ動作を確保する必要があります。  
  
-   可能なすべての操作について、データ サービス要求で受け入れる URI の長さを制限します。  
  
-   着信および発信の両方の HTTP メッセージのサイズを制限します。  
  
-   任意の時点の未処理の要求の総数を制限します。  
  
-   HTTP ヘッダーとその値のサイズを制限し、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] でヘッダーのデータにアクセスできるようにします。  
  
-   TCP SYN 攻撃やメッセージ リプレイ攻撃などの既知の攻撃を検出して阻止します。  
  
### <a name="values-are-not-further-encoded"></a>値のさらなるエンコード  
 データ サービスに送信されたプロパティ値が [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ランタイムによってさらにエンコードされることはありません。 たとえば、書式設定された HTML コンテンツがエンティティの文字列プロパティに含まれていた場合、データ サービスによってタグが HTML エンコードされることはありません。 応答のプロパティ値についても、データ サービスによってさらなるエンコードが行われることはありません。 クライアント ライブラリで追加のエンコードが行われることもありません。  
  
### <a name="considerations-for-client-applications"></a>クライアント アプリケーションに関する注意点  
 以下のセキュリティの注意点は、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントを使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスにアクセスするアプリケーションに当てはまります。  
  
-   クライアント ライブラリは、データ サービスへのアクセスに使用されるプロトコルで十分なレベルのセキュリティが確保されていることを前提としています。  
  
-   クライアント ライブラリは、基になるプラットフォームによって提供されるトランスポート スタックのタイムアウトや解析のすべてのオプションに対して既定値を使用します。  
  
-   クライアント ライブラリはアプリケーション構成ファイルの設定を読み取りません。  
  
-   クライアント ライブラリにはドメイン間アクセスのメカニズムは実装されていません。 基になる HTTP スタックによって提供されるメカニズムが使用されます。  
  
-   クライアント ライブラリにはユーザー インターフェイス要素はありません。送受信されるデータの表示は行われません。  
  
-   クライアント アプリケーションで常にユーザー入力と信頼されていないサービスからのデータを検証することをお勧めします。  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
