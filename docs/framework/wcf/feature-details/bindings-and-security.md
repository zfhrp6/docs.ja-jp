---
title: "バインディングとセキュリティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バインディング [WCF]"
  - "バインディング [WCF], セキュリティ"
  - "WCF セキュリティ"
  - "Windows Communication Foundation, セキュリティ"
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
caps.latest.revision: 42
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 42
---
# バインディングとセキュリティ
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に用意されたシステム指定のバインディングを使用すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションをすばやくプログラミングできます。1 つの例外を除き、すべてのバインディングにはセキュリティ スキームが含まれており、既定で有効になっています。ここでは、セキュリティ ニーズに適した正しいバインディングの選択方法について説明します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティの概要については、「[セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)」を参照してください。バインディングを使用した [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のプログラミング[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)」を参照してください。  
  
 バインディングを既に選択している場合、セキュリティに関連する実行時の動作の詳細については、「[セキュリティ動作](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)」を参照してください。  
  
 セキュリティ機能のなかには、システム指定のバインディングを使用してプログラミングできないものがあります。カスタム バインディングを使用したより細かな制御については、「[カスタム バインディングを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)」を参照してください。  
  
## バインディングのセキュリティ機能  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、ほとんどのニーズを満たすシステム指定のバインディングが多数用意されています。特定のバインディングでは不十分な場合は、カスタム バインディングを作成することもできます。システム指定のバインディングの一覧については、「[システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。カスタム バインディング[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)」を参照してください。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のすべてのバインディングには、API としての形式と、構成ファイルで使用する XML 要素としての形式という 2 つの形式があります。たとえば、`WSHttpBinding` \(API\) に対応する要素は [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。  
  
 以下のセクションでは、各バインディングについて両方の形式を示し、セキュリティ機能の概要を説明します。  
  
### BasicHttp  
 コードでは <xref:System.ServiceModel.BasicHttpBinding> クラスを使用し、構成では [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)を使用します。  
  
 このバインディングは、次のような既存のさまざまなテクノロジと共に使用できるようにデザインされています。  
  
-   ASP.NET Web サービス \(ASMX\) Version 1  
  
-   Web サービス拡張 \(WSE\) アプリケーション  
  
-   WS\-I \(Web Services Interoperability\) 仕様 \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=38955](http://go.microsoft.com/fwlink/?LinkId=38955)\) で定義されている基本プロファイル  
  
-   WS\-I で定義されている基本セキュリティ プロファイル  
  
 既定では、このバインディングはセキュリティで保護されません。ASMX サービスと相互運用するように設計されています。セキュリティを有効にした場合、このバインディングは、インターネット インフォメーション サービス \(IIS: Internet Information Services\) のセキュリティ機構 \(基本認証、ダイジェスト、Windows 統合セキュリティなど\) とシームレスに相互運用できるように設計されています。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).このバインディングでは、以下をサポートしています。  
  
-   HTTPS トランスポート セキュリティ  
  
-   HTTP 基本認証  
  
-   WS\-Security。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.BasicHttpSecurity>、<xref:System.ServiceModel.BasicHttpMessageSecurity>、<xref:System.ServiceModel.BasicHttpMessageCredentialType>、および <xref:System.ServiceModel.BasicHttpSecurityMode>。  
  
