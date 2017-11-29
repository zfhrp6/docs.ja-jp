---
title: "動的再構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 32339bbf40513f06c7a719c632f1c606c195b6bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-reconfiguration"></a>動的再構成
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ルーティング サービスを示します。 ルーティング サービスは、コンテンツ ベースのルーターをアプリケーションに簡単に追加できるようにする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンポーネントです。 このサンプルでは、標準の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 電卓のサンプルを改良し、ルーティング サービスを使用して通信するようにします。 このサンプルでは、実行時にルーティング サービスを動的に再構成する方法を示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルでは、実行時にルーティング サービスを動的に再構成するために、5 秒ごとにタイマーを作動させ、新しい <xref:System.ServiceModel.Routing.RoutingConfiguration> オブジェクトを作成して適用します。 この構成は、通常の電卓のエンドポイントまたは丸め処理を行う電卓のエンドポイントのいずれかを示しています。 電卓クライアント アプリケーションは、ルーティング サービスがその時点でどちらのサービスにルーティングするように構成されているかに応じて、いずれか一方のサービスからメッセージを受け取ります。  
  
 ルーティング サービスのカスタム動作を介した動的再構成機能が使用されます。 このカスタム動作は、5 秒ごとに作動する単純なスレッド タイマーを含むサービス拡張をアタッチします。このスレッド タイマーにより、`UpdateRules` メソッドへのコールバックが発生し、 新しいルーティング構成が作成および適用されます。 実際の配置では、このコールバックは、別の種類のイベント (SQL-Event 通知や WS-Discovery アナウンスなど) の結果として行われる可能性があります。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して DynamicReconfiguration.sln を開きます。  
  
2.  開くには**ソリューション エクスプ ローラー****ソリューション エクスプ ローラー**から、**ビュー**メニュー。  
  
3.  キーを押して**f5 キーを押して**または**CTRL + SHIFT + B**で[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]です。  
  
    1.  キーを押したときに必要なプロジェクトを自動的に起動するかかどうか**f5 キーを押して**、ソリューションを右クリックし **プロパティ**です。 選択、**スタートアップ プロジェクト**ノードの下**共通プロパティ**左側のウィンドウでします。 選択、**マルチ スタートアップ プロジェクト**ラジオ ボタンと、すべてのプロジェクトに対して、設定、**開始**アクション。  
  
    2.  使用してプロジェクトをビルドする場合**CTRL + SHIFT + B**、次のアプリケーションを開始する必要があります。  
  
        1.  電卓クライアント (./CalculatorClient/bin/client.exe)  
  
        2.  電卓サービス (./CalculatorService/bin/service.exe)  
  
        3.  丸め処理を行う電卓サービス (./RoundingCalcService/bin/service.exe)  
  
        4.  ルーティング サービス (./RoutingService/bin/RoutingService.exe)  
  
4.  電卓クライアントのコンソール ウィンドウで、Enter キーを押してクライアントを開始し、電卓サービス操作を呼び出します。  
  
     ルーティング サービスは、丸め処理を行う電卓と通常の電卓に交互にメッセージをルーティングします。これはルーティング構成が 5 秒ごとに動的に変化するためです。 ルーティング サービスがどちらのエンドポイントにメッセージを送信するように構成されているかに応じて、異なる出力がクライアント コンソールに表示されます。  
  
5.  Enter キーを 5 秒以上にわたって繰り返し押して、サービスから返される結果が変化することを確認します。  
  
    1.  次に、ルーター サービスが丸め処理を行う電卓サービスにメッセージをルーティングするように構成されている場合に返される出力を示します。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  次に、ルーティング サービスが通常の電卓サービスにメッセージをルーティングするように構成されている場合に返される出力を示します。  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  また、電卓サービスと丸め処理を行う電卓サービスは、呼び出された操作のログをそれぞれのコンソール ウィンドウに出力します。  
  
7.  クライアント コンソール ウィンドウには、「終了」を入力し、enter キーを押して終了します。  
  
8.  サービスを終了するには、サービス コンソール ウィンドウで Enter キーを押します。  
  
## <a name="scenario"></a>シナリオ  
 このサンプルでは、1 つのエンドポイントを介して複数の種類または実装のサービスを公開することを可能にするコンテンツ ベースのルーターとして機能するルーターを示します。  
  
### <a name="real-world-scenario"></a>実際のシナリオ  
 Contoso では、すべてのサービスを仮想化して 1 つのエンドポイントのみを公開し、そのエンドポイントを通じて複数の異なる種類のサービスへのアクセスを提供したいと考えています。 この場合は、ルーティング サービスのコンテンツ ベースのルーティング機能を使用して受信要求の送信先を決定します。  
  
## <a name="see-also"></a>関連項目  
 [AppFabric ホスティングと永続性のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
