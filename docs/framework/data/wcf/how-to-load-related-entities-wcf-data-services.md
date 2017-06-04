---
title: "方法: 関連エンティティを読み込む (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 遅延コンテンツ"
  - "WCF Data Services, データの読み込み"
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: 関連エンティティを読み込む (WCF Data Services)
関連付けられたエンティティを [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で読み込む必要がある場合、<xref:System.Data.Services.Client.DataServiceContext> クラスで <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> メソッドを使用できます。  <xref:System.Data.Services.Client.DataServiceQuery%601> で <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用して、関連エンティティが同じクエリ応答で集中的に読み込むよう要求することもできます。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の例は、返される各 `Orders` インスタンスに関連付けられた `Customer` を明示的に読み込む方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## 使用例  
 次の例は、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用して、クエリによって返される `Orders` に属する `Order Details` を返す方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## 参照  
 [データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)