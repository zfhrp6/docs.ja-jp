---
title: "方法: 関連エンティティを読み込む (WCF Data Services)"
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
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d25b2052c889fb6ea4614a43f67f07f3f0a073d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>方法: 関連エンティティを読み込む (WCF Data Services)
関連付けられたエンティティを [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で読み込む必要がある場合、<xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> クラスで <xref:System.Data.Services.Client.DataServiceContext> メソッドを使用できます。 使用することも、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>メソッドを<xref:System.Data.Services.Client.DataServiceQuery%601>関連エンティティが同じクエリの応答で集中的に読み込まれることを要求します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 完了したときにこのサービスおよびクライアント データ クラスが作成された、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。  
  
## <a name="example"></a>例  
 次の例は、返される各 `Customer` インスタンスに関連付けられた `Orders` を明示的に読み込む方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>例  
 次の例は、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用して、クエリによって返される `Order Details` に属する `Orders` を返す方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>参照  
 [データ サービスに対するクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
