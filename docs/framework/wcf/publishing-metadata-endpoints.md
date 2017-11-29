---
title: "メタデータ エンドポイントを公開する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f3f134526fd24a724ba593302ba2bf1f27fa3e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="2f052-102">メタデータ エンドポイントを公開する</span><span class="sxs-lookup"><span data-stu-id="2f052-102">Publishing Metadata Endpoints</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="2f052-103"> サービスは 1 つ以上のメタデータ エンドポイントを公開することにより、メタデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="2f052-103"> services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="2f052-104">サービス メタデータを公開すると、そのメタデータで WS-MetadataExchange (MEX) や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2f052-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="2f052-105">メタデータのエンドポイントは、アドレス、バインディング、およびコントラクトを持つ他のサービス エンドポイントに似ており、構成またはコードを使用してサービス ホストに追加できます。</span><span class="sxs-lookup"><span data-stu-id="2f052-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="2f052-106">メタデータ エンドポイントの公開を有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> サービス動作をサービスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f052-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f052-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2f052-107">In This Section</span></span>  
 [<span data-ttu-id="2f052-108">方法: 構成ファイルを使用して、サービスのメタデータを公開</span><span class="sxs-lookup"><span data-stu-id="2f052-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="2f052-109">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを構成してメタデータを公開し、`?wsdl` クエリ文字列を使用した WS-MetadataExchange または HTTP/GET 要求によりメタデータをクライアントが取得できるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f052-109">Demonstrates how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="2f052-110">方法: コードを使用して、サービスのメタデータを公開</span><span class="sxs-lookup"><span data-stu-id="2f052-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="2f052-111">コードを使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスのメタデータの公開を有効にして、クライアントが `?wsdl` クエリ文字列を使用した WS-MetadataExchange または HTTP/GET 要求によりメタデータを取得できるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f052-111">Demonstrates how to enable metadata publishing for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f052-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f052-112">See Also</span></span>  
 [<span data-ttu-id="2f052-113">メタデータの公開</span><span class="sxs-lookup"><span data-stu-id="2f052-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
