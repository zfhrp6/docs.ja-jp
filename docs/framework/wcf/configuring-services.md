---
title: "サービスの構成 | Microsoft Docs"
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
  - "構成 [WCF]"
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# サービスの構成
サービス コントラクトの設計、実装が終われば、サービスを構成できる状態になります。  クライアント側から見たサービスの動作は、ここで定義、カスタマイズします。サービスと通信するためのアドレス、メッセージの送受信に使うトランスポートやエンコーディング、必要なセキュリティ型などを指定できます。  
  
 定義やカスタマイズは、コード内で強制的に \(簡単には変更できないような形で\) 行う方法と、構成ファイルに記述して行う方法があります。エンドポイントのアドレス、実際に使うトランスポート、セキュリティ スキーマなど、サービスに関するさまざまな事項を定義、カスタマイズできます。  実際、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションのプログラミングにおいては、構成ファイルの記述が作業の大きな部分を占めます。  
  
## このセクションの内容  
 [簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)  
 [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] 以降では、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] には、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成要件を簡略化する新しい既定の構成モデルが付属しています。  特定のサービスに対し [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成を指定しないと、ランタイムは自動的に既定のエンドポイント、バインディング、および動作でサービスを構成します。  
  
 [構成ファイルを使用してサービスを構成する方法](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の構成技術を使用して構成できます。  通常、XML 要素は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスをホストするインターネット インフォメーション サービス \(IIS\) サイトの Web.config ファイルに追加されます。  この要素によって、コンピューターごとにエンドポイント アドレス \(サービスと通信するために使用する実際のアドレス\) などの詳細情報を変更できます。  
  
 [バインディング](../../../docs/framework/wcf/bindings.md)  
 さらに [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] には、一般的な構成がシステム提供のバインディングとして用意されています。これを使用すると、クライアントとサービスの通信方法に関する基本事項 \(トランスポート、セキュリティ、メッセージのエンコーディングなど\) を容易に選択できます。  
  
 [エンドポイント](../../../docs/framework/wcf/endpoints.md)  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを使用して行われるすべての通信では、サービスの*エンドポイント*が使用されます。  エンドポイントには、コントラクト、バインディングで指定されている構成情報、およびサービスの検索場所やサービスに関する情報の取得場所を示すアドレスが設定されています。  
  
 [サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] および既存のセキュリティ機構を使用することにより、機密性、整合性、認証、および承認をサービスに実装できます。  また、セキュリティに関する成功および失敗を監査することも可能です。  
  
 [WS\-I Basic Profile 1.1 の相互運用可能サービスの作成](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 他のプラットフォームやオペレーティング システム上で動作するサービスやクライアントと、相互に運用できるような形でサービスを配置するために必要な事項は、WS\-I Basic Profile 1.1 の仕様に記載されています。  
  
## 関連項目  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## 関連項目  
 [基本的なプログラミング ライフサイクル](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [サービスの設計と実装](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)  
  
 [クライアントを構築する](../../../docs/framework/wcf/building-clients.md)  
  
 [拡張機能の概要](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [管理と診断](../../../docs/framework/wcf/diagnostics/index.md)  
  
## 参照  
 [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)   
 [概念](../../../docs/framework/wcf/conceptual-overview.md)   
 [WCF 機能の詳細](../../../docs/framework/wcf/feature-details/index.md)