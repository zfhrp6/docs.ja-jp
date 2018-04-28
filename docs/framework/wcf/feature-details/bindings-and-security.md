---
title: バインディングとセキュリティ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
caps.latest.revision: 42
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 5eb1019694f6228edbe3656849b85dfa7611ef18
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="bindings-and-security"></a>バインディングとセキュリティ
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に用意されたシステム指定のバインディングを使用すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションをすばやくプログラミングできます。 1 つの例外を除き、すべてのバインディングにはセキュリティ スキームが含まれており、既定で有効になっています。 ここでは、セキュリティ ニーズに適した正しいバインディングの選択方法について説明します。  
  
 概要については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]セキュリティを参照してください[セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)です。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] プログラミング[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]バインドを使用して、参照してください[WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)です。  
  
 バインディングを既に選択した場合のセキュリティに関連付けられている実行時の動作に関する詳細を見つかります[セキュリティ動作](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)です。  
  
 セキュリティ機能のなかには、システム指定のバインディングを使用してプログラミングできないものがあります。 詳細コントロールがカスタム バインドを使用して、次を参照してください。[のカスタム バインディングのセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)します。  
  
## <a name="security-functions-of-bindings"></a>バインディングのセキュリティ機能  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、ほとんどのニーズを満たすシステム指定のバインディングが多数用意されています。 特定のバインディングでは不十分な場合は、カスタム バインドを作成することもできます。 システム指定のバインディングの一覧は、次を参照してください。[システム指定のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)です。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] カスタム バインディングを参照してください[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のすべてのバインディングには、API としての形式と、構成ファイルで使用する XML 要素としての形式という 2 つの形式があります。 たとえば、 `WSHttpBinding` (API)、対応するには、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。  
  
 以下のセクションでは、各バインディングについて両方の形式を示し、セキュリティ機能の概要を説明します。  
  
### <a name="basichttp"></a>BasicHttp  
 コードを使用して、<xref:System.ServiceModel.BasicHttpBinding>クラスは、構成を使用して、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。  
  
 このバインディングは、次のような既存のさまざまなテクノロジと共に使用できるようにデザインされています。  
  
-   ASP.NET Web サービス (ASMX) Version 1  
  
-   Web サービス拡張 (WSE) アプリケーション  
  
