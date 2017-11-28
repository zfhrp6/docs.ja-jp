---
title: "メタデータの公開"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e0cf48d429282c692557fd66bc6ef1295e6a531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="publishing-metadata"></a>メタデータの公開
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスは 1 つ以上のメタデータ エンドポイントを公開することにより、メタデータを公開します。 サービス メタデータを公開すると、そのメタデータで WS-MetadataExchange (MEX) や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。 メタデータのエンドポイントはアドレス、バインディング、コントラクトを持つ他のサービス エンドポイントに類似し、それらは構成か命令コードを使用してサービス ホストに追加することができます。  
  
## <a name="publishing-metadata-endpoints"></a>メタデータ エンドポイントを公開する  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのメタデータ エンドポイントを公開するには、最初に <xref:System.ServiceModel.Description.ServiceMetadataBehavior> のサービスの動作をサービスに追加しておく必要があります。 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> インスタンスを追加すると、サービスからメタデータ エンドポイントを公開できます。 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> サービス動作を追加すると、MEX プロトコルをサポートするメタデータ エンドポイント、または HTTP/GET 要求に応答するメタデータ エンドポイントを公開できます。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> は <xref:System.ServiceModel.Description.WsdlExporter> を使用して、サービス内のすべてのサービス エンドポイント用のメタデータをエクスポートします。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]サービスからメタデータをエクスポートするを参照してください[エクスポートおよびインポートするメタデータ](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)です。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> は、<xref:System.ServiceModel.Description.ServiceMetadataExtension> インスタンスをサービス ホストへの拡張として追加します。 <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> により、メタデータ公開プロトコルを実装することができます。 また、<xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> を使用して、<xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> プロパティにアクセスすることにより、実行時にサービスのメタデータを取得できます。  
  
### <a name="mex-metadata-endpoints"></a>MEX メタデータ エンドポイント  
 MEX プロトコルを使用するメタデータ エンドポイントを追加するには、`IMetadataExchange` サービス コントラクトを使用するサービス エンドポイントをサービス ホストに追加します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、<xref:System.ServiceModel.Description.IMetadataExchange> プログラミング モデルの一部として使用できるこのサービス コントラクト名を持つ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インターフェイスが用意されます。 WS-MetadataExchange のエンドポイント、つまり MEX エンドポイントは、<xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスで静的ファクトリ メソッドが公開する 4 つの既定のバインディングの 1 つを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ツール (Svcutil.exe など) によって使用される既定のバインディングを照合できます。 また、独自のカスタム バインディングを使用して MEX メタデータ エンドポイントを構成することもできます。  
  
### <a name="http-get-metadata-endpoints"></a>HTTP GET メタデータ エンドポイント  
 HTTP/GET 要求に応答するメタデータ エンドポイントをサービスに追加するには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> の <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> プロパティを `true` に設定します。 また、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> の <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> プロパティを `true` に設定することで、HTTPS を使用するメタデータ エンドポイントを構成することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構成してメタデータを公開し、`?wsdl` クエリ文字列を使用した WS-MetadataExchange または HTTP/GET 要求によりメタデータをクライアントが取得できるようにする方法を示します。  
  
 [方法: コードを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 コードを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのメタデータの公開を有効にして、クライアントが `?wsdl` クエリ文字列を使用した WS-MetadataExchange または HTTP/GET 要求によりメタデータを取得できるようにする方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>関連項目  
 [エクスポートして、メタデータのインポート](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
