---
title: インターネット インフォメーション サービスでのホスティング
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
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b933626c2f3f5ee7121d141d3704376efeb54ba5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="hosting-in-internet-information-services"></a>インターネット インフォメーション サービスでのホスティング
インターネット インフォメーション サービス (IIS) アプリケーションの中に [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストする 1 つのオプションがあります。 このホスティング モデルは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] や ASP.NET Web サービス (ASMX) が使用するモデルと似ています。  
  
## <a name="versions-of-iis"></a>IIS バージョン  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をホストできるオペレーティング システムと IIS バージョンの組み合わせは次のとおりです。  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上で IIS 5.1 を使用。 この環境は、後で [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] などのサーバー オペレーティング システムに展開される、IIS ホスト型アプリケーションの設計と開発に役立ちます。  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] に対する [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]。 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] は、スケーラビリティと信頼性を向上し、アプリケーションの分離を実現する高度なプロセス モデルを提供します。 この環境は、HTTP 通信のみを使用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの本運用展開に適しています。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] および [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上で IIS 7.0 を使用。 IIS 7.0 は、[!INCLUDE[iis601](../../../../includes/iis601-md.md)] と同じ高度なプロセス モデルを提供しますが、Windows プロセス アクティブ化サービス (WAS) を使用して、HTTP 以外のプロトコル経由でのアクティブ化とネットワーク通信を可能にします。 この環境は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされる任意のネットワーク プロトコル (HTTP、net.tcp、net.pipe、net.msmq など) で通信を行う [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの開発に適しています。 WAS の詳細については、次を参照してください。 [Windows Process Activation Service でのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)です。  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496)連動[!INCLUDE[iisver](../../../../includes/iisver-md.md)]およびリッチ アプリケーションをホストして、NET4 WCF および WF のサービスの環境を提供する Windows プロセス アクティブ化サービス (WAS) です。 この利点には、プロセス ライフサイクル管理、プロセス リサイクル、共有ホスティング、迅速な障害保護、プロセスの孤立化、オンデマンド アクティブ化、状態監視などがあります。 詳細については、次を参照してください。 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=196494)と[AppFabric ホスティングの概念](http://go.microsoft.com/fwlink/?LinkId=196495)です。  
  
## <a name="benefits-of-iis-hosting"></a>IIS ホスティングの利点  
 IIS で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホスティングすることには、いくつかの利点があります。  
  
-   IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションや ASMX などの他の種類の IIS アプリケーションと同じように展開、管理されます。  
  
-   IIS はプロセスのアクティブ化、状態管理、リサイクル機能を提供し、ホストされるアプリケーションの信頼性を向上します。  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] と同様に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でホストされた [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 共有ホスティング モデルを利用できます。このモデルでは、共通のワーカー プロセス内に複数のアプリケーションが存在し、サーバー密度とスケーラビリティが向上します。  
  
-   IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] と同じ動的なコンパイル モデルを使用します。これにより、ホストされるサービスの開発と展開が簡素化されます。  
  
 IIS で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストすることを決定する場合、IIS 5.1 と [!INCLUDE[iis601](../../../../includes/iis601-md.md)] は HTTP 通信のみに限定されることに注意することが重要です。 ホスト環境の選択の詳細については、次を参照してください。[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)です。  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>IIS にホストされた WCF サービスの展開  
 IIS でホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの開発と展開を行うには、次のタスクを実行します。  
  
-   IIS、ASP.NET、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、および [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP アクティブ化コンポーネントが正しくインストールおよび登録されていることを確認します。  
  
-   新しい IIS アプリケーションを作成するか、既存の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションを再利用します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス用の .svc ファイルを作成します。  
  
-   IIS アプリケーションにサービス実装を展開します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構成します。  
  
 これらの各タスクの詳細については、次を参照してください。[インターネット WCF サービスを展開する](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)です。  
  
## <a name="wcf-services-and-aspnet"></a>WCF サービスと ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] とサイド バイ サイドでホストするか、または [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 互換モードでホストできます。この互換モードでは、サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーション プラットフォームが提供する機能を最大限に活用できます。 これらの機能の詳細については、次を参照してください。 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ServiceHostFactory を使用したホストの拡張](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [インターネット インフォメーション サービスでホストされる WCF サービスの配置](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Communication Foundation での Internet Information Services 7.0 の構成](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
