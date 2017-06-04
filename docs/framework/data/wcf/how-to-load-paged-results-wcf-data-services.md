---
title: "方法: ページングされた結果を読み込む (WCF Data Services) | Microsoft Docs"
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
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: ページングされた結果を読み込む (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、1 つの応答フィードで返されるエンティティの数をデータ サービスで制限できます。  この処理を行うと、フィードの最終的なエントリには、データの次のページへのリンクが含まれます。  データの次のページの URI は、<xref:System.Data.Services.Client.DataServiceQuery%601> が実行されたときに返される <xref:System.Data.Services.Client.QueryOperationResponse%601> の<xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> メソッドを呼び出すことによって取得されます。このオブジェクトによって表される URI は、結果の次のページを読み込むために使用されます。  詳細については、「[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の例は、`do…while` ループを使用して、データ サービスからのページングされた結果の `Customers` エンティティを読み込みます。  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## 使用例  
 次の例は、関連する `Orders` エンティティと各 `Customers` エンティティを返し、`do…while` ループを使用して `Customers` エンティティ ページおよび入れ子になった `while` ループを読み込んで、データ サービスから関連する `Orders` エンティティのページを読み込みます。  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## 参照  
 [遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)   
 [方法: 関連エンティティを読み込む](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)