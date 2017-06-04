---
title: "WAS アクティベーション アーキテクチャ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# WAS アクティベーション アーキテクチャ
ここでは、Windows プロセス アクティブ化サービス \(WAS とも呼ばれます\) の各コンポーネントについて説明します。  
  
## アクティベーション コンポーネント  
 WAS は、複数のアーキテクチャ コンポーネントで構成されます。  
  
-   リスナー アダプター : 特定のネットワーク プロトコルでメッセージを受信し、WAS と通信して、受信メッセージを適切なワーカー プロセスにルーティングする Windows サービス。  
  
-   WAS : ワーカー プロセスの作成と有効期間を管理する Windows サービス。  
  
-   汎用ワーカー プロセス実行可能ファイル \(w3wp.exe\)。  
  
-   アプリケーション マネージャー : ワーカー プロセス内のアプリケーションをホストするアプリケーション ドメインの作成と有効期間を管理します。  
  
-   プロトコル ハンドラー : ワーカー プロセスで実行され、ワーカー プロセスと個々のリスナー アダプター間の通信を管理するプロトコル固有のコンポーネント。プロトコル ハンドラーには、プロセス プロトコル ハンドラーと AppDomain プロトコル ハンドラーの 2 種類があります。  
  
 ワーカー プロセス インスタンスをアクティブ化する場合、WAS は必要なプロセス プロトコル ハンドラーをワーカー プロセスに読み込み、アプリケーション マネージャーを使用して、アプリケーションをホストするアプリケーション ドメインを作成します。アプリケーション ドメインは、アプリケーションのコードと、アプリケーションが使用するネットワーク プロトコルに必要な AppDomain プロトコル ハンドラーを読み込みます。  
  
 ![WAS アーキテクチャ](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")  
  
### リスナー アダプター  
 リスナー アダプターは個別の Windows サービスであり、リッスンするネットワーク プロトコルを使用して、メッセージ受信に使用されるネットワーク通信ロジックを実装します。次の表は、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] プロトコルのリスナー アダプターの一覧です。  
  
|リスナー アダプターのサービス名|プロトコル|メモ|  
|----------------------|-----------|--------|  
|W3SVC|http|IIS 7.0 と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の両方に HTTP アクティベーションを提供する共通コンポーネントです。|  
|NetTcpActivator|net.tcp|NetTcpPortSharing サービスに依存します。|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ベースのメッセージ キュー アプリケーションで使用します。|  
|NetMsmqActivator|msmq.formatname|既存のメッセージ キュー アプリケーションとの下位互換性を提供します。|  
  
 次の XML サンプルに示すように、特定プロトコルのリスナー アダプターは、インストール時に applicationHost.config ファイルに登録されます。  
  
```  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"   
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"   
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"   
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"   
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### プロトコル ハンドラー  
 特定のプロトコルのプロセス プロトコル ハンドラーと AppDomain プロトコル ハンドラーは、コンピューター レベルの Web.config ファイルに登録されます。  
  
```  
<system.web>  
   <protocols>  
      <add name="net.tcp"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler”/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## 参照  
 [WCF で使用するための WAS を設定する](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)   
 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)