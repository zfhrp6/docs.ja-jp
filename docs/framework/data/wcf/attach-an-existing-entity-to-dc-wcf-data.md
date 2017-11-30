---
title: "方法: 既存のエンティティを DataServiceContext にアタッチする (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e389e0ff274b0b4c256bbd9764cd72805b09fcc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>方法: 既存のエンティティを DataServiceContext にアタッチする (WCF Data Services)
データ サービスで、エンティティが既に存在する場合、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]クライアント ライブラリでは、直接にエンティティを表すオブジェクトをアタッチすることができます、<xref:System.Data.Services.Client.DataServiceContext>最初にクエリを実行します。 詳細については、次を参照してください。[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)です。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 完了したときにこのサービスおよびクライアント データ クラスが作成された、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。  
  
## <a name="example"></a>例  
 次の例は、データ サービスに保存する変更を含む既存の `Customer` オブジェクトを作成する方法を示します。 オブジェクトがコンテキストにアタッチされ、<xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> メソッドが呼び出される前に、<xref:System.Data.Services.Client.EntityStates.Modified> メソッドが呼び出されてアタッチされたオブジェクトが <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> としてマークされます。  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
