---
title: "方法: リフレクション プロバイダーでフィードをカスタマイズする (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0989436b3315f69727aeaca03d51d7fbd3cbb6fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>方法: リフレクション プロバイダーでフィードをカスタマイズする (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービス応答の Atom シリアル化をカスタマイズして、AtomPub プロトコルで定義されている未使用の要素にエンティティのプロパティをマップできます。 このトピックでは、リフレクション プロバイダーを使用して、定義されているデータ モデル内のエンティティ型のマッピング属性を定義する方法について説明します。 詳細については、次を参照してください。[フィードのカスタマイズ](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)です。  
  
 この例については、データ モデルは、トピックの「定義[する方法: リフレクション プロバイダーを使用してデータ サービスを作成](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>例  
 次の例では、`Order` 型の両方のプロパティが既存の Atom 要素にマップされます。 `Product` 型の `Item` プロパティは、別の名前空間のカスタム フィード属性にマップされます。  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>例  
 前の例では、URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` に次の結果が返されます。  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>参照  
 [リフレクション プロバイダー](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
