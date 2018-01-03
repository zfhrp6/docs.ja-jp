---
title: "カスタム データ サービス プロバイダー (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7db780b97c1a7eadffbfa71f60be4afe590ccb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-data-service-providers-wcf-data-services"></a>カスタム データ サービス プロバイダー (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、遅延バインディング データ型に基づいてデータ モデルを定義できるプロバイダーのセットが含まれています。  
  
|プロバイダー|説明|  
|--------------|-----------------|  
|メタデータ プロバイダー|これは、<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを実装することによって実行時にカスタム データ モデルを定義できるコア カスタム データ サービス プロバイダーです。|  
|クエリ プロバイダー|このプロバイダーを使用すると、<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを使用して定義されたカスタム データ モデルに対してクエリを実行できます。 クエリ プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceQueryProvider> インターフェイスを実装することによって作成されます。|  
|更新プロバイダー|このプロバイダーを使用すると、カスタム データ サービス プロバイダー内で公開されている型を更新して同時実行を管理できます。 更新プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceUpdateProvider> インターフェイスを実装することによって作成されます。|  
|ページング プロバイダー|このプロバイダーは、サーバー ドリブン ページング サポートを有効にするためにカスタム データ サービス プロバイダーと一緒に使用します。 カスタム データ サービスのページング プロバイダーは、<xref:System.Data.Services.Providers.IDataServicePagingProvider> インターフェイスを実装することによって作成されます。|  
|ストリーミング プロバイダー|このプロバイダーを使用すると、ストリームとしてバイナリ ラージ オブジェクト データ型を公開できます。 ストリーミング プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスを実装することによって作成されます。 ストリーミング プロバイダーは、Entity Framework プロバイダーおよびリフレクション データ ソース プロバイダーと共に使用することもできます。 詳細については、次を参照してください。[ストリーミング プロバイダー](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)です。|  
  
 詳細については、記事を参照してください。[カスタム データ サービス プロバイダー](http://go.microsoft.com/fwlink/?LinkID=186850)と[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]プロバイダー ツールキット、 [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069)です。  
  
## <a name="see-also"></a>参照  
 [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Entity Framework プロバイダー](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
 [リフレクション プロバイダー](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
