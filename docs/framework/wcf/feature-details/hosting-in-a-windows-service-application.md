---
title: "Windows サービス アプリケーションのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1a39162097c21f20c0dd04f3911442602871436
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-in-a-windows-service-application"></a>Windows サービス アプリケーションのホスト
Windows サービス (従来 Windows NT サービスと呼ばれていたもの) が提供するプロセス モデルが特に適しているのは、長い期間にわたって動作し続ける必要があり、どのような形式でもユーザー インターフェイスを表示することのないアプリケーションです。 Windows サービス アプリケーションのプロセスの有効期間を管理するのは、サービス コントロール マネージャー (SCM) です。SCM を使用して、Windows サービス アプリケーションを起動、停止、および一時停止できます。 「常時オン」アプリケーション用の適切なホスティング環境を作成、コンピューターの起動時に自動的に開始する Windows サービスのプロセスを構成することができます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows サービス アプリケーションを参照してください[Windows サービス アプリケーション](http://go.microsoft.com/fwlink/?LinkId=89450)です。  
  
 長い期間にわたって動作し続ける [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストするアプリケーションは、さまざまな点で Windows サービスに似ています。 中でも顕著な類似点は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは長期間動作し続けるサーバー側実行可能ファイルであり、画面上でユーザーと直接対話することがないので、ユーザー インターフェイスを実装する必要がない、ということです。 したがって、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを Windows サービス アプリケーション上でホストするやり方も、頑健で長期間動作し続ける [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションの構築方法として選択肢となります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を開発する際には、多くの場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションを Windows サービス上でホストするか、それとも Internet Information Services (IIS) や Windows Process Activation Service (WAS) のホスティング環境を使うか、決定しなければなりません。 次のような場合、Windows サービス上でホストする方法を使用できないか検討してください。  
  
-   アプリケーションを明示的にアクティブ化する必要がある場合。 たとえば、サーバー起動時に自動的にアプリケーションも起動しなければならず、最初に届いたメッセージに応答して動的に起動するのでは困るような場合です。  
  
-   アプリケーションをホストするプロセスが、起動されたらそのまま動作し続けなければならない場合。 一度起動した Windows サービスのプロセスは、サーバー管理者がサービス コントロール マネージャーで明示的にシャットダウンしない限り、そのまま動作し続けます。 IIS や WAS 上でホストするアプリケーションは、動的に起動および停止して、システム リソースを効率よく使うことができます。 しかし、ホストするプロセスの有効期間にわたって明示的に制御しなければならない場合、IIS や WAS ではなく Windows サービスを使う必要があります。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを Windows Server 2003 上で実行する必要があり、HTTP 以外のトランスポート層プロトコルを使う場合。 Windows Server 2003 では、[!INCLUDE[iis601](../../../../includes/iis601-md.md)] ホスティング環境は HTTP 通信しかできないようになっています。 Windows サービス アプリケーションにはこのような制限がなく、net.tcp、net.pipe、net.msmq など、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が対応しているトランスポート層プロトコルはどれでも使用できます。  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Windows サービス アプリケーションの内部で WCF をホストするには  
  
1.  Windows サービス アプリケーションを作成します。 Windows サービス アプリケーションは、<xref:System.ServiceProcess> 名前空間のクラスを使用して、マネージ コードとして記述することができます。 このアプリケーションには、<xref:System.ServiceProcess.ServiceBase> から派生したクラスを 1 つ含める必要があります。  
  
2.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの有効期間を、Windows サービス アプリケーションの有効期間とリンクさせます。 通常、Windows サービス アプリケーションでホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、ホストする側のサービスの起動時にアクティブになり、停止時にメッセージの監視をやめ、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにエラーが生じた場合はホストする側のプロセスをシャットダウンするようにします。 これは次のようにして実装します。  
  
    -   <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> をオーバーライドして、<xref:System.ServiceModel.ServiceHost> のインスタンスを必要な個数開くようにします。 単一の Windows サービス アプリケーションで、一体となって開始および終了する複数の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストできます。  
  
    -   <xref:System.ServiceProcess.ServiceBase.OnStop%2A> をオーバーライドして、<xref:System.ServiceModel.Channels.CommunicationObject.Closed> 時に起動された <xref:System.ServiceModel.ServiceHost> サービスが稼働する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の、<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> を呼び出します。  
  
    -   <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> の <xref:System.ServiceModel.ServiceHost> イベントを定期受信し、エラー時には、<xref:System.ServiceProcess.ServiceController> クラスを使用して Windows サービス アプリケーションをシャットダウンします。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする Windows サービス アプリケーションも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使わない Windows サービス アプリケーションと同様に展開および管理されます。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceProcess>  
 [チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [方法 : マネージ Windows サービスで WCF サービスをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Windows サービス ホスト](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [サービス アプリケーションのプログラミング アーキテクチャ](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
