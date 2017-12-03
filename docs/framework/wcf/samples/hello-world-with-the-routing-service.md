---
title: "ルーティング サービスを使用した Hello World"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ba910afe91af07ecbdb2c71bba2fa496c52f2f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="hello-world-with-the-routing-service"></a>ルーティング サービスを使用した Hello World
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ルーティング サービスを示します。 ルーティング サービスは、コンテンツ ベースのルーターをアプリケーションに簡単に追加できるようにする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンポーネントです。 このサンプルでは、標準の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 電卓のサンプルを改良し、ルーティング サービスを使用して通信するようにします。 このサンプルの電卓クライアントは、ルーターによって公開されるエンドポイントにメッセージを送信するように構成されています。 ルーティング サービスは、送信されてきたすべてのメッセージを受け入れ、電卓サービスに対応するエンドポイントに転送するように構成されています。 したがって、クライアントから送信されたメッセージはルーターで受信され、実際の電卓サービスに再ルーティングされます。 電卓サービスからのメッセージはルーターに送り返され、ルーターから電卓クライアントに渡されます。  
  
### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、HelloRoutingService.sln を開きます。  
  
2.  F5 キーを押すか、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
    > [!NOTE]
    >  F5 キーを押した場合は、電卓クライアントが自動的に起動します。 Ctrl キーと Shift キーを押しながら B キーを押した (ビルドする) 場合は、次のアプリケーションを手動で開始する必要があります。  
    >   
    >  1.  電卓クライアント (./CalculatorClient/bin/client.exe)  
    > 2.  電卓サービス (./CalculatorService/bin/service.exe)  
    > 3.  ルーティング サービス (./RoutingService/bin/RoutingService.exe)  
  
3.  Enter キーを押してクライアントを起動します。  
  
     次の出力が表示されます。  
  
     Add(100,15.99) = 115.99  
  
     Subtract(145,76.54) = 68.46  
  
     Multiply(9,81.25) = 731.25  
  
     Divide(22,7) = 3.14285714285714  
  
## <a name="configurable-via-code-or-appconfig"></a>コードまたは App.Config で構成可能  
 サンプルは、提供された時点では、App.config ファイルを使用してルーターの動作を定義するように構成されています。 App.config ファイルの名前を別の名前に変更して認識されないようにし、ConfigureRouterViaCode() に対するメソッド呼び出しのコメントを解除することもできます。 どちらの方法でも、ルーターの動作は同じになります。  
  
### <a name="scenario"></a>シナリオ  
 このサンプルでは、基本的なメッセージ ポンプとして機能するルーターを示します。 ルーティング サービスは、構成済みの一連の送信先エンドポイントに直接メッセージを渡すように構成された透過的なプロキシ ノードとして機能します。  
  
### <a name="real-world-scenario"></a>実際のシナリオ  
 Contoso では、サービスの名前指定、アドレス指定、構成、およびセキュリティに関する柔軟性を高めるために、 基本的なメッセージ ポンプをサービスの前に配置して、それをエンドポイントとして公開しています。 これにより、実際のサービスの前にセキュリティが追加され、スケールアウトされたソリューションやサービスのバージョン管理を後で簡単に実装できるようになります。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric ホスティングと永続性のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
