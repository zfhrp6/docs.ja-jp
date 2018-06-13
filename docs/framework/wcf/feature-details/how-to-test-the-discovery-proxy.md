---
title: 探索プロキシをテストする方法
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 35edbd03e912ae2d9c491afb28dee1c4a3055d14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491223"
---
# <a name="how-to-test-the-discovery-proxy"></a>探索プロキシをテストする方法
これは、探索プロキシの実装方法に関する 4 つのトピックのうちの 4 番目のトピックです。 前のトピックで[する方法: を探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)、探索プロキシを使用してサービスを検索し、サービスを呼び出す、WCF クライアント アプリケーションを実装しています。 このトピックでは、探索プロキシ、サービス、およびクライアント アプリケーションが予期したとおりに動作することを確認する方法について説明します。  
  
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
 [探索プロキシを実装する方法](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [探索プロキシで登録される探索可能なサービスの実装方法](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装方法](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
