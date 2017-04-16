---
title: "Windows プロセス アクティブ化サービスでのホスティング | Microsoft Docs"
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
  - "ホスティング サービス [WCF], WAS"
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Windows プロセス アクティブ化サービスでのホスティング
Windows プロセス アクティブ化サービス \(WAS\) は、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストするアプリケーションが含まれるワーカー プロセスのアクティベーションと有効期間を管理します。  WAS プロセス モデルは HTTP の依存関係を取り除くことにより、HTTP サーバーの [!INCLUDE[iis601](../../../../includes/iis601-md.md)] プロセス モデルを一般化します。  これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、メッセージ ベースのアクティベーションがサポートされ、特定のコンピューター上で多数のアプリケーションをホストできるホスト環境で、Net.TCP などの HTTP プロトコルと非 HTTP プロトコルの両方を使用できるようになります。  
  
 WAS ホスト環境で実行される [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構築する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : WAS で WCF サービスをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)」を参照してください。  
  
 WAS プロセスモデルは、信頼性が高く管理も容易でリソースを効果的に使用する方法でアプリケーションのホストを実現するいくつかの機能を提供します。  
  
-   HTTP と非 HTTP ネットワーク プロトコルを使用して到着する作業アイテムに応答して、アプリケーションやワーカー プロセス アプリケーションを動的に起動、停止する、メッセージに基づくアクティベーション。  
  
-   実行中のアプリケーションの状態を維持するための、信頼性の高いアプリケーションとワーカー プロセスのリサイクル。  
  
-   集中化されたアプリケーション設定と管理。  
  
-   完全な IIS インストールの配置スペースを必要とせずに、アプリケーションで IIS プロセス モデルを利用可能。  
  
 WAS 機能[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[IIS 7.0 Beta: IIS 7.0 Web Administration](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)」を参照してください。  
  
 [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) は、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] および Windows Process Activation Service \(WAS\) と連携して、NET4 WCF および WF のサービスのための充実したアプリケーションのホスト環境を提供します。  この利点には、プロセス ライフサイクル管理、プロセス リサイクル、共有ホスティング、迅速な障害保護、プロセスの孤立化、オンデマンド アクティブ化、状態監視などがあります。  詳細については、「[AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=196494)」および「[AppFabric ホスティングの概念](http://go.microsoft.com/fwlink/?LinkId=196495)」を参照してください。  
  
## WAS アドレス指定モデルの要素  
 アプリケーションには、サーバーによって有効期間と実行環境が管理されているコード単位である URI \(Uniform Resource Identifier\) アドレスがあります。  1 つの WAS サーバー インスタンスを多数の異なるアプリケーションでホームとすることができます。  サーバーでアプリケーションは*サイト*と呼ばれるグループに編成されます。  サイト内でアプリケーションは階層で整理されます。この階層は URI の構造に反映されてアプリケーションの外部アドレスとして提供されます。  
  
 アプリケーション アドレスは、ベース URI プレフィックスとアプリケーション固有の相対アドレス \(パス\) の 2 つの部分に分かれます。この 2 つの部分が結合されアプリケーションの外部アドレスが提供されます。  ベース URI プレフィックスは、サイト バインドで構築され、サイト内のすべてのアプリケーションで使用されます。  次に、アプリケーション固有のパス フラグメント \(“\/applicationOne” など\) が取得され、ベース URI プレフィックス \(“net.tcp:\/\/localhost” など\) に追加されてアプリケーション アドレスが構築されます。これでアプリケーションの完全 URI になります。  
  
 HTTP と 非 HTTP サイト バインディングの両方の WAS サイト用に考えられるアドレス シナリオを次の表に示します。  
  
|シナリオ|サイト バインディング|アプリケーション パス|ベース アプリケーション URI|  
|----------|-----------------|-----------------|----------------------|  
|HTTP のみ|http: \*:80:\*|\/appTwo|http:\/\/localhost\/appTwo\/|  
|HTTP と 非 HTTP の混在|http: \*:80:\*<br /><br /> net.tcp: 808:\*|\/appTwo|http:\/\/localhost\/appTwo\/                 <br /> net.tcp:\/\/localhost\/appTwo\/|  
|非 HTTP のみ|net.pipe: \*|\/appThree|net.pipe:\/\/appThree\/|  
  
 アプリケーション内のサービスとリソースにもアドレスを指定できます。  アプリケーション内では、アプリケーション リソースにベース アプリケーション パスに対する相対アドレスが指定されます。  たとえば、コンピューター名 contoso.com のサイトに HTTP と Net.TCP プロトコルの両方のサイト バインドがあるとします。  さらに、そのサイトには 1 つのアプリケーションが \/Billing に格納されており、GetOrders.svc でサービスを公開しているとします。  このとき、GetOrders.svc サービスで SecureEndpoint の相対アドレスを持つエンドポイントが公開されている場合、サービスのエンドポイントは次の 2 つの URI で公開されることになります。  
  
 http:\/\/contoso.com\/Billing\/GetOrders.svc\/SecureEndpoint           
 net.tcp:\/\/contoso.com\/Billing\/GetOrders.svc\/SecureEndpoint  
  
## WAS ランタイム  
 アプリケーションは、アドレス指定と管理の目的でサイトに編成されます。  実行時にもアプリケーションはアプリケーション プールにグループ化されます。  アプリケーション プールには、多数の異なるサイトからの多数の異なるアプリケーションを格納できます。  アプリケーション プール内のすべてのアプリケーションで、一連の共通の実行時特性を共有します。  たとえば、すべてのアプリケーションは同じバージョンの共通言語ランタイム \(CLR\) 下で実行され、またすべてのアプリケーションで共通のプロセス ID を共有します。  各アプリケーション プールはワーカー プロセス \(w3wp.exe\) のインスタンスに対応します。  共有アプリケーション プール内で実行される各マネージ アプリケーションは、CLR AppDomain により他のアプリケーションから分離されます。  
  
## 参照  
 [WAS アクティベーション アーキテクチャ](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)   
 [WCF で使用するための WAS を設定する](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)   
 [方法 : WCF アクティブ化コンポーネントをインストールして設定する](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)   
 [方法 : WAS で WCF サービスをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)   
 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)