### WSHttpBinding  
 コードでは <xref:System.ServiceModel.WSHttpBinding> クラスを使用し、構成では [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を使用します。  
  
 既定では、このバインディングは WS\-Security 仕様を実装しており、WS\-\* 仕様を実装するサービスとの相互運用性があります。次のセキュリティをサポートします。  
  
-   HTTPS トランスポート セキュリティ。  
  
-   WS\-Security。  
  
-   SOAP メッセージ資格情報セキュリティを使用した、HTTPS トランスポート保護による呼び出し元の認証。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.WSHttpSecurity>、<xref:System.ServiceModel.MessageSecurityOverHttp>、<xref:System.ServiceModel.MessageCredentialType>、<xref:System.ServiceModel.SecurityMode>、<xref:System.ServiceModel.HttpTransportSecurity>、<xref:System.ServiceModel.HttpClientCredentialType>、および <xref:System.ServiceModel.HttpProxyCredentialType>。  
  
### WSDualHttpBinding  
 コードでは <xref:System.ServiceModel.WSDualHttpBinding> クラスを使用し、構成では [\<wsDualHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)を使用します。  
  
 このバインディングは、双方向サービス アプリケーションを有効にするために設計されています。このバインディングは、メッセージ ベースの転送セキュリティ用に WS\-Security 仕様を実装しています。トランスポート セキュリティは使用できません。既定では、次の機能を提供します。  
  
-   WS\-ReliableMessaging を実装して信頼性を確保します。  
  
-   WS\-Security を実装して転送セキュリティおよび認証を実現します。  
  
-   HTTP を使用してメッセージを配信します。  
  
-   テキスト\/XML メッセージ エンコーディングを使用します。  
  
 バインディングで WS\-Security \(メッセージ層セキュリティ\) を使用すると、次のパラメーターを構成できるようになります。  
  
-   暗号アルゴリズムを決定するためのセキュリティ アルゴリズム スイート  
  
-   以下を行うためのバインディング オプション  
  
    -   クライアントで帯域外で使用可能なサービス資格情報の提供  
  
    -   チャネル セットアップの一部としてサービスからネゴシエートされるサービス資格情報の提供  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「<xref:System.ServiceModel.WSDualHttpSecurity>」および「<xref:System.ServiceModel.WSDualHttpSecurityMode>」を参照してください。  
  
### NetTcpBinding  
 コードでは <xref:System.ServiceModel.NetTcpBinding> クラスを使用し、構成では [\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)を使用します。  
  
 このバインディングは複数のコンピューター間での通信に最適化されています。既定では、次の特性があります。  
  
-   トランスポート層セキュリティを実装します。  
  
-   Windows セキュリティを利用して、転送セキュリティと認証を確保します。  
  
-   トランスポートに TCP を使用します。  
  
-   バイナリ メッセージのエンコードを実装します。  
  
-   WS\-ReliableMessaging を実装します。  
  
 選択できる方法は次のとおりです。  
  
-   メッセージ層セキュリティ \(WS\-Security を使用\)  
  
-   メッセージ資格情報を使用するトランスポート セキュリティ \(TLS \(Transport Layer Security\) over TCP によって実現される機密性と整合性、および WS\-Security によって提供される承認に使用する資格情報\)  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.NetTcpSecurity>、<xref:System.ServiceModel.TcpTransportSecurity>、<xref:System.ServiceModel.TcpClientCredentialType>、<xref:System.ServiceModel.MessageSecurityOverTcp>、および <xref:System.ServiceModel.MessageCredentialType>。  
  
### NetNamedPipeBinding  
 コードでは <xref:System.ServiceModel.NetNamedPipeBinding> クラスを使用し、構成では [\<netNamedPipeBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)を使用します。  
  
 このバインディングは、\(通常では同じコンピューター上の\) 複数プロセス間の通信に最適化されています。既定では、このバインディングには次の特性があります。  
  
-   トランスポート セキュリティを使用して、メッセージ転送と認証を実現します。  
  
-   名前付きパイプを使用してメッセージを配信します。  
  
-   バイナリ メッセージのエンコードを実装します。  
  
-   暗号化とメッセージの署名を使用します。  
  
 選択できる方法は次のとおりです。  
  
-   Windows セキュリティを使用した認証  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「<xref:System.ServiceModel.NetNamedPipeSecurity>」、「<xref:System.ServiceModel.NetNamedPipeSecurityMode>」、および「<xref:System.ServiceModel.NamedPipeTransportSecurity>」を参照してください。  
  
### MsmqIntegrationBinding  
 コードでは <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> クラスを使用し、構成では [\<msmqIntegrationBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)を使用します。  
  
 このバインディングは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ \(Microsoft Message Queuing\) 以外のエンドポイントと相互運用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントおよびサービスの作成用に最適化されています。  
  
 既定では、このバインディングはトランスポート セキュリティを使用し、次のセキュリティ特性を提供します。  
  
-   セキュリティは無効 \(なし\) にできます。  
  
-   MSMQ トランスポート セキュリティ \(トランスポート\)。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「<xref:System.ServiceModel.NetMsmqSecurity>」および「<xref:System.ServiceModel.NetMsmqSecurityMode>」を参照してください。  
  
### NetMsmqBinding  
 コードでは <xref:System.ServiceModel.NetMsmqBinding> クラスを使用し、構成では [\<netMsmqBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)を使用します。  
  
 このバインディングは、MSMQ のキューに置かれたメッセージのサポートを必要とする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの作成時に使用します。  
  
 既定では、このバインディングはトランスポート セキュリティを使用し、次のセキュリティ特性があります。  
  
-   セキュリティは無効 \(なし\) にできます。  
  
-   MSMQ トランスポート セキュリティ \(トランスポート\)。  
  
-   SOAP に基づくメッセージ セキュリティ \(メッセージ\)。  
  
-   トランスポート セキュリティとメッセージ セキュリティ \(両方\)。  
  
-   サポートされるクライアント資格情報の種類 : なし、Windows、UserName、証明書、IssuedToken。  
  
 <xref:System.ServiceModel.MessageCredentialType> 資格情報は、セキュリティ モードが <xref:System.ServiceModel.NetMsmqSecurityMode> または <xref:System.ServiceModel.NetMsmqSecurityMode> に設定されている場合にのみサポートされます。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「<xref:System.ServiceModel.MessageSecurityOverMsmq>」および「<xref:System.ServiceModel.MsmqTransportSecurity>」を参照してください。  
  
### WSFederationHttpBinding  
 コードでは <xref:System.ServiceModel.WSFederationHttpBinding> クラスを使用し、構成では [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)を使用します。  
  
 既定では、このバインディングは WS\-Security \(メッセージ層セキュリティ\) を使用します。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]、「[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)」、「<xref:System.ServiceModel.WSFederationHttpSecurity>」、および「<xref:System.ServiceModel.WSFederationHttpSecurityMode>」を参照してください。  
  
