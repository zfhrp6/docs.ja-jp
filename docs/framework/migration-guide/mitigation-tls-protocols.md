---
title: "軽減策: TLS プロトコル | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1474aeb0e1be38018f9d27c49e8711800ecb9f01
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-tls-protocols"></a>軽減策: TLS プロトコル
.NET Framework 4.6 以降、<xref:System.Net.ServicePointManager?displayProperty=fullName> クラスおよび <xref:System.Net.Security.SslStream?displayProperty=fullName> クラスでは Tls1.0、Tls1.1、または Tls 1.2 のいずれかのプロトコルを使用できるようになりました。 SSL3.0 プロトコルと RC4 の暗号化はサポートされていません。  
  
## <a name="impact"></a>影響  
 この変更は、以下のものに影響を与えます。  
  
-   SSL を使用して <xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient>、および <xref:System.Net.Security.SslStream> のいずれかのタイプで HTTPS サーバーまたはソケット サーバーと対話するすべてのアプリ。  
  
-   Tls1.0、Tls1.1、または Tls 1.2 をサポートするためにアップグレードできない、すべてのサーバー サイド アプリ。  
  
## <a name="mitigation"></a>軽減策  
 推奨される軽減策はサーバー側のアプリを Tls1.0、Tls1.1、または Tls 1.2 にアップグレードすることです。 これが適切でない場合、またはクライアント アプリが破損している場合は、次の 2 つの方法のいずれかで、<xref:System.AppContext> クラスを使用してこの機能を無効にすることができます。  
  
-   プログラム的に。次のようにコード スニペットを使用します。  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <xref:System.Net.ServicePointManager> オブジェクトの初期化が行われるのは 1 回だけなので、アプリケーションはこれらの互換性設定の定義を最初に行う必要があります。  
  
-   これを行うには、次の行を app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加します。  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 ただし、既定の動作を除外することは、アプリケーションの安全性を低下させるので推奨されません。  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
