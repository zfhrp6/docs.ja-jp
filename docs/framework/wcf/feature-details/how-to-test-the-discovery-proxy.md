---
title: "探索プロキシをテストする方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55a7fe72b34fc8c099d921e7e295c184817825a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-test-the-discovery-proxy"></a>探索プロキシをテストする方法
これは、探索プロキシの実装方法に関する 4 つのトピックのうちの 4 番目のトピックです。 前のトピックで[する方法: を探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)、実装する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアント アプリケーションを探索プロキシを使用してサービスを検索してから、サービス。 このトピックでは、探索プロキシ、サービス、およびクライアント アプリケーションが予期したとおりに動作することを確認する方法について説明します。  
  
### <a name="run-the-discovery-proxy"></a>探索プロキシの実行  
  
1.  管理者としてコマンド プロンプトを開きます。  
  
2.  "このプログラムの機能のいくつかが Windows ファイアウォールでブロックされています" という内容のダイアログが表示される場合があります。 このメッセージを表示する場合にクリックして、**ブロックを解除する**ボタンをクリックします。  
  
3.  コマンド プロンプトから、探索プロキシ DiscoveryProxy.exe を実行します。  
  
4.  「`Proxy started. Hit Enter to exit`」というテキストが表示されます。  
  
### <a name="run-the-discoverable-service"></a>探索サービスの実行  
  
1.  管理者としてコマンド プロンプトを開きます。  
  
2.  コマンド プロンプトから、探索サービス Service.exe を実行します。  
  
3.  DiscoveryProxy.exe は、次のテキストを表示する必要があります:`******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******`です。  
  
### <a name="run-the-client-application"></a>クライアント アプリケーションの実行  
  
1.  コマンド プロンプトを開きます。  
  
2.  コマンド プロンプトから、client.exe アプリケーションを実行します。  
  
3.  数秒後に、クライアント アプリケーションにより「サービス エンドポイント に接続しています」というテキストが表示されます。  
  
4.  次に、service.exe により「Greeting request received, I will respond」というテキストが表示されます。  
  
5.  その後、client.exe により「Hello Client!」というテキストが表示されます。  
  
### <a name="shut-down-the-applications"></a>アプリケーションのシャットダウン  
  
1.  クライアント アプリケーションをシャットダウンします。  
  
2.  サービスをシャットダウンします。 探索プロキシにより、次のテキストが表示されます。`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`  
  
3.  探索プロキシをシャットダウンします。  
  
## <a name="see-also"></a>関連項目  
 [WCF Discovery の概要](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [方法: 探索プロキシの実装](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [方法: 探索プロキシで登録される探索可能なサービスを実装します。](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [方法: 探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
