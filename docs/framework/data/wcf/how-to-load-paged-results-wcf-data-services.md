---
title: "方法: ページングされた結果を読み込む (WCF Data Services)"
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
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 405bea18b03ba695dcb952d10a193decc124841d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>方法: ページングされた結果を読み込む (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、1 つの応答フィードで返されるエンティティの数をデータ サービスで制限できます。 この処理を行うと、フィードの最終的なエントリには、データの次のページへのリンクが含まれます。 データの次のページへの URI は、<xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> が実行されたときに返される <xref:System.Data.Services.Client.QueryOperationResponse%601> の <xref:System.Data.Services.Client.DataServiceQuery%601> メソッドを呼び出すことによって取得されます。 このオブジェクトによって表される URI は、結果の次のページを読み込むために使用されます。 詳細については、次を参照してください。[遅延コンテンツを読み込んで](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)です。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 完了したときにこのサービスおよびクライアント データ クラスが作成された、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。  
  
## <a name="example"></a>例  
 次の例は、`do…while` ループを使用して、データ サービスからのページングされた結果の `Customers` エンティティを読み込みます。  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>例  
 次の例は、関連する `Orders` エンティティと各 `Customers` エンティティを返し、`do…while` ループを使用して `Customers` エンティティ ページおよび入れ子になった `while` ループを読み込んで、データ サービスから関連する `Orders` エンティティのページを読み込みます。  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>参照  
 [遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [方法: 関連エンティティを読み込む](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)
