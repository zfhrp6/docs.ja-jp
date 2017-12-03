---
title: "探索プロキシのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 515f91baf48f68ba0c1cb32e00152bf025fe7323
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-proxy-sample"></a>探索プロキシのサンプル
このサンプルでは、既存のサービスに関する情報を格納するために探索プロキシの実装を作成する方法、およびクライアントからそのプロキシに情報のクエリを行う方法を示します。 このサンプルは、3 つのプロジェクトで構成されます。  
  
-   **サービス**: 単純な[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]探索プロキシに自らを登録する電卓サービス。  
  
-   **探索プロキシ**: 探索プロキシ サービスの実装です。  
  
-   **クライアント**: する WCF クライアント アプリケーション サービスの検索、探索プロキシが必要です。  
  
## <a name="demonstrates"></a>使用例  
 探索プロキシの実装  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 このサンプルでは、Program.cs ファイルの `Main` メソッドで、<xref:System.ServiceModel.Discovery.DiscoveryProxy> 型のサービスをホストする方法を示します。 このメソッドによって、<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 型と <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 型の 2 つのエンドポイントが公開されます。 どちらのエンドポイントも、TCP をトランスポートとして使用します。 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> は、`probeEndpointAddress` パラメーターで指定された URI をリッスンします。クライアントは、ここにプローブ メッセージを送信して、プロキシに対するデータのクエリを行うことができます。 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> は、`announcementEndpointAddress` パラメーターで指定された URI をリッスンします。 これは、プロキシがアナウンスをリッスンする場所です。 プロキシは、オンライン アナウンスを受け取るとサービスをキャッシュに追加し、オフライン アナウンスを受け取るとサービスをキャッシュから削除します。  
  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> の実装は DiscoveryProxy.cs に含まれています。 プロキシは <xref:System.Object> クラスから継承する必要があり、<xref:System.Runtime.Remoting.Messaging.AsyncResult> の実装を必要とします。 インスタンス化すると、プロキシは新しい <xref:System.Collections.Generic.Dictionary%602> を作成し、それを使用して認識している要素を格納します。  
  
 ファイルは、Proxy Cache Methods および Discovery Proxy Implementation という 2 つの領域に分かれています。 Proxy Cache Methods 領域には、<xref:System.Collections.Generic.Dictionary%602> の更新、<xref:System.Collections.Generic.Dictionary%602> に対するクエリの実行、およびユーザーへのデータの出力に使用するメソッドが含まれています。 Discovery Proxy Implementation 領域には、アナウンスおよびプローブ機能に必要なオーバーライドされたメソッドが含まれています。 これらによって、オンライン アナウンス、オフライン アナウンス、またはプローブ メッセージを受け取った後にプロキシで実行されるアクションが定義されます。  
  
## <a name="service"></a>サービス  
 Service プロジェクトの Program.cs ファイルでは、探索プロキシと同じ URI がアナウンス エンドポイントに使用されています。 これは、サービスがこのエンドポイントを使用して送信したアナウンスを、プロキシが同じエンドポイントを使用して受け取るためです。 サービスは、<xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> を使用し、それにアナウンス エンドポイントを追加します。  
  
## <a name="client"></a>クライアント  
 Client プロジェクトは、プロキシと同じ URI をプローブ エンドポイントに使用します。 これは、このシナリオのプローブも、プロキシで使用できるエンドポイントに明確にユニキャストされるからです。 クライアントは、この既知のアドレスに接続してサービスのクエリを実行し、 サービスを見つけるとそれに接続します。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。  
  
2.  最初に、[ソリューションの基本ディレクトリ]\DiscoveryProxy\bin\debug に生成された探索プロキシ アプリケーションを実行します。 探索プロキシを最初に実行しなければならないのは、サービスでアナウンスを送信するために TCP アナウンス エンドポイントを起動しておく必要があるからです。  
  
3.  2 番目に、[ソリューションの基本ディレクトリ]\Service\bin\debug に生成されたサービス アプリケーションを実行します。 起動時に、サービスから探索プロキシのアナウンス エンドポイントにアナウンスが送信され、サービスがプロキシのキャッシュに登録されます。  
  
4.  次に、[ソリューションの基本ディレクトリ]\Client\bin\debug に生成されたクライアント アプリケーションを実行します。 クライアントは、プロキシに対してクエリを実行してサービスのアドレスを取得し、サービスに接続します。  
  
5.  最後に、クライアント、サービス、プロキシの順に終了します。 プロキシは、サービスのオフライン アナウンスを受け取るまでは実行されている必要があります。  
  
## <a name="see-also"></a>関連項目
