---
title: "方法: エンティティ リレーションシップを定義する (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 変更 (データを)"
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: エンティティ リレーションシップを定義する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で新しいエンティティを追加するとき、新しいエンティティと関連エンティティの間のリレーションシップは自動的には定義されません。  エンティティ インスタンス間のリレーションシップを作成および変更し、クライアント ライブラリを使用して、これらの変更をデータ サービスに反映できます。  詳細については、「[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の例では、新しいオブジェクト インスタンスを作成し、<xref:System.Data.Services.Client.DataServiceContext> で <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> メソッドを呼び出して、関連する注文へのリンクと共に、コンテキスト内に項目を作成します。  <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドが呼び出されたときに HTTP POST メッセージがデータ サービスに送信されます。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## 使用例  
 次の例では、<xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> メソッドを使用して、特定の `Products` オブジェクトへの参照と共に、`Order_Details` オブジェクトを関連する `Orders` オブジェクトに追加する方法を示します。  <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> メソッドおよび <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> メソッドは、リレーションシップを定義します。  この例では、`Order_Details` オブジェクトのナビゲーション プロパティも明示的に設定されます。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorder)]  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [方法: エンティティを追加、変更、および削除する](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)