---
title: "探索プロキシをテストする方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 探索プロキシをテストする方法
これは、探索プロキシの実装方法に関する 4 つのトピックのうちの 4 番目のトピックです。  前のトピック「[探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装方法](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)」では、探索プロキシを使用してサービスを検索し、そのサービスを呼び出す [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションを実装しました。  このトピックでは、探索プロキシ、サービス、およびクライアント アプリケーションが予期したとおりに動作することを確認する方法について説明します。  
  
### 探索プロキシの実行  
  
1.  管理者としてコマンド プロンプトを開きます。  
  
2.  "このプログラムの機能のいくつかが Windows ファイアウォールでブロックされています" という内容のダイアログが表示される場合があります。  このメッセージが表示された場合は、**\[ブロックを解除する\]** をクリックします。  
  
3.  コマンド プロンプトから、探索プロキシ DiscoveryProxy.exe を実行します。  
  
4.  「`Proxy started. Hit Enter to exit`」というテキストが表示されます。  
  
### 探索サービスの実行  
  
1.  管理者としてコマンド プロンプトを開きます。  
  
2.  コマンド プロンプトから、探索サービス Service.exe を実行します。  
  
3.  DiscoveryProxy.exe により、次のテキストが表示されます。`******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### クライアント アプリケーションの実行  
  
1.  コマンド プロンプトを開きます。  
  
2.  コマンド プロンプトから、client.exe アプリケーションを実行します。  
  
3.  数秒後に、クライアント アプリケーションにより「\<サービス エンドポイント\> に接続しています」というテキストが表示されます。  
  
4.  次に、service.exe により「Greeting request received, I will respond」というテキストが表示されます。  
  
5.  その後、client.exe により「Hello Client\!」というテキストが表示されます。  
  
### アプリケーションのシャットダウン  
  
1.  クライアント アプリケーションをシャットダウンします。  
  
2.  サービスをシャットダウンします。  探索プロキシにより、次のテキストが表示されます。`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`  
  
3.  探索プロキシをシャットダウンします。  
  
## 参照  
 [WCF Discovery の概要](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)   
 [探索プロキシを実装する方法](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)   
 [探索プロキシで登録される探索可能なサービスの実装方法](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)   
 [探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装方法](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)