---
title: "インターネット インフォメーション サービスでのホスティング | Microsoft Docs"
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
  - "ホスティング サービス [WCF], IIS"
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# インターネット インフォメーション サービスでのホスティング
インターネット インフォメーション サービス \(IIS\) アプリケーションの中に [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストする 1 つのオプションがあります。  このホスティング モデルは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] や ASP.NET Web サービス \(ASMX\) が使用するモデルと似ています。  
  
## IIS バージョン  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をホストできるオペレーティング システムと IIS バージョンの組み合わせは次のとおりです。  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上で IIS 5.1 を使用。  この環境は、後で [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] などのサーバー オペレーティング システムに展開される、IIS ホスト型アプリケーションの設計と開発に役立ちます。  
  
-   [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] に対する [!INCLUDE[iis601](../../../../includes/iis601-md.md)]。  [!INCLUDE[iis601](../../../../includes/iis601-md.md)] は、スケーラビリティと信頼性を向上し、アプリケーションの分離を実現する高度なプロセス モデルを提供します。  この環境は、HTTP 通信のみを使用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの本運用展開に適しています。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] および [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上で IIS 7.0 を使用。  IIS 7.0 は、[!INCLUDE[iis601](../../../../includes/iis601-md.md)] と同じ高度なプロセス モデルを提供しますが、Windows プロセス アクティブ化サービス \(WAS\) を使用して、HTTP 以外のプロトコル経由でのアクティブ化とネットワーク通信を可能にします。  この環境は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされる任意のネットワーク プロトコル \(HTTP、net.tcp、net.pipe、net.msmq など\) で通信を行う [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの開発に適しています。  WAS [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Windows プロセス アクティブ化サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)」を参照してください。  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) は、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] および Windows Process Activation Service \(WAS\) と連携して、NET4 WCF および WF のサービスのための充実したアプリケーションのホスト環境を提供します。  この利点には、プロセス ライフサイクル管理、プロセス リサイクル、共有ホスティング、迅速な障害保護、プロセスの孤立化、オンデマンド アクティブ化、状態監視などがあります。  詳細については、「[AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=196494)」および「[AppFabric ホスティングの概念](http://go.microsoft.com/fwlink/?LinkId=196495)」を参照してください。  
  
## IIS ホスティングの利点  
 IIS で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホスティングすることには、いくつかの利点があります。  
  
-   IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションや ASMX などの他の種類の IIS アプリケーションと同じように展開、管理されます。  
  
-   IIS はプロセスのアクティブ化、状態管理、リサイクル機能を提供し、ホストされるアプリケーションの信頼性を向上します。  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] と同様に、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] でホストされた [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 共有ホスティング モデルを利用できます。このモデルでは、共通のワーカー プロセス内に複数のアプリケーションが存在し、サーバー密度とスケーラビリティが向上します。  
  
-   IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] と同じ動的なコンパイル モデルを使用します。これにより、ホストされるサービスの開発と展開が簡素化されます。  
  
 IIS で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストすることを決定する場合、IIS 5.1 と [!INCLUDE[iis601](../../../../includes/iis601-md.md)] は HTTP 通信のみに限定されることに注意することが重要です。  ホスト環境の選択[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)」を参照してください。  
  
## IIS にホストされた WCF サービスの展開  
 IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの開発と展開を行うには、次のタスクを実行します。  
  
-   IIS、ASP.NET、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、および [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP アクティブ化コンポーネントが正しくインストールおよび登録されていることを確認します。  
  
-   新しい IIS アプリケーションを作成するか、既存の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションを再利用します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス用の .svc ファイルを作成します。  
  
-   IIS アプリケーションにサービス実装を展開します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構成します。  
  
 各タスクの説明については、「[インターネット インフォメーション サービスでホストされる WCF サービスの配置](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)」を参照してください。  
  
## WCF サービスと ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] とサイド バイ サイドでホストするか、または [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換モードでホストできます。この互換モードでは、サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーション プラットフォームが提供する機能を最大限に活用できます。  これらの機能の詳細については、「[WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)」を参照してください。  
  
## 参照  
 [ServiceHostFactory を使用したホストの拡張](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)   
 [インターネット インフォメーション サービスでホストされる WCF サービスの配置](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)   
 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)   
 [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)   
 [Windows Communication Foundation での Internet Information Services 7.0 の構成](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)   
 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)