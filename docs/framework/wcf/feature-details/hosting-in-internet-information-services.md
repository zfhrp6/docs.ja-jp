---
title: インターネット インフォメーション サービスでのホスティング
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 588e069280afc369256fdbee0132f732348ffc37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494115"
---
# <a name="hosting-in-internet-information-services"></a>インターネット インフォメーション サービスでのホスティング
Windows Communication Foundation (WCF) サービスをホストするための 1 つのオプションは、インターネット インフォメーション サービス (IIS) アプリケーションの内部でです。 このホスティング モデルは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] や ASP.NET Web サービス (ASMX) が使用するモデルと似ています。  
  
## <a name="versions-of-iis"></a>IIS バージョン  
 WCF は、次のオペレーティング システムで次のバージョンの IIS でホストできます。  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上で IIS 5.1 を使用。 この環境は、後で [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] などのサーバー オペレーティング システムに展開される、IIS ホスト型アプリケーションの設計と開発に役立ちます。  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] に対する [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]。 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] は、スケーラビリティと信頼性を向上し、アプリケーションの分離を実現する高度なプロセス モデルを提供します。 この環境は、HTTP 通信のみを使用する WCF サービスの運用環境のデプロイに適しています。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] および [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上で IIS 7.0 を使用。 IIS 7.0 は、[!INCLUDE[iis601](../../../../includes/iis601-md.md)] と同じ高度なプロセス モデルを提供しますが、Windows プロセス アクティブ化サービス (WAS) を使用して、HTTP 以外のプロトコル経由でのアクティブ化とネットワーク通信を可能にします。 この環境は、WCF (HTTP、net.tcp、net.pipe、net.msmq など) によってサポートされる任意のネットワーク プロトコル経由で通信する WCF サービスの開発に適しています。 WAS の詳細については、次を参照してください。 [Windows Process Activation Service でのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)です。  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496)連動[!INCLUDE[iisver](../../../../includes/iisver-md.md)]およびリッチ アプリケーションをホストして、NET4 WCF および WF のサービスの環境を提供する Windows プロセス アクティブ化サービス (WAS) です。 この利点には、プロセス ライフサイクル管理、プロセス リサイクル、共有ホスティング、迅速な障害保護、プロセスの孤立化、オンデマンド アクティブ化、状態監視などがあります。 詳細については、次を参照してください。 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=196494)と[AppFabric ホスティングの概念](http://go.microsoft.com/fwlink/?LinkId=196495)です。  
  
## <a name="benefits-of-iis-hosting"></a>IIS ホスティングの利点  
 IIS で WCF サービスをホストするいると、いくつかの利点があります。  
  
-   IIS でホストされる WCF サービスを展開し、IIS アプリケーションの他の任意の型と同様に管理を含む[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]アプリケーションや ASMX です。  
  
-   IIS はプロセスのアクティブ化、状態管理、リサイクル機能を提供し、ホストされるアプリケーションの信頼性を向上します。  
  
-   同様に[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]、WCF サービスでホストされて[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]活用できる、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]改良されたサーバー密度とスケーラビリティのための共通のワーカー プロセスで複数のアプリケーションが存在する共有ホスティング モデルです。  
  
-   IIS でホストされる WCF サービスと同様の動的なコンパイル モデルを使用して[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]開発を簡略化する、およびホステッド サービスを展開します。  
  
 注意してくださいは IIS で WCF サービスをホストする場合は、その IIS 5.1 と[!INCLUDE[iis601](../../../../includes/iis601-md.md)]は HTTP 通信のみに制限されます。 ホスト環境の選択の詳細については、次を参照してください。[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)です。  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>IIS にホストされた WCF サービスの展開  
 IIS でホストされる WCF サービスの展開の開発と、次のタスクで構成されます。  
  
-   IIS、ASP.NET、WCF および WCF HTTP アクティブ化コンポーネントが正しくインストールされ登録されていることを確認します。  
  
-   新しい IIS アプリケーションを作成するか、既存の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションを再利用します。  
  
-   WCF サービスの .svc ファイルを作成します。  
  
-   IIS アプリケーションにサービス実装を展開します。  
  
-   WCF サービスを構成します。  
  
 これらの各タスクの詳細については、次を参照してください。[インターネット WCF サービスを展開する](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)です。  
  
## <a name="wcf-services-and-aspnet"></a>WCF サービスと ASP.NET  
 WCF サービスは、いずれかサイド バイ サイドでホストされている[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]または[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]互換モードのサービスがによって提供される機能を最大限に活用を受け取ることができます、 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーション プラットフォームです。 これらの機能の詳細については、次を参照してください。 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ServiceHostFactory を使用したホストの拡張](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [インターネット インフォメーション サービスでホストされる WCF サービスの配置](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Windows Communication Foundation での Internet Information Services 7.0 の構成](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
