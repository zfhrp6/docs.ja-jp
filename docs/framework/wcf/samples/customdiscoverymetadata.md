---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 3e3a173d99f2ba0a2fb33dfd8f91908f03e3e871
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501050"
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
このサンプルでは、サービスによって公開される探索可能なエンドポイントの探索メタデータにカスタム XML メタデータを挿入する方法を説明します。 次に、クライアントがサービスを検索してこのカスタム データを抽出する方法を示します。 このサンプルは、2 つのプロジェクト (サービスとクライアント) で構成されます。  
  
## <a name="service"></a>サービス  
 サンプルの `main` メソッドでは、<xref:System.Xml.Linq.XElement> 型のオブジェクトに必要なフィールドが設定され、このオブジェクトが <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> に追加されます。 この <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> が特定のエンドポイントに追加されます。 この特定のエンドポイントが探索されると、ここで追加されたカスタム データが探索メタデータに格納されます。  
  
## <a name="client"></a>Client  
 サンプルでは、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> で <xref:System.ServiceModel.Discovery.DiscoveryClient> メソッドが呼び出されます。 次に、生成された <xref:System.ServiceModel.Discovery.FindResponse> に対して適切かつ必要な XML 要素が照会されます。 その後、これらの要素がコンソールに出力されます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。  
  
2.  まず、[ソリューションの基本ディレクトリ]\service\bin\debug に生成されたサービス アプリケーションを実行します。次に、[ソリューションの基本ディレクトリ]\Client\bin\debug に生成されたクライアント アプリケーションを実行します。  
  
3.  サービスがオンラインになると、クライアントはサービスを検索し、エンドポイントで公開されているメタデータを出力します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>関連項目
