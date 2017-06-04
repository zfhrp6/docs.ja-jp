---
title: "メタデータ エンドポイントを公開する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# メタデータ エンドポイントを公開する
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスは 1 つ以上のメタデータ エンドポイントを公開することにより、メタデータを公開します。サービス メタデータを公開すると、そのメタデータで WS\-MetadataExchange \(MEX\) や HTTP\/GET 要求などの標準化プロトコルを使用できるようになります。メタデータのエンドポイントは、アドレス、バインディング、およびコントラクトを持つ他のサービス エンドポイントに似ており、構成またはコードを使用してサービス ホストに追加できます。メタデータ エンドポイントの公開を有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> サービス動作をサービスに追加する必要があります。  
  
## このセクションの内容  
 [方法 : 構成ファイルを使用してサービスのメタデータを公開する](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを構成してメタデータを公開し、クライアントが `?wsdl` クエリ文字列を使用した WS\-MetadataExchange または HTTP\/GET 要求によりメタデータを取得できるようにする方法を示します。  
  
 [方法 : コードを使用してサービスのメタデータを公開する](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 コードを使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスのメタデータの公開を有効にして、`?wsdl` クエリ文字列を使用した WS\-MetadataExchange または HTTP\/GET 要求によりメタデータをクライアントが取得できるようにする方法を示します。  
  
## 参照  
 [メタデータの公開](../../../docs/framework/wcf/feature-details/publishing-metadata.md)