## カスタム バインディング  
 システム指定のバインディングがいずれも要件を満たさない場合は、カスタム セキュリティ バインド要素を使用してカスタム バインディングを作成できます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][カスタム バインディングを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## バインディングの選択肢  
 次の表は、セキュリティ モード設定で提供される機能をまとめたものです。つまり、セキュリティ モードを `Transport`、`Message`、または `TransportWithMessageCredential` に設定したときに使用できる機能の一覧です。アプリケーションで必要なセキュリティ機能を決定するときに、この表を参考にしてください。  
  
|設定|機能|  
|--------|--------|  
|トランスポート|サーバー認証<br /><br /> クライアント認証<br /><br /> Point\-to\-Point のセキュリティ<br /><br /> 相互運用性<br /><br /> ハードウェア アクセラレータ<br /><br /> 高いスループット<br /><br /> セキュリティで保護されたファイアウォール<br /><br /> 待機時間の長いアプリケーション<br /><br /> 複数のホップでの再暗号化|  
|メッセージ|サーバー認証<br /><br /> クライアント認証<br /><br /> エンド ツー エンドのセキュリティ<br /><br /> 相互運用性<br /><br /> 多様なクレーム<br /><br /> フェデレーション<br /><br /> 複数要因の認証<br /><br /> カスタム トークン<br /><br /> Notary\/Timestamp サービス<br /><br /> 待ち時間の長いアプリケーション<br /><br /> メッセージ署名の永続化|  
|TransportWithMessageCredential|サーバー認証<br /><br /> クライアント認証<br /><br /> Point\-to\-Point のセキュリティ<br /><br /> 相互運用性<br /><br /> ハードウェアの高速化<br /><br /> 高いスループット<br /><br /> 多様なクライアント クレーム<br /><br /> フェデレーション<br /><br /> 複数要因の認証<br /><br /> カスタム トークン<br /><br /> セキュリティで保護されたファイアウォール<br /><br /> 待ち時間の長いアプリケーション<br /><br /> 複数のホップでの再暗号化|  
  
 さまざまなモード設定をサポートするバインディングを次の表に示します。サービス エンドポイントを作成するときは、使用するバインディングをこの表から選択してください。  
  
|バインディング|トランスポート モードのサポート|メッセージ モードのサポート|TransportWithMessageCredential のサポート|  
|-------------|----------------------|--------------------|------------------------------------------|  
|`BasicHttpBinding`|○|○|○|  
|`WSHttpBinding`|○|○|○|  
|`WSDualHttpBinding`|×|○|×|  
|`NetTcpBinding`|○|○|○|  
|`NetNamedPipeBinding`|○|×|×|  
|`NetMsmqBinding`|○|○|×|  
|`MsmqIntegrationBinding`|○|×|×|  
|`wsFederationHttpBinding`|×|○|○|  
  
## バインディングにおけるトランスポート資格情報  
 トランスポート セキュリティ モードで `BasicHttpBinding` または `WSHttpBinding` を使用するときに使用できるクライアント資格情報の種類を、次の表に示します。  
  
|種類|説明|  
|--------|--------|  
|なし|クライアントは資格情報を提示する必要がないことを指定します。匿名クライアントであると解釈されます。|  
|基本|基本認証です。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「RFC 2617 – HTTP Authentication: Basic and Digest Authentication」を参照してください。このドキュメントは、[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=84023](http://go.microsoft.com/fwlink/?LinkId=84023) で参照できます。|  
|ダイジェスト|ダイジェスト認証です。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「RFC 2617 – HTTP Authentication: Basic and Digest Authentication」を参照してください。このドキュメントは、[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=84023](http://go.microsoft.com/fwlink/?LinkId=84023) で参照できます。|  
|NTLM|NTLM \(NT LAN Manager\) 認証です。|  
|Windows|Windows 認証です。|  
|証明書|証明書を使用して実行される認証です。|  
|IssuedToken|セキュリティ トークン サービスまたは [!INCLUDE[infocard](../../../../includes/infocard-md.md)] によって発行されたトークンを使用したクライアントの認証を、サービスが要求できるようにします。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][フェデレーションと発行済みトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### バインディングにおけるメッセージ クライアント資格情報  
 メッセージ セキュリティ モードでバインディングを使用するときに使用できる、クライアント資格情報の種類を次の表に示します。  
  
|型|説明|  
|-------|--------|  
|なし|サービスが匿名クライアントとやり取りを行うことが可能になります。|  
|Windows|Windows 資格情報の認証済みコンテキストの制御下で SOAP メッセージ交換を行うことができます。|  
|UserName|サービスが、ユーザー名資格情報を使用したクライアントの認証を要求できるようにします。セキュリティ モードが `TransportWithMessageCredential` に設定されている場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、パスワード ダイジェストの送信、またはパスワードを使用したキーの派生、およびメッセージ モード セキュリティでのこのようなキーの使用がサポートされません。そのため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ユーザー名資格情報を使用する場合に、トランスポートが強制的にセキュリティで保護されます。|  
|Certificate|証明書を使用したクライアントの認証を、サービスで要求することが可能になります。|  
|IssuedToken|サービスは、セキュリティ トークン サービスを使用してカスタム トークンを提供できます。|  
  
## 参照  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [資格情報の種類の選択](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [カスタム バインディングを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)   
 [セキュリティ動作](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [Windows Server AppFabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)