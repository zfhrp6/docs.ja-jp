---
title: "方法: クエリをバッチで実行する (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 384274b127e04004117cbb2f6d5f7764c3212d0b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>方法: クエリをバッチで実行する (WCF Data Services)
使用して、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]クライアント ライブラリは、単一のバッチでデータ サービスに対して 1 つ以上のクエリを実行することができます。 詳細については、次を参照してください。[操作のバッチ処理](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)です。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 完了したときにこのサービスおよびクライアント データ クラスが作成された、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。  
  
## <a name="example"></a>例  
 次の例は、<xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> メソッドを呼び出して、<xref:System.Data.Services.Client.DataServiceRequest%601> オブジェクトと `Customers` オブジェクトの両方を Northwind データ サービスから返すクエリを含む `Products` オブジェクトの配列を実行する方法を示します。 返された <xref:System.Data.Services.Client.QueryOperationResponse%601> 内の <xref:System.Data.Services.Client.DataServiceResponse> オブジェクトのコレクションが列挙され、各 <xref:System.Data.Services.Client.QueryOperationResponse%601> に含まれるオブジェクトのコレクションも列挙されます。  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
