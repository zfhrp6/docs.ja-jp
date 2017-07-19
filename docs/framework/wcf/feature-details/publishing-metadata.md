---
title: "メタデータの公開 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メタデータ [WCF], 公開"
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# メタデータの公開
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスは 1 つ以上のメタデータ エンドポイントを公開することにより、メタデータを公開します。サービス メタデータを公開すると、そのメタデータで WS\-MetadataExchange \(MEX\) や HTTP\/GET 要求などの標準化プロトコルを使用できるようになります。メタデータのエンドポイントはアドレス、バインディング、コントラクトを持つ他のサービス エンドポイントに類似し、それらは構成か命令コードを使用してサービス ホストに追加することができます。  
  
## メタデータ エンドポイントを公開する  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのメタデータ エンドポイントを公開するには、最初に <xref:System.ServiceModel.Description.ServiceMetadataBehavior> のサービスの動作をサービスに追加しておく必要があります。<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> インスタンスを追加すると、サービスからメタデータ エンドポイントを公開できます。<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> サービス動作を追加すると、MEX プロトコルをサポートするメタデータ エンドポイント、または HTTP\/GET 要求に応答するメタデータ エンドポイントを公開できます。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> は <xref:System.ServiceModel.Description.WsdlExporter> を使用して、サービス内のすべてのサービス エンドポイント用のメタデータをエクスポートします。サービスからメタデータをエクスポートする方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[メタデータのエクスポートとインポート](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)」を参照してください。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> は、<xref:System.ServiceModel.Description.ServiceMetadataExtension> インスタンスをサービス ホストへの拡張として追加します。<xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=fullName> により、メタデータ公開プロトコルを実装することができます。また、<xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=fullName> を使用して、<xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=fullName> プロパティにアクセスすることにより、実行時にサービスのメタデータを取得できます。  
  
### MEX メタデータ エンドポイント  
 MEX プロトコルを使用するメタデータ エンドポイントを追加するには、`IMetadataExchange` サービス コントラクトを使用するサービス エンドポイントをサービス ホストに追加します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] プログラミング モデルの一部として使用できるこのサービス コントラクト名を持つ <xref:System.ServiceModel.Description.IMetadataExchange> インターフェイスが用意されます。WS\-MetadataExchange のエンドポイント、つまり MEX エンドポイントは、<xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスで静的ファクトリ メソッドが公開する 4 つの既定のバインディングの 1 つを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ツール \(Svcutil.exe など\) によって使用される既定のバインディングを照合できます。また、独自のカスタム バインディングを使用して MEX メタデータ エンドポイントを構成することもできます。  
  
### HTTP GET メタデータ エンドポイント  
 HTTP\/GET 要求に応答するメタデータ エンドポイントをサービスに追加するには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> の <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定します。また、<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> の <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> プロパティを `true` に設定することで、HTTPS を使用するメタデータ エンドポイントを構成することもできます。  
  
## このセクションの内容  
 [方法 : 構成ファイルを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構成してメタデータを公開し、クライアントが `?wsdl` クエリ文字列を使用した WS\-MetadataExchange または HTTP\/GET 要求によりメタデータを取得できるようにする方法を示します。  
  
 [方法 : コードを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 コードを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのメタデータの公開を有効にして、クライアントが `?wsdl` クエリ文字列を使用した WS\-MetadataExchange または HTTP\/GET 要求によりメタデータを取得できるようにする方法を示します。  
  
## リファレンス  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## 参照  
 [メタデータのエクスポートとインポート](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)