-   基本プロファイル、Web Services Interoperability で定義されている (WS-すれば) 仕様 ([http://go.microsoft.com/fwlink/?LinkId=38955](http://go.microsoft.com/fwlink/?LinkId=38955))。  
  
-   WS-I で定義されている基本セキュリティ プロファイル  
  
 既定では、このバインディングはセキュリティで保護されません。 ASMX サービスと相互運用するように設計されています。 セキュリティを有効にした場合、このバインディングは、インターネット インフォメーション サービス (IIS: Internet Information Services) のセキュリティ機構 (基本認証、ダイジェスト、Windows 統合セキュリティなど) とシームレスに相互運用できるように設計されています。 詳細については、次を参照してください。[トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)です。 このバインディングでは、以下をサポートしています。  
  
-   HTTPS トランスポート セキュリティ  
  
-   HTTP 基本認証  
  
-   WS-Security。  
  
 詳細については、「<xref:System.ServiceModel.BasicHttpSecurity>」、「<xref:System.ServiceModel.BasicHttpMessageSecurity>」、「<xref:System.ServiceModel.BasicHttpMessageCredentialType>」、および「<xref:System.ServiceModel.BasicHttpSecurityMode>」を参照してください。  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 コードを使用して、<xref:System.ServiceModel.WSHttpBinding>クラスは、構成を使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。  
  
 既定では、このバインディングは WS-Security 仕様を実装しており、WS-* 仕様を実装するサービスとの相互運用性があります。 次のセキュリティをサポートします。  
  
-   HTTPS トランスポート セキュリティ  
  
-   WS-Security。  
  
-   SOAP メッセージ資格情報セキュリティを使用した、HTTPS トランスポート保護による呼び出し元の認証。  
  
 詳細については、次を参照してください。 <xref:System.ServiceModel.WSHttpSecurity>、 <xref:System.ServiceModel.MessageSecurityOverHttp>、 <xref:System.ServiceModel.MessageCredentialType>、 <xref:System.ServiceModel.SecurityMode>、 <xref:System.ServiceModel.HttpTransportSecurity>、 <xref:System.ServiceModel.HttpClientCredentialType>、および<xref:System.ServiceModel.HttpProxyCredentialType>です。  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 コードを使用して、<xref:System.ServiceModel.WSDualHttpBinding>クラスは、構成を使用して、 [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。  
  
 このバインディングは、双方向サービス アプリケーションを有効にするために設計されています。 このバインディングは、メッセージ ベースの転送セキュリティ用に WS-Security 仕様を実装しています。 トランスポート セキュリティは使用できません。 既定では、次の機能を提供します。  
  
-   WS-ReliableMessaging を実装して信頼性を確保します。  
  
-   WS-Security を実装して転送セキュリティおよび認証を実現します。  
  
-   HTTP を使用してメッセージを配信します。  
  
-   テキスト/XML メッセージ エンコーディングを使用します。  
  
 バインディングで WS-Security (メッセージ層セキュリティ) を使用すると、次のパラメーターを構成できるようになります。  
  
-   暗号アルゴリズムを決定するためのセキュリティ アルゴリズム スイート  
  
-   以下を行うためのバインディング オプション  
  
    -   クライアントで帯域外で使用可能なサービス資格情報の提供  
  
    -   チャネル セットアップの一部としてサービスからネゴシエートされるサービス資格情報の提供  
  
 詳細については、<xref:System.ServiceModel.WSDualHttpSecurity> および <xref:System.ServiceModel.WSDualHttpSecurityMode> を参照してください。  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 コードを使用して、<xref:System.ServiceModel.NetTcpBinding>クラスは、構成を使用して、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)です。  
  
 このバインディングは複数のコンピューター間での通信に最適化されています。 既定では、次の特性があります。  
  
-   トランスポート層セキュリティを実装します。  
  
-   Windows セキュリティを利用して、転送セキュリティと認証を確保します。  
  
-   トランスポートに TCP を使用します。  
  
-   バイナリ メッセージのエンコードを実装します。  
  
-   WS-ReliableMessaging を実装します。  
  
 選択できる方法は次のとおりです。  
  
-   メッセージ層セキュリティ (WS-Security を使用)  
  
-   メッセージ資格情報を使用するトランスポート セキュリティ (TLS (Transport Layer Security) over TCP によって実現される機密性と整合性、および WS-Security によって提供される承認に使用する資格情報)  
  
 詳細については、次を参照してください。 <xref:System.ServiceModel.NetTcpSecurity>、 <xref:System.ServiceModel.TcpTransportSecurity>、 <xref:System.ServiceModel.TcpClientCredentialType>、 <xref:System.ServiceModel.MessageSecurityOverTcp>、および<xref:System.ServiceModel.MessageCredentialType>です。  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 コードを使用して、<xref:System.ServiceModel.NetNamedPipeBinding>クラスは、構成を使用して、 [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)です。  
  
 このバインディングは、(通常では同じコンピューター上の) 複数プロセス間の通信に最適化されています。 既定では、このバインディングには次の特性があります。  
  
-   トランスポート セキュリティを使用して、メッセージ転送と認証を実現します。  
  
-   名前付きパイプを使用してメッセージを配信します。  
  
-   バイナリ メッセージのエンコードを実装します。  
  
-   暗号化とメッセージの署名を使用します。  
  
 選択できる方法は次のとおりです。  
  
-   Windows セキュリティを使用した認証  
  
 詳細については、「<xref:System.ServiceModel.NetNamedPipeSecurity>「<xref:System.ServiceModel.NetNamedPipeSecurityMode>および「<xref:System.ServiceModel.NamedPipeTransportSecurity>」を参照してください。  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 コードを使用して、<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>クラスは、構成を使用して、 [ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)です。  
  
 このバインディングは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ (Microsoft Message Queuing) 以外のエンドポイントと相互運用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントおよびサービスの作成用に最適化されています。  
  
 既定では、このバインディングはトランスポート セキュリティを使用し、次のセキュリティ特性があります。  
  
-   セキュリティは無効 (なし) にできます。  
  
-   MSMQ トランスポート セキュリティ (トランスポート)。  
  
 詳細については、<xref:System.ServiceModel.NetMsmqSecurity> および <xref:System.ServiceModel.NetMsmqSecurityMode> を参照してください。  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 コードを使用して、<xref:System.ServiceModel.NetMsmqBinding>クラスは、構成を使用して、 [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)です。  
  
 このバインディングは、MSMQ のキューに置かれたメッセージのサポートを必要とする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの作成時に使用します。  
  
 既定では、このバインディングはトランスポート セキュリティを使用し、次のセキュリティ特性があります。  
  
-   セキュリティは無効 (なし) にできます。  
  
-   MSMQ トランスポート セキュリティ (トランスポート)。  
  
-   SOAP に基づくメッセージ セキュリティ (メッセージ)。  
  
-   トランスポート セキュリティとメッセージ セキュリティ (両方)。  
  
-   サポートされるクライアント資格情報の種類 : なし、Windows、UserName、証明書、IssuedToken。  
  
 <xref:System.ServiceModel.MessageCredentialType.Certificate> 資格情報は、セキュリティ モードが <xref:System.ServiceModel.NetMsmqSecurityMode.Both> または <xref:System.ServiceModel.NetMsmqSecurityMode.Message> に設定されている場合にのみサポートされます。  
  
 詳細については、<xref:System.ServiceModel.MessageSecurityOverMsmq> および <xref:System.ServiceModel.MsmqTransportSecurity> を参照してください。  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 コードを使用して、<xref:System.ServiceModel.WSFederationHttpBinding>クラスは、構成を使用して、 [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)です。  
  
 既定では、このバインディングは WS-Security (メッセージ層セキュリティ) を使用します。  
  
 詳細については、次を参照してください。[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)、 <xref:System.ServiceModel.WSFederationHttpSecurity>、および<xref:System.ServiceModel.WSFederationHttpSecurityMode>です。  
  
## <a name="custom-bindings"></a>カスタム バインディング  
 システム指定のバインディングがいずれも要件を満たさない場合は、カスタム セキュリティ バインド要素を使用してカスタム バインドを作成できます。 詳細については、次を参照してください。[のカスタム バインディングのセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)します。  
  
## <a name="binding-choices"></a>バインディングの選択肢  
 次の表は、セキュリティ モード設定で提供される機能をまとめたものです。つまり、セキュリティ モードを `Transport`、`Message`、または `TransportWithMessageCredential` に設定したときに使用できる機能の一覧です。 アプリケーションで必要なセキュリティ機能を決定するときに、この表を参考にしてください。  
  
|設定|フィーチャー|  
|-------------|--------------|  
|Transport|サーバー認証<br /><br /> クライアント認証<br /><br /> Point-to-Point のセキュリティ<br /><br /> 相互運用性<br /><br /> ハードウェアの高速化<br /><br /> 高いスループット<br /><br /> セキュリティで保護されたファイアウォール<br /><br /> 待ち時間の長いアプリケーション<br /><br /> 複数のホップでの再暗号化|  
|メッセージ|サーバー認証<br /><br /> クライアント認証<br /><br /> エンド ツー エンドのセキュリティ<br /><br /> 相互運用性<br /><br /> 多様なクレーム<br /><br /> フェデレーション<br /><br /> 複数要因の認証<br /><br /> カスタム トークン<br /><br /> Notary/Timestamp サービス<br /><br /> 待ち時間の長いアプリケーション<br /><br /> メッセージ署名の永続化|  
|TransportWithMessageCredential|サーバー認証<br /><br /> クライアント認証<br /><br /> Point-to-Point のセキュリティ<br /><br /> 相互運用性<br /><br /> ハードウェアの高速化<br /><br /> 高いスループット<br /><br /> 多様なクライアント クレーム<br /><br /> フェデレーション<br /><br /> 複数要因の認証<br /><br /> カスタム トークン<br /><br /> セキュリティで保護されたファイアウォール<br /><br /> 待ち時間の長いアプリケーション<br /><br /> 複数のホップでの再暗号化|  
  
 さまざまなモード設定をサポートするバインディングを次の表に示します。 サービス エンドポイントを作成するときは、使用するバインディングをこの表から選択してください。  
  
|バインド|トランスポート モードのサポート|メッセージ モードのサポート|TransportWithMessageCredential のサポート|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|[はい]|はい|はい|  
|`WSHttpBinding`|はい|はい|はい|  
|`WSDualHttpBinding`|いいえ|はい|いいえ|  
|`NetTcpBinding`|はい|はい|はい|  
|`NetNamedPipeBinding`|はい|いいえ|Ｘ|  
|`NetMsmqBinding`|はい|はい|いいえ|  
|`MsmqIntegrationBinding`|はい|いいえ|Ｘ|  
|`wsFederationHttpBinding`|Ｘ|はい|[はい]|  
  
## <a name="transport-credentials-in-bindings"></a>バインディングにおけるトランスポート資格情報  
 トランスポート セキュリティ モードで `BasicHttpBinding` または `WSHttpBinding` を使用するときに使用できるクライアント資格情報の種類を、次の表に示します。  
  
|型|説明|  
|----------|-----------------|  
|なし|クライアントが資格情報を提示する必要がないことを指定します。 匿名クライアントであると解釈されます。|  
|Basic|基本認証です。 詳細についてを参照してください RFC 2617 – HTTP Authentication: Basic and Digest Authentication で利用可能な[ http://go.microsoft.com/fwlink/?LinkId=84023](http://go.microsoft.com/fwlink/?LinkId=84023)です。|  
|Digest|ダイジェスト認証です。 詳細についてを参照してください RFC 2617 – HTTP Authentication: Basic and Digest Authentication で利用可能な[ http://go.microsoft.com/fwlink/?LinkId=84023](http://go.microsoft.com/fwlink/?LinkId=84023)です。|  
|NTLM|NTLM (NT LAN Manager) 認証です。|  
|Windows|Windows 認証です。|  
|証明書|証明書を使用して実行される認証です。|  
|IssuedToken|セキュリティ トークン サービスまたは [!INCLUDE[infocard](../../../../includes/infocard-md.md)] によって発行されたトークンを使用したクライアントの認証を、サービスが要求できるようにします。 詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)です。|  
  
### <a name="message-client-credentials-in-bindings"></a>バインディングにおけるメッセージ クライアント資格情報  
 メッセージ セキュリティ モードでバインディングを使用するときに使用できるクライアント資格情報の種類を次の表に示します。  
  
|型|説明|  
|----------|-----------------|  
|なし|サービスが匿名クライアントとやり取りを行うことが可能になります。|  
|Windows|Windows 資格情報の認証済みコンテキストの制御下で SOAP メッセージ交換を行うことができます。|  
|UserName|サービスが、ユーザー名資格情報を使用したクライアントの認証を要求できるようにします。 セキュリティ モードが `TransportWithMessageCredential` に設定されている場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、パスワード ダイジェストの送信、またはパスワードを使用したキーの派生、およびメッセージ モード セキュリティでのこのようなキーの使用がサポートされません。 そのため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ユーザー名資格情報を使用する場合は、トランスポートが強制的にセキュリティで保護されます。|  
|証明書|証明書を使用したクライアントの認証を、サービスで要求することが可能になります。|  
|IssuedToken|サービスは、セキュリティ トークン サービスを使用してカスタム トークンを提供できます。|  
  
## <a name="see-also"></a>関連項目  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [資格情報の種類の選択](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [カスタム バインドを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [セキュリティ動作](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Windows Server App Fabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
