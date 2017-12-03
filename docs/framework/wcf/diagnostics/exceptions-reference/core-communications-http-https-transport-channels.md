---
title: "コア通信: HTTP、HTTPS トランスポート チャネル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81eb778d70722cb44fa8dd4bc3f1152a12d87199
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-httphttps-transport-channels"></a>コア通信 : HTTP/HTTPS トランスポート チャネル
ここでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] の HTTP/HTTPS トランスポート チャネルによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|指定された偽装レベルが指定されました。 明示的な資格情報を使用する場合に 'Impersonation' レベルをサポートできるのは、HTTP ダイジェスト認証のみです。|  
|FramingContentTypeMismatch|指定されたコンテンツの種類は、指定されたサービスでサポートされていませんでした。 クライアントとサービスのバインディングは一致しない場合もあります。|  
|Hosting_SslSettingsMisconfigured|指定されたサービスの SSL (Secure Sockets Layer) 設定が、インターネット インフォメーション サービスの SSL 設定と一致しません。|  
|HttpAuthSchemeAndClientCert|HTTPS リスナー ファクトリが、クライアント証明書と指定された認証方式を要求するように構成されています。 ただし、クライアント認証の方式は、一度に 1 種類しか要求できません。|  
|HttpReceiveFailure|指定された対象への HTTP 応答の受信中にエラーが発生しました。 サービス エンドポイント バインディングが HTTP プロトコルを使用していない可能性があります。 サービスがシャットダウンしたため、HTTP 要求コンテキストがサーバーによって中止された可能性もあります。 詳細については、サーバー ログを参照してください。|  
|HttpRegistrationAccessDenied|HTTP は指定された URL を登録できません。 プロセスにこの名前空間へのアクセス権がありません (詳細については、http://msdn.microsoft.com/library/default.asp?url=/library/http/http/namespace_reservations_registrations_and_routing.asp を参照してください)。|  
|HttpRegistrationAlreadyExists|HTTP は指定された URL を登録できません。 別のアプリケーションが既にこの URL を HTTP.SYS に登録しています。|  
|HttpRegistrationPortInUse|HTTP が指定された URL を登録できませんでした。指定された TCP ポートは別のアプリケーションが使用しています。|  
|HttpSendFailure|指定された対象への HTTP 要求の発行中にエラーが発生しました。 この原因がセキュリティ バインディングの不一致ではないことを確認してください。 また、サービスが SSL (Secure Sockets Layer) 用に構成されていないことも確認してください。|  
|MessageXmlProtocolError|ネットワークから受信した XML に問題があります。 詳細については、内部例外を参照してください。|  
|MissingContentType|受信側は、指定された対象への要求でコンテンツの種類が指定されていないことを示すエラーを返しました。 詳細については、内部例外を参照してください。|  
|ProxyAuthenticationLevelMismatch|HTTP プロキシ認証の資格情報で、対象サーバーの認証要件より厳しい要件である相互認証が指定されています。|  
|ProxyImpersonationLevelMismatch|HTTP プロキシ認証の資格情報で、対象サーバーの認証制限より厳しい制限である偽装レベルの制限が指定されています。|  
|SecureChannelFailure|指定された証明機関との間で、SSL/TLS のセキュリティで保護されたチャネルを確立できませんでした。|  
|TrustFailure|指定された証明機関との間の SSL/TLS のセキュリティで保護されたチャネルで、信頼関係を確立できません。|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|HttpTransportBinding 要素では、明示的なプロキシ アドレスだけでなく、UseDefaultWebProxy=true も指定できません。|
