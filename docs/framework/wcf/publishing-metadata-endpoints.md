---
title: メタデータ エンドポイントを公開する
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 6060850b78c890e043dfaf6f242460bc6e0ef627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="publishing-metadata-endpoints"></a>メタデータ エンドポイントを公開する
Windows Communication Foundation (WCF) サービスは、1 つ以上のメタデータ エンドポイントを公開することにより、メタデータを公開します。 サービス メタデータを公開すると、そのメタデータで WS-MetadataExchange (MEX) や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。 メタデータのエンドポイントは、アドレス、バインディング、およびコントラクトを持つ他のサービス エンドポイントに似ており、構成またはコードを使用してサービス ホストに追加できます。 メタデータ エンドポイントの公開を有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> サービス動作をサービスに追加する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法 : 構成ファイルを使用してサービスのメタデータを公開する](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを構成してメタデータを公開し、`?wsdl` クエリ文字列を使用した WS-MetadataExchange または HTTP/GET 要求によりメタデータをクライアントが取得できるようにする方法を示します。  
  
 [方法 : コードを使用してサービスのメタデータを公開する](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 コードを使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスのメタデータの公開を有効にして、クライアントが `?wsdl` クエリ文字列を使用した WS-MetadataExchange または HTTP/GET 要求によりメタデータを取得できるようにする方法を示します。  
  
## <a name="see-also"></a>関連項目  
 [メタデータの公開](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
