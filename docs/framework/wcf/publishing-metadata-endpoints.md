---
title: メタデータ エンドポイントを公開する
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 42e0f82ca2c669bbde444cf6aac9ce8f0266f783
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807080"
---
# <a name="publishing-metadata-endpoints"></a>メタデータ エンドポイントを公開する
Windows Communication Foundation (WCF) サービスは、1 つ以上のメタデータ エンドポイントを公開することにより、メタデータを公開します。 サービス メタデータを公開すると、そのメタデータで WS-MetadataExchange (MEX) や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。 メタデータのエンドポイントは、アドレス、バインディング、およびコントラクトを持つ他のサービス エンドポイントに似ており、構成またはコードを使用してサービス ホストに追加できます。 メタデータ エンドポイントの公開を有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> サービス動作をサービスに追加する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法 : 構成ファイルを使用してサービスのメタデータを公開する](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 クライアントは、Ws-metadataexchange または HTTP/GET 要求を使用して、使用してメタデータを取得できるようにするメタデータを公開する WCF サービスを構成する方法を示します、`?wsdl`クエリ文字列。  
  
 [方法 : コードを使用してサービスのメタデータを公開する](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 クライアントは、Ws-metadataexchange または HTTP/GET 要求を使用して、使用してメタデータを取得できるように、コード内の WCF サービスのメタデータの公開を有効にする方法を示しています、`?wsdl`クエリ文字列。  
  
## <a name="see-also"></a>関連項目  
 [メタデータの公開](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
