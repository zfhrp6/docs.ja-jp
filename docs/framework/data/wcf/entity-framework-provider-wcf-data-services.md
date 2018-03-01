---
title: "Entity Framework プロバイダー (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc27663904371991855b2fe7d96b4a15827d1180
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework プロバイダー (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] と同様に、ADO.NET Entity Framework は、エンティティ リレーションシップ モデルの型である Entity Data Model をベースにしています。 Entity Framework と呼ばれる、Entity Data Model の実装に対して操作を変換する、*概念モデル*、データ ソースに対する同等の操作にします。 このことから、Entity Framework はリレーショナル データに基づくデータ サービスの理想的なプロバイダーとして使用でき、また、Entity Framework をサポートするデータ プロバイダーが存在するデータベースであれば、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用できます。 現在、Entity Framework をサポートするデータ ソースの一覧は、次を参照してください。 [Entity Framework 用のサード パーティ プロバイダー](http://go.microsoft.com/fwlink/?LinkId=143699)です。  
  
 概念モデルでは、エンティティ コンテナーはサービスのルートです。 データ サービスでデータを公開する前に、Entity Framework で概念モデルを定義する必要があります。 詳細については、次を参照してください。[する方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)です。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]有効にすると、エンティティの同時実行トークンを定義するには、オプティミスティック同時実行制御モデルをサポートします。 この同時実行トークンは、エンティティの 1 つ以上のプロパティが含まれており、要求、更新、または削除されているデータに対して行われた変更があるかどうかを判断するためにデータ サービスによって使用されます。 要求内の eTag から取得したトークンの値がエンティティの現在の値と異なる場合、データ サービスで例外が発生します。 プロパティが同時実行トークンの一部であることを示す場合、`ConcurrencyMode="Fixed"` プロバイダーで定義されているデータ モデルに属性 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] を適用する必要があります。 同時実行トークンには、キー プロパティまたはナビゲーション プロパティを含めることはできません。 詳細については、次を参照してください。[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)です。  
  
 Entity Framework の詳細については、次を参照してください。 [Entity Framework の概要](../../../../docs/framework/data/adonet/ef/overview.md)です。  
  
## <a name="see-also"></a>参照  
 [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [リフレクション プロバイダー](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
